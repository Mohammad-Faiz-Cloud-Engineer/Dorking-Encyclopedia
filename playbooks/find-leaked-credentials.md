# Playbook — Find Leaked Credentials

> ⚠️ LEGAL WARNING
> Every technique in this file is for EDUCATIONAL PURPOSES ONLY.

Step-by-step guide to hunt for leaked credentials across search engines and code hosts. Focus: non-destructive discovery, documentation, and responsible reporting.

Phases:
1. Search GitHub for `AKIA`, `sk_live_`, `BEGIN RSA PRIVATE KEY` patterns.
2. Use Google dorks for `filetype:env`, `filetype:sql` and cloud storage links.
3. Monitor paste sites and specialized engines for new leaks.
4. Triage and report, recommending rotation and revocation.
