---
name: minimalist-editorial-ui
description: Notion-style editorial interfaces with warm bone backgrounds, serif typography pairings, sparse color, and document-style layouts
---

# Minimalist Editorial UI

## Overview

Produces interfaces that feel like well-typeset documents rather than software — warm, calm, and typography-driven. Think Notion's aesthetic, Bear app, iA Writer, or a beautifully printed independent magazine translated to screen.

This style works by *subtracting* rather than adding. The interface gets out of the way and lets content breathe. Color is used as punctuation, not decoration.

## When to Use This Skill

- Note-taking apps, writing tools, or knowledge management interfaces
- Internal tools and admin dashboards that prioritize readability over flash
- Documentation sites and developer portals
- Personal sites, blogs, and portfolios with a literary sensibility
- Any product where content is the primary value (not the chrome around it)
- When the brief says "clean," "minimal," "calm," or "Notion-like"

## Process

### Step 1: Establish the Typographic Foundation

Typography carries 90% of the personality in this style:

**Heading typefaces (choose one):**
- Serif options: Newsreader, Instrument Serif, Playfair Display, Lyon Text, Lora
- Apply tight tracking: -0.02em to -0.04em on headings
- Display sizes: 32-48px (not massive — this isn't a landing page)

**Body typefaces (choose one):**
- Sans options: SF Pro Display, Geist Sans, Helvetica Neue, Switzer, Satoshi
- Body size: 16-18px, line-height 1.6-1.7
- Color: off-black (#111111 or #1a1a1a), never pure black

**Monospace (for code, metadata, shortcuts):**
- Geist Mono, SF Mono, JetBrains Mono, or Berkeley Mono
- Size: 13-14px (slightly smaller than body)
- Use for timestamps, keyboard shortcuts, file paths, and technical metadata

**The pairing rule:** Serif headings + sans body OR sans headings + sans body. Never sans headings + serif body (it reads as confused hierarchy).

### Step 2: Set the Color Environment

**Backgrounds:**
- Primary: warm bone (#F7F6F3 or #FAF9F7) — never pure white, never cool gray
- Cards/panels: white (#FFFFFF) or one shade warmer than the background
- Sidebar/nav: slightly darker warm gray (#F0EFEC)

**Borders and dividers:**
- Ultra-light: #EAEAEA or rgba(0,0,0,0.06)
- Used for: card edges, section dividers, table rows
- Style: always `border-bottom` for lists, never full borders on cards (too boxy)

**Accent colors (maximum 4, used sparingly):**
- Pale red/coral: status indicators, destructive actions
- Pale blue: links, active states, selections
- Pale green: success, completed states
- Pale yellow: highlights, warnings, pinned items
- Saturation: keep below 60% — these should whisper, not shout

**Text colors:**
- Primary: #111111 (headings and body)
- Secondary: #6B7280 (metadata, captions, timestamps)
- Tertiary: #9CA3AF (placeholders, disabled text)

### Step 3: Layout as Document

**Page structure:**
- Constrained content width: 680-720px for reading (never wider for body text)
- Generous side margins that grow on larger screens
- Vertical rhythm: consistent spacing multiples (16px base)

**Navigation:**
- Sidebar preferred over top nav (document metaphor)
- Flat hierarchy — avoid deeply nested nav trees
- Current item indicated by subtle background highlight, not bold/color

**Component patterns:**
- Cards: ultra-flat, border-bottom dividers (not boxed cards with shadows)
- Lists: simple vertical stacks with `border-bottom` separators
- Bento grids: thin borders (8-12px gap), equal 8-12px border-radius
- Buttons: solid black (#111111) for primary, ghost/outline for secondary
- Accordions: `border-bottom` only, clean expand/collapse with `+` / `−` indicators
- Keyboard shortcuts: `<kbd>` elements with subtle raised appearance

### Step 4: Motion (Minimal and Deliberate)

**Entrance animations:**
- Fade-in with slight rise: `opacity 0→1` + `translateY(12px→0)` over 600ms
- Trigger: `IntersectionObserver` at 10% visibility threshold
- Easing: `cubic-bezier(0.4, 0, 0.2, 1)`

**Hover states:**
- Cards: `translateY(-1px)` + faint shadow appearing (not growing)
- Links: underline opacity fade or color shift (subtle)
- Buttons: background lightens slightly (not dramatic)

**Staggered cascades:**
- List items animate in with 50ms offset
- Only use `transform` and `opacity` — nothing else animates

**What never moves:**
- Navigation (stays completely static)
- Text content (no text animation or reveal effects)
- Background colors (no transitioning section backgrounds)

### Step 5: Content Voice

Even placeholder content should match the editorial tone:

- Headlines: declarative and specific ("Track what matters" not "Welcome to our platform!")
- Descriptions: one sentence, plain language, no marketing fluff
- Empty states: helpful and warm ("No notes yet. Start writing to see them here.")
- Button labels: verb-first, lowercase feel ("Create note" not "CREATE NOTE")

## Key Rules

1. **Warm over cool** — bone/cream backgrounds, not blue-gray; this is a living room, not a hospital
2. **Typography IS the design** — if the type choices are good, you need almost nothing else
3. **Color as punctuation** — use it to mark meaning (status, action, emphasis), never for decoration
4. **Borders over shadows** — subtle 1px borders communicate structure more quietly than shadows
5. **Content width matters** — 65-75 characters per line; wider than that and readability drops sharply

## Anti-Patterns (Banned)

- Pure white (#FFFFFF) as page background
- Inter or Roboto as the primary typeface
- Lucide/Heroicons as the only icon source (too ubiquitous — consider Phosphor or custom)
- Drop shadows heavier than `0 1px 3px rgba(0,0,0,0.04)`
- Gradients of any kind
- Neon or saturated accent colors
- Pill-shaped containers or badges
- Emoji in UI labels or headings
- Sticky navigation bars (conflicts with document metaphor)
- Full-width content (text running edge to edge)
- ALL CAPS button labels
- Rounded avatars larger than 32px (document style uses square or subtly rounded)

## Related Skills

- `taste-ui-framework` — apply as a quality filter on top of this aesthetic direction
- `frontend-design` — use for the full design process; this skill directs the aesthetic
- `soft-premium-ui` — more expressive alternative when minimalist feels too restrained
- `brutalist-swiss-ui` — shares the typography focus but with industrial rather than editorial tone
