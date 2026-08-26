# Notes for Claude working on this site

## There is no Astro source

`index.html` is compiled Astro output (`data-astro-cid-*` attributes).
The source project was never committed and is gone. Do not try to
"regenerate" the page or set up an Astro build to match it: edit
`index.html` and the CSS in `_astro/` directly. Both are formatted as
readable source, and they are the source. Keep them readable: the page
shipped minified until PRE-85, and a change to a 17KB line cannot be
reviewed.

There are two stylesheets, and only one of them holds design rules:

1. `_astro/fonts.css` — `@font-face` only, paired with the `<link
   rel="preload">` tags in the head
2. `_astro/pretor.css` — everything else, in cascade order

`pretor.css` is one file in three clearly marked sections, in the order
the three old sheets used to load: the compiled Astro build, then the
hand-written refinements over it, then the intro. Later sections still
override earlier ones, so put a new rule in section 2 unless it belongs
to the intro, and never reorder the sections.

## The legal pages

`privacidad/index.html` and `terminos/index.html` are hand-written, not
Astro output, and they are the only other pages here. Three things point
at them and each one breaks differently if a URL moves, so the paths
`/privacidad/` and `/terminos/` are fixed:

1. the footer of `index.html`
2. the sign-up form at `app.pretor.ar` (`pretor-rails`,
   `app/views/registrations/new.html.erb`), whose spec asserts both
   absolute URLs, because the terms claim that creating the account
   accepts them
3. the Terms of service URL and Privacy statement URL fields of the Entra
   application registration, which is what stops the Outlook consent
   screen from saying "the publisher has not provided links to their
   terms"

They load `fonts.css` and `pretor.css` like the landing page and reuse
`.wrap`, `.section--stone`, `.eyebrow`, `.display`, `.lead` and the whole
footer. Those last selectors are attribute-scoped, so the legal pages
copy the `data-astro-cid-*` values the stylesheet matches on. That is not
a mistake to clean up: the attributes ARE the selectors. Their own rules
are section 2's subsection 16 (`.legal*`), not a third stylesheet.

The facts in them are checked against code the same way `#seguridad` is:
the proveedores table against what `src/` actually calls, and the
retention section against
`pretor-mastra/docs/plans/2026-08-21-tenant-lifecycle.md`, including its
thirty-day observability exception. Do not soften that exception; a
policy that claims total erasure while the spans still hold case text is
worse than one that bounds the gap.

## Asset paths are root-absolute

Everything references `/_astro/...` and `/favicon.png`. The site is served
at the root of pretor.ar, so keep paths absolute. They were `/pretor/...`
while the page lived inside personal-website; that prefix is gone along
with the `_redirects` rewrite that supported it.

## Intro animation

`_astro/pretor-intro.js` replays the curtain intro on every load. It was
deliberately changed from a video to a still image because the video was
soft on load. Verify any intro change in a real browser, on mobile width
too.

## The prices in `index.html` are a copy

The `#planes` section hardcodes the four abonos, the three bonus
percentages, the derived allowances and the two reload packs. They are
NOT the source of truth. The price list lives in
`pretor-mastra/src/billing/plans.ts` (`PLANS`, `CREDIT_PACKS`), and
`app.pretor.ar/planes` renders it live from core's catalog with nothing
typed in.

That makes this file a second place for the price to live, accepted
deliberately: a marketing page with no numbers converts badly. The cost
is that a price change is a two-repo change. When `PLANS` moves, edit
`#planes` and the `¿Cuánto cuesta?` FAQ entry in the same pass.

Two things the copy must keep, because they are decisions and not
phrasings (`docs/plans/2026-08-10-planes-y-precios.md`):

- The abono buys 30 days from the day it is paid, never a calendar
  month. Say "cada 30 días", never "por mes".
- Escrito counts are averages over one lawyer's own work, so they must
  stay hedged: "alrededor de 11 escritos", never "11 escritos". The plan
  document writes this rule as keep-the-word-"unos"; the wording was
  changed on 2026-08-10 and the rule is the hedge, not that one word.

The promo line names 100 estudios and $5.000 but deliberately shows no
remaining count: a static page cannot count, and a stale number on a
scarcity claim is worse than no number. The live counter is on
`app.pretor.ar/planes`, which the line links to.

## Claims about isolation are checked against code, not against memory

The `#seguridad` promises, the trifecta table and the `#diferencia`
comparison each name a mechanism that exists in `pretor-mastra`:
`src/tenancy/` for the per-tenant split and the fail-closed stamp,
`test/mastra/isolation.test.ts` for the one-reader-per-store claim and
every P/U/X cell, `src/system/today.ts`, `normas.ts`, `articulos.ts`,
`atribuciones.ts` for the four freshness controls, and
`src/research/provenance.ts` for what the Investigador may assert.

Before editing any of them, open the file. Do not add a claim about a
certification, an audit, a compliance standard or a vendor's training
policy: none of those is ours to make, and none is checkable here.

Two things in the legal text that look like omissions but are decisions, verified against official sources:

- The policy deliberately OMITS the "free access at intervals of no less than six months" clause.
  Disposición DNPDP 10/2008 required it; Resolución AAIP 14/2018 repealed that requirement, and
  today only the Data Protection Authority clause is mandated, which the policy does carry.
  Point 8 instead states that we do not charge and do not invoke that interval. Do not restore the
  clause as if it were still mandatory.
- The terms deliberately omit a waiver of every other forum. This is an adhesion contract
  (art. 984 CCyC), and art. 988 inc. b renders clauses restricting the adherent's rights void,
  whether or not Ley 24.240 is at stake. Point 11 expressly yields to art. 1109 CCyC.

## Language

Only user-facing page copy is Spanish. Commit messages, this file and any other
agent-facing notes are English, always. Decided 2026-08-26 after the same
mistake had to be filtered out of pretor-mastra's git history.
