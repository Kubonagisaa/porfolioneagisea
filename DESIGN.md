# DESIGN.md — Kiet Portfolio · Direction D "Signaletik"

## Visual thesis

> **A signal-red-on-ink poster wall with poster-scale display type, ticket-stub metadata, diagonal print geometry — the portfolio reads like a designer's manifesto printed on construction-site signage: bold, numbered, and legible from across the street.**

The tempting choices this thesis makes inappropriate: glassmorphism (this system is matte ink, not glass), pastel gradients (signal red is the only temperature), tiny type (signage demands poster scale), centered hero + three-card layout (index-led poster structure instead).

## Design read

`Freelance designer portfolio · potential clients (founders, SMEs, agencies) · evaluate work + hire · bold constructivist poster · static HTML/CSS/vanilla JS, no framework`

Dials: Variance 7 · Motion 6 · Density 4 (unchanged from user's preview selection).

## Typography system

| Role | Font | Weights | Notes |
|---|---|---|---|
| Display | Space Grotesk | 500, 600, 700 | Uppercase for display, tight tracking −0.01em to −0.02em |
| Body | Inter | 400, 500 | 15–16px, 1.65 line-height |
| Mono (metadata, indexes, captions) | IBM Plex Mono | 400, 500 | Uppercase labels, +0.12em tracking, 11–13px |

Type scale (fluid):
- Display XL (hero): `clamp(3.4rem, 8vw + 1rem, 7rem)`
- Display L (section titles): `clamp(2.2rem, 5vw + 0.5rem, 4.2rem)`
- Display M (project titles): `clamp(1.75rem, 3.5vw, 2.6rem)`
- Body L: `clamp(1.05rem, 1.2vw + 0.9rem, 1.2rem)`
- Body: 1rem
- Mono label: 0.72–0.8rem uppercase

## Color system

| Token | Value | Role |
|---|---|---|
| `--ink` | `#0E0E0C` | Page background (near-black, warm) |
| `--ink-2` | `#151512` | Raised surface |
| `--ink-3` | `#1C1C18` | Border hairlines on dark |
| `--paper` | `#F2EFE6` | Primary text, inverted surfaces |
| `--paper-dim` | `#B5B2A6` | Muted text |
| `--signal` | `#E8402A` | The accent — CTAs, hover inversions, active marks. Used sparingly: ~5% of pixels |
| `--signal-deep` | `#C22E1B` | Hover/pressed on signal |

Contrast: paper on ink ≈ 15.5:1 AA; paper-dim on ink ≈ 7.4:1 AA; signal red text only on ink backgrounds (4.6:1, large text only), never as body text. Signal-filled buttons carry paper text (4.9:1 AA for large/bold text, buttons ≥ 44px).

## Shape & surface

Radius grammar: **sharp** — 0px on all containers, buttons, images (signage doesn't round its corners). Single exception: 999px on the availability pill.

Borders: 1px `--ink-3` hairlines on dark; 2px solid `--paper` rules for section dividers (poster frames).

Elevation: none. Depth comes from layering type and rules, not shadows.

## Layout rules

- 12-column grid, `max-width 1360px`, gutters `clamp(20px, 4vw, 64px)`.
- Section numbering: every section carries a mono index marker (`01 / WORK`, `02 / SERVICES`…) anchored to the grid's left rail.
- Index-led work section: projects as large numbered rows; each row = poster panel with image, number, title, meta strip.
- Diagonal motif: one rotated geometric outline per major section (18°), never on text.
- Mobile: index rail collapses into horizontal mono labels; grid → single column; diagonal motifs scale down and stay decorative-only.

## Imagery

Project visuals = CSS-built abstract thumbnails derived from each project's real palette (AURELLE paper/gold, Nova violet-on-ink, Airfly blue/orange, Neagisea black/steel, Segesta aurora, Atelier cream). Each thumb is labelled in mono caps (e.g. `AURELLE / E-COMMERCE / 2026`) — honest placeholders, clearly replaceable by real screenshots later. No fake logos, no fake photos, no invented metrics.

## Motion language

Purposeful 2D only, all transform/opacity, `prefers-reduced-motion` fully honored:
- **Entrance:** staggered clip-path/translateY reveals via IntersectionObserver (`[data-reveal]`).
- **Background:** (user-requested) subtle animated grain + a faint grid drift in hero — extremely low contrast, pausable, off under reduced motion.
- **Hover:** work rows invert to signal red; images pan ±3%; links get underline strikes.
- **Ticker:** skills marquee, pauses on hover, static under reduced motion.
- **Scroll:** none beyond reveals — no scroll-jacking.

## Interaction

Hover inversions (row → signal), magnetic-free buttons, no cursor followers, real `<a>`/`<button>` semantics, visible `:focus-visible` (paper outline offset). Keyboard: works top-to-bottom, skip-link present.

## Copy

Full English (user request). Real, specific, non-marketing. No fake testimonials, no invented revenue, no "revolutionary/seamless/next-gen". Tone: confident studio manifesto — short declarative sentences.

## Components

Numbered section header · ticker band · work row (index-style) · services ledger (two-column definition list) · process strip (4 numbered steps) · availability pill · contact poster panel · footer colophon.

## Responsive

Desktop-first; mobile ≥ first-class: hero type rescales via clamp, work rows stack, index rail becomes inline labels, ticker persists, hover-only affordances duplicated with visible state on touch.
