---
name: slides-presentation
description: Generate complete HTML presentations with animations and speaker notes from simple prompts
---

# Slides Presentation Builder

## Overview
Generates complete, animated HTML presentations from simple prompts without requiring PowerPoint or Keynote. Uses reveal.js or similar frameworks to create professional slide decks with transitions, speaker notes, and visual hierarchy.

## When to Use This Skill
- Creating presentations quickly from an outline
- Building shareable web-based slide decks
- Generating pitch decks, team updates, or training materials
- When you don't have access to presentation software

## Process

### Step 1: Content Intake
Gather presentation requirements:
- Topic and audience
- Key message / thesis
- Number of slides (or let the content dictate)
- Style preference (minimal, corporate, bold, playful)
- Any required brand colors/fonts

### Step 2: Outline Generation
Create a slide-by-slide outline:
- **Title slide**: Topic, presenter, date
- **Agenda/Overview**: 3-5 main sections
- **Content slides**: One idea per slide, max 6 bullet points
- **Transition slides**: Section dividers
- **Summary/CTA**: Key takeaways and next steps

### Step 3: Build HTML
Generate a self-contained HTML file using reveal.js:
- Semantic slide structure
- CSS styling matching brand or chosen theme
- Slide transitions (fade, slide, zoom)
- Speaker notes in `<aside class="notes">` tags
- Responsive layout

### Step 4: Refinement
- Check slide count (aim for 1 slide per minute of talk time)
- Verify text is readable (max 6 lines, 6 words per line)
- Ensure visual hierarchy (title > subtitle > body)
- Add speaker notes for each slide
- Test in browser

## Key Rules
- One idea per slide — if you need two bullets to explain, it's two slides
- No walls of text — use visuals, diagrams, or short phrases
- Speaker notes carry the detail, slides carry the message
- Title slides should be immediately understandable without explanation
- Always include a "so what" — every slide answers why the audience should care
