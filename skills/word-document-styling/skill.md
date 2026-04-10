---
name: word-document-styling
description: Automatically format .docx output with custom fonts, colors, heading styles, margins, and spacing
---

# Word Document Styling

## Overview
Automatically formats .docx output to follow custom templates with specific fonts, colors, heading styles, margins, and spacing. Maintains a style configuration and applies it consistently to all Word document outputs.

## When to Use This Skill
- Generating branded reports or proposals
- Creating documents that must match corporate templates
- Ensuring formatting consistency across multiple documents
- Converting markdown to professionally styled Word docs

## Process

### Step 1: Define Style Config
```markdown
# Word Style Config: [Template Name]

## Page Setup
- Paper size: [A4 / Letter]
- Margins: Top [X], Bottom [X], Left [X], Right [X]
- Header/Footer: [content and spacing]

## Typography
- Heading 1: [Font], [Size]pt, [Color], [Bold/Regular], [Spacing before/after]
- Heading 2: [Font], [Size]pt, [Color], [Bold/Regular], [Spacing before/after]
- Heading 3: [Font], [Size]pt, [Color], [Bold/Regular], [Spacing before/after]
- Body: [Font], [Size]pt, [Color], [Line spacing]
- Caption: [Font], [Size]pt, [Color], [Italic]

## Colors
- Primary: #XXXXXX
- Accent: #XXXXXX
- Text: #XXXXXX
- Light background: #XXXXXX

## Elements
- Bullet style: [type and indentation]
- Table header: [background color, font weight]
- Table borders: [style and color]
- Blockquotes: [left border color and indent]
```

### Step 2: Apply Styles
When generating .docx output:
- Apply page setup first
- Map markdown headings to Word heading styles
- Apply body text formatting
- Style tables, lists, and special elements
- Add header/footer with logo if specified

### Step 3: Quality Check
- Verify all headings use correct styles (not manual formatting)
- Check page breaks are logical
- Ensure images are properly sized and positioned
- Validate table formatting consistency

## Key Rules
- Use Word styles (not manual formatting) so documents remain editable
- Test the template with extreme content (very long titles, wide tables)
- Include print-ready settings (bleed, crop marks) if documents will be printed
- Keep font count to 2 maximum (heading + body)
- Provide both .docx and PDF outputs when possible
