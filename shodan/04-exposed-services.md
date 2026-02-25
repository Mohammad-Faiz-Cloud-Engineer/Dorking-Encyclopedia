# Shodan — Exposed Services

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

Shodan can find exposed services like RDP, SSH, Elasticsearch, and database management consoles. These often provide direct access or information leakage.

---

## 🔎 Common service queries

```
port:3389 product:Microsoft-Windows-Terminal-Services
port:5432 product:PostgreSQL
port:9200 http.title:"Elasticsearch"
```

**Risk Level:** 🔴 - ⚫

**Defend:**
Close database ports to the public internet and require VPN or private connectivity for management services.

---

## 🔗 Related Files

[shodan/02-device-discovery.md](02-device-discovery.md)
