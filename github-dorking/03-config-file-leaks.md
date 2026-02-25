# GitHub — Config File Leaks

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

Config files often contain credentials. Searching GitHub for config filenames and known keys helps find leaks quickly.

---

## 📖 Examples

```
filename:wp-config.php "DB_PASSWORD"
filename:docker-compose.yml "PASSWORD"
filename:.env "AWS_SECRET_ACCESS_KEY"
```

**Risk Level:** 🔴

**Defend:**
Remove secrets from history, use secret scanning, and add pre-commit hooks.

---

## 🔗 Related Files

[github-dorking/02-api-keys-and-secrets.md](02-api-keys-and-secrets.md)
