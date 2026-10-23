# How to Represent a CV in JSON‑LD (2026 Guide)

A practical, copy‑paste‑ready introduction to machine‑readable CVs using Schema.org and JSON‑LD.

Representing a CV in **JSON‑LD** makes it portable, machine‑readable, and compatible with modern search engines, AI systems, and structured‑data pipelines. This guide walks through a clean, developer‑friendly way to express CV data using Schema.org. It also shows how SemanticCV applies these conventions in a consistent, predictable format that can be rendered into HTML, PDF, or any other output.

The goal isn’t to define _the_ canonical JSON‑LD CV format but to present a practical, well‑structured approach that works reliably in real‑world tooling.

## Why JSON‑LD for CVs?

JSON‑LD is a good fit for CVs because it is:

- **machine‑readable**
- **schema‑validated**
- **easy to transform into HTML, PDF, Markdown, etc.**
- **compatible with search engines and AI systems**
- **stable over time**

Unlike ad‑hoc JSON formats, JSON‑LD is designed to describe _meaning_, not just structure. That makes it ideal for representing identity, experience, skills, and education.

## Core Schema.org Types for CVs

A CV maps naturally to existing Schema.org vocabulary:

| Concept         | Schema.org Type                               |
| --------------- | --------------------------------------------- |
| Person          | `Person`                                      |
| Project         | `Project` (wrapped in `Role`)                 |
| Work experience | `Organization` (wrapped in `Role`)            |
| Education       | `EducationalOrganization` (wrapped in `Role`) |
| Skills          | `Text` or `DefinedTerm`                       |
| Certifications  | `Certification`                               |

### The Person Object (Root)

Every CV begins with a `Person`.   
Here is a real example based on the SemanticCV format:
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
This establishes identity, links, and a short professional summary.

### Skills and Knowledge

SemanticCV uses simple string lists for skills and domain knowledge:

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
This keeps the JSON‑LD compact and easy to edit.


### Certifications
Schema.org includes a `Certification` type:

```json
"hasCertification": [
  {
    "@type": "Certification",
    "name": "Microsoft Certified: Azure Developer Associate",
    "issuedBy": "Microsoft",
    "validFrom": "2021-06-24"
  },
  {
    "@type": "Certification",
    "name": "MCSA: Web Applications - Certified 2016",
    "issuedBy": "Microsoft",
    "validFrom": "2016-09-26"
  }
]
```

### Modeling Education with `Role`

Education is represented using `Role`, which allows dates and descriptions to be included consistently:

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
  },
  {
    "@type": "Role",
    "alumniOf": {
      "@type": "EducationalOrganization",
      "name": "Kulturama"
    },
    "description": "Music",
    "startDate": "1992-08-01",
    "endDate": "1993-08-01"
  }
]
```

Using `Role` keeps education, work experience and projects structurally aligned.

### Modeling Work Experience with `Role`
Work experience is also represented using `Role.`   
This pattern supports:
- `roleName`
- `description`
- `startDate / endDate`
- `keywords`
- a reference to either an __Organization__ or a __Project__

#### Skills per role with `keywords`

Use `keywords` on the `Role` in `worksFor` to list the technologies and skills used in that job or project. Each keyword is a `DefinedTerm`; plain strings are converted to that form when the CV is normalized, and `semantic-cv add keywords` adds them for you.

```json
"keywords": [
  { "@type": "DefinedTerm", "name": "C#" },
  { "@type": "DefinedTerm", "name": "Azure Service Bus" }
]
```

Keywords belong on the `Role` in `worksFor`, not on the inner `Organization` or `Project`, since they describe what you did in that role. They are not used on education (`alumniOf`). The top-level `skills` list is still the place for your overall skill set.

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
  },
  "keywords": [
    { "@type": "DefinedTerm", "name": "Node.js" },
    { "@type": "DefinedTerm", "name": "Cloudflare Workers" }
  ]
}
```

#### Why `Role`?
It allows you to attach:
- role names
- descriptions
- start/end dates
- skills used in the role, as `keywords`
- and a reference to either an Organization or a Project

### Projects vs Organizations

Your CV uses both types depending on the context:

#### Projects
```json
"worksFor": { "@type": "Project", "name": "Adlibris Storefront" }
```

#### Organizations
```json
"worksFor": { "@type": "Organization", "name": "Magine TV AB" }
```

Both are valid Schema.org types. This distinction separates project‑based work from employment relationships.   


### A Complete JSON‑LD CV Example

Here is a shortened but accurate SemanticCV‑style CV.

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
      "worksFor": { "@type": "Project", "name": "Semantic CV" },
      "keywords": [
        { "@type": "DefinedTerm", "name": "Node.js" },
        { "@type": "DefinedTerm", "name": "Cloudflare Workers" }
      ]
    },
    {
      "@type": "Role",
      "roleName": "Senior Software Engineer",
      "description": "I joined Betsson as a consultant and later transitioned directly into a full‑time role...",
      "startDate": "2023-12-18",
      "endDate": "2025-12-05",
      "worksFor": { "@type": "Organization", "name": "Betsson Group AB" }
    }
  ],

  "theme": "boiling-diesel"
}
```

## Validating Your JSON‑LD 
Useful tools:
- __[Semantic CV CLI](https://www.npmjs.com/package/semantic-cv)__
- __Schema.org Validator__
- __JSON‑LD Playground__
- __Google Rich Results Test__

These help catch structural issues and typos.


## Summary

JSON‑LD provides a flexible, expressive way to represent CVs using Schema.org. By combining types like `Person`, `Role`, `Organization`, `Project`, and `EducationalOrganization`, you can build a structured CV that works well across search engines, AI systems, and rendering pipelines.

SemanticCV follows these conventions to keep CVs consistent and easy to transform into different formats.