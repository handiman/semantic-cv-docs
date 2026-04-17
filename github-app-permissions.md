# GitHub App Permissions (semantic.cv)

_Last updated: 2026‑04‑17_

The Semantic‑CV GitHub App uses a minimal set of permissions.  
This page explains what the app can access, why it needs those permissions, and how it behaves.

---

## 1. Repository Permissions

### **Repository contents: Read‑only**
The app can read repository contents, but only receives information included in GitHub event payloads.

semantic.cv uses this permission to:

- detect when `cv.json` appears in a push event  
- fetch the updated `cv.json` file  
- remove the stored copy if `cv.json` is deleted or renamed  

The app does **not**:

- write to your repository  
- modify files  
- commit changes  
- scan your repository outside of push events  

semantic.cv only fetches `cv.json` when it is explicitly included in the event data.

---

## 2. Webhooks / Events

The app subscribes to:

### **Push events**
Used to:

- detect when `cv.json` is added, modified, or removed  
- update or delete the stored copy accordingly  
- trigger re‑rendering of your hosted CV  

No other events are required.

---

## 3. No Access to Other Data

The Semantic‑CV GitHub App does **not** request:

- write permissions  
- admin permissions  
- access to issues, pull requests, or workflows  
- access to organization settings  
- access to private user data  
- access to other repositories you did not select  

You choose which repositories the app can access during installation.

---

## 4. Least‑Privilege Design

The app is intentionally designed with a minimal permission footprint:

- **read‑only**  
- **single event type**  
- **single file of interest (`cv.json`)**  
- **no background scanning**  
- **no write operations**  

semantic.cv only stores the latest version of your `cv.json` and nothing else.

---

## 5. Removing Access

You can uninstall the GitHub App at any time from:

**https://github.com/settings/installations**

Uninstalling the app:

- immediately revokes all permissions  
- removes your stored CV from semantic.cv  
- stops all future updates  

---

## 6. Questions

For questions about permissions or security, contact:  
**security@semantic.cv**
