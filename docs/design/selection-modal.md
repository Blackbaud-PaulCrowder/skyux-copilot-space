---
component: 'selection-modal'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the selection-modal component extracted from SKY UX documentation.'
---

# Selection Modal Design Guidelines

## Component Overview
Selection modals let users select from a list of options. The lookup component is preferable for most selection tasks, but selection modals are useful when users need to take immediate action on selections.

## Usage

### ✅ Use when

Use selection modals when users need to select options from a long or unpredictable list and then immediately interact with the selections. If users only need to select options, use the lookup component instead.

Use buttons to open selection modals. After users select options, display selections in a format or pattern that supports the next interaction.

### ❌ Don't use when

Don't use selection modals when users only need to select options. Instead, use lookup fields.

Don't use selection modals for five or fewer options. Instead, use checkboxes or radio buttons.

Don't use selection modals when a list of options requires a format other than a simple selectable repeater. If a list requires a different format, such as a custom repeater template or a tree view, or if users require filters to find and select options, create a custom modal with the appropriate features.

## Anatomy

- Modal
- Search
- Multiselect toolbar (multiselect only)
- Unselected option
- Selected option
- New button

## Options

### Single-select and multiselect

Use single-select mode to limit users to a single option, and use multiselect mode to let them select multiple options.

### Button to create options

If users may need to add options to the list, include a button to start the workflow to create options. After users create options, they are selected in the selection modal.

## Behavior and states

### List scrolling

Long lists inside selection modals use infinite scroll.

### Presentation of selected options

Selection modals don't provide a default presentation of selected options. When users close selection modals, present the selected options in a format that matches the needs of the scenario.

## Content

### Modal title text

Use the following format for selection modal titles, and use plural objects when using multiselect:

Select <direct object>

### Modal footer buttons

Use Select as the standard label for the primary button. Use Cancel as the standard label for the link button.

## Related information

### Components

- Checkbox
- Lookup
- Radio button

### Guidelines

- Form design