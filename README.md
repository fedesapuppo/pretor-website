# Pretor — pretor.ar

Landing page for Pretor, the AI framework for law firms.

Live at [pretor.ar](https://pretor.ar/).

## What this repo is

Static site: a single `index.html` plus assets under `_astro/`. No build
step, no dependencies. Open `index.html` in a browser, or serve the
directory:

```bash
python3 -m http.server 4321
```

Paths are root-absolute (`/_astro/...`), so serve from the repo root
rather than opening the file directly if you want the assets to resolve.

## Origin

The page was originally built with Astro and lived at
`fedesapuppo.com/pretor/` inside the
[personal-website](https://github.com/fedesapuppo/personal-website) repo.
This repo carries that history over (paths rewritten to the root) and the
old location now redirects here.

The Astro source was never committed and no longer exists. What ships here
is the compiled output: `index.html` is generated markup with
`data-astro-cid-*` attributes, and `_astro/pretor.css` carries the Astro
build together with the hand-written overrides that were layered on it.
Both are formatted as readable source and are edited directly.

## Deployment

Pushes to `main` deploy to GitHub Pages via
`.github/workflows/deploy.yml`, which writes the `pretor.ar` CNAME into
the artifact. DNS lives on Cloudflare.
