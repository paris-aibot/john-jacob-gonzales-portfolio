# Contributing

Thanks for your interest! This is a personal portfolio, but suggestions, bug reports, and accessibility/performance improvements are welcome.

## Ways to contribute

- 🐛 **Report a bug** — open an issue using the Bug Report template.
- 💡 **Suggest an improvement** — open an issue using the Feature Request template.
- ♿ **Accessibility / performance fixes** — PRs especially welcome here.

## Development

There is no build step. Edit [`index.html`](index.html) and preview with any static server:

```bash
python3 -m http.server 8080
# open http://localhost:8080
```

## Project conventions

- **Single-file site.** Keep HTML, CSS, and JS in `index.html` unless a change clearly warrants a separate file.
- **Use the design tokens.** Reach for the `:root` CSS variables (colors, `--col-label`) instead of hard-coding values.
- **Accessibility is non-negotiable.** Maintain WCAG AA contrast, keyboard focus styles, `prefers-reduced-motion`, and the no-JS fallback (`.js`-gated reveals).
- **No new runtime dependencies** without discussion — the zero-dependency property is a feature.
- **Test before PR:** keyboard-only navigation, mobile width (≤760px), JS disabled, and print preview.

## Pull requests

1. Fork and create a branch: `git checkout -b fix/short-description`.
2. Make focused, minimal changes.
3. Verify the checklist above.
4. Open a PR using the template and describe what changed and why.

## Commit style

Conventional, imperative subject lines are appreciated:

```
fix: raise muted text contrast to meet WCAG AA
feat: add back-to-top button
docs: clarify deployment steps
```
