# Privacy Policy (semantic.cv)

_Last updated: 2026‑11‑07_

semantic.cv is a service for rendering and hosting CVs based on the Semantic‑CV format. This policy explains what information is collected, how it is used, and how it is handled.

---

## 1. Information We Collect

### CV data
semantic.cv does not fetch any files when the GitHub App is installed.

When your repository sends a push event, semantic.cv checks whether the changes include a `cv.json` file.  
If `cv.json` was added or modified, we fetch the file and store a copy so your CV can be rendered quickly and served reliably.  
If `cv.json` was removed or renamed, the stored copy is deleted.

We do not store older versions of your CV.  
We do not modify your repository.

### Service record
To serve your CV at `semantic.cv/<username>`, we keep a record of your GitHub username, the repository and branch your `cv.json` is published from, and the plan (tier) you are on.

For paid or granted plans, we also keep the date the plan started and the date it ends. This record is kept separately from your CV so that your plan is not lost if you delete your CV and publish it again later.

### Account & authentication data
semantic.cv may offer optional authentication (e.g., GitHub sign‑in) to access certain features such as theme previews.  
If you choose to authenticate, we may receive:

- your GitHub user ID  
- your GitHub username  
- your public profile information  
- your email address (if provided by GitHub)

Authentication is optional and not required to use the core CV hosting functionality.  
It is only used to provide features that require identifying you.

### Logs
We store minimal server logs for security and debugging.  
These logs do not include CV content.

---

## 2. How We Use Your Information

We use your information to:

- fetch and store your CV so it can be rendered and hosted  
- keep your public CV page up to date  
- allow you to preview themes when authenticated  
- maintain and improve the service  
- prevent abuse and ensure security  

We do not use your CV data for analytics, training, or profiling.

---

## 3. Cookies

We use a small number of cookies that are strictly necessary for:

- authentication (session cookie)

We do not use tracking or analytics cookies.  
See the [Cookie Policy](./cookie-policy.md) for details.

---

## 4. Data Sharing

We share data only when necessary to operate the service:

- **GitHub** — to receive repository updates, installation events, and (if you authenticate) basic profile information  

We do not share personal data with third parties for marketing.

---

## 5. Data Retention

- A copy of your latest `cv.json` is stored on semantic.cv as long as the GitHub App remains installed.  
- When you uninstall or suspend the GitHub App, your stored CV is removed automatically.  
- Your repository and branch are removed together with your CV.  
- If you are on a paid or granted plan, a record of your GitHub username, plan and its start and end dates is kept after your CV is deleted, so that your plan applies if you publish again. It is kept as long as your CV is published, even if your plan has ended, so that renewing it picks up where you left off. Once you have no published CV, it is removed when your plan has ended and a grace period of 7 days has passed, either when you delete your CV or by a weekly cleanup. If you are on the free plan, no such record is kept.  
- Authentication data is retained only as long as needed to provide the feature you are using.  
- Session cookies are removed when you sign out.

---

## 6. Your Rights

You may:

- **Uninstall the Semantic‑CV GitHub App at any time.**  
  This immediately revokes all permissions and removes your stored CV from semantic.cv.

- **Modify or remove your `cv.json` file in your GitHub repository at any time.**  
  semantic.cv will update or remove the stored copy accordingly.

- **Request deletion of your plan record**, or other non‑essential data  
  such as cached rendering metadata or UI preferences, by contacting us. We will remove it, unless we must keep it for legal reasons such as bookkeeping.

For information on how to remove your data, see our [data deletion](./data-deletion.md) page.  

semantic.cv does not create traditional standalone user accounts.  
Authentication is optional and only used to provide specific features.

---

## 7. Contact

For questions about privacy or data handling, contact:  
**info@semantic.cv**
