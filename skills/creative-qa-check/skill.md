---
name: creative-qa-check
description: Audit drafts for voice authenticity, structure, scanability, and accessibility with prioritized recommendations
---

# Creative QA Check

## Overview
Audits content drafts for voice authenticity, structural coherence, scanability, and accessibility. Produces a prioritized list of recommendations covering tone consistency, paragraph length, heading hierarchy, readability score, and inclusivity.

## When to Use This Skill
- Before sending a draft for review
- After major edits to check nothing broke
- When content feels "off" but you can't pinpoint why
- Final check before publishing

## Process

### Audit Dimensions

**1. Voice Authenticity (if voice profile exists)**
- Compare against established voice profile
- Flag passages that deviate from expected tone
- Check for AI-sounding phrases that crept in
- Verify intentional style choices are preserved

**2. Structure**
- Heading hierarchy (H1 > H2 > H3, no skipping)
- Section length balance (no section 5x longer than others)
- Logical flow (does each section build on the previous?)
- Introduction sets up what follows
- Conclusion delivers on the promise

**3. Scanability**
- Paragraph length (max 3-4 sentences)
- Use of subheadings (every 200-300 words)
- Bullet points and lists where appropriate
- Bold/emphasis on key takeaways
- White space distribution

**4. Readability**
- Flesch-Kincaid grade level
- Sentence length variation
- Passive voice percentage (aim under 10%)
- Jargon density appropriate for audience

**5. Accessibility**
- Image alt text present and descriptive
- Link text is meaningful (not "click here")
- Color is not the only way information is conveyed
- Heading structure supports screen readers

**6. Visual Design (if auditing UI)**
- Font choice: is it Inter/Roboto or something distinctive?
- Color: any purple/blue AI gradients or oversaturated accents?
- Layout: symmetric 3-column grids, centered everything?
- Interactions: hover/focus states present on all clickable elements?
- See `taste-ui-framework` for the full anti-pattern checklist

### Output Format
Produce a prioritized report:
- **Critical** (must fix): Issues that break comprehension or accessibility
- **Important** (should fix): Issues that hurt engagement or clarity
- **Nice to have** (consider): Polish items that improve quality

## Key Rules
- Be specific — "paragraph 3 is too long" not "improve readability"
- Always explain why something matters, not just what's wrong
- Limit to 10 recommendations max to avoid overwhelm
- Positive feedback matters — note what's working well too

## Related Skills

- `taste-ui-framework` — detailed visual anti-pattern checklist for UI-specific audits
- `ui-redesign-audit` — use when the audit results call for visual design fixes
