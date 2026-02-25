# DuckDuckGo — Bangs for Security

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

DuckDuckGo "bangs" (`!`) are shortcuts that forward your query to other sites (e.g., `!gh` opens GitHub search). Use bangs to quickly perform searches on specialized platforms.

---

## 🛠️ Useful bangs for security

- `!gh` — GitHub search: `!gh AKIA site:github.com`
- `!sh` — Shodan (if supported) — quick link to Shodan searches
- `!so` — StackOverflow — find error messages and fixes

**Example:**
```
!gh site:github.com "AWS_ACCESS_KEY_ID"
!so "TypeError: undefined is not a function"
```

**Risk Level:** 🟢 — these are convenience features.

---

## 🔗 Related Files

[duckduckgo/01-operators.md](01-operators.md)
