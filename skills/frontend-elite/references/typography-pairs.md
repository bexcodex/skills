# Typography Pairs — 12 Curated Combinations

> All fonts selected for being distinctive, character-rich, and non-generic.
> Every pairing includes context, Google Fonts URL, Next.js code, and full CSS.

---

## BANNED FONTS (Never Use as Primary)

| Font | Why Banned |
|------|-----------|
| **Inter** | Overused as default; anonymous; reads as "unstyled" |
| **Roboto** | Android system font; no character; reads as Google's default |
| **Space Grotesk** | The AI-slop font of 2022–2024; immediately recognizable |
| **Poppins** | 2019–2021 Canva aesthetic; overused in amateur projects |
| **Montserrat** | Peak saturation around 2018; no personality remaining |
| **Nunito Sans** | Weak weight contrast; forgettable in context |
| **Open Sans** | Designed to be invisible; achieves it too well |
| **Source Sans Pro** | The "I didn't choose a font" font |
| **Raleway** | Decorative but overplayed; reads as 2016 startup |
| **Quicksand** | Rounds too much; reads as children's app |

---

## THREE-FONT SYSTEM (Recommended)

For most projects, define three font roles — this is more nuanced than a two-font system:

```css
:root {
  --font-display: /* Heading/hero — character and expression */
  --font-body:    /* Long-form reading — warmth and legibility */
  --font-ui:      /* Labels, buttons, nav — neutral and clear */
  --font-mono:    /* Code, data, technical — only if needed */
}
```

Applying the three-font system:
- `--font-display` → h1, h2, h3, pull quotes, big stats
- `--font-body` → p, article text, long descriptions
- `--font-ui` → buttons, inputs, labels, nav, badges, captions
- `--font-mono` → code blocks, data tables, terminal output

---

## PAIRING 1 — Luxury Magazine
**Context:** Fashion, luxury e-commerce, high-end portfolios, hospitality, real estate

| Role | Font | Character |
|------|------|-----------|
| Display | **Cormorant Garamond** | Old-style serif, extreme contrast, refined |
| Body | **Crimson Pro** | Readable text serif, warm, literary |
| UI | **DM Sans** | Clean sans, neutral, unobtrusive |

```html
<link href="https://fonts.googleapis.com/css2?
  family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;0,700;1,300;1,400;1,600&
  family=Crimson+Pro:ital,wght@0,300;0,400;0,600;1,300;1,400&
  family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500&
  display=swap" rel="stylesheet">
```

```ts
// Next.js
import { Cormorant_Garamond, Crimson_Pro, DM_Sans } from 'next/font/google'
const display = Cormorant_Garamond({ subsets: ['latin'], weight: ['300','400','600','700'], style: ['normal','italic'], variable: '--font-display' })
const body    = Crimson_Pro({ subsets: ['latin'], weight: ['300','400','600'], style: ['normal','italic'], variable: '--font-body' })
const ui      = DM_Sans({ subsets: ['latin'], weight: ['300','400','500'], variable: '--font-ui' })
```

```css
:root {
  --font-display: 'Cormorant Garamond', Georgia, serif;
  --font-body:    'Crimson Pro', Georgia, serif;
  --font-ui:      'DM Sans', system-ui, sans-serif;
}

h1 {
  font-family: var(--font-display);
  font-weight: 300;   /* Cormorant is beautiful at light weight large */
  font-size: clamp(3rem, 8vw, 9rem);
  line-height: 1.0;
  letter-spacing: -0.02em;
}

h2 {
  font-family: var(--font-display);
  font-style: italic;  /* The italic on Cormorant is exquisite */
  font-weight: 400;
  font-size: clamp(1.75rem, 4vw, 3.5rem);
  line-height: 1.2;
}

p {
  font-family: var(--font-body);
  font-weight: 400;
  font-size: clamp(1.0625rem, 1.3vw, 1.25rem);
  line-height: 1.85;
}

button, input, label, nav {
  font-family: var(--font-ui);
}

.eyebrow {
  font-family: var(--font-ui);
  font-size: clamp(0.6875rem, 0.9vw, 0.75rem);
  font-weight: 500;
  letter-spacing: 0.15em;
  text-transform: uppercase;
}
```

