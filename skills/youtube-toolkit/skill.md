---
name: youtube-toolkit
description: Process YouTube videos for content repurposing by extracting transcripts, key moments, and social snippets
---

# YouTube Toolkit

## Overview
Processes YouTube videos for content repurposing. Extracts transcripts (preferring manual subtitles over auto-generated), identifies key moments and timestamps, generates summaries, pull quotes, and social media snippets.

## When to Use This Skill
- Repurposing video content into written formats
- Creating show notes for podcast/video episodes
- Extracting key quotes for social media
- Building a content library from video archives

## Process

### Step 1: Video Intake
- Accept YouTube URL
- Extract video metadata (title, duration, channel, publish date)
- Download transcript (prefer manual captions > auto-generated)
- Note: if no transcript available, inform user and suggest alternatives

### Step 2: Transcript Processing
- Clean auto-generated transcript (fix punctuation, paragraph breaks)
- Add timestamps at natural topic transitions
- Identify speaker changes (if multiple speakers)

### Step 3: Content Extraction

**Summary** (3 tiers):
- **One-liner**: Single sentence capturing the core message
- **Paragraph**: 3-5 sentence overview
- **Detailed**: Section-by-section summary with timestamps

**Key Moments**:
- Identify 5-10 most quotable/valuable moments
- Include timestamp and context for each
- Flag moments that would make good social clips

**Pull Quotes**:
- Extract 3-5 standalone quotes that work without context
- Clean up verbal tics without changing meaning

### Step 4: Repurposing Outputs
- **Blog post outline**: Structured from the video's main points
- **Social snippets**: 3-5 platform-ready quotes or insights
- **Newsletter section**: Video summary formatted for email
- **Thread**: Key points formatted as a Twitter/X thread

## Key Rules
- Always prefer manual subtitles — auto-generated has errors
- Preserve the speaker's actual words in quotes (don't paraphrase)
- Include timestamps for all references
- Flag low-confidence transcript sections
- Respect fair use — extraction for commentary and repurposing, not reproduction
