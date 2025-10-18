# Spyderwell Mini Site (Landing + Spyderbox)

This package contains a minimalist landing page for **Spyderwell.com** and a simple client‑side gated area called **Spyderbox**.

## Contents
- `index.html` — Public landing page
- `spyderbox_login.html` — Spyderbox access code prompt (client-side)
- `spyderbox_dashboard.html` — Post-login dashboard with simple activity widget
- `contact.vcf` — vCard for NFC/quick contact import
- `README.md` — This file

---

## Quick Start (Local Preview)
1. Download and unzip this package.
2. Double‑click `index.html` to open it in your browser.
   - To test Spyderbox, click **Spyderbox Login** and enter the demo code: `spyderbox123` (you can change it later).

> ⚠️ **Security Note:** This is a *demo* gate using client-side JavaScript. It’s suitable for casual privacy only. For sensitive documents, use real authentication (Firebase/Supabase/NextAuth) and private file storage (e.g., S3, Google Drive with signed links).

---

## Deployment Option A — GitHub Pages (Free, static hosting)
**Best for:** quick, static hosting without servers.

1. Create a new repo (e.g., `spyderwell-site`) on GitHub.
2. Add these files to the repo (drag‑and‑drop via GitHub web UI or use GitHub Desktop).
3. In GitHub, go to **Settings → Pages**:
   - **Source:** Deploy from a branch → `main` → `/ (root)`
   - Save.
4. GitHub will publish your site at: `https://<your-username>.github.io/spyderwell-site/`
5. Point your domain’s DNS to GitHub Pages (optional, to use `spyderwell.com`):
   - Add CNAME record: `www` → `<your-username>.github.io`
   - Add A records for apex root if needed (GitHub docs detail this).
6. In your repo, create a file named `CNAME` at the root that contains `spyderwell.com` (or `www.spyderwell.com`).

**Notes:**
- GitHub Pages is HTTPS by default — good for iPhone vCard downloads.
- Static only — no server-side auth.

---

## Deployment Option B — Netlify (Free tier, easy drag‑and‑drop)
**Best for:** simple deploys and nice HTTPS out of the box.

1. Create a Netlify account.
2. Drag & drop this folder into the **Sites** page, or connect your GitHub repo.
3. Netlify gives you a URL like `https://<random>.netlify.app/`.
4. Add your custom domain in **Site settings → Domain management** and follow DNS instructions.

---

## NFC Use (iPhone)
Point your NFC tag to the hosted vCard file (HTTPS):
```
https://spyderwell.com/contact.vcf
```
iOS will open the link, download the vCard, and offer **Add to Contacts**. This is the most reliable path.

---

## Customization

### Change the Spyderbox password
Open `spyderbox_login.html` and edit:
```html
<script>
  const PASSWORD = "spyderbox123"; // change this
</script>
```

### Update email, phone, and address
- In `index.html` and `spyderbox_*` files: search for `hello@spyderwell.com` and replace.
- In `contact.vcf`: update `TEL`, `EMAIL`, `ADR`, and `URL` fields.

### Replace example file links
In `spyderbox_dashboard.html`, replace the `href` targets in the “file-list” section with your real file paths or URLs.

---

## Upgrading to Real Authentication (Recommended for sensitive docs)
- **Firebase Auth + Firebase Hosting** (Google) or **Supabase Auth + Storage**.
- Protect files with **signed URLs** and serve only after verifying a login token.
- Optionally move to a framework (Next.js, SvelteKit) for better routing and session handling.

---

## Troubleshooting
- **Can’t open vCard on iPhone?** Ensure the URL is `https://...` and not blocked by a content filter.
- **Stuck at login?** Clear browser storage for the site (localStorage) or try a private/incognito window.
- **DNS not working yet?** Most DNS changes take up to 30 minutes (sometimes 24h) to fully propagate.

---

© 2025 Spyderwell. Minimal | Discreet | Practical
