# Yotoda — yotoda.tech

Studio landing site for **Yotoda** — a senior San Francisco studio that
designs, builds, and ships production-grade AI, blockchain, and SaaS products.

## What this is

A pre-built **Vite + React single-page app**. The site is fully static:
`index.html` + hashed `assets/*` (one JS bundle, one CSS bundle) + `favicon.svg`.
No server, no API, no build step required to deploy — `dist/` is the shippable artifact.

## Provenance

Forked from the 7stars.dev studio site (same design system, `@hanzo/ui` / gui.dev
primitives) and rebranded to Yotoda: wordmark, `<title>`, meta/OG/Twitter tags,
hero + section copy, contact emails (`a@`, `hello@`, `hire@` `@yotoda.tech`),
LinkedIn, blog URLs, and the `localStorage` theme key (`yotoda-theme`). Design,
layout, and animations are unchanged.

## Deploy

Cloudflare Pages, project `yotoda`, custom domains `yotoda.tech` + `www.yotoda.tech`.

    wrangler pages deploy dist --project-name yotoda --branch main

`dist/` is served directly. SPA fallback (unknown paths → `index.html`) is handled
by Pages' `_redirects`.

## Structure

    dist/
      index.html                 # SPA shell — title/meta/OG, theme bootstrap
      favicon.svg                # star-cluster mark
      assets/index-*.js          # React app bundle (all copy inlined)
      assets/index-*.css         # styles
      _redirects                 # SPA fallback for Pages
