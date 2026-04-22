---
name: soft-premium-ui
description: Premium agency-level aesthetics with texture archetypes, layered depth, haptic micro-interactions, and generous whitespace
---

# Soft Premium UI

## Overview

Produces interfaces that feel like they came from a $150k agency engagement — polished, layered, and tactile. This aesthetic sits at the intersection of luxury branding and modern product design: think Stripe's marketing pages, Linear's interface, or Apple's product showcases.

The key differentiator is *perceived depth* — elements feel like physical objects with weight, texture, and subtle dimensionality, without resorting to heavy shadows or skeuomorphism.

## When to Use This Skill

- Building a SaaS marketing site or product landing page that needs to feel premium
- Designing an interface for a product with a $50+/month price point
- Creating a brand presence that communicates quality and sophistication
- When the brief says "high-end," "premium," or "luxury" without specifying an exact direction
- Portfolio sites, agency sites, or design tool interfaces

## Process

### Step 1: Choose a Texture Archetype

Pick ONE as the foundation — mixing archetypes creates visual confusion:

**Ethereal Glass** (best for: tech products, AI tools, developer platforms)
- Frosted glass panels with `backdrop-blur` (12-20px)
- Subtle gradient overlays at 3-8% opacity
- Light refraction effects on hover
- Cool-neutral palette with one luminous accent
- Reference: Linear, Raycast, Arc browser

**Editorial Luxury** (best for: lifestyle brands, content platforms, creative tools)
- Rich typography-forward layouts with serif/sans pairings
- Generous margins (120px+ between sections)
- Muted earth tones or deep jewel tones as accents
- Photography-heavy with careful cropping and overlay treatments
- Reference: Aesop, Monocle, Cereal magazine

**Soft Structuralism** (best for: consumer products, fintech, health/wellness)
- Rounded containers with subtle nested layering
- Warm neutrals (cream, sand, warm gray) as backgrounds
- Pastel accent colors at low saturation
- Smooth, continuous surfaces with minimal hard edges
- Reference: Notion, Calm, Headspace, Monzo

### Step 2: Build Depth Through Layering

Premium UI communicates depth without heavy drop shadows:

**The nested container technique:**
- Outer shell: subtle border (1px, 5-8% opacity) + slight background offset
- Inner core: the actual content panel, slightly inset
- This "double-bezel" effect mimics physical hardware edges

**Shadow strategy:**
- Never use a single harsh shadow — layer 2-3 subtle ones:
  - Close shadow: `0 1px 2px rgba(0,0,0,0.04)` (contact shadow)
  - Medium shadow: `0 4px 8px rgba(0,0,0,0.04)` (lift)
  - Far shadow: `0 12px 24px rgba(0,0,0,0.03)` (ambient)
- On hover, shift to: `0 8px 16px rgba(0,0,0,0.06)` + slight `translateY(-2px)`

**Background layering:**
- Base: warm or cool neutral (#FAFAF9 or #FAFAFA)
- Section alternation: shift by 1-2% (not dramatic zebra striping)
- Cards: pure white or 1 shade lighter than section background
- Subtle noise texture at 2-4% opacity on backgrounds for richness

### Step 3: Typography for Premium Feel

**Heading approach:**
- Use display-weight fonts at large sizes (48-72px for hero, tight letter-spacing -0.02 to -0.04em)
- Pair with a lighter weight of the same family or a complementary sans for body
- Good premium pairings: Instrument Serif + Inter, Fraunces + Satoshi, PP Neue Montreal + any geometric sans

**Spacing philosophy:**
- Minimum `py-24` (96px) between major sections
- Let content breathe — premium never feels cramped
- Line height 1.6-1.7 for body text, 1.0-1.1 for large headings

### Step 4: Haptic Micro-Interactions

Make elements feel physically responsive:

**Buttons:**
- Slight scale on press: `transform: scale(0.98)` on `:active`
- Smooth background color shift on hover (not just opacity change)
- Consider a subtle inset shadow on press to simulate depth

**Cards and containers:**
- Gentle lift on hover: `translateY(-2px)` + enhanced shadow
- Border opacity increase on hover (5% → 12%)
- Transition duration: 200-300ms with `cubic-bezier(0.4, 0, 0.2, 1)`

**Icon buttons:**
- Circular wrapper (the "button-in-button" pattern): icon inside a circular background inside the main button
- Background shift from transparent to subtle fill on hover

### Step 5: Color with Restraint

**Primary palette structure:**
- One dominant neutral (warm or cool, not both)
- One accent color at moderate saturation (60-75% HSL saturation)
- One supporting color for secondary actions (often a desaturated version of the accent)

**What NOT to do:**
- No gradients on interactive elements (buttons, cards)
- No more than 3 colors visible in any single viewport
- No saturated colors on large surface areas — reserve for small accents (icons, badges, active states)

## Key Rules

1. **Depth over decoration** — layered shadows and nested containers communicate quality better than ornamental elements
2. **Warmth over sterility** — even tech products benefit from warm neutrals; pure gray reads as unfinished
3. **Texture over flatness** — subtle noise, gentle gradients, and layered shadows make surfaces feel real
4. **Restraint is premium** — luxury communicates confidence through what it omits, not what it adds
5. **Transitions must feel physical** — 200-300ms with easing, never instant, never longer than 400ms

## Anti-Patterns (Banned)

- Heavy box shadows (anything above 0.1 opacity as a single shadow)
- Flat solid-color backgrounds with no texture variation
- Neon or oversaturated accent colors
- Symmetric icon grids (the "features section" cliché)
- Borders heavier than 1px
- Generic stock photography without treatment (overlay, crop, filter)
- Components that snap instantly without transitions
- Pure white (#fff) as background without any warmth
- Inter or Roboto as the only typeface
- Gradients that move through more than 2 color stops

## Related Skills

- `taste-ui-framework` — apply as a general quality filter; soft-premium-ui is a specific aesthetic within that framework
- `frontend-design` — use for the full design process; apply this skill to direct the aesthetic
- `brand-design-system` — extract tokens from a soft-premium design into a reusable system
- `minimalist-editorial-ui` — a more restrained alternative if premium feels too "designed"
- `cinematic-motion-ui` — add this on top for scroll-driven experiences
