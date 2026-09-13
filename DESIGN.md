---
name: Pretor
description: Marketing site and legal pages for Pretor, an AI system for Argentine law firms.
colors:
  stone: "#f5f5f5"
  stone-2: "#ebebeb"
  stone-card: "#ffffff"
  ink: "#111111"
  muted: "#4d4d4d"
  line: "#d4d4d4"
  black: "#0a0a0a"
  panel: "#141414"
  panel-2: "#1a1a1a"
  dline: "#2b2b2b"
  marble: "#f2f2f2"
  dtext: "#cccccc"
  dmuted: "#a3a3a3"
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
    backgroundColor: "{colors.ink}"
    textColor: "{colors.stone}"
    rounded: "{rounded.sm}"
    padding: ".85em 1.6em"
  button-primary-hover:
    backgroundColor: "{colors.muted}"
  button-primary-dark:
    backgroundColor: "{colors.marble}"
    textColor: "{colors.black}"
    rounded: "{rounded.sm}"
    padding: ".85em 1.6em"
  button-ghost:
    textColor: "{colors.ink}"
    rounded: "{rounded.sm}"
    padding: ".85em 1.6em"
  access-chip-yes:
    backgroundColor: "{colors.ink}"
    textColor: "{colors.stone}"
    rounded: "{rounded.pill}"
  access-chip-no:
    textColor: "{colors.ink}"
    rounded: "{rounded.pill}"
---

# Design System: Pretor

## Overview

**Creative North Star: "The Printed Brief"**

Black ink on white paper, and its negative on the dark bands. The site reads like a well-set legal
document: a Roman capital face for the things that carry authority, a plain sans for the argument,
a monospace for what the machine does. There is no brand colour. Hierarchy comes from size,
weight, case, rules and the light-against-dark banding, never from hue. The one colour on the page
is the gold Justitia emblem, a raster asset, which is why it reads as a seal.

The owner set the black-and-white direction on this ticket (PRE-85) and ruled out borrowing a
competitor's palette. Every value below is a neutral grey; nothing is tinted.

**Key Characteristics:**
- Two grounds only: light (`stone`, `stone-2`, white cards) and dark (`black`, `panel`).
- Meaning never rides on colour alone: state is fill, outline or dash.
- Flat. One soft neutral shadow for raised grids; no glows, no gradients, no grain.
- Self-hosted type: Cinzel, Inter, JetBrains Mono. No external asset.

## Colors

A strict neutral scale, one ramp per ground.

### Neutral
- **Paper** (`stone`): page ground of light sections and the legal pages.
- **Paper Shade** (`stone-2`): the alternate light band, table heads.
- **Sheet** (`stone-card`): cards, FAQ items, tables on light ground.
- **Ink** (`ink`): text, primary buttons, rules that carry emphasis, the focus ring on light.
- **Graphite** (`muted`): secondary text on light (7:1 on Paper Shade).
- **Hairline** (`line`): borders and dividers on light.
- **Night** (`black`): dark bands, nav, footer, the demo chat.
- **Panel** (`panel`, `panel-2`): cards and bubbles on dark.
- **Dark Hairline** (`dline`): borders on dark.
- **Chalk** (`marble`): text, primary buttons and the focus ring on dark.
- **Soft Chalk** (`dtext`): long body text on dark cards.
- **Ash** (`dmuted`): secondary text on dark (at least 6.9:1 on every dark ground).

### Named Rules
**The No-Hue Rule.** No colour value outside this ramp. If something needs to stand out, give it
weight, size, an ink fill or an outline.

**The Seal Rule.** Gold exists only inside the emblem image. It is never a CSS value.

## Typography

**Display Font:** Cinzel (with Times New Roman)
**Body Font:** Inter (with system-ui)
**Label/Mono Font:** JetBrains Mono (with ui-monospace)

**Character:** Roman capitals for authority, a neutral grotesque for the argument, a monospace for
the machine's own voice.

