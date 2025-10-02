---
component: 'file-drop'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the file-drop component extracted from SKY UX documentation.'
---

# File Drop Design Guidelines

## Component Overview
The file drop element lets users attach multiple local files or link to external files, and it displays summary information about the attachments.

## Usage

### ✅ Use when

Use the file drop element when users need to upload multiple files or attach files from URLs rather than from local devices.

Use the file drop element when users need to add metadata about uploaded files.

### ❌ Don't use when

Don't use the file drop element when users only need to upload a single local file. Use the file attachment component instead.

## Anatomy

- Label
- Option to upload local files
- File name
- File size
- File preview
- Delete button
- Required field marker
- Help inline button
- Option to link to external files
- Hint text
- User-entered metadata

## Options

### Required field marker

When a file drop input is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement a file drop label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Link to external files

You can indicate whether to include the option to attach external files using their URLs.

### Hint text

To highlight important considerations about a file drop input, use hint text. This persistent inline help can explain details such as:

- The correct format
- Any constraints on the input
- Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a file drop input is immediately followed by another form input, use stacked to add a bottom margin that visually separates the file drop input from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the file drop:

- Is the last input before a field group
- Is the last input on a form
- Is followed by one or more conditional fields (use sky-margin-stacked-sm instead for closely related fields)

### Metadata

You can include inputs for users to add metadata about file attachments.

### Validation

You can specify parameters for valid files, including file types, minimum and maximum sizes, and custom validation.

## Behavior and states

### File information

After users attach files, summary information appears below the file drop options. For local files, the default summary includes the file name, file size, file preview, and a delete button. For external files, the default summary includes the URL and a delete button. You can include additional inputs to display user-entered metadata.

### Responsiveness

The file drop element switches to a vertical layout in smaller viewports.

### States

## Related information

### Components

- Field group
- Help inline button
- File attachment

### Guidelines

- Form design