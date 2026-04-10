---
name: job-description-analyzer
description: Analyze job postings against your profile to provide compatibility scores and tailored application recommendations
---

# Job Description Analyzer

## Overview
Reads job postings and compares them against a user profile (skills, experience, preferences). Provides compatibility scores, identifies gaps, highlights strengths, and generates tailored application recommendations including resume bullet points to emphasize.

## When to Use This Skill
- Evaluating whether to apply for a position
- Tailoring a resume for a specific role
- Understanding what skills to develop for target roles
- Comparing multiple job opportunities

## Process

### Step 1: Parse Job Description
Extract:
- **Required skills**: Must-have qualifications
- **Preferred skills**: Nice-to-have qualifications
- **Responsibilities**: Day-to-day work
- **Seniority signals**: Years of experience, leadership expectations
- **Culture signals**: Values, work style, team dynamics
- **Red flags**: Unrealistic requirements, vague descriptions

### Step 2: Compare Against Profile
Score each dimension:
- **Skills match**: Required skills you have / total required
- **Experience match**: Your experience level vs required
- **Responsibility fit**: How closely your past work aligns
- **Growth opportunity**: New challenges vs comfort zone
- **Culture fit**: Values and work style alignment

### Step 3: Generate Report

```markdown
## Job Fit Analysis: [Role] at [Company]

### Overall Score: [X/100]

### Strengths (Lead with these)
- [Strength 1]: [Why it's relevant + resume bullet to emphasize]
- [Strength 2]: [Why it's relevant + resume bullet to emphasize]

### Gaps (Address proactively)
- [Gap 1]: [How to frame it positively]
- [Gap 2]: [Transferable skill that covers it]

### Red Flags
- [Concern 1]: [What to ask about in the interview]

### Recommendation
[Apply / Apply with caveats / Skip — with reasoning]

### Cover Letter Angle
[The one story or angle that best positions you for this role]
```

## Key Rules
- Be honest about gaps — false confidence wastes everyone's time
- "Required" skills are often wishlists — 70% match is usually enough
- Focus on transferable skills when there's not a direct match
- Red flags are information, not dealbreakers — investigate further
- Tailor every application — generic applications get generic results
