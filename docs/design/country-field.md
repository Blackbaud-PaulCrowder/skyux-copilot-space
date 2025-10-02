---
component: 'country-field'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the country-field component extracted from SKY UX documentation.'
---

# Country Field Design Guidelines

## Component Overview
The country field lets users enter search criteria and then select a country from search results. Country fields must be wrapped in input boxes to provide styling, ordering, and positioning within forms.

## Usage

### ✅ Use when

Use country fields when users need to select countries.

## Anatomy

### Search results

- Label
- Input field
- Required field marker
- Help inline button
- Selected country flag
- Hint text

## Options

### Required field marker

When a country field is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement a country field with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a country field, use hint text. This persistent inline help can explain details such as:

- Any constraints on the input
- Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a country field is immediately followed by another form input, use stacked to add a bottom margin that visually separates the country field from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the country field:

- Is the last input before a field group
- Is the last input on a form
- Is followed by one or more conditional fields (use sky-margin-stacked-sm instead for closely related fields)

## Related information

### Components

- Autocomplete
- Field group
- Help inline button
- Input box
- Phone field

### Guidelines

- Form design