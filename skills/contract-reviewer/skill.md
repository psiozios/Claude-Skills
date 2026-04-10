---
name: contract-reviewer
description: Analyze contracts to surface key terms, obligations, deadlines, red flags, and missing protections
---

# Contract Reviewer

## Overview
Analyzes contracts and legal documents to surface key terms, obligations, deadlines, red flags, and missing protections. Provides a plain-language summary of commitments and risks. Note: this is not legal advice — always consult a lawyer for final decisions.

## When to Use This Skill
- Reviewing a vendor or service agreement
- Before signing a partnership contract
- Evaluating employment agreements or NDAs
- Understanding terms of service or licensing agreements

## Process

### Step 1: Document Intake
- Accept the contract text
- Identify the contract type (service agreement, NDA, employment, license, etc.)
- Identify the parties involved

### Step 2: Extract Key Terms
- **Parties**: Who is bound by this agreement
- **Term**: Start date, end date, renewal conditions
- **Scope**: What's included and excluded
- **Compensation**: Payment terms, amounts, schedules
- **Deliverables**: What each party must provide
- **Termination**: How either party can exit

### Step 3: Flag Issues

**Red Flags:**
- Unlimited liability or uncapped indemnification
- Auto-renewal with difficult cancellation
- Non-compete clauses that are overly broad
- IP assignment beyond the scope of work
- Unilateral modification rights
- Jurisdiction in an unfavorable location

**Missing Protections:**
- No limitation of liability
- No data protection or privacy terms
- No dispute resolution process
- No force majeure clause
- No confidentiality provisions

### Step 4: Output Report
```markdown
## Contract Review: [Contract Name]

### Plain Language Summary
[What this contract means in everyday language]

### Key Obligations
| Party | Obligation | Deadline |
|-------|-----------|----------|

### Financial Terms
[Payment amounts, schedules, conditions]

### Red Flags (⚠️)
[Issues requiring attention]

### Missing Protections
[Standard clauses that are absent]

### Negotiation Suggestions
[Specific changes to request]

### Overall Risk: [Low / Medium / High]
```

## Key Rules
- This is analysis, NOT legal advice — always recommend consulting a lawyer
- Flag anything unusual, even if it might be standard in some industries
- Focus on what's missing as much as what's present
- Use plain language — if the user needs a lawyer to understand the review, it's useless
- Highlight time-sensitive items prominently
