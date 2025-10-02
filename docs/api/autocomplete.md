---
component: 'autocomplete'
type: 'api-documentation'
description: 'API documentation for the autocomplete component including components, interfaces, and types.'
---

# Autocomplete API Documentation

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

#### SkyAgGridCellEditorAutocompleteComponent

**Selector:** `sky-ag-grid-cell-editor-autocomplete`

**Package:** `@skyux/ag-grid`

#### SkyAutocompleteInputDirective

**Selector:** `input[skyAutocomplete], textarea[skyAutocomplete]`

**Package:** `@skyux/lookup`

**Inputs:**

- `autocompleteAttribute`: `string` - The value for the `autocomplete` attribute on the form input. (default: "off")
- `disabled`: `boolean` - Whether to disable the autocomplete field on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync.
To set the disabled state on reactive forms, use the `FormControl` instead. (default: false)

#### SkyAutocompleteComponent

**Selector:** `sky-autocomplete`

**Package:** `@skyux/lookup`

**Inputs:**

- `allowAnyValue`: `InputSignalWithTransform<boolean, unknown>` - When using `searchAsync`, allows the user to specify arbitrary
values not in the search results. This only works in combination
with `searchAsync`. (default: false)
- `ariaLabelledBy`: `string | undefined` - The HTML element ID of the element that labels
the autocomplete text input. This sets the input's `aria-labelledby` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).
- `dropdownHintText`: `string | undefined` - Hint text to show in the dropdown
- `highlightSearchText`: `InputSignalWithTransform<boolean, unknown>` - Highlights the search text in each search result. Set this to false
when your search finds results that are not exact text matches, e.g.
returning "Bob" for the term "Robert." (default: true)
- `noResultsFoundText`: `string | undefined` - The text to display when no search results are found. (default: "No matches found")
- `searchAsyncDisabled`: `boolean | undefined` - Allows async search to be disabled even when a listener is specified for
the `searchAsync` output. (default: false)
- `searchResultTemplate`: `TemplateRef<unknown> | undefined` - The template that formats each search result in the dropdown list.
The autocomplete component injects search result values into the template
as `item` variables that reference all of the object properties of the search results.
- `wrapperClass`: `string | undefined`
- `data`: `any[]` - The static data source for the autocomplete component to search
when users enter text. For a dynamic data source such as an array that
changes due to server calls, use `search` or `searchAsync` instead.
- `debounceTime`: `number` - How many milliseconds to wait before searching while users
enter text in the autocomplete field. (default: 0)
- `descriptorProperty`: `string` - The object property to display in the text input after users
select an item in the dropdown list. (default: "name")
- `enableShowMore`: `boolean` - Whether to display a button in the dropdown that opens a picker where users can view all options.
- `messageStream`: `Subject<SkyAutocompleteMessage>` - The observable of `SkyAutocompleteMessage` that can close the dropdown.
- `propertiesToSearch`: `string[]` - The object properties to search. (default: ["name"])
- `search`: `SkyAutocompleteSearchFunction | undefined` - The function that dynamically manages the data source when users
change the text in the autocomplete field. The search function must return
an array or a promise of an array. The `search` property is particularly
useful when the data source does not live in the source code.
- `searchFilters`: `SkyAutocompleteSearchFunctionFilter[] | undefined` - The array of functions to call against each search result in order
to filter the search results when using the default search function. When
using the `search` property to specify a custom search function, you must
manually apply filters inside that function. The function must return `true`
or `false` for each result to indicate whether to display it in the dropdown list.
- `searchResultsLimit`: `number` - The maximum number of search results to display in the dropdown list.
By default, the component displays all matching results.
- `searchTextMinimumCharacters`: `number` - The minimum number of characters that users must enter before
the autocomplete component searches the data source and displays search
results in the dropdown list. (default: 1)
- `showAddButton`: `boolean` - Whether to display a button that lets users add options to the data source. (default: false)

**Outputs:**

- `addClick`: `EventEmitter<void>` - Fires when users select the button to add options to the data source.
- `openChange`: `EventEmitter<boolean>`
- `searchAsync`: `EventEmitter<SkyAutocompleteSearchAsyncArgs>` - Fires when users enter new search information and allows results to be
returned via an observable.
- `selectionChange`: `EventEmitter<SkyAutocompleteSelectionChange>` - Fires when users select items in the dropdown list.
- `showMoreClick`: `EventEmitter<SkyAutocompleteShowMoreArgs>` - Fires when users select the button to view all options.