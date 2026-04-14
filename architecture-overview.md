# Architecture Overview
Semantic‑CV is built on a simple idea: **your CV is structured data**. Everything else — validation, normalization, rendering — flows from that foundation. This page describes how the system works end‑to‑end in its current form.

## High‑level structure
Semantic‑CV consists of three cooperating layers that share the same rendering pipeline:

### 1. The CLI
- Validates and normalizes your JSON‑LD
- Renders HTML locally using the same themes as the hosted service
- Uses a WASM‑powered HTMLRewriter to assemble the final document

### 2. The Publishing Service
- Receives updates via GitHub webhooks
- Normalizes and stores your JSON‑LD
- Renders HTML server‑side using the same theme pipeline
- Serves the final HTML directly (no client‑side rendering required)

### 3. Theme Classes
- Each theme is a class inheriting from a shared base Theme class
- Implements `renderHTML`, `renderCSS`, and `renderJS`
- Produces deterministic output based solely on your JSON‑LD
- May optionally include a Web Component for client‑side enhancement

This architecture keeps rendering consistent across environments while remaining theme‑agnostic and future‑proof.

## Data flow
### 1. You create your JSON‑LD
You can manage your CV in two ways:

- **Using the CLI**, which gives you commands like `init`, `add`, `set`, `analyze`, and `normalize` to keep everything tidy and structurally correct.

- **Or by hand**, editing raw JSON‑LD in your favourite text editor. This is fully supported… but unless you genuinely enjoy hand‑crafting nested objects at 2 AM, the CLI is usually the more pleasant option.

Your `cv.json` is the single source of truth, regardless of how you maintain it.

### 2. The CLI validates and normalizes
Commands like `analyze` and `normalize` ensure your data is structurally correct, schema‑aligned, and ready for rendering.

### 3. Publishing stores normalized JSON‑LD
When you push to GitHub:
- the publishing service fetches your JSON‑LD
- normalizes it
- renders your CV using the same theme pipeline as the CLI
- serves the final HTML

### 4. Themes render server‑side
Each theme class:
- receives the normalized Person object
- generates HTML, CSS, and JS as strings
- relies on the HTMLRewriter pipeline to assemble the final document

Client‑side Web Components are optional and used only for enhancements.

## Rendering pipeline
Semantic‑CV uses a **runtime‑neutral HTML rewriting pipeline**. Both the CLI and the publishing service follow the same steps:

1. Load and normalize the JSON‑LD.
1. Instantiate the selected theme class.
1. Call the theme’s `renderHTML`, `renderCSS`, and `renderJS` methods.
1. Register HTMLRewriter hooks to inject:
    - OpenGraph and Twitter metadata
    - JSON‑LD
    - analysis results
    - theme CSS and JS
    - the theme’s HTML fragment
    - an optional enhancement Web Component
1. Feed a deterministic HTML skeleton into the transformer.
1. Return the fully rewritten HTML.

Two transformer implementations exist:
- WorkerTransformer (Cloudflare Worker, native HTMLRewriter)
- NodeTransformer (CLI, html‑rewriter‑wasm)

Both expose the same interface, so themes remain runtime‑agnostic.

## Theme architecture
Themes are implemented as classes that inherit from a shared base Theme class. The base class provides:
- asset loading
- shared helpers
- a consistent lifecycle
- a stable contract for the rendering pipeline

Each concrete theme overrides:
- `renderHTML(person)`
- `renderCSS(person)`
- `renderJS(person)`

Themes are deterministic, side‑effect‑free, and do not manipulate the DOM. They may optionally include a Web Component that enhances the rendered page after load.

## Why this architecture?
### JSON‑LD as the source of truth
Structured data is portable, durable, and machine‑readable.

### Deterministic server‑side rendering
Themes produce stable output across environments, with no client‑side rendering required.

### Runtime‑neutral HTML rewriting
The same pipeline runs in both the CLI and the publishing service.

### Clean separation of concerns
Data, rendering, and enhancement are isolated and composable.

### Future‑proof theme system
Themes can evolve independently without breaking published CVs.

## What this enables
- consistent rendering across CLI and hosted service
- deterministic, reproducible output
- instant theme previews
- optional client‑side enhancements
- a stable foundation for future theme packs