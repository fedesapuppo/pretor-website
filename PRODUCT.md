# Product

<!-- impeccable:product-schema 1 -->

Written 2026-09-12 by an autonomous lane (PRE-85) from repository evidence, without an owner
interview. Every fact below cites where it came from. Facts marked (inferred) were not stated
anywhere and wait for the owner to confirm.

## Platform

web

## Users

Argentine lawyers who are matriculados and sign their own escritos, working alone or in a small
estudio (index.html hero note, "Pretor es para abogados matriculados: redacta escritos que firma
usted"; plans priced per estudio with no seat limit, `#planes`). They run cases, deadlines,
clients and fees themselves, and much of their day is away from a desk, in courts and meetings
(the page's repeated "desde el teléfono" claim). The site visitor is that lawyer deciding whether
to create an account, usually on a phone (inferred from the product's Telegram and WhatsApp
channels).

## Product Purpose

Pretor is an AI system that runs an Argentine law firm's work: a coordinating agent leads a team
of specialists that research law against official sources, draft escritos on the firm's own
models, follow expedientes and deadlines on the judicial portals, and keep the library, clients and
fees (README.md; pretor-mastra `src/system/overview.ts`). Nothing is sent or filed without the
lawyer's approval. The site succeeds when a lawyer creates an estudio at
`app.pretor.ar/registration/new` or writes on WhatsApp.

## Positioning

Pretor competes on what the lawyer signs being true, not on the freshest index: it knows today's
date in every answer, keeps its own registry of norms changed after the model's cutoff, checks
national-code articles against official text, and its research may only back a claim of law with
a page it opened in the same consultation. All of it happens inside the case, with persistent
memory per expediente and express approval before anything goes out (pretor-mastra
`docs/research/2026-08-26-competitor-decisions.md`, "The paragraph"). Every such claim on the site
is checked against code (CLAUDE.md, "Claims about isolation").

## Operating Context

Lawyers reach Pretor on Telegram, WhatsApp or the web app, by text or voice, and it works with
their own mailbox and, where the provider allows, calendar (README.md). The judicial portals,
InfoLEG, SAIJ, CSJN and the Boletín Oficial are the sources it reads. Plans are bought per estudio
and each abono lasts 30 days from payment (CLAUDE.md, "The prices in index.html are a copy").

## Capabilities and Constraints

- Static site with no build step: `index.html` (compiled Astro output edited directly),
  `privacidad/`, `terminos/`, assets under `_astro/`, deployed to GitHub Pages on push to main.
- Fonts and every asset are self-hosted. No external asset may be added. The one external script
  is the Cloudflare analytics beacon, installed on purpose (comment in `index.html`).
- The cinematic intro must self-disable under `prefers-reduced-motion`, Save-Data and deep links.
- Wording is owned elsewhere (PRE-42). Design work changes no copy.
- The prices in `#planes` are a copy of pretor-mastra `src/billing/plans.ts`; the escrito counts
  stay hedged and the abono is "cada 30 días", never "por mes".
- Claims in `#seguridad`, `#diferencia` and the trifecta table name mechanisms that exist in
  pretor-mastra. No claim of a certification, audit or compliance standard.
- The legal page paths `/privacidad/` and `/terminos/` are fixed.

## Brand Commitments

- Name PRETOR, set in Cinzel capitals, with the brushed-gold Justitia emblem the owner delivered on
  2026-09-15 (`_astro/justitia.png`, `og.jpg`, `favicon.png`) and the Roman-law register: "Iura
  novit curia", "Dura lex, sed lex", "Fiat iustitia", "Lex antiqva, mens nova" (index.html, intro).
- Spanish of Argentina, formal usted throughout.
- The palette on main stays. A black-and-white pass was built on 2026-09-12 and the owner reversed
  it on 2026-09-13: it read as another legal product's site. The logo changed on 2026-09-15
  (PRE-215) and the palette did not.

## Evidence on Hand

- Named client: Cedap, Centro de Acuerdos Paraná (the `.proof` section under the hero).
- Quotes from "un usuario profesional del derecho", unnamed, as published.
- The two people behind it, with photos: Federico Sapuppo and Dr. Jesús Juan Ignacio Bornices
  (`#fundador`, `_astro/founder.jpg`, `_astro/bornices.jpg`).
- An illustrative, labelled Telegram conversation (`#demo`).
- No press, no metrics, no certifications, no customer logos. Do not invent any.

## Product Principles

1. Never invent the law: every claim of law cites a source that was opened and checked.
2. The lawyer approves everything that leaves the estudio.
3. Each estudio's data is separated by construction, and the site says only what code enforces.
4. The phone is the office: every flow must work on a small screen, by voice or text.

## Accessibility & Inclusion

Keep the skip link, the nav aria-labels, the noscript fallback and the reduced-motion paths that
already exist (PRE-85 acceptance criteria). Target WCAG 2.2 AA (inferred).
