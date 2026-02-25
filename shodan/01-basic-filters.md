# Shodan — Basic Filters

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

Shodan uses filters to narrow down results: `port:`, `org:`, `hostname:`, `country:` and `http.title:` are common. These let you find specific devices, services, or geographically-located hosts quickly.

---

## 📖 The Basics

Common filters:
```
port:22
port:443
org:"Amazon.com"
country:US
hostname:camera.example
http.title:"Gateway"
```

**Real examples:**
```
port:3389 country:RU
org:"Cloudflare, Inc." http.title:"Welcome"
```

**Risk Level:** 🟡 - 🔴 depending on service

**Defend:**
Close unnecessary ports, limit management services to private networks, and monitor public-facing services.

---

## 🔗 Related Files

[shodan/02-device-discovery.md](02-device-discovery.md)
