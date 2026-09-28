# Layerwatch website: project context

## What Layerwatch is (as of Sept 2026)
Layerwatch builds an evidence-backed model of a running application across its
code repositories, deployment configuration (Helm/Kustomize/Kubernetes) and
runtime (Celery workers, Redis, Postgres). Engineers use it to answer "where
does this data go, which setting is live, what actually reached production";
coding agents get the same facts through a local MCP server.

- Every claim carries one of five labels: **declared, configured, observed,
  inferred, unresolved**. Unknown is a valid answer; never present a guess as fact.
- Initial verified support: Python, Celery, Redis, Kubernetes (Postgres next).
- Target: backend teams running several services across multiple repos.
- Status: **private preview / early access**. One name for signups: "early access"
  (not waitlist, not design partner).
- "System Context" was the working name in the planning docs; the brand is Layerwatch.

The earlier direction (MCP security proxy, browser extension, CISO buyer) was
dropped. Don't reintroduce it.

Product spec (source of truth for messaging and claims):
`~/Downloads/System_Context_Research_and_Implementation_Package/System_Context_Company_and_Build_Plan.md`

## Copy rules
- No fabricated customers, metrics, testimonials or logos.
- No competitor-bashing; don't claim others "can't" do something.
- No internal roadmap, milestones, customer-profile guesses or dates on the public site.
- Example data is synthetic; keep it internally consistent (same worker names,
  file locators and values across hero, map and MCP example), and label each
  example claim correctly (e.g. a cause that isn't proven is not "observed").
- Each section makes one distinct point; avoid repeating the hero's example.

## Site
- Stack: Astro 6 (static) + Tailwind CSS v4 (`@theme` tokens in
  `src/styles/global.css`) + GSAP/ScrollTrigger. Fonts self-hosted via @fontsource.
- Hosting: Cloudflare (wrangler assets, `not_found_handling: 404-page`),
  auto-deploys on push to `main` of github.com/layerwatch/website.
  **Pushing to main deploys to production: confirm before pushing.**
- Live: https://layerwatch.dev. Early-access forms post to Formspree (`mrevognv`).
- Commands: `npm run dev` (localhost:4321), `npm run build`.

### Structure
- `src/pages/index.astro`: landing page; data arrays in frontmatter.
  Section order: hero → sources strip → problem → layers → workflow map →
  for agents → trust → FAQ → early access.
- `src/components/`: Nav (desktop links + mobile menu), Footer, HeroAnswer,
  LayerScroll, WorkflowMap, WaitlistForm.
- `src/layouts/Layout.astro` (head, canonical, fonts, scroll/hash handling),
  `LegalLayout.astro` (privacy, terms), `src/pages/404.astro`.
- `public/`: logo.svg (primary logo), favicons, og-image.png, robots.txt,
  sitemap.xml, .well-known/security.txt.

### Design conventions
- Dark navy base (`#0a1122`) with a page-wide hairline grid; per-section accent
  via `data-tone`. Light "paper" panels (`.panel.paper`) are used for product
  surfaces: problem cards, workflow map, MCP terminal, early-access form card.
  Avoid full-width white sections.
- Evidence-label colours are fixed tokens (declared/configured/observed/
  inferred/unresolved); inside `.paper` they switch to darker AA-contrast shades.
- Text must meet WCAG AA (4.5:1); no horizontal overflow at 390px; tap
  targets ≥44px on mobile.

### Hard-won behaviour (don't regress)
- **Layer by layer** (`LayerScroll.astro`) is a CSS-sticky scrollytelling
  section: the page scrolls natively and each text block activates its layer
  as it crosses the reading line. Do NOT intercept wheel/touch or hijack scroll
  (every attempt at "one layer per scroll" broke on real trackpads). Desktop:
  heading pinned left, diagram pinned right. Phone/tablet: only "Layer by layer"
  and progress bars pinned; headline scrolls.
- Refresh always starts at the top: in-page links don't write `#hash`, and
  scroll restoration is off (browser and ScrollTrigger).

## Accounts (reference, not secrets)
- Domain layerwatch.dev on Cloudflare; hi@ and security@ forward to personal Gmail.
- GitHub org github.com/layerwatch; X @layerwatch (both confirmed owned).
- Confirm before destructive git operations or DNS/Cloudflare/GitHub org changes.
