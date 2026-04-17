# Rinux Packages Site

This repository publishes the Rinux package registry at:

```text
https://rinux.pascalparent.ca/packages/registry.json
```

Site content is served from the `packages/` directory at the repository root.
Package archives live under `packages/pkgs/` and are deployed automatically to GitHub Pages on every push to `main`.

## Layout

- `CNAME`: custom domain for GitHub Pages
- `packages/registry.json`: registry consumed by `rpkg`
- `packages/pkgs/*.tar`: package archives downloaded by `rpkg install`

## Local changes

Update the registry and package archives in `packages/`, then push `main` to trigger Pages deployment.