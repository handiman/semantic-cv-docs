# SemanticCV CLI Reference

The SemanticCV CLI is the primary tool for creating, editing, validating, and rendering your CV as JSON‑LD. This page documents every command, its purpose, and how it fits into the structured‑data workflow.

Commands that take a file name use `cv.json` in the current directory when you leave it out.

## Installation

Install the CLI globally via npm:

```sh
npm install -g semantic-cv
```

Node.js 20 or later is required. Check the installed version with `semantic-cv --version`.

## Commands

### `init`

Create a new CV file with a [`schema.org/Person`][schema] JSON‑LD structure.

```sh
semantic-cv init [filename]
```

The command interactively prompts you for:

- **name** — your full name
- **jobTitle** — your primary professional role
- **email**
- **telephone**
- **url** — your website
- **image** — URL of a profile photo
- **description** — a short summary or tagline
- the file to write to (unless you passed `filename`), `cv.json` by default

Leave a prompt empty to skip that field. `name`, `jobTitle` and `description` are required for a valid CV, and `analyze` reports an error when one is missing.

If the file already exists, `init` asks before overwriting it.

### `set`

Set a single value on your CV.

```sh
semantic-cv set <property> [value] [filename]
```

If you leave out the value, the CLI prompts for it. Supported properties:

| Property                | Sets          |
| ----------------------- | ------------- |
| `name`                  | `name`        |
| `title`, `jobTitle`     | `jobTitle`    |
| `description`           | `description` |
| `email`                 | `email`       |
| `phone`, `telephone`    | `telephone`   |
| `url`, `website`        | `url`         |
| `image`                 | `image`       |
| `workLocation`          | `workLocation`|
| `nationality`           | `nationality` |
| `theme`                 | `theme`       |

Any other property is rejected and your file is left untouched. Use `add` for lists such as work history or skills.

### `add`

Add a structured item to your CV.

```sh
semantic-cv add <section> [filename]
```

Each section prompts you for the relevant fields and inserts the result into your CV. Supported sections and aliases:

| Section (and aliases)                          | Adds                                                  | schema.org property |
| ---------------------------------------------- | ----------------------------------------------------- | ------------------- |
| `worksFor` \| `work` \| `employer` \| `employment` | A job, as a `Role` at an `Organization`           | `worksFor`          |
| `project`                                      | A project, as a `Role` in a `Project`                 | `worksFor`          |
| `keywords` \| `keyword`                        | Keywords (skills) on one of your work or project entries | `keywords`       |
| `alumniOf` \| `education` \| `school`          | Degrees, courses and training                         | `alumniOf`          |
| `skills` \| `skill`                            | Specific skills (tools, languages, frameworks)        | `skills`            |
| `knowsAbout` \| `competence`                   | Knowledge areas                                       | `knowsAbout`        |
| `knowsLanguage` \| `language`                  | Languages you speak                                   | `knowsLanguage`     |
| `sameAs`                                       | A link to a profile elsewhere (GitHub, LinkedIn, …)   | `sameAs`            |
| `hasCertification` \| `certification` \| `cert` | A certification                                      | `hasCertification`  |
| `hasCredential` \| `credential`                | A credential                                          | `hasCredential`     |
| `lifeEvent`                                    | Awards, publications, talks and other milestones      | `lifeEvent`         |

`add keywords` needs at least one work or project entry. If you have several, it asks which one the keywords belong to. Enter the keywords separated by commas.

An unknown section is ignored with a message. The CLI has no commands for removing an item; open `cv.json` in your editor to do that.

### `analyze`

Check your CV and report problems.

```sh
semantic-cv analyze [path]
```

`path` is a file or a directory. For a directory, every `*.cv.json` file in it, including subdirectories, is analyzed.

Analysis checks that:

- `@context` is `https://schema.org` (or the schema.org + semantic.cv context that `normalize` writes), and `@type` is `Person`
- `name`, `jobTitle` and `description` are present
- `email`, `telephone`, `url` and `image` are well formed
- lists such as `skills`, `knowsAbout`, `knowsLanguage` and `sameAs` contain what they should
- entries in `worksFor`, `alumniOf`, `lifeEvent`, `hasCertification` and `hasCredential` have the expected structure

Problems are reported as **errors** or **warnings**. `analyze` never modifies your file. It exits with code 1 if any errors are found, and warnings alone do not count, so you can use it to gate a CI job.

### `normalize`

Rewrite your CV in a canonical form.

```sh
semantic-cv normalize [filename]
```

Normalization:

- fixes the casing of known property names
- sets `@context` and `@type` (`Person`)
- converts single values to arrays, and arrays to single values, where schema.org expects them
- trims whitespace and removes empty values
- sorts work, projects, education, certifications and life events with the most recent first
- writes keys in a fixed order

Running it twice gives the same result. `init`, `set`, `add` and `convert` normalize their output, so you only need `normalize` after editing the file by hand.

### `watch`

Analyze your CV every time you save it.

```sh
semantic-cv watch [path]
```

`path` is a file or a directory; a directory is watched recursively for `*.cv.json` files. The CV is analyzed once on start, and again after every change.

### `convert`

Convert a [JSON Resume](https://jsonresume.org) file into a SemanticCV file.

```sh
semantic-cv convert [source] [output]
```

`source` is a file path or a URL. The CLI prompts for `source` and `output` if you leave them out. If `output` already exists, it asks before overwriting it. Anything that isn't a JSON Resume file is rejected with "Unsupported format".

### `render`

Render your CV as HTML and plain text.

```sh
semantic-cv render <theme> [filename]
```

For `cv.json` this writes:

- `cv.json.html` — your themed CV
- `cv.json.txt` — an ATS‑friendly plain‑text version, linked from the HTML

The output file names are the CV file name plus `.html` and `.txt`.

The `theme` field in your CV is not used by `render`; it selects the theme on the hosted site. An unknown theme prints a warning that lists the available themes, and the CV is rendered with `minimal`.

The free themes are `alice`, `boiling-diesel`, `gnap`, `holden-wreck`, `lena`, `matilda`, `minimal`, `times`, `typewriter` and `winter`. They are the same themes the hosted site uses; see the [theme gallery](https://semantic.cv/themes).

### `help` and `--version`

```sh
semantic-cv help
semantic-cv --version
```

`help` (also `-h`, `--help`, or no command at all) lists the commands. An unknown command prints an error and exits with code 1.

## How the CLI Fits Into the Workflow

The CLI is designed around a simple, deterministic pipeline:

- **Describe yourself** in JSON‑LD, with `init` and `add` or by hand
- **Validate** with `analyze` or `watch`
- **Normalize** with `normalize`
- **Render** locally with `render`, or
- **Publish** to [semantic.cv](https://semantic.cv) via GitHub

Your JSON‑LD is always the single source of truth.

[schema]: https://schema.org/Person
