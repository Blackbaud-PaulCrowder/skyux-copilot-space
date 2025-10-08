# Design

                  Skip to Main Content

 Autocomplete
============

The autocomplete text input filters a data source based on user entries and then displays search results in a dropdown list.

 Usage
------

### Use when

Use the autocomplete component when users know what they are looking for and can select a single item. For guidance on which selection inputs to use in other scenarios, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/lookup`[View in NPM](https://www.npmjs.com/package/@skyux/lookup) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lookup/src/lib/modules/autocomplete/autocomplete.module.ts#L35) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lookup`Copy None found.

 SkyAutocompleteModule
----------------------

Type: Module

`import { SkyAutocompleteModule } from '@skyux/lookup';`

 SkyAutocompleteComponent
-------------------------

Type: Component

Selector: `sky-autocomplete`

### Inputs

#### `allowAnyValue: InputSignalWithTransform<boolean, unknown>`

When using `searchAsync`, allows the user to specify arbitrary values not in the search results. This only works in combination with `searchAsync`.

Default: `false`

#### `ariaLabelledBy: string | undefined`

The HTML element ID of the element that labels the autocomplete text input. This sets the input's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `data: any[]`

The static data source for the autocomplete component to search when users enter text. For a dynamic data source, such as an array that changes due to server calls, use `search` or `searchAsync` instead. You can specify static data, such as an array of objects, or you can pull data from a database.

#### `debounceTime: number`

How many milliseconds to wait before searching while users enter text in the autocomplete field.

Default: `0`

#### `descriptorProperty: string`

The object property to display in the text input after users select an item in the dropdown list.

Default: `"name"`

#### `highlightSearchText: InputSignalWithTransform<boolean, unknown>`

Highlights the search text in each search result. Set this to `false` when your search returns results that aren't exact text matches, such as returning "Bob" for "Robert."

Default: `true`

#### `noResultsFoundText: string | undefined`

The text to display when no search results are found.

Default: `"No matches found"`

#### `propertiesToSearch: string[]`

Warning: **Deprecated.** We recommend against using this property. To search specific properties, use the `searchAsync` event instead.

The object properties to search.

Default: `["name"]`

#### `search: SkyAutocompleteSearchFunction | undefined`

Warning: **Deprecated.** We recommend against using this property. To call a remote data source, use the `searchAsync` event instead.

The function that dynamically manages the data to display in search results when users change the text in the autocomplete field. The search function must return an array or a promise of an array. The `search` property is particularly useful when the data source does not live in the source code.

#### `searchFilters: SkyAutocompleteSearchFunctionFilter[] | undefined`

Warning: **Deprecated.** We recommend against using this property. To filter results, use the `searchAsync` event instead.

The array of functions to call against each search result. This filters the search results when using the `data` input and the default search function. When the `search` property specifies a custom search function, you must manually apply filters inside that function. The function must return `true` or `false` for each result to indicate whether to display it in the dropdown list.

#### `searchResultTemplate: TemplateRef<unknown> | undefined`

The template that formats each search result in the dropdown list. The autocomplete component injects search result values into the template as `item` variables that reference all of the object properties of the search results.

#### `searchResultsLimit: number`

The maximum number of search results to display in the dropdown list. By default, the component displays all matching results.

#### `searchTextMinimumCharacters: number`

The minimum number of characters that users must enter before the autocomplete component searches the data source and displays search results in the dropdown list.

Default: `1`

### Outputs

#### `searchAsync: EventEmitter<SkyAutocompleteSearchAsyncArgs>`

Fires when users enter new search information and allows results to be returned via an observable.

#### `selectionChange: EventEmitter<SkyAutocompleteSelectionChange>`

Fires when users select items in the dropdown list.

 SkyAutocompleteInputDirective
------------------------------

Type: Directive

Selector: `input[skyAutocomplete], textarea[skyAutocomplete]`

### Inputs

#### `autocompleteAttribute: string`

Warning: **Deprecated.** SKY UX only supports browser autofill on components where the direct input matches the return value. This input may not behave as expected due to the dropdown selection interaction.

The value for the `autocomplete` attribute on the form input.

Default: `"off"`

#### `disabled: boolean`

Whether to disable the autocomplete field on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

 SkyAutocompleteSearchArgs
--------------------------

Type: Interface

    interface SkyAutocompleteSearchArgs {
      context?: SkyAutocompleteSearchContext;
    }

### Properties

#### `context?: SkyAutocompleteSearchContext`

 SkyAutocompleteSearchAsyncArgs
-------------------------------

Type: Interface

Arguments passed when an asynchronous search is executed from the autocomplete or lookup component.

    interface SkyAutocompleteSearchAsyncArgs {
      continuationData?: unknown;
      displayType: AutocompleteSearchAsyncResultDisplayType;
      offset: number;
      result?: Observable<SkyAutocompleteSearchAsyncResult>;
      searchText: string;
    }

### Properties

#### `continuationData?: unknown`

A continuation token which can be set and then will be passed back with any future searches. This is helpful for applications which utilize a token instead of an offset when fetching data.

#### `displayType: AutocompleteSearchAsyncResultDisplayType`

How the search results will be displayed. Use this value to determine how many results to return.

#### `offset: number`

The offset index of the first result to return. When search is executed as a result of an infinite scroll event, for example, offset will be set to the number of items already displayed.

#### `result?: Observable<SkyAutocompleteSearchAsyncResult>`

An Observable representing the search results. Consumers should set this when the event fires so the autocomplete or lookup component can subscribe to it and then display the results.

#### `searchText: string`

The search text entered by the user.

 AutocompleteSearchAsyncResultDisplayType
-----------------------------------------

Type: Type alias

    type AutocompleteSearchAsyncResultDisplayType = "popover" | "modal"

 SkyAutocompleteSearchAsyncResult
---------------------------------

Type: Interface

The result of searching for items to display in an autocomplete or lookup field.

    interface SkyAutocompleteSearchAsyncResult {
      continuationData?: unknown;
      hasMore?: boolean;
      items: unknown[];
      totalCount: number;
    }

### Properties

#### `continuationData?: unknown`

Data provided on "load more" search result requests. Use this property for information such as a continuation token for paged database queries.

#### `hasMore?: boolean`

Whether there are more results that match the search criteria.

#### `items: unknown[]`

A list of items matching the search criteria. When there are more items that match the search criteria, set the `hasMore` property to `true` more records can be lazy-loaded as the user scrolls through the search results.

#### `totalCount: number`

The total number of records that match the search criteria, including items not returned in the current list of items.

 SkyAutocompleteSearchContext
-----------------------------

Type: Type alias

    type SkyAutocompleteSearchContext = "popover" | "modal"

 SkyAutocompleteSearchFunctionFilter
------------------------------------

Type: Type alias

    type SkyAutocompleteSearchFunctionFilter = (searchText: string, item: any, args?: SkyAutocompleteSearchArgs) => boolean

 SkyAutocompleteSearchFunctionResponse
--------------------------------------

Type: Type alias

    type SkyAutocompleteSearchFunctionResponse = any[] | Promise<any[]>

 SkyAutocompleteSearchFunction
------------------------------

Type: Type alias

    type SkyAutocompleteSearchFunction = (searchText: string, data: any[], args?: SkyAutocompleteSearchArgs) => SkyAutocompleteSearchFunctionResponse

 SkyAutocompleteSelectionChange
-------------------------------

Type: Interface

    interface SkyAutocompleteSelectionChange {
      selectedItem?: any;
    }

### Properties

#### `selectedItem?: any`

The search result object that users select in the dropdown list.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyAutocompleteHarness
-----------------------

Type: Class

`import { SkyAutocompleteHarness } from '@skyux/lookup/testing';`

Harness for interacting with an autocomplete component in tests.

### Methods

#### `blur(): Promise<void>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).blur()` instead.

Blurs the autocomplete input.

#### Returns

`Promise<void>`

#### `clear(): Promise<void>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).clear()` instead.

Clears the autocomplete input value.

#### Returns

`Promise<void>`

#### `enterText(value: string): Promise<void>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).setValue()` instead.

Enters text into the autocomplete input.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).focus()` instead.

Focuses the autocomplete input.

#### Returns

`Promise<void>`

#### `getAriaLabelledby(): Promise<null | string>`

Gets the autocomplete `aria-labelledby` value.

#### Returns

`Promise<null | string>`

#### `getControl(): Promise<SkyAutocompleteInputHarness>`

Gets the autocomplete input harness.

#### Returns

`Promise<SkyAutocompleteInputHarness>`

#### `getNoResultsFoundText(): Promise<string>`

Gets the text displayed when no search results are found.

#### Returns

`Promise<string>`

#### `getSearchResult(filter: SkyAutocompleteSearchResultHarnessFilters): Promise<SkyAutocompleteSearchResultHarness>`

Gets a specific autocomplete search result based on the filter criteria.

#### Parameters

##### `filter: SkyAutocompleteSearchResultHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyAutocompleteSearchResultHarness>`

#### `getSearchResults(filters?: SkyAutocompleteSearchResultHarnessFilters): Promise<SkyAutocompleteSearchResultHarness[]>`

Gets an array of autocomplete search results based on the filter criteria. If no filter is provided, returns all autocomplete search results.

#### Parameters

##### `filters?: SkyAutocompleteSearchResultHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyAutocompleteSearchResultHarness[]>`

#### `getSearchResultsText(filters?: SkyAutocompleteSearchResultHarnessFilters): Promise<string[]>`

Returns the text content for each autocomplete search result.

#### Parameters

##### `filters?: SkyAutocompleteSearchResultHarnessFilters`

#### Returns

`Promise<string[]>`

#### `getValue(): Promise<string>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).getValue()` instead.

Gets the value of the autocomplete input.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).isDisabled()` instead.

