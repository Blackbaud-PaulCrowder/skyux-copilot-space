                    

 Lookup
======

The lookup text input lets users search a long list of options and make selections. Lookup fields must be wrapped in [input boxes](/skyux/components/input-box.md) to provide styling, ordering, and positioning within forms.

 Usage
------

### Use when

Use lookup fields when users must choose one or more options from a very long list or from an unpredictable list with unfamiliar options. Lookup fields allow users to enter search criteria to narrow their options, so they are useful when lists are unique to the system. For example, use lookup fields for user-defined lists such as code tables where the options are unpredictable and for system-defined lists such as templates where the options are unique to the organization.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/lookup/lookup-usage-1.9b8ef00bec87fa95d9fdf58f7c42d22e.png)

Do use lookup fields when users choose from long lists of options.

Use lookup fields when users can choose multiple options from a long list.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/lookup/lookup-usage-2.1188497927c1008d190619707be6c0a1.png)

Do use lookup fields when users may need to select multiple options.

Use lookup fields when users can add options to the list during their tasks.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/lookup/lookup-usage-3.8c73bcb9d1334a18e6b7ea951a851a15.png)

Do use lookup fields when users may need to add options to the list.

### Don't use when

Don't use lookup fields when short lists include 5 options or fewer, especially if it is valuable for users to see all options at once. Use [checkboxes](/skyux/components/checkbox.md) or [radio buttons](/skyux/components/radio.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/lookup/lookup-usage-4.e9e761a1ab1dfbd2d2289981cac6196e.png)

Don't use lookup fields when users choose options from a short list.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/lookup/lookup-usage-5.f0ed25a1978a0f92bfda8bc65ebe1428.png)

Do use different selection inputs for a short list of options.

Don't use lookup fields when options are highly predictable or when users can easily browse options in an expected order. Use HTML select fields instead. For example, while a list of states is long, it's predictable and most users are familiar with the options, so the native HTML select field is the preferable option.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/lookup/lookup-usage-6.ad9182c0cd0b13e88e232a1bf9c68b93.png)

Don't use lookup fields when users likely know all the options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/lookup/lookup-usage-7.5618c47a7022786903ea536788354594.png)

Do use HTML select fields for predictable or common sets of options.

Don't use lookup fields when users need to interact with the selected options or when the options require more depth than lookup tokens provide. Instead, use a button to open a [selection modal](/skyux/components/selection-modal.md) where users can select options, and then display selections in whatever format is needed.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/lookup/lookup-usage-8.bae9529c2a3233a31aa74ad92a6613d2.png)

Don't use lookup fields for more than basic selection.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/lookup/selection-modal-usage-2.3ca3edb4987cf5b6e6dadcfe1edd98ae.png)

Do use selection modals to let users interact with selections.

 Anatomy
--------

1

Label

2

Search button

3

Input field

4

Required field marker (optional)

5

Help inline button (optional)

6

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/lookup/lookup-anatomy.9bca7f20c0319232fb190098f59e72c4.png)

### Search results

1

Lookup menu

2

Search results

3

'Show all/matches' button

4

'New' button (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/lookup/lookup-anatomy-results.fc50658b4ff30153469d9cd2c2a4e5b1.png)

 Options
--------

### Single-select and multi-select

Use a single-select to let users select a single option and multi-select to let users select multiple options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/lookup/lookup-options-1.c346a56f503b11132a34f75cba4d1e56.png)

### Required field marker

When a lookup field is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the [form design guidelines](/skyux/design/guidelines/form-design#validation-and-error-handling.md).

### Help inline button

When you need to supplement a lookup field with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a lookup field, use hint text. This persistent inline help can explain details such as:

*   The correct format
*   Any constraints on the input
*   Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a lookup field is immediately followed by another form input, use `stacked` to add a bottom margin that visually separates the lookup from the form input under it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design#form-layout.md).

Don't use `stacked` when the lookup:

*   Is the last input before a [field group](/skyux/components/field-group.md)
*   Is the last input on a form
*   Is followed by one or more conditional fields (use `sky-margin-stacked-sm` instead for closely related fields)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/lookup/lookup-options-stacked.c1e7dd22a3ebb6529c3194eaa7804728.png)

