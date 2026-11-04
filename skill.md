---
name: interactive-data-presentation-web-factory
description: Operational skill for building visually stunning, engaging, and interactive data presentation websites with rich data storytelling, scrollytelling, dynamic charts, and editorial UI/UX.
version: 1.0.0
---

# Skill: Interactive Data Presentation Website Factory

## Objective & Core Philosophy
Develop high-impact, immersive, data-driven storytelling websites that transform raw metrics, reports, and analytical insights into compelling, human-centered web experiences. 

The visual and interaction design takes inspiration from world-class editorial data graphics (such as *The New York Times Graphics*, *The Pudding*, *Bloomberg Green*, and *Stripe Press*).

### Core Design Ethos: "Editorial Elegance Meets Modern Interactivity"
- **Narrative-First Approach:** Data is never presented as raw dumps; every chart tells a specific story node.
- **Scrollytelling Integration:** Visuals update gracefully as the user scrolls through the narrative.
- **Cognitive Clarity:** High visual contrast, scannable layouts, bold stat callouts, and progressive disclosure of complex data.

---

## Target Architecture & Technical Stack

### 1. Frontend & UI Engine
- **Framework:** React / Next.js (TypeScript) or Vite + React for rapid lightweight deployments.
- **Styling & Layout:** Tailwind CSS with custom editorial typography scales, CSS Grid, and Flexbox layout systems.
- **Animation & Transitions:** Framer Motion for scroll-triggered animations, smooth layout morphing, and micro-interactions.
- **Icons & Visual Accents:** Lucide-React icons, custom SVG annotations, and subtle glow/gradient accents.

### 2. Data Visualization Engine
- **Chart Libraries:** Recharts or Chart.js for clean standard visualizations (Bar, Line, Donut, Area, Radar).
- **Custom / Complex Viz:** D3.js or SVG manipulation for specialized graphics (Sankey diagrams, Scrollytelling heatmaps, interactive timelines).
- **Interactivity:** Interactive tooltips, metric toggle switches (e.g., YoY vs. QoQ, Absolute vs. Percentage), search/filter controls, and hover highlights.

### 3. Page Structure & Key Modules
1. **Hero Header:** High-impact title, executive summary subtitle, estimated read time, key takeaway pill tags, and animated hero metric counter.
2. **Executive Summary / Quick Stats Grid:** 3–4 highlight KPI cards with animated count-up numbers and trend badges (+/- %).
3. **Scrollytelling Sections:** Sticky chart/graphic sidebar paired with scrollable narrative text blocks.
4. **Interactive Data Explorer:** Filterable data table/grid with search, pagination, and CSV export.
5. **Deep-Dive Metric Cards:** Expandable accordion panels or modal overlays for detailed methodological notes.
6. **Footer & Data Provenance:** Citation list, source links, methodology disclaimer, and download buttons (PDF/Slide export).

---

## Storytelling & Engagement Rules (Making it Highly Readable & Captivating)

1. **Typography & Visual Hierarchy:**
   - Use high-contrast font pairs: A refined Editorial Serif font (e.g., *Playfair Display*, *Lora*, or *Merriweather*) for main headlines paired with a clean Sans-Serif (e.g., *Inter*, *Plus Jakarta Sans*) for body copy and data labels.
   - Maintain strict typographic scale: H1 (3.5rem+), H2 (2.25rem), Stat Highlights (3rem+ bold), Body (1.125rem with 1.7 line-height for effortless reading).

2. **Visual Pacing & Color System:**
   - **Color Palette:** Limit primary data palette to 3–4 thematic colors (e.g., Deep Slate `#0F172A`, Electric Teal `#0D9488`, Warm Gold `#D97706`, Soft Rose `#E11D48`). Use color strictly for semantic data encoding, not decoration.
   - **Dark Mode Support:** Provide an elegant dark theme option by default or toggle, enhancing visual pop for charts.

