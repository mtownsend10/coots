# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A single-page static campaign site for **Mike Coots for Kauaʻi County Council (2026)**. No framework, no bundler, no package manager. Three hand-written files — `index.html`, `styles.css`, `script.js` — plus image assets in `assets/`.

## Running it locally

Any static server works. From the repo root:

```
python3 -m http.server 8000
# then open http://localhost:8000
```

Or just open `index.html` directly in a browser. There is no build step, no test suite, no linter.

## Architecture

The site is a single long document in `index.html`, section-by-section top to bottom:

`nav` → `hero` → `intro` (Meet Mike band) → `platform` (three prioritized issues) → `pullquote` → `about` (story) → `record` (legislative track record) → `whynow` → `endorsements` → `volunteer` (form) → `donate` → `footer`

Navigation is anchor-link only (`#platform`, `#about`, `#record`, `#endorsements`, `#volunteer`, `#donate`). When renaming/removing a section ID, update the nav and footer link lists in `index.html` to match.

`script.js` contains just two small IIFEs: a mobile nav toggle and donation-amount selection UI. There is no client-side state, routing, or data fetching — the volunteer form is a no-op that shows a thank-you message on submit (not wired to a backend).

`styles.css` is organized section-by-section matching `index.html`, with design tokens (colors, typography, spacing) defined as CSS custom properties under `:root` at the top. Fonts are Fraunces (serif, headings/italic emphasis) and Inter (sans, body) loaded from Google Fonts. The visual system is editorial and ocean-forward: ink/sand/sunset palette, large serif display type with italicized emphasis clauses.

## Content conventions

- The platform's three priorities are deliberately ordered (Housing → Infrastructure → Homelessness). The ordering and "In this order" framing is load-bearing messaging — don't reorder without intent.
- Hawaiian place names use `ʻokina`: Kauaʻi, Kīlauea, Līhuʻe, Kapaʻa, Kōloa, Hāʻena, Kūhiō. Preserve them when editing copy.
- Use HTML entities for curly quotes/em-dashes (`&rsquo;`, `&mdash;`, `&ldquo;`, `&rdquo;`, `&ndash;`) to match the existing style.
- Endorsement cards currently use `[Endorser name]` / `[Title / organization]` placeholders — they are intentional until real endorsements land.

## Git hygiene

`.gitignore` excludes `*.png` at the repo root (those are design iteration screenshots from Playwright/manual review — not site assets). Real site images live in `assets/` and are committed. Do not move working imagery out of `assets/`.
