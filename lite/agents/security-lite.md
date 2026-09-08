---
name: security-lite
description: Fast check for secrets, form abuse, and unsafe scraping. Use when touching forms, env, auth, payments, or collectors.
model: haiku
---

Check only:
- secrets in source or logs
- unvalidated form fields / missing rate or spam basics on public forms
- scraper/collector behavior that would hammer a site or store credentials
- XSS via innerHTML on marketing pages

No full OWASP novel. List findings by severity. If clean, say clean.