Whether the autocomplete input is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).isFocused()` instead.

Whether the autocomplete input is focused.

#### Returns

`Promise<boolean>`

#### `isOpen(): Promise<boolean>`

Whether the autocomplete is open.

#### Returns

`Promise<boolean>`

#### `selectSearchResult(filters: SkyAutocompleteSearchResultHarnessFilters): Promise<void>`

Selects a search result.

#### Parameters

##### `filters: SkyAutocompleteSearchResultHarnessFilters`

#### Returns

`Promise<void>`

#### `SkyAutocompleteHarness.with(filters: SkyAutocompleteHarnessFilters): HarnessPredicate<SkyAutocompleteHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyAutocompleteHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyAutocompleteHarnessFilters`

#### Returns

`HarnessPredicate<SkyAutocompleteHarness>`

 SkyAutocompleteHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyAutocompleteHarness](/skyux/components/autocomplete?docs-active-tab=design#class_sky-autocomplete-harness.md) instances.

    interface SkyAutocompleteHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyAutocompleteSearchResultHarness
-----------------------------------

Type: Class

`import { SkyAutocompleteSearchResultHarness } from '@skyux/lookup/testing';`

Harness for interacting with an autocomplete search result in tests.

### Methods

#### `getDescriptorValue(): Promise<string>`

Returns the value of the search result's descriptor property. This value is set by the autocomplete's `descriptorProperty` input.

#### Returns

`Promise<string>`

#### `getText(): Promise<string>`

Returns the text of the search result.

#### Returns

`Promise<string>`

#### `queryHarness(query: HarnessQuery<T>): Promise<T>`

Returns a child harness or throws an error if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<T>`

#### `queryHarnesses(harness: HarnessQuery<T>): Promise<T[]>`

Returns child harnesses.

#### Parameters

##### `harness: HarnessQuery<T>`

#### Returns

`Promise<T[]>`

#### `queryHarnessOrNull(query: HarnessQuery<T>): Promise<null | T>`

Returns a child harness or null if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<null | T>`

#### `querySelector(selector: string): Promise<TestElement>`

Returns a child test element or throws an error if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement>`

#### `querySelectorAll(selector: string): Promise<TestElement[]>`

Returns child test elements.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement[]>`

#### `querySelectorOrNull(selector: string): Promise<null | TestElement>`

Returns a child test element or null if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<null | TestElement>`

#### `select(): Promise<void>`

Selects the search result.

#### Returns

`Promise<void>`

#### `SkyAutocompleteSearchResultHarness.with(filters: SkyAutocompleteSearchResultHarnessFilters): HarnessPredicate<SkyAutocompleteSearchResultHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyAutocompleteSearchResultHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyAutocompleteSearchResultHarnessFilters`

#### Returns

`HarnessPredicate<SkyAutocompleteSearchResultHarness>`

 SkyAutocompleteSearchResultHarnessFilters
------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyAutocompleteSearchResultHarness](/skyux/components/autocomplete?docs-active-tab=design#class_sky-autocomplete-search-result-harness.md) instances.

    interface SkyAutocompleteSearchResultHarnessFilters {
      text?: string | RegExp;
    }

### Properties

#### `text?: string | RegExp`

Only find instances whose content matches the given value.

 SkyAutocompleteInputHarness
----------------------------

Type: Class

`import { SkyAutocompleteInputHarness } from '@skyux/lookup/testing';`

Harness to interact with the autocomplete input harness.

### Methods

#### `blur(): Promise<void>`

Blurs the input.

#### Returns

`Promise<void>`

#### `clear(): Promise<void>`

Clears the input value.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the input.

#### Returns

`Promise<void>`

#### `getAriaControls(): Promise<null | string>`

Returns the value of the input's `aria-controls` attribute.

#### Returns

`Promise<null | string>`

#### `getValue(): Promise<string>`

Gets the value of the input.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the input is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the input is focused.

#### Returns

`Promise<boolean>`

#### `setValue(value: string): Promise<void>`

Sets the value of the input. The value will be set by simulating key presses that correspond to the given value.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

# Development

                  Skip to Main Content

 Autocomplete
============

The autocomplete text input filters a data source based on user entries and then displays search results in a dropdown list.

 Usage
------

### Use when

Use the autocomplete component when users know what they are looking for and can select a single item. For guidance on which selection inputs to use in other scenarios, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/lookup`[View in NPM](https://www.npmjs.com/package/@skyux/lookup) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lookup/src/lib/modules/autocomplete/autocomplete.module.ts#L35) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lookup`Copy None found.

 SkyAutocompleteModule
----------------------

Type: Module

`import { SkyAutocompleteModule } from '@skyux/lookup';`

 SkyAutocompleteComponent
-------------------------

Type: Component

Selector: `sky-autocomplete`

### Inputs

#### `allowAnyValue: InputSignalWithTransform<boolean, unknown>`

When using `searchAsync`, allows the user to specify arbitrary values not in the search results. This only works in combination with `searchAsync`.

Default: `false`

#### `ariaLabelledBy: string | undefined`

The HTML element ID of the element that labels the autocomplete text input. This sets the input's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `data: any[]`

The static data source for the autocomplete component to search when users enter text. For a dynamic data source, such as an array that changes due to server calls, use `search` or `searchAsync` instead. You can specify static data, such as an array of objects, or you can pull data from a database.

#### `debounceTime: number`

How many milliseconds to wait before searching while users enter text in the autocomplete field.

Default: `0`

#### `descriptorProperty: string`

The object property to display in the text input after users select an item in the dropdown list.

Default: `"name"`

#### `highlightSearchText: InputSignalWithTransform<boolean, unknown>`

Highlights the search text in each search result. Set this to `false` when your search returns results that aren't exact text matches, such as returning "Bob" for "Robert."

Default: `true`

#### `noResultsFoundText: string | undefined`

The text to display when no search results are found.

Default: `"No matches found"`

#### `propertiesToSearch: string[]`

Warning: **Deprecated.** We recommend against using this property. To search specific properties, use the `searchAsync` event instead.

The object properties to search.

Default: `["name"]`

#### `search: SkyAutocompleteSearchFunction | undefined`

Warning: **Deprecated.** We recommend against using this property. To call a remote data source, use the `searchAsync` event instead.

The function that dynamically manages the data to display in search results when users change the text in the autocomplete field. The search function must return an array or a promise of an array. The `search` property is particularly useful when the data source does not live in the source code.

#### `searchFilters: SkyAutocompleteSearchFunctionFilter[] | undefined`

Warning: **Deprecated.** We recommend against using this property. To filter results, use the `searchAsync` event instead.

The array of functions to call against each search result. This filters the search results when using the `data` input and the default search function. When the `search` property specifies a custom search function, you must manually apply filters inside that function. The function must return `true` or `false` for each result to indicate whether to display it in the dropdown list.

#### `searchResultTemplate: TemplateRef<unknown> | undefined`

The template that formats each search result in the dropdown list. The autocomplete component injects search result values into the template as `item` variables that reference all of the object properties of the search results.

#### `searchResultsLimit: number`

The maximum number of search results to display in the dropdown list. By default, the component displays all matching results.

#### `searchTextMinimumCharacters: number`

The minimum number of characters that users must enter before the autocomplete component searches the data source and displays search results in the dropdown list.

Default: `1`

### Outputs

#### `searchAsync: EventEmitter<SkyAutocompleteSearchAsyncArgs>`

Fires when users enter new search information and allows results to be returned via an observable.

#### `selectionChange: EventEmitter<SkyAutocompleteSelectionChange>`

Fires when users select items in the dropdown list.

 SkyAutocompleteInputDirective
------------------------------

Type: Directive

Selector: `input[skyAutocomplete], textarea[skyAutocomplete]`

### Inputs

#### `autocompleteAttribute: string`

Warning: **Deprecated.** SKY UX only supports browser autofill on components where the direct input matches the return value. This input may not behave as expected due to the dropdown selection interaction.

The value for the `autocomplete` attribute on the form input.

Default: `"off"`

#### `disabled: boolean`

Whether to disable the autocomplete field on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

 SkyAutocompleteSearchArgs
--------------------------

Type: Interface

    interface SkyAutocompleteSearchArgs {
      context?: SkyAutocompleteSearchContext;
    }

### Properties

#### `context?: SkyAutocompleteSearchContext`

 SkyAutocompleteSearchAsyncArgs
-------------------------------

Type: Interface

Arguments passed when an asynchronous search is executed from the autocomplete or lookup component.

    interface SkyAutocompleteSearchAsyncArgs {
      continuationData?: unknown;
      displayType: AutocompleteSearchAsyncResultDisplayType;
      offset: number;
      result?: Observable<SkyAutocompleteSearchAsyncResult>;
      searchText: string;
    }

### Properties

#### `continuationData?: unknown`

A continuation token which can be set and then will be passed back with any future searches. This is helpful for applications which utilize a token instead of an offset when fetching data.

#### `displayType: AutocompleteSearchAsyncResultDisplayType`

How the search results will be displayed. Use this value to determine how many results to return.

#### `offset: number`

The offset index of the first result to return. When search is executed as a result of an infinite scroll event, for example, offset will be set to the number of items already displayed.

#### `result?: Observable<SkyAutocompleteSearchAsyncResult>`

An Observable representing the search results. Consumers should set this when the event fires so the autocomplete or lookup component can subscribe to it and then display the results.

#### `searchText: string`

The search text entered by the user.

 AutocompleteSearchAsyncResultDisplayType
-----------------------------------------

Type: Type alias

    type AutocompleteSearchAsyncResultDisplayType = "popover" | "modal"

 SkyAutocompleteSearchAsyncResult
---------------------------------

Type: Interface

The result of searching for items to display in an autocomplete or lookup field.

    interface SkyAutocompleteSearchAsyncResult {
      continuationData?: unknown;
      hasMore?: boolean;
      items: unknown[];
      totalCount: number;
    }

### Properties

#### `continuationData?: unknown`

Data provided on "load more" search result requests. Use this property for information such as a continuation token for paged database queries.

#### `hasMore?: boolean`

Whether there are more results that match the search criteria.

#### `items: unknown[]`

A list of items matching the search criteria. When there are more items that match the search criteria, set the `hasMore` property to `true` more records can be lazy-loaded as the user scrolls through the search results.

#### `totalCount: number`

The total number of records that match the search criteria, including items not returned in the current list of items.

 SkyAutocompleteSearchContext
-----------------------------

Type: Type alias

    type SkyAutocompleteSearchContext = "popover" | "modal"

 SkyAutocompleteSearchFunctionFilter
------------------------------------

Type: Type alias

    type SkyAutocompleteSearchFunctionFilter = (searchText: string, item: any, args?: SkyAutocompleteSearchArgs) => boolean

 SkyAutocompleteSearchFunctionResponse
--------------------------------------

Type: Type alias

    type SkyAutocompleteSearchFunctionResponse = any[] | Promise<any[]>

 SkyAutocompleteSearchFunction
------------------------------

Type: Type alias

    type SkyAutocompleteSearchFunction = (searchText: string, data: any[], args?: SkyAutocompleteSearchArgs) => SkyAutocompleteSearchFunctionResponse

 SkyAutocompleteSelectionChange
-------------------------------

Type: Interface

    interface SkyAutocompleteSelectionChange {
      selectedItem?: any;
    }

### Properties

#### `selectedItem?: any`

The search result object that users select in the dropdown list.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyAutocompleteHarness
-----------------------

Type: Class

`import { SkyAutocompleteHarness } from '@skyux/lookup/testing';`

Harness for interacting with an autocomplete component in tests.

### Methods

#### `blur(): Promise<void>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).blur()` instead.

Blurs the autocomplete input.

#### Returns

`Promise<void>`

#### `clear(): Promise<void>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).clear()` instead.

Clears the autocomplete input value.

#### Returns

`Promise<void>`

#### `enterText(value: string): Promise<void>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).setValue()` instead.

Enters text into the autocomplete input.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).focus()` instead.

Focuses the autocomplete input.

#### Returns

`Promise<void>`

#### `getAriaLabelledby(): Promise<null | string>`

Gets the autocomplete `aria-labelledby` value.

#### Returns

`Promise<null | string>`

#### `getControl(): Promise<SkyAutocompleteInputHarness>`

Gets the autocomplete input harness.

#### Returns

`Promise<SkyAutocompleteInputHarness>`

#### `getNoResultsFoundText(): Promise<string>`

Gets the text displayed when no search results are found.

#### Returns

`Promise<string>`

#### `getSearchResult(filter: SkyAutocompleteSearchResultHarnessFilters): Promise<SkyAutocompleteSearchResultHarness>`

Gets a specific autocomplete search result based on the filter criteria.

#### Parameters

##### `filter: SkyAutocompleteSearchResultHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyAutocompleteSearchResultHarness>`

#### `getSearchResults(filters?: SkyAutocompleteSearchResultHarnessFilters): Promise<SkyAutocompleteSearchResultHarness[]>`

Gets an array of autocomplete search results based on the filter criteria. If no filter is provided, returns all autocomplete search results.

#### Parameters

##### `filters?: SkyAutocompleteSearchResultHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyAutocompleteSearchResultHarness[]>`

#### `getSearchResultsText(filters?: SkyAutocompleteSearchResultHarnessFilters): Promise<string[]>`

Returns the text content for each autocomplete search result.

#### Parameters

##### `filters?: SkyAutocompleteSearchResultHarnessFilters`

#### Returns

`Promise<string[]>`

#### `getValue(): Promise<string>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).getValue()` instead.

Gets the value of the autocomplete input.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).isDisabled()` instead.

