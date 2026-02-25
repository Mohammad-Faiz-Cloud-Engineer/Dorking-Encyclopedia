# What Attackers Look For — Defender's Guide

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

## Overview

This file shows what an attacker would search for and how you, as a defender, can check and fix exposure. For each threat: attacker's goal, dork, how to check yourself, and remediation.

---

### Threat: Exposed `.env` or config files

1. Attacker's goal: Obtain API keys, DB credentials, or tokens.
2. Dork they'd use:
```
site:yourcompany.com filetype:env OR filetype:yaml "DB_PASSWORD"
```
3. How to check yourself: Run the same dork scoped to your domain and review results.
4. Fix it:
   - Remove `.env` from web root.
   - Add `.env` to `.gitignore` and remove any committed secret from repo history (use `git filter-repo`).
   - Rotate credentials and store secrets in a manager (AWS Secrets Manager, HashiCorp Vault).

---

### Threat: Publicly accessible backups and SQL dumps

1. Attacker's goal: Download full database or backups.
2. Dork:
```
site:yourcompany.com filetype:sql OR intitle:"index of" "backup"
```
3. How to check: Search for `filetype:sql` and `intitle:"index of" backup` on your domain.
4. Fix:
   - Move backups to private storage with proper IAM.
   - Ensure web servers do not serve backup directories.

---

### Threat: Leaked private keys

1. Goal: Use private key to access servers or infrastructure.
2. Dork:
```
site:github.com "BEGIN RSA PRIVATE KEY" "yourcompany"
```
3. Check: Search GitHub and public paste sites for your org names alongside `BEGIN RSA PRIVATE KEY`.
4. Fix:
   - Revoke and rotate keys immediately.
   - Add pre-commit hooks and CI secret scanning to block commits.

---

### Threat: Exposed admin panels

1. Goal: Find an admin login page to attempt phishing or credential stuffing.
2. Dork:
```
site:yourcompany.com inurl:admin intitle:login
```
3. Check: Run the dork and review results for unprotected panels.
4. Fix:
   - Enforce IP allowlists or place behind VPN.
   - Require MFA for admin accounts.

---

### Threat: Public cloud buckets referenced in code

1. Goal: Locate S3 or other buckets with backups or docs.
2. Dork:
```
site:github.com "s3.amazonaws.com" "yourcompany"
```
3. Check: Search public code for references to your buckets.
4. Fix:
   - Use bucket policies that deny public read.
   - Monitor bucket ACLs and enable object-level logging.

---

## Final Checklist for Defenders

- Run `site:yourcompany.com filetype:env` and review.
- Search GitHub for `yourcompany` + `AWS_ACCESS_KEY_ID` and other patterns.
- Ensure directory listing is disabled on all servers.
- Add pre-commit secret scanning and CI checks.
- Implement least privilege for cloud credentials and rotate keys on schedule.

---

## What's next?

Read [google/03-file-discovery.md](../google/03-file-discovery.md) for specific filetype dorks and [defense/how-to-remove-yourself-from-google.md](how-to-remove-yourself-from-google.md) for takedown steps.
