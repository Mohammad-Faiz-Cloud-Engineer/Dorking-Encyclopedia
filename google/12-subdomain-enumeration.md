# Google — Subdomain Enumeration

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

Subdomains often host staging, admin, API, or developer tools. Google can surface subdomains via indexing or through links on other sites. Use specific `site:` and `inurl:` queries plus certificate transparency to enumerate subdomains.

---

## 📖 The Basics

Basic dork to list subdomains indexed by Google:
```
site:*.example.com -www
```

Combine with `inurl:` to find interesting ones:
```
site:*.example.com inurl:api -www
```

---

## Advanced tips

- Search for `site:example.com -www -blog -help` to remove noise.
- Use `site:example.com "Application Name"` to find related subdomains.
- Cross-check with Certificate Transparency logs (crt.sh) and DNS bruteforce tools.

---

## Realistic workflow

1. `site:*.target.com -www -help -support`
2. Save unique subdomains.
3. Cross-reference with `http.favicon.hash:` and Shodan for matching services.

---

## ⚡ Quick Tips

- Google is a starting point — combine with `amass`, `subfinder`, and `crt.sh`.
- Look for wildcard subdomains like `*.app.target.com` in logs and headers.

---

## 🔗 Related Files

[google/02-advanced-operators.md](02-advanced-operators.md)
[google/12-subdomain-enumeration.md](12-subdomain-enumeration.md)
