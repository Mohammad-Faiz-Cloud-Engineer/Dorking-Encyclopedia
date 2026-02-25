# Bug Bounty Recon Playbook

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

## The Mission
You've joined a bug bounty program. Scope: `*.shopify.com`. Your mission: perform passive reconnaissance only. No scanning, no brute force — just public information.

---

## Phase 1: Figure Out What They've Built (30 minutes)

Step 1: Map the main domain
```
site:shopify.com
```

Step 2: Find interesting subdomains
```
site:*.shopify.com -www -help -community
```

Step 3: Look for staging/dev environments
```
site:shopify.com inurl:staging OR inurl:dev OR inurl:test
```

What's next? If you find dev/staging, note it for escalation — these often have weaker security.

---

## Phase 2: Find Login Pages and Admin Panels (20 minutes)

Step 1: Generic admin search
```
site:shopify.com inurl:admin intitle:login
```

Step 2: Search specific panels (Jenkins, Grafana, Kibana)
```
site:shopify.com intitle:"Dashboard [Jenkins]"
site:shopify.com intitle:"Grafana"
site:shopify.com intitle:"Kibana"
```

What you want: Unlinked panels, staging login pages, or pages revealing versions.

---

## Phase 3: Find Code/Config Leaks (30 minutes)

Step 1: Search for config files
```
site:shopify.com filetype:env OR filetype:yaml OR filetype:json
```

Step 2: Search GitHub for org-related secrets
```
site:github.com "shopify" "AWS_ACCESS_KEY_ID"
```

Note: If you find things, do not attempt to use credentials. Instead, prepare a responsible disclosure.

---

## Phase 4: Find Sensitive Documents & Cloud Exposure (30 minutes)

Step 1: Public cloud docs
```
site:drive.google.com shopify
site:amazonaws.com "shopify" "backup"
```

Step 2: S3 references
```
site:github.com "s3.amazonaws.com" "shopify"
```

What you want: backups, spreadsheets, or links to buckets.

---

## Phase 5: Report & Triage (30 minutes)

1. Prepare evidence: URL, snippet, and screenshot.
2. Determine impact and whether it's in-scope.
3. Draft a concise report with remediation steps (rotate keys, remove file, block indexing).

---

## Quick Live Dork Examples

```
site:shopify.com inurl:staging "index of"
site:shopify.com filetype:sql "INSERT INTO"
site:github.com shopify "AKIA"
```

---

## Tips for the Live Session

- Keep notes and timebox each phase.
- Use disposable browser profiles to avoid leaking your own cookies.
- If you escalate publicly, redact secrets in screenshots.

---

## 🔗 Related Files

[google/02-advanced-operators.md](../google/02-advanced-operators.md)
[github-dorking/02-api-keys-and-secrets.md](../github-dorking/02-api-keys-and-secrets.md)
