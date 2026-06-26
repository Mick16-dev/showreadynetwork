# Show Ready Network — Implementation Plan

This document tracks the **Show Ready Network** one-page landing site: goal, design system, guardrails, recommended improvements, and build/deploy tasks.

---

## Project goal

A one-page landing site for **Show Ready Network** — a brokerage connecting independent event promoters with sponsors and brand partners.

**The site has one job:** make promoters and sponsors trust this is a **real, small, founder-led network** worth a reply — not a SaaS product, not an agency with 50 staff.

| Audience | What they need |
|----------|----------------|
| **Independent promoters** | Skeptical, scene-based; value trust over polish |
| **Brand / sponsorship contacts** | Quick proof of legitimacy and a clear next action |

**Primary action:** get a visitor to submit the contact form (or email **michaeltesfaye613@gmail.com** as fallback).

---

## Visual identity — “show bill / ticket stub”

The design language is borrowed from event marquees, show bills, and ticket stubs — **not** generic startup gradients. This idea should run through every section.

### Color tokens

| Name | Hex | Use |
|------|-----|-----|
| Backstage Black | `#0E0D0F` | Primary background |
| Black Soft | `#161417` | Card / panel backgrounds |
| Paper | `#F2EEE6` | Primary text on dark |
| Marquee Gold | `#D8A246` | Accent, links, CTA, highlights |
| Stone | `#A39C8E` | Secondary / muted text |
| Line | `#2B2520` | Borders, dividers, hairlines |

**Rule:** Do not introduce new colors outside this `:root` set without explicit approval.

### Type system

| Role | Font | Notes |
|------|------|-------|
| Display (headlines) | **Anton** | Condensed, all-caps, poster / marquee feel |
| Body | **Source Serif 4** | Warm, editorial, readable at 16–19px |
| Mono / labels | **JetBrains Mono** | Eyebrows, small caps labels, data rows |

Google Fonts (already in `index.html`): Anton, Source Serif 4, JetBrains Mono.

### Layout concept

- Full-bleed dark hero with scrolling marquee strip across the top (`TONIGHT — PROMOTERS WANTED`)
- Hero split: big headline + small **registry status** data panel (founding spots, entry cost, control, base) — concrete numbers, not vague taglines
- **How it works** — true numbered sequence (3 real steps, in order)
- **Who it's for** — two-column comparison (promoters vs. sponsors), no forced numbering
- **Contact** — literal ticket stub with perforated edge (signature element)

### Signature element

The contact section ticket stub (`.stub` class):

- Perforated divider
- Vertical “Show Ready” text rotated on the stub side
- “No. 001” admit number

This is the **one place** the design takes a visible risk. Everything else stays disciplined and quiet.

---

## What's already built

- [x] **`index.html` added to repo** — complete, self-contained page (all CSS inline)
- [x] **No build step** — static HTML/CSS only
- [x] **Google Fonts** — Anton, Source Serif 4, JetBrains Mono via `<link>`
- [x] **Responsive** — works down to mobile
- [x] **`prefers-reduced-motion`** — respected
- [x] **Focus states** — visible on links and buttons

---

## Guardrails (do not drift)

- [x] **No generic SaaS look** — no gradient hero, rounded card grid, emoji icons
- [x] **No stock photography** — design relies on type and color, not imagery
- [x] **Plain, specific copy** — no “revolutionize,” “synergy,” “leverage”
- [x] **One signature risk only** — the ticket stub; everything else restrained
- [x] **Token colors only** — no new palette without approval

---

## Trust & copy improvements (human + professional)

Recommended refinements that fit the show-bill identity. Check off as implemented.

### Founder voice

- [x] Add 2–3 sentences in About or near contact: who Michael is, one line of scene credibility, why Show Ready Network exists
- [x] Replace vague adjectives with specifics (e.g. show types, cities, years in the scene)

### Registry status panel

- [x] Tie each data point (founding spots, entry cost, control, base) to **one plain sentence** of explanation
- [x] Make the panel read like a real ledger, not a marketing funnel

### How it works (3 steps)

- [x] Each step: verb + what happens + what you are **not** doing (e.g. “You keep your list — we don’t own your audience”)
- [x] Address promoter lock-in fear and sponsor vagueness in one line per step

### Who it's for — sponsor column

- [x] Add one legitimacy line (e.g. “Introductions only — no commission until you agree terms” or “Curated roster, not a marketplace”)

### Ticket stub / contact

- [x] Add micro-copy above CTA: what happens after email (e.g. reply within 48 hours, short intro call, no deck)
- [x] Keep single primary action — email or form, not both competing

### On-brand design tweak (one specific improvement)

- [x] Add a hairline **show bill rule** under the hero headline — full-width `Line` (`#2B2520`) with tiny JetBrains Mono center label, e.g. `ADMIT ONE — INDEPENDENT PROMOTERS & BRAND PARTNERS`
- [x] Confirm stub remains the only major visual risk

---

## Build tasks (from project brief)

### 1. Personalize

- [x] Replace every `michael@showreadynetwork.com` with final contact email — **current:** `michaeltesfaye613@gmail.com`
- [x] Update About section copy if situation has changed
- [x] Keep tone: direct, low-hype, specific

### 2. Contact form (optional — replaces or supplements mailto)

- [x] Replace mailto in `.stub-cta` with simple form: name, email, message, role dropdown (Promoter / Sponsor)
- [x] Use **Formspree** or **Netlify Forms** (static site, no backend) — **Formspree** chosen (Vercel deploy)
- [x] Match existing style: gold CTA, dark theme, JetBrains Mono labels
- [x] No new colors outside `:root` tokens
- [x] **Configure Formspree:** form endpoint `https://formspree.io/f/mjgqwblv`

### 3. Roster page (when promoters are signed)

- [ ] Create `roster.html` with same tokens and fonts as `index.html`
- [ ] Promoter cards styled like show-bill entries: name, genre/scene, frequency, audience range
- [ ] Base layout on `.bill-row` from “How it works,” adapted to a card grid
- [ ] Link from main nav / footer on `index.html`

### 4. Scroll-based motion (optional)

- [x] Single restrained scroll-reveal: top-level sections fade/slide up once on first viewport entry (`IntersectionObserver`)
- [x] Honor `prefers-reduced-motion` — no animation when set
- [x] Do **not** animate every element — sections only, once each

### 5. Deploy

- [x] Confirm no broken relative paths (logo → `/`; nav anchors; Google Fonts external only)
- [x] Deploy folder to **Netlify** (drag-and-drop) or add `netlify.toml` / `vercel.json` if needed — **`vercel.json` added**
- [x] Verify live site: fonts, marquee, stub, mailto/form, mobile — **https://showreadynetwork.vercel.app**

### 6. Design review pass

- [x] Review `index.html` against this brief (show bill / ticket stub identity)
- [x] Apply at most **one** identity-forward tweak at a time — no generic redesign
- [x] Re-check guardrails after any change

---

## Status summary

| Item | Value |
|------|-------|
| **Current phase** | Roster page (optional) — contact form live |
| **Repo** | [github.com/Mick16-dev/showreadynetwork](https://github.com/Mick16-dev/showreadynetwork) |
| **Local path** | `c:\Users\micha\.antigravity\showreadynetwork` |
| **Stack** | Static HTML/CSS, no build tools |

### Progress checklist (high level)

- [x] `index.html` in repository
- [x] Personalization complete
- [x] Trust / copy improvements applied
- [x] Contact form live (Formspree)
- [x] Deployed to production URL — https://showreadynetwork.vercel.app
- [ ] Optional: roster page
- [x] Optional: scroll reveal

---

*Last updated: June 2026*
