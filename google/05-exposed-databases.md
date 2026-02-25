# Google — Exposed Databases

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

Databases power most web apps. Exposed database panels, dumps, or admin tools like phpMyAdmin give direct access to data. This section covers common database exposures and practical dorks to find them.

---

## 📖 The Basics

We'll cover MySQL, PostgreSQL, MongoDB, Redis, Elasticsearch, phpMyAdmin, and public SQL dump files.

---

### MySQL error messages and traces

**Dorks:**
```
intext:"mysql_connect()" intext:"on line" filetype:php
intext:"Warning: mysql_connect()" site:example.com
```

**What you might find:**
PHP pages showing stack traces that reveal DB connection functions or usernames.

**Risk Level:** 🟡

**Defend:**
Suppress errors in production and log internally.

---

### phpMyAdmin exposed

**Dorks:**
```
intitle:"phpMyAdmin" inurl:phpmyadmin
```

**What you might find:**
Public phpMyAdmin login pages; sometimes misconfigured without password.

**Risk Level:** 🔴

**Defend:**
Put phpMyAdmin behind a VPN or restrict by IP, update frequently.

---

### SQL dump files

**Dorks:**
```
filetype:sql "CREATE TABLE"
filetype:sql "INSERT INTO" site:example.com
```

**What you might find:**
Full schema and data dumps — usernames, emails, hashed passwords, PII.

**Risk Level:** 🔴

**Defend:**
Avoid storing dumps in public locations; encrypt and restrict backups.

---

### MongoDB / Redis / Elasticsearch markers

**Dorks (examples):**
```
intext:"MongoDB" "bind_ip"
intext:"Elasticsearch" "cluster.name" site:example.com
intext:"redis-cli" "Authentication required"
```

**What you might find:**
Configuration snippets or endpoints referencing DB hosts and ports.

**Risk Level:** 🔴 (exposed DBs can be read/written)

**Defend:**
Bind DBs to private networks, require auth, and network-segment them.

---

### Database connection strings in source

**Dorks:**
```
intext:"mongodb://" site:github.com
intext:"postgres://" filetype:env
```

**Risk Level:** 🔴

**Defend:**
Use environment variables and secrets managers; rotate credentials.

---

## 🌍 Real-World Case Studies

- Publicly available Elasticsearch clusters have leaked PII in multiple incidents (2017–2019).
- Open MongoDB instances were commonly misconfigured and scraped by attackers for crypto-mining and data theft in 2017.

---

## ⚡ Quick Tips

- Use `filetype:sql` and `intext:` chaining to find full dumps.
- Search GitHub for `postgres://` or `mongodb://` to find connection strings.
- Check `intitle:"phpMyAdmin"` for exposed database panels.

---

## 🔗 Related Files

[google/03-file-discovery.md](03-file-discovery.md)
[github-dorking/02-api-keys-and-secrets.md](../github-dorking/02-api-keys-and-secrets.md)
