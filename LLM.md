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

Cloudflare **Worker with static assets** (the account's Pages project limit was
reached, so we use the same mechanism that serves 7stars.dev). Config in
`wrangler.toml`: assets from `./dist`, SPA fallback via
`not_found_handling = "single-page-application"`.

    wrangler deploy

Auth: `CLOUDFLARE_EMAIL` + `CLOUDFLARE_API_KEY` (global key) or a scoped token.
Custom domains `yotoda.tech` + `www.yotoda.tech` are bound to the `yotoda` Worker
(Workers → Domains). Public resolution requires the yotoda.tech registrar
nameservers to be delegated to Cloudflare — a one-time registrar action.

Default deploy URL: https://yotoda.zeekay.workers.dev

## Structure

    dist/
      index.html                 # SPA shell — title/meta/OG, theme bootstrap
      favicon.svg                # star-cluster mark
      assets/index-*.js          # React app bundle (all copy inlined)
      assets/index-*.css         # styles
