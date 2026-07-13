# omeraliomer.com

**Live at [https://www.omeraliomer.com](https://www.omeraliomer.com)**

Personal portfolio site. Built with Astro, styled in the IBM Carbon register. No frameworks beyond what's needed, no placeholder content.

## Stack

- Astro 7 (static output)
- IBM Plex Sans / Mono / Serif via `@fontsource`
- Carbon-derived design tokens: Gray 10 background, Blue 60 accent, 8px spacing scale, 12-column grid
- `@astrojs/sitemap` for `sitemap-index.xml`
- No CSS frameworks, no component libraries, no JS runtime

## Routes

- `/` homepage: Hero, Selected Work, Recognition, footer
- `/direction` the trajectory statement (locked copy, see below)
- `/work/summerbucketlist` project write-up
- `/work/culture-clash` project write-up
- `404` not-found page

## Project structure

```
src/
  components/
    Nav.astro            sticky top bar: wordmark, Home, Direction
    Hero.astro           headline, lede, headshot
    SelectedWork.astro   three projects in deliberate order
    WorkItem.astro       single project row (used by SelectedWork)
    Recognition.astro    speaking, awards, credentials
    Footer.astro         email, LinkedIn, GitHub, Twitter
    BackLink.astro       shared "← Home" breadcrumb for sub-pages
    LabelledBlock.astro  shared eyebrow-label section with a 1px top-divider
  layouts/
    Base.astro           html shell, fonts, nav mount, Person JSON-LD
    WriteupLayout.astro  shared scaffold for the /work write-ups
  pages/
    index.astro              homepage
    direction.astro          /direction
    work/
      summerbucketlist.astro /work/summerbucketlist
      culture-clash.astro    /work/culture-clash
    404.astro                not-found page
  styles/
    global.css           design tokens, reset, layout primitives, write-up prose
public/
  headshot.jpg
  work-summerbucketlist.png
  work-culture-clash.png
  work-wendy.png
  logo.png
  og-image.png
  favicon/
  robots.txt
  CNAME
```

## Shared components

Three pieces are extracted so the sub-pages stay consistent:

- **`BackLink.astro`** the "← Home" link above the heading. Used by `/direction` and both write-ups.
- **`LabelledBlock.astro`** a mono eyebrow label above slotted content, with a 1px `--border` divider between consecutive blocks. Used by `/direction` (3 blocks) and both write-ups (3 each). Prose is slotted, so it keeps the consuming page's styling.
- **`WriteupLayout.astro`** wraps `Base` and owns the write-up header (eyebrow, name, meta, links slot, icon). Both write-ups reduce to frontmatter plus `LabelledBlock`s. The write-up prose rules (`.writeup p`, `.writeup__lede`) live in `global.css` rather than the layout, because they style slotted content, which keeps the page's scope rather than the layout's.

## Running locally

```sh
npm install
npm run dev
```

Build for production:

```sh
npm run build
npm run preview
```

Accessibility check (both tools should report zero issues on every route):

```sh
npx pa11y http://localhost:4321/
npx axe http://localhost:4321/
```

## Deployment

Deployed to GitHub Pages via GitHub Actions. Every push to `main` triggers a build and deploy automatically, no manual step required.

Custom domain: [https://www.omeraliomer.com](https://www.omeraliomer.com) (HTTPS enforced, CNAME at `public/CNAME`).

## Structured data & discovery

- `Base.astro` emits a `Person` JSON-LD block (name, jobTitle, `worksFor: IBM`, `sameAs` LinkedIn/GitHub/Twitter). Values are pulled from `Hero.astro` and `Footer.astro`, not invented; keep them in sync if either changes.
- `@astrojs/sitemap` generates `sitemap-index.xml` at build time; `robots.txt` allows all crawling and points at it.
- Canonical, `og:image`, JSON-LD `url`, CNAME, and `astro.config.mjs` site all use `www.omeraliomer.com`. Keep any new absolute URLs on the same host.

## What's deferred

Intentionally not built yet. Don't add them until the content is actually ready.

**Blog** Not started. Don't add a nav link or route until there's real content to publish. A nav link to an empty page is worse than no link.

**About / trajectory** Optional longer-form page covering the arc from apprentice to architecture to the Gulf. No rush.

## Design conventions

- All spacing from `--space-*` tokens only (2/4/8/12/16/24/32/40/48/64/80/96px). No eyeballed values.
- Single accent: `--accent` (#0f62fe). Don't introduce a second colour.
- `--radius` (8px) is the one radius in use: hero photo and project icons. Everything else is square-cornered.
- 1px flat borders for separation (`--border`), 2px solid rings for focus states. No box-shadows.
- The staggered reveal animation in `Hero.astro` is the one deliberate motion moment. Don't add more.

**Things to avoid when touching styles:**
Glassmorphism, bento-grid layouts, grain/noise overlays, gradient text or blobs, neon accents, numbered section markers (01/02/03), scroll-triggered reveals on every section, Inter or Roboto as the primary typeface.

## Copy conventions

British English throughout. Direct and specific: no "passionate about", "at the intersection of", or anything ending in "drive innovation". Real projects, real facts, nothing inflated.

No em-dashes (—). Use a colon, semicolon, or comma, whichever the sentence needs. En-dashes (–) are fine used sparingly.

Banned filler: "delve", "robust", "seamless", "holistic", "leveraging", "in today's digital landscape", "testament to". Say the plain thing instead.

IBM Plex Serif is available as an editorial accent (pull-quotes in project write-ups) but is not a second UI font. Use it sparingly if at all.
