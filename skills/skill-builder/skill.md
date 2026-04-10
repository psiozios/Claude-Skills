---
name: skill-builder
description: Meta skill that defines how to create and format well-structured, reusable skill.md files for any topic or domain
---

# Skill Builder - Meta Skill for Creating Skills


## Purpose
This meta-skill helps you generate well-structured, reusable skill.md files for any topic or domain. Use this as a template and reference guide when creating new skills.


## How to Use This Skill
1. Identify the topic/domain you want to create a skill for
2. Follow the template structure below
3. Customize each section with domain-specific guidance
4. Test the skill with Claude to ensure it provides effective instructions


## CRITICAL: YAML Frontmatter Requirements


### CORRECT YAML Format


**Minimal Required Format (RECOMMENDED):**
```yaml
---
name: skill-name-here
description: Brief one-sentence description of what this skill does
---
```


**Extended Format (Avoid):**
```yaml
---
name: skill-name-here
description: Brief one-sentence description of what this skill does
license: MIT
metadata:
  author: Your Name
  version: 1.0
  created: 2025-10-18
  tags:
    - tag1
    - tag2
---
```


### COMMON YAML ERRORS TO AVOID


**ERROR 1: Using `allowed-tools` property**
```yaml
# WRONG - This property is NOT supported
---
name: my-skill
description: Does something
allowed-tools:
  - tool1
  - tool2
---
```
**Solution:** Remove `allowed-tools` entirely. Claude skills don't use this property.


**ERROR 2: Quoted name/description when not needed**
```yaml
# WRONG - Unnecessary quotes
---
name: "my-skill"
description: "Does something"
---
```
**Solution:** Only use quotes if the value contains special YAML characters (colons, brackets, etc.)


**ERROR 3: Wrong indentation**
```yaml
# WRONG - Improper indentation
---
name: my-skill
description: Does something
metadata:
author: Someone
version: 1.0
---
```
**Solution:** Use consistent 2-space indentation for nested properties


**ERROR 4: Top-level properties that should be in metadata**
```yaml
# WRONG - author and version must be inside metadata
---
name: my-skill
description: Does something
author: John Doe
version: 1.0
---
```
**Solution:** Move to metadata object:
```yaml
---
name: my-skill
description: Does something
metadata:
  author: John Doe
  version: 1.0
---
```


### Allowed YAML Properties


Only these top-level properties are supported:


1. **name** (required) - String, lowercase with hyphens, no quotes needed
2. **description** (required) - String, can be plain or quoted if contains special chars
3. **license** (optional) - String (e.g., "MIT", "Apache-2.0", "Proprietary")
4. **metadata** (optional) - Object containing any additional fields


### YAML Formatting Rules


1. **No quotes needed** for simple strings (name, description)
2. **Use 2-space indentation** (never tabs)
3. **Use quotes only when** string contains: `:`, `[`, `]`, `{`, `}`, `,`, `&`, `*`, `#`, `?`, `|`, `-`, `<`, `>`, `=`, `!`, `%`, `@`, `` ` ``
4. **Properties order**: name -> description -> license -> metadata
5. **No trailing whitespace**
6. **File ends with single newline**


### Quick YAML Validation Checklist


Before saving your skill.md, verify:
- [ ] YAML starts with `---` and ends with `---`
- [ ] Contains `name` and `description` (required)
- [ ] Does NOT contain `allowed-tools` property
- [ ] Does NOT have top-level `author`, `version`, `tags` (use metadata instead)
- [ ] Uses 2-space indentation consistently
- [ ] No unnecessary quotes on simple strings
- [ ] All nested properties properly indented


## Standard Skill.md Structure


```markdown
---
name: skill-name-here
description: Brief one-sentence description
---


# [SKILL NAME]


## Overview
[Brief 2-3 sentence description of what this skill helps accomplish]


## When to Use This Skill
- [Trigger condition 1]
- [Trigger condition 2]
- [Trigger condition 3]
[Be specific about when Claude should reference this skill]


## Core Principles
[List 3-5 fundamental rules or best practices that should always be followed]


