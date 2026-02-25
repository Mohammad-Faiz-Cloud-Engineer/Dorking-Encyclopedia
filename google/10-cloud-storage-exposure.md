# Google — Cloud Storage Exposure

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

Cloud storage (S3, Google Cloud Storage, Azure blob) often shows up in code, docs, or public links. Finding references or public buckets can reveal backups, media, or credentials.

---

## 📖 The Basics

Search for `s3.amazonaws.com`, `storage.googleapis.com`, or cloud provider URLs and file listings.

---

### Finding S3 buckets and files

**Dorks:**
```
site:amazonaws.com "s3.amazonaws.com" "confidential"
inurl:s3.amazonaws.com "backup"
```

**What you might find:**
Publicly linked S3 objects or references in code pointing to buckets.

**Risk Level:** 🔴

**Defend:**
Set bucket policies to private, enable Block Public Access, and audit bucket ACLs.

---

### Google Cloud Storage

**Dork:**
```
inurl:storage.googleapis.com "project-id"
```

**Risk Level:** 🔴

**Defend:**
Use fine-grained IAM and avoid embedding public links to sensitive objects.

---

### Azure blob storage

**Dork:**
```
inurl:blob.core.windows.net "container"
```

**Risk Level:** 🔴

**Defend:**
Use SAS tokens with expiration and restrict container ACLs.

---

## 🌍 Real-World Notes

Misconfigured S3 buckets have led to numerous data breaches (e.g., Accenture 2017, multiple incidents where backups were publicly accessible).

---

## ⚡ Quick Tips

- Search GitHub for references to `s3.amazonaws.com` to find repo-referenced buckets.
- Audit cloud storage via provider tools and enable object-level logging.

---

## 🔗 Related Files

[google/03-file-discovery.md](03-file-discovery.md)
[playbooks/find-leaked-credentials.md](../playbooks/find-leaked-credentials.md)
