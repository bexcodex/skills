---
name: antislop-ui
description: Prevent, detect, and remove generic "AI slop" from UI/UX design and frontend output. Use whenever generates, critiques, redesigns, or implements websites, landing pages, dashboards, mobile apps, design systems, components, forms, navigation, data visualizations, CSS, Tailwind, React, HTML, or other interfaces that risk looking template-like, over-decorated, trend-chasing, synthetic, or obviously AI-generated. Enforce product-specific hierarchy, composition, density, typography, color, surfaces, cards, containers, imagery, motion, states, responsiveness, accessibility, and implementation discipline. Always run a final anti-slop audit before delivery.
---

# Antislop UI

Design interfaces that feel authored rather than statistically averaged.

Do not interpret "anti-slop" as "make everything minimal." A dense financial terminal can be excellent. A playful consumer app can be excellent. A highly animated creative site can be excellent. A glass-heavy spatial interface can be excellent. The failure is not any specific aesthetic. The failure is using the same fashionable visual recipe regardless of product, audience, content, task, or platform.

Treat every visual decision as something that must earn its place. If a card, gradient, glow, border, badge, animation, oversized heading, icon bubble, or unusual layout cannot be traced to product meaning, information hierarchy, interaction state, brand character, or platform behavior, treat it as suspect decoration.

The goal is specificity, coherence, and useful character. Make the interface look like it belongs to this exact product rather than to an anonymous design-generation demo.

## Understand the actual failure mode

AI-generated UI tends to converge because some patterns are easy to combine, broadly represented in training data, visually impressive in static screenshots, and unlikely to look obviously broken. This produces interfaces that are superficially polished but structurally generic.

A typical marketing-page failure combines a centered hero, eyebrow badge, oversized heading, gray supporting paragraph, two pill buttons, purple-blue gradient, glowing dashboard mockup, abstract blobs, three equal feature cards, pastel icon circles, giant border radii, and repeated full-width sections with identical spacing. A typical dashboard failure turns every metric into a card, every card into a rounded rectangle, every icon into a colored circle, every section into another container, and every hover into a small lift animation. Other high-frequency signals include generic bento grids, gradient text, decorative dot or grid backgrounds, stars and sparkles, mesh gradients, low-contrast gray-on-gray copy, fake metrics that conveniently fit their boxes, and utility clusters such as `rounded-2xl shadow-xl backdrop-blur bg-gradient-to-*`. When three or more unrelated default signals accumulate in one viewport, assume the design is drifting toward slop and deliberately simplify or recompose it.

None of those elements is automatically wrong. The slop appears through unearned accumulation. A single gradient can be appropriate. A card grid can be appropriate. Large radius can be appropriate. The interface becomes generic when several default moves are combined without one coherent product-specific idea.

Do not solve emptiness by adding decoration. Solve hierarchy, proportion, rhythm, information architecture, content realism, and interaction behavior first. Only then add expressive styling.

## Use a fixed reasoning workflow

Before designing or redesigning, establish the product logic. Infer the primary user, primary task, screen purpose, platform, expected usage frequency, information density, trust requirement, content type, repeated objects, primary action, secondary actions, and important states. Do this from the prompt when possible rather than asking unnecessary questions.

Then form one internal design thesis. Make it concrete enough to control later decisions. Use the pattern: `[product] should feel [precise traits] because [user/task reason], expressed through [layout/type/color/surface/motion strategy].`

For example: "This finance operations screen should feel compact, calm, and dependable because users scan it all day, expressed through tight alignment, tabular numerals, restrained neutrals, low radius, and color reserved for status." A music discovery product might instead require image-led asymmetry, expressive typography, varied section rhythm, and quiet interface chrome.

Do not use vague words such as "modern", "clean", "premium", "beautiful", or "sleek" as the thesis. Those words do not tell the model what to draw or what to remove.

After defining the thesis, identify the strongest slop risks for this specific interface. Separate structural problems from decorative problems. Fix structure first: information order, grouping, layout, density, hierarchy, navigation, action priority. Fix visual language second: typography, color, radius, borders, shadows, media treatment. Add motion and special effects last.

