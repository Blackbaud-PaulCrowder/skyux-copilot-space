---
component: 'datepicker'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the datepicker component extracted from SKY UX documentation.'
---

# Datepicker Design Guidelines

## Component Overview
The datepicker module provides an input and calendar for users to select dates or fuzzy dates. Datepickers must be wrapped in input boxes to provide styling, ordering, and positioning within forms.

## Usage

### ✅ Use when

Use datepickers when users need to enter valid dates.

## Anatomy

- Label
- Input field
- Picker button
- Default hint text
- Picker
- Required field marker
- Help inline button
- Additional hint text
- Key date
- Key date popover
- Disabled date

## Options

### Fuzzy dates

Fuzzy dates allow users to specify dates that are not complete. They enable partial dates when users are unsure of the complete date. For example, if users know the year but not the month or day, they can enter just the year. Supported formats include:

- Month, day, and year
- Month and day
- Month and year
- Year only

### Minimum and maximum dates

You can specify minimum or maximum dates to prevent users from specifying dates before or after those thresholds.

### Start-at date

To initially open the datepicker calendar to a particular date, you can specify a start-at date.

### Required field marker

When a datepicker is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement a datepicker label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Additional hint text

To highlight important considerations about a datepicker, you can extend the default hint text with additional hint text. This persistent inline help can explain details such as:

- Constraints on the input
- Additional instructions or context, such as how data is used

### Key dates

To direct users to dates that are highly relevant to their selections, you can highlight key dates with a red circle indicator in the datepicker calendar. Use key dates sparingly, and only highlight dates when they are likely to impact user selections.

### Disabled dates

You can disable dates to prevent users from selecting them. The datepicker calendar indicates disabled dates with grey, italic text. You can still highlight them as key dates and display key date details in a popover.

### Stacked margin

For consistent vertical spacing when a datepicker is immediately followed by another form input, use stacked to add a bottom margin that visually separates the datepicker from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the datepicker:

- Is the last input before a field group
- Is the last input on a form
- Is followed by one or more conditional fields (use sky-margin-stacked-sm instead for closely related fields)

## Behavior and states

### Month string conversion for fuzzy dates

If users enter months as text instead of numbers, the datepicker converts the text to numbers when the datepicker loses focus.

## Related information

### Components

- Date range picker
- Field group
- Help inline button
- Input box
- Popover

### Guidelines

- Form design