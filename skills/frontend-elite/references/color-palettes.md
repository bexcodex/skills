# Color Palettes — 15 Production-Ready Palettes

Each palette is a complete token system. Copy the `:root` block directly into your project.
All palettes include: background layers, surface layers, border hierarchy, text hierarchy,
accent with states, and semantic colors.

---

## HOW TO READ THESE PALETTES

```
--color-bg              ← Page/document background (darkest or lightest)
--color-bg-elevated     ← Background for modals, drawers, popovers
--color-surface-1       ← Primary cards, side panels, section backgrounds
--color-surface-2       ← Nested elements, inputs, tags
--color-surface-3       ← Hover states on surface elements
--color-border          ← Default borders and dividers
--color-border-strong   ← Active/emphasized borders
--color-border-subtle   ← Barely-visible separators
--color-text-primary    ← Headings, labels, important text
--color-text-secondary  ← Body copy, descriptions
--color-text-muted      ← Captions, placeholders, disabled
--color-text-inverse    ← Text on accent-colored surfaces
--color-accent          ← Primary brand/action color
--color-accent-hover    ← Accent on hover
--color-accent-active   ← Accent on press/active
--color-accent-subtle   ← Semi-transparent tinted backgrounds
```

---

## DARK THEMES

---

### 1. Obsidian Gold — `luxury-dark`

Premium, silent, expensive. Suited for: luxury brands, high-end SaaS, portfolio, fashion.

```css
:root {
  /* Surfaces */
  --color-bg:             #080808;
  --color-bg-elevated:    #0f0f0f;
  --color-surface-1:      #131313;
  --color-surface-2:      #1b1b1b;
  --color-surface-3:      #222222;

  /* Borders */
  --color-border:         #242424;
  --color-border-strong:  #333333;
  --color-border-subtle:  #1a1a1a;

  /* Text */
  --color-text-primary:   #f5ede0;
  --color-text-secondary: #9a8e82;
  --color-text-muted:     #5a5248;
  --color-text-inverse:   #080808;

  /* Accent — warm gold */
  --color-accent:         #c9a84c;
  --color-accent-hover:   #dfb95f;
  --color-accent-active:  #a88838;
  --color-accent-subtle:  rgba(201, 168, 76, 0.10);

  /* Semantic */
  --color-success:        #5a9e6f;
  --color-success-subtle: rgba(90, 158, 111, 0.12);
  --color-warning:        #d4914a;
  --color-warning-subtle: rgba(212, 145, 74, 0.12);
  --color-danger:         #c45252;
  --color-danger-subtle:  rgba(196, 82, 82, 0.12);
  --color-info:           #4a8ac4;
  --color-info-subtle:    rgba(74, 138, 196, 0.12);
}
```

**Font pairing:** Cormorant Garamond (display) + DM Sans (body)  
**Signature details:** Wide letter-spacing on labels, subtle gold glow on hover, thin `1px` borders

---

### 2. Carbon Ember — `industrial-raw`

Direct, functional, raw energy. Suited for: developer tools, CLI apps, security products, agency sites.

```css
:root {
  --color-bg:             #111110;
  --color-bg-elevated:    #161614;
  --color-surface-1:      #1c1c1a;
  --color-surface-2:      #252523;
  --color-surface-3:      #2e2e2b;

  --color-border:         #333330;
  --color-border-strong:  #444440;
  --color-border-subtle:  #1e1e1c;

  --color-text-primary:   #eeede8;
  --color-text-secondary: #8a8780;
  --color-text-muted:     #5a5850;
  --color-text-inverse:   #111110;

  /* Accent — burnt orange */
  --color-accent:         #e8622a;
  --color-accent-hover:   #f07840;
  --color-accent-active:  #c04e1e;
  --color-accent-subtle:  rgba(232, 98, 42, 0.12);

  --color-success:        #5a9e60;
  --color-success-subtle: rgba(90, 158, 96, 0.12);
  --color-warning:        #e8a030;
  --color-warning-subtle: rgba(232, 160, 48, 0.12);
  --color-danger:         #d84040;
  --color-danger-subtle:  rgba(216, 64, 64, 0.12);
  --color-info:           #4a90d8;
  --color-info-subtle:    rgba(74, 144, 216, 0.12);
}
```

