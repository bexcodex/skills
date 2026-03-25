# SVG Icon Library — 70+ Ready-to-Paste Icons

## Standard Template

All icons use the Feather/Lucide 24px grid. Use this template for every icon:

```html
<svg
  xmlns="http://www.w3.org/2000/svg"
  width="20"
  height="20"
  viewBox="0 0 24 24"
  fill="none"
  stroke="currentColor"
  stroke-width="1.5"
  stroke-linecap="round"
  stroke-linejoin="round"
  aria-hidden="true"
  focusable="false"
>
  <!-- PASTE PATH CONTENT HERE -->
</svg>
```

**Stroke-width guide:**
- `1.5` — Refined, editorial, elegant. Use for luxury/editorial/minimal aesthetics.
- `2` — Standard, clear, app-like. Best for most UI work.
- `2.5` — Bold, high-contrast, accessible. Use for small sizes or industrial aesthetics.

**Size guide:**
- `16×16` — Compact UI, toolbars, badges
- `18×18` — Inline with text (small copy)
- `20×20` — Standard UI elements (recommended default)
- `24×24` — Navigation, tab bars, prominent elements
- `32–48×32–48` — Feature icons, hero icons

---

## NAVIGATION

### Home
```html
<path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/>
<polyline points="9 22 9 12 15 12 15 22"/>
```

### Menu (Hamburger)
```html
<line x1="3" y1="12" x2="21" y2="12"/>
<line x1="3" y1="6" x2="21" y2="6"/>
<line x1="3" y1="18" x2="21" y2="18"/>
```

### Close (X)
```html
<line x1="18" y1="6" x2="6" y2="18"/>
<line x1="6" y1="6" x2="18" y2="18"/>
```

### Back (Arrow Left)
```html
<line x1="19" y1="12" x2="5" y2="12"/>
<polyline points="12 19 5 12 12 5"/>
```

### Forward (Arrow Right)
```html
<line x1="5" y1="12" x2="19" y2="12"/>
<polyline points="12 5 19 12 12 19"/>
```

### Chevron Right
```html
<polyline points="9 18 15 12 9 6"/>
```

### Chevron Left
```html
<polyline points="15 18 9 12 15 6"/>
```

### Chevron Down
```html
<polyline points="6 9 12 15 18 9"/>
```

### Chevron Up
```html
<polyline points="18 15 12 9 6 15"/>
```

### External Link
```html
<path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/>
<polyline points="15 3 21 3 21 9"/>
<line x1="10" y1="14" x2="21" y2="3"/>
```

### Grid / Apps
```html
<rect x="3" y="3" width="7" height="7"/>
<rect x="14" y="3" width="7" height="7"/>
<rect x="14" y="14" width="7" height="7"/>
<rect x="3" y="14" width="7" height="7"/>
```

### Sidebar
```html
<rect x="3" y="3" width="18" height="18" rx="2" ry="2"/>
<line x1="9" y1="3" x2="9" y2="21"/>
```

### Breadcrumb Separator (Slash)
```html
<line x1="16.88" y1="3.12" x2="7.12" y2="20.88"/>
```

---

## ACTIONS

### Search
```html
<circle cx="11" cy="11" r="8"/>
<line x1="21" y1="21" x2="16.65" y2="16.65"/>
```

### Plus / Add
```html
<line x1="12" y1="5" x2="12" y2="19"/>
<line x1="5" y1="12" x2="19" y2="12"/>
```

### Minus / Remove
```html
<line x1="5" y1="12" x2="19" y2="12"/>
```

### Edit / Pencil
```html
<path d="M11 4H4a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7"/>
<path d="M18.5 2.5a2.121 2.121 0 0 1 3 3L12 15l-4 1 1-4 9.5-9.5z"/>
```

### Trash / Delete
```html
<polyline points="3 6 5 6 21 6"/>
<path d="M19 6v14a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2V6m3 0V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2"/>
```

### Download
```html
<path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/>
<polyline points="7 10 12 15 17 10"/>
<line x1="12" y1="15" x2="12" y2="3"/>
```

