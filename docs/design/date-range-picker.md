---
component: 'date-range-picker'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the date-range-picker component extracted from SKY UX documentation.'
---

# Date Range Picker Design Guidelines

## Component Overview
The date range picker's text input and dropdown let users select a date range from a set of well-known options.

## Usage

### ✅ Use when

Use the date range picker when users need to select a range of dates or a single date relative to the current day, such as yesterday.

## Anatomy

- Label
- Select field
- Help inline button
- Hint text

## Options

### Help inline button

When you need to supplement a date range picker label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a date range picker, use hint text. This persistent inline help can explain details such as:

- The correct format
- Any constraints on the input
- Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a date range picker is immediately followed by another form input, use stacked to add a bottom margin that visually separates the date range picker from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the date range picker:

- Is the last input before a field group
- Is the last input on a form
- Is followed by one or more conditional fields (use sky-margin-stacked-sm instead for closely related fields)

## Behavior and states

### Specific range

When users select "Specific range," from and to date fields appear.

### Responsiveness

On smaller viewports, the date fields that appear when users select "Specific range" reflow into a one-column layout.

## Related information

### Components

- Datepicker
- Field group
- Help inline button
- Input box

### Guidelines

- Form design