Whether the autocomplete input is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).isFocused()` instead.

Whether the autocomplete input is focused.

#### Returns

`Promise<boolean>`

#### `isOpen(): Promise<boolean>`

Whether the autocomplete is open.

#### Returns

`Promise<boolean>`

#### `selectSearchResult(filters: SkyAutocompleteSearchResultHarnessFilters): Promise<void>`

Selects a search result.

#### Parameters

##### `filters: SkyAutocompleteSearchResultHarnessFilters`

#### Returns

`Promise<void>`

#### `SkyAutocompleteHarness.with(filters: SkyAutocompleteHarnessFilters): HarnessPredicate<SkyAutocompleteHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyAutocompleteHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyAutocompleteHarnessFilters`

#### Returns

`HarnessPredicate<SkyAutocompleteHarness>`

 SkyAutocompleteHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyAutocompleteHarness](/skyux/components/autocomplete?docs-active-tab=development#class_sky-autocomplete-harness.md) instances.

    interface SkyAutocompleteHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyAutocompleteSearchResultHarness
-----------------------------------

Type: Class

`import { SkyAutocompleteSearchResultHarness } from '@skyux/lookup/testing';`

Harness for interacting with an autocomplete search result in tests.

### Methods

#### `getDescriptorValue(): Promise<string>`

Returns the value of the search result's descriptor property. This value is set by the autocomplete's `descriptorProperty` input.

#### Returns

`Promise<string>`

#### `getText(): Promise<string>`

Returns the text of the search result.

#### Returns

`Promise<string>`

#### `queryHarness(query: HarnessQuery<T>): Promise<T>`

Returns a child harness or throws an error if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<T>`

#### `queryHarnesses(harness: HarnessQuery<T>): Promise<T[]>`

Returns child harnesses.

#### Parameters

##### `harness: HarnessQuery<T>`

#### Returns

`Promise<T[]>`

#### `queryHarnessOrNull(query: HarnessQuery<T>): Promise<null | T>`

Returns a child harness or null if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<null | T>`

#### `querySelector(selector: string): Promise<TestElement>`

Returns a child test element or throws an error if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement>`

#### `querySelectorAll(selector: string): Promise<TestElement[]>`

Returns child test elements.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement[]>`

#### `querySelectorOrNull(selector: string): Promise<null | TestElement>`

Returns a child test element or null if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<null | TestElement>`

#### `select(): Promise<void>`

Selects the search result.

#### Returns

`Promise<void>`

#### `SkyAutocompleteSearchResultHarness.with(filters: SkyAutocompleteSearchResultHarnessFilters): HarnessPredicate<SkyAutocompleteSearchResultHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyAutocompleteSearchResultHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyAutocompleteSearchResultHarnessFilters`

#### Returns

`HarnessPredicate<SkyAutocompleteSearchResultHarness>`

 SkyAutocompleteSearchResultHarnessFilters
