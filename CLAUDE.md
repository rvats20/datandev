# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Marketing website for **Data & Dev**, a consulting company specializing in Cloud, AI-ML, and Python applications. This is a static single-page site deployed to GitHub Pages via Jekyll.

- **Live site:** Hosted on GitHub Pages
- **Owner:** Rahul Vats (rvats20)

## Tech Stack

- Static HTML/CSS/JavaScript — no build step, no package manager
- Tailwind CSS via CDN (`cdn.tailwindcss.com`) with inline config
- Lucide Icons via CDN (unpkg)
- Google Fonts (Inter)
- Vanilla JavaScript (no jQuery or other libraries)
- CSS `scroll-behavior: smooth` for smooth scrolling
- Intersection Observer API for scroll-triggered reveal animations

## Development

There is no build, lint, or test process. To develop locally, open `index.html` in a browser or use any static file server:

```bash
# Python
python3 -m http.server 8000

# Node (if npx available)
npx serve .
```

## Deployment

Automatic via GitHub Actions on push to `main`. The workflow (`.github/workflows/jekyll-gh-pages.yml`) builds with Jekyll and deploys to GitHub Pages. No manual deploy steps needed.

## Architecture

Everything lives in a single `index.html` with anchor-based section navigation:

| Section ID       | Purpose                                    |
|------------------|--------------------------------------------|
| `#hero`          | Hero with gradient background, animated CTA |
| `#about`         | Company story, mission, key stats          |
| `#services`      | Service cards with icons and hover effects |
| `#projects`      | Project portfolio with hover overlays      |
| `#testimonials`  | Client testimonials with JS carousel       |
| `#contact`       | Contact form + info cards, footer          |

All JavaScript is inline at the bottom of `index.html`.

## Key Conventions

- **Styling:** Tailwind CSS utility classes throughout. Custom CSS limited to animations and effects in an inline `<style>` block.
- **Icons:** Lucide icons via `data-lucide` attributes, initialized with `lucide.createIcons()`.
- **Animations:** CSS `@keyframes` for hero entrance, Intersection Observer + `.reveal` / `.visible` classes for scroll-triggered reveals, `.reveal-stagger` for staggered children.
- **Responsive:** Mobile-first design using Tailwind responsive prefixes (`sm:`, `md:`, `lg:`).
- **Carousel:** Vanilla JS testimonial carousel with prev/next buttons, responsive slide count (1/2/3 based on viewport).
- **Navigation:** Fixed navbar with scroll-based background change, mobile hamburger menu with JS toggle.

## Directory Layout

```
img/        → All images (gallery, testimonials, backgrounds)
index.html  → The entire site (single page)
CLAUDE.md   → This file
LICENSE
README.md
.github/    → GitHub Actions workflow for Pages deployment
```
