                    

 Data manager
============

The data manager component and service manage the exploration of a data set across any number of SKY UX, third party, or custom views through state observables and data set- and view-level configs.

 Installation
-------------

NPM package

`@skyux/data-manager`[View in NPM](https://www.npmjs.com/package/@skyux/data-manager) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/data-manager/src/lib/modules/data-manager/data-manager.module.ts#L33) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/data-manager`Copy None found.

 Overview
---------

The data manager is responsible for **the options applied to the data** but not the data itself. The data manager renders the toolbar and tracks the options selected in the toolbar, but the consuming SPA provides the views that display the data and applies filters and sorts to the data. This provides flexibility and control over the views and data loading while handling some repetitive tasks, such as arranging items in the toolbar and applying sticky settings.

The core pieces of the data manager are the config objects (SkyDataManagerConfig and SkyDataViewConfig), the states (SkyDataManagerState and the SkyDataViewStates it contains), and SkyDataManagerService. The data manager renders a toolbar with options based on the overall data manager config and the individual view configs. When changes are made in the toolbar, the data state is updated. These updates are made available through observables on the data manager service.

The data manager has one configuration object that includes options that apply across all views, and one configuration object per view that allows each view to be fine-tuned.

Similarly, the state includes information that could apply across all views or to a specific view. Options that dictate **what** data is displayed are in SkyDataManagerState because the data that is displayed should be the same across views. Options that dictate **how** data is displayed, such as what columns to display, are in SkyDataViewState objects. For example, if you display constituents in a grid view and a map view, the same constituents should be in both views, but the view determines the columns to display and whether to display the sort button.

 Usage with data entry grid
---------------------------

If you use a data entry grid within a data manager component, the `skyAgGridDataManagerAdapter` directive can manage some standard interactions between the data entry grid and the data manager service. Add the directive `skyAgGridDataManagerAdapter` to the `sky-data-view` element that contains the data entry grid to initialize properties from the data state and keep the data entry grid in sync with the data state. When the data entry grid changes, the data state is updated, and when the data state changes, the data entry grid responds to the changes. The directive manages:

*   column visibility, order, and width
*   selected rows
*   active sort state when selected by column header

Other properties of the data state, such as filters and applying the sort, still need to be implemented for each use.

 SkyDataManagerModule
---------------------

Type: Module

`import { SkyDataManagerModule } from '@skyux/data-manager';`

 SkyDataManagerComponent
------------------------

Type: Component

Selector: `sky-data-manager`

The top-level data manager component. Provide `SkyDataManagerService` at this level.

### Inputs

#### `dock: InputSignal<SkyDataManagerDockType>`

How the data manager docks to the page. Use `fill` to dock the data manager to the container's size where the container is a `sky-page` component with its `layout` set to `fit`, or where the container is another element with a `relative` or `absolute` position and a fixed size. `sky-data-manager-toolbar` will be docked to the top of all other content.

Default: `"none"`

 SkyDataManagerService
----------------------

Type: Service

The data manager service provides ways for data views, toolbar items, and more to stay up to date with the active view ID, data manager config, registered views and their configs, and data state. There are methods to get current values, update values, and get subscriptions to the changing values.

Provide this service at the component level for each instance of a data manager. Do not provide it at the module level or in `app-extras`. This allows multiple data managers to be used and self-contained.

### Methods

#### `getActiveViewIdUpdates(): Observable<string>`

Returns an observable of the active view ID that views and other data manager entities can subscribe to.

#### Returns

`Observable<string>`

#### `getCurrentDataManagerConfig(): SkyDataManagerConfig`

Returns the current `SkyDataManagerConfig`.

#### Returns

`SkyDataManagerConfig`

#### `getDataManagerConfigUpdates(): Observable<SkyDataManagerConfig>`

Returns an observable of data manager config changes that views and other data manager entities can subscribe to.

#### Returns

`Observable<SkyDataManagerConfig>`

#### `getDataStateUpdates(sourceId: string, updateFilter?: SkyDataManagerStateUpdateFilterArgs): Observable<SkyDataManagerState>`

Returns an observable of data state changes that views and other data manager entities can subscribe to. It excludes updates originating from the provided source. This allows subscribers to only respond to changes they did not create and helps prevent infinite loops of updates and responses.

#### Parameters

##### `sourceId: string`

The ID of the entity subscribing to data state updates. This can be any value you choose but should be unique within the data manager instance and should also be used when that entity updates the state.

##### `updateFilter?: SkyDataManagerStateUpdateFilterArgs`

#### Returns

`Observable<SkyDataManagerState>`

#### `getDataSummaryUpdates(sourceId: string): Observable<SkyDataManagerSummary>`

Returns an observable of data summary changes that views and other data manager entities can subscribe to. It excludes updates originating from the provided source. This allows subscribers to only respond to changes they did not create and helps prevent infinite loops of updates and responses.

#### Parameters

##### `sourceId: string`

The ID of the entity subscribing to data summary updates. This can be any value you choose but should be unique within the data manager instance and should also be used when that entity updates the summary.

#### Returns

`Observable<SkyDataManagerSummary>`

#### `getDataViewsUpdates(): Observable<SkyDataViewConfig[]>`

Returns an observable of data view config changes that views and other data manager entities can subscribe to.

#### Returns

`Observable<SkyDataViewConfig[]>`

#### `getViewById(viewId: string): SkyDataViewConfig | undefined`

Returns the `SkyDataViewConfig` for the given view ID.

#### Parameters

##### `viewId: string`

The ID of the view config to get.

#### Returns

`SkyDataViewConfig | undefined`

#### `initDataManager(args: SkyDataManagerInitArgs): void`

Initializes the data manager with the given settings and sets `isInitialized` to `true`. This must be called for the data manager to render.

#### Parameters

##### `args: SkyDataManagerInitArgs`

The initial active view ID, data manager config, and state to use for the data manager. If a settings key is provided, it checks for a saved data state in the SKY UI config service before using the default data state and saves any state changes to the service.

#### Returns

`void`

#### `initDataView(viewConfig: SkyDataViewConfig): void`

Initializes a view within the data manager. This must be called for each view for the views to appear within the data manager.

#### Parameters

##### `viewConfig: SkyDataViewConfig`

The [SkyDataViewConfig](/skyux/components/data-manager?docs-active-tab=development#interface_sky-data-view-config.md) settings for the view being registered.

#### Returns

`void`

#### `updateActiveViewId(id: string): void`

Updates the active view ID. The data manager changes the displayed view.

#### Parameters

##### `id: string`

The new active view ID.

#### Returns

`void`

#### `updateDataManagerConfig(value: SkyDataManagerConfig): void`

Updates the data manager config and emits a new value to entities subscribed to data config changes.

#### Parameters

##### `value: SkyDataManagerConfig`

The new `SkyDataManagerConfig` value.

#### Returns

`void`

#### `updateDataState(state: SkyDataManagerState, sourceId: string): void`

Updates the data state and emits a new value to entities subscribed to data state changes.

#### Parameters

##### `state: SkyDataManagerState`

The new `SkyDataManagerState` value.

##### `sourceId: string`

The ID of the entity updating the state. This can be any value you choose, but should be unique within the data manager instance and should also be used when that entity subscribes to state changes from `getDataStateUpdates`.

#### Returns

`void`

#### `updateDataSummary(summary: SkyDataManagerSummary, sourceId: string): void`

Updates the data summary and emits a new value to entities subscribed to data summary changes.

#### Parameters

##### `summary: SkyDataManagerSummary`

The new `SkyDataManagerSummary` value.

##### `sourceId: string`

The ID of the entity updating the summary. This can be any value you choose, but should be unique within the data manager instance and should also be used when that entity subscribes to summary changes from `getDataSummaryUpdates`.

#### Returns

`void`

#### `updateViewConfig(view: SkyDataViewConfig): void`

Updates the given view config. The registered view with the same ID is updated to the provided config, so include all properties regardless of whether they changed. If the view was not initialized already, no update happens.

#### Parameters

##### `view: SkyDataViewConfig`

The new `SkyDataViewConfig` containing all properties.

#### Returns

`void`

 SkyDataManagerToolbarComponent
-------------------------------

Type: Component

Selector: `sky-data-manager-toolbar`

Renders a `sky-toolbar` with the contents specified by the active view's `SkyDataViewConfig` and the `SkyDataManagerToolbarLeftItemComponent`, `SkyDataManagerToolbarRightItemComponent`, and `SkyDataManagerToolbarSectionComponent` wrappers.

 SkyDataManagerToolbarSectionComponent
--------------------------------------

Type: Component

Selector: `sky-data-manager-toolbar-section`

A wrapper for items to be rendered in `SkyDataManagerToolbarComponent`. The contents are rendered in an additional toolbar row beneath the primary toolbar and above the multiselect toolbar (if present).

 SkyDataManagerToolbarPrimaryItemComponent
------------------------------------------

Type: Component

Selector: `sky-data-manager-toolbar-primary-item`

A wrapper for an item to be rendered in `SkyDataManagerToolbarComponent`. The contents are rendered as the first items in the toolbar and should be standard actions. Each item should be wrapped in its own `sky-data-manager-toolbar-primary-item`. The items render in the order they are in in the template.

 SkyDataManagerToolbarLeftItemComponent
---------------------------------------

Type: Component

Selector: `sky-data-manager-toolbar-left-item`

A wrapper for an item to be rendered in `SkyDataManagerToolbarComponent`. The contents are rendered after the standard toolbar actions and before the search box. Each item should be wrapped in its own `sky-data-manager-toolbar-left-item`. The items render in the order they are in in the template.

 SkyDataManagerToolbarRightItemComponent
----------------------------------------

Type: Component

Selector: `sky-data-manager-toolbar-right-item`

A wrapper for an item to be rendered in `SkyDataManagerToolbarComponent`. The contents are rendered in `sky-toolbar-view-actions` on the right side of the toolbar and before the view switcher icons (if present). Each item should be wrapped in its own `sky-data-manager-toolbar-right-item`. The items render in the order they are in in the template.

 SkyDataViewComponent
---------------------

Type: Component

Selector: `sky-data-view`

A data view is rendered within a data manager component. It can subscribe to data state changes from `SkyDataManagerService` and apply the filters, search text, and more to the data it displays.

### Inputs

#### `viewId: string | undefined`

Required

The configuration for the view. See the `SkyDataViewConfig` interface.

 SkyDataViewConfig
------------------

Type: Interface

The data view config contains settings that apply to the specific view, such as column picker options and the buttons to display in the toolbar.

    interface SkyDataViewConfig {
      additionalOptions?: Record<string, unknown>;
      columnOptions?: SkyDataManagerColumnPickerOption[];
      columnPickerEnabled?: boolean;
      columnPickerSortStrategy?: SkyDataManagerColumnPickerSortStrategy;
      filterButtonEnabled?: boolean;
      iconName?: string;
      id: string;
      multiselectToolbarEnabled?: boolean;
      name: string;
      onClearAllClick?: () => void;
      onSelectAllClick?: () => void;
      searchEnabled?: boolean;
      searchExpandMode?: string;
      searchHighlightEnabled?: boolean;
      searchPlaceholderText?: string;
      showFilterButtonText?: boolean;
      showSortButtonText?: boolean;
      sortEnabled?: boolean;
    }

### Properties

#### `additionalOptions?: Record<string, unknown>`

An untyped property that can track any view config information relevant to a data view that the existing options do not include.

#### `columnOptions?: SkyDataManagerColumnPickerOption[]`

The column data to pass to the column picker. Columns that are always displayed should be passed in addition to the optional columns. See [SkyDataManagerColumnPickerOption](/skyux/components/data-manager?docs-active-tab=development#interface_sky-data-manager-column-picker-option.md).

#### `columnPickerEnabled?: boolean`

Whether to display the column picker button for this view.

#### `columnPickerSortStrategy?: SkyDataManagerColumnPickerSortStrategy`

The strategy used to sort the options in the column picker. If no strategy is provided the columns will be sorted by selected then alphabetical.

#### `filterButtonEnabled?: boolean`

Whether to display the filter button for this view.

#### `iconName?: string`

The name of the Blackbaud SVG icon to display for this view in the view switcher. Required if you have more than one view.

#### `id: string`

The unique ID for this view.

#### `multiselectToolbarEnabled?: boolean`

Whether to display the multiselect toolbar for this view.

#### `name: string`

The name of the view. This is used in the ARIA label for the view switcher.

#### `onClearAllClick?: () => void`

The function called when a user selects the "Clear all" button on the multi-select toolbar. Update your displayed data to indicate it is not selected in this function.

#### `onSelectAllClick?: () => void`

The function called when a user selects the "Select all" button on the multi-select toolbar. Update your displayed data to indicate it is selected in this function.

#### `searchEnabled?: boolean`

Whether to display the search box for this view.

#### `searchExpandMode?: string`

Sets the `expandMode` property on the search box for this view. See the <a href="[https://developer.blackbaud.com/skyux/components/search">search](/skyux/components/search%22>search.md) component</a> for valid options and the default value.

#### `searchHighlightEnabled?: boolean`

Highlights text that matches the search text using the text highlight directive.

#### `searchPlaceholderText?: string`

Placeholder text to display in the search input until users enter search criteria. See the <a href="[https://developer.blackbaud.com/skyux/components/search">search](/skyux/components/search%22>search.md) component</a> for the default value.

#### `showFilterButtonText?: boolean`

Whether to include the "Filter" text on the displayed filter button for this view. If it is not set, no text appears.

#### `showSortButtonText?: boolean`

Whether to include the "Sort" text on the displayed sort button for this view. If it is not set, no text appears.

#### `sortEnabled?: boolean`

Whether to display the sort button in this view.

 SkyDataViewColumnWidths
------------------------

Type: Interface

    interface SkyDataViewColumnWidths {
      sm: Record<string, number>;
      xs: Record<string, number>;
    }

### Properties

#### `sm: Record<string, number>`

A map of columnIds to column widths at the sm or larger breakpoint size.

#### `xs: Record<string, number>`

A map of columnIds to column widths at the xs breakpoint size.

 SkyDataViewState
-----------------

Type: Class

Provides options for defining how data is displayed, such as which columns appear.

### Properties

#### `additionalData: any`

An untyped property that tracks any view-specific state information that is relevant to a data manager but that existing properties do not cover.

#### `columnIds: string[]`

The IDs of the columns able to be displayed for column-based views. This property is required when utilizing a grid-based view, a column picker, or both.

Default: `[]`

#### `columnWidths: SkyDataViewColumnWidths`

The widths of columns in column-based views for xs and sm+ breakpoints. If using sticky settings, the widths a user sets will be persisted.

#### `displayedColumnIds: string[]`

The IDs of the columns displayed for column-based views.

Default: `[]`

#### `viewId: string`

The ID of this view.

### Methods

#### `getViewStateOptions(): SkyDataViewStateOptions`

Returns the `SkyDataViewStateOptions` for the current view.

#### Returns

`SkyDataViewStateOptions`

 SkyDataViewStateOptions
------------------------

Type: Interface

    interface SkyDataViewStateOptions {
      additionalData?: any;
      columnIds?: string[];
      columnWidths?: SkyDataViewColumnWidths;
      displayedColumnIds?: string[];
      viewId: string;
    }

### Properties

#### `additionalData?: any`

An untyped property that tracks any view-specific state information that is relevant to a data manager but that existing properties do not cover.

#### `columnIds?: string[]`

The IDs of the columns able to be displayed for column-based views. This property is required when utilizing a grid-based view, a column picker, or both.

#### `columnWidths?: SkyDataViewColumnWidths`

The widths of columns in column-based views for xs and sm+ breakpoints. If using sticky settings, the widths a user sets will be persisted.

#### `displayedColumnIds?: string[]`

The IDs of the columns displayed for column-based views.

#### `viewId: string`

The ID of this view.

 SkyDataManagerConfig
---------------------

Type: Interface

The data manager config contains settings that apply to the data manager across all views, such as the sort and filter settings.

    interface SkyDataManagerConfig {
      additionalOptions?: any;
      filterModalComponent?: any;
      listDescriptor?: string;
      sortOptions?: SkyDataManagerSortOption[];
    }

### Properties

#### `additionalOptions?: any`

An untyped property that can track any config information relevant to a data manager that existing options do not include.

#### `filterModalComponent?: any`

The modal component to launch when the filter button is selected. The same filter options are used for all views, but views can use `SkyDataViewConfig` to indicate whether to display the filter button. The modal receives the `filterData` in the data state as context.

#### `listDescriptor?: string`

A descriptor for the data that the data manager manipulates. Use a plural term. The descriptor helps set the data manager's `aria-label` attributes for multiselect toolbars, search inputs, sort buttons, and filter buttons to provide text equivalents for screen readers [to support accessibility](/skyux/components/checkbox#accessibility.md). For example, when the descriptor is "constituents," the search input's `aria-label` is "Search constituents." For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `sortOptions?: SkyDataManagerSortOption[]`

The sort options displayed in the sort dropdown. The same sort options are used for all views, but views can use `SkyDataViewConfig` to indicate whether to display the sort button.

 SkyDataManagerDockType
-----------------------

Type: Type alias

    type SkyDataManagerDockType = "none" | "fill"

 SkyDataManagerFilterData
-------------------------

Type: Interface

    interface SkyDataManagerFilterData {
      filters?: any;
      filtersApplied?: boolean;
    }

### Properties

#### `filters?: any`

The filter data used in the data manager. You may use any filter model that works for your data set and models. See the demo for an example.

#### `filtersApplied?: boolean`

Whether any filters are applied.

 SkyDataManagerInitArgs
-----------------------

Type: Interface

    interface SkyDataManagerInitArgs {
      activeViewId: string;
      dataManagerConfig: SkyDataManagerConfig;
      defaultDataState: SkyDataManagerState;
      settingsKey?: string;
    }

### Properties

#### `activeViewId: string`

The initial active view's ID.

#### `dataManagerConfig: SkyDataManagerConfig`

The initial configuration for the data manager. See the [SkyDataManagerConfig](/skyux/components/data-manager?docs-active-tab=development#interface_sky-data-manager-config.md) interface.

#### `defaultDataState: SkyDataManagerState`

The data state used if no settings key is provided or if no data state is saved in the SKY UI config service for the user. See the [SkyDataManagerState](/skyux/components/data-manager?docs-active-tab=development#class_sky-data-manager-state.md) interface.

#### `settingsKey?: string`

The unique key for the UI Config Service to retrieve stored settings from a database. The UI Config Service saves configuration settings for users to preserve the current data state. For more information about the UI Config Service, see [the sticky settings documentation](/skyux/learn/develop/sticky-settings.md).

 SkyDataManagerSortOption
-------------------------

Type: Interface

    interface SkyDataManagerSortOption {
      descending: boolean;
      id: string;
      label: string;
      propertyName: string;
    }

### Properties

#### `descending: boolean`

Whether to apply the sort in descending order.

#### `id: string`

An ID for the sort option.

#### `label: string`

The label to display in the sort dropdown.

#### `propertyName: string`

The data property to sort by.

 SkyDataManagerState
--------------------

Type: Class

Provides options that control which data to display.

### Properties

#### `activeSortOption: SkyDataManagerSortOption | undefined`

The selected [SkyDataManagerSortOption](/skyux/components/data-manager?docs-active-tab=development#interface_sky-data-manager-sort-option.md) to apply.

#### `additionalData: any`

An untyped property that tracks any state information that's relevant to a data manager but that the existing properties do not cover.

#### `filterData: SkyDataManagerFilterData | undefined`

The state of the filters.

#### `onlyShowSelected: boolean | undefined`

Whether to display only the selected rows or objects. The multiselect toolbar uses this property.

#### `searchText: string | undefined`

The search text to apply.

#### `selectedIds: string[] | undefined`

The currently selected rows or objects.

#### `views: SkyDataViewState[]`

The states of the individual views.

Default: `[]`

### Methods

#### `addOrUpdateView(viewId: string, view: SkyDataViewState): SkyDataManagerState`

Adds a `SkyDataViewState` to a view or updates an existing view.

#### Parameters

##### `viewId: string`

The ID for the view.

##### `view: SkyDataViewState`

The `SkyDataViewState` option to add or update.

#### Returns

`SkyDataManagerState`

#### `getStateOptions(): SkyDataManagerStateOptions`

Returns the `SkyDataManagerStateOptions` for the data manager.

#### Returns

`SkyDataManagerStateOptions`

#### `getViewStateById(viewId: string): SkyDataViewState | undefined`

Returns the `SkyDataViewState` for the specified view.

#### Parameters

##### `viewId: string`

The ID for the view.

#### Returns

`SkyDataViewState | undefined`

 SkyDataManagerStateOptions
---------------------------

Type: Interface

    interface SkyDataManagerStateOptions {
      activeSortOption?: SkyDataManagerSortOption;
      additionalData?: any;
      filterData?: SkyDataManagerFilterData;
      onlyShowSelected?: boolean;
      searchText?: string;
      selectedIds?: string[];
      views?: SkyDataViewStateOptions[];
    }

### Properties

#### `activeSortOption?: SkyDataManagerSortOption`

The selected [SkyDataManagerSortOption](/skyux/components/data-manager?docs-active-tab=development#interface_sky-data-manager-sort-option.md) to apply.

#### `additionalData?: any`

An untyped property that tracks any state information that's relevant to a data manager but that the existing properties do not cover.

#### `filterData?: SkyDataManagerFilterData`

The state of the filters.

#### `onlyShowSelected?: boolean`

Whether to display only the selected rows or objects. The multiselect toolbar uses this property.

#### `searchText?: string`

The search text to apply.

#### `selectedIds?: string[]`

The currently selected rows or objects.

#### `views?: SkyDataViewStateOptions[]`

The states of the individual views.

 SkyDataManagerStateUpdateFilterArgs
------------------------------------

Type: Interface

Optional arguments to pass to `getDataStateUpdates`. Provide either a list of properties to filter on OR a custom comparator.

    interface SkyDataManagerStateUpdateFilterArgs {
      comparator?: (state1: SkyDataManagerState, state2: SkyDataManagerState) => boolean;
      properties?: string[];
    }

### Properties

#### `comparator?: (state1: SkyDataManagerState, state2: SkyDataManagerState) => boolean`

A comparator function called to test if the new `SkyDataManagerState` is distinct from the previous.

#### `properties?: string[]`

A list of `SkyDataManagerState` properties to compare to test if the new `SkyDataManagerState` is distinct from the previous. This allows you to subscribe to changes for only the provided properties.

 SkyDataManagerColumnPickerOption
---------------------------------

Type: Interface

The options to display in a view's column picker.

    interface SkyDataManagerColumnPickerOption {
      alwaysDisplayed?: boolean;
      description?: string;
      id: string;
      initialHide?: boolean;
      label: string;
    }

### Properties

#### `alwaysDisplayed?: boolean`

Whether a column is always visible and is not listed as an option in the column picker. For example, a context menu column may always be visible.

#### `description?: string`

The description text rendered beneath the column label in the column picker.

#### `id: string`

The ID of the corresponding column.

#### `initialHide?: boolean`

Initially hide the column when it is added to the grid unless given in the view state's `displayedColumnIds`. When enabled, this column will not be automatically added to a view's state when this column is recognized as being missing from an initial data state or a data state returned via the SKY UI config service.

#### `label: string`

The label to display in the column picker.

 SkyDataManagerColumnPickerSortStrategy
---------------------------------------

Type: Enumeration

These options specify the sorting strategy applied to columns when `columnPickerEnabled` is enabled.

    enum SkyDataManagerColumnPickerSortStrategy {
      None = "none",
      SelectedThenAlphabetical = "selectedThenAlphabetical",
    }

### Properties

#### `SkyDataManagerColumnPickerSortStrategy.None`

No sorting is applied to the columns.

#### `SkyDataManagerColumnPickerSortStrategy.SelectedThenAlphabetical`

If `sortEnabled` is set to `true`, then the selected columns are displayed before the unselected columns. Unselected columns are sorted alphabetically. If `sortEnabled` is set to `false`, then the columns are displayed in the order specified by `columnOptions`.

 SkyDataManagerFilterModalContext
---------------------------------

Type: Class

Sets the state of the filters.

### Properties

#### `filterData: SkyDataManagerFilterData | undefined`

Sets the state of the filters.

 SkyDataManagerSummary
----------------------

Type: Interface

Contains summary details of the data displayed within the data manager.

    interface SkyDataManagerSummary {
      itemsMatching: number;
      totalItems: number;
    }

### Properties

#### `itemsMatching: number`

The total number of items that match the search and filter criteria.

#### `totalItems: number`

The total number of items in the data set.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyDataManagerHarness
----------------------

Type: Class

`import { SkyDataManagerHarness } from '@skyux/data-manager/testing';`

Harness to interact with a data manager toolbar section component in tests.

### Methods

#### `getDockType(): Promise<string>`

Gets the type of dock style on the data manager.

#### Returns

`Promise<string>`

#### `getToolbar(filter?: SkyDataManagerToolbarHarnessFilters): Promise<SkyDataManagerToolbarHarness>`

Gets a harness for a data manager toolbar that meets certain criteria.

#### Parameters

##### `filter?: SkyDataManagerToolbarHarnessFilters`

#### Returns

`Promise<SkyDataManagerToolbarHarness>`

#### `getView(filter: SkyDataViewHarnessFilters): Promise<SkyDataViewHarness>`

Gets a specific data view based on the filter criteria.

#### Parameters

##### `filter: SkyDataViewHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyDataViewHarness>`

#### `getViews(filters?: SkyDataViewHarnessFilters): Promise<SkyDataViewHarness[]>`

Gets an array of data views based on the filter criteria. If no filter is provided, returns all data views.

#### Parameters

##### `filters?: SkyDataViewHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyDataViewHarness[]>`

#### `SkyDataManagerHarness.with(filters: SkyDataManagerHarnessFilters): HarnessPredicate<SkyDataManagerHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyDataManagerHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyDataManagerHarnessFilters`

#### Returns

`HarnessPredicate<SkyDataManagerHarness>`

 SkyDataManagerHarnessFilters
-----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDataManagerHarness` instances.

    interface SkyDataManagerHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyDataManagerToolbarHarness
-----------------------------

Type: Class

`import { SkyDataManagerToolbarHarness } from '@skyux/data-manager/testing';`

Harness for interacting with a data manager toolbar component in tests.

### Methods

#### `clickClearAll(): Promise<void>`

Clicks the data manager clear all button. Throws an error if the multiselect toolbar is turned off.

#### Returns

`Promise<void>`

#### `clickSelectAll(): Promise<void>`

Clicks the data manager select all button. Throws an error if the multiselect toolbar is turned off.

#### Returns

`Promise<void>`

#### `getFilterButton(): Promise<null | SkyFilterButtonHarness>`

Gets a harness for the data manager filter button.

#### Returns

`Promise<null | SkyFilterButtonHarness>`

#### `getLeftItem(filter: SkyDataManagerToolbarLeftItemHarnessFilters): Promise<SkyDataManagerToolbarLeftItemHarness>`

Gets a specific data manager toolbar left item based on the filter criteria.

#### Parameters

##### `filter: SkyDataManagerToolbarLeftItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyDataManagerToolbarLeftItemHarness>`

#### `getLeftItems(filters?: SkyDataManagerToolbarLeftItemHarnessFilters): Promise<SkyDataManagerToolbarLeftItemHarness[]>`

Gets an array of data manager toolbar left items based on the filter criteria. If no filter is provided, returns all data manager toolbar left items.

#### Parameters

##### `filters?: SkyDataManagerToolbarLeftItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyDataManagerToolbarLeftItemHarness[]>`

#### `getOnlyShowSelected(): Promise<null | SkyCheckboxHarness>`

Gets a harness for the only show selected checkbox.

#### Returns

`Promise<null | SkyCheckboxHarness>`

#### `getPrimaryItem(filter: SkyDataManagerToolbarPrimaryItemHarnessFilters): Promise<SkyDataManagerToolbarPrimaryItemHarness>`

Gets a specific data manager toolbar primary item based on the filter criteria.

#### Parameters

##### `filter: SkyDataManagerToolbarPrimaryItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyDataManagerToolbarPrimaryItemHarness>`

#### `getPrimaryItems(filters?: SkyDataManagerToolbarPrimaryItemHarnessFilters): Promise<SkyDataManagerToolbarPrimaryItemHarness[]>`

Gets an array of data manager toolbar primary items based on the filter criteria. If no filter is provided, returns all data manager toolbar primary items.

#### Parameters

##### `filters?: SkyDataManagerToolbarPrimaryItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyDataManagerToolbarPrimaryItemHarness[]>`

#### `getRightItem(filter: SkyDataManagerToolbarRightItemHarnessFilters): Promise<SkyDataManagerToolbarRightItemHarness>`

Gets a specific data manager toolbar right item based on the filter criteria.

#### Parameters

##### `filter: SkyDataManagerToolbarRightItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyDataManagerToolbarRightItemHarness>`

#### `getRightItems(filters?: SkyDataManagerToolbarRightItemHarnessFilters): Promise<SkyDataManagerToolbarRightItemHarness[]>`

Gets an array of data manager toolbar right items based on the filter criteria. If no filter is provided, returns all data manager toolbar right items.

#### Parameters

##### `filters?: SkyDataManagerToolbarRightItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyDataManagerToolbarRightItemHarness[]>`

#### `getSearch(): Promise<null | SkySearchHarness>`

Gets the data manager search harness.

#### Returns

`Promise<null | SkySearchHarness>`

#### `getSection(filter: SkyDataManagerToolbarSectionHarnessFilters): Promise<SkyDataManagerToolbarSectionHarness>`

Gets a specific toolbar section based on the filter criteria.

#### Parameters

##### `filter: SkyDataManagerToolbarSectionHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyDataManagerToolbarSectionHarness>`

#### `getSections(filters?: SkyDataManagerToolbarSectionHarnessFilters): Promise<SkyDataManagerToolbarSectionHarness[]>`

Gets an array of toolbar sections based on the filter criteria. If no filter is provided, returns all toolbar sections.

#### Parameters

##### `filters?: SkyDataManagerToolbarSectionHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyDataManagerToolbarSectionHarness[]>`

#### `getSortButton(): Promise<null | SkySortHarness>`

Gets a harness for the data manager sort button.

#### Returns

`Promise<null | SkySortHarness>`

#### `getViewActions(): Promise<null | SkyRadioGroupHarness>`

Gets the harness to interact with the data manager toolbar's view actions.

#### Returns

`Promise<null | SkyRadioGroupHarness>`

#### `openColumnPicker(): Promise<SkyDataManagerColumnPickerHarness>`

Opens the data manager column picker and returns the harness. Throws an error if the column picker is turned off.

#### Returns

`Promise<SkyDataManagerColumnPickerHarness>`

#### `SkyDataManagerToolbarHarness.with(filters: SkyDataManagerToolbarHarnessFilters): HarnessPredicate<SkyDataManagerToolbarHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyDataManagerToolbarHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyDataManagerToolbarHarnessFilters`

#### Returns

`HarnessPredicate<SkyDataManagerToolbarHarness>`

 SkyDataManagerToolbarHarnessFilters
------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDataManagerToolbarHarness` instances.

    interface SkyDataManagerToolbarHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyDataManagerToolbarSectionHarness
------------------------------------

Type: Class

`import { SkyDataManagerToolbarSectionHarness } from '@skyux/data-manager/testing';`

Harness to interact with a data manager toolbar section component in tests.

### Methods

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

#### `SkyDataManagerToolbarSectionHarness.with(filters: SkyDataManagerToolbarSectionHarnessFilters): HarnessPredicate<SkyDataManagerToolbarSectionHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyDataManagerToolbarSectionHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyDataManagerToolbarSectionHarnessFilters`

#### Returns

`HarnessPredicate<SkyDataManagerToolbarSectionHarness>`

 SkyDataManagerToolbarSectionHarnessFilters
-------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDataManagerToolbarSectionHarness` instances.

    interface SkyDataManagerToolbarSectionHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyDataManagerToolbarPrimaryItemHarness
----------------------------------------

Type: Class

`import { SkyDataManagerToolbarPrimaryItemHarness } from '@skyux/data-manager/testing';`

Harness to interact with a data manager toolbar primary item component in tests.

### Methods

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

#### `SkyDataManagerToolbarPrimaryItemHarness.with(filters: SkyDataManagerToolbarPrimaryItemHarnessFilters): HarnessPredicate<SkyDataManagerToolbarPrimaryItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyDataManagerToolbarPrimaryItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyDataManagerToolbarPrimaryItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyDataManagerToolbarPrimaryItemHarness>`

 SkyDataManagerToolbarPrimaryItemHarnessFilters
-----------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDataManagerToolbarPrimaryItemHarness` instances.

    interface SkyDataManagerToolbarPrimaryItemHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyDataManagerToolbarLeftItemHarness
-------------------------------------

Type: Class

`import { SkyDataManagerToolbarLeftItemHarness } from '@skyux/data-manager/testing';`

Harness to interact with a data manager toolbar left item component in tests.

### Methods

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

#### `SkyDataManagerToolbarLeftItemHarness.with(filters: SkyDataManagerToolbarLeftItemHarnessFilters): HarnessPredicate<SkyDataManagerToolbarLeftItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyDataManagerToolbarLeftItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyDataManagerToolbarLeftItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyDataManagerToolbarLeftItemHarness>`

 SkyDataManagerToolbarLeftItemHarnessFilters
--------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDataManagerToolbarLeftItemHarness` instances.

    interface SkyDataManagerToolbarLeftItemHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyDataManagerToolbarRightItemHarness
--------------------------------------

Type: Class

`import { SkyDataManagerToolbarRightItemHarness } from '@skyux/data-manager/testing';`

Harness to interact with a data manager toolbar right item component in tests.

### Methods

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

#### `SkyDataManagerToolbarRightItemHarness.with(filters: SkyDataManagerToolbarRightItemHarnessFilters): HarnessPredicate<SkyDataManagerToolbarRightItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyDataManagerToolbarRightItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyDataManagerToolbarRightItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyDataManagerToolbarRightItemHarness>`

 SkyDataManagerToolbarRightItemHarnessFilters
---------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDataManagerToolbarRightItemHarness` instances.

    interface SkyDataManagerToolbarRightItemHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyDataViewHarness
-------------------

Type: Class

`import { SkyDataViewHarness } from '@skyux/data-manager/testing';`

Harness to interact with a data manager view component in tests.

### Methods

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

#### `SkyDataViewHarness.with(filters: SkyDataViewHarnessFilters): HarnessPredicate<SkyDataViewHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyDataViewHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyDataViewHarnessFilters`

#### Returns

`HarnessPredicate<SkyDataViewHarness>`

 SkyDataViewHarnessFilters
--------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDataViewHarness` instances.

    interface SkyDataViewHarnessFilters {
      dataSkyId?: string | RegExp;
      viewId?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `viewId?: string`

 SkyDataManagerColumnPickerHarness
----------------------------------

Type: Class

`import { SkyDataManagerColumnPickerHarness } from '@skyux/data-manager/testing';`

Harness for interacting with a data manager column picker modal in tests.

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

#### `enterSearchText(value: string): Promise<void>`

Enters text into the search input and performs a search.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

#### `getColumn(filter: SkyDataManagerColumnPickerColumnHarnessFilters): Promise<SkyDataManagerColumnPickerColumnHarness>`

Gets a specific column based on the filter criteria.

#### Parameters

##### `filter: SkyDataManagerColumnPickerColumnHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyDataManagerColumnPickerColumnHarness>`

#### `getColumns(filters?: SkyDataManagerColumnPickerColumnHarnessFilters): Promise<SkyDataManagerColumnPickerColumnHarness[]>`

Gets an array of columns based on the filter criteria. If no filter is provided, returns all columns.

#### Parameters

##### `filters?: SkyDataManagerColumnPickerColumnHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyDataManagerColumnPickerColumnHarness[]>`

#### `saveAndClose(): Promise<void>`

Saves any selections made and closes the modal.

#### Returns

`Promise<void>`

#### `selectAll(): Promise<void>`

Selects all search results.

#### Returns

`Promise<void>`

#### `selectColumns(filters?: SkyDataManagerColumnPickerColumnHarnessFilters): Promise<void>`

Selects multiple columns based on a set of criteria.

#### Parameters

##### `filters?: SkyDataManagerColumnPickerColumnHarnessFilters`

#### Returns

`Promise<void>`

 SkyDataManagerColumnPickerColumnHarness
----------------------------------------

Type: Class

`import { SkyDataManagerColumnPickerColumnHarness } from '@skyux/data-manager/testing';`

Harness for interacting with a data manager column picker column result in tests.

### Methods

#### `deselect(): Promise<void>`

Deselects the column.

#### Returns

`Promise<void>`

#### `getContentText(): Promise<string>`

Gets the text of the column content.

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

Gets the text of the column title.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether a selectable repeater item is disabled.

#### Returns

`Promise<boolean>`

#### `isSelected(): Promise<boolean>`

Whether the column is selected.

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

Selects the column.

#### Returns

`Promise<void>`

#### `SkyDataManagerColumnPickerColumnHarness.with(filters: SkyDataManagerColumnPickerColumnHarnessFilters): HarnessPredicate<SkyDataManagerColumnPickerColumnHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyDataManagerColumnPickerColumnHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyDataManagerColumnPickerColumnHarnessFilters`

#### Returns

`HarnessPredicate<SkyDataManagerColumnPickerColumnHarness>`

 SkyDataManagerColumnPickerColumnHarnessFilters
-----------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDataManagerColumnPickerSearchResultHarness` instances.

    interface SkyDataManagerColumnPickerColumnHarnessFilters {
      contentText?: string | RegExp;
      dataSkyId?: string | RegExp;
      titleText?: string | RegExp;
    }

### Properties

#### `contentText?: string | RegExp`

Only find instances whose content matches the given value.

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `titleText?: string | RegExp`

Only find instances whose title matches the given value.