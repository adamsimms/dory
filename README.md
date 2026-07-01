# Dory

[![Deploy](https://github.com/adamsimms/dory/actions/workflows/deploy.yml/badge.svg)](https://github.com/adamsimms/dory/actions/workflows/deploy.yml)

Interactive 3D dory boat — live at [pinchards.is/dory/](https://www.pinchards.is/dory/), model on [Sketchfab](https://sketchfab.com/models/579758d4c7d3419cac6b380877ead206) (CC BY 4.0).

Related: [pinchards.is](https://github.com/adamsimms/pinchards.is), [Adrift](https://github.com/adamsimms/adrift), [Waves](https://github.com/adamsimms/waves).

## Local dev

```bash
python3 -m http.server 8080
```

Open [http://localhost:8080/](http://localhost:8080/). No build step or secrets.

## Deploy

Push to `main` rsyncs to `pinchards.is/dory/` on DreamHost. The parent pinchards.is deploy excludes `dory/`, so these workflows do not conflict.

Reuse the DreamHost secrets from pinchards.is:

| Secret | Notes |
|--------|--------|
| `FTP_SERVER` | SSH hostname only — no `user@`, port, or path |
| `FTP_USERNAME` | Shell user |
| `FTP_SERVER_DIR` | Site root, e.g. `/home/USER/pinchards.is` (workflow appends `/dory/`) |
| `SSH_DEPLOY_KEY` | ed25519 private key — PEM or base64 single line |

Dry run: **Actions → Deploy → Run workflow** with `dry_run: true`.
