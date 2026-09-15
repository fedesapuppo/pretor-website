---
name: Pretor
description: Marketing site and legal pages for Pretor, an AI system for Argentine law firms.
colors:
  stone: "#f4f0e8"
  stone-2: "#ece6d8"
  stone-card: "#fbf8f1"
  ink: "#1a1a1a"
  muted: "#5b5852"
  oxblood: "#6e2233"
  oxblood-soft: "#8f3b4d"
  line: "#d8cfba"
  black: "#0c0a08"
  panel: "#15110b"
  panel-2: "#19140d"
  dline: "#2a241a"
  marble: "#f0ebdf"
  dmuted: "#a89e8a"
  gold: "#cda455"
  gold-soft: "#e3ca8f"
  button-ink: "#16130b"
  dark-text-leader: "#d9d4c8"
  dark-text-card: "#c4bba8"
  dark-text-security: "#b6ac98"
  dark-text-chat: "#d9d0bd"
  qr-plate: "#ffffff"
  status-partial-tint: "#8a6a1f"
  status-yes: "#8c3a3a"
  status-no: "#33684a"
  status-partial: "#7a5b18"
  status-yes-dark: "#e7a3a3"
  status-no-dark: "#8fd6a8"
typography:
  display:
    fontFamily: "Cinzel, Times New Roman, serif"
    fontSize: "clamp(2.6rem, 2rem + 3vw, 4.6rem)"
    fontWeight: 500
    lineHeight: 1.08
    letterSpacing: "0.01em"
  headline:
    fontFamily: "Cinzel, Times New Roman, serif"
    fontSize: "clamp(2rem, 1.6rem + 2vw, 3.2rem)"
    fontWeight: 500
    lineHeight: 1.08
  headline-dark:
    fontFamily: "Inter, system-ui, sans-serif"
    fontSize: "clamp(2rem, 1.6rem + 2vw, 3.2rem)"
    fontWeight: 600
    lineHeight: 1.12
    letterSpacing: "-0.01em"
  body:
    fontFamily: "Inter, system-ui, sans-serif"
    fontSize: "clamp(.95rem, .9rem + .25vw, 1.05rem)"
    fontWeight: 400
    lineHeight: 1.65
  label:
    fontFamily: "JetBrains Mono, ui-monospace, monospace"
    fontSize: "clamp(.78rem, .74rem + .18vw, .88rem)"
    fontWeight: 400
rounded:
  photo: "2px"
  plate: "4px"
  icon: "6px"
  sm: "8px"
  md: "12px"
  device: "16px"
  pill: "999px"
spacing:
  pad-x: "clamp(1.25rem, 5vw, 4rem)"
  section-y: "clamp(4rem, 9vw, 8rem)"
  max-width: "1180px"
components:
  button-primary:
    backgroundColor: "{colors.gold}"
    textColor: "{colors.button-ink}"
    rounded: "{rounded.sm}"
    padding: ".85em 1.6em"
  button-primary-hover:
    backgroundColor: "{colors.gold-soft}"
  button-ghost:
    textColor: "{colors.ink}"
    rounded: "{rounded.sm}"
    padding: ".85em 1.6em"
  button-ghost-dark:
    textColor: "{colors.marble}"
    rounded: "{rounded.sm}"
    padding: ".85em 1.6em"
  access-chip-yes:
    textColor: "{colors.status-yes}"
    rounded: "{rounded.pill}"
  access-chip-no:
    textColor: "{colors.status-no}"
    rounded: "{rounded.pill}"
  access-chip-partial:
    textColor: "{colors.status-partial}"
    rounded: "{rounded.pill}"
---

# Design System: Pretor

## Overview

**Creative North Star: "Lex Antiqva, Mens Nova"**

Two worlds on one page. The Roman one: warm stone paper, Cinzel capitals, oxblood accents, maxims in
Latin. The machine one: warm near-black bands, Inter and JetBrains Mono, gold as patina. The page
alternates them band by band, and the hero diptych sets them side by side. Gold carries the brand
across both, from the Justitia emblem to the primary buttons.

This palette is an owner decision. A black-and-white pass was built on 2026-09-12 and reversed on
2026-09-13 because it read as another legal product's site; the palette below is the one on main,
kept as is. The logo changed on 2026-09-15 (PRE-215) and the palette did not; the intro art
changes later, under its own ticket, not here.

Every value in this file is read from `_astro/pretor.css`. Section 1 of that sheet declares the
tokens and section 2's "Palette retune" overrides most of them; the frontmatter lists the values
that ship, which are the retuned ones.

**Key Characteristics:**
- Light bands in warm stone with oxblood accents; dark bands in warm near-black with gold accents.
- One gold primary button on every ground.
- Atmosphere by design: faint film grain, soft radial glows on dark bands, gold hairline seams.
- Self-hosted type: Cinzel, Inter, JetBrains Mono. No external asset.

## Colors

A warm two-ground palette: stone and oxblood, near-black and gold.

### Primary
- **Patina Gold** (`gold`): primary buttons, dark-band eyebrows and accents, plan prices, the focus ring on dark grounds.
- **Soft Gold** (`gold-soft`): primary button hover, secondary accents on dark.

### Secondary
- **Oxblood** (`oxblood`): light-band eyebrows, the emphasised words of the h1, numerals, link text and underlines on light, the hero's trust lines and step numbers, the focus ring on light grounds.
- **Soft Oxblood** (`oxblood-soft`): link hover on light.