When redesigning, prefer subtraction before addition. Remove unnecessary effects, flatten unnecessary containers, normalize inconsistent radii, reduce repeated accent color, remove decorative icon bubbles, replace generic copy, and make the interface remain understandable without the visual shell. Then rebuild character deliberately.

## Recognize slop by product type

Do not assume AI slop looks identical across products. Detect the characteristic failure mode of the product category.

For SaaS marketing pages, the common failure is theatrical sameness: centered hero, generic promise, gradient text, floating product mockup, three-card features, logo strip, testimonial cards, pricing cards, and CTA band. Break this pattern by letting the product story dictate section form. A capability may be better shown through an annotated screenshot, workflow sequence, comparison, evidence table, customer example, or one large concrete claim instead of another feature grid.

For dashboards and admin tools, the common failure is cardification. AI often mistakes "organized" for "everything in a bordered rounded surface." Prefer tables, rows, grouped metrics, aligned labels, inline controls, dividers, and direct typography. Reserve cards for actual independent modules or objects.

For developer tools, the common failure is automatic futurism: black backgrounds, cyan or purple accents, code snippets in glowing cards, grid textures, monospace everywhere, and neon borders. Developer products often benefit more from compact controls, clear hierarchy, predictable navigation, keyboard affordances, readable code surfaces, and sparse accent usage.

For fintech, healthcare, security, legal, or enterprise software, the common failure is visual softness that undermines trust or scan speed. Do not let pale gray text, giant rounded cards, playful gradients, ambiguous icons, or low-information hero treatments weaken clarity. Use strong semantic states, explicit labels, legible contrast, and disciplined density.

For consumer and social products, the common failure is generic friendliness: oversized radius, pastel surfaces, excessive emoji-like icons, identical feed cards, and springy motion everywhere. Let actual content, identity, media, and social behavior create personality instead of decorating the chrome.

For commerce, the common failure is turning products into uniform UI cards while suppressing the merchandise. Let photography, product information, price, availability, size/color choices, comparison, and purchase confidence dominate. Decorative interface treatments should not compete with the thing being sold.

For editorial, portfolio, fashion, art, and brand experiences, the common failure is the opposite: AI often imposes standard SaaS structure on content that needs pacing and art direction. Use type, imagery, cropping, sequencing, negative space, and rhythm as primary composition tools. Do not force every idea into a reusable component grid.

For mobile apps, the common failure is desktop thinking squeezed into a narrow viewport. Avoid miniature desktop sidebars, tiny controls, stacked cards copied from desktop, hover assumptions, and excessive vertical padding. Recompose the task around touch, reachability, navigation depth, keyboard appearance, sheets, tabs, and transient states.

## Make hierarchy exist before containers

Treat visual hierarchy as the foundation. A screen should still make sense when shadows, gradients, glows, and decorative backgrounds are disabled.

Express relationships first through proximity, alignment, type scale, emphasis, indentation, ordering, and whitespace. Add a divider when those are insufficient. Add surface contrast when a region needs stronger grouping. Add a border when the boundary matters. Add a card only when the content behaves like a bounded object. Add elevation only when something is actually elevated or overlapping.

A card is justified when the content is independently selectable, movable, stateful, repeatable as an entity, dismissible, expandable, draggable, or meaningfully separated from surrounding content. A static heading and paragraph do not automatically need a card. A metric does not automatically need a card. A form section does not automatically need a card.

If a rectangle can disappear without reducing comprehension, remove it.

Be especially suspicious of container-inside-container patterns. A page surface containing a rounded panel containing smaller rounded cards containing rounded badges or icon bubbles creates the unmistakable AI-dashboard look. Inside an existing surface, prefer rows, subheadings, spacing, indentation, separators, or subtle tonal changes before nesting another box.

Keep surface hierarchy shallow. In many products, canvas, base surface, and raised/floating surface are enough. Do not invent many nearly indistinguishable gray layers merely to create visual complexity.

## Compose around the shape of information

Do not begin from a component gallery or from the assumption that every page needs a twelve-column grid. Identify the dominant relationship in the content.

