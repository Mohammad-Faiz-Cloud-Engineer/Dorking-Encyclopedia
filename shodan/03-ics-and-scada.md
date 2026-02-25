# Shodan — ICS & SCADA

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

Shodan sometimes indexes industrial control systems (ICS) and SCADA interfaces. These are extremely sensitive; finding them can indicate a severe exposure of critical infrastructure.

---

## 📖 What to look for

Search for common ICS products and ports:
```
product:Siemens port:102
product:GE SCADA
```

**Risk Level:** ⚫ Critical

**Defend:**
These systems should never be internet-facing. Isolate them on private networks, apply strict ingress filtering, and monitor for abnormal access.

---

## 🔗 Related Files

[shodan/02-device-discovery.md](02-device-discovery.md)
