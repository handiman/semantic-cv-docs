# SemanticCV
SemanticCV is a structured, schema.org‑based way to write, version, and publish your CV. Instead of wrestling with layout tools, you describe yourself as JSON‑LD, and SemanticCV takes care of validation, normalization, and rendering.

You can use SemanticCV in two ways: through the CLI or by publishing directly to this website.

## CLI Workflow
The SemanticCV CLI helps you create and maintain your CV as valid [`schema.org/Person`][schema]
JSON‑LD. It provides commands to:
- Add and edit sections of your CV
- Analyze your data to ensure it follows the schema
- Normalize fields for consistency
- Render your CV as HTML using any of the included free themes
- Generate an ATS‑friendly plain‑text version
The CLI writes the rendered output to disk. From there, you can host it yourself, print to PDF, or integrate it into your own site or workflow

## Hosted Workflow
If you prefer a fully automated publishing flow, you can publish your CV directly to semantic.cv.
- Install the [SemanticCV GitHub App][install]
- Push your CV JSON‑LD to a repository the app has access to

SemanticCV will normalize your JSON‑LD and store it. Your CV will then be available at:
https://semantic.cv/<your-github-username\>


Whenever you push updates, your published CV is automatically updated.

### How Rendering Works
The site uses the JSON‑LD as the single source of truth:
- Your normalized JSON‑LD is embedded in the page as
`<script type="application/ld+json">…</script>`
- Themes are rendered server‑side to transform JSON‑LD into HTML
- The final HTML is served directly with full styling applied

## Themes
Themes control the visual presentation of your CV. SemanticCV includes several free themes, each with its own layout, typography, and personality.

By default, your CV uses the [minimal theme][default].

To choose a different theme, add an `theme` field to your JSON‑LD:
```json
{
  "@context": [
    "https://schema.org",
    "https://semantic.cv/context/latest.jsonld"
  ],
  "@type": "Person",
  "theme": "boiling-diesel",
  // … more fields
}
```


You can browse available themes in the [Theme Gallery][gallery].

## Why JSON‑LD?
JSON‑LD turns your CV into structured data. That means:
- Your CV becomes machine‑readable and semantically meaningful
- Validation and normalization are deterministic
- Themes can render your data consistently without guessing
- Your CV can be version‑controlled like any other code artifact
- Future integrations (search, indexing, automation) become trivial

In short: JSON‑LD makes your CV portable, durable, and unambiguous.


## Next Steps
- Install the CLI
  ```sh
  npm install semantic-cv
  ```
- Install the [GitHub App][install]
- Explore the [theme gallery][gallery]
- Start describing yourself in JSON‑LD

SemanticCV takes care of the rest.


[schema]: https://schema.org/Person
[install]: https://github.com/apps/semantic-cv/installations/new
[gallery]: https://semantic.cv/themes
[default]: https://semantic.cv/preview?theme=minimal
