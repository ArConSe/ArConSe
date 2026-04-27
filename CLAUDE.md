# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

ArConSe is a static business website for a Philippine-based construction and renewable energy company. There is no build system, package manager, or framework — everything is plain HTML, CSS, and vanilla JavaScript, deployed via GitHub Pages.

## Development

To preview the site locally, open `index.html` directly in a browser or use any static file server:

```bash
python3 -m http.server 8080
# then open http://localhost:8080
```

There are no lint, test, or build commands.

## Architecture

### File Layout

- `index.html` — Single-page site with anchor-based navigation (`#services`, `#products`, `#projects`, `#contact`)
- `style.css` — All styling; brand color is orange `#f97316`, fonts are Poppins (headings) and Roboto (body)
- `script.js` — Mobile menu toggle, lightbox image viewer, smooth scroll
- `thankyou.html` — Redirect target after contact form submission
- `solar-calculator/index.html` — Self-contained solar cost calculator (all CSS and JS are inline)
- `assets/` — All images referenced by the HTML pages

### Key Patterns

**Contact form** uses [Formsubmit.co](https://formsubmit.co) (no backend required). Configuration is via hidden inputs in `index.html` — the recipient email, redirect URL, subject, and timezone are all set there.

**Lightbox** for products and projects is implemented entirely in `script.js`; clicking a card image opens a full-screen overlay.

**Solar calculator** (`solar-calculator/index.html`) is a standalone tool with Philippine-specific defaults (Meralco rates, peso currency, regional sun hours). It calculates system sizing, costs, savings projections, and payback period entirely in-browser.

**Responsive layout** uses CSS Grid and Flexbox with media queries. No CSS framework is used.

## Deployment

Pushing to the default branch automatically deploys to GitHub Pages. The `.nojekyll` file prevents Jekyll processing.
