---
component: 'text-editor'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the text-editor component extracted from SKY UX documentation.'
---

# Text Editor Design Guidelines

## Component Overview
Text editors let users format and manipulate text.

## Usage

### ✅ Use when

Use text editors when users need to create blocks of text that include formatted text, hyperlinks, or merge fields.

### ❌ Don't use when

Don't use the text editor when users only need to enter unformatted plain text. Use a text input or textarea instead.

## Anatomy

- Label
- Text entry area
- Required field marker
- Help inline button
- Menus
- Toolbar actions
- Hint text

## Options

### Required field marker

When a text editor is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement the text editor label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Menus and toolbar

Default menus:

- Edit
- Format

Optional menu:

- Merge

Default toolbar actions:

- Font
- Text size
- Text style (bold/italic/underline)
- Text color
- Highlight color
- List format (numbered/bulleted)
- Hyperlink

Optional toolbar actions:

- Alignment (left/center/right)
- Undo/redo
- Indentation

### Hint text

To highlight important considerations about a text editor, use hint text. This persistent inline help can explain details such as:

- The correct format
- Any constraints on text editor content
- Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a text editor is immediately followed by another form input, use stacked to add a bottom margin that visually separates the text editor from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the text editor:

- Is the last input before a field group
- Is the last input on a form

## Related information

### Components

- Field group
- Help inline button

### Guidelines

- Form design