### Upload
```html
<path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/>
<polyline points="17 8 12 3 7 8"/>
<line x1="12" y1="3" x2="12" y2="15"/>
```

### Copy
```html
<rect x="9" y="9" width="13" height="13" rx="2" ry="2"/>
<path d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"/>
```

### Share
```html
<circle cx="18" cy="5" r="3"/>
<circle cx="6" cy="12" r="3"/>
<circle cx="18" cy="19" r="3"/>
<line x1="8.59" y1="13.51" x2="15.42" y2="17.49"/>
<line x1="15.41" y1="6.51" x2="8.59" y2="10.49"/>
```

### Link / Chain
```html
<path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"/>
<path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"/>
```

### Filter
```html
<polygon points="22 3 2 3 10 12.46 10 19 14 21 14 12.46 22 3"/>
```

### Sort / Sliders
```html
<line x1="4" y1="21" x2="4" y2="14"/>
<line x1="4" y1="10" x2="4" y2="3"/>
<line x1="12" y1="21" x2="12" y2="12"/>
<line x1="12" y1="8" x2="12" y2="3"/>
<line x1="20" y1="21" x2="20" y2="16"/>
<line x1="20" y1="12" x2="20" y2="3"/>
<line x1="1" y1="14" x2="7" y2="14"/>
<line x1="9" y1="8" x2="15" y2="8"/>
<line x1="17" y1="16" x2="23" y2="16"/>
```

### Refresh / Rotate
```html
<polyline points="23 4 23 10 17 10"/>
<polyline points="1 20 1 14 7 14"/>
<path d="M3.51 9a9 9 0 0 1 14.85-3.36L23 10M1 14l4.64 4.36A9 9 0 0 0 20.49 15"/>
```

### Move / Drag
```html
<polyline points="5 9 2 12 5 15"/>
<polyline points="9 5 12 2 15 5"/>
<polyline points="15 19 12 22 9 19"/>
<polyline points="19 9 22 12 19 15"/>
<line x1="2" y1="12" x2="22" y2="12"/>
<line x1="12" y1="2" x2="12" y2="22"/>
```

### Maximize / Expand
```html
<polyline points="15 3 21 3 21 9"/>
<polyline points="9 21 3 21 3 15"/>
<line x1="21" y1="3" x2="14" y2="10"/>
<line x1="3" y1="21" x2="10" y2="14"/>
```

### Minimize / Compress
```html
<polyline points="4 14 10 14 10 20"/>
<polyline points="20 10 14 10 14 4"/>
<line x1="10" y1="14" x2="3" y2="21"/>
<line x1="21" y1="3" x2="14" y2="10"/>
```

### More Horizontal (⋯)
```html
<circle cx="12" cy="12" r="1"/>
<circle cx="19" cy="12" r="1"/>
<circle cx="5" cy="12" r="1"/>
```

### More Vertical (⋮)
```html
<circle cx="12" cy="12" r="1"/>
<circle cx="12" cy="5" r="1"/>
<circle cx="12" cy="19" r="1"/>
```

---

## STATUS & FEEDBACK

### Check / Success
```html
<polyline points="20 6 9 17 4 12"/>
```

### Check Circle
```html
<path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"/>
<polyline points="22 4 12 14.01 9 11.01"/>
```

### X Circle
```html
<circle cx="12" cy="12" r="10"/>
<line x1="15" y1="9" x2="9" y2="15"/>
<line x1="9" y1="9" x2="15" y2="15"/>
```

### Alert Triangle / Warning
```html
<path d="M10.29 3.86L1.82 18a2 2 0 0 0 1.71 3h16.94a2 2 0 0 0 1.71-3L13.71 3.86a2 2 0 0 0-3.42 0z"/>
<line x1="12" y1="9" x2="12" y2="13"/>
<line x1="12" y1="17" x2="12.01" y2="17"/>
```

### Info Circle
```html
<circle cx="12" cy="12" r="10"/>
<line x1="12" y1="8" x2="12" y2="12"/>
<line x1="12" y1="16" x2="12.01" y2="16"/>
```

