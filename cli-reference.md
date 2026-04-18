# SemanticCV CLI Reference

The SemanticCV CLI is the primary tool for creating, editing, validating, and rendering your CV as JSON‑LD. This page documents every command, its purpose, and how it fits into the structured‑data workflow.
All commands operate on the cv.json file in the current directory unless otherwise specified.

## Installation

Install the CLI globally via npm:

```sh
npm install -g semantic-cv
```

## Commands

`init`

Create a new CV file with a minimal [`schema.org/Person`][schema] JSON‑LD structure.

```sh
semantic-cv init
```

The init command interactively prompts you for the basic CV fields that form the foundation of any résumé:

- **name** — your full name
- **jobTitle** — your primary professional role
- **description** — a short summary or tagline

These aren’t strictly required by the schema, but they’re essential for producing a meaningful CV.

After collecting your answers, the CLI generates a clean `cv.json` file you can expand manually or through additional commands.

`add`

Add a structured section to your CV.
semantic-cv add <section>

Supported sections and aliases:

| Subcommand(s)                              | Description                      | schema.org/Person |
| ------------------------------------------ | -------------------------------- | ----------------- |
| worksFor \| work \| employment \| employer | Work history entries             | worksFor          |
| alumniOf \| education \| school            | Degrees, certifications, courses | alumniOf          |
| skills \| skill                            | Specific skills                  | skills            |
| knowsAbout \| competence                   | Knowledge areas                  | knowsAbout        |
| knowsLanguage \| language                  | Lanugage proficiency             | knowsLanguage     |
| sameAs                                     | Social network link              | sameAs            |
| hasCertification \| certification \| cert  | Certification                    | hasCertification  |
| lifeEvent \| event                         | Awards, milestones, events       | lifeEvent         |

Each add command prompts you for the relevant fields and inserts the resulting JSON‑LD into your CV.

`analyze`
Validate your CV against the `schema.org/Person` structure.

```sh
semantic-cv analyze
```

This command checks for:

- missing or malformed fields
- incorrect types
- unexpected values
- structural inconsistencies

analyze does **not** modify your file — it only reports issues.

`normalize`
Automatically fix common issues and enforce consistent structure.

```sh
semantic-cv normalize
```

Normalization includes:

- converting single values to arrays where required and vice versa
- sorting entries deterministically
- ensuring consistent field shapes
- applying schema‑aligned defaults

  This helps keep your CV predictable, clean, and theme‑friendly.

`render`
Render your CV as HTML and plain text.

```sh
semantic-cv render <theme>
```

Outputs:

- cv.json\<theme\>.html — your themed CV
- cv.json.txt — an ATS‑friendly plain‑text version

Rendering uses the same free themes that the hosted site uses.

`help`
Show help for any command:

```sh
semantic-cv help
semantic-cv help add
```

## How the CLI Fits Into the Workflow

The CLI is designed around a simple, deterministic pipeline:

- **Describe yourself** in JSON‑LD
- **Validate** with `analyze`
- **Normalize** with `normalize`
- **Render** locally or
- **Publish** to [semantic.cv](https://semantic.cv) via GitHub

Your JSON‑LD is always the single source of truth.

[schema]: https://schema.org/Person
