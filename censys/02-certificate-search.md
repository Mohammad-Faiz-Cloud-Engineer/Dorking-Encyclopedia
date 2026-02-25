# Censys — Certificate Search

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

Certificates reveal hostnames, SANs, and sometimes email addresses and organization names. Certificate transparency logs and Censys let you find hosts by certificate fields and spot reused certs across unrelated hosts.

---

## 📖 Certificate Queries

Examples:
```
parsed.extensions.subject_alt_name.dns_names: "example.com"
parsed.subject.common_name: "www.example.com"
parsed.issuer.common_name: "Let's Encrypt"
```

**Use case:**
Find all hosts using a particular certificate, or find hosts that present a cert with a specific SAN.

**Risk Level:** 🟡

**Defend:**
Audit CT logs for unexpected certificates, and set up monitoring for certificates issued for your domains.

---

## 🔗 Related Files

[censys/01-basic-search.md](01-basic-search.md)