### Loading (Spinner arc — animate with CSS rotate)
```html
<!-- Add to SVG: style="animation: spin 0.8s linear infinite" -->
<!-- @keyframes spin { to { transform: rotate(360deg); } } -->
<path d="M21 12a9 9 0 1 1-6.219-8.56"/>
```

### Loading Dots (Inline pulse)
```html
<!-- Use three separate circles and stagger pulse animation -->
<circle cx="4" cy="12" r="2"/>
<circle cx="12" cy="12" r="2"/>
<circle cx="20" cy="12" r="2"/>
```

---

## USER & PROFILE

### User (Single)
```html
<path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/>
<circle cx="12" cy="7" r="4"/>
```

### Users (Group)
```html
<path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/>
<circle cx="9" cy="7" r="4"/>
<path d="M23 21v-2a4 4 0 0 0-3-3.87"/>
<path d="M16 3.13a4 4 0 0 1 0 7.75"/>
```

### User Plus
```html
<path d="M16 21v-2a4 4 0 0 0-4-4H6a4 4 0 0 0-4 4v2"/>
<circle cx="9" cy="7" r="4"/>
<line x1="19" y1="8" x2="19" y2="14"/>
<line x1="22" y1="11" x2="16" y2="11"/>
```

### Heart (Like / Favorite)
```html
<path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/>
```

### Star (Rating / Bookmark)
```html
<polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"/>
```

### Bookmark
```html
<path d="M19 21l-7-5-7 5V5a2 2 0 0 1 2-2h10a2 2 0 0 1 2 2z"/>
```

### Award / Badge
```html
<circle cx="12" cy="8" r="6"/>
<path d="M15.477 12.89L17 22l-5-3-5 3 1.523-9.11"/>
```

---

## COMMUNICATION

### Mail / Email
```html
<path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/>
<polyline points="22,6 12,13 2,6"/>
```

### Message / Chat Bubble
```html
<path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/>
```

### Phone
```html
<path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.63 13a19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 3.54 2h3a2 2 0 0 1 2 1.72c.127.96.361 1.903.7 2.81a2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l.81-.81a2 2 0 0 1 2.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0 1 22 16.92z"/>
```

### Bell (Notification)
```html
<path d="M18 8A6 6 0 0 0 6 8c0 7-3 9-3 9h18s-3-2-3-9"/>
<path d="M13.73 21a2 2 0 0 1-3.46 0"/>
```

### Send
```html
<line x1="22" y1="2" x2="11" y2="13"/>
<polygon points="22 2 15 22 11 13 2 9 22 2"/>
```

---

## FILES & MEDIA

### File
```html
<path d="M13 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V9z"/>
<polyline points="13 2 13 9 20 9"/>
```

### Folder
```html
<path d="M22 19a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h5l2 3h9a2 2 0 0 1 2 2z"/>
```

### Image / Photo
```html
<rect x="3" y="3" width="18" height="18" rx="2" ry="2"/>
<circle cx="8.5" cy="8.5" r="1.5"/>
<polyline points="21 15 16 10 5 21"/>
```

### Video / Film
```html
<polygon points="23 7 16 12 23 17 23 7"/>
<rect x="1" y="5" width="15" height="14" rx="2" ry="2"/>
```

### Music Note
```html
<path d="M9 18V5l12-2v13"/>
<circle cx="6" cy="18" r="3"/>
<circle cx="18" cy="16" r="3"/>
```

### Play
```html
<polygon points="5 3 19 12 5 21 5 3"/>
```

### Pause
```html
<rect x="6" y="4" width="4" height="16"/>
<rect x="14" y="4" width="4" height="16"/>
```

### Mic
```html
<path d="M12 1a3 3 0 0 0-3 3v8a3 3 0 0 0 6 0V4a3 3 0 0 0-3-3z"/>
<path d="M19 10v2a7 7 0 0 1-14 0v-2"/>
<line x1="12" y1="19" x2="12" y2="23"/>
<line x1="8" y1="23" x2="16" y2="23"/>
```

---

## SETTINGS & SYSTEM

### Settings (Gear)
```html
<circle cx="12" cy="12" r="3"/>
<path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06A1.65 1.65 0 0 0 4.68 15a1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06A1.65 1.65 0 0 0 9 4.68a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 2-2 2 2 0 0 1 2 2v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06A1.65 1.65 0 0 0 19.4 9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.51 1z"/>
```

