# Google — File Discovery

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

Files like `.env`, `.sql`, `.bak`, and `.pem` can contain secrets and configuration. Developers sometimes push these to web roots or commit them to repositories — and search engines index them. This file covers why each extension matters and how attackers and defenders treat them.

Analogy: If a website is a house, these files are the hidden safes and drawers — sometimes left unintentionally open.

---

## 📖 The Basics

We'll cover each filetype with: why it's dangerous, real contents, dork syntax, real examples, impact, and defense.

---

### .env Files

**Why they're dangerous:**
.env files often contain environment variables that store DB credentials, API keys, and third-party secrets.

**What's inside a real .env file:**
```
DB_HOST=prod-db.internal
DB_USER=admin
DB_PASSWORD=SuperSecret123
AWS_ACCESS_KEY_ID=AKIAIOSFODNN7EXAMPLE
STRIPE_SECRET_KEY=sk_live_abc123xyz
```

**The dork:**
```
filetype:env DB_PASSWORD
site:target.com filetype:env
intitle:"index of" ".env"
```

**Real Examples:**
```
site:github.com "DB_PASSWORD" filetype:env
```

**Real-world impact:**
Bug bounty reports have documented live Stripe and AWS keys found in `.env` files leading to server compromise and financial loss.

**Risk Level:** 🔴

**🛡️ How to Defend Against This:**
Remove `.env` from web roots, add `.env` to `.gitignore`, use secrets managers (AWS Secrets Manager, Vault), and rotate keys if accidentally exposed.

---

### .sql Files

**Why they're dangerous:**
SQL dumps often contain full database contents, including PII and credentials.

**Dork:**
```
filetype:sql "CREATE TABLE"
site:target.com filetype:sql
```

**Real Example:**
```
filetype:sql "INSERT INTO" "users"
```

**Risk Level:** 🔴

**🛡️ Defend:**
Avoid publishing DB dumps; restrict access to backups; encrypt backups at rest.

---

### .bak / backup files

**Why dangerous:**
Backups can contain code, config, or data that was removed from the site but is still sensitive.

**Dork:**
```
intitle:"index of" "backup" filetype:bak
```

**Risk Level:** 🟡

**Defend:**
Store backups in private object storage, enforce IAM, and remove backup files from web roots.

---

### .log Files

**Why dangerous:**
Logs often contain error messages, stack traces, and sometimes tokens or credentials.

**Dork:**
```
filetype:log "password"
site:target.com filetype:log
```

**Risk Level:** 🔴

**Defend:**
Avoid logging secrets, sanitize logs, and use centralized, access-controlled logging.

---

### .conf / .cfg

**Why dangerous:**
Configuration files can include service endpoints, credentials, or internal hostnames.

**Dork:**
```
filetype:conf "apache" site:target.com
filetype:cfg "password"
```

**Risk Level:** 🟡 - 🔴 depending on content

**Defend:**
Remove configs from public web directories and secure deployment pipelines.

---

### .json / .yaml / .yml

**Why dangerous:**
They may include API keys, OAuth tokens, or service accounts.

**Dork:**
```
filetype:json "API_KEY" site:github.com
filetype:yaml "secret" site:example.com
```

**Risk Level:** 🔴

**Defend:**
Keep config in environment platforms, not in committed files; use secret scanning in CI.

---

### Office files: .pdf .doc .docx .xls .xlsx .csv

**Why dangerous:**
Spreadsheets and documents often include PII, financials, or lists of credentials.

**Dork:**
```
site:*.gov filetype:xls "social security"
site:company.com filetype:pdf "confidential"
```

**Risk Level:** 🔴

**Defend:**
Check public storage and shared drives for exposed documents; restrict sharing permissions.

---

### .pem .key .p12 .ppk (private keys)

**Why dangerous:**
These are private keys. Possession often means full server access.

**Dork:**
```
filetype:pem "PRIVATE KEY"
filetype:key "BEGIN RSA PRIVATE KEY"
```

**Real Examples:**
```
site:github.com "BEGIN RSA PRIVATE KEY" filename:id_rsa
```

**Risk Level:** ⚫ Critical

**🛡️ How to Defend Against This:**
Never commit private keys. Use hardware modules or secrets managers and rotate keys immediately if exposed.

---

### Code files: .php .sh .py .rb .ps1

**Why dangerous:**
Source files can reveal DB credentials, debug endpoints, or tokens.

**Dork:**
```
filetype:php intext:"DB_PASSWORD"
filetype:py "AWS_ACCESS_KEY_ID"
```

**Risk Level:** 🔴

**Defend:**
Secret scanning in commit hooks and CI, and restrict repository visibility.

---

### .htpasswd

**Why dangerous:**
Contains credential hashes for Apache basic auth — useful for offline cracking.

**Dork:**
```
filetype:htpasswd "htpasswd"
```

**Risk Level:** 🔴

**Defend:**
Use stronger auth than basic, and do not leave these files in web roots.

---

## 🌍 Real-World Stories

- 2019–2020 GitHub incidents: developers accidentally committed AWS keys, which were quickly used by attackers for crypto-mining on the cloud account.
- Public S3 buckets containing database exports have repeatedly led to class-action lawsuits and regulatory fines.

---

## ⚡ Quick Tips & Tricks

- Search for `filetype:` across `site:` to reduce noise.
- Use date ranges for filetypes that include timestamps (`2019..2021`).
- Use a local domain you control for practicing dangerous dorks.

---

## 🔗 Related Files in This Repo

[google/01-basic-operators.md](01-basic-operators.md)
[google/06-config-and-secret-files.md](06-config-and-secret-files.md)
[github-dorking/02-api-keys-and-secrets.md](../github-dorking/02-api-keys-and-secrets.md)
