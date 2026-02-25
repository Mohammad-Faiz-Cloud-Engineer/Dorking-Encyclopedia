# DuckDuckGo — Operators

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

## 🧠 What Is This? (Start With the "Why")

DuckDuckGo uses simpler operators but is useful for cross-checks when Google returns sparse or personalized results. Treat it as a second opinion when hunting for public leaks.

---

## 🛠️ Operators / Techniques

### site: `site:`

**What it does in plain English:** Limits results to a domain.

**Real Examples:**
```
site:github.com "AKIA"
site:tesla.com filetype:pdf
```

**Risk Level:** 🟢

**How to Defend:** Monitor your domain with the same queries.

---

### filetype: `filetype:`

**What it does:** Filter by file extension.

**Example:**
```
filetype:env "DB_PASSWORD"
```

**Risk Level:** 🔴

---

### quoted phrases, inurl:

Works as expected. Use quotes for exact matches and `inurl:` to find terms in URLs.

---

## 🔗 Related Files

[duckduckgo/02-bangs-for-security.md](02-bangs-for-security.md)