------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyAutocompleteSearchResultHarness](/skyux/components/autocomplete?docs-active-tab=development#class_sky-autocomplete-search-result-harness.md) instances.

    interface SkyAutocompleteSearchResultHarnessFilters {
      text?: string | RegExp;
    }

### Properties

#### `text?: string | RegExp`

Only find instances whose content matches the given value.

 SkyAutocompleteInputHarness
----------------------------

Type: Class

`import { SkyAutocompleteInputHarness } from '@skyux/lookup/testing';`

Harness to interact with the autocomplete input harness.

### Methods

#### `blur(): Promise<void>`

Blurs the input.

#### Returns

`Promise<void>`

#### `clear(): Promise<void>`

Clears the input value.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the input.

#### Returns

`Promise<void>`

#### `getAriaControls(): Promise<null | string>`

Returns the value of the input's `aria-controls` attribute.

#### Returns

`Promise<null | string>`

#### `getValue(): Promise<string>`

Gets the value of the input.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the input is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the input is focused.

#### Returns

`Promise<boolean>`

#### `setValue(value: string): Promise<void>`

Sets the value of the input. The value will be set by simulating key presses that correspond to the given value.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

# Examples

                    Skip to Main Content

 Autocomplete
============

The autocomplete text input filters a data source based on user entries and then displays search results in a dropdown list.

Usage
------

### Use when

Use the autocomplete component when users know what they are looking for and can select a single item. For guidance on which selection inputs to use in other scenarios, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/lookup`[View in NPM](https://www.npmjs.com/package/@skyux/lookup) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lookup/src/lib/modules/autocomplete/autocomplete.module.ts#L35) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lookup`Copy None found.

 SkyAutocompleteModule
----------------------

Type: Module

`import { SkyAutocompleteModule } from '@skyux/lookup';`

 SkyAutocompleteComponent
-------------------------

Type: Component

Selector: `sky-autocomplete`

### Inputs

#### `allowAnyValue: InputSignalWithTransform<boolean, unknown>`

When using `searchAsync`, allows the user to specify arbitrary values not in the search results. This only works in combination with `searchAsync`.

Default: `false`

#### `ariaLabelledBy: string | undefined`

The HTML element ID of the element that labels the autocomplete text input. This sets the input's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `data: any[]`

The static data source for the autocomplete component to search when users enter text. For a dynamic data source, such as an array that changes due to server calls, use `search` or `searchAsync` instead. You can specify static data, such as an array of objects, or you can pull data from a database.

#### `debounceTime: number`

How many milliseconds to wait before searching while users enter text in the autocomplete field.

Default: `0`

#### `descriptorProperty: string`

The object property to display in the text input after users select an item in the dropdown list.

Default: `"name"`

#### `highlightSearchText: InputSignalWithTransform<boolean, unknown>`

Highlights the search text in each search result. Set this to `false` when your search returns results that aren't exact text matches, such as returning "Bob" for "Robert."

Default: `true`

#### `noResultsFoundText: string | undefined`

The text to display when no search results are found.

Default: `"No matches found"`

#### `propertiesToSearch: string[]`

Warning: **Deprecated.** We recommend against using this property. To search specific properties, use the `searchAsync` event instead.

The object properties to search.

Default: `["name"]`

#### `search: SkyAutocompleteSearchFunction | undefined`

Warning: **Deprecated.** We recommend against using this property. To call a remote data source, use the `searchAsync` event instead.

The function that dynamically manages the data to display in search results when users change the text in the autocomplete field. The search function must return an array or a promise of an array. The `search` property is particularly useful when the data source does not live in the source code.

#### `searchFilters: SkyAutocompleteSearchFunctionFilter[] | undefined`

Warning: **Deprecated.** We recommend against using this property. To filter results, use the `searchAsync` event instead.

The array of functions to call against each search result. This filters the search results when using the `data` input and the default search function. When the `search` property specifies a custom search function, you must manually apply filters inside that function. The function must return `true` or `false` for each result to indicate whether to display it in the dropdown list.

#### `searchResultTemplate: TemplateRef<unknown> | undefined`

The template that formats each search result in the dropdown list. The autocomplete component injects search result values into the template as `item` variables that reference all of the object properties of the search results.

#### `searchResultsLimit: number`

The maximum number of search results to display in the dropdown list. By default, the component displays all matching results.

#### `searchTextMinimumCharacters: number`

The minimum number of characters that users must enter before the autocomplete component searches the data source and displays search results in the dropdown list.

Default: `1`

### Outputs

#### `searchAsync: EventEmitter<SkyAutocompleteSearchAsyncArgs>`

Fires when users enter new search information and allows results to be returned via an observable.

#### `selectionChange: EventEmitter<SkyAutocompleteSelectionChange>`

Fires when users select items in the dropdown list.

 SkyAutocompleteInputDirective
------------------------------

Type: Directive

Selector: `input[skyAutocomplete], textarea[skyAutocomplete]`

### Inputs

#### `autocompleteAttribute: string`

Warning: **Deprecated.** SKY UX only supports browser autofill on components where the direct input matches the return value. This input may not behave as expected due to the dropdown selection interaction.

The value for the `autocomplete` attribute on the form input.

Default: `"off"`

#### `disabled: boolean`

Whether to disable the autocomplete field on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

 SkyAutocompleteSearchArgs
--------------------------

Type: Interface

    interface SkyAutocompleteSearchArgs {
      context?: SkyAutocompleteSearchContext;
    }

### Properties

#### `context?: SkyAutocompleteSearchContext`

 SkyAutocompleteSearchAsyncArgs
-------------------------------

Type: Interface

Arguments passed when an asynchronous search is executed from the autocomplete or lookup component.

    interface SkyAutocompleteSearchAsyncArgs {
      continuationData?: unknown;
      displayType: AutocompleteSearchAsyncResultDisplayType;
      offset: number;
      result?: Observable<SkyAutocompleteSearchAsyncResult>;
      searchText: string;
    }

### Properties

#### `continuationData?: unknown`

A continuation token which can be set and then will be passed back with any future searches. This is helpful for applications which utilize a token instead of an offset when fetching data.

#### `displayType: AutocompleteSearchAsyncResultDisplayType`

How the search results will be displayed. Use this value to determine how many results to return.

#### `offset: number`

The offset index of the first result to return. When search is executed as a result of an infinite scroll event, for example, offset will be set to the number of items already displayed.

#### `result?: Observable<SkyAutocompleteSearchAsyncResult>`

An Observable representing the search results. Consumers should set this when the event fires so the autocomplete or lookup component can subscribe to it and then display the results.

#### `searchText: string`

The search text entered by the user.

 AutocompleteSearchAsyncResultDisplayType
-----------------------------------------

Type: Type alias

    type AutocompleteSearchAsyncResultDisplayType = "popover" | "modal"

 SkyAutocompleteSearchAsyncResult
---------------------------------

Type: Interface

The result of searching for items to display in an autocomplete or lookup field.

    interface SkyAutocompleteSearchAsyncResult {
      continuationData?: unknown;
      hasMore?: boolean;
      items: unknown[];
      totalCount: number;
    }

### Properties

#### `continuationData?: unknown`

Data provided on "load more" search result requests. Use this property for information such as a continuation token for paged database queries.

#### `hasMore?: boolean`

Whether there are more results that match the search criteria.

#### `items: unknown[]`

A list of items matching the search criteria. When there are more items that match the search criteria, set the `hasMore` property to `true` more records can be lazy-loaded as the user scrolls through the search results.

#### `totalCount: number`

The total number of records that match the search criteria, including items not returned in the current list of items.

 SkyAutocompleteSearchContext
-----------------------------

Type: Type alias

    type SkyAutocompleteSearchContext = "popover" | "modal"

 SkyAutocompleteSearchFunctionFilter
------------------------------------

Type: Type alias

    type SkyAutocompleteSearchFunctionFilter = (searchText: string, item: any, args?: SkyAutocompleteSearchArgs) => boolean

 SkyAutocompleteSearchFunctionResponse
--------------------------------------

Type: Type alias

    type SkyAutocompleteSearchFunctionResponse = any[] | Promise<any[]>

 SkyAutocompleteSearchFunction
------------------------------

Type: Type alias

    type SkyAutocompleteSearchFunction = (searchText: string, data: any[], args?: SkyAutocompleteSearchArgs) => SkyAutocompleteSearchFunctionResponse

 SkyAutocompleteSelectionChange
-------------------------------

Type: Interface

    interface SkyAutocompleteSelectionChange {
      selectedItem?: any;
    }

### Properties

#### `selectedItem?: any`

The search result object that users select in the dropdown list.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyAutocompleteHarness
-----------------------

Type: Class

`import { SkyAutocompleteHarness } from '@skyux/lookup/testing';`

Harness for interacting with an autocomplete component in tests.

### Methods

#### `blur(): Promise<void>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).blur()` instead.

Blurs the autocomplete input.

#### Returns

`Promise<void>`

#### `clear(): Promise<void>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).clear()` instead.

Clears the autocomplete input value.

#### Returns

`Promise<void>`

#### `enterText(value: string): Promise<void>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).setValue()` instead.

Enters text into the autocomplete input.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).focus()` instead.

Focuses the autocomplete input.

#### Returns

`Promise<void>`

#### `getAriaLabelledby(): Promise<null | string>`

Gets the autocomplete `aria-labelledby` value.

#### Returns

`Promise<null | string>`

#### `getControl(): Promise<SkyAutocompleteInputHarness>`

Gets the autocomplete input harness.

#### Returns

`Promise<SkyAutocompleteInputHarness>`

#### `getNoResultsFoundText(): Promise<string>`

Gets the text displayed when no search results are found.

#### Returns

`Promise<string>`

#### `getSearchResult(filter: SkyAutocompleteSearchResultHarnessFilters): Promise<SkyAutocompleteSearchResultHarness>`

Gets a specific autocomplete search result based on the filter criteria.

#### Parameters

##### `filter: SkyAutocompleteSearchResultHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyAutocompleteSearchResultHarness>`

#### `getSearchResults(filters?: SkyAutocompleteSearchResultHarnessFilters): Promise<SkyAutocompleteSearchResultHarness[]>`

Gets an array of autocomplete search results based on the filter criteria. If no filter is provided, returns all autocomplete search results.

#### Parameters

##### `filters?: SkyAutocompleteSearchResultHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyAutocompleteSearchResultHarness[]>`

#### `getSearchResultsText(filters?: SkyAutocompleteSearchResultHarnessFilters): Promise<string[]>`

Returns the text content for each autocomplete search result.

#### Parameters

##### `filters?: SkyAutocompleteSearchResultHarnessFilters`

#### Returns

`Promise<string[]>`

#### `getValue(): Promise<string>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).getValue()` instead.

Gets the value of the autocomplete input.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).isDisabled()` instead.

