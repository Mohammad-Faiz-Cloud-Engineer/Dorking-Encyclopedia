# Google — Advanced Operators

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

Advanced operator chaining is where dorking becomes surgical. By combining three or more operators you can find staging environments, error pages revealing software versions, exposed git repositories, and backup files that public indexes swallowed.

Analogy: If basic operators are single filters in a search tool, chaining is like using a set of lenses to zoom in on a single photograph in a giant album.

---

## 📖 The Basics

We'll show how to combine operators to find high-value targets: staging sites, error messages, backups, git repositories, and software-specific leaks.

---

### Finding specific software versions

**What it does:**
Find pages that contain product names and version strings.

**Real example:**
```
intext:"Apache/2.4.41 (Ubuntu)" site:example.com
```

**Why:**
Version strings in error pages can be matched to known CVEs like CVE-2021-44228 (Log4Shell) or older Apache vulnerabilities.

**Risk Level:** 🟡 / 🔴 depending on version

**Defense:**
Hide version banners, patch, and suppress verbose error pages.

---

### Finding test/staging environments

**What it does:**
Locate subdomains and URLs that clearly indicate non-production environments.

**Example:**
```
site:target.com (inurl:staging OR inurl:dev OR inurl:test) -www
```

**Why:**
Staging often has weaker access controls or uses real credentials.

**Risk Level:** 🔴

**Defense:**
Require authentication, restrict by IP, and ensure staging does not contain production secrets.

---

### Finding backup and archive files

**What it does:**
Find zip, tar, bak, and other archived files that may contain sensitive data.

**Example:**
```
site:target.com (filetype:zip OR filetype:bak OR inurl:backup)
```

**Risk Level:** 🟡 - 🔴

**Defense:**
Remove archives from public web roots and store backups in private, access-controlled locations.

---

### Finding exposed `.git` repositories

**What it does:**
Detect when a site's `.git` directory is accessible, which can yield full source history and secrets.

**Example:**
```
intitle:"Index of /.git" OR inurl:"/.git/config" site:target.com
```

**Why:**
Access to `.git` can expose commit history, deleted files, and sensitive strings.

**Risk Level:** 🔴

**Defense:**
Prevent `.git` exposure (deny access via web server rules), and remove `.git` and other VCS directories from public deployments.

---

### Finding error messages that reveal tech stack

**What it does:**
Search for common error text that includes file paths or stack traces.

**Examples:**
```
intext:"Warning: mysql_connect()" filetype:php
intext:"Stack trace" "/var/www/" site:example.com
```

**Why:**
Error messages can reveal file structure, usernames, or framework versions.

**Risk Level:** 🟡

**Defense:**
Turn off verbose errors in production and log stack traces privately.

---

## 🔗 Combining Operators — Examples

1. Find staging MySQL dump files in government sites:
```
site:*.gov inurl:staging filetype:sql
```

2. Find exposed `.env` files on subdomains:
```
site:target.com inurl:/.env OR filetype:env
```

3. Find public `.git` folders that include credentials:
```
intitle:"Index of" ".git" "config" site:target.com
```

---

## 🌍 Real-World Case

Finding staging environments with live keys has repeatedly led to high-severity reports in bug bounty programs. In many public write-ups, authors found that staging sites had hard-coded API keys and no MFA, allowing account takeover or data leaks.

---

## ⚡ Quick Tips

- Use `-www -blog` to reduce noise.
- Combine `site:` with `filetype:` for focused results.
- Use parentheses to group OR clauses.

---

## 🔗 Related Files

[google/01-basic-operators.md](01-basic-operators.md)
[google/03-file-discovery.md](03-file-discovery.md)
