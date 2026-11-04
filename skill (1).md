---
name: interactive-data-presentation-web-factory
description: Operational skill for building visually stunning, engaging, highly readable, and interactive data presentation websites featuring rich mouse/click animations, scrollytelling, dynamic charts, and modern editorial UI/UX.
version: 1.1.0
---

# Skill: Interactive Data Presentation Website Factory

## Objective & Core Philosophy
Develop high-impact, immersive, data-driven storytelling websites that transform raw metrics, reports, and analytical insights into compelling, human-centered web experiences.

The visual and interaction design takes inspiration from world-class editorial data graphics (such as *The New York Times Graphics*, *The Pudding*, *Bloomberg Green*, and *Stripe Press*).

### Core Design Ethos: "Editorial Elegance Meets Tactile Interactivity"
- **Narrative-First Approach:** Data is never presented as raw dumps; every chart tells a specific story node.
- **Scrollytelling Integration:** Visuals update gracefully as the user scrolls through the narrative.
- **Tactile Interactivity & Micro-Animations:** Every user movement (hover, point, click, scroll) yields immediate, fluid animation feedback.
- **Cognitive Clarity:** High visual contrast, scannable layouts, bold stat callouts, and progressive disclosure of complex data.

---

## Target Architecture & Technical Stack

### 1. Frontend & Motion Engine
- **Framework:** React / Next.js (TypeScript) or Vite + React for rapid lightweight deployments.
- **Styling & Layout:** Tailwind CSS with custom editorial typography scales, CSS Grid, and Flexbox layout systems.
- **Animation Engine:** **Framer Motion** for spring physics, layout animations (`layoutId`), scroll-triggered triggers, gestures (`whileHover`, `whileTap`), and DOM exit animations (`AnimatePresence`).
- **Cursor & Mouse Tracking:** Canvas/CSS mouse tracking primitives (e.g., custom magnetic cursor, radial spotlight background shaders).
- **Icons & Visual Accents:** Lucide-React icons, custom SVG annotations, and subtle glow/gradient accents.

### 2. Data Visualization Engine
- **Chart Libraries:** Recharts or Chart.js for clean standard visualizations (Bar, Line, Donut, Area, Radar) wrapped in interactive containers.
- **Custom / Complex Viz:** D3.js or SVG manipulation for specialized graphics (Sankey diagrams, Scrollytelling heatmaps, interactive timelines).
- **Interactivity Stack:** Interactive custom tooltips, metric toggle switches (e.g., YoY vs. QoQ, Absolute vs. Percentage), search/filter controls, and two-way hover highlights.

### 3. Page Structure & Key Modules
1. **Hero Header:** High-impact title, executive summary subtitle, estimated read time, key takeaway pill tags, and animated hero metric counter.
2. **Executive Summary / Quick Stats Grid:** 3–4 highlight KPI cards with animated count-up numbers, hover spotlight effects, and trend badges (+/- %).
3. **Scrollytelling Sections:** Sticky chart/graphic sidebar paired with scrollable narrative text blocks.
4. **Interactive Data Explorer:** Filterable data table/grid with hover highlight rows, search, pagination, and CSV export.
5. **Deep-Dive Metric Cards:** Expandable accordion panels or modal overlays with smooth click-to-expand morph animations.
6. **Footer & Data Provenance:** Citation list, source links, methodology disclaimer, and download buttons (PDF/Slide export).

---

## Interactive Motion & Mouse Feedback System (Hover, Point, Click & Animations)

To ensure the website is exceptionally engaging and responsive to user input, every component MUST incorporate rich mouse feedback and fluid motion:

### 1. Mouse Hover & Cursor Pointer Interactions (เมาส์เลื่อนผ่าน / เมาชี้)
- **Glow Spotlight Cards:** Cards feature a dynamic background radial gradient (`radial-gradient(circle at var(--mouse-x) var(--mouse-y), rgba(13, 148, 136, 0.15), transparent 80%)`) that follows cursor movement in real time.
- **Magnetic Buttons & Icons:** Interactive buttons and pill tags subtly drift toward the user's cursor when hovered (using Framer Motion spring physics).
- **Hover Scale & Elevation:** Stat cards and chart bars lift and scale (`whileHover={{ scale: 1.03, y: -4 }}`) with crisp drop shadows (`shadow-xl shadow-teal-500/10`).
- **Cursor-Attached Rich Tooltips:** Chart hover points render a floating glassmorphism tooltip (`backdrop-blur-md bg-slate-900/90`) that tracks the cursor smoothly without lag.
- **Two-Way Highlight Synchronization:** Hovering over a specific chart bar automatically highlights the related paragraph or bullet point in the narrative text, and vice versa.

### 2. Click & Gesture Animations (กดแล้วแสดงอนิเมชัน)
- **Fluid Layout Morphing:** Clicking metric toggle tabs (e.g., "Monthly" vs "Yearly") triggers a smooth layout morphing animation (`layoutId="activeTabIndicator"`) where the background pill slides seamlessly into place.
- **Expandable Card Morphing:** Clicking a summary card smoothly expands it into a detailed deep-dive overlay or modal using Framer Motion's `<AnimatePresence>` and `layout` transition (expanding width, height, and content seamlessly).
- **Chart Drill-Down Animations:** Clicking a chart data point smoothly animates the chart canvas, morphing into a detailed sub-category breakdown with staggered bar entrances.
- **Interactive Ripple & Tap Feedback:** All clickable elements feature tap scale feedback (`whileTap={{ scale: 0.96 }}`) and subtle CSS radial ripple animations upon click.

