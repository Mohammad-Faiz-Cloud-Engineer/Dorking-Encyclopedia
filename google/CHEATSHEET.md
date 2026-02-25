# Google Dorking — Cheatsheet

> ⚠️ LEGAL WARNING
> Every technique in this file is for EDUCATIONAL PURPOSES ONLY.
> Use these only on systems you OWN or have WRITTEN PERMISSION to test.
> Using these on systems without permission is a CRIMINAL OFFENSE in most countries.
> In the USA → Computer Fraud and Abuse Act (CFAA) → up to 10 years in prison.
> In the UK → Computer Misuse Act → up to 10 years in prison.
> In the EU → Directive 2013/40/EU → criminal prosecution.
> The people who built this repo are not responsible for how you use it.
> If you're a bug bounty hunter: only test targets listed in your program scope.

---

## Quick Operator Reference

- `site:domain` — Limit to a domain
- `filetype:ext` — Find documents and files
- `inurl:term` — Term in URL
- `intitle:term` — Term in page title
- `intext:term` — Term in page body
- `-term` — Exclude term
- `OR` — Logical OR
- `"exact phrase"` — Exact match
- `inurl:.git` — Exposed git directories
- `cache:` — View cached page

---

## Fast Examples

```
site:tesla.com filetype:pdf
site:github.com "AKIA" filetype:env
intitle:"index of" "backup"
inurl:phpmyadmin intitle:"phpMyAdmin"
filetype:pem "PRIVATE KEY"
```

---

## Risk Levels Quick Key

- 🟢 Informational — low sensitivity
- 🟡 Medium — reveals structure or tech
- 🔴 High — direct sensitive data
- ⚫ Critical — private keys / full access

---

## What's next?

Read the deeper files in `google/` for context and real examples.
