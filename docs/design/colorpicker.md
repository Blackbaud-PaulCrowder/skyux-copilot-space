---
component: 'colorpicker'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the colorpicker component extracted from SKY UX documentation.'
---

# Colorpicker Design Guidelines

## Component Overview
Colorpickers let users select a color using a variety of input methods.

## Usage

### ✅ Use when

Use colorpickers when users needs to visually select color values or specify specific hexadecimal or RGBa color values.

## Anatomy

### Colorpicker button

### Colorpicker dropdown

- Label
- Colorpicker button
- Required field marker
- Help inline button
- Reset button
- Hint text

## Options

### Required field marker

When a colorpicker is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement a colorpicker label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Reset button

To allow users to clear their color selection and revert to the default value, include the reset button.

### Hint text

To highlight important considerations about a colorpicker, use hint text. This persistent inline help can explain details such as:

- Consequences of a choice that may not be apparent
- Additional instructions or context, such as how data is used

### Transparency slider

To allow users to set a transparency level or alpha channel level, include the transparency slider.

### Preset color swatches

To present users with up to 12 colors to select directly, use preset color swatches.

### Stacked margin

For consistent vertical spacing when a colorpicker is immediately followed by another form input, use stacked to add a bottom margin that visually separates the file attachment from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the colorpicker:

- Is the last input before a field group
- Is the last input on a form

## Related information

### Components

- Field group
- Help inline button

### Guidelines

- Form design