1. **[Principle Name]**: [Clear explanation]
2. **[Principle Name]**: [Clear explanation]
3. **[Principle Name]**: [Clear explanation]


## Step-by-Step Process


### Phase 1: [Planning/Analysis/Setup]
[Detailed instructions for the first phase]


**Actions:**
- [Specific action 1]
- [Specific action 2]
- [Specific action 3]


**Checklist:**
- [ ] [Verification item 1]
- [ ] [Verification item 2]


### Phase 2: [Execution/Implementation]
[Detailed instructions for the main work]


**Actions:**
- [Specific action 1]
- [Specific action 2]


**Best Practices:**
- [Best practice 1]
- [Best practice 2]


### Phase 3: [Review/Finalization]
[Detailed instructions for completing and verifying the work]


**Actions:**
- [Specific action 1]
- [Specific action 2]


**Quality Checks:**
- [ ] [Check 1]
- [ ] [Check 2]


## Common Patterns and Examples


### Pattern 1: [Common Scenario Name]
**When to use:** [Description]
**Approach:**
```
[Example or code snippet if applicable]
```


### Pattern 2: [Common Scenario Name]
**When to use:** [Description]
**Approach:**
```
[Example or code snippet if applicable]
```


## Anti-Patterns (What NOT to Do)


**[Anti-pattern 1]**
- Why it's problematic: [Explanation]
- Instead do: [Correct approach]


**[Anti-pattern 2]**
- Why it's problematic: [Explanation]
- Instead do: [Correct approach]


## Tools and Resources
[List relevant tools, file paths, or resources needed]


- **Tool 1**: [Purpose and when to use]
- **Tool 2**: [Purpose and when to use]
- **Reference**: [Links to documentation or related skills]


## Decision Framework
[Provide a decision tree or flowchart for complex choices]


```
IF [condition 1]
  THEN [action A]
ELSE IF [condition 2]
  THEN [action B]
ELSE
  THEN [action C]
```


## Troubleshooting


### Issue: [Common Problem 1]
**Symptoms:** [How to recognize it]
**Solution:** [How to fix it]


### Issue: [Common Problem 2]
**Symptoms:** [How to recognize it]
**Solution:** [How to fix it]


## Success Criteria
[Define what successful completion looks like]


A successful [outcome] should:
- [Criterion 1]
- [Criterion 2]
- [Criterion 3]


## Advanced Techniques
[Optional advanced strategies for complex scenarios]


### Technique 1: [Name]
[When and how to use this advanced approach]


### Technique 2: [Name]
[When and how to use this advanced approach]


## Related Skills
- [Related skill 1]: [Brief description of relationship]
- [Related skill 2]: [Brief description of relationship]
```


## Key Principles for Effective Skills


### 1. **Clarity and Specificity**
- Use concrete, actionable language
- Avoid vague terms like "consider" or "might want to"
- Provide specific examples and code snippets where relevant


### 2. **Completeness**
- Cover the entire workflow from start to finish
- Include edge cases and error handling
- Address common pitfalls and misconceptions


### 3. **Practical Focus**
- Prioritize real-world applicability
- Include actual examples from the domain
- Provide templates and starter code when possible


### 4. **Hierarchy and Structure**
- Use clear headings and sections
- Progress from simple to complex
- Make it easy to scan and reference quickly


### 5. **Actionability**
- Every section should lead to concrete actions
- Include checklists and verification steps
- Provide decision frameworks for choices


## Domain-Specific Customization Guide


### For Technical/Code Skills:
- Include code examples with comments
- Specify file naming conventions
- Define testing and validation steps
- Reference relevant libraries/frameworks
- Include common error messages and fixes


### For Document Creation Skills:
- Provide formatting guidelines
- Include style and tone guidance
- Specify structural requirements
- Give example templates
- Define quality criteria


### For Analysis/Research Skills:
- Define data gathering methods
- Specify analysis frameworks
- Provide interpretation guidelines
- Include example outputs
- Define confidence levels and caveats


### For Communication/Writing Skills:
- Define audience considerations
- Specify tone and style guidelines
- Provide example phrases/templates
- Include formatting rules
- Define success metrics


## Example: Creating a Skill for [Your Topic]


To create a skill for **[YOUR TOPIC]**, follow these steps:


1. **Define the Scope**
   - What specific problem does this skill solve?
   - What are the boundaries (what's in/out of scope)?


2. **Identify Trigger Conditions**
   - When should Claude use this skill?
   - What keywords or scenarios indicate this skill is needed?


3. **Map the Process**
   - What are the main phases of work?
   - What sequence must be followed?


4. **Document Best Practices**
   - What are the established conventions in this domain?
   - What mistakes do novices commonly make?


5. **Provide Examples**
   - Include 3-5 real examples
   - Show both good and bad approaches


6. **Test and Iterate**
   - Use the skill with Claude
   - Refine based on results
   - Add missing information


## Quick Start Template


Use this minimal template for rapid skill creation:


```markdown
---
name: skill-name-here
description: One sentence description of what this skill does
---


