# Google — Sensitive Documents

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

Documents like PDFs, spreadsheets, and Word files are commonly mis-shared. They may contain PII, financials, or credentials. Attackers use targeted filetype searches to harvest these findings.

---

## 📖 The Basics

We'll cover `pdf`, `doc`, `xls`, `csv`, and how to find sensitive terms inside them.

---

### PDFs and Docs

**Dork:**
```
site:company.com filetype:pdf "confidential"
filetype:doc "internal use only"
```

**What you might find:**
Policies, financial reports, slide decks containing internal URLs or credentials.

**Risk Level:** 🔴

**Fix:**
Audit shared drives and enforce DLP policies.

---

### Spreadsheets (xls, xlsx, csv)

**Dork:**
```
site:*.gov filetype:xls "social security"
filetype:csv "employee" "ssn"
```

**Why:**
Spreadsheets frequently contain structured PII and bulk data exports.

**Risk Level:** 🔴

**Fix:**
Restrict share settings on cloud drives and scan for sensitive patterns before publishing.

---

### Text files and logs

**Dork:**
```
filetype:txt "password"
filetype:log "Authorization: Bearer"
```

**Risk Level:** 🔴

**Fix:**
Remove logs from web roots, sanitize before public storage, and use retention policies.

---

## 🌍 Real-World Stories

- Public spreadsheets containing voter or healthcare data have repeatedly caused breaches and fines.
- Corporate slide decks leaked financial projections that impacted markets.

---

## ⚡ Quick Tips

- Use `filetype:` with quoted sensitive terms for precise results.
- Search cloud storage domains like `drive.google.com` and `dropbox.com` for organization names.
- Implement DLP scanning for common document types.

---

## 🔗 Related Files

[google/03-file-discovery.md](03-file-discovery.md)
[defense/prevent-file-indexing.md](../defense/prevent-file-indexing.md)
