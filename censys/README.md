# Censys — Overview

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

## 🧠 What Is Censys? (Start With the "Why")

Censys is an internet-wide scanner that focuses heavily on certificates and TLS information. It scans hosts and indexes TLS, SSH, and service metadata. Security teams use Censys to find certificate reuse, expired certs, and hosts by certificate attributes.

---

## 📖 The Basics

- Use Censys to search by `autonomous_system.asn`, certificate subject, issuer, and subjectAltName.
- It's particularly useful for certificate-based reconnaissance and finding hosts by TLS attributes.

---

## 🔗 Related Files

[censys/01-basic-search.md](01-basic-search.md)
[censys/02-certificate-search.md](02-certificate-search.md)
[censys/CHEATSHEET.md](CHEATSHEET.md)
