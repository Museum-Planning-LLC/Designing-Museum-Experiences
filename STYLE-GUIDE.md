# Designing Museum Experiences — Style Guide

Source of truth for visual and structural consistency on **[museum-experiences.com](https://museum-experiences.com/)** and all pages in this repo (`/resources/`, `/museum-toolbox/`, etc.).

Implementation lives in `index.html` today (inline CSS). New pages should copy the `:root` tokens and component patterns from that file — do not introduce new palettes or type families without updating this guide.

---

## Brand positioning

| Attribute | Direction |
|-----------|-----------|
| **Tone** | Editorial, warm, practitioner-facing — a published book, not a SaaS landing page |
| **Layout** | Light reading room on cream/paper fields; ink used for contrast strips and CTAs |
| **Audience** | Museum practitioners, students, boards exploring visitor experience design |
| **Sibling sites** | Part of four primary properties — see [README.md](./README.md) |

This site is **not** museumplanning.com (consulting). Visual DNA is closer to a book hub than the dark consulting site (Playfair + Lato) or museums101.com (Playfair + red accent).

---

## Color tokens

All colors are defined in `:root` in `index.html`. Reuse exactly — do not drift.

| Token | Hex | Role |
|-------|-----|------|
| `--paper` | `#f7f3ec` | Nav background base, primary button text on dark |
| `--cream` | `#faf7f2` | Page background, card/cell surfaces |
| `--pale` | `#ede8df` | Alternate section background, hover states, sidebar cards |
| `--rule` | `#d4c9b8` | Borders, grid gutters, ghost button outlines |
| `--ink` | `#1a1510` | Primary text, dark sections (facts strip, pull quote, CTA) |
| `--mid` | `#5c5446` | Body copy, secondary text |
| `--muted` | `#8a8070` | Nav links, meta, footer-adjacent labels |
| `--gold` | `#9b6e2e` | Italic headline accents, hover states, emphasis |
| `--copper` | `#c4834a` | Kickers, section tags, fact numbers, primary CTA on dark |
| `--red` | `#8c2018` | Reserved — use sparingly; not used on homepage today |

**Footer background:** `#110e09` (hard-coded, slightly darker than `--ink`).

### Rules

- Do **not** add rainbow, neon, or cool-gray palettes.
- Dark sections use `--ink` or `#110e09`; light sections use `--cream`, `--pale`, or `--paper`.
- Accent hierarchy: **copper** for labels/eyebrows → **gold** for emphasis and hover.
- Grid cells use `gap: 1px; background: var(--rule)` so borders read as hairlines.

---

## Typography

Load from Google Fonts (same URL as `index.html`):

```
Cormorant Garamond — 300, 400, 600, 700 + italics
DM Sans — 300, 400, 500
DM Mono — 300, 400, 500
```

| Role | Font | CSS variable | Typical usage |
|------|------|--------------|---------------|
| **Display / headlines** | Cormorant Garamond | `--serif` | H1, H2, H3, pull quotes, tool names, stage titles |
| **Body** | DM Sans | `--sans` | Default `body`, resource links, card descriptions |
| **UI / labels / nav / meta** | DM Mono | `--mono` | Nav, kickers, section tags, buttons, footer, bylines |

### Type scale

| Element | Size | Weight | Notes |
|---------|------|--------|-------|
| **H1** | `clamp(44px, 5.5vw, 72px)` | 300 | `<em>` → italic, `--gold` |
| **H2** | `clamp(32px, 4.5vw, 52px)` | 300 | Section titles; `<em>` → `--gold` |
| **H2 (CTA section)** | `clamp(36px, 5vw, 58px)` | 300 | On `--ink` background; `<em>` → `--copper` |
| **H3** | 24–26px | 400 | Resource groups, cards; `<em>` → `--gold` |
| **Hero description** | 20px serif | 300 italic | `--mid`, max-width ~520px |
| **Body** | 16px sans | 400 | line-height `1.75` |
| **Small body** | 13–15px | 400 | Cards, stages, about copy |
| **Kicker / section tag** | 9px mono | 400 | uppercase, letter-spacing 3–3.5px, `--copper` |
| **Nav links** | 9.5px mono | 400 | uppercase, letter-spacing 1.5px, `--muted` |
| **Buttons** | 9.5px mono | 400 | uppercase, letter-spacing 2px |

### Italic emphasis pattern

Headlines use `<em>` for one emphasized word in **gold** (light backgrounds) or **copper** (dark backgrounds). Example:

```html
<h1><em>Designing</em><br>Museum<br>Experiences</h1>
<h2>The instruments of<br><em>visitor-centered</em> design.</h2>
```

---

## Layout and spacing

| Constant | Value |
|----------|-------|
| **Max content width** | `1140px` (`.section-inner`, `.hero-inner`, `.eco-inner`) |
| **Desktop horizontal padding** | `56px` (nav, hero, sections, footer, ecosystem, CTA) |
| **Mobile horizontal padding** | `24px` (breakpoint `960px`) |
| **Section vertical padding** | `96px` desktop / `64px` mobile |
| **Hero top padding** | `80px` desktop / `60px` mobile |

### Breakpoint

Single breakpoint at **`max-width: 960px`** — stacks multi-column grids, collapses facts strip, reduces padding.

---

## Global navigation

Every page in this site uses the same nav pattern:

```html
<nav>
  <a href="/" class="nav-logo">Designing Museum Experiences</a>
  <ul class="nav-links">
    <li><a href="/#the-book">The Book</a></li>
    <li><a href="/#resources">Resources</a></li>
    <li><a href="https://museums101.com">Museums 101</a></li>
    <li><a href="https://museumplanning.com" class="cta">Hire Mark →</a></li>
  </ul>
</nav>
```

| Property | Value |
|----------|-------|
| Height | `56px` |
| Position | `sticky`, `top: 0`, `z-index: 100` |
| Background | `rgba(247,243,236,.96)` + `backdrop-filter: blur(10px)` |
| Logo | Serif italic, 16px — site title, links to `/` |
| CTA | `.cta` — `--ink` fill, `--paper` text; hover → `--gold` |

**Do not** link to museumplanner.org or museumcourses.com (retiring properties).

---

## Footer

Standard four-property footer on every page:

```html
<footer>
  <div class="footer-left">Museum-Experiences.com · A property of Museum Planning LLC · © 2026</div>
  <div class="footer-links">
    <a href="https://markwalhimer.com">Art</a>
    <a href="https://museumplanning.com">Consulting</a>
    <a href="https://museums101.com">Museums 101</a>
    <a href="https://museum-experiences.com">Experiences</a>
    <a href="mailto:mark@museumplanning.com">Contact</a>
  </div>
</footer>
```

Background `#110e09`; links `--copper` on hover.

---

## Components

### Kicker / section tag

Eyebrow label with leading hairline rule:

- **`.kicker`** — hero only; copper rule + uppercase mono
- **`.section-tag`** — section openings; same pattern, used above H2

Always place directly above the headline they introduce.

### Buttons

| Class | Use | Default | Hover |
|-------|-----|---------|-------|
| **`.btn-primary`** | Primary actions on light bg | `--ink` bg, `--paper` text | `--gold` bg |
| **`.btn-ghost`** | Secondary actions | `--rule` border, `--mid` text | `--gold` border + text |
| **`.cta-btn`** | CTA section only (dark bg) | `--copper` bg, white text | `--gold` bg |

Padding: primary/ghost `12–13px` vertical, `28–36px` horizontal.

### Hero (book landing)

Two-column grid: copy left, book cover right (`1fr 420px`, gap `80px`).

- **`.hero-desc`** — serif italic lede
- **`.pub-line`** — publisher badges below actions; mono uppercase in bordered pills
- **`.book-cover`** — max-width `380px`, layered box-shadow; always include descriptive `alt` text
- **`.book-cover-fallback`** — CSS-only cover if image fails; dark gradient + gold left rule

### Facts strip

Full-width `--ink` bar with four equal columns. Large serif number in `--copper`, mono label in muted white.

### Three-stage grid (`.stages`)

3-column grid on `--rule` gutter. Roman numeral watermark, serif title with italic subtitle in `<em>`.

### Tools grid (`.tools-grid`)

4-column grid of **`.tool-cell`** items — serif 15px labels. Intro paragraph uses serif italic (`.tools-intro`).

### Pull quote (`.pull-quote`)

Full-bleed `--ink` band. Large decorative open quote (`\201C`), serif italic body, mono uppercase cite in `--copper`.

### Resource lists (`.resource-list`)

Two-column **`.resources-grid`** on pale section background (`--pale`). List rows with **`.res-arrow`** (→ or ↓) aligned right.

### Side cards (`.course-card` pattern)

Used for consulting / companion text blocks:

- **`.course-card-tag`** — mono eyebrow in `--copper`
- Pale background or bordered box on `--cream`
- Prefer reusing this pattern over inventing new card styles

### Ecosystem grid (`.eco-grid`)

Four cards linking to primary properties (Art · Consulting · Museums 101 · Experiences). 4-column desktop, 2-column mobile.

### CTA section (`.cta-section`)

Dark `--ink` with centered headline, italic subcopy, single **`.cta-btn`**. Optional radial copper glow via `::before`.

---

## Page structure template

New pages should follow this order:

1. **`<head>`** — SEO block per [README.md](./README.md); reuse font link and inline styles (or extract shared CSS later)
2. **Nav** — global pattern above
3. **Main content** — one or more **`.section`** blocks inside **`.section-inner`**
4. **Ecosystem** (optional on sub-pages; required on homepage)
5. **CTA section** (optional — use when routing to consulting)
6. **Footer** — global pattern above

Sub-pages (e.g. `/resources/`) may use a simpler hero — single column with **`.section-tag`** + **H1** — but must reuse tokens and nav/footer.

---

## Motion

- **`.fadeUp`** — `fadeUp` keyframe: opacity 0→1, translateY 20px→0, ~0.6s ease
- Hero elements stagger delays (`0.1s`–`0.5s`)
- Hover transitions: `0.2s` on backgrounds, borders, and color
- `html { scroll-behavior: smooth; }` for anchor links

Keep motion subtle. No bounce, parallax, or scroll-jacking.

---

## Voice and content

- **Voice:** Clear, practitioner-facing, book-authoritative — not sales-heavy
- **Consulting mentions:** Brief; link to museumplanning.com; do not target consulting SEO keywords in body copy
- **Keywords for this site:** visitor experience, journey mapping, inclusive design, immersive experiences, designing museum experiences, mark walhimer
- **Publisher line:** Rowman & Littlefield · AAM Press · 2021 (when citing the book)

---

## Four-property cross-links

When linking to sibling sites, use this order and labeling:

1. **markwalhimer.com** — Art  
2. **museumplanning.com** — Consulting  
3. **museums101.com** — Museums 101  
4. **museum-experiences.com** — Experiences (this site)

Schema `sameAs` on the homepage lists the same four domains.

---

## Do not

- Use Playfair Display, Lato, or Open Sans (those belong to museumplanning.com / old WordPress)
- Add Museum Planner or Museum Courses to nav, footer, or ecosystem
- Use dark-mode-only layouts — this site is light-first
- Inline arbitrary hex colors outside the token table
- Break the `1140px` max-width content column without good reason

---

## File maintenance

When changing visual design:

1. Update CSS in `index.html` (or future shared stylesheet)
2. Update this **STYLE-GUIDE.md** in the same commit
3. Apply the same nav and footer to all HTML pages in the repo

Related guides (different sites — do not merge blindly):

- `Museum-Planning-LLC/website-2.0/STYLE-GUIDE.md` — museumplanning.com  
- `Museum-Planning-LLC/museums-101` — separate book site (Playfair + red; align over time if desired)
