# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static HTML website for "Small-Cox, Big Projects" — Tyler and Mallory's renovation, travel, and maker project site. Deployed via GitHub Pages at https://smallcox-bigprojects.github.io/BigProject/.

No build system, no package manager, no JavaScript framework. All pages are self-contained HTML files.

## Local Preview

```bash
python -m http.server 8000
# open http://localhost:8000/
```

## Architecture

The site is four standalone HTML pages, each containing all CSS inline in a `<style>` block:

- `index.html` — Main landing page (hero, about section, channel grid, lake house spotlight)
- `project-labs.html` — Lil' Projects / 3D prints page
- `big-trips.html` — Travel/adventures page
- `the-rental.html` — Rental property project page

**There is no shared CSS file.** The design system is duplicated via a `:root` CSS custom-properties block at the top of each page's `<style>` tag. When updating colors, fonts, or shared variables, all four files must be updated.

## Design System

All pages share the same color palette and typography defined in `:root`:

| Variable | Value | Use |
|---|---|---|
| `--cream` | `#FAF4E8` | Page background |
| `--tan` | `#E8D9B8` | Borders, tags |
| `--rust` | `#C45C2A` | Accent / spotlight bg |
| `--forest` | `#3A5E42` | Intro blurb bg |
| `--navy` | `#243556` | Nav, hero bg |
| `--gold` | `#D4960A` | Highlights, CTAs |
| `--ink` | `#1E1810` | Body text |
| `--muted` | `#7A6A54` | Secondary text |
| `--card-bg` | `#FFFDF6` | Card backgrounds |

Fonts (Google Fonts): `Abril Fatface` for display/headings (`--serif`), `Nunito` for body (`--sans`).

## Known Issue

`index.html` uses en-dashes (`–`) instead of double-dashes (`--`) for CSS custom property names in its `:root` block and property references (e.g., `–cream` instead of `--cream`). The other three pages correctly use `--`. This means `index.html`'s CSS variables don't actually resolve — browsers fall back to initial values. When editing `index.html`, fix these to use `--` syntax.