**Dos:** Use Cormorant at 80–140px for hero headlines. Lean into the italic heavily.
**Don'ts:** Never use Cormorant below 18px. Don't bold Cormorant at body sizes.

---

## PAIRING 2 — Editorial & Journalistic
**Context:** Blogs, news, magazines, publishing platforms, long-form content

| Role | Font | Character |
|------|------|-----------|
| Display | **Playfair Display** | High-contrast transitional serif, classic editorial |
| Body | **Lora** | Calligraphic serif, warm, excellent for long reading |
| UI | **Karla** | Humanist sans, clean, slightly informal |

```html
<link href="https://fonts.googleapis.com/css2?
  family=Playfair+Display:ital,wght@0,400;0,600;0,700;0,800;1,400;1,700&
  family=Lora:ital,wght@0,400;0,500;0,600;1,400;1,500&
  family=Karla:ital,wght@0,300;0,400;0,500;0,600;1,400&
  display=swap" rel="stylesheet">
```

```ts
import { Playfair_Display, Lora, Karla } from 'next/font/google'
const display = Playfair_Display({ subsets: ['latin'], weight: ['400','600','700','800'], style: ['normal','italic'], variable: '--font-display' })
const body    = Lora({ subsets: ['latin'], weight: ['400','500','600'], style: ['normal','italic'], variable: '--font-body' })
const ui      = Karla({ subsets: ['latin'], weight: ['300','400','500','600'], variable: '--font-ui' })
```

```css
:root {
  --font-display: 'Playfair Display', Georgia, serif;
  --font-body:    'Lora', Georgia, serif;
  --font-ui:      'Karla', system-ui, sans-serif;
}

h1 {
  font-family: var(--font-display);
  font-weight: 700;
  font-size: clamp(2.25rem, 5.5vw, 5.5rem);
  line-height: 1.1;
  letter-spacing: -0.02em;
}

/* Playfair italic for subheadings */
h2 { font-family: var(--font-display); font-style: italic; font-weight: 400; }

/* Lora for article body — excellent reading experience */
.article p {
  font-family: var(--font-body);
  font-size: clamp(1.0625rem, 1.2vw, 1.1875rem);
  line-height: 1.9;
  max-width: 62ch;
}

/* Pull quote */
.pullquote {
  font-family: var(--font-display);
  font-style: italic;
  font-size: clamp(1.375rem, 2.5vw, 2.25rem);
  line-height: 1.4;
  border-left: 3px solid var(--color-accent);
  padding-left: clamp(1rem, 3vw, 2rem);
}
```

---

## PAIRING 3 — Industrial & Bold
**Context:** Agencies, streetwear, sports, music, construction, bold personal brands

| Role | Font | Character |
|------|------|-----------|
| Display | **Bebas Neue** | Condensed all-caps, poster impact |
| Body | **Barlow** | Broad grotesque family, industrial |
| UI | **Barlow Condensed** | Same family condensed — unified system |

```html
<link href="https://fonts.googleapis.com/css2?
  family=Bebas+Neue&
  family=Barlow:ital,wght@0,300;0,400;0,500;0,600;1,400&
  family=Barlow+Condensed:wght@400;500;600;700&
  display=swap" rel="stylesheet">
```

```ts
import { Bebas_Neue, Barlow, Barlow_Condensed } from 'next/font/google'
const display = Bebas_Neue({ subsets: ['latin'], weight: '400', variable: '--font-display' })
const body    = Barlow({ subsets: ['latin'], weight: ['300','400','500','600'], variable: '--font-body' })
const ui      = Barlow_Condensed({ subsets: ['latin'], weight: ['400','500','600','700'], variable: '--font-ui' })
```

```css
:root {
  --font-display: 'Bebas Neue', 'Arial Narrow', Arial, sans-serif;
  --font-body:    'Barlow', system-ui, sans-serif;
  --font-ui:      'Barlow Condensed', 'Arial Narrow', sans-serif;
}

/* Bebas at extreme scale */
h1 {
  font-family: var(--font-display);
  font-size: clamp(4rem, 12vw, 16rem);
  line-height: 0.9;
  letter-spacing: 0.02em;
  text-transform: uppercase;
}

/* Background ghost text — signature industrial move */
.ghost-text {
  font-family: var(--font-display);
  font-size: clamp(8rem, 28vw, 40rem);
  line-height: 1;
  opacity: 0.04;
  pointer-events: none;
  user-select: none;
  position: absolute;
  white-space: nowrap;
}

/* Stats */
.stat { font-family: var(--font-display); font-size: clamp(3rem, 7vw, 7rem); }
.stat-label { font-family: var(--font-ui); font-size: clamp(0.75rem, 1vw, 0.875rem); letter-spacing: 0.1em; text-transform: uppercase; }
```

