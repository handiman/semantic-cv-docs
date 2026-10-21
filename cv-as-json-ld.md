# CV as JSON‑LD

A practical guide to representing your résumé as structured data

A CV written in __JSON‑LD__ is portable, machine‑readable, and easy to transform into any layout or format. Instead of maintaining a fixed document, you describe yourself using structured data based on the Schema.org vocabulary. Tools like SemanticCV can then render that data into a clean résumé you can preview locally or publish online.

This page explains what a JSON‑LD CV looks like, why it’s useful, and how to model common CV sections using Schema.org.

## Why write a CV in JSON‑LD?

### Portability

Your CV becomes structured data instead of a fixed layout. It can be rendered into any theme or exported into any format without rewriting content.

### Future‑proofing

JSON‑LD and Schema.org are widely adopted standards used by search engines, AI systems, and structured‑data pipelines.

### Machine‑readability

A JSON‑LD CV can be parsed, indexed, and processed automatically — useful for automation, integrations, and long‑term storage.

### Version‑control friendly

A CV expressed as JSON‑LD fits naturally into Git, CI pipelines, and developer workflows.

## What JSON‑LD looks like in practice

A JSON‑LD CV starts with a Person object.   
Here’s an example based on a real SemanticCV document:   

```json
{
  "@context": "https://schema.org",
  "@type": "Person",

  "name": "Henrik Becker",
  "jobTitle": "Senior Software Engineer",
  "description": "Henrik Becker is an experienced .Net developer and solution architect dedicated to delivering quality software practicing Agile Processes, Test Driven Development, applying SOLID principles and a healthy dose of dad-jokes.",
  "image": "https://www.henrikbecker.net/assets/img/landscape-800x534.jpg",
  "url": "https://www.henrikbecker.net",

  "sameAs": [
    "https://github.com/handiman",
    "https://www.linkedin.com/in/prettygoodprogrammer/"
  ]
}
```
This establishes identity, links, and a short summary.

### Skills and knowledge

Skills can be represented as simple string lists:

```json
"skills": [
  ".NET",
  ".NET Aspire",
  "Microsoft Orleans",
  "Node",
  "GitHub Actions",
  "Azure DevOps",
  "C#",
  "TypeScript",
  "JavaScript"
],
"knowsAbout": [
  "Domain Driven Design",
  "Solution Architecture",
  "System Integration",
  "Event Sourcing",
  "Event Driven Systems",
  "Azure",
  "Node",
  "SOLID",
  "Agile Methodologies",
  "CI/CD"
]
```

This keeps the structure compact and easy to maintain.

### Certifications

Schema.org includes a `Certification` type:

```json
"hasCertification": [
  {
    "@type": "Certification",
    "name": "Microsoft Certified: Azure Developer Associate",
    "issuedBy": "Microsoft",
    "validFrom": "2021-06-24"
  }
]
```

### Education in JSON‑LD

Education can be modeled using Role to include dates and descriptions:

```json
"alumniOf": [
  {
    "@type": "Role",
    "alumniOf": {
      "@type": "EducationalOrganization",
      "name": "Komvux Lidingö"
    },
    "description": "Municipal adult education",
    "startDate": "1995-08-01",
    "endDate": "1997-06-18"
  }
]
```

Using Role keeps education, work experience and projects structurally consistent.

### Work experience using `Role`

Work experience is also represented using Role.   
This allows you to attach:   

- `roleName`
- `description` 
- `startDate`/`endDate` 
- a reference to either an __Organization__ or a __Project__

#### Example: Project‑based work

```json
{
  "@type": "Role",
  "roleName": "Lead Developer",
  "description": "A schema.org‑first CV generator for developers built with Nodejs and Cloudflare workers.",
  "startDate": "2026-03-26",
  "worksFor": {
    "@type": "Project",
    "name": "Semantic CV"
  }
}
```

#### Example: Employment at an organization

```json
{
  "@type": "Role",
  "roleName": "Senior Software Engineer",
  "description": "I joined Betsson as a consultant and later transitioned directly into a full‑time role...",
  "startDate": "2023-12-18",
  "endDate": "2025-12-05",
  "worksFor": {
    "@type": "Organization",
    "name": "Betsson Group AB"
  }
}
```

#### Example: Consulting engagement

```json
{
  "@type": "Role",
  "roleName": "IT Consultant, Senior Software Engineer",
  "description": "Strengthened architecture, performance, and team capability across Betsson’s gamification systems through hands‑on engineering and candidate assessments.",
  "startDate": "2021-10-21",
  "endDate": "2025-12-05",
  "worksFor": {
    "@type": "Project",
    "name": "Betsson Group"
  }
}
```

#### A complete JSON‑LD CV example

Here is a shortened but representative example combining all sections:

```json
{
  "@context": "https://schema.org",
  "@type": "Person",

  "name": "Henrik Becker",
  "jobTitle": "Senior Software Engineer",
  "description": "Henrik Becker is an experienced .Net developer and solution architect dedicated to delivering quality software practicing Agile Processes, Test Driven Development, applying SOLID principles and a healthy dose of dad-jokes.",
  "image": "https://www.henrikbecker.net/assets/img/landscape-800x534.jpg",
  "url": "https://www.henrikbecker.net",

  "sameAs": [
    "https://github.com/handiman",
    "https://www.linkedin.com/in/prettygoodprogrammer/"
  ],

  "skills": [
    ".NET", ".NET Aspire", "Microsoft Orleans",
    "Node", "GitHub Actions", "Azure DevOps",
    "C#", "TypeScript", "JavaScript"
  ],

  "hasCertification": [
    {
      "@type": "Certification",
      "name": "Microsoft Certified: Azure Developer Associate",
      "issuedBy": "Microsoft",
      "validFrom": "2021-06-24"
    }
  ],

  "alumniOf": [
    {
      "@type": "Role",
      "alumniOf": { "@type": "EducationalOrganization", "name": "Komvux Lidingö" },
      "description": "Municipal adult education",
      "startDate": "1995-08-01",
      "endDate": "1997-06-18"
    }
  ],

  "worksFor": [
    {
      "@type": "Role",
      "roleName": "Lead Developer",
      "description": "A schema.org‑first CV generator for developers built with Nodejs and Cloudflare workers.",
      "startDate": "2026-03-26",
      "worksFor": { "@type": "Project", "name": "Semantic CV" }
    },
    {
      "@type": "Role",
      "roleName": "Senior Software Engineer",
      "description": "I joined Betsson as a consultant and later transitioned directly into a full‑time role...",
      "startDate": "2023-12-18",
      "endDate": "2025-12-05",
      "worksFor": { "@type": "Organization", "name": "Betsson Group AB" }
    }
  ]
}
```

## Validating your JSON‑LD

Useful tools:
- __[Semantic CV CLI](https://www.npmjs.com/package/semantic-cv)__
- __Schema.org Validator__
- __JSON‑LD Playground__
- __Google Rich Results Test__

These help ensure the structure is correct and the data is interpretable.

## Using SemanticCV
SemanticCV applies these conventions to:
- keep CVs consistent
- separate content from presentation
- support multiple themes
- allow local preview and publishing
- keep the JSON‑LD clean and portable

You write your CV once as structured data.   
SemanticCV handles the rendering.   