**Font pairing:** Bebas Neue (display, all-caps) + Outfit (body)  
**Signature details:** Slightly warm (not cool) dark bg, strong orange CTAs, monospace code blocks

---

### 3. Deep Navy Cyan — `futuristic-cold`

Precision, data, technology. Suited for: fintech, AI products, data dashboards, analytics.

```css
:root {
  --color-bg:             #05080f;
  --color-bg-elevated:    #080d18;
  --color-surface-1:      #0c1220;
  --color-surface-2:      #111827;
  --color-surface-3:      #1a2540;

  --color-border:         #1e2d45;
  --color-border-strong:  #2a3d5e;
  --color-border-subtle:  #111827;

  --color-text-primary:   #e8f4f8;
  --color-text-secondary: #6a8ca0;
  --color-text-muted:     #3a5468;
  --color-text-inverse:   #05080f;

  /* Accent — electric cyan */
  --color-accent:         #00c8f0;
  --color-accent-hover:   #22d8ff;
  --color-accent-active:  #0098c0;
  --color-accent-subtle:  rgba(0, 200, 240, 0.10);

  /* Secondary glow accent */
  --color-accent-2:       #39ff85;  /* neon green — use sparingly */
  --color-accent-2-subtle: rgba(57, 255, 133, 0.08);

  --color-success:        #39d47a;
  --color-success-subtle: rgba(57, 212, 122, 0.12);
  --color-warning:        #f0a830;
  --color-warning-subtle: rgba(240, 168, 48, 0.12);
  --color-danger:         #e04848;
  --color-danger-subtle:  rgba(224, 72, 72, 0.12);
  --color-info:           #00c8f0;
  --color-info-subtle:    rgba(0, 200, 240, 0.10);
}
```

**Font pairing:** Syne (display) + DM Sans (body) + JetBrains Mono (data)  
**Signature details:** Grid-line backgrounds, glow shadows on accent elements, tight data density

---

### 4. Midnight Ink — `editorial-dark`

Readable, authoritative, cultured. Suited for: news/media, publishing, content-heavy apps.

```css
:root {
  --color-bg:             #0d0d0b;
  --color-bg-elevated:    #131311;
  --color-surface-1:      #181816;
  --color-surface-2:      #202020;
  --color-surface-3:      #2a2a28;

  --color-border:         #2e2e2c;
  --color-border-strong:  #3e3e3c;
  --color-border-subtle:  #1c1c1a;

  --color-text-primary:   #f0ece5;
  --color-text-secondary: #918e88;
  --color-text-muted:     #585550;
  --color-text-inverse:   #0d0d0b;

  /* Accent — rich crimson */
  --color-accent:         #c84040;
  --color-accent-hover:   #d85050;
  --color-accent-active:  #a02e2e;
  --color-accent-subtle:  rgba(200, 64, 64, 0.10);

  --color-success:        #5c9e6a;
  --color-success-subtle: rgba(92, 158, 106, 0.12);
  --color-warning:        #c8922e;
  --color-warning-subtle: rgba(200, 146, 46, 0.12);
  --color-danger:         #c84040;
  --color-danger-subtle:  rgba(200, 64, 64, 0.12);
  --color-info:           #4a90c8;
  --color-info-subtle:    rgba(74, 144, 200, 0.12);
}
```

---

### 5. Void Violet — EXCEPTION Case Only

This is the ONLY scenario where violet/purple is acceptable as accent.
Context: creative tools, gaming, entertainment, art platforms.

