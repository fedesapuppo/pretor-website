# Pretor — pretor.ar

Landing page for Pretor, the AI framework for law firms.

Live at [pretor.ar](https://pretor.ar/).

## What the product is

Pretor is an AI assistant for Argentine law firms: a coordinating agent ("Pretor")
leading a team of specialists (Investigador, Bibliotecario, per-fuero Escribientes,
Secretario, Relator, Procurador, Gestor). It researches law against official sources
(InfoLEG, SAIJ, CSJN, Boletín Oficial) with anti-hallucination controls, drafts
escritos on the firm's own models, tracks expedientes and procedural deadlines on the
judicial portals, keeps the firm's library and client ledger, and delivers documents
as real PDF/Word files.

Lawyers reach it on Telegram, WhatsApp, or the web app. It works with each lawyer's
own mailbox and, where the provider allows it, calendar: Gmail (app password),
Outlook personal (OAuth), and Zoho. Nothing is sent or filed without the lawyer's
approval; every action outward is gated.

Canonical documentation lives in two places:

- Lawyer-facing usage guide (connection steps, examples, pricing): pretor-rails,
  `app/views/guides/show.html.erb`, served at `/guia`.
- What Pretor knows about itself in conversation (capabilities, phrases, connection
  summaries): pretor-mastra, `src/system/overview.ts`, pinned by deriving tests so it
  cannot drift from the code.

This repo carries only the marketing landing page and the two legal pages.

## What this repo is

Static site: `index.html`, the two legal pages (`privacidad/index.html`
and `terminos/index.html`), and assets under `_astro/`. No build step, no
dependencies. Open `index.html` in a browser, or serve the directory:

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
