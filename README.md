# Saran Kumar KC — Marketing Portfolio
### Project Documentation

---

## Table of Contents

1. [Project Overview](#1-project-overview)
2. [File Structure](#2-file-structure)
3. [Page Descriptions & Routing](#3-page-descriptions--routing)
4. [Design System](#4-design-system)
   - [CSS Custom Properties (Variables)](#css-custom-properties-variables)
   - [Typography](#typography)
   - [Color Usage Guide](#color-usage-guide)
5. [Shared CSS Components](#5-shared-css-components)
   - [Custom Cursor](#custom-cursor)
   - [Navigation Bar & Hamburger Menu](#navigation-bar--hamburger-menu)
   - [Buttons](#buttons)
   - [Typography Classes](#typography-classes)
   - [Cards](#cards)
   - [Lists](#lists)
   - [Metrics Grid](#metrics-grid)
   - [Data Table](#data-table)
   - [Notion Button](#notion-button)
6. [Animation System](#6-animation-system)
7. [Page-Specific Styles & Content](#7-page-specific-styles--content)
   - [index.html — Sections](#indexhtml--sections)
   - [clients.html](#clientshtml)
   - [case-studies.html](#case-studieshtml)
8. [JavaScript Behaviour](#8-javascript-behaviour)
9. [External Links & Integrations](#9-external-links--integrations)
10. [Responsive Breakpoints](#10-responsive-breakpoints)
11. [Changelog](#11-changelog)
12. [Deployment Notes](#12-deployment-notes)

---

## 1. Project Overview

A static HTML/CSS/JS personal marketing portfolio for **Saran Kumar KC**, a Digital Marketing Executive. The site showcases work across Content Creation, SEO, Social Media, Client Experience, and Case Studies — with dedicated pages for each.

- **Stack:** Pure HTML5, embedded CSS, vanilla JavaScript
- **Fonts:** Google Fonts (loaded via CDN)
- **No build step required** — open `index.html` directly in a browser
- **Deployment:** GitHub Pages / Netlify-compatible (all styles embedded in each file for full portability)
- **Live site:** `https://mahadevanpb.github.io/Saran-Portfolio/index.html`

---

## 2. File Structure

```
Saran Port/
├── index.html              # Main portfolio homepage
├── clients.html            # Client Experience page (9 brands)
├── case-studies.html       # Case Studies page (4 expandable studies)
├── content-creation.html   # Case study: Content Creation at HighBizz
├── seo.html                # Case study: SEO & Copywriting at HighBizz
├── social-media.html       # Case study: Social Media Management at HighBizz
├── images/                 # Local assets
│   ├── aster-holidays.png
│   ├── aster-travel.png
│   ├── arigato-wellness.svg
│   ├── geown-properties.png
│   ├── mana-herbals.avif
│   ├── pruthvi-projects.png
│   ├── sdp-stones.webp
│   ├── venue-by-choice.png
│   ├── Screenshot_2026-01-05_021256.png   # Space Technique — GSC screenshot
│   ├── Screenshot_2026-01-05_021456.png   # Pruthvi Projects — GSC screenshot
│   ├── Screenshot_2026-01-05_035938.png   # Palagiri Construction — GSC screenshot
│   ├── Screenshot_2026-01-05_040103.png   # Geown Properties — GSC screenshot
│   └── Screenshot_2026-01-05_040328.png   # Aster Travel — GSC screenshot
├── notion-attach/          # Exported Notion pages used as content source
│   ├── content-creation-notion.html
│   ├── social-media-notion.html
│   └── seo/
│       ├── SEO d3ba57b8526b83da9b368138652070f9.html
│       └── Screenshot_2026-01-05_*.png    # (5 GSC screenshots)
├── portfoliov1/            # Snapshot of site before April 2026 update
├── portfoliov2/            # Snapshot of site before content-embed update
├── Saran_Portfolio_LLM_Instructions.md
└── README.md
```

> **Note:** All CSS is embedded inside a `<style>` block within each HTML file. There is no external stylesheet. This was a deliberate choice for portability — each page is fully self-contained.

---

## 3. Page Descriptions & Routing

### Navigation Flow

```
index.html
├── #hero          → Landing section
├── #about         → About Me (+ Why Me? + My Approach blocks)
├── #experience    → Work Experience (HighBizz + Brandstory) — NEW
├── #my-work       → Work navigation cards
│   ├── clients.html          → Client Experience — NEW
│   ├── case-studies.html     → Case Studies — NEW
│   ├── content-creation.html → "← Back" returns to index.html#my-work
│   ├── seo.html              → "← Back" returns to index.html#my-work
│   └── social-media.html     → "← Back" returns to index.html#my-work
├── #skills        → Core Skills + Tools & Certifications
├── #education     → Education timeline
├── #awards        → Achievements & Awards
└── #contact       → Contact info & footer
```

### Page-by-Page Summary

| File | Title | Background | Purpose |
|---|---|---|---|
| `index.html` | Saran Kumar KC — Marketing Portfolio | Multi-section (dark/light alternating) | Full portfolio homepage |
| `clients.html` | Client Experience — Saran Kumar KC | `var(--ink-mid)` dark | 9 client brand cards with logos |
| `case-studies.html` | Case Studies — Saran Kumar KC | `var(--ink-mid)` dark | 4 expandable case study accordions |
| `content-creation.html` | Content Creation — Saran Kumar KC | `var(--ink)` pure dark | Content Creation case study |
| `seo.html` | SEO & Copywriting — Saran Kumar KC | `var(--ink-mid)` dark | SEO case study |
| `social-media.html` | Social Media — Saran Kumar KC | `var(--ink)` pure dark | Social Media case study |

### Work Section Card Order (My Work)

Cards appear in the following order on `index.html#my-work`:
1. 🤝 **Clients** → `clients.html`
2. 🔬 **Case Studies** → `case-studies.html`
3. 🎬 **Content Creation** → `content-creation.html`
4. 🔍 **SEO** → `seo.html`
5. 📱 **Social Media** → `social-media.html`

---

## 4. Design System

### CSS Custom Properties (Variables)

Defined in `:root` on every page:

```css
:root {
  --ink:       #0d0d0d;   /* Deepest dark — used for dark backgrounds and base text */
  --ink-mid:   #1a1a1a;   /* Slightly lighter dark — used for mid-tone dark sections */
  --off-white: #f4f0e8;   /* Warm off-white — used for text on dark, and light backgrounds */
  --warm-gray: #e8e4dc;   /* Warm gray — used as a lighter section background */
  --accent:    #d4531a;   /* Burnt orange — primary accent, CTAs, arrows, highlights */
  --accent2:   #1a4d3e;   /* Deep forest green — Awards section background */
  --accent3:   #c9a84c;   /* Warm gold — secondary accent, gold labels */
}
```

### Typography

Three Google Fonts are loaded on every page:

```html
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Instrument+Serif:ital@0;1&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet">
```

| Font | Usage |
|---|---|
| **Bebas Neue** | Display headings, titles, hero text, nav logo, mobile menu links |
| **Instrument Serif** | Decorative subtitles, pull quotes, italic accents |
| **Syne** | Body text, nav links, labels, buttons |

### Color Usage Guide

| Context | Color |
|---|---|
| Dark section background | `var(--ink)` or `var(--ink-mid)` |
| Primary CTA / arrows / accents | `var(--accent)` — `#d4531a` |
| Text on dark bg | `var(--off-white)` or `rgba(244,240,232,0.75)` |
| Muted text on dark bg | `rgba(244, 240, 232, 0.55)` |
| Gold labels / secondary accent | `var(--accent3)` — `#c9a84c` |
| Experience timeline (Brandstory) | `var(--accent3)` border |

---

## 5. Shared CSS Components

### Custom Cursor

The site uses a custom two-element cursor replacing the default browser cursor (`cursor: none` on `body`).

```html
<div id="cur"></div>    <!-- Small filled orange dot -->
<div id="curl"></div>   <!-- Larger orange ring outline -->
```

Additionally, 7 **cursor trail particles** (`.c-trail`) are injected by JS for a comet-tail effect on `index.html`.

---

### Navigation Bar & Hamburger Menu

Fixed at the top of every page. Dark glassmorphism style.

```css
nav {
  position: fixed; top: 0; z-index: 200;
  background: rgba(13, 13, 13, 0.95);
  backdrop-filter: blur(10px);
}
```

**Desktop nav links (index.html):** About · Experience · Work · Skills · Education · Contact

**Desktop nav links (clients.html, case-studies.html):** About · Experience · Work · Skills · Education · Contact (all link to `index.html#{section}`)

**Mobile (≤860px):** Nav links hidden. A 3-line hamburger button (`.hamburger`) appears. Clicking it opens a full-screen dark overlay (`.mobile-menu`) with large Bebas Neue links.

Hamburger animation: spans rotate and fade into an ✕ on open. Body scroll is locked while open.

---

### Buttons

#### Back Button (all sub-pages)
```html
<a href="index.html#my-work" class="back-btn">← Back to Work</a>
```
- Target: `index.html#my-work`
- Hover: slides left 4px

#### Hero CTA Button (`index.html`)
```html
<a href="#my-work" class="hero-btn">View My Work ↓</a>
```
Has **magnetic hover** effect (follows cursor slightly) and **ripple on click**.

#### Notion Button (case study pages)
A centered CTA at the bottom of each case study. Has permanent **glow-pulse animation** and **ripple on click**.

| Page | Button Text | Notion URL |
|---|---|---|
| `content-creation.html` | *(Removed — replaced with inline embeds)* | — |
| `seo.html` | *(Removed — replaced with inline content sections)* | — |
| `social-media.html` | *(Removed — replaced with inline embeds)* | — |

---

### Typography Classes

```css
.section-label          /* Small orange uppercase label */
.port-heading.light     /* Large Bebas Neue title on dark backgrounds */
.port-heading.dark      /* Large Bebas Neue title on light backgrounds */
.port-intro.light       /* Body intro paragraph on dark backgrounds */
```

---

### Cards

Used across `index.html` (experience section) and case study pages:

```css
.card          { background: rgba(244,240,232,0.06); border-radius: 10px; padding: 24px 28px; }
.card.on-light { background: white; border-color: rgba(13,13,13,0.1); box-shadow: ...; }
```

Experience cards use: `.card.on-light` with a colored left border (`var(--accent)` for HighBizz, `var(--accent3)` for Brandstory).

---

### Lists

Arrow-prefixed bullet lists. The `→` arrow is added automatically via CSS `::before`.

> **Important:** Do NOT manually add `→` arrows inside `<li>` tags — the CSS `::before` pseudo-element adds them automatically. Manually adding them results in double arrows.

---

### Metrics Grid

Used in `content-creation.html` for key numbers. 3-col on desktop → 2-col on tablet → 1-col on phone.

---

### Data Table

Used in `social-media.html`. On mobile (≤860px): `display: block; overflow-x: auto` for horizontal scrolling.

---

### Notion Button

```css
.notion-btn {
  animation: notionPulse 2.6s ease-in-out infinite;
}
@keyframes notionPulse {
  0%,100% { box-shadow: 0 4px 28px rgba(212,83,26,0.35); }
  50%      { box-shadow: 0 8px 52px rgba(212,83,26,0.72), 0 0 0 5px rgba(212,83,26,0.12); }
}
```

---

## 6. Animation System

### index.html Animations

| Animation | Trigger | Description |
|---|---|---|
| **Scroll progress bar** (`#scroll-prog`) | Scroll | Glowing orange shimmer bar fills across the top of the page as user scrolls |
| **Hero title scramble** | Page load (600ms delay) | Letters rapidly cycle through random chars before resolving to "SARAN KC" |
| **Typewriter cursor** | Always | Blinking `|` cursor after the hero subtitle via `::after` |
| **Cursor trail** | Mouse move | 7 staggered orange dots follow the cursor with increasing delay |
| **Divider running-light** | Always | The orange/dark stripe divider animates like a running LED strip |
| **Hero glow breathe** | Always | Radial orange glow pulses in opacity + floats |
| **Magnetic buttons** | Hover | Hero CTA and contact pills follow the cursor; snap back on leave |
| **Ripple on click** | Click | White circular ripple expands from click point on hero btn and contact pills |
| **Tag cloud stagger** | Scroll into view | Skill tags pop in one-by-one with 55ms delay chain |
| **Cert list stagger** | Scroll into view | Cert items slide in from the left with 90ms delay chain |
| **Award list stagger** | Scroll into view | Award items rise up with 100ms delay chain |
| **Work card stagger** | Scroll into view | Work nav cards drop in one-by-one with 80ms delay chain |
| **Nav logo glitch** | Hover | "SARAN KC" logo scrambles characters before resolving back |
| **Section reveals** | Scroll into view | `.reveal`, `.reveal-l`, `.reveal-r`, `.t-item` fade/slide in via `IntersectionObserver` |

### clients.html Animations

| Animation | Trigger | Description |
|---|---|---|
| **Card scroll reveal** | Scroll into view | Each client card fades up with a staggered `transitionDelay` (70ms per card) |

### case-studies.html Animations

| Animation | Trigger | Description |
|---|---|---|
| **Card scroll reveal** | Scroll into view | Each case study card fades up on scroll via `IntersectionObserver` |
| **Accordion expand** | Click header | `.cs-body` expands via `max-height` transition (0 → 800px) with cubic-bezier easing |
| **Toggle icon rotation** | Active header | The `+` icon rotates 45° to become `×` when open |

### Case Study Page Animations (content-creation, seo, social-media)

| Animation | Pages | Description |
|---|---|---|
| **Page load slide-up** | All 3 | `.case-container` fades in and slides up on arrival |
| **List item stagger** | All 3 | Bullet points slide in from the left, 70ms delay chain |
| **Card stagger** | CC + SEO | Cards fade up as they enter the viewport |
| **Metric scale-in** | CC only | Metric boxes scale from 92% to 100% with stagger |
| **Table row stagger** | Social Media | Each table row slides in from the left, 80ms delay chain |
| **Notion btn pulse** | All 3 | Continuous glow shadow pulse |
| **Notion btn ripple** | All 3 | White ripple spreads from click point |

---

## 7. Page-Specific Styles & Content

### index.html — Sections

| Section ID | Background | Key Elements |
|---|---|---|
| `#hero` | `var(--ink)` | Animated stripe + breathing glow, scramble title, typewriter subtitle, magnetic CTA |
| `#about` | `var(--ink-mid)` | 2-col grid (text + info cards), Why Me? block, My Approach block |
| `#experience` | `var(--off-white)` | Two work experience cards (HighBizz + Brandstory) with categorised bullet points |
| `#my-work` | `var(--off-white)` | 5 staggered work-card nav links |
| `#skills` | `var(--ink)` | Core Skills tag cloud + Tools tag cloud (stagger on scroll) + cert list |
| `#education` | `var(--off-white)` | Vertical timeline with scroll-reveal |
| `#awards` | `var(--accent2)` | Staggered award list, including published research entry |
| `#contact` | `var(--ink)` | Magnetic contact pills |

#### About Section Info Cards

| Icon | Label | Value |
|---|---|---|
| 💼 | Current Role | Digital Marketing Executive · HighBizz |
| 🎓 | Education | MBA – Marketing · Alliance Ascent College, Bengaluru |
| 🎯 | Specialisations | SEO · Content Creation · Social Media Marketing |
| 📍 | Location | Bengaluru, Karnataka, India |
| 📩 | Email | kcsaran2001@gmail.com |

#### Experience Section

**Entry 1 — Digital Marketing Executive (Intern)**
- Company: HighBizz · Bengaluru
- Duration: Aug 2025 – Present
- Categories: SEO · Social Media · Email Marketing · Content Creation · Analytics

**Entry 2 — Marketing Intern**
- Company: Brandstory · Bengaluru
- Duration: Jun 2024 – Aug 2024

#### Skills Section

**Core Skills tag cloud:**
SEO · Keyword Research · Backlink Building · On-Page SEO · Local SEO · Content Strategy · Social Media Management · Reels Creation · Content Shoots · Email Marketing · Performance Marketing (Meta Ads) · Market Research · Analytics & Reporting · Influencer/UGC Research

**Tools I Use:**
Google Analytics · Search Console · SEMrush · Yoast SEO · Rank Math · WordPress · GA4 · Google Ads Planner · Meta Business Suite · Canva · Microsoft Office · G Suite · Notion · Instagram · LinkedIn · **Brevo · CapCut · ChatGPT / AI Tools · Excel**

#### Achievements Section (top-to-bottom order)
1. 🧠 Published Research — "How Humor in Advertising Influences Consumer Decision-Making"
2. 🏅 Organised and led "ALLIANCE ONE" inter-college event
3. 🥇 Winner of inter-college volleyball tournament
4. 🎤 Represented college in marketing competitions
5. 📢 Volunteered in on-campus marketing campaigns

---

### clients.html

**Page heading:** `client experience.`
**Subheading:** `9 brands across D2C, Real Estate, Healthcare, Travel & Events`

#### Client Cards

All 9 cards display: logo · brand name · industry tag · service tags.

| # | Client | Industry | Logo Source | Services |
|---|---|---|---|---|
| 1 | Aster Holidays | Hospitality – Resorts | `images/aster-holidays.png` | SEO · Social Media · Email Marketing · Local SEO |
| 2 | Aster Travel | B2B Travel | `images/aster-travel.png` | SEO · Email Marketing |
| 3 | Venue By Choice | Event Platform | `images/venue-by-choice.png` | SEO · Social Media · Local SEO |
| 4 | Vahaan Oils | D2C (Edible Oils) | Emoji 🛢 (placeholder) | SEO · Content Strategy · Meta Ads |
| 5 | Arigato Wellness Centre | Healthcare & Wellness | `images/arigato-wellness.svg` | SEO · Social Media · Content Shoots · Local SEO |
| 6 | Geown Properties | Real Estate | `images/geown-properties.png` | SEO · Social Media |
| 7 | Pruthvi Projects | Real Estate | `images/pruthvi-projects.png` | SEO · Content |
| 8 | Mana Herbals | D2C Ayurveda | `images/mana-herbals.avif` | SEO · Content |
| 9 | SDP Stones | Building Materials | `images/sdp-stones.webp` | SEO · Local SEO |

> **Logo handling:** Local files in `/images` take priority. If a logo file is missing for a brand (e.g. Vahaan Oils), a generic emoji is shown instead. To add a logo later: drop `vahaan-oils.{ext}` into `/images` and update the `src` in `clients.html`.

#### Card Reveal Animation
Each `.client-card` starts with `opacity: 0; transform: translateY(28px)`. An `IntersectionObserver` adds `.vis` class (making it visible) with a per-card `transitionDelay` stagger.

---

### case-studies.html

**Page heading:** `case studies.`
**Subheading:** `Real problems. Real strategies. Real results.`

#### Case Studies (accordion — click to expand)

| # | Title | Industry | Key Insight |
|---|---|---|---|
| 01 | Aster Holidays — Building a Travel Growth Engine | Hospitality | SEO + Content + Email = full-funnel growth |
| 02 | Arigato Wellness Centre — Trust-Based Healthcare Marketing | Healthcare & Wellness | Authentic content builds trust faster than paid ads |
| 03 | Vahaan Oils — D2C Positioning Strategy | D2C Edible Oils | Positioning > Promotion |
| 04 | Venue By Choice — Capturing Search Intent | Event Platform | Capture existing demand first |

Each study shows 3 columns: **Problem · Action · Result**, plus a gold **💡 Insight** bar spanning the full width.

#### Accordion Behaviour
- One study open at a time (clicking another closes the open one)
- `max-height: 0 → 800px` transition with `cubic-bezier(0.4, 0, 0.2, 1)` easing
- `.cs-body-inner` padding: `24px 30px 30px` (top padding added to prevent content touching the header border)
- The `+` toggle icon rotates 45° → becomes `×` when active

---

## 8. JavaScript Behaviour

All pages share the same base cursor JS. `index.html` has the full animation suite.

### Scroll Progress Bar (`index.html` only)
```js
function updateProgress() {
    const scrolled = window.scrollY || document.documentElement.scrollTop;
    const total = document.documentElement.scrollHeight - document.documentElement.clientHeight;
    prog.style.width = Math.min((scrolled / total) * 100, 100) + '%';
}
window.addEventListener('scroll', updateProgress, { passive: true });
window.addEventListener('resize', updateProgress, { passive: true });
```

### Hamburger Menu (all pages)
```js
function toggleMenu(open) {
    ham.classList.toggle('open', open);
    mobMenu.classList.toggle('open', open);
    document.body.style.overflow = open ? 'hidden' : '';
}
ham.addEventListener('click', () => toggleMenu(!mobMenu.classList.contains('open')));
mobMenu.querySelectorAll('a').forEach(a => a.addEventListener('click', () => toggleMenu(false)));
```

### Scroll Reveal — Section Animations (`index.html` only)
`IntersectionObserver` watches `.reveal`, `.reveal-l`, `.reveal-r`, `.t-item` → adds `.vis` class when in viewport.

Separate observers for `.tags`, `.cert-list`, `.award-list`, `.work-nav` trigger stagger chains.

### Case Study Accordion (`case-studies.html`)
```js
function toggleCS(header) {
    const body = header.nextElementSibling;
    const isOpen = body.classList.contains('open');
    document.querySelectorAll('.cs-body').forEach(b => b.classList.remove('open'));
    document.querySelectorAll('.cs-header').forEach(h => h.classList.remove('active'));
    if (!isOpen) {
        body.classList.add('open');
        header.classList.add('active');
    }
}
```

---

## 9. External Links & Integrations

| Service | URL | Used in |
|---|---|---|
| Google Fonts | `fonts.googleapis.com` | All pages |
| Instagram Embed API | `https://www.instagram.com/embed.js` | `content-creation.html`, `social-media.html` |
| Miro Live Embed | `miro.com/app/live-embed/uXjVJQDKUo8=` | `social-media.html` |
| Canva Embed (Design 01) | `canva.com/design/DAG9XfYaN9k/…/view?embed` | `seo.html` |
| Canva Embed (Design 02) | `canva.com/design/DAG8PcxvRX8/…/view?embed` | `seo.html` |
| Canva Embed (Design 03) | `canva.com/design/DAG67DWjtLw/…/view?embed` | `seo.html` |
| LinkedIn | `linkedin.com/in/saran-kumar-kc` | All pages (contact/footer) |
| Email (mailto) | `kcsaran2001@gmail.com` | All pages (contact/footer) |
| Phone (tel) | `+91 63799 70050` | All pages (contact/footer) |

---

## 10. Responsive Breakpoints

```
≤860px  — Tablet/mobile: hamburger menu, stacked grids, reduced section padding
≤480px  — Small phone: tighter font sizes, stacked contact pills, single-column layouts
```

### Key changes at ≤860px (all pages)
- Nav links hidden → hamburger shown
- Section padding: `100px 10vw` → `80px 5vw` (or `60px 5vw` on sub-pages)
- About, skills, two-col grids: collapse to single column
- Work cards: wrap into 2-per-row
- Data table: horizontal scroll enabled
- Case study accordion body: single-column layout

### Key changes at ≤480px
- Hero title: scales via `clamp(3.5rem, 18vw, 16rem)`
- Footer heading: `clamp(2rem, 14vw, 7rem)`
- Contact pills: stack vertically, full-width
- Work cards: full-width single column
- Client cards: single column grid
- Notion button: reduced padding

---

## 11. Changelog

### April 2026 Update

#### `index.html`
- **Fixed:** Job title corrected from `Digital Marketing Manager` → `Digital Marketing Executive · HighBizz`
- **Added:** "⚡ Why Me?" stats block in the About section (9+ clients, 12–20% SEO growth, 300+ backlinks, etc.)
- **Added:** "🧩 My Marketing Approach" 4-step framework block in the About section
- **Added:** `#experience` section (Work Experience) between About and My Work, with two entries:
  - Digital Marketing Executive (Intern) · HighBizz · Aug 2025–Present
  - Marketing Intern · Brandstory · Jun 2024–Aug 2024
- **Added:** `Experience` link to desktop navbar and mobile menu
- **Added:** Core Skills tag cloud above the Tools grid in `#skills`
- **Added:** 4 new tools to "Tools I Use": Brevo · CapCut · ChatGPT / AI Tools · Excel
- **Added:** Published Research achievement at the top of `#awards`
- **Added:** 🤝 Clients and 🔬 Case Studies work cards to `#my-work`
- **Reordered:** Work cards — Clients and Case Studies now appear first
- **Removed:** "Skills & Certs" and "Education" buttons from the My Work section

#### `clients.html` — New File
- 9 client brand cards with logos, industry tags, and service tags
- Local image files from `/images` folder used for all available logos
- Vahaan Oils uses emoji placeholder (no logo available)

#### `case-studies.html` — New File
- 4 expandable accordion case studies
- Each study: Problem · Action · Result columns + 💡 Insight bar
- Smooth `max-height` accordion animation
- Fixed inner padding (`24px 30px 30px`) to prevent content touching the header border

#### `images/` — New Folder
- Local logo assets for 8 of the 9 clients
- Mixed formats supported: `.png`, `.svg`, `.avif`, `.webp`

#### `portfoliov1/` — New Folder
- Full snapshot of the original site before the April 2026 update

---

### April 2026 — Content Embed Update

> This update replaced all external Notion portfolio buttons with inline, embedded content directly on each case study page.

#### Files Changed

| File | Change Type | Summary |
|---|---|---|
| `content-creation.html` | Modified | Replaced Notion button with Instagram reel embeds grid |
| `social-media.html` | Modified | Replaced Notion button with Miro board iframe + Instagram reel embed grid |
| `seo.html` | Modified | Replaced Notion button with Email Marketing section, Canva newsletter embeds, and GSC screenshot grid |
| `images/` | Modified | Added 5 Google Search Console screenshot PNGs from `notion-attach/seo/` |
| `portfoliov2/` | New Folder | Full backup of site files taken before this update |

#### `content-creation.html`
- **Removed:** "View Content Portfolio ↗" Notion button
- **Added:** `.notion-content-section` block with:
  - **8 Instagram reel embeds** in a responsive `reel-embed-grid` (2-col, `auto-fit minmax(320px, 1fr)`)
  - Each reel uses the official `<blockquote class="instagram-media">` embed format
  - Instagram `embed.js` loaded via `<script async src="https://www.instagram.com/embed.js">`
- **CSS added:** `.reel-embed-grid`, `.embed-wrap`, `.embed-wrap > .instagram-media` (scoped under `.notion-content-section`)
- **Security:** All external links use `rel="noopener noreferrer"`
- **Note:** A broken-link "Reference Content" section (5 annotated format embeds) was added then later removed in the same session

#### `social-media.html`
- **Removed:** "View Social Media Portfolio ↗" Notion button
- **Added:** `.notion-content-section` block with:
  - **Miro Board iframe embed** — live-embed URL (`?embedMode=view_only_without_ui`) displayed at 520px height in a rounded dark container with a subtle "Open in Miro ↗" fallback link
  - **8 Instagram reel embeds** in a responsive `reel-embed-grid` (same pattern as `content-creation.html`)
- **CSS added:** `.reel-embed-grid`, `.embed-wrap`, `.ref-embed`, `.miro-embed-wrap`, `.miro-fallback`, `hr.notion-divider`
- **Note:** A broken-link "Reference Content" section (5 annotated growth format embeds) was added then later removed

#### `seo.html`
- **Removed:** "View SEO Portfolio ↗" Notion button
- **Added:** `.notion-content-section` block with:
  1. **Email Marketing section** — 3 detailed sub-bullets (newsletter design, subject-line optimisation, engagement monitoring)
  2. **Newsletter Designs** — 3 Canva newsletter designs embedded as portrait iframes (`?embed` URL parameter) in a 3-col responsive grid (`canva-embed-row`). Each embed uses A4 aspect ratio (`padding-top: 141%`) with a "Open in Canva ↗" fallback link
  3. **Clients SEO Performance** — 5 Google Search Console screenshots embedded as a labelled image grid:
     - Row 1 (3-col): Space Technique · Palagiri Construction · Pruthvi Projects
     - Row 2 (2-col): Geown Properties · Aster Travel
- **CSS added:** `.notion-content-section`, `.canva-embed-row`, `.canva-embed-wrap`, `.canva-embed-label`, `.iframe-ratio`, `.canva-fallback`, `.seo-img-grid`, `.img-wrap`, `.img-label`
- **Images:** 5 PNG screenshots copied from `notion-attach/seo/` → `images/`

#### Embed Compatibility Notes

| Embed Type | Requirement | Fallback if failed |
|---|---|---|
| Instagram reels | Post must be public | "View on Instagram" text link |
| Miro board | Board must be set to public/shareable | "Open in Miro ↗" link |
| Canva designs | Design must be "Anyone with link can view" | "Open in Canva ↗" link |

---

## 12. Deployment Notes

- **No build process.** All files are plain HTML with embedded CSS and JS.
- **GitHub Pages:** Push to the `main` branch of `mahadevanpb/Saran-Portfolio`. Entry point is `index.html`.
- **Netlify:** Drag the `Saran Port/` folder into Netlify Drop, or connect via Git.
- **All styles are embedded** inside each HTML file — no broken CSS links on deployment.
- **All pages linked relatively** (e.g., `href="clients.html"`) — keep all `.html` files in the same directory.
- **Images folder:** The `/images` folder must be deployed alongside the HTML files. Includes both logo assets and 5 GSC performance screenshots added in the content embed update.
- **Google Fonts require internet.** The site uses system fallback fonts (`sans-serif`) if offline.
- **Instagram embeds require internet.** `embed.js` loads from `instagram.com`; reel embeds will show a fallback link if the script fails or the post is deleted/privatised.
- **Miro embed requires internet and public board access.** If the Miro board is set to "private", the iframe will show a login screen.
- **Canva embeds require internet and public design access.** Each Canva design must be set to "Anyone with the link can view" for the `?embed` iframe to load. If not, a login screen is shown instead.
- **`portfoliov1/` and `portfoliov2/` folders** are local backups — they do not need to be deployed and can be excluded from the repo.
- **`notion-attach/` folder** is a local content source — it does not need to be deployed.
