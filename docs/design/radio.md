---
component: 'radio'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the radio component extracted from SKY UX documentation.'
---

# Radio Design Guidelines

## Component Overview
Radio buttons let users select one item from a short list of items.

## Usage

### ✅ Use when

Use radio button groups when users must choose one option from a set of 2-5. Use radio buttons in modals where users confirm decisions before changes take effect.

Use icon radio button groups when icons clearly communicate the options.

Use radio buttons to enable conditional inputs. For options that enable 1-3 inputs, disable the inputs until users select the radio buttons. For options that enable more inputs, hide the inputs until users select the radio buttons. If all options in a radio button group enable conditional inputs or significantly change the workflow, consider using action buttons instead. See the form layout guidelines for more information.

### ❌ Don't use when

Don't use radio buttons when users must choose from more than five items. Use a different selection input instead.

Don't use radio buttons for two options that are exact opposites. Use a checkbox instead.

Don't use radio buttons when user selections significantly alter the workflow. Use action buttons instead, and place them at the beginning of the task.

## Anatomy

### Individual radio button

### Radio button group

### Icon radio button group

- Radio button
- Label
- Help inline button
- Hint text

## Options

### Headings

By default, the labels for radio button groups aren't treated as HTML headings. To emphasize a label as an HTML heading in a form hierarchy, you can use headingLevel to specify a semantic heading level in the document structure and headingStyle to set the heading font style. For example, use a label as a heading to indicate that a radio button group is a form section just like other field groups. Or use a label as a heading to emphasize a radio button group as the main section of a form, such as a test or a survey.

In rare cases, you can hide radio button group label text and use other text to present the radio buttons.

### Required field marker

In rare cases, you can make a radio button group required and leave every option unselected to force users to select an option. When a radio button group is required, a red asterisk appears to the right of the radio group label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

You can't make individual radio buttons required.

### Help inline button

When you need to supplement a radio button or radio button group label with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a radio button or radio button group, use hint text. This persistent inline help can explain details such as:

- Consequences of a choice that may not be apparent
- Additional instructions or context, such as how data is used

### Stacked margin

Radio button groups automatically add vertical spacing between individual radio buttons. For consistent vertical spacing when a radio button group is immediately followed by another form input, use stacked to add a bottom margin that visually separates the radio button group from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the radio button group:

- Is the last input inside a field group
- Is the last input on a form

If a radio button group uses headingLevel, use stacked when the radio button group is followed by a field group or another heading. The radio button group automatically increases the size of the margin to fit the visual hierarchy.

## Content

## Layout

Don't wrap a radio button group inside a field group component if the radio button group is the only content.

In this example, “Payment processing mode” should be the heading of the radio button group, with headingLevel and headingStyle set to 3 in the component options. An additional field group and label around the radio button group is unnecessary and confusing.

## Accessibility

## Related information

### Components

- Action buttons
- Checkbox
- Field group
- Help inline button
- Modal

### Guidelines

- Form design