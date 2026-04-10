---
name: brand-design-system
description: Apply visual branding (colors, fonts, spacing, logos) automatically to documents and presentations
---

# Brand Design System

## Overview
Maintains and applies visual branding (logos, colors, fonts, spacing rules) automatically to documents, presentations, and digital outputs. Ensures all produced materials are brand-consistent without manual design work.

## When to Use This Skill
- Creating any branded document or presentation
- Onboarding a new brand identity
- Checking existing materials for brand compliance
- Generating CSS/style configurations from brand guidelines

## Process

### Step 1: Brand Config Setup
Create a brand configuration:

```markdown
# Brand Config: [Brand Name]

## Colors
- Primary: #XXXXXX
- Secondary: #XXXXXX
- Accent: #XXXXXX
- Background: #XXXXXX
- Text: #XXXXXX
- Error/Warning: #XXXXXX

## Typography
- Headings: [Font family], [weight], [sizes H1-H4]
- Body: [Font family], [weight], [size], [line-height]
- Mono/Code: [Font family], [size]

## Spacing
- Base unit: [Xpx]
- Section padding: [value]
- Element margins: [value]

## Logo
- Placement: [top-left / center / etc.]
- Minimum size: [dimensions]
- Clear space: [requirements]
- Dark/light variants: [when to use each]

## Visual Rules
- Border radius: [value]
- Shadow style: [value]
- Image treatment: [rounded / sharp / masked]
```

### Step 2: Application
Apply the config to outputs:
- **HTML/CSS**: Generate stylesheet from config
- **Presentations**: Apply to slide templates
- **Documents**: Format headings, body, accent elements
- **Social**: Size and style for platform specs

### Step 3: Compliance Check
Review any output against the brand config:
- Color usage matches palette
- Typography is correct
- Spacing follows the grid
- Logo placement follows rules

## Key Rules
- Brand config is the single source of truth — never improvise
- When in doubt, use the primary color and heading font
- Always provide dark mode alternatives if applicable
- Test outputs at multiple screen sizes
- Update the config when brand guidelines change
