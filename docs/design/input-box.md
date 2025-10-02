---
component: 'input-box'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the input-box component extracted from SKY UX documentation.'
---

# Input Box Design Guidelines

## Component Overview
Input boxes wrap data entry elements to provide styling, ordering, and positioning within forms.

## Usage

### ✅ Use when

Use input boxes when users need to enter data on forms. Input boxes provide styling for data entry elements, such as basic text fields, text areas, and SKY UX components.

Use input boxes when forms include native HTML elements for text and selection, such as <input>, <select>, and <textarea>. To determine whether to use the HTML <select> element or a SKY UX component, see the form design guidelines.

Use input boxes when forms include SKY UX components, such as country fields, datepickers, lookup fields, phone fields, and timepickers.

## Anatomy

- Label
- Input field
- Required field marker
- Help inline button
- Hint text

## Options

### Required field marker

When an input is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement an input box label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about an input, use hint text. This persistent inline help can explain details such as:

- The correct format
- Any constraints on the input
- Additional instructions or context, such as how data is used

### Character count

When users are likely to exceed a character limit, use a character count indicator. Character count indicators are useful when technical requirements lead to restrictive character limits and when free-form user entries may be very long.

### Stacked margin

For consistent vertical spacing when a form input is immediately followed by another form input, use stacked to add a bottom margin that visually separates the form input from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the form input:

- Is the last input before a field group
- Is the last input on a form
- Is followed by one or more conditional fields (use sky-margin-stacked-sm instead for closely related fields)

### Suggested text

## Behavior and states

### Errors

When an input is in an error state, it provides visual indication with a red border and displays an error message under the input. For users of assistive technologies, the message is also read out and programmatically associated with the input. For more information, see the error-handling guidelines.

## Content

Make input labels succinct and descriptive. Use nouns for input labels. Don't use verbs or questions.

## Layout

Input boxes are most common inside modals and follow form design guidelines. For two-column or three-column layouts, use fluid grid's small gutters spacing option to apply vertical and horizontal padding evenly.

## Related information

### Components

- Character count
- Country field
- Datepicker
- Field group
- Fluid grid
- Help inline button
- Lookup
- Modal
- Phone field
- Timepicker

### Guidelines

- Error handling
- Form design
- Spacing