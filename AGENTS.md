# AGENTS.md — Game Creator AI

> Instructions for AI coding agents (GitHub Copilot, Cursor, Claude Code, etc.) working with this project.

## Project Overview

Game Creator AI is a static landing/hub page that links to two separate AI-powered game generator web apps. The landing page is hosted on Netlify at `https://gamecreatorai.netlify.app/`.

This repository contains **only the landing page** — not the two apps themselves. The apps are deployed on separate Netlify subdomains.

## Tech Stack

- **HTML** — Vanilla HTML5, no templating engine
- **CSS** — Single stylesheet (`landing/style.css`), CSS custom properties, flexbox + grid
- **JavaScript** — None on the landing page (the apps have their own JS, not in this repo)
- **Frameworks** — None
- **Build tools** — None
- **Package manager** — None

## Project Structure

```
game creator master/
├── index.html              # Root redirect page (meta refresh → landing/)
├── robots.txt              # Crawler directives (AI crawlers allowed)
├── sitemap.xml             # XML sitemap (4 URLs)
├── sitemap.md              # Markdown sitemap for AI agents
├── llms.txt                # Curated site summary for AI models
├── llms-full.txt           # Full-text content for deep ingestion
├── AGENTS.md               # This file
├── brand.txt               # Brand identity and naming rules
├── ai.json                 # Structured content map + AI permissions
├── ai.txt                  # AI permissions declaration
├── _headers                # Netlify HTTP headers (Content-Type, Link)
├── _redirects              # Netlify redirect rules (301 / → /landing/)
├── favicon.svg             # SVG favicon
├── game creator pic.png    # OG/social image + Game Creator AI preview
├── game creator learn pic.png  # Game Creator Learn preview
├── landing/
│   ├── index.html          # Main landing page (content lives here)
│   └── style.css            # Landing page styles
└── .well-known/
    ├── ai-plugin.json      # ChatGPT plugin manifest
    ├── agents.json         # A2A agent discovery
    └── agent-skills/
        ├── index.json      # Agent Skills index
        ├── game-learn/
        │   └── SKILL.md    # Educational game creation skill
        └── game-fun/
            └── SKILL.md    # Entertainment game creation skill
```

## Key URLs

| Resource | URL |
|----------|-----|
| Landing page | `https://gamecreatorai.netlify.app/landing/` |
| Game Creator Learn app | `https://aigamecreatorlearn.netlify.app/` |
| Game Creator AI app | `https://aigamecreator.netlify.app/` |
| Tip Jar | `https://buy.stripe.com/5kQ9AVgCY5dJ77TbIA9R600` |

## How to Modify

### Editing the Landing Page

All visible content is in `landing/index.html`. The page has:

- `<header class="hero-header">` — Brand mark, H1, Tip Jar button
- `<section class="hero-panel">` — Tagline + two CTA buttons
- `<section class="site-grid">` — Two `<article>` cards (Learn + Fun)
- `<section class="feature-row">` — Three feature blocks
- `<footer class="page-footer">` — Footer text

### Editing Styles

All styles are in `landing/style.css`. Design tokens are CSS custom properties at the top of the file (`:root { ... }`). Key variables:

- `--bg`, `--surface`, `--text` — Page colors
- `--radius-*` — Border radii
- `--shadow-*` — Box shadows
- `--transition` — Default transition timing

### Adding a New Page

1. Create the HTML file in the root or a subdirectory
2. Add it to `sitemap.xml` with a `<url>` entry
3. Add it to `sitemap.md` under the appropriate section
4. Add it to `llms.txt` under the appropriate section
5. Update `llms-full.txt` if the page has significant content

### Updating AI Discovery Files

When content changes, update these files to stay in sync:

| File | When to update |
|------|-----------------|
| `llms.txt` | When key pages or features change |
| `llms-full.txt` | When landing page content changes |
| `sitemap.xml` | When pages are added/removed |
| `sitemap.md` | When pages are added/removed |
| `ai.json` | When site structure or permissions change |
| `brand.txt` | When brand name or products change |
| `.well-known/agent-skills/*` | When app capabilities change |

## Deployment

The site is deployed on Netlify. Push to the main branch to deploy. No build step is required — files are served as-is.

### Netlify Configuration

- `_redirects` — Handles the root `/` → `/landing/` redirect with a 301
- `_headers` — Sets `Content-Type: text/plain` for `.txt` files and adds `Link` headers for AI discovery

## Coding Conventions

- **HTML:** Semantic HTML5 elements (`<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`)
- **CSS:** BEM-ish class names, CSS custom properties for tokens, mobile-first responsive with `@media` breakpoints
- **Links:** All external links use `rel="noopener noreferrer"` and `target="_blank"`
- **Images:** Always include descriptive `alt` text and `loading="lazy"`
- **Accessibility:** Use `aria-hidden="true"` on decorative elements
- **No JavaScript** on the landing page — keep it static

## Important Notes

- The two apps (Game Creator Learn, Game Creator AI) are **separate projects** not contained in this repo
- The landing page has **no JavaScript** — it is purely static HTML/CSS
- Do not add frameworks, build tools, or package managers to this project
- Preserve the factual, non-marketing tone in all AI discovery files (`llms.txt`, `ai.json`, etc.)
- The `brand.txt` file defines canonical naming — follow it in all content