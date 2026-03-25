# Performance Reference — Deep Patterns by Framework

> Target: LCP < 2.5s, CLS < 0.1, INP < 200ms, TTI < 3.5s on mid-range mobile (Moto G4 equivalent)
> All techniques ordered by impact: highest ROI first.

---

## MEASUREMENT FIRST — Don't Optimize Blindly

Always measure before and after. Optimization without measurement is guesswork.

### Tools

| Tool | Use For | URL |
|------|---------|-----|
| **Lighthouse** | Overall score, all metrics | Chrome DevTools → Lighthouse tab |
| **WebPageTest** | Real device testing, waterfall | https://webpagetest.org |
| **PageSpeed Insights** | Field data (real users) + Lab data | https://pagespeed.web.dev |
| **Chrome DevTools Performance** | JS execution, main thread, layout | F12 → Performance tab |
| **Chrome DevTools Coverage** | Unused CSS/JS | F12 → Coverage tab |
| **Bundle Size** | JS payload | below |

```bash
# Lighthouse CLI — automate in CI
npm install -g lighthouse
lighthouse https://yoursite.com --output html --output-path report.html

# Bundle analysis
# Next.js:
ANALYZE=true npm run build

# Vite:
npx vite-bundle-visualizer

# Webpack:
npx webpack-bundle-analyzer
```

### Performance Budget — Track These Numbers

| Metric | Mobile Budget | Desktop Budget |
|--------|-------------|----------------|
| LCP | < 2.5s | < 1.5s |
| CLS | < 0.1 | < 0.1 |
| INP | < 200ms | < 100ms |
| FCP | < 1.8s | < 1.0s |
| TTI | < 3.5s | < 2.0s |
| Total JS (gzipped) | < 250KB | < 400KB |
| Total CSS (gzipped) | < 30KB | < 50KB |
| Initial HTML | < 14KB | < 14KB |
| Hero image (WebP) | < 150KB | < 250KB |
| Total page weight | < 1.5MB | < 3MB |

---

## IMAGE OPTIMIZATION

Images are responsible for 60–80% of page weight on most sites.

### Format Decision Tree

```
Is it a photo or complex illustration?
  YES → WebP (with AVIF src for modern browsers)
  NO  → Is it a logo, icon, or geometric illustration?
          YES → SVG
          NO  → Does it have transparency + sharp edges?
                  YES → PNG
                  NO  → WebP
```

### Compression Targets

```bash
# Install sharp (Node) for batch processing
npm install sharp

# One-liner conversions:
# WebP from JPEG:
npx sharp-cli --input "*.jpg" --output ./optimized --format webp --quality 80

# AVIF from JPEG (better compression, slower encode):
npx sharp-cli --input "*.jpg" --output ./optimized --format avif --quality 65

# Resize + compress in one step:
npx sharp-cli --input hero.jpg --output hero.webp --width 1200 --format webp --quality 82
```

