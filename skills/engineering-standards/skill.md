---
name: engineering-standards
description: Encode team-wide coding conventions, security patterns, and debugging approaches into referenceable form
---

# Engineering Standards

## Overview
Encodes team-wide coding conventions, security patterns, naming conventions, testing requirements, and debugging approaches into a structured, referenceable skill. Ensures consistency across team members and AI-assisted development.

## When to Use This Skill
- Starting a new project or onboarding new team members
- When code reviews reveal inconsistent patterns
- Setting up AI-assisted development workflows
- Establishing or updating team coding standards

## Process

### Step 1: Define Standards Document

```markdown
# Engineering Standards: [Project/Team Name]

## Language & Framework
- Primary language: [e.g., TypeScript]
- Framework: [e.g., Next.js 14]
- Runtime: [e.g., Node 20]

## Naming Conventions
- Files: [kebab-case / camelCase / PascalCase]
- Components: [PascalCase]
- Functions: [camelCase]
- Constants: [SCREAMING_SNAKE_CASE]
- Database: [snake_case]
- CSS classes: [BEM / Tailwind / CSS Modules]

## Code Structure
- Max file length: [lines]
- Max function length: [lines]
- Import order: [external > internal > relative > types]
- Export style: [named vs default]

## Testing
- Minimum coverage: [percentage]
- Required test types: [unit / integration / e2e]
- Naming: test('[action] should [expected result]')
- Mocking policy: [when to mock vs use real implementations]

## Security
- Authentication pattern: [JWT / session / OAuth]
- Input validation: [where and how]
- Secret management: [env vars / vault / etc.]
- Dependency policy: [audit frequency, auto-merge rules]

## Error Handling
- Error format: [structure]
- Logging levels: [when to use each]
- User-facing errors: [guidelines]

## Git
- Branch naming: [feature/xxx, fix/xxx, etc.]
- Commit format: [conventional commits / other]
- PR requirements: [reviews, checks, size limits]
```

### Step 2: Integration
- Reference this document in PR templates
- Include in onboarding documentation
- Use as context for AI-assisted coding
- Review and update quarterly

## Key Rules
- Standards must be enforced by tooling (linters, formatters) where possible
- If a standard can't be automated, it should be in the PR review checklist
- Keep standards minimal — every rule adds cognitive load
- Document the WHY behind non-obvious standards
- Update standards based on team feedback, not just top-down