Whether the autocomplete input is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).isFocused()` instead.

Whether the autocomplete input is focused.

#### Returns

`Promise<boolean>`

#### `isOpen(): Promise<boolean>`

Whether the autocomplete is open.

#### Returns

`Promise<boolean>`

#### `selectSearchResult(filters: SkyAutocompleteSearchResultHarnessFilters): Promise<void>`

Selects a search result.

#### Parameters

##### `filters: SkyAutocompleteSearchResultHarnessFilters`

#### Returns

`Promise<void>`

#### `SkyAutocompleteHarness.with(filters: SkyAutocompleteHarnessFilters): HarnessPredicate<SkyAutocompleteHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyAutocompleteHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyAutocompleteHarnessFilters`

#### Returns

`HarnessPredicate<SkyAutocompleteHarness>`

 SkyAutocompleteHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyAutocompleteHarness](/skyux/components/autocomplete?docs-active-tab=examples#class_sky-autocomplete-harness.md) instances.

    interface SkyAutocompleteHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyAutocompleteSearchResultHarness
-----------------------------------

Type: Class

`import { SkyAutocompleteSearchResultHarness } from '@skyux/lookup/testing';`

Harness for interacting with an autocomplete search result in tests.

### Methods

#### `getDescriptorValue(): Promise<string>`

Returns the value of the search result's descriptor property. This value is set by the autocomplete's `descriptorProperty` input.

#### Returns

`Promise<string>`

#### `getText(): Promise<string>`

Returns the text of the search result.

#### Returns

`Promise<string>`

#### `queryHarness(query: HarnessQuery<T>): Promise<T>`

Returns a child harness or throws an error if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<T>`

#### `queryHarnesses(harness: HarnessQuery<T>): Promise<T[]>`

Returns child harnesses.

#### Parameters

##### `harness: HarnessQuery<T>`

#### Returns

`Promise<T[]>`

#### `queryHarnessOrNull(query: HarnessQuery<T>): Promise<null | T>`

Returns a child harness or null if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<null | T>`

#### `querySelector(selector: string): Promise<TestElement>`

Returns a child test element or throws an error if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement>`

#### `querySelectorAll(selector: string): Promise<TestElement[]>`

Returns child test elements.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement[]>`

#### `querySelectorOrNull(selector: string): Promise<null | TestElement>`

Returns a child test element or null if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<null | TestElement>`

#### `select(): Promise<void>`

Selects the search result.

#### Returns

`Promise<void>`

#### `SkyAutocompleteSearchResultHarness.with(filters: SkyAutocompleteSearchResultHarnessFilters): HarnessPredicate<SkyAutocompleteSearchResultHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyAutocompleteSearchResultHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyAutocompleteSearchResultHarnessFilters`

#### Returns

`HarnessPredicate<SkyAutocompleteSearchResultHarness>`

 SkyAutocompleteSearchResultHarnessFilters
------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyAutocompleteSearchResultHarness](/skyux/components/autocomplete?docs-active-tab=examples#class_sky-autocomplete-search-result-harness.md) instances.

    interface SkyAutocompleteSearchResultHarnessFilters {
      text?: string | RegExp;
    }

### Properties

#### `text?: string | RegExp`

Only find instances whose content matches the given value.

 SkyAutocompleteInputHarness
----------------------------

Type: Class

`import { SkyAutocompleteInputHarness } from '@skyux/lookup/testing';`

Harness to interact with the autocomplete input harness.

### Methods

#### `blur(): Promise<void>`

Blurs the input.

#### Returns

`Promise<void>`

#### `clear(): Promise<void>`

Clears the input value.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the input.

#### Returns

`Promise<void>`

#### `getAriaControls(): Promise<null | string>`

Returns the value of the input's `aria-controls` attribute.

#### Returns

`Promise<null | string>`

#### `getValue(): Promise<string>`

Gets the value of the input.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the input is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the input is focused.

#### Returns

`Promise<boolean>`

#### `setValue(value: string): Promise<void>`

Sets the value of the input. The value will be set by simulating key presses that correspond to the given value.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

### Autocomplete with basic setup

Edit in StackBlitz

Favorite color

Form model:

{
  "favoriteColor": null
}

Show code

Copy

    <form novalidate [formGroup]="formGroup">
      <sky-input-box labelText="Favorite color" stacked>
        <sky-autocomplete data-sky-id="favorite-color" [data]="colors">
          <input formControlName="favoriteColor" type="text" skyAutocomplete />
        </sky-autocomplete>
      </sky-input-box>
      <p class="sky-font-emphasized">Form model:</p>
      <pre>{{ formGroup.value | json }}</pre>
    </form>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { SkyAutocompleteHarness } from '@skyux/lookup/testing';
    
    import { LookupAutocompleteBasicExampleComponent } from './example.component';
    
    describe('Basic autocomplete example', () => {
      async function setupTest(options: { dataSkyId: string }): Promise<{
        harness: SkyAutocompleteHarness;
        fixture: ComponentFixture<LookupAutocompleteBasicExampleComponent>;
      }> {
        const fixture = TestBed.createComponent(
          LookupAutocompleteBasicExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const harness = await loader.getHarness(
          SkyAutocompleteHarness.with({ dataSkyId: options.dataSkyId }),
        );
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        return { harness, fixture };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [LookupAutocompleteBasicExampleComponent],
        });
      });
    
      it('should set up favorite color autocomplete input', async () => {
        const { harness, fixture } = await setupTest({
          dataSkyId: 'favorite-color',
        });
    
        await harness.focus();
        await harness.enterText('b');
    
        const searchResultsText = await harness.getSearchResultsText();
    
        expect(searchResultsText.length).toBe(3);
    
        await harness.clear();
        await harness.enterText('blu');
    
        const searchResults = await harness.getSearchResults();
        await expectAsync(searchResults[0].getDescriptorValue()).toBeResolvedTo(
          'Blue',
        );
        await expectAsync(searchResults[0].getText()).toBeResolvedTo('Blue');
    
        await searchResults[0].select();
        const value =
          fixture.componentInstance.formGroup.get('favoriteColor')?.value;
        expect(value?.name).toBe('Blue');
      });
    });

Copy

    import { CommonModule } from '@angular/common';
    import { Component, inject } from '@angular/core';
    import {
      FormBuilder,
      FormControl,
      FormsModule,
      ReactiveFormsModule,
    } from '@angular/forms';
    import { SkyIdModule } from '@skyux/core';
    import { SkyInputBoxModule } from '@skyux/forms';
    import { SkyAutocompleteModule } from '@skyux/lookup';
    
    /**
     * @title Autocomplete with basic setup
     */
    @Component({
      selector: 'app-lookup-autocomplete-basic-example',
      templateUrl: './example.component.html',
      imports: [
        CommonModule,
        FormsModule,
        ReactiveFormsModule,
        SkyAutocompleteModule,
        SkyIdModule,
        SkyInputBoxModule,
      ],
    })
    export class LookupAutocompleteBasicExampleComponent {
      public colors: { name: string }[] = [
        { name: 'Red' },
        { name: 'Blue' },
        { name: 'Green' },
        { name: 'Orange' },
        { name: 'Pink' },
        { name: 'Purple' },
        { name: 'Yellow' },
        { name: 'Brown' },
        { name: 'Turquoise' },
        { name: 'White' },
        { name: 'Black' },
      ];
    
      public formGroup = inject(FormBuilder).group({
        favoriteColor: new FormControl<{ name: string } | undefined>(undefined),
      });
    }
### Advanced example

Edit in StackBlitz

The following field:  

*   utilizes a custom search result template,
*   searches against the name and description properties,
*   limits the search results to two,
*   runs the search if the query is at least three characters long,
*   and fires an event when a selection is made.

Farthest planet from the sun

Form model:

{
  "farthestPlanet": {}
}

Show code

Copy

    <form novalidate [formGroup]="formGroup">
      <div class="sky-margin-stacked-lg">
        The following field:<br />
        <ul>
          <li>utilizes a custom search result template,</li>
          <li>searches against the name and description properties,</li>
          <li>limits the search results to two,</li>
          <li>runs the search if the query is at least three characters long,</li>
          <li>and fires an event when a selection is made.</li>
        </ul>
      </div>
    
      <div class="sky-margin-stacked-lg">
        <sky-input-box labelText="Farthest planet from the sun" stacked>
          <sky-autocomplete
            [data]="planets"
            [propertiesToSearch]="['name', 'description']"
            [searchResultsLimit]="2"
            [searchResultTemplate]="planetSearchResultTemplate"
            [searchTextMinimumCharacters]="3"
            (selectionChange)="onPlanetSelection($event)"
          >
            <input formControlName="farthestPlanet" skyAutocomplete type="text" />
          </sky-autocomplete>
        </sky-input-box>
      </div>
      <p class="sky-font-emphasized">Form model:</p>
      <pre>{{ formGroup.value | json }}</pre>
    </form>
    
    <ng-template #planetSearchResultTemplate let-item="item">
      <strong>
        {{ item.name }}
      </strong>
      <br />
      {{ item.description }}
    </ng-template>
Copy

    export interface Planet {
      name?: string;
      description?: string;
    }

