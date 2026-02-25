# GitHub Dorking — API Keys & Secrets

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

GitHub is a massive index of source code. People accidentally commit secrets: API keys, private keys, tokens, and credentials. These leaks are gold for attackers — they often allow immediate, high-impact access (cloud accounts, payment systems).

As a bug hunter, you can find these leaks responsibly and report them. As a defender, you must hunt for your own keys before attackers do.

---

## 📖 The Basics

This file focuses on common secret types, real-world patterns, dorks to find them, how to verify safely, and responsible reporting.

---

### AWS Access Keys

**What it is:**
AWS access keys allow programmatic access to AWS APIs. Leaked keys can be used to spin up resources, access S3 buckets, or manage infrastructure.

**Damage if leaked:**
Full AWS account misuse: data exfiltration, resource provisioning (crypto-mining), and service abuse causing large bills.

**Pattern:**
`AKIA[0-9A-Z]{16}`

**Dorks:**
```
"AKIA" AND ("secret" OR "aws_secret") filename:.env
"AWS_ACCESS_KEY_ID" extension:env
"AWSSecretKey" filename:credentials
path:.aws/credentials
```

**What a real leaked key looks like (redacted pattern):**
```
AKIAIOSFODNN7EXAMPLE
```

**How to verify (safely):**
- Check the repository metadata (owner/org) and commit timestamp.
- Do NOT attempt to use the key. Instead, if you have permission, contact the repository owner or program.

**Responsible reporting:**
- For public repos, open an issue in the repo (if appropriate) or email the repo owner. For orgs, follow the security contact.
- If it's an organization's repo and there's a bug bounty program, file a report with full evidence and recommendations to rotate keys.

---

### Stripe Keys

**What it is:**
Stripe secret keys (`sk_live_...`) let you charge cards and access payment data.

**Damage if leaked:**
Unauthorized charges, refunds, customer data exposure, or charges to the company's account.

**Pattern:**
`sk_live_[A-Za-z0-9]{24}`

**Dorks:**
```
"sk_live_" filename:.env
"STRIPE_SECRET_KEY" extension:env
"stripe_secret" language:python
```

**Redacted example:**
```
sk_live_4eC39HqLyjWDarjtT1zdp7dc
```

**Verify:**
Look for evidence in the repo that the key is tied to production (config files naming production). Do not use the key.

**Report:**
Contact the app owner or the payment processor's abuse team; recommend rotating keys immediately.

---

### Google API Keys

**Pattern:** `AIza[0-9A-Za-z\-_]{35}`

**Dorks:**
```
"AIzaSy" filename:.env
"GOOGLE_API_KEY" extension:json
"google_maps_api_key" language:javascript
```

**Risk Level:** 🟡 - 🔴 depending on API permissions

**Defend:**
Restrict API keys to allowed referrers and rotate them.

---

### SSH Private Keys

**What it is:**
An SSH private key is essentially a master key for servers. `BEGIN RSA PRIVATE KEY` or `BEGIN OPENSSH PRIVATE KEY` in a file is a red flag.

**Dorks:**
```
"BEGIN RSA PRIVATE KEY" extension:pem
"BEGIN OPENSSH PRIVATE KEY" filename:id_rsa
filename:id_ed25519
```

**Redacted example:**
```
-----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEA...
-----END RSA PRIVATE KEY-----
```

**Risk Level:** ⚫ Critical

**How to report:**
Immediately contact the owner/org; recommend revoking the key and rotating credentials.

---

### Slack / Discord Tokens

**Why important:**
Tokens can let an attacker post messages as a bot or access channels.

**Dorks:**
```
"xoxp-" OR "xoxb-" site:github.com
"discord_bot_token" filename:.env
```

**Risk Level:** 🔴

---

### GitHub Tokens (Personal Access Tokens)

**Pattern:** `ghp_[A-Za-z0-9_]{36}` (older patterns vary)

**Dorks:**
```
"ghp_" site:github.com
"GITHUB_TOKEN" filename:.env
```

**Risk Level:** ⚫ Critical

---

### Other Secrets (short list)

- Twilio: `SK[0-9a-fA-F]{32}`
- SendGrid: `SG.[A-Za-z0-9_-]{20,}`
- Firebase server keys: `AAAA...`
- Heroku API keys: `[0-9a-f]{32}`
- JWT secrets: long random strings used to sign tokens

For each of the above: include the typical dork patterns in the same manner, do NOT attempt to use any discovered secret, and always recommend rotation and restrictions.

---

## How to Verify a Secret is Real (Non-Destructive)

1. Check repo context (is it a config file for production?).
2. Look for references to production endpoints or AWS ARNs.
3. Use public metadata (commit messages, CI YAML) to estimate impact.
4. Never attempt to authenticate with a found key — that's unauthorized access.

---

## Responsible Disclosure Template

1. Title: Found exposed secret in public repository
2. Target: `https://github.com/org/repo/path`
3. Evidence: screenshot of file with redacted secret
4. Impact: Describe what the secret allows (e.g., S3 access, charges via Stripe)
5. Remediation: Revoke key, rotate, add secrets scanning, remove from repo and history

---

## 🔗 Related Files in This Repo

[google/03-file-discovery.md](../google/03-file-discovery.md)
[playbooks/bug-bounty-recon.md](../playbooks/bug-bounty-recon.md)
[defense/how-to-remove-yourself-from-google.md](../defense/how-to-remove-yourself-from-google.md)
