---
name: cinematic-motion-ui
description: Motion-first UI with scroll-driven animations, AIDA narrative structure, cinematic spacing, and orchestrated reveal sequences
---

# Cinematic Motion UI

## Overview

Produces interfaces where motion is the primary design tool — pages that unfold like a film sequence as users scroll, with choreographed reveals, pinned sections, and physics-based interactions. This is the aesthetic of award-winning agency sites (Awwwards, FWA) translated into a repeatable framework.

The core idea: every page tells a story using the AIDA structure (Attention → Interest → Desire → Action), and motion is how you control the pacing of that story.

This skill is intensive — use it for hero experiences, marketing pages, and showcase sites. Don't apply it to utility interfaces or dashboards where motion would slow users down.

## When to Use This Skill

- Marketing landing pages or product launch pages
- Portfolio and showcase sites
- Brand storytelling experiences
- Product demos or interactive walkthroughs
- Any page where the goal is to impress and persuade (not to enable fast task completion)
- When the brief says "award-winning," "immersive," "cinematic," or "scroll experience"

## Process

### Step 1: Plan the AIDA Narrative

Before writing any code, map the page to the AIDA framework:

**Attention (hero section):**
- Purpose: stop the scroll, create immediate visual impact
- Typical elements: oversized headline (2-3 lines max), supporting visual, ambient motion
- Duration: first viewport, visible without scrolling

**Interest (feature/benefit sections):**
- Purpose: build curiosity through progressive disclosure
- Typical elements: bento grids, scroll-triggered reveals, animated statistics
- Duration: 2-4 viewport heights of scrollable content

**Desire (proof/social validation):**
- Purpose: create want through demonstrated value
- Typical elements: testimonials, case studies, before/after, live demos
- Duration: 1-2 viewport heights

**Action (conversion):**
- Purpose: clear next step with no ambiguity
- Typical elements: CTA section, pricing, sign-up form
- Duration: final viewport, always ends with a footer

### Step 2: Cinematic Spacing

Motion needs room to breathe. Cramped layouts kill the cinematic feel:

**Section spacing:**
- Minimum `py-48` (192px) between major AIDA sections
- `py-24` (96px) between sub-sections within an AIDA block
- Hero section: full viewport height minimum (`min-h-[100dvh]`)

**Typography for impact:**
- Hero headlines: 64-96px, tight tracking (-0.03 to -0.05em), line-height 0.95-1.05
- Headlines must flow naturally in 2-3 lines — if it wraps awkwardly, rewrite the copy
- Use ultra-wide containers for headlines (80-90% of viewport), narrow containers for body text (max 680px)

**Visual breathing room:**
- Large images/videos: bleed to edges or use generous internal padding
- Cards in bento grids: `grid-auto-flow: dense` with no empty cells — every cell occupied
- White space between elements should feel intentional and generous, not accidental

### Step 3: The Motion Arsenal

Build from these animation primitives, combined as needed:

**Scroll-triggered reveals:**
- Elements fade in + slide up as they enter the viewport
- Use `IntersectionObserver` for detection, CSS or JS for animation
- Threshold: trigger at 15-20% visibility
- Stagger siblings by 75-100ms for cascade effect

**Scroll-pinned sections:**
- Pin a container while its children animate through states
- Use case: feature comparisons, step-by-step processes, before/after reveals
- Implementation: CSS `position: sticky` for simple cases; GSAP ScrollTrigger or Framer Motion for complex orchestration

**Parallax layers:**
- Background elements move slower than foreground (0.3-0.7x scroll speed)
- Keep to 2-3 layers maximum — more creates visual noise
- Use `transform: translateY()` driven by scroll position, never `background-attachment: fixed` (poor mobile support)

**Text reveals:**
- Words or lines animate in sequentially (split text into spans)
- Clip-mask reveals: text slides up from behind a hidden overflow boundary
- Character-by-character reveals for short headlines only (5 words or fewer)

**Hover micro-physics:**
- Magnetic effect: element subtly follows cursor within a radius (use `mousemove` + `transform`)
- Scale on hover: 1.02-1.05x (subtle, not dramatic)
- Spring-based easing for natural deceleration (Framer Motion `spring`, GSAP `elastic`)

**Continuous ambient motion:**
- Floating elements with slow `translateY` oscillation (3-6s loop)
- Gradient shifts or color cycling on backgrounds (8-15s loop)
- Grain/noise texture with subtle movement
- These run perpetually — they're not scroll-triggered

### Step 4: Performance Guardrails

Cinematic motion can destroy performance if unchecked:

**Hardware acceleration:**
- Animate ONLY `transform` and `opacity` — these stay on the GPU
- Never animate `width`, `height`, `top`, `left`, `margin`, or `padding`
- Use `will-change: transform` on elements about to animate (remove after animation completes)

**Scroll performance:**
- Debounce or throttle scroll listeners to 16ms (requestAnimationFrame)
- Use `IntersectionObserver` instead of scroll position checks where possible
- Disable parallax on mobile (too many layers tank mobile GPUs)

**Asset strategy:**
- Hero images/videos: preload with `<link rel="preload">`
- Below-fold images: lazy load with `loading="lazy"`
- Videos: muted autoplay with `playsinline` for mobile, poster frame for slow connections
- Compress aggressively — a 10MB hero video negates all the motion polish

**Mobile adaptation:**
- Reduce all motion to simple fade-in reveals on screens below 768px
- No parallax, no pinned sections, no magnetic hover effects on touch devices
- Stagger delays halved (keep things snappy on slower devices)
- Test on real devices — Chrome DevTools throttling is not enough

### Step 5: Pre-Flight Design Plan

Before coding, document these decisions:

1. **AIDA mapping:** which content goes in which section and why
2. **Motion inventory:** list every animation and its trigger (scroll, hover, load, time)
3. **Performance budget:** target total page weight and number of animated elements per viewport
4. **Hero math:** headline character count, line breaks, and container width to ensure clean wrapping
5. **Grid density:** bento grid cell counts and size ratios

This plan prevents the "I'll just add one more animation" drift that turns cinematic into chaotic.

## Key Rules

1. **Motion serves narrative** — every animation should reveal, emphasize, or pace; never just decorate
2. **Scroll is the director** — the user's scroll position controls what they see and when, like a film timeline
3. **Less, better** — 5 well-choreographed animations beat 20 generic fade-ins
4. **Mobile is different** — gracefully degrade to simple reveals; don't try to preserve the full experience
5. **Performance is a feature** — a janky 60fps-dropping animation is worse than no animation at all

## Anti-Patterns (Banned)

- Animating anything besides `transform` and `opacity` for layout elements
- Scroll-jacking (overriding native scroll behavior)
- Auto-playing video with sound
- Text animation on paragraphs or long content (only headlines)
- Parallax on mobile devices
- More than 3 simultaneously visible animated elements
- Animation without reduced-motion media query support (`@media (prefers-reduced-motion: reduce)`)
- Loading screens longer than 2 seconds (show content progressively, not all-at-once after a loader)
- Emoji in hero sections or CTAs
- Generic meta-labels ("SECTION 01", "SCROLL TO EXPLORE")
- Invisible or low-contrast button text

## Related Skills

- `taste-ui-framework` — apply as a quality filter; cinematic-motion-ui handles motion, taste handles everything else
- `soft-premium-ui` — combine for motion-rich premium marketing pages
- `frontend-design` — use for the overall design system; this skill layers motion on top
- `prototype` — build interactive motion prototypes before committing to full implementation
- `implement-design` — hand off the motion spec for production implementation
