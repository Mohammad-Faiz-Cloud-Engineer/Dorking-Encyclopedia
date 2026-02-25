# GitHub — Database Credentials

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

Database connection strings and credentials in code allow attackers to connect to databases directly. GitHub search can find plaintext URIs and config snippets.

---

## 📖 Dorks and Patterns

```
intext:"postgres://" site:github.com
intext:"mongodb://" filename:.env
"DB_PASSWORD" path:config
```

**Risk Level:** 🔴

**Defend:**
Rotate credentials, remove secrets from repos, and use IAM roles instead of embedded usernames/passwords.

---

## 🔗 Related Files

[github-dorking/02-api-keys-and-secrets.md](02-api-keys-and-secrets.md)