If users need comparison, align comparable attributes. If users need status scanning, use repeated rows or a table. If users need storytelling, vary composition and image scale. If users need command and control, use stable zones and predictable alignment. If users need discovery, let content diversity affect rhythm. If users need a sequence, show sequence rather than three unrelated cards.

Avoid repetitive section grammar. A page that repeats `heading + paragraph + three equal cards` three times feels generated even if each section is individually polished. Change the composition when the information changes. Evidence can become a table. A workflow can become a sequence. A capability can be shown in the product itself. A comparison can use aligned rows. A major proposition can stand alone.

Use asymmetry when it creates hierarchy, character, or useful tension. Unequal columns, offset media, anchored metadata, changing section depth, and deliberate negative space can make a composition feel authored. Do not use asymmetry simply to look different; scanning must remain clear.

Treat whitespace as structure, not unfinished area. Do not fill every open region with blobs, stars, sparkles, grids, random circles, floating icons, abstract waves, or mesh gradients.

## Control density and spacing rhythm

Choose density according to task frequency and information load. Operational products used for hours each day usually need shorter vertical travel, more compact controls, stronger alignment, and less theatrical whitespace. Editorial, premium commerce, portfolios, and storytelling experiences can support more breathing room because pacing and imagery matter more than throughput.

Use a spacing system without making the page robotic. A scale such as `4, 8, 12, 16, 24, 32, 48, 64` is reasonable, but choose steps according to semantic relationship. A label should sit closer to its control than one section sits to another. Related rows should feel grouped. Major sections should not all receive identical top and bottom padding.

Avoid the generated look produced by `gap-6` everywhere, identical `p-6` cards, and repeated `py-24` sections. Consistency means a coherent vocabulary, not one spacing value repeated mechanically. As a useful starting relationship, keep label-to-control gaps around 6–8px, icon-to-label gaps around 6–10px, title-to-supporting-copy gaps around 8–12px, related-row spacing around 8–16px, internal card groups around 16–24px, and major section separation around 32–64px depending on density. Treat these as relational guidance rather than fixed laws.

Keep reading measure under control. Body text usually benefits from roughly 45–80 characters per line. Tables, code, charts, timelines, and structured data can use wider regions. Do not center a tiny text column inside a giant canvas just because large margins look expensive.

## Use typography as structure

Make typography carry enough hierarchy that containers do less work. Differentiate page title, section title, object title, body, labels, metadata, and numeric information using an intentional combination of size, weight, line height, width, tone, alignment, and spacing.

Do not make every text role 14–16px with weight changes only. Do not make every heading enormous. Oversized display type should correspond to importance, pacing, or brand character. Dense applications generally need more compact type than marketing pages.

Do not choose Inter automatically. A system UI font may be the right decision for an application because of familiarity and performance. A distinctive display face may be right for editorial or brand work. Choose based on product character, not on what most generated interfaces use.

Avoid bold-everything hierarchy. Reserve strong weight for genuine emphasis. For dashboards and finance, consider tabular numerals where numeric alignment matters. For long reading, use comfortable line height. For display headings, tighter leading may be appropriate.

Do not simulate elegance with faint text. Muted text may be lower priority but must remain legible.

## Give color a job

Do not default to cool gray plus electric purple, cyan, or blue. That palette is not banned; it is simply too common to use without a contextual reason.

Build a neutral foundation first, then decide where chroma earns attention. Use semantic roles such as canvas, base surface, raised surface, primary text, secondary text, muted text, subtle border, strong border, accent, accent-hover, success, warning, danger, and information. This creates a system instead of a pile of arbitrary hex values.

Concentrate accent color. Use it for interaction, selection, important data, brand anchors, or meaningful state. When every icon, title, border, metric, button, badge, and illustration uses the accent, nothing is emphasized.

Choose palette temperature from product context. Finance or healthcare may need restrained neutrals and precise semantic colors. Food may benefit from warmth. Creative software may support broader chroma. Luxury commerce may let photography carry most color while interface chrome stays quiet.

Use gradients only when they belong to the brand, encode a real transition, support meaningful depth, or serve a deliberate art direction. Ask whether a solid color would communicate equally well. If yes, prefer the solid unless the gradient itself is part of the concept.

