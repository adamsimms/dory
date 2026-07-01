# Security Policy

**Do not open a public issue** for security problems. Use [GitHub private vulnerability reporting](https://github.com/adamsimms/dory/security/advisories/new).

Include what you found, how to reproduce it, and which URLs or files are affected.

Deploy credentials live in GitHub Actions secrets only (`FTP_SERVER`, `FTP_USERNAME`, `FTP_SERVER_DIR`, `SSH_DEPLOY_KEY`). If you commit a secret, rotate it immediately and file a private advisory.

In scope: deploy misconfigurations, credential leaks, and XSS or injection in this repo’s HTML or server config. Out of scope: issues in Sketchfab’s embed unless introduced by our integration.
