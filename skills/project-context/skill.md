---
name: project-context
description: Maintain structured project architecture documentation to eliminate repetitive context-rebuilding each session
---

# Project Context

## Overview
Maintains a structured document of project architecture, tech stack, module responsibilities, API patterns, deployment pipelines, and current project goals. Eliminates the need to rebuild context at the start of each development session.

## When to Use This Skill
- Starting a new project
- When AI tools need project context to be effective
- After major architectural changes
- When onboarding new developers

## Process

### Step 1: Create Project Context Document

```markdown
# Project Context: [Project Name]

## Overview
[2-3 sentences: what this project does and who it serves]

## Tech Stack
- Frontend: [framework, language, state management]
- Backend: [framework, language, database]
- Infrastructure: [hosting, CI/CD, monitoring]
- Key libraries: [list with versions]

## Architecture
[High-level architecture description]
- [Module A]: [responsibility]
- [Module B]: [responsibility]
- [Module C]: [responsibility]

## Key Patterns
- API style: [REST / GraphQL / gRPC]
- Authentication: [method]
- State management: [approach]
- Error handling: [pattern]
- Data fetching: [pattern]

## Directory Structure
[Key directories and their purpose]

## Current Goals
- [ ] [Goal 1]: [status and context]
- [ ] [Goal 2]: [status and context]

## Known Issues / Tech Debt
- [Issue 1]: [impact and planned resolution]
- [Issue 2]: [impact and planned resolution]

## Environment Setup
[How to get the project running locally]
```

### Step 2: Maintenance
- Update after every significant change
- Review weekly for accuracy
- Keep the "Current Goals" section fresh
- Archive completed goals with dates

## Key Rules
- Keep it under 3 pages — this is a reference, not documentation
- Focus on decisions and patterns, not implementation details
- Include the WHY behind architectural choices
- This is not a substitute for code comments or API docs
- Update it or delete it — stale context is worse than no context