---

## PAIRING 4 — Futuristic / Technical
**Context:** AI products, fintech, SaaS developer tools, data platforms, cybersecurity

| Role | Font | Character |
|------|------|-----------|
| Display | **Syne** | Geometric, slightly alien, memorable letterforms |
| Body | **IBM Plex Sans** | Technical clarity, made by IBM for software contexts |
| Mono | **IBM Plex Mono** | Same family, perfect for data/code contexts |

```html
<link href="https://fonts.googleapis.com/css2?
  family=Syne:wght@400;500;600;700;800&
  family=IBM+Plex+Sans:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&
  family=IBM+Plex+Mono:wght@300;400;500&
  display=swap" rel="stylesheet">
```

```ts
import { Syne, IBM_Plex_Sans, IBM_Plex_Mono } from 'next/font/google'
const display = Syne({ subsets: ['latin'], weight: ['400','600','700','800'], variable: '--font-display' })
const body    = IBM_Plex_Sans({ subsets: ['latin'], weight: ['300','400','500','600'], variable: '--font-body' })
const mono    = IBM_Plex_Mono({ subsets: ['latin'], weight: ['300','400','500'], variable: '--font-mono' })
```

```css
:root {
  --font-display: 'Syne', sans-serif;
  --font-body:    'IBM Plex Sans', system-ui, sans-serif;
  --font-ui:      'IBM Plex Sans', system-ui, sans-serif;
  --font-mono:    'IBM Plex Mono', 'Fira Code', monospace;
}

h1 {
  font-family: var(--font-display);
  font-weight: 800;
  font-size: clamp(2.75rem, 7vw, 8rem);
  line-height: 0.95;
  letter-spacing: -0.04em;
}

/* Syne works as an all-caps label too */
.tech-label {
  font-family: var(--font-display);
  font-weight: 600;
  font-size: 0.7rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
}

pre, code, .data-table {
  font-family: var(--font-mono);
  font-size: clamp(0.8125rem, 1vw, 0.9375rem);
}
```

---

## PAIRING 5 — Organic & Natural
**Context:** Wellness, food, skincare, sustainability, lifestyle, local businesses

| Role | Font | Character |
|------|------|-----------|
| Display | **Fraunces** | Variable optical-size, wonky and warm, unlike anything else |
| Body | **Lora** | Calligraphic serif, warm, inviting |
| UI | **DM Sans** | Clean, neutral, friendly |

```html
<link href="https://fonts.googleapis.com/css2?
  family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,400;0,9..144,600;0,9..144,700;1,9..144,400;1,9..144,600&
  family=Lora:ital,wght@0,400;0,500;1,400&
  family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500&
  display=swap" rel="stylesheet">
```

```css
:root {
  --font-display: 'Fraunces', Georgia, serif;
  --font-body:    'Lora', Georgia, serif;
  --font-ui:      'DM Sans', system-ui, sans-serif;
}

h1 {
  font-family: var(--font-display);
  font-optical-sizing: auto;  /* Critical for Fraunces */
  font-weight: 600;
  font-size: clamp(2.5rem, 6vw, 6.5rem);
  line-height: 1.1;
}

/* Fraunces italic is exceptional */
.highlight { font-family: var(--font-display); font-style: italic; font-weight: 300; }
```

---

## PAIRING 6 — Data Dashboard
**Context:** Analytics, admin panels, SaaS dashboards, financial tools, monitoring

| Role | Font | Character |
|------|------|-----------|
| Display | **Epilogue** | Variable, slightly mechanical, dashboard-appropriate |
| Body/UI | **IBM Plex Sans** | Technical, readable at small sizes, tabular numerals |
| Mono | **JetBrains Mono** | Best coding/data font, high x-height, ligatures |