### Button to view all options

The 'Show all/matches' button in the lookup menu lets users open a picker that either displays all options or just the options that match their search string. This button is technically optional for backwards compatibility, but we strongly recommend that you enable it in all instances.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/lookup/lookup-options-2.db8d96f12788dc3771b260494b8d092a.png)

### Custom results template

Use a custom results template when users need more information in the search results to help them select the correct options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/lookup/lookup-options-3.692ba41d40747c3b40af5343b9726127.png)

### Custom picker

By default, the search and "Show all/matches" buttons display a [selection modal](/skyux/components/selection-modal.md) with a selectable [repeater](/skyux/components/repeater.md). When different presentations are valuable, use custom pickers, such as custom repeaters or [tree views](/skyux/components/angular-tree.md). By default, both the native picker and custom pickers format options based on the same template as the dropdown list, but you can specify a different template to format the picker options as necessary.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/lookup/lookup-options-4.3c3c9a2ee3ec8628d6eba932c7beafda.png)

 Behavior and states
--------------------

### Behavior

When users place focus on lookup fields, the lookup menu displays the 'Show all #' button. It also displays the 'New' button if that is enabled.

When users enter the minimum number of characters for search, the lookup menu displays search results and highlights the search string. The “Show all #” button label changes to “Show matches (#)."

At any time, users can select the search or 'Show all/matches' buttons to open a picker that either displays all options or the options that match their search string.

When users choose an option in single-select mode, the lookup menu or picker closes, and the selected option appears as text in the lookup field.

When users choose options in multi-select mode, the selected options appear as tokens in the text input field, and focus returns to the lookup field. The lookup menu displays the 'Show all #' button but does not display search results until users enter the minimum number of characters.

When users remove focus before selecting an option, the lookup field deletes any text.

 Related information
--------------------

### Components

