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
   - [index.html Animations](#indexhtml-animations)
   - [Case Study Page Animations](#case-study-page-animations)
7. [Page-Specific Styles](#7-page-specific-styles)
8. [JavaScript Behaviour](#8-javascript-behaviour)
9. [External Links & Integrations](#9-external-links--integrations)
10. [Responsive Breakpoints](#10-responsive-breakpoints)
11. [Deployment Notes](#11-deployment-notes)

---

## 1. Project Overview

A static HTML/CSS/JS personal marketing portfolio for **Saran Kumar KC**, a Digital Marketing professional. The site showcases three main areas of work — Content Creation, SEO & Copywriting, and Social Media Management — with dedicated case study pages for each.

- **Stack:** Pure HTML5, embedded CSS, vanilla JavaScript
- **Fonts:** Google Fonts (loaded via CDN)
- **No build step required** — open `index.html` directly in a browser
- **Deployment:** Netlify-compatible (all styles embedded in each file for full portability)

---

## 2. File Structure

```
Saran Port/
├── index.html              # Main portfolio homepage (single-page)
├── content-creation.html   # Case study: Content Creation at HighBizz
├── seo.html                # Case study: SEO & Copywriting at HighBizz
├── social-media.html       # Case study: Social Media Management at HighBizz
├── desc.md                 # Personal description / notes (not linked publicly)
└── README.md               # This documentation file
```

> **Note:** All CSS is embedded inside a `<style>` block within each HTML file. There is no external stylesheet. This was a deliberate choice for Netlify compatibility — each page is fully self-contained.

---

## 3. Page Descriptions & Routing

### Navigation Flow

```
index.html
├── #hero         → Landing section
├── #about        → About Me
├── #my-work      → Work navigation cards (links to case study pages)
│   ├── content-creation.html  → "← Back" returns to index.html#my-work
│   ├── seo.html               → "← Back" returns to index.html#my-work
│   └── social-media.html      → "← Back" returns to index.html#my-work
├── #skills       → Tools & Certifications
├── #education    → Education timeline
├── #awards       → Achievements & Awards
└── #contact      → Contact info & footer
```

### Page-by-Page Summary

| File | Title | Background | Purpose |
|---|---|---|---|
| `index.html` | Saran Kumar KC — Marketing Portfolio | Multi-section (dark/light alternating) | Full portfolio homepage |
| `content-creation.html` | Content Creation — Saran Kumar KC | `var(--ink)` — pure dark `#0d0d0d` | Content Creation case study |
| `seo.html` | SEO & Copywriting — Saran Kumar KC | `var(--ink-mid)` — dark `#1a1a1a` | SEO case study |
| `social-media.html` | Social Media — Saran Kumar KC | `var(--ink)` — pure dark `#0d0d0d` | Social Media case study |

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
| **Instrument Serif** | Decorative subtitles, pull quotes |
| **Syne** | Body text, nav links, labels, buttons |

### Color Usage Guide

| Context | Color |
|---|---|
| Dark section background | `var(--ink)` or `var(--ink-mid)` |
| Primary CTA / arrows / accents | `var(--accent)` — `#d4531a` |
| Text on dark bg | `var(--off-white)` or `rgba(244,240,232,0.75)` |
| Muted text on dark bg | `rgba(244, 240, 232, 0.55)` |

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

**Desktop:** Logo + nav links visible.

**Mobile (≤860px):** Nav links hidden. A 3-line **hamburger button** (`.hamburger`) appears. Clicking it opens a **full-screen dark overlay** (`.mobile-menu`) with large Bebas Neue links.

Mobile menu on case study pages includes:
- **Portfolio** → `index.html`
- **About / Work / Skills / Contact** → `index.html#{section}`

Hamburger animation: spans rotate and fade into an ✕ on open. Body scroll is locked while open.

---

### Buttons

#### Back Button (case study pages)
```html
<a href="index.html#my-work" class="back-btn">← Back</a>
```
- Text: **"← Back"**
- Target: `index.html#my-work` (lands on the Work section, not the top of the page)
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
| `content-creation.html` | View Content Portfolio ↗ | `roan-draw-2ee.notion.site/Content-Creation-s-2de6aa05a7c381b68f78e87390e5f15a` |
| `seo.html` | View SEO Portfolio ↗ | `roan-draw-2ee.notion.site/SEO-2de6aa05a7c3812f93cec3d2170df187` |
| `social-media.html` | View Social Media Portfolio ↗ | `roan-draw-2ee.notion.site/Social-Media-creative-s-2de6aa05a7c3813a82aff9b9afd1fb29` |

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

Used on case study pages for key findings:

```css
.card { background: rgba(244,240,232,0.06); border-radius: 10px; padding: 24px 28px; }
```

On case study pages, cards **fade up and stagger in** as they enter the viewport.

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
  background: linear-gradient(135deg, var(--accent) 0%, #b8440f 100%);
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
| **Scroll progress bar** (`#scroll-prog`) | Scroll | Glowing orange shimmer bar fills across the top of the page as user scrolls. Uses `documentElement.scrollHeight` for accuracy. `z-index: 99999` |
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

### Case Study Page Animations

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

## 7. Page-Specific Styles

### index.html — Sections

| Section ID | Background | Key Elements |
|---|---|---|
| `#hero` | `var(--ink)` | Animated stripe + breathing glow, scramble title, typewriter subtitle, magnetic CTA |
| `#about` | `var(--ink-mid)` | 2-col grid (text + info cards) |
| `#my-work` | `var(--off-white)` | Staggered work-card nav links |
| `#skills` | `var(--ink)` | Tag cloud (stagger on scroll) + cert list (stagger on scroll) |
| `#education` | `var(--off-white)` | Vertical timeline with scroll-reveal |
| `#awards` | `var(--accent2)` | Staggered award list |
| `#contact` | `var(--ink)` | Magnetic contact pills |

### Content Areas (About Section)

- **Role card:** Digital Marketing Manager · HighBizz
- **About text:** "Graduated with my **MBA in Marketing** from Alliance Ascent College, Bengaluru — currently working at HighBizz managing multi-client digital campaigns..."

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

---

## 9. External Links & Integrations

| Service | URL | Used in |
|---|---|---|
| Google Fonts | `fonts.googleapis.com` | All pages |
| Notion (Content Creation) | `roan-draw-2ee.notion.site/Content-Creation-s-2de6aa05a7c381b68f78e87390e5f15a` | `content-creation.html` |
| Notion (SEO) | `roan-draw-2ee.notion.site/SEO-2de6aa05a7c3812f93cec3d2170df187` | `seo.html` |
| Notion (Social Media) | `roan-draw-2ee.notion.site/Social-Media-creative-s-2de6aa05a7c3813a82aff9b9afd1fb29` | `social-media.html` |
| LinkedIn | `linkedin.com/in/saran-kumar-kc` | `index.html` contact section |
| Email (mailto) | `kcsaran2001@gmail.com` | `index.html` contact section |
| Phone (tel) | `+91 63799 70050` | `index.html` contact section |

---

## 10. Responsive Breakpoints

```
≤860px  — Tablet/mobile: hamburger menu, stacked grids, reduced section padding (80px 5vw)
≤480px  — Small phone: tighter font sizes, stacked contact pills, single-column metrics,
           reduced notion button padding, smaller back button
```

### Key changes at ≤860px (all pages)
- Nav links hidden → hamburger shown
- Section padding: `100px 10vw` → `80px 5vw`
- About, skills, two-col grids: collapse to single column
- Work cards: 2-per-row on tablet
- Data table: horizontal scroll enabled

### Key changes at ≤480px
- Hero title: `clamp(3.5rem, 18vw, 16rem)` (min reduced so it scales correctly)
- Footer heading: `clamp(2rem, 14vw, 7rem)`
- Contact pills: stack vertically, full-width
- Work cards: full-width single column
- Notion button: reduced padding, text allowed to wrap

---

## 11. Deployment Notes

- **No build process.** All files are plain HTML with embedded CSS and JS.
- **Netlify:** Drag the `Saran Port/` folder into Netlify Drop, or connect via Git. Entry point is `index.html`.
- **All styles are embedded** inside each HTML file — no broken CSS links on deployment.
- **All pages linked relatively** (e.g., `href="content-creation.html"`) — keep all `.html` files in the same directory.
- **Google Fonts require internet.** The site uses system fallback fonts (`sans-serif`) if offline.
