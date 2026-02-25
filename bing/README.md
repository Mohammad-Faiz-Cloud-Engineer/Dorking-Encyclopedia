# Bing Dorking

> ⚠️ LEGAL WARNING
> Every technique in this file is for EDUCATIONAL PURPOSES ONLY.
> Use these only on systems you OWN or have WRITTEN PERMISSION to test.
> Using these on systems without permission is a CRIMINAL OFFENSE in most countries.
> In the USA → Computer Fraud and Abuse Act (CFAA) → up to 10 years in prison.
> In the UK → Computer Misuse Act → up to 10 years in prison.
> In the EU → Directive 2013/40/EU → criminal prosecution.
> The people who built this repo are not responsible for how you use it.
+If you're a bug bounty hunter: only test targets listed in your program scope.

---

## 🧠 What Is This? (Start With the "Why")

Bing is Microsoft's search engine. It supports many of the same operators as Google but also has unique behaviors and filters. Bug hunters use Bing because some sites are indexed differently than Google, and Bing can return different results for the same query.

---

## 📖 Basics & Operators

- `site:domain` — Limit to a domain
- `filetype:ext` — Filter by file type
- `inurl:term` — Term in URL
- `intitle:term` — Term in page title
- `ip:` — Search by IP address (Bing supports IP-based queries)

---

## Unique Bing Tips

- Use `ip:` to find webpages hosted on a specific IP.
- Bing sometimes indexes dynamically generated pages that Google doesn't.

---

## CHEATSHEET

```
site:target.com filetype:env
ip:93.184.216.34
site:github.com "AKIA"
```

---

## 🔗 Related Files

[google/01-basic-operators.md](../google/01-basic-operators.md)
