# Prevent File Indexing

> ⚠️ LEGAL WARNING
> Every technique in this file is for EDUCATIONAL PURPOSES ONLY.

Practical steps to prevent files from being indexed:

1. Use `robots.txt` to disallow crawlers (not an access control):

```
User-agent: *
Disallow: /private/
```

2. Add `<meta name="robots" content="noindex">` to HTML pages.
3. Use HTTP auth or IP restrictions for sensitive directories.
4. Remove files from public web roots and store in private object storage with ACLs.

---

What's next: See `robots-txt-guide.md` for details.