Copy

    import { CommonModule } from '@angular/common';
    import { Component, inject } from '@angular/core';
    import {
      FormBuilder,
      FormControl,
      FormGroup,
      FormsModule,
      ReactiveFormsModule,
    } from '@angular/forms';
    import { SkyInputBoxModule } from '@skyux/forms';
    import {
      SkyAutocompleteModule,
      SkyAutocompleteSearchFunctionFilter,
      SkyAutocompleteSelectionChange,
    } from '@skyux/lookup';
    
    import { Planet } from './planet';
    
    /**
     * @title Advanced example
     */
    @Component({
      selector: 'app-lookup-autocomplete-advanced-example',
      templateUrl: './example.component.html',
      imports: [
        CommonModule,
        FormsModule,
        ReactiveFormsModule,
        SkyAutocompleteModule,
        SkyInputBoxModule,
      ],
    })
    export class LookupAutocompleteAdvancedExampleComponent {
      protected farthestPlanet: FormControl;
      protected formGroup: FormGroup;
    
      protected planets: Planet[] = [
        {
          name: 'Mercury',
          description: 'Mercury is a planet in our solar system.',
        },
        { name: 'Venus', description: 'Venus is a planet in our solar system.' },
        { name: 'Earth', description: 'Earth is a planet in our solar system.' },
        { name: 'Mars', description: 'Mars is a planet in our solar system.' },
        {
          name: 'Jupiter',
          description: 'Jupiter is a planet in our solar system.',
        },
        { name: 'Saturn', description: 'Saturn is a planet in our solar system.' },
        { name: 'Uranus', description: 'Uranus is a planet in our solar system.' },
        {
          name: 'Neptune',
          description: 'Neptune is a planet in our solar system.',
        },
      ];
    
      protected searchFilters: SkyAutocompleteSearchFunctionFilter[] = [
        (searchText: string, item: Planet): boolean => {
          return item.name !== 'Red';
        },
      ];
    
      readonly #formBuilder = inject(FormBuilder);
    
      constructor() {
        this.farthestPlanet = this.#formBuilder.control({});
        this.formGroup = this.#formBuilder.group({
          farthestPlanet: this.farthestPlanet,
        });
      }
    
      protected onPlanetSelection(args: SkyAutocompleteSelectionChange): void {
        alert(`You selected ${(args.selectedItem as Planet).name}`);
      }
    }
### Autocomplete with custom search

Edit in StackBlitz

The following field has a preselected value and utilizes a custom search function, as well as a custom template for the search results.

Largest ocean

Form model:

{
  "largestOcean": {
    "title": "Arctic",
    "id": 1
  }
}

Show code

Copy

    <form novalidate [formGroup]="formGroup">
      <p>
        The following field has a preselected value and utilizes a custom search
        function, as well as a custom template for the search results.
      </p>
      <div class="sky-margin-stacked-lg">
        <sky-input-box labelText="Largest ocean" stacked>
          <sky-autocomplete
            descriptorProperty="title"
            [data]="oceans"
            [search]="getOceanSearchFunction()"
            [searchResultTemplate]="oceanSearchResultTemplate"
          >
            <input formControlName="largestOcean" type="text" skyAutocomplete />
          </sky-autocomplete>
        </sky-input-box>
      </div>
      <p class="sky-font-emphasized">Form model:</p>
      <pre>{{ formGroup.value | json }}</pre>
    </form>
    
    <ng-template #oceanSearchResultTemplate let-item="item">
      <sky-icon iconName="arrow-right" />
      {{ item.title }} &bull; ID {{ item.id }}
    </ng-template>
Copy

    export interface Ocean {
      id: number;
      title: string;
    }

Copy

    import { CommonModule } from '@angular/common';
    import { Component, inject } from '@angular/core';
    import {
      FormBuilder,
      FormControl,
      FormGroup,
      FormsModule,
      ReactiveFormsModule,
    } from '@angular/forms';
    import { SkyInputBoxModule } from '@skyux/forms';
    import { SkyIconModule } from '@skyux/icon';
    import {
      SkyAutocompleteModule,
      SkyAutocompleteSearchFunction,
      SkyAutocompleteSearchFunctionResponse,
    } from '@skyux/lookup';
    
    import { Ocean } from './ocean';
    
    /**
     * @title Autocomplete with custom search
     */
    @Component({
      selector: 'app-lookup-autocomplete-custom-search-example',
      templateUrl: './example.component.html',
      imports: [
        CommonModule,
        FormsModule,
        ReactiveFormsModule,
        SkyAutocompleteModule,
        SkyIconModule,
        SkyInputBoxModule,
      ],
    })
    export class LookupAutocompleteCustomSearchExampleComponent {
      protected formGroup: FormGroup;
      protected largestOcean: FormControl;
    
      protected oceans: Ocean[] = [
        { title: 'Arctic', id: 1 },
        { title: 'Atlantic', id: 2 },
        { title: 'Indian', id: 3 },
        { title: 'Pacific', id: 4 },
      ];
    
      readonly #formBuilder = inject(FormBuilder);
    
      constructor() {
        this.largestOcean = this.#formBuilder.control({ title: 'Arctic', id: 1 });
        this.formGroup = this.#formBuilder.group({
          largestOcean: this.largestOcean,
        });
      }
    
      protected getOceanSearchFunction(): SkyAutocompleteSearchFunction {
        const searchFunction = (
          searchText: string,
          oceans: Ocean[],
        ): SkyAutocompleteSearchFunctionResponse => {
          return new Promise((resolve) => {
            const searchTextLower = searchText.toLowerCase();
    
            const results = oceans.filter((ocean: Ocean) => {
              const val = ocean.title;
              return !!val?.toString().toLowerCase().includes(searchTextLower);
            });
    
            // Simulate an async request.
            setTimeout(() => {
              resolve(results);
            }, 500);
          });
        };
    
        return searchFunction;
      }
    }
### Autocomplete with search filters

Edit in StackBlitz

The following field provides a custom function that filters the data before every search attempt.

Color ("Red" is not available)

Form model:

{
  "favoriteColor": null
}

Show code

Copy

    <form novalidate [formGroup]="formGroup">
      <p>
        The following field provides a custom function that filters the data before
        every search attempt.
      </p>
      <div class="sky-margin-stacked-lg">
        <sky-input-box labelText='Color ("Red" is not available)' stacked>
          <sky-autocomplete [data]="colors" [searchFilters]="searchFilters">
            <input formControlName="favoriteColor" skyAutocomplete type="text" />
          </sky-autocomplete>
        </sky-input-box>
      </div>
      <p class="sky-font-emphasized">Form model:</p>
      <pre>{{ formGroup.value | json }}</pre>
    </form>

Copy

    import { CommonModule } from '@angular/common';
    import { Component, inject } from '@angular/core';
    import {
      FormBuilder,
      FormGroup,
      FormsModule,
      ReactiveFormsModule,
    } from '@angular/forms';
    import { SkyInputBoxModule } from '@skyux/forms';
    import {
      SkyAutocompleteModule,
      SkyAutocompleteSearchFunctionFilter,
    } from '@skyux/lookup';
    
    /**
     * @title Autocomplete with search filters
     */
    @Component({
      selector: 'app-lookup-autocomplete-search-filters-example',
      templateUrl: './example.component.html',
      imports: [
        CommonModule,
        FormsModule,
        ReactiveFormsModule,
        SkyAutocompleteModule,
        SkyInputBoxModule,
      ],
    })
    export class LookupAutocompleteSearchFiltersExampleComponent {
      protected colors: { name: string }[] = [
        { name: 'Red' },
        { name: 'Blue' },
        { name: 'Green' },
        { name: 'Orange' },
        { name: 'Pink' },
        { name: 'Purple' },
        { name: 'Yellow' },
        { name: 'Brown' },
        { name: 'Turquoise' },
        { name: 'White' },
        { name: 'Black' },
      ];
    
      protected formGroup: FormGroup;
    
      protected searchFilters: SkyAutocompleteSearchFunctionFilter[] = [
        (searchText: string, item: { name: string }): boolean => {
          return item.name !== 'Red';
        },
      ];
    
      constructor() {
        this.formGroup = inject(FormBuilder).group({
          favoriteColor: undefined,
        });
      }
    }
### Autocomplete with any value allowed

Edit in StackBlitz

Favorite color

Show code

Copy

    export interface ColorOption {
      id?: number;
      name: string;
    }
