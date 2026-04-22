---
name: ui-redesign-audit
description: Three-phase audit and upgrade for existing UIs — scan the tech stack, diagnose design issues, fix without breaking functionality
---

# UI Redesign Audit

## Overview

A systematic process for upgrading an existing website or application's visual design without breaking functionality. Instead of rebuilding from scratch, this skill identifies the specific patterns that make an interface look generic, dated, or AI-generated, then applies targeted fixes within the existing tech stack.

Think of it as a design renovation, not a demolition. You keep the plumbing and wiring, but replace the fixtures and finishes.

## When to Use This Skill

- An existing site or app "works fine" but looks generic, template-like, or dated
- You inherited a codebase with functional but visually unpolished UI
- A prototype needs to be elevated to production-quality visuals without a rewrite
- The team wants design improvements but doesn't have bandwidth for a full redesign
- You need to remove the "AI-generated" look from a v0/Bolt/Lovable/GPT-built interface

## Process

### Phase 1: Scan (Understand What Exists)

Before changing anything, inventory the current state:

**Tech stack identification:**
- Framework: React, Vue, Svelte, vanilla HTML, etc.
- Styling method: Tailwind, CSS modules, styled-components, plain CSS, inline styles
- Component library: shadcn/ui, MUI, Chakra, Ant Design, custom, or none
- Animation library: Framer Motion, GSAP, CSS transitions, or none
- Font loading: Google Fonts, local files, system fonts, or CDN

**Visual inventory:**
- Screenshot every major page/view
- List all unique components (buttons, cards, forms, navigation, modals)
- Note the current color palette (inspect actual hex values, don't guess)
- Note the current typography (actual fonts, sizes, weights in use)
- Identify the spacing system (is it consistent or ad hoc?)

**Functional dependencies:**
- Which visual elements are tied to business logic? (e.g., color-coded statuses, icon-based navigation)
- What can't change without breaking functionality?
- Are there external brand guidelines that must be respected?

### Phase 2: Diagnose (Identify What's Wrong)

Run through each audit dimension and score 1-5 (1 = needs immediate attention, 5 = fine as-is):

**Typography audit:**
- [ ] Font choice: Is it Inter/Roboto/system default? (Score low if yes)
- [ ] Hierarchy: Can you tell H1 from H2 from body at a glance? (Score low if everything looks similar)
- [ ] Line length: Is body text wider than 75 characters per line? (Score low if yes)
- [ ] Spacing: Are line-heights and letter-spacing intentional or browser defaults?

**Color audit:**
- [ ] Black usage: Is pure #000 used anywhere? (Score low if yes)
- [ ] Accent colors: More than 2 saturated colors competing? (Score low if yes)
- [ ] AI gradient: Is there a purple-to-blue gradient? (Score very low — this is the #1 AI fingerprint)
- [ ] Background: Is it pure white with no warmth? (Score low if yes)
- [ ] Contrast: Do all text/background combinations pass WCAG AA?

**Layout audit:**
- [ ] Symmetry: Is every section a centered 3-column grid? (Score low if yes)
- [ ] Card uniformity: Are all cards identical sizes in a flat grid? (Score low if yes)
- [ ] Spacing consistency: Are gaps between elements ad hoc or from a system?
- [ ] Mobile: Does the layout actually reflow, or just shrink?

**Interaction audit:**
- [ ] Hover states: Do buttons and links have visible hover feedback? (Score low if not)
- [ ] Focus states: Can a keyboard user see where they are? (Score low if not)
- [ ] Loading states: Are there skeleton screens or just spinners/blank screens?
- [ ] Empty states: Is "no data" handled gracefully?
- [ ] Transitions: Do state changes animate or snap instantly?

**Content audit:**
- [ ] Headlines: Are they generic ("Welcome to X", "The Future of Y")?
- [ ] Placeholder data: Are there obvious fakes ("John Doe", "$99.00", "Lorem ipsum")?
- [ ] Imagery: Stock photos without treatment? Broken image links?
- [ ] Microcopy: Are button labels specific ("Save changes") or vague ("Submit")?

### Phase 3: Fix (Targeted Improvements)

Apply fixes in this priority order — each step has the highest visual impact for the least structural risk:

**1. Typography upgrade (highest impact, lowest risk):**
- Replace Inter/Roboto with a distinctive font (Satoshi, Geist, Cabinet Grotesk, General Sans)
- Tighten heading letter-spacing (-0.01 to -0.03em)
- Set body line-height to 1.6, heading line-height to 1.1-1.2
- Constrain body text width to max 680px
- Establish 3-4 clear text sizes with consistent weights

**2. Color cleanup:**
- Replace #000 with off-black (#111 or #0a0a0a)
- Replace pure #fff backgrounds with warm off-white (#FAFAF9, #F7F6F3)
- Remove any purple/blue AI gradients — replace with solid colors or subtle single-hue gradients
- Reduce accent colors to 1 primary + 1 muted secondary
- Ensure WCAG AA contrast on all text

**3. Hover and focus states:**
- Add hover transitions to all clickable elements (200-250ms, ease-out)
- Add visible focus rings (2px offset, accent color) for keyboard navigation
- Add subtle scale or shadow changes on card hover

**4. Layout improvements:**
- Break symmetric grids — introduce size variation (1 large + 2 small instead of 3 equal)
- Add more vertical spacing between sections (double what exists if it feels tight)
- Left-align body text if everything is currently centered

**5. Component refinements:**
- Replace generic card borders with subtler alternatives (shadow layers or faint borders)
- Add border-radius consistency (pick one value: 8px, 12px, or 16px — apply everywhere)
- Style empty states with helpful messages and appropriate illustrations
- Add skeleton loading states to replace spinners

**6. Content polish:**
- Replace generic headlines with specific value propositions
- Swap placeholder data for realistic (but not round-number) examples
- Add alt text to all images
- Make button labels action-specific

### Post-Fix Verification

After all changes, verify:
- [ ] No functionality was broken (click through every interactive element)
- [ ] Mobile layout still works (test at 375px and 768px)
- [ ] Page load performance is equal or better (check with Lighthouse)
- [ ] All text passes WCAG AA contrast
- [ ] Hover/focus states work consistently across all interactive elements
- [ ] No visual regressions in areas you didn't intentionally change

## Key Rules

1. **Diagnose before fixing** — never start changing code until you've completed the full audit
2. **Typography first** — font changes alone can transform a generic interface; do this before anything else
3. **Work within the stack** — don't introduce Tailwind into a styled-components project or vice versa
4. **One change at a time** — apply fixes in order, verify each before moving on
5. **Don't redesign features** — change how things look, not how they work; layout adjustments yes, new navigation patterns no

## Anti-Patterns (Banned)

- Introducing a new CSS framework alongside the existing one
- Changing component behavior while updating visuals
- Applying a "theme" globally without per-component verification
- Removing existing accessibility features (even accidental ones)
- Adding motion/animation before fixing typography and color (foundations first)
- Redesigning navigation or information architecture (that's a different project)

## Related Skills

- `taste-ui-framework` — use the bias corrections checklist as a diagnostic supplement
- `frontend-design` — use when building from scratch; this skill is for upgrading existing work
- `implement-design` — use after this audit to implement the fixes with production quality
- `soft-premium-ui` / `minimalist-editorial-ui` / `brutalist-swiss-ui` — choose an aesthetic direction to guide the Phase 3 fixes
- `creative-qa-check` — run after fixes to verify content quality alongside visual quality