Do not stack gradient background, gradient text, gradient borders, gradient buttons, and glow in the same viewport unless the entire visual identity is explicitly built around that language.

In dark mode, do not default to pure black plus neon. Use layered dark neutrals, luminance, restrained borders, and spacing to create depth. Avoid luminous colored shadows unless they communicate a strong brand or state.

Maintain accessible contrast. As a practical baseline, target WCAG AA where applicable: 4.5:1 for normal text, 3:1 for large text, and 3:1 for meaningful non-text UI boundaries or icons where required.

## Treat radius, borders, shadows, glass, pills, badges, and icons as materials

Choose a radius family that matches the product. A utilitarian interface may work around 4–8px. A friendly consumer product may use 8–16px. A soft expressive brand may use larger values selectively. Do not turn every surface, image, input, button, navigation item, badge, and modal into `rounded-2xl` or a capsule.

Use borders where boundaries matter and contrast alone is insufficient. Avoid borders on every nested region. Avoid colored borders unless they represent state, selection, severity, or a deliberate visual identity.

Use shadows to communicate elevation, overlap, drag state, menus, popovers, dialogs, or floating controls. Static sections usually do not need them. A shadow added only to make a rectangle feel "premium" is usually decorative debt.

Use glass only when translucency explains layering over meaningful content such as a map, canvas, image, or spatial scene. A translucent card on top of a decorative purple gradient usually has no structural reason to exist. Keep glass contrast strong and material behavior consistent.

Use pills for tags, filters, status chips, segmented controls, compact categories, or other naturally capsule-like objects. Do not make pills the universal shape of the interface.

Use badges only for compact metadata or state that benefits from categorical scanning. Do not badge ordinary nouns merely to fill space.

Use icons when they improve recognition, scanning, spatial economy, or action comprehension. Keep one coherent icon family. For ordinary interface work, roughly 16px suits dense metadata and actions, 20px suits compact controls, 24px suits standard controls or navigation, and 28–32px should be reserved for genuinely emphasized iconography. Do not enlarge icons merely to fill empty space. Do not put every icon inside a pastel circle. Do not mix outline, filled, 3D, emoji, and hand-drawn icons without an explicit system. Ambiguous icons need labels.

## Design navigation as orientation, not decoration

Make navigation reveal product structure and current location. Do not automatically create a floating rounded navbar because it looks polished in a hero screenshot. Do not use capsule tabs everywhere. Do not hide important destinations inside a hamburger on desktop simply to make the header sparse.

For desktop applications, prioritize persistent orientation, efficient switching, compact navigation density, keyboard support where relevant, and visible active state. For marketing sites, keep navigation subordinate to the story but clear. For mobile, choose patterns that fit destination count, hierarchy, reachability, and platform conventions rather than shrinking desktop navigation.

Use sidebars when persistent multi-level navigation is genuinely useful. Use tabs when users switch among sibling views. Use breadcrumbs when hierarchy matters. Use command palettes for expert shortcuts, not as replacements for understandable information architecture.

Avoid redundant navigation layers. A sidebar, top nav, subnav, tab bar, segmented control, and breadcrumb all on one screen usually indicate unresolved structure unless the product is unusually complex.

## Make forms look like tasks, not component showcases

Design forms around the user decision flow. Group fields by meaning, not by equal card sizes. Use clear labels, useful helper text, and validation near the field it affects. Avoid placeholder-only labels. Do not place every field inside a large rounded card or decorate every field with an icon.

Choose one-column or multi-column form layout based on dependency and scanning, not on visual symmetry. Short, related fields can share a row when this improves efficiency. Long or cognitively heavy fields usually deserve their own width.

Make required, optional, error, success, disabled, read-only, and loading states visually distinct. Do not rely on red borders alone for errors. Explain what failed and how to fix it.

Keep action hierarchy explicit. One local primary action is usually enough. Do not place several equally loud buttons at the bottom of a form. Destructive actions should be distinct but need not dominate the entire screen with red.

## Treat tables and data visualization as information systems

Do not turn every dataset into decorative metric cards. Use tables when exact values, scanning, sorting, or comparison matter. Use charts when shape, trend, distribution, relationship, or change is the important message.

