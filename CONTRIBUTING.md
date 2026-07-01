# Contributing

Thanks for your interest in **Dory** — a fullscreen interactive 3D boat model embedded from Sketchfab.

This is a small personal project, but focused improvements are welcome.

## Good first contributions

- Documentation fixes and clarifications
- Accessibility (iframe titles, semantic HTML, keyboard-friendly embed options)
- SEO metadata improvements
- Performance (cache headers, embed load tuning)
- Bug fixes with clear reproduction steps

## Before you start

1. **Search existing issues** — someone may already be working on it.
2. **Open an issue** for non-trivial changes so we can agree on approach before you invest time.
3. **Keep scope small** — one logical change per pull request.

## Development setup

See the [README local development section](README.md#local-development).

```bash
git clone https://github.com/adamsimms/dory.git
cd dory
python3 -m http.server 8080
```

Open [http://localhost:8080](http://localhost:8080). No secrets or build step required.

## Code conventions

Match the existing style in the files you touch:

- **HTML:** Semantic structure, two-space indentation, meaningful `title` and meta tags.
- **CSS:** Keep the fullscreen embed layout simple; avoid unnecessary frameworks.
- **Deploy:** Workflow changes should mirror validation patterns in [pinchards.is](https://github.com/adamsimms/pinchards.is) and [adrift](https://github.com/adamsimms/adrift).
- **Secrets:** Never commit deploy keys or server passwords.

## Pull requests

- Describe what changed and why.
- Note if you tested locally (static server) or ran a deploy dry-run.
- Link related issues when applicable.

## Security

See [SECURITY.md](SECURITY.md). Do not file public issues for vulnerabilities — use GitHub private vulnerability reporting.

## License

By contributing, you agree that your contributions are licensed under the [MIT License](LICENSE), except where they incorporate the separately licensed Sketchfab 3D model.
