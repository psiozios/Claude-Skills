---
name: brutalist-swiss-ui
description: Industrial Swiss typography with military/aerospace data density, rigid grids, visible structure, and austere visual treatment
---

# Brutalist Swiss UI

## Overview

Produces interfaces inspired by mid-century Swiss graphic design crossed with military command-center aesthetics — stark, data-dense, and unapologetically structural. Every pixel serves a purpose. Decoration is stripped away entirely; the grid, typography, and information density ARE the design.

Think Bloomberg Terminal meets a Josef Müller-Brockmann poster. Or: the UI equivalent of a concrete building where you can see the rebar.

This is a beta aesthetic — it's polarizing by design. Use it when the product values information density, technical credibility, and brutalist honesty over approachability.

## When to Use This Skill

- Developer tools, CLIs with web interfaces, or monitoring dashboards
- Data-heavy applications (analytics, trading, logistics, infrastructure)
- Technical documentation or specification sites
- Portfolio sites for architects, engineers, or designers who want to signal rigor
- Any product where "looking friendly" is less important than "looking competent"
- When the brief says "technical," "data-dense," "industrial," or "no-nonsense"

## Process

### Step 1: Choose a Visual Archetype

Pick ONE — these should not be mixed:

**Swiss Industrial Print** (light mode dominant)
- High-contrast light backgrounds with heavy black typography
- Aggressive negative space alternating with dense information blocks
- Aviation red (#E61919) as the sole accent color
- Feels like: a Swiss railway timetable or a Dieter Rams product manual
- Reference: Zwischen design studio, Experimental Jetset, any Swiss Style poster

**Tactical Telemetry** (dark mode dominant)
- Near-black backgrounds (#0A0A0A) with light text
- Monospaced typography dominant, simulating hardware readouts
- Phosphor green (#00FF41) or aviation red (#E61919) as accent
- Subtle CRT scanline or noise overlay for analog texture
- Feels like: a radar screen, a flight control console, a terminal
- Reference: SpaceX launch UI, air traffic control interfaces, Bloomberg Terminal

### Step 2: Typography as Architecture

Typography does ALL the heavy lifting in brutalist design:

**Macro-typography (headings, hero text):**
- Heavy neo-grotesque sans-serifs at massive scale: Helvetica Neue Black, Neue Haas Grotesk, ABC Diatype, Suisse Int'l
- Extremely tight letter-spacing: -0.03em to -0.06em
- Compressed line-height: 0.85-0.95 (letters nearly touching vertically)
- Sizes: 64-120px for display, making type the dominant visual element

**Micro-typography (data, labels, metadata):**
- Monospace fonts at small sizes: 10-14px
- Generous tracking (+0.05em to +0.1em) to simulate mechanical typewriter spacing
- Use for: timestamps, coordinates, status codes, measurements, IDs
- ALL CAPS for labels and category markers (the one context where it's appropriate)

**The contrast rule:** Macro and micro typography should feel dramatically different — massive compressed headings next to small tracked-out monospace creates the tension that defines this aesthetic.

### Step 3: Color Discipline

**Swiss Industrial palette:**
- Background: #F4F4F0 (warm paper white)
- Foreground: #050505 (near-black)
- Accent: #E61919 (aviation red) — used ONLY for emphasis, warnings, active states
- Secondary: #6B6B6B (medium gray for metadata)

**Tactical Telemetry palette:**
- Background: #0A0A0A (near-black)
- Foreground: #EAEAEA (off-white)
- Accent: #E61919 or #00FF41 — pick one, never both
- Secondary: #4A4A4A (dark gray for borders and secondary text)

**Strict rules:**
- Maximum 3 colors in the entire interface (background, foreground, accent)
- No gradients — ever
- No transparency effects or frosted glass
- No soft shadows of any kind
- Color is functional, not decorative: it marks status, danger, or active state

### Step 4: Spatial Logic — The Rigid Grid

**Grid structure:**
- Use CSS Grid exclusively (never flexbox for page layout)
- Visible 1-2px solid borders compartmentalize every section
- No border-radius anywhere — every corner is sharp
- Cells contain either dense information OR calculated emptiness (never medium)

**The density/void alternation:**
- Adjacent grid cells should contrast dramatically: one packed with data, the next completely empty or containing a single large number
- This creates rhythm through information contrast, not decorative elements
- Empty cells are not wasted space — they're intentional counterweight

**Spacing:**
- Generous outer margins (80-120px on desktop)
- Tight inner padding within grid cells (12-16px)
- No space between grid cells — borders do the separation work

### Step 5: Textural Degradation (Optional — Tactical Telemetry Only)

Add analog texture to simulate hardware authenticity:

**CRT scanlines:**
```css
background-image: repeating-linear-gradient(
  0deg,
  rgba(255,255,255,0.03) 0px,
  rgba(255,255,255,0.03) 1px,
  transparent 1px,
  transparent 3px
);
```

**Noise overlay:**
- SVG noise filter at 2-5% opacity on a fixed pseudo-element
- Use `isolation: isolate` to prevent performance bleed

**Halftone (for images):**
- Convert photos to high-contrast duotone
- Apply dot screen or line screen filter
- Images should feel printed, not photographed

## Key Rules

1. **The grid is visible** — borders are structural, not decorative; hiding them defeats the purpose
2. **No border-radius** — sharp corners are non-negotiable; rounded corners imply friendliness this aesthetic rejects
3. **Type IS the design** — if you remove all non-text elements and the layout still has character, you're doing it right
4. **Density is intentional** — pack information tight where it matters, leave dramatic voids where it doesn't
5. **Monochrome + one** — two text colors (primary + secondary) plus exactly one accent; nothing more

## Anti-Patterns (Banned)

- Border-radius on any element
- Gradients, transparency, or backdrop-blur
- Drop shadows (hard or soft)
- Icons as decoration (icons may convey specific meaning in data contexts)
- Friendly/rounded typefaces (Nunito, Poppins, Quicksand)
- Pastel colors or muted tones
- Card-based layouts with hover lift effects
- Emoji anywhere in the interface
- Photography (unless heavily treated — duotone, halftone, high-contrast)
- Centered hero sections with marketing copy
- Loading spinners (use progress bars or percentage counters)
- Smooth/spring animations (if anything moves, it should snap or step)

## Related Skills

- `taste-ui-framework` — apply as a general quality filter on top of this aesthetic
- `minimalist-editorial-ui` — shares the typography focus but warm and editorial rather than cold and industrial
- `soft-premium-ui` — the opposite aesthetic; use when you need approachability over authority
- `frontend-design` — use for full design process; this skill provides the aesthetic direction