### 3. Scroll & Viewport Triggers
- **Staggered Entrance Animations:** As sections scroll into view, text blocks, badges, and cards animate in with staggered fade-and-rise effects (`initial={{ opacity: 0, y: 20 }}` -> `whileInView={{ opacity: 1, y: 0 }}`).
- **Interactive Progress Indicator:** A slim top progress bar tracks scroll percentage with an animated gradient.
- **Parallax Background Accents:** Subtle background grid dots or ambient glow spheres move at different speeds during scroll, creating visual depth.

---

## Storytelling & Engagement Rules (Making it Highly Readable & Captivating)

1. **Typography & Visual Hierarchy:**
   - Use high-contrast font pairs: A refined Editorial Serif font (e.g., *Playfair Display*, *Lora*, or *Merriweather*) for main headlines paired with a clean Sans-Serif (e.g., *Inter*, *Plus Jakarta Sans*) for body copy and data labels.
   - Maintain strict typographic scale: H1 (3.5rem+), H2 (2.25rem), Stat Highlights (3rem+ bold), Body (1.125rem with 1.7 line-height for effortless reading).

2. **Visual Pacing & Color System:**
   - **Color Palette:** Limit primary data palette to 3–4 thematic colors (e.g., Deep Slate `#0F172A`, Electric Teal `#0D9488`, Warm Gold `#D97706`, Soft Rose `#E11D48`). Use color strictly for semantic data encoding, not decoration.
   - **Dark Mode Support:** Provide an elegant dark theme option by default or toggle, enhancing visual pop for glowing animations and charts.

3. **Data Annotation & Scannability:**
   - Every major chart MUST feature a **Direct Annotation Callout** (e.g., an arrow or highlighted marker pointing to a peak, drop, or anomaly) with a 1-sentence narrative context.
   - Highlight key figures within body text using bold colored badges (e.g., `<span class="bg-teal-500/10 text-teal-600 px-2 py-0.5 rounded font-semibold">+34.2% Growth</span>`).

---

## User & AI Workflow (Division of Labor)

### Human Team Roles
- **Product Owner / Lead Editor:** Defines the overall narrative angle, provides raw dataset, approves visual styling, and verifies factual accuracy.
- **UI/UX & Motion Designer:** Curates color schemes, selects typography, and designs micro-interaction & animation specs.
- **QA & Data Auditor:** Cross-checks chart data against raw source files and tests responsiveness and animation performance across devices.

### AI Agent Specialization
- **Claude (Sonnet/Opus):** Core React component architecture, D3/Recharts implementation, Framer Motion scrollytelling & cursor interaction logic, and complex state management.
- **Codex:** Component refactoring, 60fps animation performance optimization (using GPU-accelerated transforms), accessibility (a11y) audits, and cross-browser testing.
- **GPT:** Editorial copywriting, headline sharpening, converting complex technical descriptions into punchy executive summaries.
- **Gemini:** Dataset structural analysis, JSON data transformation, reference benchmarking, and citation validation.

---

## Operating Rules & Guardrails

1. **Performance & Animation Smoothness (60 FPS Floor):**
   - All hover, click, and scroll animations MUST run at 60 FPS. Only animate GPU-friendly properties (`transform` and `opacity`). Never animate `width`, `height`, or `margin` directly during continuous scroll/hover.
   - Zero Layout Shift (CLS): All charts must have explicit responsive aspect ratios (`Aspect-Ratio` or container wrappers).
   - Mobile First Optimization: Touch devices must replace hover spotlight triggers with intuitive tap states and touch-friendly gestures.

2. **Code & Quality Standards:**
   - Keep chart components modular and declarative (separate raw data JSON from visualization markup).
   - Ensure color contrast ratios meet WCAG AA standards (4.5:1 for body text).

3. **Permission Boundaries:**
   - Always seek explicit approval before altering the underlying data values or changing the core narrative structure.
   - Never introduce heavy unapproved 3D canvas libraries (e.g., Three.js) if lightweight 2D Framer Motion / SVG solutions suffice.

4. **Session Handoff Protocol:**
   - If the AI session token budget is low, generate a `HANDOFF_SUMMARY.md` documenting:
     1. Components & animation states completed.
     2. Data state structures implemented.
     3. Next immediate layout, chart, or interaction tasks for the following session.

---

## Phased Implementation Roadmap

### Phase 1 — Project Setup & Data Transformation
- [ ] Initialize React/Next.js environment with Tailwind CSS & Framer Motion.
- [ ] Clean and transform raw input data into structured JSON format (`data/metrics.json`).
- [ ] Define global color palette, typography tokens, and responsive layout primitives.

### Phase 2 — Interactive Hero Header & Executive Stat Cards
- [ ] Build high-impact Hero Header with title, estimated reading time, and executive tags.
- [ ] Implement Executive Stat Cards with animated number count-ups (`framer-motion` / `useInView`) and cursor spotlight tracking.

### Phase 3 — Scrollytelling Engine & Interactive Motion System
- [ ] Implement sticky layout split (Narrative Scroll Column + Sticky Visual Container).
- [ ] Build interactive chart components (Recharts / D3) with hover tracking, custom glassmorphism tooltips, and direct callout annotations.
- [ ] Implement two-way hover synchronization between text highlights and chart elements.
- [ ] Add click-to-morph tab toggles and drill-down dataset transitions.

### Phase 4 — Data Explorer & Deep-Dive Expansion Cards
- [ ] Build filterable Data Explorer grid (Search, Category Filter, Sorting) with row hover feedback.
- [ ] Add click-to-expand accordion sections and modal overlays for methodology breakdowns.

### Phase 5 — Polishing, Performance Audit & Build Output
- [ ] Audit 60fps animation performance, touch interactions, and WCAG AA contrast.
- [ ] Add dark mode toggle, animated scroll progress bar, and reading indicator.
- [ ] Perform build verification and export preview.