Choose a visualization based on the question, not on which chart looks impressive. Avoid unnecessary 3D, gradients, shadows, rounded bar ends everywhere, excessive color, or animated entrance sequences that make the chart feel like a demo. Keep gridlines, labels, legends, and annotations only when they help reading.

Use color semantically and sparingly. Do not assign a different bright color to every series if position, labeling, or direct annotation can do the work. Highlight what matters and quiet the rest.

For dashboards, build a visual hierarchy among summary, trend, exception, detail, and action. Do not give every metric equal card size and equal emphasis. A key anomaly may deserve more visual weight than six routine KPIs.

For dense tables, prioritize column alignment, readable headers, row scanning, selection, sorting, filters, pinned context, and responsive behavior. Do not add icons to every header or shadow every row.

## Use imagery and art direction purposefully

Do not invent abstract blobs, random 3D objects, fake device renders, or synthetic dashboards because a hero "needs an image." A strong layout can be typographic when no meaningful visual exists.

Prefer media that explains or embodies the product: real screenshots, real data visualization, product-specific diagrams, authentic photography, meaningful illustration, workflow previews, before/after comparisons, or content created inside the product.

Treat crop, scale, repetition, framing, and image rhythm as part of the visual language. If photography is the main source of personality, keep UI chrome quiet enough to support it. If illustration is used, define a coherent illustration system rather than mixing several internet-friendly styles.

Avoid the AI habit of placing every screenshot inside a floating rounded browser frame with large shadow and glow. Show the product in the framing that best communicates it. Sometimes that is a crop, annotated detail, full-bleed capture, stacked workflow, or no frame at all.

## Make motion explain change

Use motion to explain where something came from, where it went, what changed, what is interactive, whether an action succeeded, or what currently requires attention. If removing the animation leaves understanding unchanged, question whether it belongs.

Keep most routine motion quick. Micro feedback often works around 100–180ms, common state transitions around 160–260ms, and dialogs or panels around 180–320ms. Larger spatial transitions can extend toward roughly 400ms when the movement itself communicates structure. Do not make ordinary controls spend 600–1200ms performing theater.

Prefer natural ease-out for entrances and ease-in-out for reversible transitions. Avoid bounce, elastic overshoot, exaggerated springs, or scale effects unless the product character genuinely supports playful motion.

Do not animate every card on hover. For a clickable card, one restrained signal such as a subtle background shift, border change, small elevation change, or minimal translate is usually enough. Do not combine translate, scale, glow, shadow, and border animation simultaneously.

Avoid looping decorative motion such as animated gradients, floating blobs, marquees, typewriter cursors, bouncing arrows, shimmer, parallax, or endlessly moving backgrounds unless the concept strongly depends on them.

In code, prefer `transform` and `opacity` where appropriate and avoid `transition-all`. Respect `prefers-reduced-motion` and remove nonessential animation when reduced motion is requested.

## Use realistic content to expose weak design

Generic copy produces generic layout. Avoid phrases such as "Unlock your potential", "Supercharge your workflow", "Seamlessly manage everything", "Powerful insights at your fingertips", or "Revolutionize the way you work" unless they are actually supplied brand copy.

Write concrete interface copy that reveals the task. "See which invoices are overdue and contact the client without leaving the page" creates a real design problem. "Boost productivity with powerful insights" does not.

Use realistic names, dates, amounts, statuses, labels, message lengths, table values, and edge cases. Include long labels and imperfect content where appropriate. Do not engineer fake data merely to keep every card the same height.

Account for loading, empty, error, success, disabled, selected, hover, pressed, and focus states when they matter. A beautiful default-state screenshot is not a complete interface.

## Recompose responsively instead of shrinking

Treat responsive design as recomposition. Reconsider hierarchy, ordering, navigation, visibility, density, tables, media crop, sticky controls, and action placement at meaningful breakpoints.

Do not keep a desktop three-column card grid and simply make the cards narrower. Do not convert every table to stacked cards automatically. A table may need horizontal preservation, selective columns, disclosure, or a purpose-built summary. Secondary content may move, collapse, or become on-demand.