### Lock
```html
<rect x="3" y="11" width="18" height="11" rx="2" ry="2"/>
<path d="M7 11V7a5 5 0 0 1 10 0v4"/>
```

### Unlock
```html
<rect x="3" y="11" width="18" height="11" rx="2" ry="2"/>
<path d="M7 11V7a5 5 0 0 1 9.9-1"/>
```

### Eye (Show)
```html
<path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"/>
<circle cx="12" cy="12" r="3"/>
```

### Eye Off (Hide)
```html
<path d="M17.94 17.94A10.07 10.07 0 0 1 12 20c-7 0-11-8-11-8a18.45 18.45 0 0 1 5.06-5.94M9.9 4.24A9.12 9.12 0 0 1 12 4c7 0 11 8 11 8a18.5 18.5 0 0 1-2.16 3.19m-6.72-1.07a3 3 0 1 1-4.24-4.24"/>
<line x1="1" y1="1" x2="23" y2="23"/>
```

### Sun (Light Mode)
```html
<circle cx="12" cy="12" r="5"/>
<line x1="12" y1="1" x2="12" y2="3"/>
<line x1="12" y1="21" x2="12" y2="23"/>
<line x1="4.22" y1="4.22" x2="5.64" y2="5.64"/>
<line x1="18.36" y1="18.36" x2="19.78" y2="19.78"/>
<line x1="1" y1="12" x2="3" y2="12"/>
<line x1="21" y1="12" x2="23" y2="12"/>
<line x1="4.22" y1="19.78" x2="5.64" y2="18.36"/>
<line x1="18.36" y1="5.64" x2="19.78" y2="4.22"/>
```

### Moon (Dark Mode)
```html
<path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/>
```

### Globe / Language
```html
<circle cx="12" cy="12" r="10"/>
<line x1="2" y1="12" x2="22" y2="12"/>
<path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/>
```

### Map Pin / Location
```html
<path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/>
<circle cx="12" cy="10" r="3"/>
```

### Calendar
```html
<rect x="3" y="4" width="18" height="18" rx="2" ry="2"/>
<line x1="16" y1="2" x2="16" y2="6"/>
<line x1="8" y1="2" x2="8" y2="6"/>
<line x1="3" y1="10" x2="21" y2="10"/>
```

### Clock / Time
```html
<circle cx="12" cy="12" r="10"/>
<polyline points="12 6 12 12 16 14"/>
```

### Tag
```html
<path d="M20.59 13.41l-7.17 7.17a2 2 0 0 1-2.83 0L2 12V2h10l8.59 8.59a2 2 0 0 1 0 2.82z"/>
<line x1="7" y1="7" x2="7.01" y2="7"/>
```

---

## DATA & ANALYTICS

### Bar Chart
```html
<line x1="18" y1="20" x2="18" y2="10"/>
<line x1="12" y1="20" x2="12" y2="4"/>
<line x1="6" y1="20" x2="6" y2="14"/>
<line x1="2" y1="20" x2="22" y2="20"/>
```

### Trending Up
```html
<polyline points="23 6 13.5 15.5 8.5 10.5 1 18"/>
<polyline points="17 6 23 6 23 12"/>
```

### Trending Down
```html
<polyline points="23 18 13.5 8.5 8.5 13.5 1 6"/>
<polyline points="17 18 23 18 23 12"/>
```

### Pie Chart
```html
<path d="M21.21 15.89A10 10 0 1 1 8 2.83"/>
<path d="M22 12A10 10 0 0 0 12 2v10z"/>
```

### Activity (Pulse / Heartbeat)
```html
<polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/>
```

---

## DEVELOPER / TECH

### Code Brackets
```html
<polyline points="16 18 22 12 16 6"/>
<polyline points="8 6 2 12 8 18"/>
```

### Terminal / CLI
```html
<polyline points="4 17 10 11 4 5"/>
<line x1="12" y1="19" x2="20" y2="19"/>
```

