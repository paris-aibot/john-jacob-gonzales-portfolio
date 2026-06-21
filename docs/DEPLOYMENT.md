# Deployment Guide

This site is fully static, so it can be hosted free on any static host. The
recommended target is **Cloudflare Pages** (global CDN, generous free tier,
native support for `_headers` and `_redirects`, zero config for a single-page site).

---

## Why Cloudflare Pages

| Option | Verdict for this project |
|--------|--------------------------|
| **Cloudflare Pages** ✅ | Fastest global edge, free, honours `_headers`/`_redirects` already in this repo, no build step. **Recommended.** |
| GitHub Pages | Great if you want zero extra accounts; needs a Pages workflow; ignores `_headers` (no custom CSP). |
| Netlify | Excellent DX; best if you later add Netlify Forms for a contact form. |
| Vercel | Polished, but optimized for app frameworks; overkill for a static page. |

---

## Method A — Dashboard (no CI, easiest)

1. Push this repository to GitHub (see [First push](#first-push) below).
2. Go to the [Cloudflare dashboard](https://dash.cloudflare.com/) → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
3. Authorize GitHub and select this repository.
4. Build settings:
   - **Framework preset:** `None`
   - **Build command:** *(leave empty)*
   - **Build output directory:** `/`
5. Click **Save and Deploy**. Your site goes live at `https://<project>.pages.dev`.
6. Every future `git push` auto-deploys.

> Cloudflare automatically applies `_headers`, `_redirects`, and serves `404.html`.

## Method B — GitHub Actions (CI/CD, included)

A workflow is already provided at [`.github/workflows/deploy.yml`](../.github/workflows/deploy.yml).

1. Create a Pages project once (dashboard, or `npx wrangler pages project create jjg-portfolio`).
2. In Cloudflare, create an API token with the **"Cloudflare Pages — Edit"** permission, and note your **Account ID** (right sidebar of the dashboard).
3. In GitHub → repo **Settings → Secrets and variables → Actions**, add:
   - `CLOUDFLARE_API_TOKEN`
   - `CLOUDFLARE_ACCOUNT_ID`
4. Make sure the `--project-name` in the workflow matches your Pages project.
5. Push to `main`. The action deploys automatically; check the **Actions** tab.

---

## First push

```bash
cd "john-jacob-gonzales-portfolio"
git init
git add .
git commit -m "feat: production-ready portfolio"
git branch -M main
git remote add origin https://github.com/<your-username>/john-jacob-gonzales-portfolio.git
git push -u origin main
```

---

## After deploy — required follow-ups

1. **Set your real domain everywhere.** Replace the placeholder
   `https://johnjacobgonzales.pages.dev/` in:
   - `index.html` (canonical, OG/Twitter URLs, JSON-LD `url`)
   - `sitemap.xml`
   - `robots.txt`

2. **Social card.** A `1200×630` PNG (`assets/og-image.png`) is **already generated**
   and wired into the OG/Twitter meta tags, so social sharing works out of the box.
   If you edit `og-image.svg`, regenerate the PNG with any of:

   ```bash
   # macOS (no install needed) — Quick Look + crop
   qlmanage -t -s 1200 -o /tmp assets/og-image.svg && \
     sips -c 630 1200 /tmp/og-image.svg.png --out assets/og-image.png

   # or rsvg-convert (brew install librsvg)
   rsvg-convert -w 1200 -h 630 assets/og-image.svg -o assets/og-image.png
   ```

   After any change, validate with the
   [LinkedIn Post Inspector](https://www.linkedin.com/post-inspector/) and
   [Meta Sharing Debugger](https://developers.facebook.com/tools/debug/).

3. **Add screenshots** to `docs/` and reference them in the README.

4. **Custom domain (optional):** Pages → your project → **Custom domains** →
   add your domain and follow the DNS instructions.

---

## Verifying production readiness

- [ ] Site loads at the `.pages.dev` URL
- [ ] `view-source` shows OG tags and JSON-LD
- [ ] `/_headers` applied: check response headers include `content-security-policy`
- [ ] Disable JS in DevTools → all sections still visible
- [ ] Lighthouse: aim for 95+ on Performance, Accessibility, Best Practices, SEO
- [ ] Visiting a random bad URL shows `404.html`
- [ ] Social card renders in the LinkedIn Post Inspector (after PNG step)
