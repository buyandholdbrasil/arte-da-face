# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev       # Dev server at localhost:4321
npm run build     # Production build to ./dist/
npm run preview   # Preview production build locally
```

No test or lint scripts are configured.

## Stack

- **Astro 6** with file-based routing (`src/pages/` → URL)
- **Tailwind CSS 4** via `@tailwindcss/vite` plugin (no `tailwind.config.*`)
- **@astrojs/vercel** adapter for deployment
- Node >= 22.12.0 required

## Architecture

Two pages share a `Layout.astro` wrapper (handles `<head>`, Google Fonts, meta tags):

- `src/pages/index.astro` — hub/catalog listing courses; most are "coming soon"
- `src/pages/labios.astro` — full sales landing page for the "Arte dos Lábios" course

Content (modules, FAQs, testimonials, course list) lives as inline arrays at the top of each `.astro` file — there is no CMS or external data source. Enrollment links point to an external Kiwify URL.

## Design System

Defined in `src/styles/global.css`:

- **Colors**: Gold `#9A8245` / `#C4AD77`, Cream `#FAF7F2`, Charcoal `#0D0D0D` / `#161616`
- **Fonts**: Cormorant Garamond (serif, headings) + Montserrat (sans, body)
- **Styling**: mix of Tailwind utility classes and inline `style=` attributes with `clamp()` for fluid type; interactive states use `onmouseover`/`onmouseout`

## Conventions

- SVG icons are embedded inline, not imported as files
- Images live in `public/` and are referenced with root-relative paths
- The logo mark is a Unicode/text character (`𓁹` or similar statue glyph), not an image file
