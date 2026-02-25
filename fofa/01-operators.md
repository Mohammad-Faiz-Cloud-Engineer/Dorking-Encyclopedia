# FOFA — Operators

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

FOFA's query language focuses on banners and headers. It's useful for finding specific software or versions across the internet.

---

## 📖 Example Operators

- `domain="example.com"`
- `header="Server: nginx"`
- `body="login"`
- `cert="CN=example.com"`

**Example:**
```
header="Server: Apache" and body="index of"
```

**Risk Level:** 🟡 - 🔴 depending on results

---

## 🔗 Related Files

[fofa/CHEATSHEET.md](CHEATSHEET.md)
