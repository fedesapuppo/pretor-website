# Notes for Claude working on this site

## There is no Astro source

`index.html` is compiled Astro output (`data-astro-cid-*` attributes,
minified inline scripts). The source project was never committed and is
gone. Do not try to "regenerate" the page or set up an Astro build to
match it: edit `index.html` and the CSS in `_astro/` directly.

The stylesheets load in this order and later ones override earlier ones:

1. `_astro/index.edUtr7Fi.css` — the original Astro build output
2. `_astro/pretor-refine.css` — hand-written refinements
3. `_astro/pretor-intro.css` — the curtain-reveal intro

Put new rules in `pretor-refine.css` unless they belong to the intro.

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
