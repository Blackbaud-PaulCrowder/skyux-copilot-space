---
component: 'file-attachment'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the file-attachment component extracted from SKY UX documentation.'
---

# File Attachment Design Guidelines

## Component Overview
The file attachment element lets users attach a single local file.

## Usage

### ✅ Use when

Use the file attachment input when users need to upload a single local file.

### ❌ Don't use when

Don't use the file attachment input when users need to link to a URL to attach an external file. Use the file drop component instead.

Don't use the file attachment input to upload multiple local files. Use the file drop component instead.

## Anatomy

### Before file is attached

### After file is attached

- Label
- File attachment button
- Required field marker
- Help inline button
- Hint text

## Options

### Required field marker

When a file attachment input is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement a file attachment label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about an input, use hint text. This persistent inline help can explain details such as:

- The correct format
- Any constraints on the input
- Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a file attachment input is immediately followed by another form input, use stacked to add a bottom margin that visually separates the file attachment input from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the file attachment:

- Is the last input before a field group
- Is the last input on a form
- Is followed by one or more conditional fields (use sky-margin-stacked-sm instead for closely related fields)

## Behavior and states

### Image preview

When users attach images, a small preview appears below the replace file button.

### File link

When users attach a file, the file name displays as a link beside the replace file button. You must bind an action to the click event to prevent a dead link and to allow users to download the file.

## Related information

### Components

- Field group
- File drop

### Guidelines

- Form design