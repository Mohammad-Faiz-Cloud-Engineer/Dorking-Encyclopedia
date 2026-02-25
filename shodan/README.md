# Shodan — Overview

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

## 🧠 What Is Shodan? (Start With the "Why")

Google indexes websites. Shodan indexes devices and services. It scans IPs and records their banners — those initial responses that reveal software, version, and sometimes default pages.

Why it matters: your router, CCTV, HVAC controllers, and industrial systems respond to probes. Shodan keeps a catalog of that visibility.

---

## 📖 The Basics

How Shodan works technically:

1. Shodan scans IP ranges on common ports (80, 443, 22, 3389, etc.).
2. It captures the banner (what the service says when you connect), response headers, and sometimes screenshots of web pages.
3. It indexes results and lets you search by port, product, hostname, and banner content.

Is it legal? Yes — scanning public IPs is lawful in many jurisdictions, but aggressive scanning or exploiting found devices is not.

What's a banner? A banner is the initial text a service returns. Example SSH banner:
```
SSH-2.0-OpenSSH_7.4p1 Debian-10+deb9u3
```

Free vs paid: Free accounts give limited results; paid accounts unlock the full dataset, historical data, and more API calls.

---

## 🔍 Why Security Teams Use It

- Asset discovery: find internet-facing assets you forgot about.
- Vulnerability discovery: match banners to known vulnerable versions.
- Threat hunting: find attacker infrastructure or leaked services.

---

## ⚙️ Getting Started

1. Create a free account at Shodan.io.
2. Get an API key from your account dashboard for automation.
3. Start with simple searches: `port:22 product:OpenSSH`.

---

## 🔗 Related Files

[shodan/05-favicon-hash-technique.md](05-favicon-hash-technique.md)
[specialized-engines/publicwww.md](../specialized-engines/publicwww.md)
