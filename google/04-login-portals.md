# Google — Login Portals

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

Login portals are high-value targets because they gate access. Finding unadvertised or misconfigured login pages is a staple of reconnaissance: they may be default installs, staging logins, or admin consoles.

Analogy: imagine finding a hidden door to a building — even if it's locked, its presence narrows attack paths.

---

## 📖 The Basics

Below are common portal types, real dorks, what attackers look for, and how to secure them.

---

### WordPress admin

**What it is:** The WordPress administration dashboard.

**Why target:** Many sites use WordPress; admin pages can allow plugin installation or code execution.

**Dork:**
```
inurl:wp-admin intitle:"WordPress"
```

**Risk Level:** 🟡

**Defend:**
Use strong MFA, limit login attempts, and protect `/wp-admin` with IP restrictions or HTTP auth.

---

### cPanel

**What it is:** Hosting control panel.

**Dork:**
```
inurl:2082 OR inurl:2083 intitle:"cPanel"
```

**Risk Level:** 🔴

**Defend:**
Ensure cPanel is not exposed to the public internet or is behind a VPN.

---

### phpMyAdmin

**What it is:** Database administration UI.

**Dork:**
```
inurl:phpmyadmin intitle:"phpMyAdmin"
```

**Risk Level:** 🔴

**Defend:**
Restrict access, enforce strong auth, and disable root login.

---

### Cisco VPN

**Dork:**
```
intitle:"Cisco SSL VPN" inurl:webvpn
```

**Risk Level:** 🔴

**Defend:**
Keep firmware updated, require MFA, and limit exposure to known IP ranges.

---

### Citrix Gateway

**Dork:**
```
intitle:"Citrix Gateway"
```

**Risk Level:** 🔴

**Defend:**
Patch known CVEs (e.g., CVE-2019-19781 historically) and protect management interfaces.

---

### Outlook Web Access (OWA)

**Dork:**
```
intitle:"Outlook Web App" inurl:owa
```

**Risk Level:** 🔴

**Defend:**
Enable MFA, monitor login attempts, and isolate mail admin panels.

---

### Fortinet / Juniper / VPN portals

**Dorks:**
```
intitle:"FortiGate SSL VPN"
intitle:"Juniper Networks Web Device Manager"
```

**Risk Level:** 🔴

**Defend:**
Apply vendor patches, rotate admin creds, and limit remote access.

---

### Jenkins / Grafana / Kibana / Jupyter

**Dorks:**
```
intitle:"Dashboard [Jenkins]"
intitle:"Grafana"
intitle:"Kibana"
intitle:"Jupyter Notebook" inurl:tree
```

**Why:**
These developer and ops tools often contain secrets, pipelines, and data.

**Risk Level:** 🔴

**Defend:**
Require auth, enable role-based access, and avoid default credentials.

---

## 🔗 Combining Operators

Find admin panels on subdomains (avoid false-positives):
```
site:target.com (inurl:admin OR intitle:login) -www -help
```

---

## ⚡ Quick Tips

- Record URLs and titles for triage later.
- Use non-destructive checks only — don't attempt logins.
- For defenders: monitor your domain for `intitle:"login"` results.

---

## 🔗 Related Files

[google/01-basic-operators.md](01-basic-operators.md)
[playbooks/bug-bounty-recon.md](../playbooks/bug-bounty-recon.md)
