---
name: hero-image-prompt
description: Generate brand-consistent image prompts for AI image generators with automatic visual theme selection
---

# Hero Image Prompt Generator

## Overview
Produces brand-consistent image generation prompts for hero/header images. Takes brand guidelines and content topic as input, outputs detailed prompts for AI image generators (DALL-E, Midjourney, Stable Diffusion) with automatic visual theme selection.

## When to Use This Skill
- Creating header images for blog posts or newsletters
- Generating social media visuals
- Building presentation imagery
- Any time you need on-brand visual content

## Process

### Step 1: Brand Input
Gather brand visual guidelines:
- Color palette (hex codes)
- Visual style (illustration, photography, abstract, minimalist)
- Mood (professional, playful, bold, calm)
- Recurring visual elements or characters
- Things to avoid (stock photo cliches, specific imagery)

### Step 2: Content Analysis
From the article/content, extract:
- Core concept or metaphor
- Emotional tone
- Key visual keywords
- Abstract vs literal representation preference

### Step 3: Theme Selection
Auto-select a visual theme based on content type:
- **Conceptual**: Abstract representations of ideas
- **Metaphorical**: Visual metaphors for the topic
- **Scene-based**: Situational illustrations
- **Data-visual**: Charts, diagrams, or infographic elements
- **Character-driven**: People or mascots in relevant scenarios

### Step 4: Prompt Construction
Build the prompt with these components:
1. **Subject**: What's in the image
2. **Style**: Art direction (illustration style, photography type)
3. **Composition**: Layout, focal point, negative space
4. **Color**: Brand palette application
5. **Mood**: Lighting, atmosphere
6. **Technical**: Aspect ratio, resolution, format

**Output format:**
```
[Generator]: Midjourney / DALL-E / Stable Diffusion
[Prompt]: Full prompt text
[Negative prompt]: What to exclude
[Settings]: Aspect ratio, style parameters
```

## Key Rules
- Always reference brand colors by hex code in prompts
- Avoid text in images (AI generators handle it poorly)
- Generate 3 prompt variations per request (safe, creative, bold)
- Include negative prompts to avoid common AI image issues
- Specify aspect ratios for the target platform