```html
<link href="https://fonts.googleapis.com/css2?
  family=Epilogue:ital,wght@0,400;0,500;0,600;0,700;0,800;1,400&
  family=IBM+Plex+Sans:wght@300;400;500;600&
  family=JetBrains+Mono:ital,wght@0,300;0,400;0,500;0,700;1,400&
  display=swap" rel="stylesheet">
```

```css
:root {
  --font-display: 'Epilogue', system-ui, sans-serif;
  --font-body:    'IBM Plex Sans', system-ui, sans-serif;
  --font-ui:      'IBM Plex Sans', system-ui, sans-serif;
  --font-mono:    'JetBrains Mono', 'Fira Code', monospace;
}

/* Tabular numerals — critical for data tables */
.data-value, .metric, table {
  font-family: var(--font-mono);
  font-feature-settings: "tnum" 1;  /* tabular number alignment */
  font-variant-numeric: tabular-nums;
}

/* Compact label system for dense dashboards */
.dash-label {
  font-family: var(--font-ui);
  font-size: 0.6875rem;
  font-weight: 500;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  color: var(--color-text-muted);
}

.metric-value {
  font-family: var(--font-display);
  font-weight: 700;
  font-size: clamp(1.5rem, 2.5vw, 2.5rem);
  font-feature-settings: "tnum" 1;
}
```

---

## PAIRING 7 — Playful Consumer
**Context:** Consumer apps, food delivery, social, games, onboarding flows, Gen Z products

| Role | Font | Character |
|------|------|-----------|
| Display | **Syne Mono** or **Boogaloo** | Expressive and fun |
| Body | **Plus Jakarta Sans** | Rounded, modern, approachable |
| UI | **Plus Jakarta Sans** | Same family for consistency |

*Alternative display options for playful: `Pacifico`, `Righteous`, `Fredoka`, `Baloo 2`*

```html
<link href="https://fonts.googleapis.com/css2?
  family=Boogaloo&
  family=Plus+Jakarta+Sans:ital,wght@0,300;0,400;0,500;0,600;0,700;1,400&
  display=swap" rel="stylesheet">
```

```css
:root {
  --font-display: 'Boogaloo', cursive;
  --font-body:    'Plus Jakarta Sans', system-ui, sans-serif;
  --font-ui:      'Plus Jakarta Sans', system-ui, sans-serif;
}

h1 {
  font-family: var(--font-display);
  font-size: clamp(2.5rem, 7vw, 7rem);
  line-height: 1.1;
  letter-spacing: -0.01em;
}

/* Big friendly numbers */
.big-number {
  font-family: var(--font-display);
  font-size: clamp(3rem, 9vw, 9rem);
  line-height: 1;
}
```

---

## PAIRING 8 — Brutalist
**Context:** Design agencies, art, experimental, anti-template projects

| Role | Font | Character |
|------|------|-----------|
| Display | **Anton** | Ultra-bold condensed, aggressive, unambiguous |
| Body | **Barlow** | Clean and readable |
| Mono | **Space Mono** | Retro-futuristic, fits the brutalist rawness |

```html
<link href="https://fonts.googleapis.com/css2?
  family=Anton&
  family=Barlow:ital,wght@0,300;0,400;0,600;1,400&
  family=Space+Mono:ital,wght@0,400;0,700;1,400&
  display=swap" rel="stylesheet">
```

```css
:root {
  --font-display: 'Anton', 'Impact', sans-serif;
  --font-body:    'Barlow', system-ui, sans-serif;
  --font-mono:    'Space Mono', monospace;
}

h1 {
  font-family: var(--font-display);
  font-size: clamp(4rem, 14vw, 18rem);
  line-height: 0.85;
  letter-spacing: -0.01em;
  text-transform: uppercase;
}

/* Brutalism: use large, simple, black borders */
.card {
  border: 2px solid black;
  border-radius: 0;
}
```

---

## PAIRING 9 — Retro / Nostalgic
**Context:** Indie games, podcasts, vintage brands, zines, craft products

| Role | Font | Character |
|------|------|-----------|
| Display | **Abril Fatface** | Extreme contrast ink display, Victorian poster energy |
| Body | **Spectral** | Screen-optimized literary serif, slightly old-fashioned |
| Mono | **VT323** | Pixel/terminal retro, use for accents only |

