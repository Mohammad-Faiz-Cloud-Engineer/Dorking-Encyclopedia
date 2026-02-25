# Google — Email & People Search

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

Finding email addresses and people-related info helps map an organization and can support phishing or social engineering. Defenders should know what contact data is public.

---

## 📖 The Basics

Use `site:` with employee directories, `"@company.com"`, and `intext:` searches to find role-based addresses and personal emails exposed in docs.

---

### Finding emails

**Dorks:**
```
"@company.com" site:linkedin.com
site:company.com "@company.com" filetype:pdf
```

**Risk Level:** 🟡

**Defend:**
Limit public exposure of personal emails and encourage role-based contacts for reporting.

---

### Searching for people and roles

**Dorks:**
```
site:company.com "works at" "Google"
site:linkedin.com "Chief Technology Officer" "Tesla"
```

**Why:**
Mapping staff helps attackers craft targeted phishing messages.

**Risk Level:** 🟡

**Defend:**
Train employees on phishing and minimize publish of role-specific contact details.

---

### Finding exposed mailing lists or support emails

**Dorks:**
```
site:company.com "support@" OR "security@"
```

**Risk Level:** 🟢 - 🟡 depending on use

**Defend:**
Monitor contact addresses for abuse and ensure support channels have rate-limiting and verification.

---

## 🔗 Related Files

[google/01-basic-operators.md](01-basic-operators.md)
[playbooks/brand-monitoring.md](../playbooks/brand-monitoring.md)
