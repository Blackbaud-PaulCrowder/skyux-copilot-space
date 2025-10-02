---
component: 'phone-field'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the phone-field component extracted from SKY UX documentation.'
---

# Phone Field Design Guidelines

## Component Overview
The phone field module creates a button, search input, and text input for entering and validating international phone numbers. Phone fields must be wrapped in input boxes to provide styling, ordering, and positioning within forms.

## Usage

### ✅ Use when

Use phone fields to validate phone numbers against the correct format for the selected country.

## Anatomy

### Phone field

### Country selector

- Country selector button
- Label
- Input field
- Default hint text
- Required field marker
- Help inline button
- Additional hint text

## Options

### Default country

By default, the country selector is set to the United States, but you can specify a different default value. You can also set the default dynamically. For example, you can set the default value using location detection.

### Required field marker

When a phone field is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement a phone field label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a phone field, use hint text. This persistent inline help can explain details such as:

- The correct format
- Any constraints on the phone field
- Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a phone field is immediately followed by another form input, use stacked to add a bottom margin that visually separates the phone field from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the phone field:

- Is the last input before a field group
- Is the last input on a form
- Is followed by one or more conditional fields (use sky-margin-stacked-sm instead for closely related fields)

## Behavior and states

### Country selection

The selected country determines the format to use to validate phone numbers. If users enter phone numbers from a different country, they must also select that country to validate phone numbers based on the correct format.

### Phone format validation

The phone field input directive validates phone numbers based on the format for the selected country. You must specify an error message. In most cases, the error message should be "Enter a phone number matching the format for the selected country."

## Related content

### Components

- Field group
- Help inpline button
- Input box

### Guidelines

- Form design