Choose breakpoints based on content pressure rather than only on framework defaults. Preserve readable margins and reachable primary actions. On mobile, account for touch targets, virtual keyboard, bottom sheets, safe areas, thumb reach, and platform navigation behavior when relevant.

For touch interfaces, aim for roughly 44x44 CSS pixels/points for important targets where practical. Do not rely on hover to reveal essential functionality.

## Treat accessibility as visual quality

Do not trade legibility or operability for subtle aesthetics. Use semantic structure, meaningful labels, visible keyboard focus, appropriate touch targets, accessible names for icon-only controls, useful alt text, and non-color cues for important state.

Do not hide focus outlines without replacing them. Do not communicate error, success, warning, or selection through color alone. Do not use tiny gray text because it makes a screenshot look refined.

Accessibility failures are not minor polish issues. If important text cannot be read, state cannot be understood, controls cannot be reached, or motion cannot be reduced, the design is structurally weak.

## Preserve platform coherence

Use platform conventions as constraints, not as obstacles. Native-feeling mobile UI should use familiar navigation, expected sheets and dialogs, platform-appropriate touch sizes, and no web-only hover assumptions. Desktop productivity UI should support scan speed, compact repeated controls, keyboard use, shortcuts, and stable spatial organization where relevant.

Marketing pages should prioritize narrative flow and content differentiation. Editorial experiences should prioritize reading and media rhythm. Command interfaces should prioritize efficiency. Do not create a cross-platform hybrid that ignores all conventions unless the user explicitly wants a novel interaction model.

## Encode the reasoning in frontend code

When generating HTML, CSS, React, Tailwind, or similar code, do not merely explain these rules. Make the implementation reflect them.

Treat repeated utility clusters such as `rounded-2xl shadow-xl border bg-white/80 backdrop-blur`, `bg-gradient-to-r from-purple-* to-blue-*`, `text-transparent bg-clip-text bg-gradient-to-r`, `hover:-translate-y-1 hover:shadow-2xl transition-all`, repeated `grid md:grid-cols-3 gap-8`, or universal `inline-flex rounded-full` controls as warning signs. They are allowed only when the design thesis justifies them.

Define reusable tokens for color, typography, spacing, radius, elevation, transition timing, and container width. Avoid arbitrary one-off values unless a deliberate compositional exception requires them.

Implement states rather than polishing only the default view. Include `focus-visible` and disabled behavior whenever applicable, and include hover, pressed, selected, loading, empty, and error states when relevant.

Avoid unnecessary component abstraction. Do not create a universal `Card` component and then force unrelated information into it. Build components around recurring semantic patterns, not around the desire to reuse one rounded rectangle everywhere.

## Use concrete transformation logic

When a generic SaaS hero appears, do not simply recolor it. Replace vague headline copy with a concrete promise. Reconsider alignment. Reduce competing CTAs. Replace the glowing fake dashboard with a real product view, a useful crop, a diagram, or no media. Remove decorative blobs unless they are part of brand art direction.

When a dashboard is card-heavy, flatten the least meaningful cards. Group summary values into a strip or aligned region. Use tables or rows for repeatable data. Keep cards for independent modules. Remove decorative icon circles and shadows. Let typography, alignment, and semantic color carry more hierarchy.

When a feature section is three equal icon cards, inspect the actual content. A workflow may become steps. A comparison may become aligned rows. A product capability may become an annotated screenshot. Evidence may become metrics or a customer example. Do not preserve three equal boxes just because the content happens to have three headings.

When a dark interface looks "futuristic" through black, cyan, purple, glow, glass, and grid texture, rebuild depth with layered neutrals, restrained borders, selective accent, solid surfaces, and readable luminance. Reintroduce glow or glass only if the product concept genuinely needs them.

When an interface is overanimated, keep motion on state changes and remove background performance. Reduce hover behavior to one clear signal. Do not make every interaction announce itself with scale and glow.

## Build distinctiveness from a small number of coherent moves

Do not confuse originality with visual novelty. A product can become recognizable through one or two disciplined ideas repeated consistently.

