# Dory

Sketchfab 3D model embed — live at [pinchards.is/dory/](https://www.pinchards.is/dory/).

## Deploy

On **push to `main`**, `.github/workflows/deploy.yml` rsyncs this repo to `dory/` on DreamHost (same server as [pinchards.is](https://github.com/adamsimms/pinchards.is)).

### Repository secrets

Reuse the DreamHost deploy secrets from pinchards.is:

| Secret | Notes |
|--------|--------|
| `FTP_SERVER` | SSH hostname |
| `FTP_USERNAME` | Shell user |
| `FTP_SERVER_DIR` | Site root, e.g. `/home/USER/pinchards.is` (workflow appends `/dory`) |
| `SSH_DEPLOY_KEY` | ed25519 private key (base64-encoded single line) |

Use **Actions → Deploy SFTP → Run workflow** with `dry_run: true` to preview changes.

## Local dev

Serve the folder with any static server, e.g.:

```bash
python3 -m http.server 8080
```

Open `http://localhost:8080/`.