*   [Checkbox](/skyux/components/checkbox.md)
*   [Field group](/skyux/components/field-group.md)
*   [Help inline button](/skyux/components/help%3Dinlin.md)
*   [Input box](/skyux/components/input-box.md)
*   [Radio button](/skyux/components/radio.md)
*   [Selection modal](/skyux/components/selection-modal.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/lookup`[View in NPM](https://www.npmjs.com/package/@skyux/lookup) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lookup/src/lib/modules/lookup/lookup.module.ts#L24) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lookup`Copy None found.

 Setup
------

To enable standard form features, you must wrap the lookup in an [input box](/skyux/components/input-box.md). Use `labelText` and the appropriate inputs on the input box. For example, use `helpInlineContent` or `helpKey` to add a help inline button, `hintText` to display persistent inline help, and `stacked` to provide vertical spacing between components. To provide a custom validation error message, use `sky-form-error` within the `sky-input-box` element.

 SkyLookupModule
----------------

Type: Module

`import { SkyLookupModule } from '@skyux/lookup';`

 SkyLookupComponent
-------------------

Type: Component

Selector: `sky-lookup`

### Inputs

#### `ariaLabel: string | undefined`

Warning: **Deprecated.** Use the input box `labelText` input instead.

The ARIA label for the typeahead search input. This sets the input's `aria-label` attribute to provide a text equivalent for [to support accessibility](/skyux/learn/accessibility.md). If the input includes a visible label, use `ariaLabelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `ariaLabelledBy: string | undefined`

Warning: **Deprecated.** Use the input box `labelText` input instead.

The HTML element ID of the element that labels the typeahead search input. This sets the input's `aria-labelledby` attribute to provide a text equivalent for [to support accessibility](/skyux/learn/accessibility.md). If the input does not include a visible label, use `ariaLabel` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `autocompleteAttribute: string | undefined`

Warning: **Deprecated.** SKY UX only supports browser autofill on components where the direct input matches the return value. This input may not behave as expected due to the dropdown selection interaction.

The value to provide to the `autocomplete` attribute on the form input.

Default: `'off'`

#### `data: any[]`

Warning: **Deprecated.** Use the `searchAsync` event emitter and callback instead to provide data to the lookup component.

The data source for the lookup component to search when users enter text. You can specify static data, such as an array of objects, or you can pull data from a database.

Default: `[]`

#### `debounceTime: number | undefined`

How many milliseconds to wait before searching while users enter text in the lookup field.

Default: `0`

#### `descriptorProperty: string`

The object property to display in the text input after users select an item in the dropdown list.

Default: `"name"`

#### `disabled: boolean`

Whether to disable the lookup field on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync. To set the disabled state on reactive forms, use the `FormControl` instead.

Default: `false`

#### `enableShowMore: boolean`

Whether to enable users to open a picker where they can view all options.

Default: `false`

#### `idProperty: string | undefined`

The object property that represents the object's unique identifier. Specifying this property enables token animations and more efficient rendering. This property is required when using `enableShowMore` and `searchAsync` together.

#### `placeholderText: string | undefined`

Placeholder text to display in the lookup field.

#### `propertiesToSearch: string[]`

Warning: **Deprecated.** Use the `searchAsync` event emitter and callback instead to provide data to the lookup component.

The array of object properties to search when utilizing the `data` property and the built-in search function.

Default: `["name"]`

#### `required: boolean`

Whether the lookup field is required.

Default: `false`

#### `search: SkyAutocompleteSearchFunction | undefined`

Warning: **Deprecated.** Use the `searchAsync` event emitter and callback instead to provide searched data to the lookup component.

The function that dynamically manages the data to display in search results when users change the text in the lookup field. The search function must return an array or a promise of an array. The `search` property is particularly useful when the data source does not live in the source code.

#### `searchFilters: SkyAutocompleteSearchFunctionFilter[] | undefined`

Warning: **Deprecated.** Use the `searchAsync` event emitter and callback instead to provide searched data to the lookup component.

The array of functions to call against each search result in order to filter the search results when using the `data` input and the default search function. When using a custom search function via the `search` property filters must be applied manually inside that function. The function must return `true` or `false` for each result to indicate whether to display it in the dropdown list.

#### `searchResultTemplate: TemplateRef<unknown> | undefined`

The template that formats each option in the dropdown list. The lookup component injects values into the template as `item` variables that reference all of the object properties of the search results.

#### `searchResultsLimit: number | undefined`

The maximum number of search results to display in the dropdown list. By default, the lookup component displays all matching results. This property has no effect on the results in the "Show more" picker.

#### `searchTextMinimumCharacters: number | undefined`

The minimum number of characters that users must enter before the lookup component searches the data source and displays search results in the dropdown list.

Default: `1`

#### `selectMode: SkyLookupSelectModeType`

The ability for users to select one option or multiple options.

Default: `"multiple"`

#### `showAddButton: boolean`

Whether to display a button that lets users add options to the list.

Default: `false`

#### `showMoreConfig: SkyLookupShowMoreConfig | undefined`

Configuration options for the picker that displays all options.

### Outputs

#### `addClick: EventEmitter<SkyLookupAddClickEventArgs>`

Fires when users select the button to add options to the list.

#### `searchAsync: EventEmitter<SkyAutocompleteSearchAsyncArgs>`

Fires when users enter new search information and allows results to be returned via an observable. The event is also fired when the "Show more" picker is opened without search text.

 SkyLookupAddCallbackArgs
-------------------------

Type: Interface

Specifies the information for the callback used when adding a new item to the lookup component.

    interface SkyLookupAddCallbackArgs {
      data?: any[];
      item: any;
    }

### Properties

#### `data?: any[]`

The new state of the data source for the lookup component to search when users enter text. If not specified, the component will use the current state of the lookup component's `data` input; however, if this is not yet updated the new item will not be automatically selected.

#### `item: any`

The new item which has been added to the data. This item will be automatically selected.

 SkyLookupAddClickEventArgs
---------------------------

Type: Interface

Specifies a callback function for the consumer to use to notify the lookup that a new item has been added.

    interface SkyLookupAddClickEventArgs {
      itemAdded: (args: SkyLookupAddCallbackArgs) => void;
    }

### Properties

#### `itemAdded: (args: SkyLookupAddCallbackArgs) => void`

A callback function for the consumer to use to notify the lookup that a new item has been added.

 SkyLookupSelectModeType
------------------------

Type: Type alias

    type SkyLookupSelectModeType = "single" | "multiple"

 SkyLookupShowMoreConfig
------------------------

Type: Interface

Specifies configuration options for the picker to display when users select the button to view all options. You can use a native, out-of-the-box modal picker, or you can create a custom picker. If you provide configuration options for both, the lookup component uses the custom configuration.

    interface SkyLookupShowMoreConfig {
      customPicker?: SkyLookupShowMoreCustomPicker;
      nativePickerConfig?: SkyLookupShowMoreNativePickerConfig;
    }

### Properties

#### `customPicker?: SkyLookupShowMoreCustomPicker`

The configuration object to display a custom picker.

#### `nativePickerConfig?: SkyLookupShowMoreNativePickerConfig`

Configuration options for the native picker.

 SkyLookupShowMoreCustomPickerContext
-------------------------------------

Type: Class

Specifies configuration options to launch a custom picker when users select the button to view all options.

### Properties

#### `initialSearch: string`

Search text to filter the contents of the custom picker.

#### `initialValue: any`

The current selections in the lookup field.

#### `items: any[]`

The options that users can select in the custom picker.

 SkyLookupShowMoreCustomPicker
------------------------------

Type: Interface

Defines a custom picker to display when users select the button to view all options.

    interface SkyLookupShowMoreCustomPicker {
      open: (pickerContext: SkyLookupShowMoreCustomPickerContext) => void;
    }

### Properties

#### `open: (pickerContext: SkyLookupShowMoreCustomPickerContext) => void`

 SkyLookupShowMoreNativePickerConfig
------------------------------------

Type: Interface

Specifies configuration options to display the native picker when users select the button to view all options.

    interface SkyLookupShowMoreNativePickerConfig {
      itemTemplate?: TemplateRef<unknown>;
      selectionDescriptor?: string;
      title?: string;
    }

### Properties

#### `itemTemplate?: TemplateRef<unknown>`

The template that formats each option in the picker. The lookup component injects values into the template as `item` variables that reference all the object properties of the options. If you do not specify a template, the picker uses the same template as the dropdown list.

#### `selectionDescriptor?: string`

A descriptor for the item or items being selected. Use a plural term when the lookup's `selectMode` is set to `'multiple'`; otherwise, use a singular term. The descriptor helps set the picker's `aria-label` attributes for the multiselect toolbar controls, the search input, and the save button to provide text equivalents for screen readers [to support accessibility](/skyux/components/checkbox#accessibility.md). For example, when the descriptor is "constituents," the search input's `aria-label` is "Search constituents." For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `title?: string`

Warning: **Deprecated.** Use the `selectionDescriptor` input to give context to the title and accessibility labels instead.

The title for the picker.

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

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyLookupHarness
-----------------

Type: Class

`import { SkyLookupHarness } from '@skyux/lookup/testing';`

Harness for interacting with a lookup component in tests.

### Methods

#### `blur(): Promise<void>`

Warning: **Deprecated.** Call `await (await lookup.getControl()).blur()` instead.

Blurs the lookup input.

#### Returns

`Promise<void>`

#### `clear(): Promise<void>`

Warning: **Deprecated.** Call `await (await lookup.getControl()).clear()` instead.

Clears the lookup input value.

#### Returns

`Promise<void>`

#### `clickAddButton(): Promise<void>`

Clicks the "Add" button on the search results panel.

#### Returns

`Promise<void>`

#### `clickShowMoreButton(): Promise<void>`

Clicks the "Show more" button on the search results panel.

#### Returns

`Promise<void>`

#### `dismissSelections(): Promise<void>`

Dismisses the selections made with a multiselect lookup.

#### Returns

`Promise<void>`

#### `enterText(value: string): Promise<void>`

Warning: **Deprecated.** Call `await (await lookup.getControl()).setValue()` instead.

Enters text into the lookup input.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Warning: **Deprecated.** Call `await (await lookup.getControl()).focus()` instead.

Focuses the lookup input.

#### Returns

`Promise<void>`

#### `getAriaLabelledby(): Promise<null | string>`

Warning: **Deprecated.** Don't use this property. It returns a value from a deprecated input that lookup no longer uses.

Gets the lookup `aria-labelledby` value.

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

#### `getSearchResult(filters: SkyLookupSearchResultHarnessFilters): Promise<SkyLookupSearchResultHarness>`

Gets a specific lookup search result based on the filter criteria.

#### Parameters

##### `filters: SkyLookupSearchResultHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyLookupSearchResultHarness>`

#### `getSearchResults(filters?: SkyLookupSearchResultHarnessFilters): Promise<SkyLookupSearchResultHarness[]>`

Gets an array of lookup search results based on the filter criteria. If no filter is provided, returns all lookup search results.

#### Parameters

##### `filters?: SkyLookupSearchResultHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyLookupSearchResultHarness[]>`

#### `getSearchResultsText(filters?: SkyLookupSearchResultHarnessFilters): Promise<string[]>`

Returns the text content for each lookup search result.

#### Parameters

##### `filters?: SkyLookupSearchResultHarnessFilters`

#### Returns

`Promise<string[]>`

#### `getSelections(): Promise<SkyLookupSelectionHarness[]>`

Gets a list of selections made with a multiselect lookup.

#### Returns

`Promise<SkyLookupSelectionHarness[]>`

#### `getSelectionsText(): Promise<string[]>`

Gets the text content of all selections made with a multiselect lookup.

#### Returns

`Promise<string[]>`

#### `getShowMorePicker(): Promise<SkyLookupShowMorePickerHarness>`

Gets the "Show more" picker harness.

#### Returns

`Promise<SkyLookupShowMorePickerHarness>`

#### `getValue(): Promise<string>`

Warning: **Deprecated.** Call `await (await lookup.getControl()).getValue()` instead.

Gets the value of the lookup input.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Warning: **Deprecated.** Call `await (await lookup.getControl()).isDisabled()` instead.

Whether the lookup input is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Warning: **Deprecated.** Call `await (await lookup.getControl()).isFocused()` instead.

Whether the lookup input is focused.

#### Returns

`Promise<boolean>`

#### `isMultiselect(): Promise<boolean>`

Whether the lookup allows for multiple selections.

#### Returns

`Promise<boolean>`

#### `isOpen(): Promise<boolean>`

Whether the lookup is open.

#### Returns

`Promise<boolean>`

#### `selectSearchResult(filters: SkyLookupSearchResultHarnessFilters): Promise<void>`

Selects a search result.

#### Parameters

##### `filters: SkyLookupSearchResultHarnessFilters`

#### Returns

`Promise<void>`

#### `SkyLookupHarness.with(filters: SkyLookupHarnessFilters): HarnessPredicate<SkyLookupHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyLookupHarness` that meets certain criteria.

These filters only work for standalone lookups. For lookups wrapped inside `sky-input-box`, place filters on the input box instead and query the datepicker using a `SkyInputBoxHarness`. For the input box implementation, see the code example.

#### Parameters

##### `filters: SkyLookupHarnessFilters`

#### Returns

`HarnessPredicate<SkyLookupHarness>`

 SkyLookupHarnessFilters
------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyLookupHarness` instances.

    interface SkyLookupHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyLookupSearchResultHarness
-----------------------------

Type: Class

`import { SkyLookupSearchResultHarness } from '@skyux/lookup/testing';`

Harness for interacting with an autocomplete search result in tests.

### Methods

#### `getDescriptorValue(): Promise<string>`

Returns the value of the search result's descriptor property.

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

#### `SkyLookupSearchResultHarness.with(filters: SkyLookupSearchResultHarnessFilters): HarnessPredicate<SkyLookupSearchResultHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyLookupSearchResultHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyLookupSearchResultHarnessFilters`

#### Returns

`HarnessPredicate<SkyLookupSearchResultHarness>`

 SkyLookupSearchResultHarnessFilters
------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyLookupSearchResultHarness` instances.

    interface SkyLookupSearchResultHarnessFilters {
      text?: string | RegExp;
    }

### Properties

#### `text?: string | RegExp`

Only find instances whose content matches the given value.

 SkyLookupSelectionHarness
--------------------------

Type: Class

`import { SkyLookupSelectionHarness } from '@skyux/lookup/testing';`

Harness for interacting with a multiselect lookup selection in tests.

### Methods

#### `dismiss(): Promise<void>`

Dismisses the token.

#### Returns

`Promise<void>`

#### `getText(): Promise<string>`

Returns the text content of the token.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the token is disabled.

#### Returns

`Promise<boolean>`

#### `isDismissible(): Promise<boolean>`

Whether the token is dismissible.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the token is focused.

#### Returns

`Promise<boolean>`

#### `select(): Promise<void>`

Selects the token.

#### Returns

`Promise<void>`

#### `SkyLookupSelectionHarness.with(filters: SkyTokenHarnessFilters): HarnessPredicate<SkyTokenHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTokenHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTokenHarnessFilters`

#### Returns

`HarnessPredicate<SkyTokenHarness>`

 SkyLookupShowMorePickerHarness
-------------------------------

Type: Class

`import { SkyLookupShowMorePickerHarness } from '@skyux/lookup/testing';`

Harness for interacting with a lookup's "Show more" picker in tests.

### Methods

#### `cancel(): Promise<void>`

Closes the picker without saving any selections made.

#### Returns

`Promise<void>`

#### `clearAll(): Promise<void>`

Clears all selections made.

#### Returns

`Promise<void>`

#### `clearSearchText(): Promise<void>`

Clears the text of the search input.

#### Returns

`Promise<void>`

#### `clickAddButton(): Promise<void>`

Clicks the add button.

#### Returns

`Promise<void>`

#### `enterSearchText(value: string): Promise<void>`

Enters text into the search input and performs a search.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

#### `getClearAllButtonAriaLabel(): Promise<null | string>`

Gets the clear all button's aria-label.

#### Returns

`Promise<null | string>`

#### `getOnlyShowSelectedAriaLabel(): Promise<null | string>`

Gets the "Only show selected" checkbox's aria-label

#### Returns

`Promise<null | string>`

#### `getSaveButtonAriaLabel(): Promise<null | string>`

Gets the save button's aria-label.

#### Returns

`Promise<null | string>`

#### `getSearchAriaLabel(): Promise<null | string>`

Gets the search input's aria-label.

#### Returns

`Promise<null | string>`

#### `getSearchResult(filter: SkySelectionModalSearchResultHarnessFilters): Promise<SkySelectionModalSearchResultHarness>`

Gets a specific search result based on the filter criteria.

#### Parameters

##### `filter: SkySelectionModalSearchResultHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkySelectionModalSearchResultHarness>`

#### `getSearchResults(filters?: SkyLookupShowMorePickerSearchResultHarnessFilters): Promise<SkyLookupShowMorePickerSearchResultHarness[]>`

Gets a list of search results.

#### Parameters

##### `filters?: SkyLookupShowMorePickerSearchResultHarnessFilters`

#### Returns

`Promise<SkyLookupShowMorePickerSearchResultHarness[]>`

#### `getSelectAllButtonAriaLabel(): Promise<null | string>`

Gets the select all button's aria-label.

#### Returns

`Promise<null | string>`

#### `hasAddButton(): Promise<boolean>`

Whether the selection modal is configured to show the add button.

#### Returns

`Promise<boolean>`

#### `isMultiselect(): Promise<boolean>`

Whether the selection modal is configured to allow multiple selections.

#### Returns

`Promise<boolean>`

#### `loadMore(): Promise<void>`

Loads more results in the picker.

#### Returns

`Promise<void>`

#### `saveAndClose(): Promise<void>`

Saves any selections made and closes the modal.

#### Returns

`Promise<void>`

#### `selectAll(): Promise<void>`

Selects all search results.

#### Returns

`Promise<void>`

#### `selectSearchResult(filters?: SkyLookupShowMorePickerSearchResultHarnessFilters): Promise<void>`

Selects multiple search results based on a set of criteria.

#### Parameters

##### `filters?: SkyLookupShowMorePickerSearchResultHarnessFilters`

#### Returns

`Promise<void>`

#### `SkyLookupShowMorePickerHarness.with(filters: SkyLookupShowMorePickerHarnessFilters): HarnessPredicate<SkyLookupShowMorePickerHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyLookupShowMorePickerHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyLookupShowMorePickerHarnessFilters`

#### Returns

`HarnessPredicate<SkyLookupShowMorePickerHarness>`

 SkyLookupShowMorePickerHarnessFilters
--------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyLookupShowMorePickerHarness` instances.

    interface SkyLookupShowMorePickerHarnessFilters {}

 SkyLookupShowMorePickerSearchResultHarness
-------------------------------------------

Type: Class

`import { SkyLookupShowMorePickerSearchResultHarness } from '@skyux/lookup/testing';`

Harness for interacting with a lookup's "Show more" picker search results in tests.

### Methods

#### `click(): Promise<void>`

Clicks on the repeater item.

#### Returns

`Promise<void>`

#### `collapse(): Promise<void>`

Collapses the repeater item, or does nothing if already collapsed.

#### Returns

`Promise<void>`

#### `deselect(): Promise<void>`

Deselects the repeater item.

#### Returns

`Promise<void>`

#### `expand(): Promise<void>`

Expands the repeater item, or does nothing if already expanded.

#### Returns

`Promise<void>`

#### `getContentText(): Promise<string>`

Gets the text of the repeater item content.

#### Returns

`Promise<string>`

#### `getContextMenuDropdown(filters?: SkyDropdownHarnessFilters): Promise<SkyDropdownHarness>`

Gets a harness for the dropdown inside the context menu.

#### Parameters

##### `filters?: SkyDropdownHarnessFilters`

#### Returns

`Promise<SkyDropdownHarness>`

#### `getInlineForm(): Promise<SkyInlineFormHarness>`

Gets the inline form harness.

#### Returns

`Promise<SkyInlineFormHarness>`

#### `getItemName(): Promise<null | string>`

Gets the item name.

#### Returns

`Promise<null | string>`

#### `getTitleText(): Promise<string>`

Gets the text of the repeater item title.

#### Returns

`Promise<string>`

#### `isCollapsible(): Promise<boolean>`

Whether the repeater item is collapsible.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether a selectable repeater item is disabled.

#### Returns

`Promise<boolean>`

#### `isExpanded(): Promise<boolean>`

Whether the repeater item is expanded, or throws an error informing of the lack of collapsibility.

#### Returns

`Promise<boolean>`

#### `isReorderable(): Promise<boolean>`

Whether the repeater item is reorderable.

#### Returns

`Promise<boolean>`

#### `isSelectable(): Promise<boolean>`

Whether a repeater item has selection enabled.

#### Returns

`Promise<boolean>`

#### `isSelected(): Promise<boolean>`

Whether a selectable repeater item is selected. Throws an error if the item is not selectable.

#### Returns

`Promise<boolean>`

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

Selects the repeater item.

#### Returns

`Promise<void>`

#### `sendToTop(): Promise<void>`

Moves the repeater item to the top of the list

#### Returns

`Promise<void>`

#### `SkyLookupShowMorePickerSearchResultHarness.with(filters: SkyRepeaterItemHarnessFilters): HarnessPredicate<SkyRepeaterItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyRepeaterItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyRepeaterItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyRepeaterItemHarness>`

 SkyLookupShowMorePickerSearchResultHarnessFilters
--------------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyLookupShowMorePickerSearchResultHarness` instances.

    interface SkyLookupShowMorePickerSearchResultHarnessFilters {
      contentText?: string | RegExp;
      dataSkyId?: string | RegExp;
    }

### Properties

#### `contentText?: string | RegExp`

Only find instances whose content matches the given value.

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

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