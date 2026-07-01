# omeraliomer.com

Personal portfolio site. Built with Astro, styled in the IBM Carbon register. No frameworks beyond what's needed, no placeholder content.

## Stack

- Astro 7 (static output)
- IBM Plex Sans / Mono / Serif via `@fontsource`
- Carbon-derived design tokens — Gray 10 background, Blue 60 accent, 8px spacing scale, 12-column grid
- No CSS frameworks, no component libraries, no JS runtime

## Project structure

```
src/
  components/
    Nav.astro          sticky top bar — wordmark only for now
    Hero.astro         headline, lede, headshot
    SelectedWork.astro three projects in deliberate order
    WorkItem.astro     single project row
    Recognition.astro  speaking, awards, credentials
    Footer.astro       email, LinkedIn, GitHub, Twitter
  layouts/
    Base.astro         html shell, fonts, nav mount
  pages/
    index.astro        homepage
  styles/
    global.css         design tokens, reset, layout primitives
public/
  headshot.jpg
  work-summerbucketlist.png
  work-culture-clash.png
  work-wendy.png
```

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

## Current state

Homepage is complete: Hero, Selected Work, Recognition, footer. Nav bar shows the wordmark only.

**Selected work**

- summerbucketlist.me — React + TypeScript, 64 Manchester activities, filter-sheet UX. Live at summerbucketlist.me, repo at github.com/omer111-50/summer-bucket-list. The Live badge links to the site; the repo URL below the description links to the code — two distinct affordances, both intentional.
- Culture Clash — Next.js 15 + TypeScript, Google Gemini fusion recipes across 28 cuisines, built with a team of five (Omer, Aun Raza, Ibraheem Iqbal, Anas Bataweel, Ismail Shafie) at GreatUniHack 2025. Repo at github.com/Git-Push-Chill/CultureClash. No live deployment — repo link only.
- Wendy — Next.js + TypeScript on IBM Carbon, real-time scam-call detection concept, built same-day at an internal IBM hackathon.

**Recognition diary note:** Manchester Young Talent Awards shortlist drops September 2026. If shortlisted, update "Nominee" to "Shortlisted" in `Recognition.astro`.

## What's deferred

These are intentionally not built yet. Don't add them until the content is actually ready.

**Nav links and /direction page**
The nav currently shows the wordmark only. Once ready, add Home and Direction links back to `Nav.astro` and create `src/pages/direction.astro`. The copy is locked below — do not rewrite it.

**Blog**
Not started. Do not add a nav link or route until there's real content to publish. A nav link to an empty page is worse than no link.

**Project write-ups**
Individual pages for each project — problem, decisions, what would be different. Worth doing once the homepage is settled.

**About / trajectory**
Optional longer-form page covering the arc from apprentice to architecture to the Gulf. No rush.

## Direction page — locked copy

When the `/direction` page is built, use exactly this. Three paragraphs. Do not expand without a new concrete fact to anchor it — sentiment without a fact is the failure mode this has been pulled back from twice.

> I'm Muslim, of Yemeni background, and I speak Arabic. That's not background — it's a good part of why I build the way I do, and it's the direction the next stage of my career is pointed in.
>
> In April 2026 I hosted the Muslims@IBM panel on careers in the Middle East — organised and facilitated end to end. It's the kind of thing I want to keep doing: helping people who look like me picture themselves working in the region, not just visiting it.
>
> The Gulf isn't a someday plan. It's where enterprise cloud and AI work is scaling fastest right now, and it's the market my trajectory is pointed at — from platform engineering, through technical architecture, aimed specifically there rather than wherever the job happens to take me.

## Design conventions

- All spacing from `--space-*` tokens only (2/4/8/12/16/24/32/40/48/64/80/96px). No eyeballed values.
- Single accent: `--accent` (#0f62fe). Don't introduce a second colour.
- `--radius` (8px) is the one radius in use — hero photo and project icons. Everything else is square-cornered.
- 1px flat borders for separation (`--border`), 2px solid rings for focus states. No box-shadows.
- The staggered reveal animation in `Hero.astro` is the one deliberate motion moment. Don't add more.

**Things to avoid when touching styles:**
Glassmorphism, bento-grid layouts, grain/noise overlays, gradient text or blobs, neon accents, numbered section markers (01/02/03), scroll-triggered reveals on every section, Inter or Roboto as the primary typeface.

## Copy conventions

British English throughout. Direct and specific — no "passionate about", "at the intersection of", or anything ending in "drive innovation". Real projects, real facts, nothing inflated.

IBM Plex Serif is available as an editorial accent (pull-quotes in project write-ups) but is not a second UI font. Use it sparingly if at all.
