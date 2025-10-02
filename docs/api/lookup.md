---
component: 'lookup'
type: 'api-documentation'
description: 'API documentation for the lookup component including components, interfaces, and types.'
---

# Lookup API Documentation

## Components and Directives

#### LookupAutocompleteAdvancedExampleComponent

**Selector:** `app-lookup-autocomplete-advanced-example`

**Package:** `@skyux/code-examples`

#### LookupAutocompleteAnyValueExampleComponent

**Selector:** `app-lookup-autocomplete-basic-example`

**Package:** `@skyux/code-examples`

#### LookupAutocompleteBasicExampleComponent

**Selector:** `app-lookup-autocomplete-basic-example`

**Package:** `@skyux/code-examples`

#### LookupAutocompleteCustomSearchExampleComponent

**Selector:** `app-lookup-autocomplete-custom-search-example`

**Package:** `@skyux/code-examples`

#### LookupAutocompleteSearchFiltersExampleComponent

**Selector:** `app-lookup-autocomplete-search-filters-example`

**Package:** `@skyux/code-examples`

#### LookupCountryFieldBasicExampleComponent

**Selector:** `app-lookup-country-field-basic-example`

**Package:** `@skyux/code-examples`

#### LookupAddItemExampleComponent

**Selector:** `app-lookup-add-item-example`

**Package:** `@skyux/code-examples`

#### LookupCustomPickerExampleComponent

**Selector:** `app-lookup-custom-picker-example`

**Package:** `@skyux/code-examples`

#### LookupMultiSelectExampleComponent

**Selector:** `app-lookup-multi-select-example`

**Package:** `@skyux/code-examples`

#### LookupResultTemplatesExampleComponent

**Selector:** `app-lookup-result-templates-example`

**Package:** `@skyux/code-examples`

#### LookupSingleSelectExampleComponent

**Selector:** `app-lookup-single-select-example`

**Package:** `@skyux/code-examples`

#### LookupSearchBasicExampleComponent

**Selector:** `app-lookup-search-basic-example`

**Package:** `@skyux/code-examples`

#### LookupSelectionModalAddItemExampleComponent

**Selector:** `app-lookup-selection-modal-add-item-example`

**Package:** `@skyux/code-examples`

#### LookupSelectionModalBasicExampleComponent

**Selector:** `app-lookup-selection-modal-basic-example`

**Package:** `@skyux/code-examples`

#### SkyAgGridCellEditorLookupComponent

**Selector:** `sky-ag-grid-cell-editor-lookup`

**Package:** `@skyux/ag-grid`

#### SkyAgGridCellRendererLookupComponent

**Selector:** `sky-cell-renderer-lookup`

**Package:** `@skyux/ag-grid`

#### SkyLookupComponent

**Selector:** `sky-lookup`

**Package:** `@skyux/lookup`

**Inputs:**

- `ariaLabel`: `string | undefined` - The ARIA label for the typeahead search input. This sets the input's `aria-label` attribute to provide a text equivalent for
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the input includes a visible label, use `ariaLabelledBy` instead.
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `ariaLabelledBy`: `string | undefined` - The HTML element ID of the element that labels
the typeahead search input. This sets the input's `aria-labelledby` attribute to provide a text equivalent for
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the input does not include a visible label, use `ariaLabel` instead.
For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).
- `autocompleteAttribute`: `string | undefined` - The value for the `autocomplete` attribute on the form input. (default: 'off')
- `debounceTime`: `number | undefined` - How many milliseconds to wait before searching while users
enter text in the lookup field. (default: 0)
- `disabled`: `boolean` - Whether to disable the lookup field on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync.
To set the disabled state on reactive forms, use the `FormControl` instead. (default: false)
- `enableShowMore`: `boolean` - Whether to enable users to open a picker where they can view all options. (default: false)
- `idProperty`: `string | undefined` - The object property that represents the object's unique identifier.
Specifying this property enables token animations and more efficient rendering.
This property is required when using `enableShowMore` and `searchAsync` together.
- `placeholderText`: `string | undefined` - Placeholder text to display in the lookup field.
- `searchResultsLimit`: `number | undefined` - The maximum number of search results to display in the dropdown
list. By default, the lookup component displays all matching results.
This property has no effect on the results in the "Show more" picker.
- `searchResultTemplate`: `TemplateRef<unknown> | undefined` - The template that formats each option in the dropdown list. The lookup component
injects values into the template as `item` variables that reference all the object
properties of the options.
- `searchTextMinimumCharacters`: `number | undefined` - The minimum number of characters that users must enter before
the lookup component searches the data source and displays search results
in the dropdown list. (default: 1)
- `showAddButton`: `boolean` - Whether to display a button that lets users add options to the list. (default: false)
- `showMoreConfig`: `SkyLookupShowMoreConfig | undefined` - Configuration options for the picker that displays all options.
- `wrapperClass`: `string | undefined`
- `data`: `any[]` - The data source for the lookup component to search when users
enter text. You can specify static data such as an array of objects, or
you can pull data from a database. (default: [])
- `descriptorProperty`: `string` - The object property to display in the text input after users
select an item in the dropdown list. (default: "name")
- `propertiesToSearch`: `string[]` - The array of object properties to search when utilizing the `data` property and the built-in search function. (default: ["name"])
- `required`: `boolean` - Whether the lookup field is required. (default: false)
- `search`: `SkyAutocompleteSearchFunction | undefined` - The function to dynamically manage the data source when users
change the text in the lookup field. The search function must return
an array or a promise of an array. The `search` property is particularly
useful when the data source does not live in the source code.
- `searchFilters`: `SkyAutocompleteSearchFunctionFilter[] | undefined` - The array of functions to call against each search result in order
to filter the search results when using the `data` input and the default search function. When
using a custom search function via the `search` property filters must be
applied manually inside that function. The function must return `true` or
`false` for each result to indicate whether to display it in the dropdown list.
- `selectMode`: `SkyLookupSelectModeType` - The ability for users to select one option or multiple options. (default: "multiple")

**Outputs:**

- `addClick`: `EventEmitter<SkyLookupAddClickEventArgs>` - Fires when users select the button to add options to the list.
- `openChange`: `EventEmitter<boolean>`
- `searchAsync`: `EventEmitter<SkyAutocompleteSearchAsyncArgs>` - Fires when users enter new search information and allows results to be
returned via an observable. The event is also fired with empty search text
when the "Show more" picker is opened without search text.
- `selectionModalOpenChange`: `EventEmitter<boolean>`