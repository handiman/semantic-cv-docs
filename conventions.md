# Conventions by CV Area

Recommended fields and how to use them.

## Identity

| Field          | Purpose                                          |
| -------------- | ------------------------------------------------ |
| `name`         | Full name (required)                             |
| `jobTitle`     | Current role or professional identity (required) |
| `description`  | Short summary / professional pitch (required)    |
| `image`        | Profile photo (URL)                              |
| `url`          | Personal website or portfolio                    |
| `workLocation` | Where you're based                               |

## Contact & Online Presence

| Field       | Purpose                                                                                   |
| ----------- | ----------------------------------------------------------------------------------------- |
| `email`     | Email address                                                                             |
| `telephone` | Phone number                                                                              |
| `address`   | Postal address                                                                            |
| `sameAs`    | List of authoritative external profiles (GitHub, LinkedIn, Mastodon, StackOverflow, etc.) |

Example:

```json
"sameAs": [
  "https://github.com/username",
  "https://www.linkedin.com/in/username"
]
```

## Work Experience

Use `worksFor` to represent both current and past employment, consulting, and long‑term engagements.

Example:

```json
"worksFor": [
  {
    "@type": "Role",
    "roleName": "Senior Software Engineer",
    "startDate": "2023-07-01",
    "description": "Led development of the Y platform.",
    "worksFor": {
      "@type": "Organization",
      "name": "Acme Ltd."
    }
  },
  {
    "@type": "Role",
    "roleName": "Senior Software Engineer",
    "startDate": "2020-01-01",
    "endDate": "2023-06-30",
    "description": "Led development of the X platform.",
    "worksFor": {
      "@type": "Organization",
      "name": "Acm  e Inc."
    }
  }
]
```

## Education

Use `alumniOf` for degrees, programs, courses, and training.

```json
"alumniOf": [
  {
    "@type": "Role",
    "startDate": "2015-09-14",
    "endDate": "2017-07-05",
    "description": "BSc in Computer Science",
    "alumniOf": {
      "@type": "EducationalOrganization",
      "name": "KTH Royal Institute of Technology"
    }
  }
]
```

## Projects

Use `worksFor` with inner `"@type": "Project"` for open source projects, volunteer assignments etc.

```json
"worksFor": [
  {
    "@type": "Role",
    "name": "Lead Developer",
    "startDate": "2026-03-01",
    "worksFor": {
      "@type": "Project",
      "name": "Semantic CV"
    }
  }
]
```

## Skills & Competence

### Knowledge Areas (broad categories)

Use `knowsAbout`:

```json
"knowsAbout": [
  "Distributed Systems",
  "Cloud Architecture"
]
```

### Specific skills (tools, languages, frameworks)

Use `skills`:

```json
"skills": [
  ".NET",
  "Nodejs",
  "Docker",
  "Azure"
]
```

## Languages

Use `knowsLanguage`:

```json
"knowsLanguage": [
  "sv-SE",
  "en-US"
]
```

## Certifications

Use `hasCertification` or `hasCredential`:

```json
"hasCertification": [
  {
    "@type": "Certification",
    "name": "Microsoft Certified: Azure Developer Associate",
    "issuedBy": {
      "@type": "Organization",
      "name": "Microsoft"
    },
    "validFrom": "2021-06-24",
    "expires": "2026-06-24"
  }
],
"hasCredential": [
  {
    "@type": "EducationalOccupationalCredential",
    "name": "AWS Solutions Architect Associate"
  }
]
```

## Achievements & Milestones

Use `lifeEvent` for:

- awards
- publications
- speaking engagements
- career milestones
- notable events

```json
"lifeEvent": [
  {
    "@type": "Event",
    "name": "Speaker at Nordic.js 2023"
  }
]
```

## Theme

semantic-cv adds one custom field: `@theme`:

```json
"@theme": "minimal"
```

This selects the rendering theme.  
It does **not** affect the data model.

[country]: https://schema.org/Country