```css
:root {
  --color-bg:             #0a080f;
  --color-bg-elevated:    #100d18;
  --color-surface-1:      #160f20;
  --color-surface-2:      #1e162c;
  --color-surface-3:      #261d36;

  --color-border:         #2e2040;
  --color-border-strong:  #3e2e55;
  --color-border-subtle:  #180f24;

  --color-text-primary:   #ede8f5;
  --color-text-secondary: #8878a8;
  --color-text-muted:     #4e4468;
  --color-text-inverse:   #0a080f;

  /* Accent — electric violet (justified here — it's the THEME, not the default) */
  --color-accent:         #9b6fff;
  --color-accent-hover:   #b085ff;
  --color-accent-active:  #7850d8;
  --color-accent-subtle:  rgba(155, 111, 255, 0.12);

  --color-success:        #50d89a;
  --color-success-subtle: rgba(80, 216, 154, 0.12);
  --color-warning:        #e8b040;
  --color-warning-subtle: rgba(232, 176, 64, 0.12);
  --color-danger:         #e04868;
  --color-danger-subtle:  rgba(224, 72, 104, 0.12);
  --color-info:           #50b4f0;
  --color-info-subtle:    rgba(80, 180, 240, 0.10);
}
```

> This palette is ONLY appropriate when the product context is explicitly creative/entertainment/gaming.
> Never use this as a default choice.

---

### 6. GitHub Dark Clone — `data-dense`

High-information density. Suited for: dev tools, code editors, dashboards, admin panels.

```css
:root {
  --color-bg:             #0d1117;
  --color-bg-elevated:    #161b22;
  --color-surface-1:      #161b22;
  --color-surface-2:      #21262d;
  --color-surface-3:      #30363d;

  --color-border:         #30363d;
  --color-border-strong:  #484f58;
  --color-border-subtle:  #21262d;

  --color-text-primary:   #e6edf3;
  --color-text-secondary: #8b949e;
  --color-text-muted:     #484f58;
  --color-text-inverse:   #0d1117;

  /* Accent — GitHub blue */
  --color-accent:         #388bfd;
  --color-accent-hover:   #58a6ff;
  --color-accent-active:  #1f6feb;
  --color-accent-subtle:  rgba(56, 139, 253, 0.12);

  --color-success:        #3fb950;
  --color-success-subtle: rgba(63, 185, 80, 0.12);
  --color-warning:        #d29922;
  --color-warning-subtle: rgba(210, 153, 34, 0.12);
  --color-danger:         #f85149;
  --color-danger-subtle:  rgba(248, 81, 73, 0.12);
  --color-info:           #388bfd;
  --color-info-subtle:    rgba(56, 139, 253, 0.12);
}
```

---

## LIGHT THEMES

---

### 7. Cream Editorial — `editorial-magazine`

Readable, warm, authoritative. Suited for: blogs, news, publishing, content-focused products.

```css
:root {
  --color-bg:             #faf8f3;
  --color-bg-elevated:    #ffffff;
  --color-surface-1:      #f4f1ea;
  --color-surface-2:      #ede9e0;
  --color-surface-3:      #e4e0d6;

  --color-border:         #d4cfc4;
  --color-border-strong:  #bab4a8;
  --color-border-subtle:  #eae7de;

  --color-text-primary:   #1a1a18;
  --color-text-secondary: #5a5850;
  --color-text-muted:     #9a9890;
  --color-text-inverse:   #faf8f3;

  /* Accent — deep editorial red */
  --color-accent:         #c0392b;
  --color-accent-hover:   #d44030;
  --color-accent-active:  #962c20;
  --color-accent-subtle:  rgba(192, 57, 43, 0.08);

  --color-success:        #2e8b57;
  --color-success-subtle: rgba(46, 139, 87, 0.10);
  --color-warning:        #b8860b;
  --color-warning-subtle: rgba(184, 134, 11, 0.10);
  --color-danger:         #c0392b;
  --color-danger-subtle:  rgba(192, 57, 43, 0.10);
  --color-info:           #2060a8;
  --color-info-subtle:    rgba(32, 96, 168, 0.10);
}
```

