---
component: 'select-field'
description: 'Design guidelines, API documentation, and usage instructions for the select-field component extracted from SKY UX documentation.'
---

# Select Field Component Guidelines

## Component Overview
A select field creates a text input or button to launch a modal picker for users to select items from a searchable, browsable, and filterable list. Select field is deprecated. We will remove it in a future major version. In most cases, we recommend using the lookup component instead, but some scenarios require a different option, such as a selection box component or an HTML <select> element in an input box. For more information, review the select field deprecation instructions.

## Usage

### ✅ Use when

Use select fields when users don't know the exact values to select in long lists of items. For guidance on selection inputs for other scenarios, see the form design guidelines.

### Guidelines

- Form design

## Related information

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### SkySelectFieldPickerContext

Provides values to a custom picker.

**Package:** `@skyux/select-field`

⚠️ **This component is deprecated.**

#### SkySelectFieldComponent

**Selector:** `sky-select-field`

**Package:** `@skyux/select-field`

**Inputs:**

- `ariaLabel`: `string` - The ARIA label for the text input or button. This sets the `aria-label` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the input or button includes a visible label, use `ariaLabelledBy` instead.
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `ariaLabelledBy`: `string` - The HTML element ID of the element that labels
the text input or button. This sets the `aria-labelledby` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the input or button does not include a visible label, use `ariaLabel` instead.
For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).
- `customPicker`: `SkySelectFieldCustomPicker` - The `SkySelectFieldCustomPicker` object that displays a custom UI when users
select the select field button.
- `data`: `Observable<SkySelectField[]>` - Defines a data source to populate the modal picker with items that users can select.
This property accepts an observable array of `SkySelectField` values. The `SkySelectField`
type extends the any type and supports `id`, `label`, and `category` values. **[Required]**
- `inMemorySearchEnabled`: `boolean` - Whether to use the default search function. To circumvent the list-builder search function
and provide search results from a remote source, set this property to `false` and specify the source
with the *data* property. (default: true)
- `multipleSelectOpenButtonText`: `string` - The label for the button when `selectMode` is set to `multiple`. (default: "Select values")
- `pickerHeading`: `string` - The header for the picker. When `selectMode` is set to `"single"`, the default
header is "Select a value." When `selectMode` is set to `"multiple"`, the default header
is "Select values."
- `showAddNewRecordButton`: `boolean` - Whether to display a button in the picker for users to add items. Consumers
must tie into the `addNewRecordButtonClick` event and provide the logic to add items. (default: false)
- `singleSelectClearButtonTitle`: `string` - Tooltip text for the icon that clears the text input when `selectMode`
is set to `"single"`. The clear icon appears after users select an item. (default: "Clear selection")
- `singleSelectOpenButtonTitle`: `string` - Tooltip text for the text input when `selectMode` is set to `"single"`. (default: "Click to select a value")
- `singleSelectPlaceholderText`: `string` - Placeholder text to display in the text input when `selectMode` is set to
`"single"` and no item is selected. (default: "Select a value")
- `descriptorKey`: `string` - The property to highlight in the picker with bold text. The valid options are
the values that the `data` property injects into the component: `"id"`, `"label"`, and `"category"`. (default: "label")
- `disabled`: `boolean` - Whether to disable the text input or button and prevent users
from opening the picker on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync.
To set the disabled state on reactive forms, use the `FormControl` instead. (default: false)
- `selectMode`: `SkySelectFieldSelectMode` - The selection mode that determines whether users can select one item
or multiple items. The valid options are `single`, which displays a text input,
and `multiple`, which displays a button. (default: "multiple")

**Outputs:**

- `addNewRecordButtonClick`: `EventEmitter<void>` - Fires when users select the add button in the picker to add an item. The button appears
when when `showAddNewRecordButton` is set to `true`.
- `blur`: `EventEmitter<any>` - Fires when the component loses focus. This event does not emit a value.
- `searchApplied`: `EventEmitter<string>` - Fires when a search is submitted from the picker's toolbar.

⚠️ **This component is deprecated.**

#### SkySelectFieldModule

**Package:** `@skyux/select-field`

⚠️ **This component is deprecated.**

#### SkySelectFieldCustomPicker

**Package:** `@skyux/select-field`

⚠️ **This component is deprecated.**

#### SkySelectFieldSelectMode

**Package:** `@skyux/select-field`

⚠️ **This component is deprecated.**

#### SkySelectField

Extends the `any` type and supports values for data objects that you can inject into
the select field component to populate the picker.

**Package:** `@skyux/select-field`

⚠️ **This component is deprecated.**

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.