### Neutral
- **Stone** (`stone`), **Stone Shade** (`stone-2`), **Card** (`stone-card`): light grounds and cards.
- **Ink** (`ink`): text on light; the leader agent card's ground.
- **Muted** (`muted`): secondary text on light.
- **Hairline** (`line`): borders on light.
- **Night** (`black`), **Panel** (`panel`, `panel-2`): dark grounds and cards.
- **Dark Hairline** (`dline`): borders on dark.
- **Marble** (`marble`): text on dark.
- **Dark Muted** (`dmuted`): secondary text on dark.
- **Button Ink** (`button-ink`): text on gold buttons.
- **Warm Parchment greys** (`dark-text-leader`, `dark-text-card`, `dark-text-security`, `dark-text-chat`): body text on the leader card, capability cards, security promises and chat bubbles, each set as a literal in the CSS.
- **QR Plate** (`qr-plate`): the white behind each QR code, so a camera can read it on any ground.

### Status
The P/U/X access chips and the trifecta table mark exposure by hue, always next to a text label
("Sí", "No", "Transitorio"). Light cards use `status-yes`, `status-no` and `status-partial` on a
10-12% tint of the same hue; the dark table uses `status-yes-dark`, `status-no-dark` and `gold-soft`.

### Named Rules
**The Two Grounds Rule.** Gold text belongs on dark grounds, oxblood on light ones. Gold on stone
measures 2.04:1 and fails; oxblood on stone measures 9.53:1.

## Typography

**Display Font:** Cinzel (with Times New Roman)
**Body Font:** Inter (with system-ui)
**Label/Mono Font:** JetBrains Mono (with ui-monospace)

**Character:** Roman capitals for authority on light bands, a neutral grotesque for the argument,
a monospace for the machine's own voice on dark bands.

### Hierarchy
- **Display** (500, `--step-4`, 1.08): the hero h1.
- **Headline** (500, `--step-3`): h2 on light bands in Cinzel; dark bands set h2 in Inter 600.
- **Title** (500, `--step-1`): card and step titles.
- **Body** (400, `--step-0`, 1.65): prose. Measures: lead 56ch, trifecta explanation and plan terms 56ch, legal prose 64ch.
- **Label** (`--step--1`): tracked uppercase eyebrows on light, mono eyebrows on dark.

### Named Rules
**The 12px Floor Rule.** Functional text is at least 0.72rem: access chips and agent tags 0.75rem,
demo timestamps and the document icon 0.72rem. Sentence-long agent tags are in sentence case.

## Layout

A 1180px column with `clamp()` side padding, bands of `clamp(4rem, 9vw, 8rem)`. Card grids share 1px
gaps on a hairline ground. The nav collapses below 860px; the versus table restacks below 700px with
its row labels at full width. Anchors clear the sticky nav with `scroll-padding-top: 5.5rem` on `html`.

## Elevation & Depth

Layered and warm. Raised grids on light carry a warm shadow; dark bands get depth from radial
glows and a faint grain over the whole page.

### Shadow Vocabulary
- **Sheet lift** (`box-shadow: 22px 40px -28px rgba(40, 24, 12, .35)`): marco, agents, security, steps and versus grids, and the demo chat.
- **Gold lift** (`box-shadow: 0 12px 30px -14px` gold at 65%): the primary button on dark bands; the featured plan carries a wider gold shadow.

## Shapes

Containers 12px, buttons 8px, the demo chat 16px, chips and tags full pills, QR plates and photo
frames 4px, portraits 2px. Seams between light and dark bands, the hero seam and the capability
card hover bar are solid gold lines.

## Components

### Buttons
- **Primary:** Patina Gold with Button Ink text on every ground; hover Soft Gold and a 2px lift.
- **Ghost:** 1px Ink outline on light; Marble text with a Dark Hairline outline on dark, gold border on hover.
- **Focus:** a 2px ring offset 3px, Oxblood on light grounds, Gold on dark bands, the nav, the legal nav, the leader agent card and the intro.

### Access chips (P/U/X)
Mono pills at 0.75rem in the status colours, each with its text label. On the leader card the partial
chip turns Soft Gold on a gold tint.

### Cards / Containers
Card (`stone-card`) on light, Panel on dark, 1px hairline borders, internal padding `clamp(1.6rem, 3vw, 2.6rem)`.

### Navigation
A translucent Night band with a gold hairline under it, Marble wordmark in tracked Cinzel, Dark Muted
links, and a gold outlined pill for "Registrarse".

### Mark
The brushed-gold Justitia, cut out of the owner's logo with its marble removed, on dark grounds only:
nav, legal nav, hero, contacto, footer and the intro loader. The favicon is the scales alone on a
Night rounded tile, because the whole figure does not read at 16px and bare gold vanishes on a light
tab. `og.jpg` is the whole logo, wordmark included, on Night.

### Demo chat
A Night device frame with a gold avatar. Outgoing bubbles are oxblood mixed into Night, incoming are
Panel 2; system lines are dashed gold pills; "Aprobar" is the only gold filled control.

## Do's and Don'ts

### Do:
- **Do** keep gold text on dark grounds and oxblood text on light ones.
- **Do** keep the focus ring Oxblood on light and Gold on dark.
- **Do** keep every status chip's text label; the hue is never the only signal.
- **Do** keep every font self-hosted in `_astro/fonts/`.

### Don't:
- **Don't** change the palette to black and white or any other scheme without the owner; it was tried and reversed on 2026-09-13.
- **Don't** touch the intro art here; it changes under its own ticket.
- **Don't** put the transparent Justitia on a light ground or rasterise the PRETOR wordmark beside it; the CSS text is the wordmark.
- **Don't** set functional text below 0.72rem or sentence-long tags in uppercase.
- **Don't** change copy to fix a design problem; wording belongs to PRE-42.