```html
<link href="https://fonts.googleapis.com/css2?
  family=Abril+Fatface&
  family=Spectral:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&
  family=VT323&
  display=swap" rel="stylesheet">
```

```css
:root {
  --font-display: 'Abril Fatface', Georgia, serif;
  --font-body:    'Spectral', Georgia, serif;
  --font-mono:    'VT323', monospace;
}

h1 {
  font-family: var(--font-display);
  font-size: clamp(3rem, 8vw, 9rem);
  line-height: 1.0;
  /* Single weight only — use size for hierarchy */
}

/* VT323 for labels / accents — not body text */
.retro-label {
  font-family: var(--font-mono);
  font-size: clamp(1rem, 1.5vw, 1.25rem);
  letter-spacing: 0.05em;
}
```

---

## PAIRING 10 — Zen & Minimal
**Context:** Writing tools, note apps, meditation, focus products, quiet luxury

| Role | Font | Character |
|------|------|-----------|
| Display | **Libre Baskerville** | Sturdy American serif, confident and timeless |
| Body | **Libre Baskerville** | Same family — fully serif for a literary feel |
| UI | **Karla** | Minimal without being cold |

```html
<link href="https://fonts.googleapis.com/css2?
  family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&
  family=Karla:ital,wght@0,300;0,400;0,500;0,600;1,400&
  display=swap" rel="stylesheet">
```

```css
:root {
  --font-display: 'Libre Baskerville', Georgia, serif;
  --font-body:    'Libre Baskerville', Georgia, serif;
  --font-ui:      'Karla', system-ui, sans-serif;
}

h1 {
  font-family: var(--font-display);
  font-weight: 700;
  font-size: clamp(2rem, 5vw, 5.5rem);
  line-height: 1.15;
  letter-spacing: -0.02em;
}

/* Italic for second heading level — creates contrast without extra font */
h2 { font-family: var(--font-display); font-style: italic; font-weight: 400; }

p {
  font-family: var(--font-body);
  font-weight: 400;
  font-size: clamp(1.0625rem, 1.2vw, 1.1875rem);
  line-height: 1.9;
}
```

---

## PAIRING 11 — Modern Grotesque
**Context:** B2B SaaS, startup, professional portfolio, modern agencies

| Role | Font | Character |
|------|------|-----------|
| Display | **Cabinet Grotesk** | Organic grotesque, editorial but approachable — NOT another geometric sans |
| Body | **General Sans** | Contemporary grotesque with optical corrections |
| Mono | **Fira Code** | Readable code font with elegant ligatures |

*These are hosted on Fontshare (free) — different URL:*

```html
<!-- Fontshare — free, high quality, not on Google Fonts -->
<link href="https://api.fontshare.com/v2/css?
  f[]=cabinet-grotesk@400,500,600,700,800,900&
  f[]=general-sans@300,400,500,600&
  display=swap" rel="stylesheet">

<!-- Fira Code from Google Fonts for mono -->
<link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@300;400;500&display=swap" rel="stylesheet">
```

```css
:root {
  --font-display: 'Cabinet Grotesk', system-ui, sans-serif;
  --font-body:    'General Sans', system-ui, sans-serif;
  --font-ui:      'General Sans', system-ui, sans-serif;
  --font-mono:    'Fira Code', monospace;
}

h1 {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: clamp(2.75rem, 7vw, 8rem);
  line-height: 0.95;
  letter-spacing: -0.04em;
}

/* Cabinet Grotesk at regular weight for a softer subheading */
h3 {
  font-family: var(--font-display);
  font-weight: 500;
  letter-spacing: -0.01em;
}
```

---

## PAIRING 12 — Variable Font (Single Family)
**Context:** When performance matters or you want perfect type harmony

| Role | Font | Character |
|------|------|-----------|
| All roles | **Instrument Serif** + **Instrument Sans** | Elegant, literary, both from same type family |

*Or use `Fraunces` (variable) alone — it supports optical size and wonky axes*

```html
<link href="https://fonts.googleapis.com/css2?
  family=Instrument+Serif:ital@0;1&
  family=Instrument+Sans:ital,wght@0,400;0,500;0,600;1,400&
  display=swap" rel="stylesheet">
```

