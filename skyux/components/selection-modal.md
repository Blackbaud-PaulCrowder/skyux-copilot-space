                  

 Selection modal
===============

Selection modals let users select from a list of options. The [lookup component](/skyux/components/lookup.md) is preferable for most selection tasks, but selection modals are useful when users need to take immediate action on selections.

 Usage
------

### Use when

Use selection modals when users need to select options from a long or unpredictable list and then immediately interact with the selections. If users only need to select options, use the [lookup component](/skyux/components/lookup.md) instead.

Use buttons to open selection modals. After users select options, display selections in a format or pattern that supports the next interaction.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/selection-modal/selection-modal-usage-1.70e74c7217cf53412de714bf8a3efcac.png)

Do use selection modals when users select options and then immediately interact with the selections.

### Don't use when

Don't use selection modals when users only need to select options. Instead, use [lookup fields](/skyux/components/lookup.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/selection-modal/selection-modal-usage-3.5730deda4b2404d79ab27a78d7574b71.png)

Don't use selection modals for basic selection tasks.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/selection-modal/selection-modal-usage-4.01c4abf55f24dce1b390d37ceddb530a.png)

Do use lookup fields for basic selection tasks.

Don't use selection modals for five or fewer options. Instead, use [checkboxes](/skyux/components/checkbox.md) or [radio buttons](/skyux/components/radio.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/selection-modal/selection-modal-usage-5.d10074a1b9a7b77338b5b370732b4fcc.png)

Don't use selection modals for a few options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/radio-button/radio-button-usage-2.69522665a167662e83baec4d293f780b.png)

Do use checkboxes or radio buttons for small sets of options.

Don't use selection modals when a list of options requires a format other than a simple selectable [repeater](/skyux/components/repeater.md). If a list requires a different format, such as a custom repeater template or a [tree view](/skyux/components/angular-tree.md), or if users require filters to find and select options, create a custom modal with the appropriate features.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/lookup/lookup-options-4.3c3c9a2ee3ec8628d6eba932c7beafda.png)

Do use other formats, such as custom modals with tree views, instead of selection modals when lists of options require filtering or special list formats.

 Anatomy
--------

1

Modal

2

Search

3

Multiselect toolbar (multiselect only)

4

Unselected option

5

Selected option

6

New button (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/selection-modal/selection-modal-anatomy.9928b310687d9da55c02a7a5dec7710f.png)

 Options
--------

### Single-select and multiselect

Use single-select mode to limit users to a single option, and use multiselect mode to let them select multiple options.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/selection-modal/selection-modal-single.2bb24d37cc132acc591fc773270cef37.png)

Use single-select mode when users can only select one option.

### Button to create options

If users may need to add options to the list, include a button to start the workflow to create options. After users create options, they are selected in the selection modal.

 Behavior and states
--------------------

### List scrolling

Long lists inside selection modals use [infinite scroll](/skyux/components/infinite-scroll.md).

### Presentation of selected options

Selection modals don't provide a default presentation of selected options. When users close selection modals, present the selected options in a format that matches the needs of the scenario.

 Content
--------

### Modal title text

Use the following format for selection modal titles, and use plural objects when using multiselect:

Select <direct object>

### Modal footer buttons

Use **Select** as the standard label for the primary button. Use **Cancel** as the standard label for the link button.

 Related information
--------------------

### Components

