# ZoomEye — Operators

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

ZoomEye supports fields like `app`, `port`, `country`, and `header`. Use it to find banners and web applications at scale.

---

## 📖 Examples

```
app:nginx port:80 country:CN
header:"Server: Apache" app:php
```

**Risk Level:** 🟡 - 🔴

**Defend:**
Monitor exposed app banners and avoid publishing management interfaces.