Copy

    <form novalidate [formGroup]="formGroup">
      <sky-input-box labelText="Favorite color" stacked>
        <sky-autocomplete
          data-sky-id="favorite-color"
          allowAnyValue="true"
          highlightSearchText="false"
          (searchAsync)="onSearchAsync($event)"
        >
          <input formControlName="favoriteColor" skyAutocomplete type="text" />
        </sky-autocomplete>
      </sky-input-box>
    
      <span class="selected-color">{{
        formGroup.get('favoriteColor')?.value?.name
      }}</span>
    </form>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { SkyAutocompleteHarness } from '@skyux/lookup/testing';
    
    import { of } from 'rxjs';
    
    import { LookupAutocompleteAnyValueExampleComponent } from './example.component';
    import { LookupAutocompleteAnyValueExampleService } from './example.service';
    
    describe('Autocomplete with any value example', () => {
      let mockSvc!: jasmine.SpyObj<LookupAutocompleteAnyValueExampleService>;
    
      async function setupTest(options: { dataSkyId: string }): Promise<{
        harness: SkyAutocompleteHarness;
        fixture: ComponentFixture<LookupAutocompleteAnyValueExampleComponent>;
      }> {
        const fixture = TestBed.createComponent(
          LookupAutocompleteAnyValueExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const harness = await loader.getHarness(
          SkyAutocompleteHarness.with({ dataSkyId: options.dataSkyId }),
        );
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        return { harness, fixture };
      }
    
      beforeEach(() => {
        // Create a mock search service. In a real-world application, the search
        // service would make a web request which should be avoided in unit tests.
        mockSvc = jasmine.createSpyObj<LookupAutocompleteAnyValueExampleService>(
          'LookupAutocompleteAnyValueExampleService',
          ['search'],
        );
    
        TestBed.configureTestingModule({
          imports: [LookupAutocompleteAnyValueExampleComponent],
          providers: [
            {
              provide: LookupAutocompleteAnyValueExampleService,
              useValue: mockSvc,
            },
          ],
        });
      });
    
      it('should set up favorite color autocomplete input', async () => {
        const { harness, fixture } = await setupTest({
          dataSkyId: 'favorite-color',
        });
    
        mockSvc.search.and.callFake((searchText) =>
          of({
            hasMore: false,
            colors:
              searchText === 'b'
                ? [
                    {
                      id: 1,
                      name: 'Blue',
                    },
                  ]
                : [],
            totalCount: 1,
          }),
        );
    
        const ctrl = await harness.getControl();
    
        await ctrl.focus();
        await ctrl.setValue('b');
    
        const searchResultsText = await harness.getSearchResultsText();
    
        expect(searchResultsText[0]).toBe('b');
        expect(searchResultsText[1]).toBe('Blue');
    
        await ctrl.clear();
        await ctrl.setValue('Turquoise');
    
        const searchResults = await harness.getSearchResults();
        await expectAsync(searchResults[0].getDescriptorValue()).toBeResolvedTo(
          'Turquoise',
        );
        await expectAsync(searchResults[0].getText()).toBeResolvedTo('Turquoise');
    
        await searchResults[0].select();
    
        expect(
          (fixture.nativeElement as HTMLElement).querySelector<HTMLElement>(
            '.selected-color',
          )?.innerText,
        ).toBe('Turquoise');
      });
    });
Copy

    import { Injectable } from '@angular/core';
    
    import { Observable, delay, of } from 'rxjs';
    
    import { ColorOption } from './color-option';
    import { SearchResults } from './search-results';
    
    const colors: ColorOption[] = [
      { id: 1, name: 'Red' },
      { id: 2, name: 'Blue' },
      { id: 3, name: 'Green' },
    ];
    
    @Injectable({
      providedIn: 'root',
    })
    export class LookupAutocompleteAnyValueExampleService {
      public search(searchText: string): Observable<SearchResults> {
        // Simulate a network call with latency. A real-world application might
        // use Angular's HttpClient to create an Observable from a call to a
        // web service.
        searchText = searchText.toUpperCase();
    
        const matchingColors = colors.filter((color) =>
          color.name.toUpperCase().includes(searchText),
        );
    
        return of({
          hasMore: false,
          colors: matchingColors,
          totalCount: matchingColors.length,
        }).pipe(delay(800));
      }
    }
Copy

    import { ColorOption } from './color-option';
    
    export interface SearchResults {
      hasMore: boolean;
      colors: ColorOption[];
      totalCount: number;
    }

Copy

    import { Component, inject } from '@angular/core';
    import {
      FormBuilder,
      FormControl,
      FormsModule,
      ReactiveFormsModule,
    } from '@angular/forms';
    import { SkyInputBoxModule } from '@skyux/forms';
    import {
      SkyAutocompleteModule,
      SkyAutocompleteSearchAsyncArgs,
    } from '@skyux/lookup';
    
    import { map } from 'rxjs';
    
    import { ColorOption } from './color-option';
    import { LookupAutocompleteAnyValueExampleService } from './example.service';
    
    /**
     * @title Autocomplete with any value allowed
     */
    @Component({
      selector: 'app-lookup-autocomplete-basic-example',
      templateUrl: './example.component.html',
      imports: [
        FormsModule,
        ReactiveFormsModule,
        SkyAutocompleteModule,
        SkyInputBoxModule,
      ],
    })
    export class LookupAutocompleteAnyValueExampleComponent {
      readonly #svc = inject(LookupAutocompleteAnyValueExampleService);
    
      protected readonly favoriteColor = new FormControl<ColorOption | undefined>(
        undefined,
      );
    
      public readonly formGroup = inject(FormBuilder).group({
        favoriteColor: this.favoriteColor,
      });
    
      protected onSearchAsync(args: SkyAutocompleteSearchAsyncArgs): void {
        // In a real-world application the search service might return an Observable
        // created by calling HttpClient.get(). Assigning that Observable to the result
        // allows the autocomplete component to cancel the web request if it does not
        // // complete before the user searches again.
        args.result = this.#svc.search(args.searchText).pipe(
          map((result) => ({
            hasMore: result.hasMore,
            items: result.colors,
            totalCount: result.totalCount,
          })),
        );
      }
    }

# Testing

                  Skip to Main Content

 Autocomplete
============

The autocomplete text input filters a data source based on user entries and then displays search results in a dropdown list.

 Usage
------

### Use when

Use the autocomplete component when users know what they are looking for and can select a single item. For guidance on which selection inputs to use in other scenarios, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/lookup`[View in NPM](https://www.npmjs.com/package/@skyux/lookup) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lookup/src/lib/modules/autocomplete/autocomplete.module.ts#L35) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lookup`Copy None found.

 SkyAutocompleteModule
----------------------

Type: Module

`import { SkyAutocompleteModule } from '@skyux/lookup';`

 SkyAutocompleteComponent
-------------------------

Type: Component

Selector: `sky-autocomplete`

### Inputs

#### `allowAnyValue: InputSignalWithTransform<boolean, unknown>`

When using `searchAsync`, allows the user to specify arbitrary values not in the search results. This only works in combination with `searchAsync`.

Default: `false`

#### `ariaLabelledBy: string | undefined`

The HTML element ID of the element that labels the autocomplete text input. This sets the input's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `data: any[]`

The static data source for the autocomplete component to search when users enter text. For a dynamic data source, such as an array that changes due to server calls, use `search` or `searchAsync` instead. You can specify static data, such as an array of objects, or you can pull data from a database.

#### `debounceTime: number`

How many milliseconds to wait before searching while users enter text in the autocomplete field.

Default: `0`

#### `descriptorProperty: string`

The object property to display in the text input after users select an item in the dropdown list.

Default: `"name"`

#### `highlightSearchText: InputSignalWithTransform<boolean, unknown>`

Highlights the search text in each search result. Set this to `false` when your search returns results that aren't exact text matches, such as returning "Bob" for "Robert."

Default: `true`

#### `noResultsFoundText: string | undefined`

The text to display when no search results are found.

Default: `"No matches found"`

#### `propertiesToSearch: string[]`

Warning: **Deprecated.** We recommend against using this property. To search specific properties, use the `searchAsync` event instead.

The object properties to search.

Default: `["name"]`

#### `search: SkyAutocompleteSearchFunction | undefined`

Warning: **Deprecated.** We recommend against using this property. To call a remote data source, use the `searchAsync` event instead.

The function that dynamically manages the data to display in search results when users change the text in the autocomplete field. The search function must return an array or a promise of an array. The `search` property is particularly useful when the data source does not live in the source code.

#### `searchFilters: SkyAutocompleteSearchFunctionFilter[] | undefined`

Warning: **Deprecated.** We recommend against using this property. To filter results, use the `searchAsync` event instead.

The array of functions to call against each search result. This filters the search results when using the `data` input and the default search function. When the `search` property specifies a custom search function, you must manually apply filters inside that function. The function must return `true` or `false` for each result to indicate whether to display it in the dropdown list.

#### `searchResultTemplate: TemplateRef<unknown> | undefined`

The template that formats each search result in the dropdown list. The autocomplete component injects search result values into the template as `item` variables that reference all of the object properties of the search results.

#### `searchResultsLimit: number`

The maximum number of search results to display in the dropdown list. By default, the component displays all matching results.

#### `searchTextMinimumCharacters: number`

The minimum number of characters that users must enter before the autocomplete component searches the data source and displays search results in the dropdown list.

Default: `1`

### Outputs

#### `searchAsync: EventEmitter<SkyAutocompleteSearchAsyncArgs>`

Fires when users enter new search information and allows results to be returned via an observable.

#### `selectionChange: EventEmitter<SkyAutocompleteSelectionChange>`

Fires when users select items in the dropdown list.

 SkyAutocompleteInputDirective
------------------------------

Type: Directive

Selector: `input[skyAutocomplete], textarea[skyAutocomplete]`

### Inputs

#### `autocompleteAttribute: string`

Warning: **Deprecated.** SKY UX only supports browser autofill on components where the direct input matches the return value. This input may not behave as expected due to the dropdown selection interaction.

The value for the `autocomplete` attribute on the form input.

Default: `"off"`

#### `disabled: boolean`

Whether to disable the autocomplete field on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

 SkyAutocompleteSearchArgs
--------------------------

Type: Interface

    interface SkyAutocompleteSearchArgs {
      context?: SkyAutocompleteSearchContext;
    }

### Properties

#### `context?: SkyAutocompleteSearchContext`

 SkyAutocompleteSearchAsyncArgs
-------------------------------

Type: Interface

