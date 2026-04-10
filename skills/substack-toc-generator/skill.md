---
name: substack-toc-generator
description: Automatically create numbered tables of contents with working anchor links for long-form Substack posts
---

# Substack TOC Generator

## Overview
Automatically creates numbered tables of contents with working internal anchor links for long-form Substack posts. Scans headings, generates anchors, and outputs formatted markdown ready to paste.

## When to Use This Skill
- Publishing a long-form post (1500+ words)
- Posts with 4+ sections
- Tutorial or guide-style content
- Any post where readers need to jump between sections

## Process

### Step 1: Scan Content
Parse the post content and extract all headings (H2, H3).

### Step 2: Generate Anchors
For each heading, create a URL-friendly anchor:
- Convert to lowercase
- Replace spaces with hyphens
- Remove special characters
- Handle duplicate headings with numeric suffixes

### Step 3: Build TOC
Output formatted markdown:

```markdown
## Table of Contents

1. [Section Title](#section-title)
2. [Another Section](#another-section)
   1. [Subsection](#subsection)
3. [Final Section](#final-section)
```

### Step 4: Verify Links
- Confirm each anchor matches a heading in the post
- Check for duplicates
- Validate special character handling

## Key Rules
- Only include H2 and H3 (deeper nesting clutters the TOC)
- Substack uses `§` prefix for anchors — format as `#§section-name` when needed
- Indent H3s under their parent H2
- Keep section titles concise in the TOC (abbreviate if the heading is very long)
- Place TOC immediately after the introduction paragraph
