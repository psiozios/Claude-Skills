---
name: voice-profiles
description: Maintain separate voice profiles for different audiences to prevent context confusion when switching
---

# Voice Profiles

## Overview
Maintains separate voice profiles for different audiences (public, technical, executive, casual, coaching). Each profile captures tone, vocabulary level, formality, humor usage, and sentence patterns. Prevents context confusion when switching between audiences.

## When to Use This Skill
- When writing for multiple distinct audiences
- When onboarding new team members to brand voice
- When AI outputs blend tones inappropriately
- When switching between internal and external communication

## Process

### Step 1: Define Audiences
List all distinct audiences you write for. Common splits:
- Public / General audience
- Technical / Developer audience
- Executive / C-suite
- Internal team / Casual
- Coaching / Educational
- Sales / Prospect-facing

### Step 2: Create Profile Per Audience

For each audience, define:

```markdown
# Voice Profile: [Audience Name]

## Tone Spectrum
- Formality: [1-10]
- Warmth: [1-10]
- Authority: [1-10]
- Humor: [none / light / frequent]
- Directness: [1-10]

## Vocabulary
- Jargon level: [avoid / define / assume knowledge]
- Preferred terms: [list]
- Banned terms: [list]
- Acronym policy: [always expand / assume known / context-dependent]

## Structure Preferences
- Sentence length: [short / mixed / long]
- Paragraph length: [1-2 / 2-3 / 3-5 sentences]
- Use of lists: [heavy / moderate / minimal]
- Headers: [frequent / section-level / minimal]

## Example Paragraph
[One paragraph perfectly capturing this voice]

## Common Mistakes
[What goes wrong when AI writes for this audience]
```

### Step 3: Context Switching Protocol
When switching between audiences:
1. Explicitly state which voice profile to use
2. Reference the profile at the start of each writing session
3. Never blend profiles in a single document
4. When unsure, default to the more formal option

## Key Rules
- Each profile must be distinct — if two profiles are similar, merge them
- Include "what NOT to do" examples for each profile
- Update profiles quarterly based on feedback
- Test profiles by having someone guess the target audience from a sample
