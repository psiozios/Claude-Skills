---
name: verify-work
description: Pre-shipping review checklist catching unused imports, debug statements, edge cases, and incomplete work
---

# Verify Work

## Overview
Pre-shipping review that catches common issues before deployment. Checks for unused imports, console.logs, debug statements, TODO comments, edge cases, incomplete error handling, and accessibility issues. Acts as a final gate before committing or deploying.

## When to Use This Skill
- Before committing code changes
- Before creating a pull request
- After a large refactor
- As a final check before deployment

## Process

### Checklist

**1. Code Cleanliness**
- [ ] No unused imports or variables
- [ ] No console.log / print / debug statements
- [ ] No commented-out code blocks
- [ ] No TODO/FIXME/HACK comments left unresolved
- [ ] No hardcoded values that should be config/env

**2. Error Handling**
- [ ] All async operations have error handling
- [ ] API calls handle timeout and network errors
- [ ] User-facing errors have helpful messages
- [ ] Errors are logged appropriately (not swallowed silently)

**3. Edge Cases**
- [ ] Empty states handled (empty lists, null values)
- [ ] Loading states present for async operations
- [ ] Large data sets don't break the UI
- [ ] Concurrent access/race conditions considered

**4. Security**
- [ ] No secrets or API keys in code
- [ ] User input is sanitized
- [ ] Authentication checks are in place
- [ ] No SQL injection or XSS vulnerabilities

**5. Accessibility**
- [ ] Images have alt text
- [ ] Interactive elements are keyboard accessible
- [ ] Color is not the sole indicator of state
- [ ] ARIA labels on non-standard elements

**6. Performance**
- [ ] No unnecessary re-renders or recomputation
- [ ] Large lists are virtualized
- [ ] Images are optimized and lazy-loaded
- [ ] No N+1 query patterns

### Output
- **Pass/Fail** for each category
- **Specific issues** with file paths and line numbers
- **Severity**: Critical / Warning / Info
- **Suggested fixes** for each issue

## Key Rules
- Run this BEFORE asking for code review (don't waste reviewers' time on lint issues)
- Critical issues block shipping — no exceptions
- Warnings should be addressed or explicitly documented as accepted risk
- Add any project-specific checks to the checklist over time