**Font pairing:** Playfair Display (display) + Lato (body)  
**Signature details:** Paper-like warmth, ink-black text, pullquotes with accent left-border

---

### 8. Arctic White — `zen-minimal`

Focused, distraction-free, clean. Suited for: productivity apps, writing tools, note apps.

```css
:root {
  --color-bg:             #fefefe;
  --color-bg-elevated:    #ffffff;
  --color-surface-1:      #f8f8f8;
  --color-surface-2:      #f0f0f0;
  --color-surface-3:      #e8e8e8;

  --color-border:         #e2e2e2;
  --color-border-strong:  #cccccc;
  --color-border-subtle:  #f0f0f0;

  --color-text-primary:   #111111;
  --color-text-secondary: #555555;
  --color-text-muted:     #999999;
  --color-text-inverse:   #fefefe;

  /* Accent — pure ink (monochromatic — very intentional) */
  --color-accent:         #111111;
  --color-accent-hover:   #333333;
  --color-accent-active:  #000000;
  --color-accent-subtle:  rgba(17, 17, 17, 0.06);

  /* Use a single colored accent for CTAs only */
  --color-cta:            #0052cc;
  --color-cta-hover:      #0066ff;
  --color-cta-subtle:     rgba(0, 82, 204, 0.08);

  --color-success:        #1a7f37;
  --color-success-subtle: rgba(26, 127, 55, 0.08);
  --color-warning:        #9a6700;
  --color-warning-subtle: rgba(154, 103, 0, 0.08);
  --color-danger:         #d1242f;
  --color-danger-subtle:  rgba(209, 36, 47, 0.08);
  --color-info:           #0052cc;
  --color-info-subtle:    rgba(0, 82, 204, 0.08);
}
```

---

### 9. Sand Terracotta — `organic-warm`

Natural, approachable, trustworthy. Suited for: wellness, food, lifestyle, e-commerce organic brands.

```css
:root {
  --color-bg:             #f7f3ed;
  --color-bg-elevated:    #fdfaf7;
  --color-surface-1:      #ede8e0;
  --color-surface-2:      #e2dbd0;
  --color-surface-3:      #d8d0c5;

  --color-border:         #c8bfb0;
  --color-border-strong:  #b0a898;
  --color-border-subtle:  #e8e4dc;

  --color-text-primary:   #2d2420;
  --color-text-secondary: #6a5e55;
  --color-text-muted:     #9a8e85;
  --color-text-inverse:   #f7f3ed;

  /* Accent — warm terracotta */
  --color-accent:         #c4714a;
  --color-accent-hover:   #d4825a;
  --color-accent-active:  #a05838;
  --color-accent-subtle:  rgba(196, 113, 74, 0.10);

  /* Complementary green */
  --color-accent-2:       #3d6b47;
  --color-accent-2-hover: #4a8056;
  --color-accent-2-subtle: rgba(61, 107, 71, 0.10);

  --color-success:        #3d6b47;
  --color-success-subtle: rgba(61, 107, 71, 0.10);
  --color-warning:        #a07830;
  --color-warning-subtle: rgba(160, 120, 48, 0.10);
  --color-danger:         #b84040;
  --color-danger-subtle:  rgba(184, 64, 64, 0.10);
  --color-info:           #3a6890;
  --color-info-subtle:    rgba(58, 104, 144, 0.10);
}
```

---

### 10. Coral Playful — `playful-kinetic`

Warm, energetic, expressive. Suited for: consumer apps, social, fun tools, onboarding flows.

