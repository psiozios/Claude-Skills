---
name: taste-ui-framework
description: Calibrate AI-generated UI to eliminate generic patterns using three design dials, bias correction, and banned anti-patterns
---

# Taste UI Framework

## Overview

A calibration system that transforms generic AI-generated interfaces into distinctive, production-quality designs. Works by correcting common AI biases (defaulting to Inter, centering everything, using neon gradients) and providing three adjustable dials to control the aesthetic output.

Think of this as a quality filter — apply it after (or alongside) any UI design process to ensure the result doesn't scream "made by AI."

## When to Use This Skill

- Your generated UI looks generic, safe, or "template-like"
- You want to eliminate the telltale AI aesthetic (purple gradients, Inter font, symmetric grids)
- You need a systematic way to dial design choices up or down
- You're building a landing page, dashboard, or product interface that needs to feel crafted
- Before handing off a prototype for implementation

## Process

### Step 1: Set the Three Dials

Rate each from 1-10 based on the project's needs:

**Design Variance** (how experimental vs. clean)
- 1-3: Corporate, predictable, safe layouts
- 4-6: Balanced — asymmetric touches within familiar structures
- 7-10: Bold, unexpected compositions, editorial layouts

**Motion Intensity** (how much animation)
- 1-3: Subtle transitions only (opacity, slight transforms)
- 4-6: Fluid CSS transitions with selective scroll-triggered reveals
- 7-10: Orchestrated sequences, spring physics, parallax layers

**Visual Density** (how packed or spacious)
- 1-3: Generous whitespace, minimal elements per viewport
- 4-6: Balanced — breathing room without feeling empty
- 7-10: Information-rich, data-dense, compact interfaces

**Default recommendation:** 8 / 6 / 4 — this produces distinctive layouts with fluid motion and comfortable breathing room.

### Step 2: Apply Bias Corrections

These are the most common ways AI-generated UI reveals itself. Actively avoid:

**Typography bias:**
- Do NOT default to Inter, Roboto, or Open Sans — choose a typeface with character (Satoshi, General Sans, Cabinet Grotesk, Instrument Sans, Geist)
- Do NOT make all headings the same weight — vary between light/regular for large display text and medium/bold for smaller headings
- Do NOT center all text — left-align body copy, reserve centering for short hero headlines only

**Layout bias:**
- Do NOT default to symmetric 3-column grids — use asymmetric splits (60/40, 70/30), bento grids, or editorial layouts
- Do NOT center everything vertically — use intentional alignment points
- Do NOT make all cards the same size — vary proportions in grid layouts

**Color bias:**
- Do NOT use purple-to-blue gradients (the #1 AI design fingerprint)
- Do NOT use more than one accent color at <80% saturation
- Do NOT use pure black (#000) — use off-blacks (#0a0a0a, #111, #1a1a1a)
- Do NOT use neon glows or oversaturated colors

**Content bias:**
- Do NOT use placeholder names like "John Doe" or "Acme Corp"
- Do NOT use round numbers ($99, 10k users) — use specific-feeling numbers ($97, 11,847 users)
- Do NOT write generic headlines ("Welcome to the Future of X")

### Step 3: Enforce Interaction States

Every interactive element must account for:
- Default, hover, active, focus, disabled states
- Loading states (skeleton screens, not spinners where possible)
- Empty states (helpful, not just "No data")
- Error states (specific, actionable messages)

### Step 4: Performance-Conscious Motion

When adding animation:
- Use `transform` and `opacity` only for smooth 60fps (hardware-accelerated)
- Keep grain/noise textures on fixed pseudo-elements with `isolation: isolate`
- Use `will-change` sparingly and only on elements about to animate
- Prefer CSS transitions for simple state changes; reach for JS animation libraries only for orchestrated sequences
- Stagger group animations (50-100ms offset per item)

### Step 5: Mobile Safety

- Use `min-h-[100dvh]` instead of `h-screen` (accounts for mobile browser chrome)
- Use CSS Grid for layouts that need to reflow, not flex-math hacks
- Collapse to single column aggressively below 768px — no horizontal scrolling
- Touch targets minimum 44x44px
- Test that text remains readable without zooming

## Key Rules

1. **Typography is identity** — the typeface choice alone determines 60% of whether the UI feels generic or crafted
2. **Asymmetry signals intention** — symmetric layouts feel automated; deliberate asymmetry feels designed
3. **Restraint over excess** — one accent color, two typefaces max, motion only where it aids comprehension
4. **Specificity over defaults** — specific numbers, realistic content, named personas over placeholder text
5. **States are not optional** — a button without a hover state is an unfinished button

## Anti-Patterns (Banned)

- Inter/Roboto as the sole typeface
- Purple/blue AI gradients
- Pure black (#000000) backgrounds or text
- Neon glow effects or oversaturated accent colors
- Symmetric 3-column feature grids with icons
- "Lorem ipsum" or obviously fake placeholder content
- Generic hero headlines ("Revolutionize your workflow")
- Centered everything (text, cards, layouts)
- Missing hover/focus states on interactive elements
- `h-screen` without `dvh` fallback on mobile
- Z-index values above 50 without clear layering strategy
- Serif fonts on dashboard/app interfaces (unless the whole brand is editorial)

## Related Skills

- `frontend-design` — use for full design process from brief to prototype; apply taste-ui-framework as a quality filter on the output
- `soft-premium-ui` — specific aesthetic direction: luxury agency feel
- `minimalist-editorial-ui` — specific aesthetic direction: Notion-style document interfaces
- `brutalist-swiss-ui` — specific aesthetic direction: industrial data-dense interfaces
- `cinematic-motion-ui` — when motion is the primary differentiator (scroll-driven, award-site feel)
- `ui-redesign-audit` — when upgrading an existing site rather than building from scratch
