# Getting Started

SemanticCV helps you write and publish your CV as structured JSON‑LD. This guide walks you through the quickest path from installation to a published CV, whether you prefer working locally or using the hosted workflow.

## 1. Install the CLI
SemanticCV is distributed as an npm package.

Install it globally:
```sh
npm install -g semantic-cv
```

## 2. Create Your CV
Initialize a new CV:
```sh
semantic-cv init
```
The `init command walks you through a short set of prompts to collect the core information every CV needs, such as:
- **name** — your full name
- **jobTitle** — your current role or professional identity
- **description** — a short summary or headline`

These aren’t strictly required by `schema.org/Person`, but they are the foundation of a meaningful CV. Once you’ve answered the prompts, the CLI generates a `cv.json` file containing a clean, minimal JSON‑LD structure based on your input.

You can expand this file manually or continue building it using `semantic-cv add` commands.

The [CLI-reference](./cli-reference.md) page contains a complete list of commands.

### Where should I put my `cv.json`?
SemanticCV doesn’t require a specific repository layout — you can place your `cv.json` in **any** GitHub repository you prefer. The GitHub App listens to all repositories where it’s installed and automatically processes updates to `cv.json` in the default branch.

**Optional convenience:**     
Many users choose to store their cv.json in their personal profile repository:
```
https://github.com/<username>/<username>
```

This is the same repository that powers your GitHub profile README, and since every GitHub user already has one, it’s a simple place to keep a personal CV file without creating a dedicated repo. But this is entirely optional — SemanticCV works equally well with:

- a Jekyll or static‑site repo
- a portfolio repo
- a dedicated cv repo
- any existing project where a CV fits naturally

Use whatever makes sense for your workflow.

## Why JSON‑LD and schema.org?
SemanticCV uses JSON‑LD and the schema.org/Person vocabulary because they’re global, widely adopted standards created by Google, Microsoft, and other major search engines. They’re stable, well‑supported, and designed for long‑term interoperability — which makes your CV portable, future‑proof, and machine‑readable everywhere.
