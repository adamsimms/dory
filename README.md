# Dory

[![Deploy SFTP](https://github.com/adamsimms/dory/actions/workflows/deploy.yml/badge.svg)](https://github.com/adamsimms/dory/actions/workflows/deploy.yml)

Fullscreen interactive 3D dory boat model — embedded from [Sketchfab](https://sketchfab.com/models/579758d4c7d3419cac6b380877ead206) and live at [pinchards.is/dory/](https://www.pinchards.is/dory/).

Related projects: [pinchards.is](https://github.com/adamsimms/pinchards.is) (parent site), [Adrift](https://github.com/adamsimms/adrift), [Waves](https://github.com/adamsimms/waves).

## Contents

- [Overview](#overview)
- [Project layout](#project-layout)
- [Local development](#local-development)
- [Deploy](#deploy)
- [SEO](#seo)
- [Contributing](#contributing)
- [Security](#security)
- [License](#license)

## Overview

Dory is a minimal static site: one HTML page, a small CSS file, and a Sketchfab iframe that fills the viewport. Visitors can rotate, zoom, and open the model in fullscreen or VR (where supported).

The 3D model ([Dory Boat on Sketchfab](https://sketchfab.com/models/579758d4c7d3419cac6b380877ead206)) is published under [CC Attribution 4.0](https://creativecommons.org/licenses/by/4.0/) by Adam Simms.

This repo deploys independently to `pinchards.is/dory/`. The parent [pinchards.is](https://github.com/adamsimms/pinchards.is) deploy excludes `dory/` so the two workflows do not overwrite each other.

## Project layout

| Path | Purpose |
|------|---------|
| **`index.html`** | Page shell, SEO metadata, Sketchfab embed |
| **`css/style.css`** | Full-viewport iframe layout |
| **`favicon/boat.svg`** | Tab icon |
| **`.htaccess`** | Apache security headers and cache hints |
| **`robots.txt`** | Crawler rules and sitemap pointer |
| **`sitemap.xml`** | Subsite URL for search engines |
| **`.github/workflows/deploy.yml`** | rsync deploy to DreamHost on push to `main` |

## Local development

Serve the repo root with any static file server:

```bash
python3 -m http.server 8080
```

Open [http://localhost:8080/](http://localhost:8080/). The Sketchfab embed loads from their CDN; no API keys or build step required.

## Deploy

On **push to `main`**, [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml) rsyncs this repository to `dory/` on DreamHost (same server as [pinchards.is](https://github.com/adamsimms/pinchards.is)).

### Repository secrets

Reuse the DreamHost deploy secrets from pinchards.is:

| Secret | Notes |
|--------|--------|
| `FTP_SERVER` | SSH hostname only (e.g. `iad1-shared-b8-36.dreamhost.com`) — no `user@`, port, or path |
| `FTP_USERNAME` | Shell user |
| `FTP_SERVER_DIR` | Absolute site root, e.g. `/home/USER/pinchards.is` (workflow appends `/dory/`) |
| `SSH_DEPLOY_KEY` | ed25519 private key — paste the PEM directly **or** a base64-encoded single line |

**One-time setup:** generate an ed25519 deploy key, append the public key to `~/.ssh/authorized_keys` on the server, and store the private key as `SSH_DEPLOY_KEY`.

### Dry run

Use **Actions → Deploy SFTP → Run workflow** with `dry_run: true` to preview rsync changes without modifying the server.

### Validation

The workflow checks that secrets are present, that `FTP_SERVER` is a bare hostname, that `FTP_SERVER_DIR` is an absolute path, and that the SSH key is valid before deploying.

## SEO

The page includes:

- Descriptive `<title>` and meta description
- Canonical URL (`https://www.pinchards.is/dory/`)
- Open Graph and Twitter Card tags (preview image from Sketchfab)
- JSON-LD structured data (`WebPage` + `3DModel`)
- `robots.txt` and `sitemap.xml` for crawlers

After deploy, consider adding `https://www.pinchards.is/dory/` to the parent site [sitemap.xml](https://github.com/adamsimms/pinchards.is/blob/main/sitemap.xml) and linking from an appropriate page on pinchards.is for discoverability.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Small, focused pull requests are welcome.

## Security

See [SECURITY.md](SECURITY.md). Report vulnerabilities through [GitHub private vulnerability reporting](https://github.com/adamsimms/dory/security/advisories/new) — not public issues.

## License

Site code is [MIT](LICENSE). The embedded 3D model is [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — see [LICENSE](LICENSE) for details.
