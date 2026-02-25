# Shodan — API & Automation

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

Shodan has an API that lets you run searches programmatically. Automation enables large-scale asset tracking, but API keys must be protected.

---

## 🔧 Example automation (Python)

```python
# Example: use an environment variable for the API key and handle errors/pagination.
# Requirements: pip install shodan
import os
from shodan import Shodan

API_KEY = os.getenv('SHODAN_API_KEY')
if not API_KEY:
    raise SystemExit('Set SHODAN_API_KEY environment variable')

api = Shodan(API_KEY)
query = 'http.favicon.hash:116323821'
try:
    # Small searches: api.search
    results = api.search(query)
    for r in results.get('matches', []):
        print(r.get('ip_str'), r.get('http', {}).get('host'))

    # For large result sets prefer the cursor API (pagination):
    # for r in api.search_cursor(query):
    #     print(r.get('ip_str'))
except Exception as e:
    print('Shodan API error:', e)
```

**Risk Level:** 🟡

**Defend:**
Keep API keys secret, rotate them, and monitor for anomalous usage.

---

## 🔗 Related Files

[shodan/05-favicon-hash-technique.md](05-favicon-hash-technique.md)
