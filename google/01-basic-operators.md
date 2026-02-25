# Google — Basic Operators

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

Google is the most widely used web index. It crawls billions of pages and stores snippets and metadata in an index. Knowing the basic operators lets you narrow results to a domain, file type, or phrase — which is the foundation of effective dorking.

Analogy: imagine Google as a library card catalog where operators let you filter by author (`site:`), file type (`filetype:`), title (`intitle:`), or the exact sentence (`"phrase"`).

---

## 📖 The Basics

The most useful operators below are included with examples, realistic use-cases, and defense tips.

---

### site: `site:`

**What it does in plain English:**
Limits results to a single domain or host.

**Real-world situation where you'd use this:**
You're testing a company's public-facing domain and want only results from that site.

**Syntax:**
```
site:example.com
site:sub.example.com
site:*.example.com
```

**Real Examples (copy-paste ready):**
```
site:linkedin.com "works at" "Apple Inc"
site:github.com "AKIA"
site:tesla.com filetype:pdf
```

**What you might find:**
Public pages, PDF reports, employee profiles, or files indexed under that domain.

**Risk Level:** 🟢

**🛡️ How to Defend Against This:**
Use `robots.txt` to request non-indexing for sensitive paths, avoid publishing secrets, and ensure private subdomains are protected by authentication.

---

### inurl: `inurl:`

**What it does in plain English:**
Finds pages with a term in the URL.

**Real-world situation where you'd use this:**
Searching for admin panels, staging environments, or phpMyAdmin instances.

**Syntax:**
```
inurl:admin
inurl:wp-admin
inurl:phpmyadmin
```

**Real Examples:**
```
site:microsoft.com inurl:admin intitle:login
inurl:phpmyadmin intitle:"phpMyAdmin"
```

**What you might find:**
Login pages, management consoles, or default admin endpoints.

**Risk Level:** 🟡

**🛡️ How to Defend Against This:**
Move admin panels behind VPN or IP restrictions; use non-standard URLs and strong multi-factor authentication.

---

### intitle: `intitle:`

**What it does in plain English:**
Searches for terms in the page title.

**Real-world situation:**
Finding pages that explicitly say "login", "index of", or product names.

**Syntax:**
```
intitle:"login"
intitle:"index of"
```

**Real Examples:**
```
intitle:"index of" "parent directory" site:edu
intitle:"Jenkins" "Dashboard"
```

**What you might find:**
Directory listings, admin dashboards, or product-specific pages.

**Risk Level:** 🟡

**🛡️ How to Defend Against This:**
Disable directory listing, set correct titles, and restrict discovery via authentication.

---

### intext: `intext:`

**What it does:**
Searches for terms in the page body text.

**Use case:**
Find error messages, API keys mentioned in pages, or copy-paste developer notes.

**Syntax:**
```
intext:"mysql_connect()"
intext:"DB_PASSWORD"
```

**Real Examples:**
```
intext:"mysql_connect()" intext:"on line" site:.php
intext:"DB_PASSWORD" site:example.com
```

**Risk Level:** 🟡

**🛡️ How to Defend:**
Avoid leaking stack traces in production and sanitize error outputs.

---

### filetype: `filetype:`

**What it does:**
Filters results by file extension (pdf, env, sql, xls, etc.).

**Use case:**
Finding spreadsheets or configuration files with sensitive content.

**Syntax:**
```
filetype:pdf
filetype:env
filetype:sql
```

**Real Examples:**
```
site:*.gov filetype:xls "social security"
site:github.com filetype:env "DB_PASSWORD"
```

**What you might find:**
Spreadsheets with PII, .env files, SQL dumps.

**Risk Level:** 🔴

**🛡️ How to Defend:**
Remove sensitive files from public web roots, use access controls on file shares, and scan for filetypes in CI.

---

### cache: `cache:`

**What it does:**
Shows Google's cached snapshot of a page.

**Use case:**
Viewing a page that has since been removed or investigating deleted content.

**Syntax / Example:**
```
cache:example.com/some/page
```

**Risk Level:** 🟢

**🛡️ How to Defend:**
Request removal from Google's cache via Search Console or use `noarchive` metadata where appropriate.

---

### related: `related:`

**What it does:**
Finds pages similar to a given domain.

**Example:**
```
related:github.com
```

**Risk Level:** 🟢

---

### "exact phrase"

**What it does:**
Searches for the exact phrase in quotes.

**Example:**
```
"password123"
"AWS_SECRET_ACCESS_KEY"
```

**Risk Level:** 🔴 (depends on phrase)

---

### Excluding and Combining: `-`, `OR`, `*`, `..`, `( )`, `allinurl:`

**What they do:**
- `-term` excludes term. `OR` finds either. `*` is a wildcard for a single word. `..` ranges (numbers/dates). Grouping with parentheses.

**Examples:**
```
site:example.com -www
site:example.com (inurl:dev OR inurl:staging)
filetype:pdf 2018..2021
allinurl: admin login
```

**Risk Level:** 🟡 / 🔴 depending on combination

---

## 🔗 Combining Operators (Chaining)

Example 1: Find exposed admin panels on a specific company
```
site:target.com inurl:admin intitle:"login"
```
This searches only within target.com for URLs containing "admin" whose titles say "login".

Example 2: Find Excel files with personal data
```
site:*.gov filetype:xls "social security" OR "ssn"
```

---

## 📊 Quick Reference Table

| Operator | What It Does | Example | Risk |
|----------|--------------|---------|------|
| `site:` | Limit to one domain | `site:tesla.com` | 🟢 |
| `filetype:` | Find filetypes | `filetype:sql` | 🔴 |
| `inurl:` | Terms in URL | `inurl:admin` | 🟡 |
| `intitle:` | Terms in title | `intitle:"index of"` | 🟡 |
| `intext:` | Terms in body | `intext:"DB_PASSWORD"` | 🟡 |

---

## 🌍 Real-World Case Studies

1. GitHub leaks of AWS keys: Multiple incidents (2018–2020) where developers committed `aws_access_key_id` and `aws_secret_access_key` into public repos; attackers used them to spin up crypto-mining instances and cause high bills.

2. Public S3 buckets exposing backups: Several breaches where misconfigured S3 buckets exposed customer data (e.g., Accenture S3 report in 2017).

---

## ⚡ Quick Tips & Tricks

- Start broad with `site:target.com` then narrow with `filetype:` or `inurl:`.
- Use quotes for exact phrase matching to avoid noisy results.
- Combine `-` to exclude known public paths like `-www`.
- Keep a small test domain you own for experimenting safely.
- Record every discovery with screenshots and full URLs for reporting.

---

## 🔗 Related Files in This Repo

[START-HERE.md](../START-HERE.md)
[google/02-advanced-operators.md](../google/02-advanced-operators.md)
[google/03-file-discovery.md](../google/03-file-discovery.md)
