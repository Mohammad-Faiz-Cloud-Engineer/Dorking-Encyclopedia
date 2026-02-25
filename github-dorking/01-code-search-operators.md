# GitHub — Code Search Operators

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

GitHub code search has operators like `filename:`, `path:`, `extension:`, and `repo:`. Use these to focus on likely locations for secrets.

---

## 📖 Operators

- `filename:.env` — find environment files
- `extension:json` — find JSON files
- `path:.github/workflows` — find CI files
- `repo:organization/repo` — limit to a repo

**Real Examples:**
```
filename:.env "DB_PASSWORD"
extension:yaml "secret"
path:.github/workflows "secrets"
```

**Risk Level:** 🔴 when secrets are present

**Defend:**
Use GitHub secret scanning, remove secrets from history, and restrict repo visibility.

---

## 🔗 Related Files

[github-dorking/02-api-keys-and-secrets.md](02-api-keys-and-secrets.md)
