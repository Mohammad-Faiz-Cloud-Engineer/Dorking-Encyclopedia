# Dorking Encyclopedia

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

This repository is a practical, hands-on encyclopedia of search engine dorking and passive reconnaissance techniques. Think of it as a field guide for finding publicly indexed resources — from accidentally exposed .env files to unprotected admin panels — using search engines and specialized internet-wide scanners.

Dorking is the art of asking search engines very specific questions so they return the exact drawer in the filing cabinet you want. Attackers use these techniques for reconnaissance; defenders use the same techniques to find and fix leaks before they become breaches.

---

## 📖 Who Is This For?

- **Beginners**: Learn the absolute fundamentals of indexing and safe reconnaissance.
- **Bug bounty hunters**: Practical dorks, playbooks, and responsible disclosure notes.
- **Penetration testers**: Recon checklists and ways to quickly map an attack surface.
- **Defenders / DevOps**: Actionable steps to remove sensitive files from public indexes.
- **Security educators**: Teaching-friendly examples and analogies for training.

---

## 🔍 How This Repo Is Organized

Visual map:

- Root: general guides and quick starts
- `google/` — deep Google dorking operators and file discovery
- `bing/`, `duckduckgo/` — other web search engines
- `shodan/`, `censys/`, `fofa/`, `zoomeye/` — internet-wide scanners
- `github-dorking/` — code search and leaked secrets
- `specialized-engines/` — niche OSINT engines
- `playbooks/` — mission-style workflows
- `defense/` — how to remove yourself from indexes and block exposures
- `tools/` — usage guides for common recon tooling

---

## ⚡ Quick Start — Beginners

1. Read [START-HERE.md](START-HERE.md).
2. Run the five safe dorks in `START-HERE.md` on open domains (no login required).
3. Read `google/01-basic-operators.md` to understand how operators work.

---

## ⚡ Quick Start — Advanced

- Use `shodan/05-favicon-hash-technique.md` to fingerprint similar web apps across the internet.
- Search GitHub for `file:.env "AWS_SECRET"` patterns in `github-dorking/02-api-keys-and-secrets.md`.
- Build chained queries from `google/02-advanced-operators.md` for targeted passive recon.

---

## 📋 Top 20 Useful Dorks (Across Engines)

| Rank | Dork | Why it matters |
|------|------|----------------|
| 1 | `site:target.com filetype:env` | Find environment files with secrets |
| 2 | `site:target.com inurl:admin intitle:login` | Discover admin login panels |
| 3 | `"BEGIN RSA PRIVATE KEY" site:github.com` | Leaked private keys on GitHub |
| 4 | `site:pastebin.com "api_key"` | Keys leaked to public pastes |
| 5 | `site:*.gov filetype:xls "social security"` | Sensitive spreadsheets on gov domains |
| 6 | `intitle:"index of" "parent directory"` | Open directory listings |
| 7 | `filetype:sql "CREATE TABLE"` | Public SQL dumps |
| 8 | `site:target.com inurl:staging OR inurl:dev` | Exposed staging environments |
| 9 | `site:github.com "AKIA"` | AWS key patterns in repositories |
| 10 | `http.favicon.hash:116323821` | Favicon-based fingerprinting (Shodan) |
| 11 | `inurl:phpmyadmin intitle:phpMyAdmin` | phpMyAdmin panels |
| 12 | `site:target.com "password" filetype:log` | Passwords in logs |
| 13 | `site:drive.google.com "confidential"` | Publicly shared cloud docs |
| 14 | `site:target.com filetype:pem "PRIVATE KEY"` | Private keys exposed |
| 15 | `site:github.com "stripe" "sk_live_"` | Live Stripe keys leaked |
| 16 | `site:target.com "DB_PASSWORD" filetype:env` | DB credentials in env files |
| 17 | `site:target.com "index of /backup"` | Backup folders exposed |
| 18 | `site:target.com "server at" "Apache"` | Server banners revealing tech |
| 19 | `site:target.com "Jenkins" intitle:Dashboard` | Jenkins CI panels |
| 20 | `site:target.com "s3.amazonaws.com" "confidential"` | Public S3 buckets referenced |

---

## 📚 Table of Contents (links)

- [START-HERE.md](START-HERE.md)
- [GLOSSARY.md](GLOSSARY.md)
- google/
  - [google/01-basic-operators.md](google/01-basic-operators.md)
  - [google/02-advanced-operators.md](google/02-advanced-operators.md)
  - [google/03-file-discovery.md](google/03-file-discovery.md)
  - [google/04-login-portals.md](google/04-login-portals.md)
  - [google/05-exposed-databases.md](google/05-exposed-databases.md)
  - [google/06-config-and-secret-files.md](google/06-config-and-secret-files.md)
  - [google/07-sensitive-documents.md](google/07-sensitive-documents.md)
  - [google/08-cameras-and-iot.md](google/08-cameras-and-iot.md)
  - [google/09-vulnerability-discovery.md](google/09-vulnerability-discovery.md)
  - [google/10-cloud-storage-exposure.md](google/10-cloud-storage-exposure.md)
  - [google/11-email-and-people.md](google/11-email-and-people.md)
  - [google/12-subdomain-enumeration.md](google/12-subdomain-enumeration.md)
  - [google/CHEATSHEET.md](google/CHEATSHEET.md)
- bing/
  - [bing/README.md](bing/README.md)
- shodan/
  - [shodan/README.md](shodan/README.md)
  - [shodan/05-favicon-hash-technique.md](shodan/05-favicon-hash-technique.md)
- github-dorking/
  - [github-dorking/02-api-keys-and-secrets.md](github-dorking/02-api-keys-and-secrets.md)
- playbooks/
  - [playbooks/bug-bounty-recon.md](playbooks/bug-bounty-recon.md)
- defense/
  - [defense/what-attackers-look-for.md](defense/what-attackers-look-for.md)
- tools/
  - [tools/README.md](tools/README.md)

---

## ⭐ Star / Fork / Contribute

If this repo helped you, star it and contribute. Pull requests accepted.

![Stars](https://img.shields.io/github/stars/Mohammad-Faiz-Cloud-Engineer/Dorking-Master-Repository)
![Forks](https://img.shields.io/github/forks/Mohammad-Faiz-Cloud-Engineer/Dorking-Master-Repository)

---

## Disclaimer

This repository contains techniques used by both attackers and defenders. The intent is educational. Always obtain permission before testing.

What's next? Start with [START-HERE.md](START-HERE.md).