*   [Checkbox](/skyux/components/checkbox.md)
*   [Lookup](/skyux/components/lookup.md)
*   [Radio button](/skyux/components/radio.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/lookup`[View in NPM](https://www.npmjs.com/package/@skyux/lookup) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lookup/src/lib/modules/selection-modal/selection-modal.service.ts#L22) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lookup`Copy None found.

 SkySelectionModalService
-------------------------

Type: Service

Displays a modal for selecting one or more values.

### Methods

#### `open(args: SkySelectionModalOpenArgs): SkySelectionModalInstance`

Opens the selection modal.

#### Parameters

##### `args: SkySelectionModalOpenArgs`

Parameters for the selection modal.

#### Returns

`SkySelectionModalInstance`

 SkySelectionModalInstance
--------------------------

Type: Class

Represents an instance of a selection modal.

### Properties

#### `closed: Observable<SkySelectionModalCloseArgs>`

An event that the selection modal instance emits when it closes. It emits a `SkySelectionModalCloseArgs` object with a `selectedItems` property that includes items selected by users on close or save and a `reason` property that indicates whether the selection modal was saved or closed without saving. The `reason` property accepts `"cancel"`, `"close"`, and `"save"`.

 SkyLookupSelectModeType
------------------------

Type: Type alias

    type SkyLookupSelectModeType = "single" | "multiple"

 SkySelectionModalAddCallbackArgs
---------------------------------

Type: Interface

Specifies the information for the callback used when adding a new item to a selection modal instance.

    interface SkySelectionModalAddCallbackArgs {
      item: any;
    }

### Properties

#### `item: any`

The new item which has been added to the data. This item will be automatically selected.

 SkySelectionModalAddClickEventArgs
-----------------------------------

Type: Interface

Specifies a callback function for the consumer to use to notify the selection modal that a new item has been added.

    interface SkySelectionModalAddClickEventArgs {
      itemAdded: (args: SkySelectionModalAddCallbackArgs) => void;
    }

### Properties

#### `itemAdded: (args: SkySelectionModalAddCallbackArgs) => void`

A callback function for the consumer to use to notify the selection modal that a new item has been added.

 SkySelectionModalCloseArgs
---------------------------

Type: Interface

The result from the selection modal.

    interface SkySelectionModalCloseArgs {
      reason: "cancel" | "close" | "save";
      selectedItems?: unknown[];
    }

### Properties

#### `reason: "cancel" | "close" | "save"`

Indicates why the selection modal was closed.

#### `selectedItems?: unknown[]`

A collection of items the user selected. This property is only set when the `result` property is set to `save`.

 SkySelectionModalOpenArgs
--------------------------

Type: Interface

Parameters for the selection modal.

    interface SkySelectionModalOpenArgs {
      addClick?: (args: SkySelectionModalAddClickEventArgs) => void;
      descriptorProperty: string;
      idProperty: string;
      initialSearch?: string;
      itemTemplate?: TemplateRef<unknown>;
      searchAsync: (args: SkySelectionModalSearchArgs) => undefined | Observable<SkySelectionModalSearchResult>;
      selectionDescriptor?: string;
      selectMode: SkyLookupSelectModeType;
      showAddButton?: boolean;
      title?: string;
      value?: unknown[];
      wrapperClass?: string;
    }

### Properties

#### `addClick?: (args: SkySelectionModalAddClickEventArgs) => void`

Called when users select the button to add options to the list.

#### `descriptorProperty: string`

Specifies an object property to display in the text input after users select an item in the dropdown list.

#### `idProperty: string`

An object property that represents the object's unique identifier.

#### `initialSearch?: string`

The initial search text.

#### `itemTemplate?: TemplateRef<unknown>`

The template to format each option in the search results. The selection modal injects values into the template as `item` variables that reference all the object properties of the options. If you do not specify a template, the item's descriptor property value is displayed.

#### `searchAsync: (args: SkySelectionModalSearchArgs) => undefined | Observable<SkySelectionModalSearchResult>`

Called when users enter new search information and returns results via an observable.

#### `selectionDescriptor?: string`

A descriptor for the item or items being selected. Use a plural term when `selectMode` is set to `multiple`; otherwise, use a singular term. The descriptor helps set the selection modal's `aria-label` attributes for the multiselect toolbar controls, the search input, and the save button to provide text equivalents for screen readers [to support accessibility](/skyux/components/checkbox#accessibility.md). For example, when the descriptor is "constituents," the search input's `aria-label` is "Search constituents." For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `selectMode: SkyLookupSelectModeType`

Specifies whether users can select one option or multiple options.

#### `showAddButton?: boolean`

Whether to display a button that lets users add options to the list.

#### `title?: string`

Warning: **Deprecated.** Use the `selectionDescriptor` input to give context to the title and accessibility labels instead.

The title for the selection modal.

#### `value?: unknown[]`

The initial value for the selection modal.

#### `wrapperClass?: string`

The CSS class to add to the modal, such as `ag-custom-component-popup` for using a modal as part of a cell editor in Data Entry Grid.

 SkySelectionModalResult
------------------------

Type: Interface

The result from the selection modal.

    interface SkySelectionModalResult {
      result: "cancel" | "save";
      selectedItems?: unknown[];
    }

### Properties

#### `result: "cancel" | "save"`

Indicates whether the user saved or canceled the modal.

#### `selectedItems?: unknown[]`

A collection of items the user selected. This property is only set when the `result` property is set to `save`.

 SkySelectionModalSearchArgs
----------------------------

Type: Interface

Arguments passed when an asynchronous search is executed from the selection modal service.

    interface SkySelectionModalSearchArgs {
      continuationData?: unknown;
      offset: number;
      searchText: string;
    }

### Properties

#### `continuationData?: unknown`

A continuation token which can be set and then will be passed back with any future searches. This is helpful for applications which utilize a token instead of an offset when fetching data.

#### `offset: number`

The offset index of the first result to return. When search is executed as a result of an infinite scroll event, for example, offset will be set to the number of items already displayed.

#### `searchText: string`

The search text entered by the user.

 SkySelectionModalSearchResult
------------------------------

Type: Interface

The result of searching for items to display in a selection modal.

    interface SkySelectionModalSearchResult {
      continuationData?: unknown;
      hasMore?: boolean;
      items: unknown[];
      totalCount: number;
    }

### Properties

#### `continuationData?: unknown`

Data provided on "load more" search result requests. Use this property for information such as a continuation token for paged database queries.

#### `hasMore?: boolean`

Indicates whether there are more results that match the search criteria.

#### `items: unknown[]`

A list of items matching the search criteria. When there are more items that match the search criteria, set the `hasMore` property to `true` more records can be lazy-loaded as the user scrolls through the search results.

#### `totalCount: number`

The total number of records that match the search criteria, including items not returned in the current list of items.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkySelectionModalHarness
-------------------------

Type: Class

`import { SkySelectionModalHarness } from '@skyux/lookup/testing';`

Harness for interacting with a selection modal in tests.

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

#### `getSearchResults(filters?: SkySelectionModalSearchResultHarnessFilters): Promise<SkySelectionModalSearchResultHarness[]>`

Gets an array of search results based on the filter criteria. If no filter is provided, returns all search results.

#### Parameters

##### `filters?: SkySelectionModalSearchResultHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkySelectionModalSearchResultHarness[]>`

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

#### `selectSearchResult(filters?: SkySelectionModalSearchResultHarnessFilters): Promise<void>`

Selects multiple search results based on a set of criteria.

#### Parameters

##### `filters?: SkySelectionModalSearchResultHarnessFilters`

#### Returns

`Promise<void>`

 SkySelectionModalSearchResultHarness
-------------------------------------

Type: Class

`import { SkySelectionModalSearchResultHarness } from '@skyux/lookup/testing';`

Harness for interacting with a selection modal's search results in tests.

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

#### `SkySelectionModalSearchResultHarness.with(filters: SkyRepeaterItemHarnessFilters): HarnessPredicate<SkyRepeaterItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyRepeaterItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyRepeaterItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyRepeaterItemHarness>`

 SkySelectionModalSearchResultHarnessFilters
--------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkySelectionModalSearchResultHarness` instances.

    interface SkySelectionModalSearchResultHarnessFilters {
      contentText?: string | RegExp;
      dataSkyId?: string | RegExp;
    }

### Properties

#### `contentText?: string | RegExp`

Only find instances whose content matches the given value.

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.