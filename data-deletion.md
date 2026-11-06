# Data Deletion (semantic.cv)

_Last updated: 2026‑11‑07_

This page explains how to remove your data from semantic.cv and what data can and cannot be deleted.

---

## 1. CV Data
semantic.cv stores a copy of your `cv.json` only when it appears in a push event from your GitHub repository.

You can delete your hosted CV in any of the following ways:

### Remove or rename `cv.json`
If you delete or rename the `cv.json` file in your repository, semantic.cv will automatically remove the stored copy.

### Uninstall the GitHub App
If you uninstall or suspend the Semantic‑CV GitHub App, all stored CV data associated with your installation is removed automatically.

semantic.cv does not store older versions of your CV.

### Plan record
If you are on a paid or granted plan, we keep a small record of your GitHub username, your plan and its start and end dates after your CV is deleted. This lets your plan apply again if you publish a new CV.

- On the free plan, no such record is kept.
- While your CV is published, the record is kept even if your plan has ended, so that renewing it picks up where you left off.
- Once you have no published CV (you deleted it or uninstalled the GitHub App), the record is removed when your plan has ended and a grace period of 7 days has passed. A weekly cleanup removes it if that happened without you deleting anything.
- You can ask us to remove it at any time, see section 4.

---

## 2. Authentication Data
semantic.cv offers optional authentication (e.g., GitHub sign‑in) for accessing certain features.

semantic.cv does not store any authentication‑related data on the server.  
Authentication is handled entirely through a session cookie, which is removed automatically when you sign out or when the session expires.

Apart from the plan record described in section 1, no additional authentication data, preferences, or metadata are stored by semantic.cv.

---

## 3. Logs
semantic.cv stores minimal server logs for security and debugging.  
These logs do not include CV content and are automatically purged on a rolling basis.

---

## 4. Requesting Data Deletion
To request deletion of your plan record, authentication data, non‑essential metadata, or other removable information, contact:

**privacy@semantic.cv**

Include:

- your GitHub username  
- the repository connected to semantic.cv  
- a description of what you want removed  

We may ask for additional information to verify the request.

---

## 5. Summary
You can delete your data by:

- removing or renaming `cv.json`  
- uninstalling the GitHub App  
- contacting us to remove your plan record, authentication or UI data  


---
