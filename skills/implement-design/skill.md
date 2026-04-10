---
name: implement-design
description: Translate design files and mockups into production-ready code with pixel-perfect accuracy and accessibility
---

# Implement Design

## Overview
Translates design files (Figma screenshots, mockups, wireframes) into production-ready code. Focuses on pixel-perfect accuracy, responsive layouts, accessibility compliance, and clean component structure. Outputs HTML/CSS/JS or framework-specific components.

## When to Use This Skill
- Converting approved designs into code
- Building components from a design system
- Implementing a redesign
- Creating responsive layouts from static mockups

## Process

### Step 1: Design Analysis
From the design file or screenshot:
- Identify all unique components
- Map the layout grid (columns, gutters, breakpoints)
- Extract colors, fonts, and spacing values
- Note interactive states (hover, active, disabled, loading)
- Identify responsive behavior expectations

### Step 2: Component Breakdown
- List all unique components needed
- Identify shared patterns (buttons, cards, inputs)
- Determine component hierarchy (parent/child relationships)
- Map data requirements for each component

### Step 3: Implementation
For each component:
- Write semantic HTML structure
- Apply CSS styling matching the design exactly
- Implement responsive behavior
- Add interaction states
- Include accessibility attributes (ARIA, roles, labels)

### Quality Checks
- **Visual accuracy**: Overlay the code output on the design — they should match
- **Responsive**: Test at 320px, 768px, 1024px, 1440px
- **Accessibility**: Run axe or Lighthouse audit
- **Performance**: No unnecessary DOM nesting, optimized images
- **Cross-browser**: Test in Chrome, Firefox, Safari

### Step 4: Output
Deliver:
- Clean, commented component code
- CSS/style tokens extracted from design
- Responsive breakpoint documentation
- List of any design ambiguities encountered and decisions made

## Key Rules
- Pixel-perfect is the goal but accessibility trumps visual accuracy
- Use semantic HTML elements (not div soup)
- Extract design tokens (colors, spacing, fonts) into variables
- Document any decisions where the design was ambiguous
- Mobile-first approach — start with the smallest screen and scale up
