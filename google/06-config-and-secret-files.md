# Google — Config & Secret Files

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

Config files and secret material (SSH keys, Docker configs, `wp-config.php`) are high-value because they directly map to credentials and internal configuration. This file focuses on the most common config leaks and concrete dorks to find them.

---

## 📖 The Basics

We'll cover `.git` exposure, `wp-config.php`, Apache/Nginx configs, SSH keys, AWS credentials, and Docker configs.

---

### Exposed `.git` directories

**Why:**
`.git` contains the repository history. It can include deleted files and credentials.

**Dork:**
```
intitle:"Index of /.git" OR inurl:"/.git/" site:target.com
```

**Risk Level:** 🔴

**Fix:**
Ensure `.git` is not deployed to production; deny access via web server rules.

---

### WordPress `wp-config.php`

**Dork:**
```
filetype:php inurl:wp-config "DB_PASSWORD"
```

**Why:**
`wp-config.php` contains DB creds and salts.

**Risk Level:** 🔴

**Fix:**
Ensure proper file permissions and prevent direct web access to config files.

---

### SSH private keys

**Dork:**
```
filetype:pem "PRIVATE KEY" site:github.com
```

**Risk Level:** ⚫ Critical

**Fix:**
Rotate keys, use passphrases, and enable key management.

---

### AWS credentials in CSV or code

**Dork:**
```
filetype:csv "AWSAccessKeyId" OR "AWS_SECRET_ACCESS_KEY"
"AWS_ACCESS_KEY_ID" filename:.env
```

**Risk Level:** 🔴

**Fix:**
Rotate keys, use IAM roles, and replace long-lived credentials with temporary tokens.

---

### Docker and Kubernetes config leaks

**Dork:**
```
filename:docker-compose.yml password
filetype:yaml "kind: Pod" "imagePullSecrets"
```

**Why:**
Leaked deployment files can reveal private registries, secrets, and cluster endpoints.

**Risk Level:** 🔴

**Fix:**
Use secrets management (Kubernetes Secrets backed by sealed-secrets or HashiCorp Vault) and avoid committing deploy files with secrets.

---

## 🔗 Related Files

[google/03-file-discovery.md](03-file-discovery.md)
[github-dorking/02-api-keys-and-secrets.md](../github-dorking/02-api-keys-and-secrets.md)
