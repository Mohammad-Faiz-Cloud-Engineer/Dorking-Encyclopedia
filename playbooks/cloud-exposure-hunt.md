# Playbook — Cloud Exposure Hunt

> ⚠️ LEGAL WARNING
> Every technique in this file is for EDUCATIONAL PURPOSES ONLY.

Hunt for cloud misconfigurations: public buckets, leaked IAM keys, and improperly secured services.

Phases:
1. Search for `s3.amazonaws.com`, `storage.googleapis.com`, and `blob.core.windows.net` references in code and docs.
2. Use Shodan/Censys to find open management ports for cloud consoles.
3. Check public repos for long-lived cloud keys and rotate.