Arguments passed when an asynchronous search is executed from the autocomplete or lookup component.

    interface SkyAutocompleteSearchAsyncArgs {
      continuationData?: unknown;
      displayType: AutocompleteSearchAsyncResultDisplayType;
      offset: number;
      result?: Observable<SkyAutocompleteSearchAsyncResult>;
      searchText: string;
    }

### Properties

#### `continuationData?: unknown`

A continuation token which can be set and then will be passed back with any future searches. This is helpful for applications which utilize a token instead of an offset when fetching data.

#### `displayType: AutocompleteSearchAsyncResultDisplayType`

How the search results will be displayed. Use this value to determine how many results to return.

#### `offset: number`

The offset index of the first result to return. When search is executed as a result of an infinite scroll event, for example, offset will be set to the number of items already displayed.

#### `result?: Observable<SkyAutocompleteSearchAsyncResult>`

An Observable representing the search results. Consumers should set this when the event fires so the autocomplete or lookup component can subscribe to it and then display the results.

#### `searchText: string`

The search text entered by the user.

 AutocompleteSearchAsyncResultDisplayType
-----------------------------------------

Type: Type alias

    type AutocompleteSearchAsyncResultDisplayType = "popover" | "modal"

 SkyAutocompleteSearchAsyncResult
---------------------------------

Type: Interface

The result of searching for items to display in an autocomplete or lookup field.

    interface SkyAutocompleteSearchAsyncResult {
      continuationData?: unknown;
      hasMore?: boolean;
      items: unknown[];
      totalCount: number;
    }

### Properties

#### `continuationData?: unknown`

Data provided on "load more" search result requests. Use this property for information such as a continuation token for paged database queries.

#### `hasMore?: boolean`

Whether there are more results that match the search criteria.

#### `items: unknown[]`

A list of items matching the search criteria. When there are more items that match the search criteria, set the `hasMore` property to `true` more records can be lazy-loaded as the user scrolls through the search results.

#### `totalCount: number`

The total number of records that match the search criteria, including items not returned in the current list of items.

 SkyAutocompleteSearchContext
-----------------------------

Type: Type alias

    type SkyAutocompleteSearchContext = "popover" | "modal"

 SkyAutocompleteSearchFunctionFilter
------------------------------------

Type: Type alias

    type SkyAutocompleteSearchFunctionFilter = (searchText: string, item: any, args?: SkyAutocompleteSearchArgs) => boolean

 SkyAutocompleteSearchFunctionResponse
--------------------------------------

Type: Type alias

    type SkyAutocompleteSearchFunctionResponse = any[] | Promise<any[]>

 SkyAutocompleteSearchFunction
------------------------------

Type: Type alias

    type SkyAutocompleteSearchFunction = (searchText: string, data: any[], args?: SkyAutocompleteSearchArgs) => SkyAutocompleteSearchFunctionResponse

 SkyAutocompleteSelectionChange
-------------------------------

Type: Interface

    interface SkyAutocompleteSelectionChange {
      selectedItem?: any;
    }

### Properties

#### `selectedItem?: any`

The search result object that users select in the dropdown list.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyAutocompleteHarness
-----------------------

Type: Class

`import { SkyAutocompleteHarness } from '@skyux/lookup/testing';`

Harness for interacting with an autocomplete component in tests.

### Methods

#### `blur(): Promise<void>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).blur()` instead.

Blurs the autocomplete input.

#### Returns

`Promise<void>`

#### `clear(): Promise<void>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).clear()` instead.

Clears the autocomplete input value.

#### Returns

`Promise<void>`

#### `enterText(value: string): Promise<void>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).setValue()` instead.

Enters text into the autocomplete input.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).focus()` instead.

Focuses the autocomplete input.

#### Returns

`Promise<void>`

#### `getAriaLabelledby(): Promise<null | string>`

Gets the autocomplete `aria-labelledby` value.

#### Returns

`Promise<null | string>`

#### `getControl(): Promise<SkyAutocompleteInputHarness>`

Gets the autocomplete input harness.

#### Returns

`Promise<SkyAutocompleteInputHarness>`

#### `getNoResultsFoundText(): Promise<string>`

Gets the text displayed when no search results are found.

#### Returns

`Promise<string>`

#### `getSearchResult(filter: SkyAutocompleteSearchResultHarnessFilters): Promise<SkyAutocompleteSearchResultHarness>`

Gets a specific autocomplete search result based on the filter criteria.

#### Parameters

##### `filter: SkyAutocompleteSearchResultHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyAutocompleteSearchResultHarness>`

#### `getSearchResults(filters?: SkyAutocompleteSearchResultHarnessFilters): Promise<SkyAutocompleteSearchResultHarness[]>`

Gets an array of autocomplete search results based on the filter criteria. If no filter is provided, returns all autocomplete search results.

#### Parameters

##### `filters?: SkyAutocompleteSearchResultHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyAutocompleteSearchResultHarness[]>`

#### `getSearchResultsText(filters?: SkyAutocompleteSearchResultHarnessFilters): Promise<string[]>`

Returns the text content for each autocomplete search result.

#### Parameters

##### `filters?: SkyAutocompleteSearchResultHarnessFilters`

#### Returns

`Promise<string[]>`

#### `getValue(): Promise<string>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).getValue()` instead.

Gets the value of the autocomplete input.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).isDisabled()` instead.

Whether the autocomplete input is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Warning: **Deprecated.** Call `await (await autocomplete.getControl()).isFocused()` instead.

Whether the autocomplete input is focused.

#### Returns

`Promise<boolean>`

#### `isOpen(): Promise<boolean>`

Whether the autocomplete is open.

#### Returns

`Promise<boolean>`

#### `selectSearchResult(filters: SkyAutocompleteSearchResultHarnessFilters): Promise<void>`

Selects a search result.

#### Parameters

##### `filters: SkyAutocompleteSearchResultHarnessFilters`

#### Returns

`Promise<void>`

#### `SkyAutocompleteHarness.with(filters: SkyAutocompleteHarnessFilters): HarnessPredicate<SkyAutocompleteHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyAutocompleteHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyAutocompleteHarnessFilters`

#### Returns

`HarnessPredicate<SkyAutocompleteHarness>`

 SkyAutocompleteHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyAutocompleteHarness](/skyux/components/autocomplete?docs-active-tab=testing#class_sky-autocomplete-harness.md) instances.

    interface SkyAutocompleteHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyAutocompleteSearchResultHarness
-----------------------------------

Type: Class

`import { SkyAutocompleteSearchResultHarness } from '@skyux/lookup/testing';`

Harness for interacting with an autocomplete search result in tests.

### Methods

#### `getDescriptorValue(): Promise<string>`

Returns the value of the search result's descriptor property. This value is set by the autocomplete's `descriptorProperty` input.

#### Returns

`Promise<string>`

#### `getText(): Promise<string>`

Returns the text of the search result.

#### Returns

`Promise<string>`

#### `queryHarness(query: HarnessQuery<T>): Promise<T>`

Returns a child harness or throws an error if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<T>`

#### `queryHarnesses(harness: HarnessQuery<T>): Promise<T[]>`

Returns child harnesses.

#### Parameters

##### `harness: HarnessQuery<T>`

#### Returns

`Promise<T[]>`

#### `queryHarnessOrNull(query: HarnessQuery<T>): Promise<null | T>`

Returns a child harness or null if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<null | T>`

#### `querySelector(selector: string): Promise<TestElement>`

Returns a child test element or throws an error if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement>`

#### `querySelectorAll(selector: string): Promise<TestElement[]>`

Returns child test elements.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement[]>`

#### `querySelectorOrNull(selector: string): Promise<null | TestElement>`

Returns a child test element or null if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<null | TestElement>`

#### `select(): Promise<void>`

Selects the search result.

#### Returns

`Promise<void>`

#### `SkyAutocompleteSearchResultHarness.with(filters: SkyAutocompleteSearchResultHarnessFilters): HarnessPredicate<SkyAutocompleteSearchResultHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyAutocompleteSearchResultHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyAutocompleteSearchResultHarnessFilters`

#### Returns

`HarnessPredicate<SkyAutocompleteSearchResultHarness>`

 SkyAutocompleteSearchResultHarnessFilters
------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyAutocompleteSearchResultHarness](/skyux/components/autocomplete?docs-active-tab=testing#class_sky-autocomplete-search-result-harness.md) instances.

    interface SkyAutocompleteSearchResultHarnessFilters {
      text?: string | RegExp;
    }

### Properties

#### `text?: string | RegExp`

Only find instances whose content matches the given value.

 SkyAutocompleteInputHarness
----------------------------

Type: Class

`import { SkyAutocompleteInputHarness } from '@skyux/lookup/testing';`

Harness to interact with the autocomplete input harness.

### Methods

#### `blur(): Promise<void>`

Blurs the input.

#### Returns

`Promise<void>`

#### `clear(): Promise<void>`

Clears the input value.

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the input.

#### Returns

`Promise<void>`

#### `getAriaControls(): Promise<null | string>`

Returns the value of the input's `aria-controls` attribute.

#### Returns

`Promise<null | string>`

#### `getValue(): Promise<string>`

Gets the value of the input.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the input is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the input is focused.

#### Returns

`Promise<boolean>`

#### `setValue(value: string): Promise<void>`

Sets the value of the input. The value will be set by simulating key presses that correspond to the given value.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`