### Hierarchy
- **Display** (500, `--step-4`, 1.08): the hero h1 only. Emphasis inside it is weight 600, not colour.
- **Headline** (500, `--step-3`): h2 on light sections. Dark sections set h2 in Inter 600 instead.
- **Title** (500, `--step-1`): card and step titles in Cinzel; capability and security titles in Inter 600.
- **Body** (400, `--step-0`, 1.65): prose, capped at 56 to 74ch.
- **Label** (`--step--1`, mono or tracked caps): eyebrows, captions, chips. Never below 0.72rem.

### Named Rules
**The 12px Floor Rule.** Functional text (chips, tags, timestamps) is at least 0.72rem. Sentence-long
tags stay in sentence case; uppercase is for labels of a few words.

## Layout

A single 1180px column with `clamp()` side padding. Sections alternate light and dark bands with
`clamp(4rem, 9vw, 8rem)` vertical padding. Grids of cards share 1px gaps on a hairline ground
rather than floating cards. The nav collapses to a toggle below 860px; tables restack below 700px.
Anchored sections clear the sticky nav through `scroll-padding-top: 5.5rem` on `html`.

## Elevation & Depth

Flat by default. Raised grids on light ground carry one neutral shadow; buttons carry a small dark
one. Depth on dark bands comes from the step between Night and Panel, not from light effects.

### Shadow Vocabulary
- **Sheet lift** (`box-shadow: 22px 40px -28px rgba(0, 0, 0, .22)`): the marco, agents, security,
  steps and versus grids, and the demo chat.

### Named Rules
**The No-Glow Rule.** No zero-offset or coloured shadows, no radial spotlights, no film grain.

## Shapes

Gently rounded containers (12px), buttons and fields at 8px, chips and tags as full pills. The demo
chat's device frame is 16px; QR plates and photo frames 4px, portraits 2px. Rules are 1px. No side stripes thicker than 1px on cards or callouts.

## Components

### Buttons
- **Shape:** gently rounded (8px).
- **Primary:** Ink fill with Paper text on light; Chalk fill with Night text on dark. One primary per group.
- **Hover / Focus:** hover lifts 2px and softens the fill; focus is a 2px ring in Ink on light and Chalk on dark, offset 3px.
- **Ghost:** 1px outline in the text colour, no fill.

### Access chips (P/U/X)
The signature component. Three states, readable in greyscale:
- **Sí:** solid Ink pill, Paper text (inverted to Chalk on the leader card and the dark table).
- **No:** 1px solid outline.
- **Partial:** 1px dashed outline.

### Cards / Containers
- **Corner Style:** 12px on the outer grid, square inside it.
- **Background:** Sheet on light, Panel on dark.
- **Border:** 1px Hairline or Dark Hairline.
- **Internal Padding:** `clamp(1.6rem, 3vw, 2.6rem)`.

### Navigation
Night band, Chalk wordmark in tracked Cinzel, Ash links that turn Chalk on hover, and an outlined
pill for "Registrarse". Mobile uses a toggle and a stacked panel.

### Demo chat
A Night device frame. Outgoing bubbles are Chalk with Night text, incoming are Panel with a hairline.
System lines are dashed pills. "Aprobar" is the only filled control.

## Do's and Don'ts

### Do:
- **Do** mark state with fill, outline or dash, and keep the text label that names it.
- **Do** keep the focus ring 2px Ink on light and Chalk on dark.
- **Do** keep the emblem as the only coloured element.
- **Do** keep every font self-hosted in `_astro/fonts/`.

### Don't:
- **Don't** reintroduce gold, oxblood or cream as CSS values.
- **Don't** add glows, radial gradients, grain or double frames.
- **Don't** use a border wider than 1px on one side of a card or callout.
- **Don't** set functional text below 0.72rem or sentence-long tags in uppercase.
- **Don't** change copy to fix a design problem; wording belongs to PRE-42.
