---
component: 'lookup'
type: 'design-guidelines'
description: 'Design guidelines and usage instructions for the lookup component extracted from SKY UX documentation.'
---

# Lookup Design Guidelines

## Component Overview
The lookup text input lets users search a long list of options and make selections. Lookup fields must be wrapped in input boxes to provide styling, ordering, and positioning within forms.

## Usage

### ✅ Use when

Use lookup fields when users must choose one or more options from a very long list or from an unpredictable list with unfamiliar options. Lookup fields allow users to enter search criteria to narrow their options, so they are useful when lists are unique to the system. For example, use lookup fields for user-defined lists such as code tables where the options are unpredictable and for system-defined lists such as templates where the options are unique to the organization.

Use lookup fields when users can choose multiple options from a long list.

Use lookup fields when users can add options to the list during their tasks.

### ❌ Don't use when

Don't use lookup fields when short lists include 5 options or fewer, especially if it is valuable for users to see all options at once. Use checkboxes or radio buttons instead.

Don't use lookup fields when options are highly predictable or when users can easily browse options in an expected order. Use HTML select fields instead. For example, while a list of states is long, it's predictable and most users are familiar with the options, so the native HTML select field is the preferable option.

Don't use lookup fields when users need to interact with the selected options or when the options require more depth than lookup tokens provide. Instead, use a button to open a selection modal where users can select options, and then display selections in whatever format is needed.

## Anatomy

### Search results

- Label
- Search button
- Input field
- Required field marker
- Help inline button
- Hint text

## Options

### Single-select and multi-select

Use a single-select to let users select a single option and multi-select to let users select multiple options.

### Required field marker

When a lookup field is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement a lookup field with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a lookup field, use hint text. This persistent inline help can explain details such as:

- The correct format
- Any constraints on the input
- Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a lookup field is immediately followed by another form input, use stacked to add a bottom margin that visually separates the lookup from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the lookup:

- Is the last input before a field group
- Is the last input on a form
- Is followed by one or more conditional fields (use sky-margin-stacked-sm instead for closely related fields)

### Button to view all options

The 'Show all/matches' button in the lookup menu lets users open a picker that either displays all options or just the options that match their search string. This button is technically optional for backwards compatibility, but we strongly recommend that you enable it in all instances.

### Custom results template

Use a custom results template when users need more information in the search results to help them select the correct options.

### Custom picker

By default, the search and "Show all/matches" buttons display a selection modal with a selectable repeater. When different presentations are valuable, use custom pickers, such as custom repeaters or tree views. By default, both the native picker and custom pickers format options based on the same template as the dropdown list, but you can specify a different template to format the picker options as necessary.

## Behavior and states

### Behavior

When users place focus on lookup fields, the lookup menu displays the 'Show all #' button. It also displays the 'New' button if that is enabled.

When users enter the minimum number of characters for search, the lookup menu displays search results and highlights the search string. The “Show all #” button label changes to “Show matches (#)."

At any time, users can select the search or 'Show all/matches' buttons to open a picker that either displays all options or the options that match their search string.

When users choose an option in single-select mode, the lookup menu or picker closes, and the selected option appears as text in the lookup field.

When users choose options in multi-select mode, the selected options appear as tokens in the text input field, and focus returns to the lookup field. The lookup menu displays the 'Show all #' button but does not display search results until users enter the minimum number of characters.

When users remove focus before selecting an option, the lookup field deletes any text.

## Related information

### Components

- Checkbox
- Field group
- Help inline button
- Input box
- Radio button
- Selection modal

### Guidelines

- Form design