A signature may come from editorial type scale, unusual but usable navigation composition, product-specific data visualization, a strong image-cropping system, characteristic density, meaningful color coding, a branded illustration language, a recognizable geometric motif used sparingly, or an interaction pattern that emerges from the product itself.

Choose very few signature moves. Repetition builds identity; accumulation builds noise. Do not combine asymmetry, glass, oversized type, mesh gradients, animated backgrounds, floating shapes, experimental navigation, and 3D illustration just to avoid looking generic.

Distinctiveness must survive the removal of decorative effects. If the interface only feels unique because of a background gradient or glow, it is not structurally distinctive yet.

## Distinguish "generic but correct" from "forced originality"

Do not redesign familiar patterns merely because they are common. A standard search field, checkbox, table, tab bar, breadcrumb, modal, form label, or settings list is often correct precisely because users already understand it.

The anti-slop goal applies most strongly to composition, hierarchy, visual language, content treatment, and unnecessary ornament. Preserve conventional interaction patterns when convention improves usability.

Do not create unusual navigation, unconventional controls, or asymmetry solely to prove that the design is original. A familiar control in a specific, well-composed product is better than a novel control that adds cognitive load.

When choosing between generic correctness and novelty, protect comprehension first. Add character where it does not make the task harder.

## Run the final anti-slop audit silently

Before delivery, remove the logo and imagine the copy replaced with placeholders. Ask whether the remaining composition could belong to almost any startup template. If yes, revise until the layout, density, media treatment, or interaction structure reflects the product more specifically.

Check whether hierarchy survives without gradients, shadows, glow, or glass. If not, rebuild hierarchy. Check whether every visible rectangle corresponds to a real content boundary. If not, flatten surfaces. Check whether strong chroma still functions as emphasis. If it appears everywhere, reduce it.

Check whether section composition changes when information changes. If every section uses the same grid, same card proportions, same spacing, and same weight, redesign the rhythm. Check whether copy and data reveal the real product. If the interface depends on vague marketing text or perfectly balanced fake data, replace them.

Check navigation, forms, tables, charts, responsive behavior, loading, empty, error, disabled, selected, and focus states where applicable. Static polish does not compensate for missing product behavior.

Score the result mentally from 0 to 2 across context specificity, information hierarchy, composition, spacing rhythm, typography, color discipline, surface discipline, component coherence, interaction clarity, motion purpose, content realism, responsive adaptation, accessibility, platform fit, and visual distinctiveness. Use 0 for generic or poor, 1 for acceptable, and 2 for deliberate or strong. Aim for at least 24/30. Treat hierarchy, accessibility, responsive behavior, content realism, and context specificity as hard gates: if any of those scores 0, revise before delivery even if the total score is otherwise high.

Do not consider the work complete when it still contains an unjustified generic gradient hero, glass as default material, cards around nearly all content, repeated icon-card feature grids, meaningless nested rounded rectangles, inaccessible low-contrast text, several equally prominent primary actions, arbitrary glow, decorative looping animation, desktop-only responsive logic, fake content that hides layout problems, inaccessible focus states, or major style decisions that cannot be explained by product context.

## Output behavior

Prioritize the requested artifact over explaining this doctrine. Do not repeatedly mention "AI slop" unless the user explicitly asks for diagnosis or critique.

Make decisive design choices instead of dumping a large menu of styles. Explain rationale only where it helps the user understand an important tradeoff.

Preserve the user's framework, brand constraints, established design system, and platform requirements unless the task explicitly asks for a redesign. Do not make an existing product visually different merely for the sake of novelty.

If the user explicitly asks for gradients, glass, neon, huge radius, bento layouts, playful motion, or another style commonly associated with generated UI, honor the direction. Execute it coherently, remove accidental repetition, keep hierarchy strong, and make the style belong to the product rather than fighting the user's request.

The goal is not minimalism. The goal is intentionality. A colorful interface can be excellent. A brutalist interface can be excellent. A dense dashboard can be excellent. A playful app can be excellent. A glass interface can be excellent. What must disappear is unearned styling, template repetition, vague hierarchy, fake polish, and decorative decisions that exist only because an AI commonly generates them.
