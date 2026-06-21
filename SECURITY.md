# Security Policy

## Scope

This is a static, client-side-only website. There is no backend, database, user
authentication, or server-side processing. The attack surface is therefore
limited, but the project still follows sensible web-security hygiene.

## Hardening in place

- **Content Security Policy** and other security headers are configured in [`_headers`](_headers):
  - `Content-Security-Policy` (restricts script/style/font/image origins)
  - `X-Content-Type-Options: nosniff`
  - `X-Frame-Options: DENY` / CSP `frame-ancestors 'none'`
  - `Referrer-Policy: strict-origin-when-cross-origin`
  - `Permissions-Policy` (disables geolocation, camera, microphone, FLoC)
- All external links use `rel="noopener noreferrer"`.
- No secrets, tokens, or API keys are stored in this repository.
- No third-party JavaScript is loaded (fonts are the only third-party resource).

## Reporting a vulnerability

If you discover a security issue (for example, a way to inject content, a header
misconfiguration, or an exposed secret), please report it privately:

- **Email:** johnjacobgonzales12678@gmail.com
- Please include a description, steps to reproduce, and potential impact.
- Do **not** open a public issue for security-sensitive reports.

You can expect an acknowledgement within a few business days.

## Supported versions

The latest version on the default branch is the only supported version.
