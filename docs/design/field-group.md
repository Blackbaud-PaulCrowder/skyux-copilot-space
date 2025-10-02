---
component: 'field-group'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the field-group component extracted from SKY UX documentation.'
---

# Field Group Design Guidelines

## Component Overview
Field groups organize related form inputs and controls into semantic and visual groups on long or complex forms.

## Usage

### ✅ Use when

Use field groups to divide long or complex forms into groups of related inputs and controls. Field groups create semantic and visual groups to communicate context and relationships between the elements on a form.

Semantically, a field group creates an HTML fieldset element for its contents. It also creates a legend element and an h3 or h4 heading using the field group label.

Not every form requires field groups. Simple forms with a small number of inputs can use the modal title to establish context and don't require a field group.

Use nested field groups to organize related elements into subgroups in form sections. To communicate hierarchy, adjust heading tags and the visual style of field group labels. For example, you can nest two field groups with h4 headings in a form section with an h3 heading. For more details, see the form design guidelines.

### ❌ Don't use when

Don't use field groups when short or simple forms contain a small number of elements and don't require groups.

Don't use field groups to divide a complex task into multiple steps that users should complete in a particular order. Use a wizard instead.

Don't use field groups for very long forms, especially when users don't need to interact with every group of inputs. Consider using a sectioned form instead.

## Anatomy

- Heading
- Help inline button
- Hint text

## Options

### Heading level and style

By default, field group headings create h3 headings with a sky-font-heading-3 visual style. When nesting field groups, adjust the semantic heading tag and the font style to maintain the semantic and visual hierarchy of the form. For more details, see the form design guidelines.

### Help inline button

When you need to supplement a field group with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a field group, use hint text. This persistent inline help can explain details such as:

- The correct format
- Any constraints on the inputs
- Additional instructions or context, such as how data is used

### Stacked margin

To provide consistent vertical spacing between field groups, use stacked. This adds a bottom margin to visually separate a field group from another field group or other form content below it. For more information about spacing on forms, see the form layout guidelines.

## Content

### Headings

Make field group headings succinct and descriptive. Use nouns for field group headings. Don't use verbs or sentences.

For details about the styling for field group headings, see the "Heading level and style" section on this page.

### Checkbox and radio button groups

Don't use a field group when the only content is a lone checkbox group or radio button group. Instead, adjust the heading level and heading style on the label for the checkbox group or radio button group. For more details, see checkboxes and radio buttons.

For example, if a "General" field group is followed by a "Supported credit cards" section that only includes a checkbox group, use the checkbox group's label to provide an h3 heading with a sky-font-heading-3 visual style. An additional heading from a field group would be unnecessary and confusing.

Use a field group to organize multiple related checkbox groups or radio button groups and also to organize a checkbox group or radio button group with other form fields. To maintain visual hierarchy within the field group, use the label of the checkbox group or radio button group.

## Related information

### Components

- Checkbox
- Help inline button
- Input box
- Radio button
- Sectioned form
- Wizard

### Guidelines

- Form design