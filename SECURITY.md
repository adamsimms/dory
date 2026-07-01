# Security Policy

## Supported versions

| Version | Supported |
|---------|-----------|
| `main` branch (live at [pinchards.is/dory](https://www.pinchards.is/dory/)) | Yes |
| Older tags / forks | No |

## Reporting a vulnerability

**Please do not open a public GitHub issue** for security problems.

Use [GitHub private vulnerability reporting](https://github.com/adamsimms/dory/security/advisories/new)
for this repository. Reports are delivered only to maintainers.

Include:

- A description of the issue and impact
- Steps to reproduce (or proof of concept)
- Affected URLs or files, if known

We aim to acknowledge reports within a few days and will coordinate on disclosure timing.

## Secrets and credentials

- **Never commit** SSH private keys, FTP passwords, or other deploy credentials.
- Production deploy secrets live in **GitHub Actions repository secrets**
  (`FTP_SERVER`, `FTP_USERNAME`, `FTP_SERVER_DIR`, `SSH_DEPLOY_KEY`).
- This project has **no runtime secrets** — it is a static HTML/CSS embed.

If you accidentally commit a secret:

1. **Rotate the credential immediately** — assume it is compromised once pushed.
2. Open a private security advisory so history can be reviewed.

## Scope notes

Dory is a static Sketchfab embed on shared hosting.

**In scope:** misconfigurations that expose private files, deploy workflow issues that could leak credentials, and XSS or injection introduced by changes to `index.html` or server config.

**Out of scope:** social engineering, denial-of-service, and vulnerabilities in third-party services (Sketchfab) unless introduced by this repo’s integration.

## Safe harbor

We appreciate responsible disclosure and will not pursue action against researchers who act in good faith and follow this policy.
