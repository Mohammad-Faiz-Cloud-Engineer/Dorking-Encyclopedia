# robots.txt Guide

> ⚠️ LEGAL WARNING
> Every technique in this file is for EDUCATIONAL PURPOSES ONLY.

robots.txt tells well-behaved crawlers which paths to avoid. It's not a security control — sensitive files should not rely on it alone.

Example:
```
User-agent: *
Disallow: /admin/
Disallow: /config/

User-agent: Googlebot
Disallow: /staging/
```

Use `noindex` and access controls in addition to robots.
