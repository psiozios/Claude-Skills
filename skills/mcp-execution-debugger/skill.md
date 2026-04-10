---
name: mcp-execution-debugger
description: Generate structured debugging reports for MCP tool chains showing call sequences, failures, and fixes
---

# MCP Execution Debugger

## Overview
Generates structured debugging reports for MCP (Model Context Protocol) tool chains. Maps every tool call in sequence, identifies failures, traces error propagation, and recommends fixes. Essential for diagnosing why an MCP integration isn't working as expected.

## When to Use This Skill
- An MCP tool chain is failing silently or with unclear errors
- Debugging a multi-step MCP workflow
- Verifying a new MCP server integration
- Investigating unexpected MCP behavior

## Process

### Step 1: Capture the Chain
Document the MCP execution sequence:
```
Call 1: [tool_name] → Input: {...} → Output: {...} → Status: OK/FAIL
Call 2: [tool_name] → Input: {...} → Output: {...} → Status: OK/FAIL
...
```

### Step 2: Identify Failure Points
For each failed call:
- **Error type**: Connection, authentication, schema mismatch, timeout, rate limit
- **Error message**: Exact text
- **Input state**: What was passed in
- **Expected vs actual**: What should have happened

### Step 3: Trace Propagation
Map how the failure cascades:
- Did downstream calls use bad data from a failed upstream call?
- Did a partial failure produce misleading "success" results?
- Are retries masking the root cause?

### Step 4: Debug Report
```markdown
## MCP Debug Report

### Summary
- Total calls: X
- Successful: Y
- Failed: Z
- Root cause: [description]

### Call Trace
[Numbered sequence with status]

### Root Cause Analysis
[What failed and why]

### Recommended Fixes
1. [Fix with specific instructions]
2. [Alternative approach if fix 1 doesn't work]

### Prevention
[How to avoid this in the future]
```

## Key Rules
- Always capture the full chain, not just the failing call
- Check authentication/credentials first (most common failure)
- Verify MCP server is running and reachable
- Schema mismatches between versions are a frequent cause
- Log everything during debugging, clean up after
