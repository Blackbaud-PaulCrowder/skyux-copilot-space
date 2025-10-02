---
component: 'timepicker'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the timepicker component extracted from SKY UX documentation.'
---

# Timepicker Design Guidelines

## Component Overview
The timepicker module creates a SKY UX-themed input field and picker for users to enter or select times. Timepickers must be wrapped in input boxes to provide styling, ordering, and positioning within forms.

## Usage

### ✅ Use when

Use timepickers when users need to specify the time of day.

Use two timepickers when users need to specify start and stop times.

### ❌ Don't use when

Don't use timepickers when users need to specify general durations or time spans. Use radio buttons or HTML select fields instead.

## Anatomy

- Label
- Picker button
- Input field
- Picker
- Required field marker
- Help inline button
- Hint text

## Options

### 12-hour timepicker

Use the 12-hour option for regions and users that use 12-hour time designations. This allows users to select hours, minutes, and "AM" or "PM."

### 24-hour timepicker

Use the 24-hour option for regions and users that use 24-hour time designations. This allows users to select hours and minutes.

### Required field marker

When a timepicker is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement a timepicker label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a timepicker, use hint text. This persistent inline help can explain details such as:

- The correct format
- Any constraints on the input
- Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a timepicker is immediately followed by another form input, use stacked to add a bottom margin that visually separates the timepicker from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the timepicker:

- Is the last input before a field group
- Is the last input on a form
- Is followed by one or more conditional fields (use sky-margin-stacked-sm instead for closely related fields)

## Behavior and states

### Keyboard entries

Users can use the keyboard to enter time values in the input field. Times automatically resolve to the correct format when the field loses focus.

## Layout

Use 1/2- or 1/3-width columns for individual timepicker fields inside modals, except when using small (300px) modals. When using two timepickers for start and stop times, use 10px of horizontal space between them.

## Related information

### Components

- Datepicker
- Field group
- Help inline button
- Input box
- Popover
- Radio button

### Guidelines

- Form design