3. **Data Annotation & Scannability:**
   - Every major chart MUST feature a **Direct Annotation Callout** (e.g., an arrow or highlighted marker pointing to a peak, drop, or anomaly) with a 1-sentence narrative context.
   - Highlight key figures within body text using bold colored badges (e.g., `<span class="bg-teal-500/10 text-teal-600 px-2 py-0.5 rounded font-semibold">+34.2% Growth</span>`).

4. **Scrollytelling & Micro-Interactions:**
   - Implement sticky positioning (`sticky top-24`) so charts remain pinned in view while explanatory paragraphs scroll alongside.
   - Add hover states to chart data points that highlight corresponding bullet points in the copy (two-way state synchronization).

---

## User & AI Workflow (Division of Labor)

### Human Team Roles
- **Product Owner / Lead Editor:** Defines the overall narrative angle, provides raw dataset, approves visual styling, and verifies factual accuracy.
- **UI/UX & Graphics Designer:** Curates color schemes, selects typography, and designs key visual mockups.
- **QA & Data Auditor:** Cross-checks chart data against raw source files and tests responsiveness across mobile/tablet/desktop.

### AI Agent Specialization
- **Claude (Sonnet/Opus):** Core React component architecture, D3/Recharts implementation, Scrollytelling scroll-sync logic, and state management.
- **Codex:** Component refactoring, performance optimization (reducing chart re-renders), accessibility (a11y) audits, and cross-browser testing.
- **GPT:** Editorial copywriting, headline sharpening, converting complex technical descriptions into punchy executive summaries.
- **Gemini:** Dataset structural analysis, JSON data transformation, reference benchmarking, and citation validation.

---

## Operating Rules & Guardrails

1. **Performance & Responsiveness:**
   - Zero Layout Shift (CLS): All charts must have explicit responsive aspect ratios (`Aspect-Ratio` or container wrappers).
   - Mobile First Optimization: Complex multi-column charts must automatically stack or simplify into touch-friendly cards on screens smaller than 768px.

2. **Code & Quality Standards:**
   - Keep chart components modular and declarative (separate raw data JSON from visualization markup).
   - Ensure color contrast ratios meet WCAG AA standards (4.5:1 for body text).

3. **Permission Boundaries:**
   - Always seek explicit approval before altering the underlying data values or changing the core narrative structure.
   - Never introduce heavy unapproved 3D canvas libraries (e.g., Three.js) if lightweight 2D SVG/Canvas solutions suffice.

4. **Session Handoff Protocol:**
   - If the AI session token budget is low, generate a `HANDOFF_SUMMARY.md` documenting:
     1. Components completed.
     2. Data state structures implemented.
     3. Next immediate layout or chart tasks for the following session.

---

## Phased Implementation Roadmap

### Phase 1 — Project Setup & Data Transformation
- [ ] Initialize React/Next.js environment with Tailwind CSS & Framer Motion.
- [ ] Clean and transform raw input data into structured JSON format (`data/metrics.json`).
- [ ] Define global color palette, typography tokens, and responsive layout primitives.

### Phase 2 — Hero Header & Executive Summary Cards
- [ ] Build high-impact Hero Header with title, estimated reading time, and executive tags.
- [ ] Implement Executive Stat Cards with animated number count-ups (`framer-motion` / `useInView`).

### Phase 3 — Core Storytelling & Scrollytelling Engine
- [ ] Implement sticky layout split (Narrative Scroll Column + Sticky Visual Container).
- [ ] Build interactive chart components (Recharts / D3) with custom tooltips and direct annotations.
- [ ] Synchronize scroll triggers with chart state transitions.

### Phase 4 — Data Explorer & Interactive Deep-Dives
- [ ] Build filterable Data Explorer grid (Search, Category Filter, Sorting).
- [ ] Add expandable accordion sections for methodology and secondary data breakdowns.

### Phase 5 — Polishing, Accessibility & Build Output
- [ ] Audit mobile responsiveness and touch interactions.
- [ ] Add dark mode toggle, scroll progress bar, and reading indicator.
- [ ] Perform build verification and export preview.
