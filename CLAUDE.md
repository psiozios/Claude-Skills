# Claude Skills Repository

This repository is a collection of reusable Claude skills. It serves no other purpose.

## Structure

- Each skill lives in its own directory under `skills/<skill-name>/`
- The skill file is always named `skill.md`
- Full path pattern: `skills/<skill-name>/skill.md`

## Creating New Skills

When adding a new skill, follow the formatting and structure defined in the **skill-builder** meta skill at `skills/skill-builder/skill.md`.

### Required YAML Frontmatter

Every skill must have at minimum:

```yaml
---
name: skill-name-here
description: Brief one-sentence description
---
```

Optional properties: `license`, `metadata` (for author, version, tags, etc.)

Do NOT use `allowed-tools` or put `author`/`version`/`tags` at the top level.

## Conventions

- Skill directory names use lowercase with hyphens (e.g., `code-review`, `api-docs`)
- One skill per directory
- Keep skills self-contained within their `skill.md` file
