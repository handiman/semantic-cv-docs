# Getting Started

Semantic‑CV helps you write and publish your CV as structured JSON‑LD. This guide walks you through the quickest path from installation to a published CV, whether you prefer working locally or using the hosted workflow.

## 1. Install the CLI
Semantic‑CV is distributed as an npm package.

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
- name — your full name
- jobTitle — your current role or professional identity
- description — a short summary or headline`

These aren’t strictly required by `schema.org/Person`, but they are the foundation of a meaningful CV. Once you’ve answered the prompts, the CLI generates a `cv.json` file containing a clean, minimal JSON‑LD structure based on your input.

You can expand this file manually or continue building it using `semantic-cv add` commands.

The [CLI-reference](./cli-reference.md) page contains a complete list of commands.

## Why JSON‑LD and schema.org?
Semantic‑CV uses JSON‑LD and the schema.org/Person vocabulary because they’re global, widely adopted standards created by Google, Microsoft, and other major search engines. They’re stable, well‑supported, and designed for long‑term interoperability — which makes your CV portable, future‑proof, and machine‑readable everywhere.