**Manual targets:**
- Hero images: 80–150KB WebP (1200–1920px wide, quality 80–85)
- Card thumbnails: 20–50KB WebP (400–800px wide, quality 75–82)
- Avatar/profile: 5–15KB WebP (100–200px, quality 75)
- Open Graph / social: 200–300KB (must be JPEG/PNG — social crawlers don't support WebP)

### Next.js Image Component — Always Use This

```tsx
import Image from 'next/image'

// Hero image — LCP element
<Image
  src="/hero.webp"
  alt="Descriptive alt text"
  width={1200}
  height={630}
  priority          // fetchpriority="high" + disables lazy loading
  quality={85}      // default is 75, good for hero
  sizes="100vw"     // full viewport width
/>

// Responsive card image
<Image
  src="/feature.webp"
  alt="Feature description"
  width={800}
  height={600}
  quality={80}
  sizes="(max-width: 640px) 100vw, (max-width: 1024px) 50vw, 400px"
  // Auto-generates srcset matching your sizes
/>

// Fill container (unknown dimensions)
<div style={{ position: 'relative', aspectRatio: '16/9' }}>
  <Image
    src="/banner.webp"
    alt="Banner"
    fill
    style={{ objectFit: 'cover' }}
    sizes="(max-width: 768px) 100vw, 1200px"
  />
</div>

// Remote images — must whitelist domain in next.config.js
// next.config.js:
module.exports = {
  images: {
    domains: ['images.unsplash.com', 'cdn.yourapp.com'],
    // or use remotePatterns for more control:
    remotePatterns: [{
      protocol: 'https',
      hostname: '**.amazonaws.com',
    }],
  },
}
```

**next.config.js image optimization:**
```js
module.exports = {
  images: {
    formats: ['image/avif', 'image/webp'],  // serve AVIF where supported
    minimumCacheTTL: 60 * 60 * 24 * 30,    // 30 days
    deviceSizes: [320, 480, 640, 750, 828, 1080, 1200, 1920],
    imageSizes: [16, 32, 48, 64, 96, 128, 256, 384],
  },
}
```

### Vanilla HTML — Correct Responsive Image Markup

```html
<!-- Complete pattern: AVIF → WebP → JPEG fallback, multiple sizes -->
<picture>
  <!-- AVIF: best compression, Chrome 85+ / Firefox 93+ / Safari 16.4+ -->
  <source
    type="image/avif"
    srcset="hero-800.avif 800w, hero-1200.avif 1200w, hero-1920.avif 1920w"
    sizes="(max-width: 640px) 100vw, (max-width: 1280px) 80vw, 1200px"
  >
  <!-- WebP: broad support -->
  <source
    type="image/webp"
    srcset="hero-800.webp 800w, hero-1200.webp 1200w, hero-1920.webp 1920w"
    sizes="(max-width: 640px) 100vw, (max-width: 1280px) 80vw, 1200px"
  >
  <!-- JPEG fallback: all browsers -->
  <img
    src="hero-1200.jpg"
    alt="Descriptive text — never empty for content images"
    width="1200"
    height="630"
    fetchpriority="high"
    decoding="async"
  >
</picture>

<!-- Art direction: different composition on mobile vs desktop -->
<picture>
  <source media="(max-width: 639px)"
    srcset="hero-portrait-640.webp"
    width="640" height="960">
  <source media="(min-width: 640px)"
    srcset="hero-landscape-1200.webp 1200w, hero-landscape-1920.webp 1920w"
    sizes="100vw">
  <img src="hero-landscape-1200.webp" alt="..."
       width="1200" height="630" loading="lazy" decoding="async">
</picture>
```

### Preventing CLS from Images (Critical)

```html
<!-- ✅ Always set width + height on img — browser reserves space before load -->
<img src="photo.webp" alt="..." width="800" height="600">

<!-- ✅ CSS aspect-ratio as backup (for when dimensions aren't known) -->
<style>
.img-container {
  aspect-ratio: 16 / 9;
  overflow: hidden;
}
.img-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>
```

---

## FONT PERFORMANCE

Fonts are the #2 cause of CLS and a major FCP blocker.

### The Waterfall Problem

Without optimization: HTML → parse → find font CSS link → fetch font CSS → parse → find .woff2 → fetch .woff2 → render text (3 round trips before text appears)

With optimization: HTML → [preconnect ready] → parse → [preload ready, font already downloading] → render immediately (0 extra trips)

### Complete Font Loading Pattern (Vanilla)

```html
<head>
  <!-- Step 1: Preconnect to font servers (do this FIRST in <head>) -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

  <!-- Step 2: Preload the most critical woff2 file -->
  <!-- To get the actual URL: open the Google Fonts CSS link in browser,
       find the @font-face for woff2, copy that URL -->
  <link rel="preload"
    href="https://fonts.gstatic.com/s/playfairdisplay/v37/nuFiD-vYSZviVYUb_rj3ij__anPXDTzYgEMmS-mDmA.woff2"
    as="font"
    type="font/woff2"
    crossorigin
  >
  <!-- Preload the body font too if it's serif (renders slower) -->

  <!-- Step 3: Non-blocking font CSS load -->
  <link rel="preload"
    href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700&family=Crimson+Pro:wght@400&display=swap"
    as="style"
    onload="this.onload=null;this.rel='stylesheet'"
  >
  <noscript>
    <link rel="stylesheet"
      href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700&family=Crimson+Pro:wght@400&display=swap">
  </noscript>

  <!-- Step 4: Inline critical font declarations as fallback -->
  <style>
    /* Immediately show text using system font while web font loads */
    :root {
      --font-display: 'Playfair Display', 'Playfair Display Fallback', Georgia, serif;
      --font-body: 'Crimson Pro', Georgia, serif;
    }
  </style>
</head>
```

### Size-Adjust Fallback — Eliminate Font CLS

This technique adjusts the system fallback font to match web font metrics exactly,
so when the web font swaps in, there's zero layout shift:

```css
/* Use https://screenspan.net/fallback to auto-generate these values */

@font-face {
  font-family: 'Playfair Display Fallback';
  src: local('Georgia'), local('Times New Roman');
  /* These values match Playfair Display's metrics */
  size-adjust: 97.5%;
  ascent-override: 103%;
  descent-override: 28%;
  line-gap-override: 0%;
}

@font-face {
  font-family: 'Crimson Pro Fallback';
  src: local('Georgia');
  size-adjust: 102%;
  ascent-override: 101%;
  descent-override: 26%;
  line-gap-override: 0%;
}

@font-face {
  font-family: 'DM Sans Fallback';
  src: local('Arial'), local('Helvetica Neue');
  size-adjust: 105%;
  ascent-override: 95%;
  descent-override: 25%;
  line-gap-override: 0%;
}

:root {
  --font-display: 'Playfair Display', 'Playfair Display Fallback', Georgia, serif;
  --font-body:    'Crimson Pro', 'Crimson Pro Fallback', Georgia, serif;
  --font-ui:      'DM Sans', 'DM Sans Fallback', Arial, sans-serif;
}
```

### Self-Hosting Fonts (Best for Performance)

```bash
# Download Google Fonts as self-hosted woff2
# Tool: https://gwfh.mranftl.com/fonts (Google Webfonts Helper)
# Or: npm install fontsource
```

```js
// npm/fontsource — zero external requests, tree-shakeable weights
import '@fontsource/playfair-display/700.css'       // only weight 700
import '@fontsource/playfair-display/700-italic.css' // italic weight 700
import '@fontsource/crimson-pro/400.css'
import '@fontsource/dm-sans/400.css'
import '@fontsource/dm-sans/500.css'
```

```css
/* Self-hosted @font-face — full control */
@font-face {
  font-family: 'Playfair Display';
  font-style: normal;
  font-weight: 700;
  font-display: swap;  /* never omit this */
  src: url('/fonts/playfair-display-700.woff2') format('woff2');
  unicode-range: U+0000-00FF, U+0131, U+0152-0153; /* Latin subset only */
}
```

### Next.js Font Optimization (Zero-Config Best Practice)

```ts
// next/font self-hosts, eliminates external font requests entirely
// Zero CLS: generates size-adjust fallback automatically
// Zero layout shift: font loads with page in same request

import { Playfair_Display, Crimson_Pro, DM_Sans } from 'next/font/google'

const displayFont = Playfair_Display({
  subsets: ['latin'],
  weight: ['400', '600', '700'],
  style: ['normal', 'italic'],
  display: 'swap',     // show fallback immediately, swap when ready
  preload: true,       // <link rel="preload"> for woff2
  variable: '--font-display',
  fallback: ['Georgia', 'Times New Roman'],
  adjustFontFallback: true,  // auto-generates size-adjust — eliminates CLS
})

// Local fonts (client's custom font files)
import localFont from 'next/font/local'
const brandFont = localFont({
  src: [
    { path: './fonts/brand-400.woff2', weight: '400', style: 'normal' },
    { path: './fonts/brand-700.woff2', weight: '700', style: 'normal' },
  ],
  display: 'swap',
  variable: '--font-display',
})
```

---

## CSS PERFORMANCE

### Critical CSS Inlining Strategy

```html
<head>
  <!-- Critical CSS: inlined — zero network request for above-fold render -->
  <style>
    /* Include ONLY what's needed for the initial viewport:
       - CSS variables / tokens
       - Reset / box-sizing
       - Body base styles
       - Navigation
       - Hero section
       - Skip any component that won't appear above the fold
    */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    :root {
      --color-bg: #0a0a0a; --color-text: #f0ece4; --color-accent: #d4a843;
      --font-display: 'Playfair Display', Georgia, serif;
      --font-ui: 'DM Sans', system-ui, sans-serif;
    }
    html { font-family: var(--font-ui); background: var(--color-bg); color: var(--color-text); }
    .nav { position: sticky; top: 0; display: flex; align-items: center; height: 64px; padding-inline: 1.5rem; }
    .hero { min-height: 100dvh; display: flex; align-items: center; padding: clamp(2rem, 8vw, 6rem); }
    h1 { font-family: var(--font-display); font-size: clamp(3rem, 8vw, 9rem); line-height: 1.0; }
  </style>

  <!-- Non-critical CSS deferred -->
  <link rel="preload" href="/css/main.css" as="style"
        onload="this.onload=null;this.rel='stylesheet'">
  <noscript><link rel="stylesheet" href="/css/main.css"></noscript>
</head>
```

### CSS Property Performance Tiers

```css
/* ── TIER 1: GPU-composited — zero layout, zero paint, 60fps guaranteed ─ */
/* Use ONLY these for animations */
transform: translateX() translateY() translateZ() scale() rotate() skew();
opacity: 0 → 1;
filter: blur() brightness() (when GPU-accelerated);

/* ── TIER 2: Paint-only — no layout, slight cost ──────────────────────── */
/* Acceptable for hover states, not for continuous animation */
color, background-color, border-color, box-shadow, outline;

/* ── TIER 3: Layout-triggering — causes full reflow ────────────────────── */
/* NEVER animate these. Use transform: scale() instead of width/height */
width, height, padding, margin, top, right, bottom, left,
font-size, line-height, border-width;
```

```css
/* ✅ Card hover — composited only */
.card {
  transition: transform 200ms cubic-bezier(0.34, 1.56, 0.64, 1),
              box-shadow 200ms ease;
}
.card:hover {
  transform: translateY(-4px) scale(1.01);
  box-shadow: 0 20px 40px rgba(0,0,0,0.3);
}

/* ❌ Never animate these — causes layout thrash */
.card:hover {
  width: calc(100% + 8px);  /* causes reflow */
  margin-top: -4px;          /* causes reflow */
}
```

### `contain` Property — Isolate Subtrees

```css
/* Tell browser this component is independent — skip recalculating rest of page */
.widget {
  contain: layout;    /* changes inside don't affect outside layout */
}
.card {
  contain: style;     /* CSS counters/properties don't escape */
}
.sidebar {
  contain: strict;    /* layout + style + size + paint — most isolated */
}

/* content-visibility skips rendering off-screen content entirely */
.below-fold-section {
  content-visibility: auto;
  contain-intrinsic-size: auto 500px;  /* placeholder size to prevent scroll jump */
}
```

### `@layer` — Specificity Control & Load Order

```css
/* Define layer order — later = higher priority */
@layer reset, base, components, utilities, overrides;

@layer reset {
  *, *::before, *::after { box-sizing: border-box; }
}
@layer base {
  html { font-family: var(--font-body); }
}
@layer components {
  .btn { /* component styles */ }
  .card { /* component styles */ }
}
@layer utilities {
  .sr-only { /* screen reader only */ }
}
/* Anything outside @layer has highest specificity by default */
```

---

## JAVASCRIPT PERFORMANCE

### Code Splitting — Ship Less per Route

```js
// ── React Router ──────────────────────────────────────────────────────
import { lazy, Suspense } from 'react'
import { Routes, Route } from 'react-router-dom'

const Home      = lazy(() => import('./pages/Home'))
const Dashboard = lazy(() => import('./pages/Dashboard'))
const Settings  = lazy(() => import('./pages/Settings'))

function App() {
  return (
    <Suspense fallback={<PageSkeleton />}>
      <Routes>
        <Route path="/"          element={<Home />} />
        <Route path="/dashboard" element={<Dashboard />} />
        <Route path="/settings"  element={<Settings />} />
      </Routes>
    </Suspense>
  )
}

// ── Next.js App Router (automatic code splitting per route) ───────────
// Each page.tsx in app/ is automatically a separate bundle
// No configuration needed

// ── Dynamic imports for heavy components ─────────────────────────────
const VideoPlayer  = lazy(() => import('./VideoPlayer'))  // don't load until needed
const PDFViewer    = lazy(() => import('./PDFViewer'))
const RichEditor   = lazy(() => import('./RichEditor'))
```

### Tree Shaking — Eliminate Dead Code

```js
// ── Your own modules ──────────────────────────────────────────────────
// ✅ Named exports — tree-shakeable
export function formatDate(date) { return ... }
export function formatCurrency(amount) { return ... }

// ❌ Default export object — not tree-shakeable
export default {
  formatDate: (date) => ...,
  formatCurrency: (amount) => ...,
}

// ── Third-party libraries ─────────────────────────────────────────────
// ✅ Import only what you use
import { format, parseISO }    from 'date-fns'
import { groupBy, sortBy }     from 'lodash-es'  // must use lodash-es not lodash
import { Search, Home }        from 'lucide-react'

// ❌ Default import — pulls entire library
import _ from 'lodash'
import * as LucideIcons from 'lucide-react'

// ✅ Verify your imports are actually tree-shaken
// Run: npx webpack-bundle-analyzer or vite-bundle-visualizer
// Look for unexpected large chunks
```

### Data Fetching — Avoid Waterfalls

```tsx
// ── React / Vanilla ───────────────────────────────────────────────────
// ❌ Sequential requests — total time = req1 + req2 + req3
const user    = await fetchUser(id)
const posts   = await fetchPosts(user.id)   // waits for user
const friends = await fetchFriends(user.id) // waits for user

// ✅ Parallel requests — total time = max(req1, req2, req3)
const [user, posts, friends] = await Promise.all([
  fetchUser(id),
  fetchPosts(id),    // starts immediately
  fetchFriends(id),  // starts immediately
])

// ── Next.js App Router — parallel data loading ────────────────────────
// app/dashboard/page.tsx
async function DashboardPage() {
  // These fire in parallel automatically because they're all initiated
  // before any await
  const userPromise    = getUser()
  const postsPromise   = getPosts()
  const metricsPromise = getMetrics()

  const [user, posts, metrics] = await Promise.all([
    userPromise, postsPromise, metricsPromise
  ])

  return <Dashboard user={user} posts={posts} metrics={metrics} />
}

// ── Next.js: fetch deduplication (built-in) ───────────────────────────
// Next.js deduplicates identical fetch() calls in same render cycle
// Both of these share ONE network request:
async function UserAvatar({ id }) {
  const user = await fetch(`/api/users/${id}`).then(r => r.json())
  return <img src={user.avatar} />
}
async function UserName({ id }) {
  const user = await fetch(`/api/users/${id}`).then(r => r.json()) // deduplicated
  return <span>{user.name}</span>
}
```

### React-Specific Optimizations

```tsx
// ── Prevent re-renders ────────────────────────────────────────────────
import { memo, useMemo, useCallback, useTransition, useDeferredValue } from 'react'

// memo: skip re-render if props are the same (shallow compare)
const ExpensiveCard = memo(function ExpensiveCard({ title, desc, imageUrl }) {
  return <div>...</div>
})

// useMemo: cache expensive computation
function SearchResults({ items, query }) {
  const filtered = useMemo(() =>
    items.filter(item =>
      item.title.toLowerCase().includes(query.toLowerCase())
    ),
    [items, query]  // only re-run when these change
  )
  return filtered.map(item => <ResultCard key={item.id} {...item} />)
}

// useCallback: stable function reference for memoized children
function Parent({ items }) {
  const handleDelete = useCallback((id: string) => {
    deleteItem(id)
  }, [])  // stable across re-renders

  return items.map(item =>
    <MemoizedChild key={item.id} onDelete={handleDelete} />
  )
}

// useTransition: mark updates as non-urgent — keeps UI responsive
function SearchPage() {
  const [query, setQuery] = useState('')
  const [results, setResults] = useState([])
  const [isPending, startTransition] = useTransition()

  const handleSearch = (e: React.ChangeEvent<HTMLInputElement>) => {
    setQuery(e.target.value)  // urgent — update input immediately
    startTransition(() => {
      setResults(heavySearch(e.target.value))  // non-urgent — can be deferred
    })
  }

  return (
    <>
      <input value={query} onChange={handleSearch} />
      {isPending ? <Spinner /> : <ResultsList results={results} />}
    </>
  )
}

// useDeferredValue: defer expensive re-render of child
function SearchPage({ query }) {
  const deferredQuery = useDeferredValue(query) // lags behind query intentionally
  return <ExpensiveList filter={deferredQuery} /> // re-renders at lower priority
}
```

**Virtualization for long lists:**
```tsx
import { useVirtualizer } from '@tanstack/react-virtual'

function VirtualList({ items }: { items: Item[] }) {
  const parentRef = useRef<HTMLDivElement>(null)

  const rowVirtualizer = useVirtualizer({
    count: items.length,
    getScrollElement: () => parentRef.current,
    estimateSize: () => 80,  // estimated row height in px
    overscan: 5,             // render 5 extra rows above/below viewport
  })

  return (
    <div ref={parentRef} style={{ height: '600px', overflow: 'auto' }}>
      <div style={{ height: `${rowVirtualizer.getTotalSize()}px`, position: 'relative' }}>
        {rowVirtualizer.getVirtualItems().map(virtualRow => (
          <div
            key={virtualRow.index}
            style={{
              position: 'absolute',
              top: 0,
              left: 0,
              width: '100%',
              height: `${virtualRow.size}px`,
              transform: `translateY(${virtualRow.start}px)`,
            }}
          >
            <ItemCard item={items[virtualRow.index]} />
          </div>
        ))}
      </div>
    </div>
  )
}
```

### Web Workers — Heavy Computation Off Main Thread

```js
// ── worker.js ────────────────────────────────────────────────────────
self.onmessage = ({ data }) => {
  const { type, payload } = data

  switch (type) {
    case 'FILTER':
      const result = payload.items.filter(heavyFilter)
      self.postMessage({ type: 'FILTER_DONE', result })
      break
    case 'SORT':
      const sorted = payload.items.sort(complexSort)
      self.postMessage({ type: 'SORT_DONE', result: sorted })
      break
  }
}

// ── main thread ───────────────────────────────────────────────────────
const worker = new Worker(new URL('./worker.js', import.meta.url))

worker.onmessage = ({ data }) => {
  if (data.type === 'FILTER_DONE') setItems(data.result)
}

// Send work to worker (off main thread — UI stays responsive)
function handleFilterChange(filter) {
  worker.postMessage({ type: 'FILTER', payload: { items, filter } })
}
```

---

## NEXT.JS SPECIFIC

### App Router Performance Patterns

```tsx
// ── Streaming with Suspense — show content progressively ─────────────
import { Suspense } from 'react'

export default function Page() {
  return (
    <main>
      {/* Renders immediately — static */}
      <HeroSection />

      {/* Streams in when ready — doesn't block hero */}
      <Suspense fallback={<CardGridSkeleton />}>
        <FeaturedPosts />  {/* async server component */}
      </Suspense>

      {/* Streams in independently */}
      <Suspense fallback={<ListSkeleton />}>
        <RecentActivity />
      </Suspense>
    </main>
  )
}

// ── Static vs Dynamic — choose the right rendering ───────────────────
// STATIC (default): rendered at build time, served from CDN — fastest
export default async function BlogPost({ params }) {
  const post = await getPost(params.slug)
  return <Article post={post} />
}
export function generateStaticParams() {
  return posts.map(post => ({ slug: post.slug }))
}

// DYNAMIC: rendered per request — for personalized/real-time content
export const dynamic = 'force-dynamic'  // or use cookies/headers in component

// REVALIDATE: ISR — regenerate every N seconds
export const revalidate = 3600  // regenerate every hour

// ── Partial Prerendering (PPR) — static shell + dynamic holes ────────
import { Suspense } from 'react'
// Static shell renders at build time
export default function Page() {
  return (
    <StaticLayout>
      {/* Dynamic hole — streams in per request */}
      <Suspense fallback={<Skeleton />}>
        <PersonalizedContent />
      </Suspense>
    </StaticLayout>
  )
}

// ── Route prefetching ─────────────────────────────────────────────────
import Link from 'next/link'
// Link prefetches the linked route when it enters viewport (default)
<Link href="/dashboard" prefetch={true}>Dashboard</Link>
// Disable for routes user unlikely to visit:
<Link href="/privacy-policy" prefetch={false}>Privacy</Link>
```

### Caching in Next.js App Router

```ts
// ── fetch() caching ───────────────────────────────────────────────────
// Static: cached indefinitely (ISR)
const data = await fetch('https://api.example.com/posts', {
  cache: 'force-cache'  // default for server components
})

// Dynamic: no cache
const user = await fetch('/api/me', {
  cache: 'no-store'     // always fresh, never cached
})

// Revalidate: refresh every N seconds (ISR)
const posts = await fetch('/api/posts', {
  next: { revalidate: 3600 }  // re-fetch after 1 hour
})

// Tag-based revalidation: purge specific cached data on demand
const product = await fetch(`/api/products/${id}`, {
  next: { tags: ['products', `product-${id}`] }
})
// In a Server Action or Route Handler:
import { revalidateTag } from 'next/cache'
revalidateTag('products')  // purge all 'products' tagged fetches

// ── React cache() — deduplicate server-side data fetching ────────────
import { cache } from 'react'

// Calling getUser(123) multiple times in same render = 1 DB query
export const getUser = cache(async (id: string) => {
  return db.user.findUnique({ where: { id } })
})
```

---

## VITE PERFORMANCE

```ts
// vite.config.ts — production optimizations
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
  build: {
    // Code splitting strategy
    rollupOptions: {
      output: {
        manualChunks: {
          // Separate vendor chunk — cached separately from app code
          vendor:  ['react', 'react-dom'],
          router:  ['react-router-dom'],
          ui:      ['@radix-ui/react-dialog', '@radix-ui/react-dropdown-menu'],
          icons:   ['lucide-react'],
          charts:  ['recharts'],
        },
      },
    },
    // Minification
    minify: 'terser',
    terserOptions: {
      compress: {
        drop_console: true,   // remove console.log in production
        drop_debugger: true,
      },
    },
    // Chunk size warnings
    chunkSizeWarningLimit: 500,  // warn if any chunk > 500KB
    // CSS code splitting
    cssCodeSplit: true,
    // Asset inlining threshold (inline assets < 4KB as base64)
    assetsInlineLimit: 4096,
  },
  // Dependency pre-bundling
  optimizeDeps: {
    include: ['react', 'react-dom', 'react-router-dom'],
  },
})
```

---

## CACHING HEADERS — Nginx / Vercel / Netlify

### Nginx Config
```nginx
# Immutable static assets (versioned filenames with content hash)
location ~* \.(js|css|woff2|woff|png|webp|avif|svg|ico)$ {
    expires 1y;
    add_header Cache-Control "public, max-age=31536000, immutable";
    add_header Vary "Accept-Encoding";
}

# HTML — always revalidate
location ~* \.html$ {
    expires 0;
    add_header Cache-Control "public, max-age=0, must-revalidate";
}

# API responses
location /api/ {
    add_header Cache-Control "private, max-age=0, no-store";
}
```

### Vercel (vercel.json)
```json
{
  "headers": [
    {
      "source": "/(.*)\\.(?:js|css|woff2|webp|avif|png|svg|ico)$",
      "headers": [
        { "key": "Cache-Control", "value": "public, max-age=31536000, immutable" }
      ]
    },
    {
      "source": "/",
      "headers": [
        { "key": "Cache-Control", "value": "public, max-age=0, must-revalidate" }
      ]
    }
  ]
}
```

### Netlify (netlify.toml)
```toml
[[headers]]
  for = "/*.js"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"

[[headers]]
  for = "/*.css"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"

[[headers]]
  for = "/*.woff2"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"

[[headers]]
  for = "/*.html"
  [headers.values]
    Cache-Control = "public, max-age=0, must-revalidate"
```

---

## SERVICE WORKER — Offline + Instant Repeat Visits

```js
// public/sw.js — basic cache-first strategy
const CACHE_VERSION = 'v3'
const STATIC_CACHE  = `static-${CACHE_VERSION}`
const DYNAMIC_CACHE = `dynamic-${CACHE_VERSION}`

const PRECACHE_ASSETS = [
  '/',
  '/offline.html',
  '/css/main.css',
  '/js/app.js',
  '/fonts/display.woff2',
  '/icons/icon-192.png',
]

// Install: precache critical assets
self.addEventListener('install', event => {
  event.waitUntil(
    caches.open(STATIC_CACHE)
      .then(cache => cache.addAll(PRECACHE_ASSETS))
      .then(() => self.skipWaiting())
  )
})

// Activate: clean old caches
self.addEventListener('activate', event => {
  event.waitUntil(
    caches.keys().then(keys =>
      Promise.all(
        keys
          .filter(key => key !== STATIC_CACHE && key !== DYNAMIC_CACHE)
          .map(key => caches.delete(key))
      )
    ).then(() => self.clients.claim())
  )
})

// Fetch: stale-while-revalidate for dynamic content
self.addEventListener('fetch', event => {
  const { request } = event
  const url = new URL(request.url)

  // Skip non-GET and non-same-origin
  if (request.method !== 'GET' || url.origin !== location.origin) return

  // HTML: network-first (fresh content)
  if (request.headers.get('accept')?.includes('text/html')) {
    event.respondWith(
      fetch(request)
        .then(response => {
          const clone = response.clone()
          caches.open(DYNAMIC_CACHE).then(cache => cache.put(request, clone))
          return response
        })
        .catch(() => caches.match('/offline.html'))
    )
    return
  }

  // Static assets: cache-first
  event.respondWith(
    caches.match(request).then(cached =>
      cached || fetch(request).then(response => {
        const clone = response.clone()
        caches.open(DYNAMIC_CACHE).then(cache => cache.put(request, clone))
        return response
      })
    )
  )
})
```

```html
<!-- Register service worker -->
<script>
  if ('serviceWorker' in navigator) {
    window.addEventListener('load', () => {
      navigator.serviceWorker.register('/sw.js')
        .then(reg => console.log('SW registered', reg.scope))
        .catch(err => console.error('SW registration failed', err))
    })
  }
</script>
```

---

## NETWORK PERFORMANCE

### HTTP/2 — Multiplexed Requests

With HTTP/2 (all modern hosts), multiple small files load faster than one large file.
This reverses the old HTTP/1.1 advice of "bundle everything":

```
HTTP/1.1: 6 parallel connections max → bundle JS/CSS → fewer requests
HTTP/2:   unlimited multiplexing → smaller chunks OK → better caching
```

Implication: code-split aggressively. Don't bundle everything just to reduce file count.

### Preloading Strategy

```html
<!-- Priority order: -->

<!-- 1. DNS-prefetch (cheapest — just resolve DNS) -->
<link rel="dns-prefetch" href="https://cdn.analytics.io">

<!-- 2. Preconnect (TCP + TLS handshake — ~300ms saved on first request) -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://cdn.yourapp.com" crossorigin>

<!-- 3. Preload (fetch AND cache specific resource NOW) -->
<!-- Use for: LCP image, critical font, critical CSS, critical JS -->
<link rel="preload" href="/fonts/display.woff2" as="font" type="font/woff2" crossorigin>
<link rel="preload" href="/images/hero.webp" as="image">
<link rel="preload" href="/css/critical.css" as="style">

<!-- 4. Prefetch (fetch during idle — for next navigation) -->
<link rel="prefetch" href="/dashboard">
<link rel="prefetch" href="/images/about-hero.webp" as="image">

<!-- 5. Prerender (full pre-render of next page — aggressive, use sparingly) -->
<link rel="prerender" href="/checkout">
```

---

## PERFORMANCE QUICK-WINS CHECKLIST

These are the 10 changes that together account for 80%+ of performance gains:

1. **Add `width` and `height` to every `<img>`** — eliminates CLS instantly
2. **Add `loading="lazy"` to below-fold images** — defers load cost
3. **Add `fetchpriority="high"` to LCP image** — improves LCP by 200–500ms
4. **Convert images to WebP** — 30–50% size reduction
5. **Add `display=swap` to font loading** — eliminates FOIT
6. **Add `size-adjust` fallback font** — eliminates font CLS
7. **Add `defer` to non-critical scripts** — unblocks HTML parsing
8. **Add `preconnect` for Google Fonts, CDN** — saves ~300ms per origin
9. **Add `preload` for LCP image and primary font** — starts fetch early
10. **Remove unused CSS** — use DevTools Coverage to find it, delete it
