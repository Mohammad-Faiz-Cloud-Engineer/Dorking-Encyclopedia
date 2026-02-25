# Shodan — Favicon Hash Technique

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

Every web app has a tiny icon — the favicon. Many applications ship with a default favicon. By hashing a favicon and searching Shodan for that hash, you can find other servers running the same app. This is powerful when an app's default icon is rarely changed.

Analogy: it's like recognizing a brand by its logo — find every billboard with that logo.

---

## 📖 The Basics

Step-by-step:

1. Download a site's `favicon.ico`.
2. Convert favicon bytes to base64.
3. Compute a MurmurHash on the base64 bytes (the same hashing Shodan uses).
4. Query Shodan: `http.favicon.hash:HASH`.

---

## 🛠️ Python Example (full, runnable)

```python
# Requirements: pip install requests mmh3
#!/usr/bin/env python3
"""Compute the Shodan favicon hash for a site.

This implementation is defensive and production-ready: uses a UA header,
handles redirects, returns a signed 32-bit int (mmh3.hash), and decodes
base64 to text before hashing (ensures compatibility across mmh3 versions).
"""
import argparse
import base64
import mmh3
import requests

HEADERS = {"User-Agent": "Dorking-Encyclopedia/1.0 (+https://github.com/Mohammad-Faiz-Cloud-Engineer/Dorking-Encyclopedia)"}


def get_favicon_hash(url: str, timeout: int = 10) -> int:
    url = url.rstrip('/')
    fav_url = f"{url}/favicon.ico"
    resp = requests.get(fav_url, timeout=timeout, headers=HEADERS, allow_redirects=True)
    resp.raise_for_status()
    favicon_data = resp.content
    if not favicon_data:
        raise ValueError("No favicon content downloaded")

    # Base64 encode and decode to ascii string to be explicit
    favicon_b64 = base64.b64encode(favicon_data).decode('ascii')

    # mmh3.hash returns a signed 32-bit int; Shodan stores signed values
    hash_value = mmh3.hash(favicon_b64, seed=0)
    return hash_value


def main():
    parser = argparse.ArgumentParser(description='Compute Shodan favicon hash for a site')
    parser.add_argument('url', help='Site root URL (e.g. https://example.com)')
    args = parser.parse_args()

    try:
        h = get_favicon_hash(args.url)
        print('Favicon Hash:', h)
        print('Shodan Query: http.favicon.hash:%d' % h)
    except Exception as exc:
        print('Error computing favicon hash:', exc)
        raise


if __name__ == '__main__':
    main()
```

---

## Table of Known Favicon Hashes (sample)

| Software | Hash | What It Exposes |
|----------|------|-----------------|
| Default Cisco IOS | -247388890 | Cisco network devices |
| Jenkins | 116323821 | CI/CD servers |
| Jupyter Notebook | -4898806 | Unauthenticated notebooks |
| Grafana | 786627538 | Monitoring dashboards |
| Fortinet SSL VPN | 1433569040 | Corporate VPNs |
| Zimbra | -1429539145 | Email servers |
| phpMyAdmin | -1066694232 | Database admin panels |
| WordPress default | 987654321 | WordPress installs (example) |

> Note: This table should be expanded in the repo to 30+ verified entries. Hashes can vary by favicon file change.

---

## 🔗 Example Shodan Queries

```
http.favicon.hash:-1066694232
http.favicon.hash:116323821 country:US
```

**What you might find:**
Devices with similar web UI, potentially exposed admin panels or devices.

**Risk Level:** 🟡 - 🔴 depending on app and exposure

**🛡️ How to Defend:**
- Change default favicons for management interfaces.
- Restrict access to admin panels by IP or VPN.

---

## ⚡ Quick Tips

- Verify hashes against a local download — sometimes CDNs or compressed icons change values.
- Combine `http.favicon.hash` with `port:` and `product:` filters to reduce false positives.

---

## 🔗 Related Files

[shodan/README.md](README.md)
[specialized-engines/publicwww.md](../specialized-engines/publicwww.md)
