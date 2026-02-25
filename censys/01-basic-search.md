# Censys — Basic Search

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

Censys provides structured search over internet-wide scan data. You can search for open ports, services, and certificate properties. It's useful for finding hosts by TLS fields or by software banners.

---

## 📖 Basic Queries

Examples:
```
services.tcp.port:443 and parsed.http.title: "Welcome"
443.https.tls.cipher_suite: "TLS_AES_128_GCM_SHA256"
autonomous_system.asn: 15169
```

**Risk Level:** 🟡 - 🔴 depending on results

**Defend:**
Monitor your certificate usage and revoke/reissue reused or expired certs.

---

## 🔗 Related Files

[censys/02-certificate-search.md](02-certificate-search.md)