```css
:root {
  --font-display: 'Instrument Serif', Georgia, serif;
  --font-body:    'Instrument Serif', Georgia, serif;
  --font-ui:      'Instrument Sans', system-ui, sans-serif;
}

h1 { font-family: var(--font-display); font-size: clamp(3rem, 7vw, 8rem); }
h2 { font-family: var(--font-display); font-style: italic; }
p  { font-family: var(--font-body); line-height: 1.85; }
button, input, nav { font-family: var(--font-ui); }
```

---

## RESPONSIVE TYPE SCALE (Universal)

```css
:root {
  /* Fully fluid — single scale for all devices, no breakpoints needed */
  --text-2xs:  clamp(0.625rem,  0.58rem + 0.22vw,  0.75rem);    /* 10–12px */
  --text-xs:   clamp(0.75rem,   0.70rem + 0.25vw,  0.875rem);   /* 12–14px */
  --text-sm:   clamp(0.875rem,  0.82rem + 0.28vw,  1rem);        /* 14–16px */
  --text-base: clamp(1rem,      0.95rem + 0.25vw,  1.125rem);    /* 16–18px */
  --text-md:   clamp(1.125rem,  1.0rem  + 0.63vw,  1.375rem);   /* 18–22px */
  --text-lg:   clamp(1.25rem,   1.05rem + 1.0vw,   1.625rem);   /* 20–26px */
  --text-xl:   clamp(1.5rem,    1.1rem  + 2.0vw,   2.25rem);    /* 24–36px */
  --text-2xl:  clamp(1.875rem,  1.2rem  + 3.4vw,   3.25rem);    /* 30–52px */
  --text-3xl:  clamp(2.5rem,    1.4rem  + 5.5vw,   5rem);       /* 40–80px */
  --text-4xl:  clamp(3rem,      1.2rem  + 9vw,     7.5rem);     /* 48–120px */
  --text-hero: clamp(3.5rem,    1rem    + 12.5vw,  10rem);      /* 56–160px */
}
```

## CRITICAL MOBILE TYPOGRAPHY RULES

```css
/* 1. Prevent iOS automatic zoom on input focus */
input, select, textarea {
  font-size: max(1rem, 16px);  /* Never below 16px */
}

/* 2. Fluid headings — tighter tracking on small screens */
@media (max-width: 639px) {
  h1 { letter-spacing: -0.02em; }  /* Less tight than desktop */
  p  { max-width: 100%; }           /* No measure constraint on mobile */
}

/* 3. Better paragraph reading on mobile */
p {
  text-wrap: pretty;    /* prevents widows/orphans */
  overflow-wrap: break-word;
  word-break: break-word;
}

/* 4. Balanced headlines on all screen sizes */
h1, h2, h3 {
  text-wrap: balance;
}

/* 5. Base font rendering */
html {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-rendering: optimizeLegibility;
  font-feature-settings: "kern" 1, "liga" 1;
}
```

## LEADING (LINE HEIGHT) GUIDE

| Element | Mobile | Tablet | Desktop | Token |
|---------|--------|--------|---------|-------|
| Hero h1 | 1.0 | 1.0 | 0.95 | `--leading-tightest` |
| H1 | 1.1 | 1.1 | 1.05 | `--leading-tight` |
| H2–H3 | 1.2 | 1.15 | 1.15 | `--leading-snug` |
| Short body | 1.6 | 1.65 | 1.65 | `--leading-normal` |
| Long-form body | 1.75 | 1.80 | 1.85 | `--leading-relaxed` |
| Article text | 1.85 | 1.9 | 1.95 | `--leading-loose` |

## LETTER SPACING GUIDE

| Element | Tracking | Note |
|---------|---------|------|
| Hero display (80px+) | `-0.04em` to `-0.05em` | Very tight — fills optical gaps at large scale |
| Large heading (40–80px) | `-0.02em` to `-0.03em` | Tight |
| Medium heading (24–40px) | `-0.01em` to `-0.02em` | Slightly tight |
| Body text | `0` | Never touch body tracking |
| UI labels | `0` to `0.01em` | Neutral |
| All-caps labels | `0.08em` to `0.15em` | Needs extra space to breathe |
| Small all-caps (under 12px) | `0.1em` to `0.2em` | Even more space |
