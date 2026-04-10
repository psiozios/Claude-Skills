---
name: explainer-graphic
description: Convert complex concepts into visual HTML explainers with step-by-step diagrams and interactive elements
---

# Explainer Graphic

## Overview
Converts complex concepts into visual HTML explainers with analogies, step-by-step diagrams, and interactive elements. Takes a concept and audience level as input, outputs a self-contained HTML page with clear visual explanations.

## When to Use This Skill
- Explaining a technical concept to a non-technical audience
- Creating educational content or documentation
- Building onboarding materials
- Making a complex process understandable

## Process

### Step 1: Concept Intake
- What concept needs explaining?
- Who is the audience? (technical level: beginner / intermediate / expert)
- What do they already know? (starting point)
- What should they understand after? (end point)

### Step 2: Simplification
- Break the concept into 3-5 core components
- Find a real-world analogy that maps to the concept
- Identify the one thing that confuses people most
- Order from simple to complex

### Step 3: Visual Design
Choose visual approach:
- **Flowchart**: For processes with decision points
- **Timeline**: For sequential steps
- **Comparison**: For contrasting approaches
- **Layered**: For systems with abstraction levels
- **Animated**: For cause-and-effect relationships

### Step 4: Build HTML
Create a self-contained HTML file with:
- Clean typography and spacing
- SVG or CSS-based diagrams (no external dependencies)
- Step-by-step progression
- Interactive elements (hover states, click-to-reveal)
- Responsive layout
- Print-friendly version

### Output Structure
```html
<!-- Self-contained, no external deps -->
<html>
<style>/* All styles inline */</style>
<body>
  <section class="intro"><!-- Analogy + hook --></section>
  <section class="steps"><!-- Step-by-step visual --></section>
  <section class="diagram"><!-- Core visual --></section>
  <section class="summary"><!-- Key takeaways --></section>
</body>
</html>
```

## Key Rules
- If you can't explain it simply, you don't understand it well enough
- One concept per explainer — don't cram multiple ideas
- The analogy does 80% of the work — choose it carefully
- Progressive disclosure: show the simple version first, details on demand
- Test with someone from the target audience — if they're confused, simplify