### GitHub (Fill style — use fill="currentColor", remove stroke)
```html
<!-- NOTE: Change SVG to fill="currentColor" stroke="none" for this icon -->
<path fill-rule="evenodd" clip-rule="evenodd" d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0 1 12 6.844a9.59 9.59 0 0 1 2.504.337c1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.02 10.02 0 0 0 22 12.017C22 6.484 17.522 2 12 2z"/>
```

### Zap / Lightning (Feature / Fast)
```html
<polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"/>
```

### Package / Box
```html
<line x1="16.5" y1="9.4" x2="7.5" y2="4.21"/>
<path d="M21 16V8a2 2 0 0 0-1-1.73l-7-4a2 2 0 0 0-2 0l-7 4A2 2 0 0 0 3 8v8a2 2 0 0 0 1 1.73l7 4a2 2 0 0 0 2 0l7-4A2 2 0 0 0 21 16z"/>
<polyline points="3.27 6.96 12 12.01 20.73 6.96"/>
<line x1="12" y1="22.08" x2="12" y2="12"/>
```

### Database
```html
<ellipse cx="12" cy="5" rx="9" ry="3"/>
<path d="M21 12c0 1.66-4 3-9 3s-9-1.34-9-3"/>
<path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5"/>
```

### Server
```html
<rect x="2" y="2" width="20" height="8" rx="2" ry="2"/>
<rect x="2" y="14" width="20" height="8" rx="2" ry="2"/>
<line x1="6" y1="6" x2="6.01" y2="6"/>
<line x1="6" y1="18" x2="6.01" y2="18"/>
```

### CPU / Processor
```html
<rect x="4" y="4" width="16" height="16" rx="2" ry="2"/>
<rect x="9" y="9" width="6" height="6"/>
<line x1="9" y1="1" x2="9" y2="4"/>
<line x1="15" y1="1" x2="15" y2="4"/>
<line x1="9" y1="20" x2="9" y2="23"/>
<line x1="15" y1="20" x2="15" y2="23"/>
<line x1="20" y1="9" x2="23" y2="9"/>
<line x1="20" y1="14" x2="23" y2="14"/>
<line x1="1" y1="9" x2="4" y2="9"/>
<line x1="1" y1="14" x2="4" y2="14"/>
```

---

## COMPLETE ICON COMPONENT EXAMPLES

### React (Lucide import)
```jsx
import { Search, X, ChevronDown, Settings } from 'lucide-react'

export function SearchBar() {
  return (
    <div className="relative flex items-center">
      <Search
        size={18}
        strokeWidth={1.5}
        className="absolute left-3 text-[var(--color-text-muted)]"
      />
      <input
        className="pl-10 pr-4 py-2 bg-[var(--color-surface-2)] border border-[var(--color-border)] rounded-lg"
        placeholder="Search..."
      />
    </div>
  )
}
```

### Inline SVG with CSS animation (Spinner)
```html
<svg
  xmlns="http://www.w3.org/2000/svg"
  width="20" height="20"
  viewBox="0 0 24 24"
  fill="none"
  stroke="currentColor"
  stroke-width="2"
  stroke-linecap="round"
  stroke-linejoin="round"
  style="animation: spin 0.8s linear infinite; color: var(--color-accent);"
  aria-label="Loading"
>
  <path d="M21 12a9 9 0 1 1-6.219-8.56"/>
</svg>

<style>
@keyframes spin { to { transform: rotate(360deg); } }
</style>
```

### Standalone icon button (accessible)
```html
<button
  type="button"
  aria-label="Close"
  class="icon-btn"
  style="
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 36px;
    height: 36px;
    border: none;
    background: transparent;
    color: var(--color-text-muted);
    border-radius: 8px;
    cursor: pointer;
    transition: background 150ms ease, color 150ms ease;
  "
>
  <svg width="18" height="18" viewBox="0 0 24 24" fill="none"
       stroke="currentColor" stroke-width="2"
       stroke-linecap="round" stroke-linejoin="round"
       aria-hidden="true">
    <line x1="18" y1="6" x2="6" y2="18"/>
    <line x1="6" y1="6" x2="18" y2="18"/>
  </svg>
</button>
```