# [SKILL NAME]


## Purpose
[One sentence: what this helps accomplish]


## When to Use
- [Trigger 1]
- [Trigger 2]


## Process
1. **[Step 1]**: [Action]
2. **[Step 2]**: [Action]
3. **[Step 3]**: [Action]


## Key Rules
- [Rule 1]
- [Rule 2]
- [Rule 3]


## Example
[One complete example showing the skill in action]
```


## Maintenance and Updates


Keep your skills effective by:
- Reviewing and updating quarterly
- Adding new examples as they emerge
- Incorporating user feedback
- Removing outdated information
- Cross-referencing with related skills


## Tips for Success


**Do:**
- Start with minimal YAML (just name and description)
- Use real examples from actual use cases
- Keep language clear and direct
- Test the skill before finalizing
- Validate YAML syntax before uploading


**Don't:**
- Add `allowed-tools` to YAML frontmatter
- Put author/version/tags at top level (use metadata instead)
- Make assumptions about prior knowledge
- Use jargon without explanation
- Create overly long sections (break them up)
- Forget to include examples
- Leave out error handling


## YAML Troubleshooting Guide


### "Malformed YAML frontmatter" Error


**Most Common Causes:**


1. **Using unsupported properties**
   - Check: Do you have `allowed-tools`? -> Remove it
   - Check: Do you have top-level `author`, `version`, `tags`? -> Move to metadata


2. **Indentation issues**
   - Solution: Use exactly 2 spaces for each level
   - Never use tabs


3. **Missing required fields**
   - Solution: Must have `name` and `description`


4. **Improper YAML syntax**
   - Solution: Test with a YAML validator
   - Check for unmatched quotes or brackets


**Quick Fix Process:**
1. Strip YAML to minimal: name + description only
2. Test if it uploads
3. If successful, gradually add optional fields (license, metadata)
4. Test after each addition


---


## Usage Instructions


When you want to create a new skill.md:


1. Tell me: "Create a skill for [TOPIC]"
2. I'll use this template to build a comprehensive skill.md with proper YAML
3. Review and refine together
4. Save to `skills/[skill-name]/skill.md`


Example topics:
- "Create a skill for writing API documentation"
- "Create a skill for data visualization with Python"
- "Create a skill for conducting code reviews"
- "Create a skill for creating marketing copy"


## Real-World Example: Correct vs Incorrect


### INCORRECT (Will Fail)
```yaml
---
name: "my-awesome-skill"
description: "Does amazing things"
author: John Doe
version: 1.0
allowed-tools:
  - web-search
  - bash-tool
tags:
  - utility
  - helper
---
```


**Problems:**
- Unnecessary quotes on name/description
- `author`, `version`, `tags` at top level (not in metadata)
- `allowed-tools` is not supported


### CORRECT (Will Work)
```yaml
---
name: my-awesome-skill
description: Does amazing things
metadata:
  author: John Doe
  version: 1.0
  tags:
    - utility
    - helper
---
```


**Why it works:**
- Simple strings without quotes
- All extra properties inside metadata
- No unsupported properties
- Clean, minimal structure
