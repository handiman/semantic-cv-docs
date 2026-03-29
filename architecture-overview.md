
# Architecture Overview
SemanticCV is built around a simple idea: your CV is structured data. Everything else — validation, rendering, publishing — flows from that principle.
This page explains how the system works end‑to‑end.

## High‑Level Architecture
SemanticCV consists of three main components:
### 1. The CLI
- Helps you create, edit, validate, and normalize your JSON‑LD
- Can render HTML locally using the same themes as the site
### 2. The Publishing Service
- Receives updates via GitHub webhooks
- Normalizes and stores your JSON‑LD
- Serves a minimal HTML shell containing your JSON‑LD
### 3. Client‑Side Themes
- JavaScript/Web Component bundles
- Read your JSON‑LD from `<script type="application/ld+json">`
- Render your CV entirely in the browser

This architecture keeps the system fast, flexible, and theme‑agnostic.

## Data Flow
### 1. You write JSON‑LD
Your cv.json is the single source of truth.
### 2. The CLI validates and normalizes
Commands like analyze and normalize ensure your data is clean and schema‑aligned.
### 3. Publishing stores normalized JSON‑LD
When you push to GitHub:
- the publishing service fetches your JSON‑LD
- normalizes it
- stores it
- embeds it into a minimal HTML page
### 4. Themes render client‑side
Each theme is a JavaScript bundle that:
- loads the JSON‑LD from the page
- interprets it according to the schema
- renders the CV using Web Components

This means:
- no server‑side rendering
- no stored HTML
- instant theme switching
- future‑proof rendering

## Why This Architecture?
### 1. JSON‑LD as the source of truth
Structured data is portable, durable, and machine‑readable.
### 2. Client‑side rendering
Themes can evolve independently without breaking published CVs.
### 3. Deterministic normalization
Ensures consistent rendering across themes and versions.
### 4. GitHub‑based publishing
Your CV becomes version‑controlled, reviewable, and diff‑friendly.

## What This Enables
- instant theme previews
- zero server‑side rendering load
- easy future integrations
- deterministic, reproducible CVs
- a clean separation between data and presentation

## Why SemanticCV uses JSON‑LD and schema.org
SemanticCV is built on JSON‑LD and the schema.org/Person vocabulary because they’re **global, industry‑backed standards**. Schema.org was created by Google, Microsoft, Yahoo, and Yandex to provide a shared, structured way of describing people, organizations, and content on the web.

Using these standards means your CV:
- is based on a format recognized across the entire web
- remains compatible with search engines, AI tools, and future platforms
- avoids lock‑in to niche or proprietary schemas
- stays readable and durable for years to come

In short: **your CV becomes structured data that the whole world understands.**


[install]: https://github.com/apps/semantic-cv/installations/new
[default]: https://semantic.cv/preview?theme=minimal
[gallery]: https://semantic.cv/themes