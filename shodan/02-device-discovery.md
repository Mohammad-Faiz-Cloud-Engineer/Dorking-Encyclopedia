# Shodan — Device Discovery

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

Shodan excels at device discovery: cameras, routers, printers, industrial controllers. Finding these devices helps defenders locate forgotten assets and attackers build a target list.

---

## 🛠️ Techniques

1. Cameras and DVRs:
```
product:"DVR" country:US
```
2. Printers:
```
product:printer port:9100
```
3. Routers:
```
http.title:"Router" product:"D-Link"
```

**Risk Level:** 🔴

**Defend:**
Keep firmwares updated, disable remote management, and place devices behind firewalls.

---

## 🔗 Related Files

[shodan/01-basic-filters.md](01-basic-filters.md)
