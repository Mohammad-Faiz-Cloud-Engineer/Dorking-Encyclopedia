# Google — Cameras & IoT

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

IoT devices and cameras often expose web interfaces or default credentials. Search engines can index their web UIs or public screenshots linked from other pages. This section explains how to find such devices and how to mitigate exposure.

---

## 📖 The Basics

Google sometimes indexes web UI pages for cameras and routers; combined with Shodan/Censys, an attacker can map live devices.

---

## 📷 IP Cameras

**Dork:**
```
inurl:"/view.shtml" "DVR" OR "IP Camera" site:example.com
inurl:"/snapshot.cgi"
```

**What you might find:**
Camera vendor login pages, snapshot URLs, or publicly embedded images.

**Risk Level:** 🔴

**Defend:**
Change default passwords, keep firmware updated, and block camera interfaces from the public internet.

---

## 🔌 Routers, NAS, and Other IoT

**Dorks:**
```
intitle:"D-Link" "router" inurl:login
intitle:"QNAP" "login"
```

**Risk Level:** 🔴

**Defend:**
Disable remote management, use strong passwords, and segment IoT on a separate network.

---

## 🌍 Realistic Scenario

Researchers find public webcam feeds (baby monitors, store cameras) indexed via crawling or publicly linked pages. These often expose personal data and are a privacy disaster for victims.

---

## ⚡ Quick Tips

- Combine `inurl:` with vendor names for focused searches.
- Use Shodan for port- and banner-based discovery and Google for pages that reference or embed camera feeds.

---

## 🔗 Related Files

[shodan/README.md](../shodan/README.md)
[google/09-vulnerability-discovery.md](09-vulnerability-discovery.md)