```css
:root {
  --color-bg:             #fff9f5;
  --color-bg-elevated:    #ffffff;
  --color-surface-1:      #fff2ea;
  --color-surface-2:      #ffe8d8;
  --color-surface-3:      #ffddc8;

  --color-border:         #f0cdb5;
  --color-border-strong:  #ddb595;
  --color-border-subtle:  #fff5ee;

  --color-text-primary:   #2d1a0e;
  --color-text-secondary: #6a4030;
  --color-text-muted:     #a07860;
  --color-text-inverse:   #fff9f5;

  /* Accent — vivid coral */
  --color-accent:         #ff6b35;
  --color-accent-hover:   #ff8050;
  --color-accent-active:  #e05520;
  --color-accent-subtle:  rgba(255, 107, 53, 0.10);

  /* Fun secondary — sunshine yellow */
  --color-accent-2:       #ffc42a;
  --color-accent-2-subtle: rgba(255, 196, 42, 0.12);

  --color-success:        #2e9a5a;
  --color-success-subtle: rgba(46, 154, 90, 0.10);
  --color-warning:        #e89020;
  --color-warning-subtle: rgba(232, 144, 32, 0.10);
  --color-danger:         #e03030;
  --color-danger-subtle:  rgba(224, 48, 48, 0.10);
  --color-info:           #2878d4;
  --color-info-subtle:    rgba(40, 120, 212, 0.10);
}
```

---

### 11. Pure Brutalist — `brutalist-raw`

Uncompromising contrast. Suited for: design agencies, art portfolios, experimental/conceptual projects.

```css
:root {
  --color-bg:             #ffffff;
  --color-bg-elevated:    #ffffff;
  --color-surface-1:      #f4f4f4;
  --color-surface-2:      #e8e8e8;
  --color-surface-3:      #dcdcdc;

  --color-border:         #000000;  /* 2px solid borders everywhere */
  --color-border-strong:  #000000;
  --color-border-subtle:  #cccccc;

  --color-text-primary:   #000000;
  --color-text-secondary: #333333;
  --color-text-muted:     #666666;
  --color-text-inverse:   #ffffff;

  /* Accent — single brutal color (swap this for the project's personality) */
  --color-accent:         #ff3300;  /* Options: #ffff00, #0000ff, #00ff00 */
  --color-accent-hover:   #ff5500;
  --color-accent-active:  #cc2200;
  --color-accent-subtle:  rgba(255, 51, 0, 0.08);

  --color-success:        #008800;
  --color-success-subtle: rgba(0, 136, 0, 0.08);
  --color-warning:        #888800;
  --color-warning-subtle: rgba(136, 136, 0, 0.08);
  --color-danger:         #cc0000;
  --color-danger-subtle:  rgba(204, 0, 0, 0.08);
  --color-info:           #0000cc;
  --color-info-subtle:    rgba(0, 0, 204, 0.08);
}

/* Brutalist requires heavier borders */
.btn, .card, input, select {
  border-width: 2px;
  border-style: solid;
  border-color: var(--color-border);
  border-radius: 0 !important;  /* No rounded corners in brutalism */
}
```

---

### 12. Sage Professional — B2B/Enterprise Light

Clean, trustworthy, professional. Suited for: B2B SaaS, enterprise tools, healthcare, finance.

```css
:root {
  --color-bg:             #f8f9fa;
  --color-bg-elevated:    #ffffff;
  --color-surface-1:      #ffffff;
  --color-surface-2:      #f1f3f5;
  --color-surface-3:      #e9ecef;

  --color-border:         #dee2e6;
  --color-border-strong:  #adb5bd;
  --color-border-subtle:  #f1f3f5;

  --color-text-primary:   #1a2332;
  --color-text-secondary: #495057;
  --color-text-muted:     #868e96;
  --color-text-inverse:   #ffffff;

  /* Accent — trustworthy blue (NOT Tailwind default blue) */
  --color-accent:         #1565c0;
  --color-accent-hover:   #1976d2;
  --color-accent-active:  #0d47a1;
  --color-accent-subtle:  rgba(21, 101, 192, 0.08);

  --color-success:        #2e7d32;
  --color-success-subtle: rgba(46, 125, 50, 0.08);
  --color-warning:        #e65100;
  --color-warning-subtle: rgba(230, 81, 0, 0.08);
  --color-danger:         #c62828;
  --color-danger-subtle:  rgba(198, 40, 40, 0.08);
  --color-info:           #0277bd;
  --color-info-subtle:    rgba(2, 119, 189, 0.08);
}
```

