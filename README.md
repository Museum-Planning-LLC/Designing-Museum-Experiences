# Designing Museum Experiences

Official hub for [*Designing Museum Experiences*](https://museum-experiences.com/) by Mark Walhimer (Rowman & Littlefield / AAM Press, 2021) — a how-to guide for visitor-centered, inclusive, and immersive museum experiences.

Static site deployed via **GitHub Pages** at **[museum-experiences.com](https://museum-experiences.com/)**.

---

## Four primary properties

This site is one of four primary web properties in a unified Mark Walhimer / Museum Planning LLC brand:

| Site | Role | Search intent |
|------|------|---------------|
| **[markwalhimer.com](https://markwalhimer.com/)** | Art practice — selected works, catalog, studio | Curators, collectors, residency programs |
| **[museumplanning.com](https://museumplanning.com/)** | Commercial consulting — hire, services, contact | Museum consultant, feasibility, master planning, capital campaign |
| **[museums101.com](https://museums101.com/)** | Book 1 — *Museums 101* | Starting a museum, governance, museum basics |
| **[museum-experiences.com](https://museum-experiences.com/)** | Book 2 — *Designing Museum Experiences* (this site) | Visitor experience design, journey mapping, inclusive & immersive experiences |

Each site owns a distinct keyword lane. Consulting service terms belong on **museumplanning.com**, not here.

---

## Retiring properties

These are being phased out to reduce SEO cannibalization and simplify the brand:

| Property | Status | Notes |
|----------|--------|-------|
| **museum-experiences.com (WordPress)** | Retiring | Replaced by this static GitHub Pages site |
| **museumplanner.org** | Retiring | 400+ articles competed with museumplanning.com for “museum planning” and “feasibility” queries; use noindex + 301 redirects, not hard 404s |
| **museumcourses.com** | Retiring | Low SEO value; cannibalization risk vs. paid consulting; 301 → museum-experiences.com if course remains elsewhere |

**mark-walhimer.com** → redirecting to **markwalhimer.com** (hyphen dropped).

---

## SEO on this site

Implemented in `index.html` (May 2026):

- `<title>`, meta description, keywords (book / experience-design focused)
- `robots`: index, follow
- Canonical: `https://museum-experiences.com/`
- Open Graph + Twitter Card (`summary_large_image`)
- JSON-LD: `Book`, `Person`, `WebSite`, `Organization` with `sameAs` linking all four primary domains
- `robots.txt`, `sitemap.xml`
- Self-hosted cover image at `images/designing-museum-experiences-cover.jpg`

### Keywords this site targets

- designing museum experiences
- mark walhimer
- visitor-centered museum design
- inclusive museum experiences
- immersive museum experiences
- museum visitor journey mapping
- museum experience design

### Keywords that belong elsewhere

| Keyword | Owner |
|---------|-------|
| museum consultant, feasibility studies, master planning, strategic planning, capital campaign | museumplanning.com |
| starting a museum, museum basics, governance | museums101.com |
| digital art, installations, selected works | markwalhimer.com |

---

## Migration from WordPress

### Current state

- **This repo** is the replacement for the old WordPress site at museum-experiences.com.
- `CNAME` points GitHub Pages at `museum-experiences.com`.
- DNS for `museum-experiences.com` may still resolve to WordPress (SiteGround) until cutover — visitors see the old site until DNS is updated.

### DNS cutover checklist

1. **GitHub** → Settings → Pages → confirm custom domain `museum-experiences.com` → enable **Enforce HTTPS**
2. **DNS** at registrar:
   - `A` records for apex → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - Or `CNAME` for `www` → `museum-planning-llc.github.io`
3. Wait for propagation; verify new static site loads
4. **Retire WordPress** — keep 301 redirects from old URLs for 6–12 months minimum
5. **Google Search Console** — submit sitemap, request indexing, monitor URL changes

### WordPress URL redirect map (to build)

Old WordPress paths that need 301 targets before shutdown:

| Old path | Planned destination |
|----------|---------------------|
| `/` | `/` (this site) |
| `/resources/` | `/resources/` (live) |
| `/museum-toolbox/` | `/resources/#toolbox` |
| Other indexed URLs | Map individually or redirect to `/` |

---

## Pending work

- [ ] **DNS cutover** — point museum-experiences.com to GitHub Pages
- [x] **Resource pages** — `/resources/` with templates, checklists, toolbox, and reading links
- [ ] **museum-toolbox/** — merged into `/resources/#toolbox`; add redirect from old WordPress URL
- [ ] **WordPress 301 redirects** — full URL map before shutdown
- [ ] **museumplanning.com** — update footer/links to four-site navigation (remove Museum Planner / Courses)
- [ ] **museums101.com** — migrate from WordPress to static GitHub site; trim meta keywords to avoid consulting cannibalization
- [ ] **markwalhimer.com** — configure DNS (replacing mark-walhimer.com)
- [ ] **museumplanner.org / museumcourses.com** — noindex + redirect strategy

---

## Repo structure

```
Designing-Museum-Experiences/
├── index.html          # Single-page book hub
├── assets/
│   └── site.css        # Shared styles (homepage + subpages)
├── resources/
│   ├── index.html      # Companion resources hub
│   └── downloads/      # Self-hosted PDFs
├── STYLE-GUIDE.md      # Visual and structural source of truth
├── CNAME               # museum-experiences.com
├── robots.txt
├── sitemap.xml
├── images/
│   └── designing-museum-experiences-cover.jpg
└── README.md           # Strategy, SEO, migration plan
```

---

## Related repos

| Repo | Site |
|------|------|
| [Museum-Planning-LLC/website-2.0](https://github.com/Museum-Planning-LLC/website-2.0) | museumplanning.com |
| [Museum-Planning-LLC/museums-101](https://github.com/Museum-Planning-LLC/museums-101) | museums101.com |
| [walhimer/walhimer.github.io](https://github.com/walhimer/walhimer.github.io) | markwalhimer.com (art) |

---

## Local development

No build step. Open `index.html` in a browser or serve locally:

```bash
python3 -m http.server 8080
# → http://localhost:8080
```

---

## Contact

**Museum Planning LLC** — [museumplanning.com](https://museumplanning.com/) · mark@museumplanning.com

*Designing Museum Experiences* · A property of Museum Planning LLC · © 2026
