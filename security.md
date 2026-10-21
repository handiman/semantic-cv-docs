# Security (semantic.cv)

_Last updated: 2026‑10‑21_

semantic.cv is designed to be a minimal, privacy‑focused service.  
This page describes the security measures in place to protect your data.

---

## 1. Data Access and Permissions
semantic.cv uses a GitHub App with **read‑only** access to your repository.  
The app only receives information included in push events.

- We do **not** write to your repository  
- We do **not** request access to other files  
- We only fetch `cv.json` when it appears in the push event payload  
- If `cv.json` is removed or renamed, the stored copy is deleted automatically  

semantic.cv follows the principle of **least privilege**.

---

## 2. Authentication
Some features may require optional authentication (e.g., GitHub sign‑in).

- semantic.cv does **not** store authentication data on the server  
- Authentication is handled entirely through a short‑lived session cookie  
- No OAuth tokens or personal profile data are stored by semantic.cv  

Authentication is optional and not required to host a CV.

---

## 3. Storage and Hosting
semantic.cv stores only:

- the latest version of your `cv.json` (if present in push events)  

We do **not** store:

- older versions of your CV  
- analytics data  
- tracking data  
- user preferences  
- server‑side session data  

All data is stored in secure, access‑controlled environments.

---

## 4. Transport Security
All communication with semantic.cv uses **HTTPS** with modern TLS.  
Unencrypted HTTP requests are redirected to HTTPS.

---

## 5. Logging
semantic.cv keeps minimal server logs for security and debugging.

- Logs do **not** contain CV content  
- Logs are automatically purged on a rolling basis  
- Logs are not used for analytics or tracking  

---

## 6. Vulnerability Reporting
If you discover a security issue, please contact:

**security@semantic.cv**

We appreciate responsible disclosure.

---

## 7. Summary
semantic.cv is built with a minimal attack surface:

- read‑only GitHub App  
- no server‑side authentication storage  
- no analytics or tracking  
- no unnecessary data retention  
- HTTPS everywhere  

This approach reduces risk and keeps your data safe by design.

---