---

### 13. Retro Amber — `retro-nostalgic`

Vintage warmth, character-rich. Suited for: indie games, podcasts, journals, creative projects.

```css
:root {
  --color-bg:             #f5f0dc;
  --color-bg-elevated:    #faf6e8;
  --color-surface-1:      #ece5c8;
  --color-surface-2:      #e2d8b8;
  --color-surface-3:      #d8cda8;

  --color-border:         #c0b48e;
  --color-border-strong:  #a09070;
  --color-border-subtle:  #e8e2cc;

  --color-text-primary:   #2a2018;
  --color-text-secondary: #5a4e40;
  --color-text-muted:     #8a8070;
  --color-text-inverse:   #f5f0dc;

  /* Accent — deep forest green */
  --color-accent:         #5c7a2e;
  --color-accent-hover:   #6e9038;
  --color-accent-active:  #486022;
  --color-accent-subtle:  rgba(92, 122, 46, 0.10);

  /* Secondary — brick red */
  --color-accent-2:       #8b3a3a;
  --color-accent-2-hover: #a04444;
  --color-accent-2-subtle: rgba(139, 58, 58, 0.10);

  --color-success:        #5c7a2e;
  --color-success-subtle: rgba(92, 122, 46, 0.10);
  --color-warning:        #a07020;
  --color-warning-subtle: rgba(160, 112, 32, 0.10);
  --color-danger:         #8b3a3a;
  --color-danger-subtle:  rgba(139, 58, 58, 0.10);
  --color-info:           #3a5a8b;
  --color-info-subtle:    rgba(58, 90, 139, 0.10);
}
```

---

### 14. Mint Fresh — Startup/Consumer

Fresh, modern, optimistic. Suited for: fintech apps, health trackers, productivity tools.

```css
:root {
  --color-bg:             #f0faf5;
  --color-bg-elevated:    #ffffff;
  --color-surface-1:      #ffffff;
  --color-surface-2:      #e8f5ee;
  --color-surface-3:      #d8eee0;

  --color-border:         #b8d8c4;
  --color-border-strong:  #88b89a;
  --color-border-subtle:  #eaf7f0;

  --color-text-primary:   #0f2d1e;
  --color-text-secondary: #3d6550;
  --color-text-muted:     #6a9878;
  --color-text-inverse:   #ffffff;

  /* Accent — deep emerald */
  --color-accent:         #0d9e5e;
  --color-accent-hover:   #10b86e;
  --color-accent-active:  #088048;
  --color-accent-subtle:  rgba(13, 158, 94, 0.10);

  --color-success:        #0d9e5e;
  --color-success-subtle: rgba(13, 158, 94, 0.10);
  --color-warning:        #b87a10;
  --color-warning-subtle: rgba(184, 122, 16, 0.10);
  --color-danger:         #c84040;
  --color-danger-subtle:  rgba(200, 64, 64, 0.10);
  --color-info:           #1a78c4;
  --color-info-subtle:    rgba(26, 120, 196, 0.10);
}
```

---

### 15. Sable Gray — Neutral Professional

Versatile, neutral, modern. Best for: when client hasn't defined brand, or when content should
dominate over the chrome.

