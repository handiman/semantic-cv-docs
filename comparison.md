# Comparing Semantic‑CV to other formats

Semantic‑CV builds on schema.org instead of creating a new proprietary standard, giving you a future‑proof, web‑native way to describe and publish your CV.

This page compares Semantic‑CV with two well‑known alternatives: schema‑resume.org and JSON Resume.

## High‑level Summary

Semantic‑CV is fundamentally different from both schema‑resume.org and JSON Resume:

- **Semantic‑CV** uses **schema.org/Person**, idiomatic JSON‑LD, and minimal conventions.
- **schema‑resume.org** defines a **new, monolithic schema** with its own context, structure, and validation stack.
- **JSON Resume** is a simple JSON format with a fixed schema, not JSON‑LD, and not compatible with schema.org.

All three aim to structure résumé data — but with very different philosophies.

## Comparison Table

### 1. Conceptual Model

| Feature            | Semantic‑CV                    | schema‑resume.org           | JSON Resume                  |
| ------------------ | ------------------------------ | --------------------------- | ---------------------------- |
| Primary data model | **schema.org/Person**          | Custom proprietary schema   | Custom proprietary schema    |
| JSON‑LD            | **Yes (native)**               | Yes (custom context)        | **No**                       |
| Schema philosophy  | Minimal, idiomatic, web‑native | Large, rigid, all‑inclusive | Simple, fixed JSON structure |
| Extensibility      | High (schema.org ecosystem)    | Low–medium                  | Low                          |

### 2. Ecosystem & Interoperability

| Feature                                  | Semantic‑CV | schema‑resume.org | JSON Resume |
| ---------------------------------------- | ----------- | ----------------- | ----------- |
| Web‑native semantics                     | Yes         | Partially         | No          |
| Search engine compatibility              | Excellent   | Limited           | None        |
| Compatibility with existing vocabularies | High        | Low               | Low         |
| Works with existing JSON‑LD tooling      | Yes         | Partially         | No          |

### 3. Validation & Tooling

| Feature             | Semantic‑CV              | schema‑resume.org                         | JSON Resume        |
| ------------------- | ------------------------ | ----------------------------------------- | ------------------ |
| Validation          | Light, optional          | **Heavy (JSON Schema + XSD)**             | JSON Schema        |
| Multi‑language SDKs | Not needed               | **Yes (Go, Python, PHP, Java, Ruby, JS)** | Yes (JS ecosystem) |
| Rendering           | Themes + HTML generation | XSLT (!), custom renderers                | Themes (JS‑based)  |
| Editor              | GitHub‑native workflow   | Web editor                                | CLI + web editor   |

### 4. Philosophy & Design Goals

| Aspect      | Semantic‑CV                | schema‑resume.org             | JSON Resume                  |
| ----------- | -------------------------- | ----------------------------- | ---------------------------- |
| Goal        | Use existing web standards | Create a new universal schema | Provide a simple JSON format |
| Approach    | Convention over invention  | Specification‑heavy           | Developer‑friendly JSON      |
| Complexity  | **Low**                    | **High**                      | Medium                       |
| Flexibility | **Very high**              | Medium                        | Low                          |

### 5. Strengths & Weaknesses
#### Semantic‑CV
##### Strengths
- Built on schema.org (global standard)
- Idiomatic JSON‑LD
- Minimal, flexible, future‑proof
- No proprietary schema to maintain
- Perfect for GitHub‑native workflows
##### Weaknesses
- Requires basic schema.org familiarity
- Less strict validation (by design)

#### schema‑resume.org
##### Strengths
- Very complete schema
- Strong validation (JSON Schema + XSD)
- Multi‑language SDKs
- Online editor and validator
##### Weaknesses
- Reinvents the wheel
- Heavy, rigid, complex
- Not schema.org‑compatible
- XML/XSD stack feels outdated
- Harder to extend or evolve

#### JSON Resume
##### Strengths
- Simple and easy to understand
- Large theme ecosystem
- Popular in the JS community
##### Weaknesses
- Not JSON‑LD
- Not schema.org‑compatible
- Limited extensibility
- Schema is frozen and opinionated

## When to choose what?
### Choose Semantic‑CV if you want:
- A modern, web‑native, schema.org‑based CV
- JSON‑LD that works with the semantic web
- Maximum flexibility with minimal constraints
- A GitHub‑native publishing workflow
- Clean, professional HTML themes

## Choose schema‑resume.org if you want:
- Heavy validation
- A strict, enterprise‑style schema
- Multi‑language SDKs
- XML/XSD compatibility

## Choose JSON Resume if you want:
- A simple JSON format
- A quick CLI workflow
- A large JS theme ecosystem

## Final positioning
__Semantic‑CV is not a new résumé schema.__  
It is a lightweight convention for expressing CV data using __schema.org/Person__ and idiomatic __JSON‑LD__, making it fully compatible with the semantic web, search engines, and existing tooling.

Unlike schema‑resume.org and JSON Resume, Semantic‑CV does not invent a new proprietary structure. It builds on global standards and keeps your data portable, future‑proof, and easy to publish.

__Plus we have a kitten__   
<img src="https://assets.semantic.cv/semantikitten-napping.png" alt="Sleepy Semantikitten" height="100" style="margin-left: 20px;margin-top:20px;" />