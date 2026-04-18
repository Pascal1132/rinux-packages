# Rinux Site

This repository (`rinux-site`) publishes the Rinux website and package registry.

- **Landing page**: `https://rinux.pascalparent.ca/`
- **Registry**: `https://rinux.pascalparent.ca/packages/registry.json`

## Layout

```
CNAME                  → custom domain for GitHub Pages
packages/
  index.html           → landing page (copied to site root on deploy)
  registry.json        → registry consumed by rpkg
  pkgs/*.tar           → package archives downloaded by rpkg install
  _config.yml          → GitHub Pages config (unused with static deploy)
  README.md            → rpkg integration docs
```

The `packages/` directory is the web root. On deploy, `index.html` is promoted
to the site root so the landing page is served at `/` while the registry and
archives remain under `/packages/`.

## Local changes

Update files in `packages/`, then push `main` to trigger Pages deployment.