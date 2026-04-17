# Privacy Policy (semantic.cv)

_Last updated: 2026‑04‑17_

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

### Account & authentication data
semantic.cv may offer optional authentication (e.g., GitHub sign‑in) to access certain features such as theme previews or paid features.  
If you choose to authenticate, we may receive:

- your GitHub user ID  
- your GitHub username  
- your public profile information  
- your email address (if provided by GitHub)

Authentication is optional and not required to use the core CV hosting functionality.  
It is only used to provide features that require identifying you.

### Subscription data
If you purchase a subscription, we store:

- your Stripe customer ID  
- your current subscription status (“Pro” or “Free”)

semantic.cv does **not** store payment card details. These are handled securely by Stripe.

### Logs
We store minimal server logs for security and debugging.  
These logs do not include CV content.

---

## 2. How We Use Your Information

We use your information to:

- fetch and store your CV so it can be rendered and hosted  
- keep your public CV page up to date  
- determine whether your page should display Pro features  
- allow you to preview paid themes when authenticated  
- manage your subscription  
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
- **Stripe** — to process payments and manage subscriptions  

We do not share personal data with third parties for marketing.

---

## 5. Data Retention

- A copy of your latest `cv.json` is stored on semantic.cv as long as the GitHub App remains installed.  
- When you uninstall or suspend the GitHub App, your stored CV is removed automatically.  
- Subscription records (GitHub user ID, Stripe customer ID, subscription status) are retained as long as your subscription is active and as required for accounting and tax compliance.  
- Authentication data is retained only as long as needed to provide the feature you are using.  
- Session cookies are removed when you sign out.

Subscription and billing records are not removed when uninstalling the GitHub App, as they must be retained for legal compliance.

---

## 6. Your Rights

You may:

- **Uninstall the Semantic‑CV GitHub App at any time.**  
  This immediately revokes all permissions and removes your stored CV from semantic.cv.

- **Modify or remove your `cv.json` file in your GitHub repository at any time.**  
  semantic.cv will update or remove the stored copy accordingly.

- **Request deletion of non‑essential data**,  
  such as cached rendering metadata or UI preferences.

### What cannot be deleted
semantic.cv must retain certain billing records (e.g., Stripe customer ID, transaction details) as required for accounting, tax, and licensing purposes.  
These records cannot be removed on request but are stored securely and used only for compliance and access control.

semantic.cv does not create traditional standalone user accounts.  
Authentication is optional and only used to provide specific features.

---

## 7. Contact

For questions about privacy or data handling, contact:  
**info@semantic.cv**
