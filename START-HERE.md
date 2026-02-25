# Start Here — Beginner's Guide

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

## 🧠 What Is a Search Engine Index?

Think of the internet as a massive library. Search engines are librarians that read every page they can and write a short note about it in an index (a big catalog). When you search, the librarian looks through the index, not every page in real time. That index often contains things people accidentally left in public.

## What Is Dorking?

Dorking is the practice of crafting very specific search queries (called dorks) to find interesting stuff in the index — like forgotten backups, admin panels, or leaked credentials. It's not hacking into systems; it's asking better questions of the librarian.

## Why This Is a Skill, Not a Hack

Most dorks don't bypass authentication — they reveal what's already public. The skill is in knowing which operators to use and how to interpret results without tripping into illegal activity.

---

## Your First 5 Safe Dorks (Try these on public demo sites or your own domains)

1. Find a company's public PDFs:
```
site:tesla.com filetype:pdf
```

2. Look for obvious admin panels (read-only reconnaissance):
```
site:microsoft.com inurl:admin intitle:login
```

3. Find directory listings (useful to learn what people accidentally expose):
```
intitle:"index of" "parent directory"
```

4. Search for `.env` mentions (do not attempt to access contents without permission):
```
filetype:env "DB_PASSWORD"
```

5. Find public cloud docs:
```
site:drive.google.com "confidential"
```

---

## What To Do When You Find Something Sensitive

1. Do not access more than the search result preview.
2. Document the URL, snippet, and why it looks sensitive.
3. Check the target's bug bounty or disclosure policy (HackerOne/Bugcrowd). If in scope, follow their disclosure process.
4. If there's no program, find a legitimate contact (security@company.com) and send a concise, non-alarming report.

Always act professionally and never exploit an exposure.

---

## Beginner Glossary — 10 Terms

- **Index**: The search engine's catalog of pages.
- **Dork**: A crafted search query for reconnaissance.
- **Operator**: A special word like `site:` or `filetype:` that changes search behavior.
- **OSINT**: Open-source intelligence — information collected from public sources.
- **Cache**: A stored snapshot of a page that the search engine saved.
- **Fingerprinting**: Identifying technologies used by a site.
- **Banner**: A service's initial text reply (e.g., an SSH banner).
- **Recon**: Short for reconnaissance — the information-gathering phase.
- **GHDB**: Google Hacking Database — a collection of dorks.
- **Robots.txt**: A file that tells crawlers which pages not to index.

---

## What's Next?

Read [google/01-basic-operators.md](google/01-basic-operators.md) to learn the operators that make dorking powerful. Then try the safe dorks above on a site you own.
