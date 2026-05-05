# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static single-page website for Inlet Arts (inlet-arts.org), a contemporary dance nonprofit on Seattle's Eastside. Served via GitHub Pages with no build step — changes to files are deployed directly.

## Development

To preview locally, serve the root directory with any static file server:

```bash
python3 -m http.server 8000
# or
npx serve .
```

There are no dependencies, build tools, linters, or tests.

## Architecture

Three files make up the entire site:

- **[index.html](index.html)** — single HTML file with all content. Sections (`#home`, `#programs`, `#about`, `#press`) are navigated via anchor links. The `#contact` section and team member photos are commented out pending future activation.
- **[styles.css](styles.css)** — all styles. CSS custom properties are defined in `:root` at the top.
- **[script.js](script.js)** — mobile menu toggle, smooth scroll, and IntersectionObserver-based active nav highlighting.

## Design system

Colors (defined as CSS vars):
- Navy `#1a2b3c` — primary text and CTAs
- Slate `#3d5166` — secondary/muted elements
- Mist `#f4f2ee` — light section backgrounds
- Sand `#e8e4dc` — image placeholders

Fonts loaded from Google Fonts:
- **Cormorant Garamond** — display/headings (`--font-display`)
- **DM Sans** — body text (`--font-body`)

Max content width is `900px` (`--max-w`). Responsive breakpoints at `768px` and `480px`.

## Image handling

Images live in `images/`. All `<img>` tags use `onerror` to add a fallback class (`.img-fallback` or `.hero-fallback`) that shows a sand-colored placeholder with "Photo coming soon" text via CSS `::after`. Team member photo `<img>` tags exist but are wrapped in HTML comments.

## Deployment

Push to `main` — GitHub Pages serves the site automatically. The `CNAME` file sets the custom domain to `inlet-arts.org`.
