# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm install        # Install dependencies
npm run dev        # Start dev server at http://localhost:4321
npm run build      # Build static output to /dist
npm run preview    # Preview production build locally
```

No test suite is configured. Type checking is enforced via `tsconfig.json` (extends `astro/tsconfigs/strict`).

## Architecture

This is a **single-page static CV/portfolio site** built with Astro 5, deployed to Netlify. All output is static HTML/CSS/JS — no server-side rendering.

### Content → Data → Component → Page flow

1. **Content layer** (`src/content/*.json`): All CV data lives here — profile, experience, education, courses, certifications, skills, contact. This is the only layer that needs editing for content changes.
2. **Data layer** (`src/data/site.ts`): Re-exports all JSON files as typed modules. Components import from here, not directly from JSON.
3. **Component layer** (`src/components/`): One Astro component per CV section (e.g., `ExperienceSection.astro`, `SkillsSection.astro`). `SectionHeading.astro` is a shared heading primitive.
4. **Layout** (`src/layouts/MainLayout.astro`): Base HTML5 template. Owns the global CSS design system (custom properties for color, spacing, typography, shadows), SEO meta tags, and OG tags.
5. **Page** (`src/pages/index.astro`): Single entry point. Imports all components and assembles the responsive grid layout.

### Design system

Defined entirely in `MainLayout.astro` as CSS custom properties:
- Accent color: `#059669` (green)
- Palette: slate-based
- Fonts: Poppins (headings), Inter (body) — loaded from Google Fonts
- Breakpoints: 768px (tablet), 900px / 980px / 1024px (desktop)

### Deployment

Push to `main` → Netlify auto-deploys (`netlify.toml`: build = `npm run build`, publish = `dist`, Node 20).

The `site` URL in `astro.config.mjs` should be updated to the real Netlify domain when known.
