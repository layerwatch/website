# Layerwatch — Project Context

## What this is
Layerwatch is a developer security startup focused on runtime visibility and
interception for AI coding agents at the MCP (Model Context Protocol) layer.
Core product: an open-source MCP proxy that sits between AI coding agents and
the file system/tools they access — addressing silent file access, no audit
trail, and unvetted MCP servers.

## Strategic positioning
- Every funded competitor (Runlayer, Zenity, Helmet, Golf) sells top-down to
  security teams. The unoccupied wedge is a developer-first IDE layer.
- Target paying customer: CISOs in fintech and healthtech.
- Exit thesis: acquisition by a security platform (Palo Alto, CrowdStrike,
  Wiz) or an AI lab.

## Build priority (don't reorder without discussion)
1. **MCP proxy** — the moat, open-source, defensible core. Build first.
2. **Browser + VS Code extensions** — free, distribution-only. Already have
   a browser extension with regex-based key redaction built, not yet deployed.
3. **Enterprise console** — paid tier (dashboards, audit logs, compliance
   exports, SSO). Built last, once there's adoption to monetize.

## Revenue model
- Free: browser extension + VS Code extension
- Free/open-source: MCP proxy
- Paid: enterprise console

## Current site (this repo)
- Stack: Astro + Tailwind CSS
- Hosting: Cloudflare Pages, auto-deploy on push to GitHub main branch
- Live at: layerwatch.dev
- Waitlist form: Formspree (already wired up and working)
- Local path: /Users/likith/Documents/Layerwatch/website

## Infra / accounts (for reference, not secrets)
- Domain: layerwatch.dev on Cloudflare (DNSSEC + WHOIS privacy on)
- Email routing: hi@, security@, noreply@layerwatch.dev → personal Gmail
- GitHub org: github.com/layerwatch (GitHub username: likithv)
- X: @layerwatch
- SSH auth already configured for GitHub
- Mac username: likith

## Naming principle
Chose "Layerwatch" over invented/foreign-language names (e.g. Vaktio, Limen)
because immediate comprehensibility to a global developer audience beats
cleverness. Apply this lens to any future naming (products, features, repos).

## Conventions / working style
- Prioritize the proxy over the extensions in any roadmap discussion —
  extensions are distribution, the proxy is the moat.
- Confirm before any destructive git operation (force push, history rewrite)
  or before changing DNS/Cloudflare/GitHub org settings.
- Keep the dark theme and existing visual identity unless explicitly asked
  to redesign.

## What's next
- Deploy the existing browser extension
- Build and open-source the MCP proxy (critical path: API calls → tool
  use/function calling → MCP)
- Develop the enterprise console