```css
:root {
  --color-bg:             #f6f6f6;
  --color-bg-elevated:    #ffffff;
  --color-surface-1:      #ffffff;
  --color-surface-2:      #eeeeee;
  --color-surface-3:      #e4e4e4;

  --color-border:         #d8d8d8;
  --color-border-strong:  #b8b8b8;
  --color-border-subtle:  #eeeeee;

  --color-text-primary:   #181818;
  --color-text-secondary: #484848;
  --color-text-muted:     #888888;
  --color-text-inverse:   #ffffff;

  /* Accent — rich amber (the only warmth in an otherwise neutral palette) */
  --color-accent:         #d4820a;
  --color-accent-hover:   #e8940e;
  --color-accent-active:  #b06808;
  --color-accent-subtle:  rgba(212, 130, 10, 0.10);

  --color-success:        #2a7a3a;
  --color-success-subtle: rgba(42, 122, 58, 0.08);
  --color-warning:        #a87808;
  --color-warning-subtle: rgba(168, 120, 8, 0.08);
  --color-danger:         #c43030;
  --color-danger-subtle:  rgba(196, 48, 48, 0.08);
  --color-info:           #1860b8;
  --color-info-subtle:    rgba(24, 96, 184, 0.08);
}
```

---

## GRADIENT BACKGROUNDS (Use Sparingly)

Gradients belong in hero sections and backgrounds, not on buttons or cards.

```css
/* ─── HERO: radial spotlight (dark themes) ────────────────────────── */
.hero-spotlight {
  background:
    radial-gradient(ellipse 100% 80% at 50% -20%,
      rgba(0, 200, 240, 0.15) 0%, transparent 60%),
    var(--color-bg);
}

/* ─── HERO: mesh gradient (light themes) ─────────────────────────── */
.hero-mesh {
  background:
    radial-gradient(at 15% 25%, hsla(42, 90%, 55%, 0.18) 0px, transparent 55%),
    radial-gradient(at 85% 15%, hsla(200, 80%, 55%, 0.12) 0px, transparent 55%),
    radial-gradient(at 50% 85%, hsla(42, 70%, 55%, 0.10) 0px, transparent 55%),
    var(--color-bg);
}

/* ─── SECTION: subtle gradient transition ─────────────────────────── */
.section-fade-in {
  background: linear-gradient(
    to bottom,
    var(--color-bg) 0%,
    var(--color-surface-1) 100%
  );
}

/* ─── CARD: inner glow (dark themes) ─────────────────────────────── */
.card-glow {
  background: radial-gradient(
    ellipse 70% 50% at 50% 0%,
    var(--color-accent-subtle),
    var(--color-surface-1) 100%
  );
}

/* ─── PHOTO OVERLAY (text over images) ───────────────────────────── */
.photo-overlay {
  background: linear-gradient(
    to bottom,
    transparent 30%,
    rgba(0,0,0,0.75) 100%
  );
}
```

---

## BACKGROUND TEXTURES

```css
/* ─── NOISE/GRAIN ─────────────────────────────────────────────────── */
/* For grain SVG data URL, use: https://grainy-gradients.vercel.app */
/* Opacity 3-6% on dark themes, 2-4% on light themes */
.grainy::after {
  content: '';
  position: absolute;
  inset: 0;
  background-image: url("data:image/svg+xml,...");
  opacity: 0.04;
  pointer-events: none;
  z-index: 0;
}

/* ─── DOT GRID ────────────────────────────────────────────────────── */
.bg-dots {
  background-image: radial-gradient(
    circle, var(--color-border) 1px, transparent 1px
  );
  background-size: 24px 24px;
}

/* ─── LINE GRID ───────────────────────────────────────────────────── */
.bg-grid {
  background-image:
    linear-gradient(var(--color-border-subtle) 1px, transparent 1px),
    linear-gradient(90deg, var(--color-border-subtle) 1px, transparent 1px);
  background-size: 40px 40px;
}

/* ─── DIAGONAL LINES (brutalist/industrial) ───────────────────────── */
.bg-diagonal {
  background-image: repeating-linear-gradient(
    45deg,
    transparent 0px,
    transparent 8px,
    var(--color-border-subtle) 8px,
    var(--color-border-subtle) 9px
  );
}
```
