# Rinux Site

This repository (`rinux-site`) publishes the Rinux website and package registry.

- **Landing page**: `https://rinux.pascalparent.ca/`
- **Registry**: `https://rinux.pascalparent.ca/packages/registry.json`

## Layout

```
CNAME                            → custom domain for GitHub Pages
.github/workflows/
  deploy-pages.yml               → deploys site to GitHub Pages on push main
packages/
  index.html                     → landing page (promoted to site root on deploy)
  registry.json                  → registry consumed by rpkg
  release.json                   → latest ISO release metadata (written by Rinux CI)
  releases/
    rinux-latest.iso             → stable alias, overwritten on every non-prerelease
    rinux-latest.iso.sha256
    rinux-<tag>.iso              → versioned snapshots
    rinux-<tag>.iso.sha256
  pkgs/*.tar                     → package archives downloaded by rpkg install
  _config.yml                    → GitHub Pages config (unused with static deploy)
  README.md                      → rpkg integration docs
```

The `packages/` directory is the web root. On deploy, `index.html` is promoted
to the site root so the landing page is served at `/` while the registry,
release metadata, and archives remain under `/packages/`.

## Release publishing

Because the Rinux source repository is private, ISO assets cannot be served
from GitHub Releases. Instead, the Rinux CI (`build-iso.yml`) clones this
repository on each published release and commits the ISO under
`packages/releases/` along with an updated `packages/release.json`. The landing
page reads that JSON at runtime to show version, size, date, and SHA256.

The publishing step uses a PAT stored as `SITE_DISPATCH_TOKEN` in the Rinux
repository secrets (fine-grained token with `contents:write` on
`Pascal1132/rinux-site`).

## Local changes

Update files in `packages/`, then push `main` to trigger Pages deployment.