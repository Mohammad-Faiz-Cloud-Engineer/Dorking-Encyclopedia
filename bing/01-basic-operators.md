# Bing — Basic Operators

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

Bing supports many of the same operators as Google (`site:`, `filetype:`, `inurl:`, `intitle:`). Use it as a secondary index to find results that Google might not surface.

Examples:
```
site:example.com filetype:env
site:github.com "AKIA"
inurl:admin intitle:login site:example.com
```

Risk Level: 🟡 - 🔴 depending on query results.

What's next? See `bing/02-unique-bing-operators.md` for Bing-specific tips.
