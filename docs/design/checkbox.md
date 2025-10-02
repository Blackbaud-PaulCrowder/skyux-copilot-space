---
component: 'checkbox'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the checkbox component extracted from SKY UX documentation.'
---

# Checkbox Design Guidelines

## Component Overview
Checkboxes let users select multiple items from a short list of items.

## Usage

### ✅ Use when

Use a checkbox when users need to make a yes/no decision about a single question and the changes don't take effect immediately. For example, use a checkbox in a modal where the user confirms the decision before changes take effect.

Use checkbox groups when users must make multiple, related yes/no decisions.

Use icon checkboxes in a checkbox group when the icons are sufficient to clearly communicate the options.

Use checkboxes to enable conditional inputs as part of a task. For 1-3 inputs, disable the inputs until users select the checkbox. For more than 3 inputs, hide the inputs until users select the checkbox.

### ❌ Don't use

Don't use checkbox groups when users need to make multiple selections from homogenous lists of more than 5 items. Use a different selection input, such as a lookup field, instead.

However, checkbox groups can include more than 5 checkboxes when users need to make a series of yes/no decisions about heterogenous options.

Don't use a checkbox when users can toggle between two states or options and changes take place immediately. Use toggle switch instead.

Don't use a checkbox group for a lone checkbox in a form or field group.

However, if the form or field group contains both a checkbox group and a lone checkbox, use a checkbox group for the lone checkbox to differentiate it from the other checkboxes.

## Anatomy

### Individual checkbox

### Checkbox group

### Icon checkbox

- Checkbox
- Label
- Required field marker
- Help inline button
- Hint text

## Options

### Headings

By default, the labels for checkbox groups aren't treated as HTML headings. To emphasize a label as an HTML heading in a form hierarchy, you can use headingLevel to specify a semantic heading level in the document structure and headingStyle to set the heading font style. For example, use a label as a heading to indicate that a checkbox group is a form section just like other field groups. Or use a label as a heading to emphasize a checkbox group as the main section of a form, such as a test or a survey.

In rare cases, you can hide a checkbox group label and use other text to present the checkboxes.

### Required field marker

You can require a checkbox group to force users to meet criteria that you set, such as a minimum or maximum number of checkboxes to select. Use hint text to communicate those constraints. For example, use hint text to tell users to "Select at least one" or "Select no more than three."

In rare cases, you can require a lone checkbox, such as when you need to force users to select a checkbox to agree to terms of use.

When a checkbox or checkbox group is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement a checkbox or checkbox group label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a checkbox or checkbox group, use hint text. This persistent inline help can explain details such as:

- Constraints or requirements on a checkbox group
- Consequences of a choice that may not be apparent
- Additional instructions or context, such as how data is used

### Stacked margin

Checkbox groups automatically add vertical spacing between individual checkboxes. For consistent vertical spacing when a checkbox group is immediately followed by another form input, use stacked to add a bottom margin that visually separates the checkbox group for the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the checkbox group:

- Is the last input inside a field group
- Is the last input on a form

Also use stacked when an individual checkbox is immediately followed by another form input. However, don't use stacked when the checkbox is followed by one or more conditional fields. Use sky-margin-stacked-sm instead for closely related fields.

If a checkbox group uses headingLevel, use stacked when the checkbox group is followed by a field group or another heading. The checkbox group automatically increases the size of the margin to fit the visual hierarchy.

## Content

## Layout

Don't wrap a checkbox group inside a field group component when the checkbox group is the only content.

For example, if a form's "Supported credit cards" section only includes a checkbox group, don't use a field group. Instead, set the checkbox group's headingLevel and headingStyle to 3 to use the label as an h3 heading with a sky-font-heading-3 visual style. An additional heading from a field group would be unnecessary and confusing.

## Accessibility

## Related information

### Components

- Field group
- Lookup
- Modal
- Radio button

### Guidelines

- Form design