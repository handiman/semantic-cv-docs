# Publishing Guide

SemanticCV can publish your CV directly to the web using the SemanticCV GitHub App. This guide explains how the publishing flow works, how to set it up, and what happens behind the scenes.

## Overview
Publishing with SemanticCV is designed to be effortless:
- You write your CV as JSON‑LD (cv.json)
- You push it to a GitHub repository
- The SemanticCV GitHub App normalizes and stores your JSON‑LD
- Your CV becomes available at: 
```
https://semantic.cv/<your-github-username>
```

Whenever you push updates, your published CV updates automatically.

## 1. Install the GitHub App
Install the SemanticCV GitHub App:
→ [][install]

During installation, you choose which repositories the app can access.   
You can grant access to:
- a single repository
- multiple repositories
- or all repositories (not required)

You can change this at any time.

## 2. Add Your CV to a Repository
Create a repository (or use an existing one) and add your cv.json file to the root:
```
my-cv-repo/
└── cv.json
```

Commit and push:
```sh
git add cv.json
git commit -m "Add my CV"
git push
```

## 3. Publishing and Updates
After you push:
- The GitHub App receives a webhook
- SemanticCV fetches your `cv.json`
- It validates and normalizes the JSON‑LD
- The normalized JSON‑LD is stored
- Your public CV page is updated

This usually takes a few seconds.   
Your published CV will always reflect the **latest commit** on the default branch.

## 4. Choosing a Theme
To select a theme for your published CV, add an @theme field to your JSON‑LD:
{
  "@context": "https://schema.org",
  "@type": "Person",
  "@theme": "minimal"
}


If no theme is specified, the [default theme][default] is used.
You can browse available themes in the [Theme Gallery][gallery].

## 5. Privacy and Visibility
Your published CV is publicly accessible at:
```
https://semantic.cv/<your-github-username>
```

If you want to unpublish your CV:
- remove `cv.json` from the repository, or
- revoke the GitHub App’s access to the repository

## 6. Troubleshooting
### My CV isn’t updating
Check that:
- the GitHub App has access to the repository
- `cv.json` is in the repository root
- you pushed to the default branch
- your JSON‑LD is valid (run `semantic-cv analyze`)

### My theme isn’t applied
Ensure:
- the `@theme` field is present
- the theme name matches the gallery exactly

[install]: https://github.com/apps/semantic-cv/installations/new
[default]: https://semantic.cv/preview?theme=minimal
[gallery]: https://semantic.cv/themes