                 

 Select field (deprecated)
=========================

A select field creates a text input or button to launch a modal picker for users to select items from a searchable, browsable, and filterable list.

Select field is deprecated. We will remove it in a future major version. In most cases, we recommend using the [lookup](/skyux/components/lookup.md) component instead, but some scenarios require a different option, such as a [selection box](/skyux/components/selection-box.md) component or an HTML `<select>` element in an [input box](/skyux/components/input-box.md). For more information, review the [select field deprecation instructions](/skyux/learn/develop/deprecation/select-field.md).

 Usage
------

### Use when

Use select fields when users don't know the exact values to select in long lists of items. For guidance on selection inputs for other scenarios, see the [form design guidelines](/skyux/design/guidelines/form-design#selection-inputs.md).

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design#selection-inputs.md)

 Installation
-------------

NPM package

`@skyux/select-field`[View in NPM](https://www.npmjs.com/package/@skyux/select-field) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/select-field/src/lib/modules/select-field/select-field.module.ts#L12) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/select-field`Copy None found.

 SkySelectFieldModule
---------------------

Type: Module

`import { SkySelectFieldModule } from '@skyux/select-field';`

Warning: **Deprecated.** `SkySelectFieldComponent` is deprecated. Use `SkyLookupComponent` instead.

 SkySelectFieldComponent
------------------------

Type: Component

Selector: `sky-select-field`

Warning: **Deprecated.** `SkySelectFieldComponent` is deprecated. Use `SkyLookupComponent` instead.

### Inputs

#### `data: Observable<SkySelectField[]>`

Required

Defines a data source to populate the modal picker with items that users can select. This property accepts an observable array of `SkySelectField` values. The `SkySelectField` type extends the any type and supports `id`, `label`, and `category` values.

#### `ariaLabel: string`

The ARIA label for the text input or button. This sets the `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the input or button includes a visible label, use `ariaLabelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `ariaLabelledBy: string`

The HTML element ID of the element that labels the text input or button. This sets the `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the input or button does not include a visible label, use `ariaLabel` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `customPicker: SkySelectFieldCustomPicker`

The `SkySelectFieldCustomPicker` object that displays a custom UI when users select the select field button.

#### `descriptorKey: string`

The property to highlight in the picker with bold text. The valid options are the values that the `data` property injects into the component: `"id"`, `"label"`, and `"category"`.

Default: `"label"`

#### `disabled: boolean`

Whether to disable the text input or button and prevent users from opening the picker on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `inMemorySearchEnabled: boolean`

Whether to use the default search function. To circumvent the list-builder search function and provide search results from a remote source, set this property to `false` and specify the source with the _data_ property.

Default: `true`

#### `multipleSelectOpenButtonText: string`

The label for the button when `selectMode` is set to `multiple`.

Default: `"Select values"`

#### `pickerHeading: string`

The header for the picker. When `selectMode` is set to `"single"`, the default header is "Select a value." When `selectMode` is set to `"multiple"`, the default header is "Select values."

#### `selectMode: SkySelectFieldSelectMode`

The selection mode that determines whether users can select one item or multiple items. The valid options are `single`, which displays a text input, and `multiple`, which displays a button.

Default: `"multiple"`

#### `showAddNewRecordButton: boolean`

Whether to display a button in the picker for users to add items. Consumers must tie into the `addNewRecordButtonClick` event and provide the logic to add items.

Default: `false`

#### `singleSelectClearButtonTitle: string`

Tooltip text for the icon that clears the text input when `selectMode` is set to `"single"`. The clear icon appears after users select an item.

Default: `"Clear selection"`

#### `singleSelectOpenButtonTitle: string`

Tooltip text for the text input when `selectMode` is set to `"single"`.

Default: `"Click to select a value"`

#### `singleSelectPlaceholderText: string`

Placeholder text to display in the text input when `selectMode` is set to `"single"` and no item is selected.

Default: `"Select a value"`

### Outputs

#### `addNewRecordButtonClick: EventEmitter<void>`

Fires when users select the add button in the picker to add an item. The button appears when when `showAddNewRecordButton` is set to `true`.

#### `blur: EventEmitter<any>`

Fires when the component loses focus. This event does not emit a value.

#### `searchApplied: EventEmitter<string>`

Fires when a search is submitted from the picker's toolbar.

 SkySelectFieldPickerContext
----------------------------

Type: Class

Warning: **Deprecated.** `SkySelectFieldComponent` is deprecated. Use `SkyLookupComponent` instead.

Provides values to a custom picker.

### Properties

#### `data: Observable<SkySelectField[]>`

An array of `SkySelectField` objects from the select field's `data` property. Use this property to populate the custom picker with items for users to select.

#### `headingText: string`

Text from the select field's `pickerHeading` property. If your custom picker is a modal, use this property to display a header.

#### `inMemorySearchEnabled: boolean`

The boolean value from the select field's `inMemorySearchEnabled`. When `false`, it circumvents the list-builder search function to enable consumers to provide results from a remote source by updating the `data` value.

Default: `true`

#### `selectedValue: any`

The select field's current value. If the select field's `selectMode` is set to `single`, then this value is a `SkySelectField` object. If `selectMode` is set to `multiple`, then this value is an array of `SkySelectField` objects. Use this property to select the corresponding items in the custom picker.

#### `selectMode: SkySelectFieldSelectMode`

The `SkySelectFieldSelectMode` value from the select field's `selectMode` property. Use this property to determine whether users can select one item or multiple items.

#### `showAddNewRecordButton: boolean`

The boolean value from the select field's `showAddNewRecordButton` property. Use this property to determine whether to display a button in the custom picker for users to add items.

Default: `false`

 SkySelectFieldCustomPicker
---------------------------

Type: Interface

Warning: **Deprecated.** `SkySelectFieldComponent` is deprecated. Use `SkyLookupComponent` instead.

    interface SkySelectFieldCustomPicker {
      open: (pickerContext: SkySelectFieldPickerContext, updateValue: (value: SkySelectField[]) => void) => void;
    }

### Properties

#### `open: (pickerContext: SkySelectFieldPickerContext, updateValue: (value: SkySelectField[]) => void) => void`

The function to call when users select the text field or button.

 SkySelectFieldSelectMode
-------------------------

Type: Type alias

Warning: **Deprecated.** `SkySelectFieldComponent` is deprecated. Use `SkyLookupComponent` instead.

    type SkySelectFieldSelectMode = "single" | "multiple"

 SkySelectField
---------------

Type: Interface

Warning: **Deprecated.** `SkySelectFieldComponent` is deprecated. Use `SkyLookupComponent` instead.

Extends the `any` type and supports values for data objects that you can inject into the select field component to populate the picker.

    interface SkySelectField {
      category?: string;
      description?: string;
      id?: string;
      label?: string;
    }

### Properties

#### `category?: string`

The category for an item.

#### `description?: string`

The description to display below an item's label when `selectMode` is set to `multiple`.

#### `id?: string`

The ID for an item.

#### `label?: string`

The label for an item.