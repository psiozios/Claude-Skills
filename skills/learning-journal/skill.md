---
name: learning-journal
description: Automatically extract and organize learning moments from conversations into a categorized knowledge base
---

# Learning Journal

## Overview
Automatically extracts and organizes learning moments, insights, and aha-moments from conversations and work sessions. Categorizes by topic, tags with themes, and maintains a searchable knowledge base that grows over time.

## When to Use This Skill
- At the end of a work session or conversation
- After learning something surprising or non-obvious
- When you want to capture context around a decision
- Building a personal knowledge management system

## Process

### Step 1: Capture
At the end of a session, extract:
- **Key insight**: What did I learn that I didn't know before?
- **Context**: What was I working on when I learned this?
- **Source**: Where did this insight come from?
- **Surprise factor**: Was this expected or unexpected?

### Step 2: Categorize
Tag each entry with:
- **Topic**: Technical, strategic, interpersonal, domain knowledge
- **Project**: Which project or initiative
- **Type**: Fact, pattern, mistake, best practice, mental model
- **Confidence**: High / medium / low (how sure am I?)

### Step 3: Format Entry
```markdown
## [Date]: [One-line summary]

**Category**: [topic] | **Type**: [type] | **Confidence**: [level]
**Context**: [What I was working on]

### Insight
[2-3 sentences describing what I learned]

### Why It Matters
[How this changes my thinking or approach]

### Connected To
[Links to related journal entries or resources]
```

### Step 4: Periodic Review
- Weekly: Scan recent entries for patterns
- Monthly: Identify recurring themes
- Quarterly: Consolidate insights into principles
- Archive entries that are no longer relevant

## Key Rules
- Capture immediately — insights fade fast
- Focus on surprising or non-obvious learnings
- Include the context, not just the fact (context makes it retrievable)
- Review regularly — unreviewed journals are just diaries
- Quality over quantity — one genuine insight beats ten observations

## Related Skills
- **[second-brain](../second-brain/skill.md)** — The richer alternative when you want cross-linked, cited, queryable knowledge that compounds. `learning-journal` is chronological capture; `second-brain` is an interlinked wiki you can query. Use `learning-journal` for quick end-of-session capture; use `second-brain` when you want those insights stitched into a growing knowledge base. A learning-journal entry can become a source for `/second-brain ingest` if it grows into something worth linking.
