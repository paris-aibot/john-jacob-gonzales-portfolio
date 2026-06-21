# Changelog

All notable changes to this project are documented here.
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.0.0] — 2026-06-21

Production-readiness pass: refactor, accessibility, SEO, features, and repository packaging.

### Added
- **Progressive enhancement**: content is now fully visible without JavaScript (`.js`-gated scroll-reveal). Previously all sections were invisible if JS failed.
- `prefers-reduced-motion` support across animations, transitions, and smooth scroll.
- Visible `:focus-visible` keyboard focus rings and a skip-to-content link.
- SEO/social: Open Graph + Twitter Card meta, canonical URL, `theme-color`, author meta, and JSON-LD `Person` structured data.
- Sticky navigation with scroll-spy active-section highlighting.
- Back-to-top button.
- "Download résumé" button + `@media print` stylesheet (Save as PDF).
- `favicon.svg`, `og-image.svg`, `site.webmanifest`.
- `404.html` on-brand error page, `robots.txt`, `sitemap.xml`.
- Cloudflare Pages `_headers` (CSP + security/cache headers) and `_redirects`.
- Repository scaffolding: README, LICENSE (MIT), `.gitignore`, CONTRIBUTING, CODE_OF_CONDUCT, SECURITY, issue/PR templates, GitHub Actions deploy workflow.
- `docs/DEPLOYMENT.md` and `docs/PORTFOLIO.md`.

### Changed
- Raised `--muted` color from `#5C6779` to `#707B8F` to meet WCAG AA contrast (~3.5:1 → ~4.9:1).
- Converted fixed `px` font sizes to `rem` for better respect of user font-size preferences.
- Replaced empty `<span></span>` grid-spacer hacks with a reusable `.colgrid` layout utility.
- Wrapped page content in a semantic `<main>` landmark; added `aria-labelledby` to sections and `aria-hidden` to decorative elements.
- External links hardened with `rel="noopener noreferrer"` and screen-reader "opens in new tab" text.
- Renamed entry file to `index.html` for clean hosting.

### Fixed
- Critical: sections no longer render blank when JavaScript is unavailable.
- Corrected likely typo in "Train Operator Basic Training" date (2025 → 2022); **please verify**.

## [1.0.0] — 2026

### Added
- Initial single-file portfolio (`John_Jacob_Gonzales_HTML_WEBSITE.html`) with hero, about, experience, projects, skills, certifications, and contact sections.
