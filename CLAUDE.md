# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Local Preview

No build step. Open any HTML file directly in a browser, or run a local server:

```bash
python -m http.server 8000
# then open http://localhost:8000/
```

The site is deployed automatically via GitHub Pages at https://smallcox-bigprojects.github.io/BigProject/.

## Architecture

This is a pure static site — no framework, no bundler, no dependencies. Three HTML pages, each self-contained:

- `index.html` — Main landing page (hero, meet section, channels grid, lake house spotlight)
- `the-rental.html` — Project detail page with a tabbed room-by-room photo gallery
- `project-labs.html` — 3D prints gallery with client-side category filtering

**Shared design system** — The CSS custom properties (color palette, font stacks) are duplicated in a `<style>` block inside each page's `<head>`. There is no shared stylesheet. When updating the design system (colors, fonts, spacing tokens), all three pages must be updated.

**Color palette (`:root` variables):** `--cream`, `--tan`, `--rust`, `--rust-lt`, `--forest`, `--forest-lt`, `--navy`, `--gold`, `--gold-lt`, `--brown`, `--ink`, `--muted`, `--card-bg`. Typography: `--serif` (Abril Fatface) for headings/logos, `--sans` (Nunito) for body.

**Image hosting** — Renovation photos are served from S3 at `https://smallcox-bigprojects-public.s3.us-east-2.amazonaws.com/BigProjects/TheRental/reno_images/{before|after|during}/{filename}`. The gallery in `the-rental.html` dynamically constructs image URLs and hides cards on `onerror` — missing images are a normal state, not a bug.

**JavaScript** is minimal and inline in each page:
- `the-rental.html`: room-tab switching + lazy S3 image loading per room
- `project-labs.html`: filter button toggling by `data-category` attribute

## Adding a New Page
Follow the pattern in existing pages: copy the nav, hero wave SVG, footer, and `:root` CSS block. Link back to `index.html` in the nav logo and navigation links.

## Site Purpose & Audience
This site showcases personal projects — a rental property renovation, a vacation propery renovation, 3D printing work, 
and other ongoing ventures. The audience is friends and family staying in touch and general public through social media

## Content Tone & Voice
- Enthusiastic about projects
- Clever and cute

## Content Goals
- Share progress and updates on ongoing projects
- [Attract rental inquiries? Build an audience? Document for personal reference?]
- Grow content across the channels section over time

## Channels (from index.html)
- Big Projects (flagship) -> Full-scale renovations, flips, and builds.
- - Current focus is The Lakehouse
- - Prior Big Projects were 'The Rental' and 'The Homestead'
- Guest Stars (friends and family) -> a display of cards for ourselves, friends, and family
- - A card will contain a name, funny title, short description, and may contain a photo
- - Posts and other content within the sight may reference these cards
- Lil projects (3d printing) -> A catalog of fun things I've designed and printed
- Big Trips -> Collection of Travels.  A sub-blog for our big trips which include descriptions and pictures
- - Prior Big Trips include Alaska, Italy, Africa, Mediterranean Cruise

## Content Types I Want Help With
- Blog post drafts
- Channel content ideas
- Copy for new pages or sections
- Photo/gallery captions

## Design Preferences
- Keep additions consistent with the existing warm, earthy palette (cream, rust, forest, gold)
- Prefer simple, readable HTML over complex JS
- Mobile-friendliness matters