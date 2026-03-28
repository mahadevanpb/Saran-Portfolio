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
   - [Navigation Bar](#navigation-bar)
   - [Buttons](#buttons)
   - [Typography Classes](#typography-classes)
   - [Cards](#cards)
   - [Lists](#lists)
   - [Metrics Grid](#metrics-grid)
   - [Data Table](#data-table)
   - [Notion Button](#notion-button)
6. [Page-Specific Styles](#6-page-specific-styles)
   - [index.html — Sections](#indexhtml--sections)
   - [content-creation.html](#content-creationhtml)
   - [seo.html](#seohtml)
   - [social-media.html](#social-mediahtml)
7. [JavaScript Behaviour](#7-javascript-behaviour)
8. [External Links & Integrations](#8-external-links--integrations)
9. [Responsive Breakpoints](#9-responsive-breakpoints)
10. [Deployment Notes](#10-deployment-notes)

---

## 1. Project Overview

A static HTML/CSS/JS personal marketing portfolio for **Saran Kumar KC**, a Digital Marketing professional and MBA student. The site showcases three main areas of work — Content Creation, SEO & Copywriting, and Social Media Management — with dedicated case study pages for each.

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
│   ├── content-creation.html
│   ├── seo.html
│   └── social-media.html
├── #skills       → Tools & Certifications
├── #education    → Education timeline
├── #awards       → Achievements & Awards
└── #contact      → Contact info & footer

content-creation.html  → "← Back to Portfolio" links back to index.html
seo.html               → "← Back to Portfolio" links back to index.html
social-media.html      → "← Back to Portfolio" links back to index.html
```

### Page-by-Page Summary

| File | Title | Background | Purpose |
|---|---|---|---|
| `index.html` | Saran Kumar KC — Marketing Portfolio | Multi-section (dark/light alternating) | Full portfolio homepage |
| `content-creation.html` | Content Creation — Saran Kumar KC | `var(--ink)` — pure dark `#0d0d0d` | Content Creation case study |
| `seo.html` | SEO & Copywriting — Saran Kumar KC | `var(--ink-mid)` — dark `#1a1a1a` | SEO case study |
| `social-media.html` | Social Media — Saran Kumar KC | `var(--ink)` — pure dark `#0d0d0d` | Social Media case study |

### Internal Anchor Links (index.html)

All nav links on the case study pages point back to sections of `index.html`:

```html
<a href="index.html#about">About</a>
<a href="index.html#my-work">Work</a>
<a href="index.html#skills">Skills</a>
<a href="index.html#contact">Contact</a>
```

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

  /* index.html only: */
  --stripe-a:          #0d0d0d;
  --stripe-b:          #1f1f1f;
  --text-on-dark:      #f4f0e8;
  --text-muted-dark:   rgba(244, 240, 232, 0.55);
  --text-muted-light:  rgba(13, 13, 13, 0.5);
}
```

### Typography

Three Google Fonts are loaded on every page:

```html
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Instrument+Serif:ital@0;1&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet">
```

| Font | Weights/Styles | Usage |
|---|---|---|
| **Bebas Neue** | Regular | Display headings, titles, hero text, nav logo |
| **Instrument Serif** | Regular, Italic | Decorative subtitles, pull quotes |
| **Syne** | 400, 600, 700, 800 | Body text, nav links, labels, buttons |

### Color Usage Guide

| Context | Color |
|---|---|
| Dark section background | `var(--ink)` or `var(--ink-mid)` |
| Light section background | `var(--off-white)` or `var(--warm-gray)` |
| Primary CTA / arrows / accents | `var(--accent)` — `#d4531a` |
| Section labels (default) | `var(--accent)` |
| Section labels (gold variant) | `var(--accent3)` — `#c9a84c` |
| Section labels (green variant) | `#4ade80` (used in Awards only) |
| Text on dark bg | `var(--off-white)` or `rgba(244,240,232,0.75)` |
| Muted text on dark bg | `rgba(244, 240, 232, 0.55)` |
| Text on light bg | `var(--ink)` |
| Muted text on light bg | `rgba(13, 13, 13, 0.68)` |

---

## 5. Shared CSS Components

The following components appear on all pages (index + case study pages).

### Custom Cursor

The site uses a custom two-element cursor replacing the default browser cursor (`cursor: none` on `body`).

```html
<div id="cur"></div>    <!-- Small filled dot -->
<div id="curl"></div>   <!-- Larger ring -->
```

```css
#cur {
  width: 10px; height: 10px;
  background: var(--accent);      /* Filled orange dot */
  border-radius: 50%;
  position: fixed; z-index: 9999;
  pointer-events: none;
  transition: transform 0.12s;
}
#curl {
  width: 32px; height: 32px;
  border: 1.5px solid var(--accent);  /* Orange ring outline */
  border-radius: 50%;
  position: fixed; z-index: 9998;
  opacity: 0.6;
  pointer-events: none;
}
```

Behaviour (via JS): Both elements follow the mouse. On `mousedown`, both scale to `0.8`. On hover over interactive elements (`a`, `button`, `.work-card` etc.), both scale to `1.5`.

---

### Navigation Bar

Fixed at the top of every page. Dark glassmorphism style.

```css
nav {
  position: fixed; top: 0; left: 0; right: 0; z-index: 200;
  display: flex; justify-content: space-between; align-items: center;
  padding: 18px 56px;
  background: rgba(13, 13, 13, 0.95);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid rgba(244, 240, 232, 0.07);
}
.nav-logo   { font-family: 'Bebas Neue'; font-size: 1.3rem; color: var(--off-white); }
.nav-links  { display: flex; gap: 36px; list-style: none; }
.nav-links a {
  font-size: 0.72rem; font-weight: 600; letter-spacing: 0.15em;
  text-transform: uppercase; color: rgba(244,240,232,0.55);
  transition: color 0.2s;
}
.nav-links a:hover { color: var(--accent); }
```

On mobile (≤860px): `nav-links` is hidden (`.nav-links { display: none }`). Nav padding reduces to `14px 20px`.

---

### Buttons

#### Back Button (case study pages)
```css
.back-btn {
  display: inline-flex; align-items: center; gap: 8px;
  padding: 12px 24px;
  background: rgba(244, 240, 232, 0.1);
  color: var(--off-white);
  border-radius: 6px;
  font-size: 0.78rem; font-weight: 600; letter-spacing: 0.1em;
  text-transform: uppercase; text-decoration: none;
  margin-bottom: 40px;
  transition: background 0.2s, transform 0.2s;
  border: 1px solid rgba(244, 240, 232, 0.2);
}
.back-btn:hover { background: rgba(244,240,232,0.2); transform: translateX(-4px); }
```

Usage: `<a href="index.html" class="back-btn">← Back to Portfolio</a>`

#### Notion Button (case study pages)
A large centered CTA linking to Notion portfolio pages.

```css
.notion-btn-wrap { margin-top: 56px; display: flex; justify-content: center; }
.notion-btn {
  display: inline-flex; align-items: center; gap: 14px;
  padding: 20px 44px;
  background: linear-gradient(135deg, var(--accent) 0%, #b8440f 100%);
  color: #fff; border-radius: 8px;
  font-size: 0.88rem; font-weight: 700; letter-spacing: 0.14em;
  text-transform: uppercase; text-decoration: none;
  transition: transform 0.22s, box-shadow 0.22s;
  box-shadow: 0 4px 28px rgba(212, 83, 26, 0.35);
}
.notion-btn:hover {
  transform: translateY(-4px) scale(1.03);
  box-shadow: 0 10px 40px rgba(212, 83, 26, 0.55);
}
```

Each case study page has one Notion button pointing to a specific Notion page:

| Page | Notion URL |
|---|---|
| `content-creation.html` | `https://www.notion.so/Content-Creation-s-7cba57b8526b834a947081c6a614487f` |
| `seo.html` | `https://www.notion.so/SEO-d3ba57b8526b83da9b368138652070f9` |
| `social-media.html` | `https://www.notion.so/Social-Media-creative-s-51ea57b8526b829b9547019765c0feb2` |

---

### Typography Classes

```css
/* Section eyebrow label */
.section-label {
  font-size: 0.68rem; font-weight: 700; letter-spacing: 0.28em;
  text-transform: uppercase; color: var(--accent); margin-bottom: 16px;
}
.section-label.gold  { color: var(--accent3); }   /* Gold variant */
.section-label.green { color: #4ade80; }           /* Green variant (Awards only) */

/* Large display heading */
.port-heading {
  font-family: 'Bebas Neue', sans-serif;
  font-size: clamp(3rem, 7vw, 5.5rem);
  line-height: 1; letter-spacing: 0.03em; margin-bottom: 12px;
}
.port-heading.light { color: var(--off-white); }   /* For use on dark backgrounds */
.port-heading.dark  { color: var(--ink); }          /* For use on light backgrounds */

/* Body intro paragraph */
.port-intro {
  font-size: 0.95rem; line-height: 1.8; font-weight: 400;
  margin-bottom: 48px; max-width: 580px;
}
.port-intro.light { color: rgba(244, 240, 232, 0.75); }
.port-intro.dark  { color: rgba(13, 13, 13, 0.68); }
```

---

### Cards

Used in case study pages for key findings / outcomes.

```css
.card {
  background: rgba(244, 240, 232, 0.06);
  border: 1px solid rgba(244, 240, 232, 0.12);
  border-radius: 10px; padding: 24px 28px;
  margin-bottom: 16px;
  transition: background 0.2s, transform 0.2s;
}
.card:hover { background: rgba(244, 240, 232, 0.1); transform: translateY(-3px); }
.card h4 { font-size: 0.9rem; font-weight: 700; color: var(--off-white); margin-bottom: 8px; }
.card p  { font-size: 0.86rem; color: rgba(244, 240, 232, 0.68); line-height: 1.65; }
.card .big-num { font-family: 'Bebas Neue'; font-size: 3rem; color: var(--accent); }
```

Also: `.card.on-light` variant for use on light backgrounds (used in `index.html`).

---

### Lists

Arrow-prefixed bullet lists. The `→` arrow is added automatically via CSS `::before`.

```css
.port-list { list-style: none; padding: 0; }
.port-list li {
  padding: 14px 0;
  border-bottom: 1px solid rgba(244, 240, 232, 0.1);
  font-size: 0.9rem; color: rgba(244, 240, 232, 0.78);
  line-height: 1.65; display: flex; gap: 12px;
}
.port-list li::before {
  content: '→'; color: var(--accent); font-weight: 700; flex-shrink: 0;
}
```

> **Important:** Do NOT manually add `→` arrows inside `<li>` tags — the CSS `::before` pseudo-element adds them automatically. Manually adding them will result in double arrows.

---

### Metrics Grid

Used in `content-creation.html` for key numbers.

```css
.metrics {
  display: grid; grid-template-columns: repeat(3, 1fr);
  gap: 16px; margin-bottom: 24px;
}
.metric {
  background: rgba(244, 240, 232, 0.05);
  border: 1px solid rgba(244, 240, 232, 0.1);
  border-radius: 8px; padding: 22px 14px; text-align: center;
}
.metric .num { font-family: 'Bebas Neue'; font-size: 2.2rem; color: var(--accent); }
.metric .lbl { font-size: 0.68rem; font-weight: 600; letter-spacing: 0.1em; text-transform: uppercase; color: rgba(244,240,232,0.55); }
```

On mobile: collapses to 2-column (`grid-template-columns: 1fr 1fr`).

---

### Data Table

Used in `social-media.html` for the metrics/results table.

```css
.data-table {
  width: 100%; border-collapse: collapse; margin: 30px 0;
  background: rgba(244, 240, 232, 0.04);
  border: 1px solid rgba(244, 240, 232, 0.1);
  border-radius: 10px; overflow: hidden;
}
.data-table th {
  text-align: left; padding: 14px 18px; font-size: 0.68rem;
  font-weight: 700; letter-spacing: 0.12em; text-transform: uppercase;
  color: var(--accent);
  border-bottom: 2px solid rgba(212, 83, 26, 0.6);
  background: rgba(212, 83, 26, 0.08);
}
.data-table td {
  padding: 14px 18px; font-size: 0.9rem;
  border-bottom: 1px solid rgba(244, 240, 232, 0.08);
  color: rgba(244, 240, 232, 0.82); line-height: 1.5;
}
.data-table td:first-child { font-weight: 600; color: var(--off-white); }
.data-table tr:hover td   { background: rgba(212, 83, 26, 0.08); }
```

---

## 6. Page-Specific Styles

### index.html — Sections

| Section ID | Background | Notes |
|---|---|---|
| `#hero` | `var(--ink)` | Animated stripe pattern + radial glow |
| (divider) | — | 8px accent stripe between hero and about |
| `#about` | `var(--ink-mid)` | 2-column grid (about text + info cards) |
| `#my-work` | `var(--off-white)` | Navigation cards linking to case studies |
| `#skills` | `var(--ink)` | Tools tags + Certifications list |
| `#education` | `var(--off-white)` | Vertical timeline |
| `#awards` | `var(--accent2)` | Dark forest green |
| `#contact` | `var(--ink)` | Centered, with contact pills |

#### Hero-Specific Classes (`index.html` only)

```css
.hero-stripes   /* Repeating dark stripe background pattern */
.hero-glow      /* Floating radial orange glow, animates with @keyframes floatGlow */
.hero-inner     /* Centered content wrapper */
.hero-eyebrow   /* Small uppercase label above title */
.hero-title     /* Giant "SARAN KC" display heading */
.hero-subtitle  /* Italic serif subtitle */
.hero-name      /* Gold uppercase name tag */
.hero-btn       /* Orange CTA button */
.scroll-indicator /* Animated scroll prompt at bottom of hero */
```

#### Scroll Animation System (`index.html` only)

Elements with these classes animate in when they enter the viewport (via `IntersectionObserver`):

```css
.reveal   /* Fades up from below */
.reveal-l /* Slides in from the left */
.reveal-r /* Slides in from the right */

/* When in viewport, JS adds .vis class: */
.reveal.vis, .reveal-l.vis, .reveal-r.vis { opacity: 1; transform: translate(0); }

/* Stagger delays */
.d1 { transition-delay: 0.1s; }
.d2 { transition-delay: 0.2s; }
/* ...up to .d5 */
```

#### Education Timeline (`index.html` only)

```css
.timeline       /* Relative position wrapper with left border line */
.t-item         /* Each entry — 2-col grid (year | content) */
.t-year         /* Bebas Neue year label in accent orange */
.t-body         /* Content — has orange dot via ::before */
```

Timeline items also animate in via `IntersectionObserver` (`.t-item` → `.t-item.vis`).

---

### content-creation.html

- **Background:** `var(--ink)` (`#0d0d0d`)
- **Case container padding:** `100px 10vw`
- **Sections:**
  - Title + intro paragraph
  - Arrow bullet list of responsibilities
  - Metrics grid (3 stats: Avg Reel Views, Top Reel, Paid Promotion)
  - Standout result card (`.card` with `.big-num`)
  - Notion button → Content Creation Notion page

---

### seo.html

- **Background:** `var(--ink-mid)` (`#1a1a1a`)
- **Case container padding:** `100px 10vw`
- **Sections:**
  - Title + intro paragraph
  - Arrow bullet list of responsibilities
  - "Clients Managed" card — client names at `1rem`, `color: var(--off-white)`
  - "Engagement Overview" card
  - "Key Outcomes" card — uses `.port-list` inside a `.card` (borders overridden inline)
  - Notion button → SEO Notion page

---

### social-media.html

- **Background:** `var(--ink)` (`#0d0d0d`)
- **Case container padding:** `100px 10vw`
- **Sections:**
  - Title + intro paragraph
  - Arrow bullet list of responsibilities
  - Data table (6 rows of metrics + results)
  - Notion button → Social Media Notion page

---

## 7. JavaScript Behaviour

All pages share the same JS patterns. The JS is embedded at the bottom of each `<body>`.

### Custom Cursor Tracking

```js
document.addEventListener('mousemove', (e) => {
  cursor.style.left = e.clientX + 'px';
  cursor.style.top  = e.clientY + 'px';
  cursorL.style.left = e.clientX - 11 + 'px';   // offset to center the 32px ring
  cursorL.style.top  = e.clientY - 11 + 'px';
});
```

### Cursor Scale on Click

```js
document.addEventListener('mousedown', () => { /* scale(0.8) */ });
document.addEventListener('mouseup',   () => { /* scale(1) */ });
```

### Cursor Scale on Hover (Interactive Elements)

```js
const interactiveElements = document.querySelectorAll('a, .work-card');
// (.work-card, .about-card, .tag, button added in index.html)
interactiveElements.forEach(el => {
  el.addEventListener('mouseenter', () => { /* scale(1.5) */ });
  el.addEventListener('mouseleave', () => { /* scale(1) */ });
});
```

### Scroll Reveal Animation (index.html only)

```js
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) entry.target.classList.add('vis');
  });
}, { threshold: 0.1, rootMargin: '0px 0px -50px 0px' });

document.querySelectorAll('.reveal, .reveal-l, .reveal-r, .t-item')
        .forEach(el => observer.observe(el));
```

---

## 8. External Links & Integrations

| Service | URL | Used in |
|---|---|---|
| Google Fonts | `fonts.googleapis.com` | All pages (Bebas Neue, Instrument Serif, Syne) |
| Notion (Content Creation) | `notion.so/Content-Creation-s-7cba57b8526b834a947081c6a614487f` | `content-creation.html` |
| Notion (SEO) | `notion.so/SEO-d3ba57b8526b83da9b368138652070f9` | `seo.html` |
| Notion (Social Media) | `notion.so/Social-Media-creative-s-51ea57b8526b829b9547019765c0feb2` | `social-media.html` |
| LinkedIn | `linkedin.com/in/saran-kumar-kc` | `index.html` contact section |
| Email (mailto) | `kcsaran2001@gmail.com` | `index.html` contact section |
| Phone (tel) | `+91 63799 70050` | `index.html` contact section |

---

## 9. Responsive Breakpoints

```css
/* Main breakpoint — affects all pages */
@media (max-width: 860px) {
  nav { padding: 14px 20px; }
  .nav-links { display: none; }           /* Hide nav links on mobile */
  .case-container { padding: 80px 5vw; }  /* Reduce padding on case pages */

  /* index.html specific: */
  #about, .two-col, .skills-grid { grid-template-columns: 1fr; gap: 40px; }
  .timeline::before { left: 60px; }
  .t-item { grid-template-columns: 60px 1fr; }
  .metrics { grid-template-columns: 1fr 1fr; }
  .work-card { min-width: 120px; }
  .work-top { flex-direction: column; align-items: flex-start; gap: 24px; }
}

/* Instagram/image grid — index.html only */
@media (max-width: 1200px) { .ig-grid { grid-template-columns: repeat(3, 1fr); } }
@media (max-width: 760px)  { .ig-grid { grid-template-columns: repeat(2, 1fr); } }
@media (max-width: 480px)  { .ig-grid { grid-template-columns: 1fr; } }
```

---

## 10. Deployment Notes

- **No build process needed.** All files are plain HTML with embedded CSS and JS.
- **Netlify:** Deploy by dragging the `Saran Port/` folder into Netlify Drop, or connect via Git. The entry point is `index.html`.
- **All styles are embedded** inside each HTML file to avoid any broken CSS link issues on deployment.
- **All pages are linked relatively** (e.g., `href="content-creation.html"`) — keep all `.html` files in the same directory.
- **Google Fonts require internet.** The site will use system fallback fonts (`sans-serif`) if offline.
