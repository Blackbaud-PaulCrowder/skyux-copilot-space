---
component: 'filter'
description: 'Design guidelines, API documentation, and usage instructions for the filter component extracted from SKY UX documentation.'
---

# Filter Component Guidelines

## Component Overview
Expandable inline filters allow users to access the filter options that they need to narrow lists. They are hidden by default, and users select a button to display them.

## Usage

### ✅ Use when

Use expandable inline filters when users need up to four simple filter controls for lists that appear within containers, such as boxes, on pages or modals. Simple filters include checkboxes and HTML select inputs.

Filter controls are hidden by default and accessed through a Filter button, so they are especially useful for controls that users don't need frequently or that don't have significant impact. If users need more filters or more complex filtering, use a dedicated list view with a filter bar instead, and allow users to navigate to the dedicated list from the container to complete their filtering tasks.

For more details about filtering lists, see the filtering lists guidelines.

**✅ Do use expandable inline filters in containers for simple filter controls that won't be used frequently.**

### ❌ Don't use when

Don't use expandable inline filters when users only need one or two simple filter controls that can fit above the lists. Use persistent inline filters instead. Persistent inline filters are especially useful for controls that users will need frequently or that have significant impact.

**❌ Don't use expandable inline filters for one or two simple filter controls that users need frequently.**

Don't use expandable inline filters for full-page lists when the main, or only, task for users is to narrow a collection of items or manipulate a pre-filtered collection. Use a filter bar instead to make filters always available and directly selectable.

**❌ Don't use expandable inline filters for full-page lists. Use filter bars instead.**

## Anatomy

- Toolbar (transparent)
- Filter button
- Expandable filter section (transparent)
- Simple filters

## Behaviors and states

## Layout

Filter buttons appear in the toolbar above lists.

## Related information

### Components

- Toolbar

### Guidelines

- Filter lists

## API Documentation

### Components and Directives

#### SkyProgressIndicatorFilters

A set of criteria that can be used to filter a list of `SkyProgressIndicatorHarness` instances.

**Package:** `@skyux/progress-indicator/testing`

#### SkyProgressIndicatorItemFilters

A set of criteria that can be used to filter a list of `SkyProgressIndicatorItemHarness` instances.

**Package:** `@skyux/progress-indicator/testing`

#### FilterBarBasicExampleComponent

**Selector:** `app-filter-bar-basic-example`

**Package:** `@skyux/code-examples`

#### ListsFilterInlineExampleComponent

**Selector:** `app-lists-filter-inline-example`

**Package:** `@skyux/code-examples`

#### ListsFilterModalExampleComponent

**Selector:** `app-lists-filter-modal-example`

**Package:** `@skyux/code-examples`

#### LookupAutocompleteSearchFiltersExampleComponent

**Selector:** `app-lookup-autocomplete-search-filters-example`

**Package:** `@skyux/code-examples`

#### SkyDataManagerFilterModalContext

Sets the state of the filters.

**Package:** `@skyux/data-manager`

#### SkyDataManagerFilterData

**Package:** `@skyux/data-manager`

#### SkyDataManagerStateUpdateFilterArgs

Optional arguments to pass to `getDataStateUpdates`.
Provide either a list of properties to filter on OR a custom comparator.

**Package:** `@skyux/data-manager`

#### SkyDataManagerColumnPickerColumnHarnessFilters

A set of criteria that can be used to filter a list of `SkyDataManagerColumnPickerSearchResultHarness` instances.

**Package:** `@skyux/data-manager/testing`

#### SkyDataManagerHarnessFilters

A set of criteria that can be used to filter a list of `SkyDataManagerHarness` instances.

**Package:** `@skyux/data-manager/testing`

#### SkyDataManagerToolbarHarnessFilters

A set of criteria that can be used to filter a list of `SkyDataManagerToolbarHarness` instances.

**Package:** `@skyux/data-manager/testing`

#### SkyDataManagerToolbarLeftItemHarnessFilters

A set of criteria that can be used to filter a list of `SkyDataManagerToolbarLeftItemHarness` instances.

**Package:** `@skyux/data-manager/testing`

#### SkyDataManagerToolbarPrimaryItemHarnessFilters

A set of criteria that can be used to filter a list of `SkyDataManagerToolbarPrimaryItemHarness` instances.

**Package:** `@skyux/data-manager/testing`

#### SkyDataManagerToolbarRightItemHarnessFilters

A set of criteria that can be used to filter a list of `SkyDataManagerToolbarRightItemHarness` instances.

**Package:** `@skyux/data-manager/testing`

#### SkyDataManagerToolbarSectionHarnessFilters

A set of criteria that can be used to filter a list of `SkyDataManagerToolbarSectionHarness` instances.

**Package:** `@skyux/data-manager/testing`

#### SkyDataViewHarnessFilters

A set of criteria that can be used to filter a list of `SkyDataViewHarness` instances.

**Package:** `@skyux/data-manager/testing`

#### ListFilterModel

**Package:** `@skyux/list-builder`

#### SkyListFilterButtonComponent

Contains a filter button for the list toolbar. Place a
[`sky-filter-button`](https://developer.blackbaud.com/skyux/components/filter)
component inside this component to open a modal with filtering options.
To apply filter options, use the
[list component's](https://developer.blackbaud.com/skyux/components/list/overview#list-properties)
`appliedFilters` property.

**Selector:** `sky-list-filter-button`

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### SkyListFilterInlineItemComponent

Creates a filter in the list's inline filter area.

**Selector:** `sky-list-filter-inline-item`

**Package:** `@skyux/list-builder`

**Inputs:**

- `defaultValue`: `any` - The default value of the filter. If the value of the filter
is set to the default value, then the filter is not applied.
- `filter`: `(item: ListItemModel, filter: any) => boolean` - The function that determines whether an item is filtered.
This property is required when using an in-memory data provider. For information
about `ListItemModel`, see the
[shared classes for lists](https://developer.blackbaud.com/skyux-list-builder-common/docs/list-builder-common).
- `name`: `string` - The name of the filter. **[Required]**
- `template`: `TemplateRef<unknown>` - The template for the filter. The template can access the `filter`
variable that contains the `value` of the filter control, which should be bound to
`ngModel`, and the `changed` function, which should be called when the model changes. **[Required]**
- `value`: `any` - The current value of the filter.

⚠️ **This component is deprecated.**

#### SkyListFilterInlineComponent

Creates an inline filter area for the list. Place each filter
in a `sky-list-filter-inline-item` component.

**Selector:** `sky-list-filter-inline`

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### SkyListFilterInlineModel

**Package:** `@skyux/list-builder`

#### SkyListFilterSummaryComponent

Creates a filter summary based on the
[list component's](https://developer.blackbaud.com/skyux/components/list/overview#list-properties)
`appliedFilters` property. Place this component within the
[`sky-list-toolbar`](https://developer.blackbaud.com/skyux/components/list/toolbar) component.

**Selector:** `sky-list-filter-summary`

**Package:** `@skyux/list-builder`

**Outputs:**

- `summaryItemClick`: `EventEmitter<ListFilterModel>` - Emits a `ListFilterModel` when users select a summary item. A common use case is
to open a filter modal when this event is received.

⚠️ **This component is deprecated.**

#### SkyListFiltersModule

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListFiltersOrchestrator

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListFiltersUpdateAction

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### SkySummaryActionBarCancelHarnessFilters

A set of criteria that can be used to filter a list of SkySummaryActionBarCancelHarness instances.

**Package:** `@skyux/action-bars/testing`

#### SkySummaryActionBarHarnessFilters

A set of criteria that can be used to filter a list of SkySummaryActionBarHarness instances.

**Package:** `@skyux/action-bars/testing`

#### SkySummaryActionBarPrimaryActionHarnessFilters

A set of criteria that can be used to filter a list of SkySummaryActionBarPrimaryActionHarness instances.

**Package:** `@skyux/action-bars/testing`

#### SkySummaryActionBarSecondaryActionHarnessFilters

A set of criteria that can be used to filter a list of SkySummaryActionBarSecondaryActionHarness instances.

**Package:** `@skyux/action-bars/testing`

#### SkySummaryActionBarSecondaryActionsHarnessFilters

A set of criteria that can be used to filter a list of SkySummaryActionBarSecondaryActionsHarness instances.

**Package:** `@skyux/action-bars/testing`

#### SkySummaryActionBarSummaryHarnessFilters

A set of criteria that can be used to filter a list of SkySummaryActionBarSummaryHarness instances.

**Package:** `@skyux/action-bars/testing`

#### SkyColorpickerDropdownHarnessFilters

A set of criteria that can be used to filter a list of `SkyColorpickerDropdownHarness` instances.

**Package:** `@skyux/colorpicker/testing`

#### SkyColorpickerHarnessFilters

A set of criteria that can be used to filter a list of `SkyColorpickerHarness` instances.

**Package:** `@skyux/colorpicker/testing`

#### SkyHelpInlineHarnessFilters

A set of criteria that can be used to filter a list of `SkyHelpInlineHarness` instances.

**Package:** `@skyux/help-inline/testing`

#### SkyInlineFormButtonHarnessFilters

A set of criteria that can be used to filter a list of `SkyInlineFormButtonHarness` instances.

**Package:** `@skyux/inline-form/testing`

#### SkyInlineFormHarnessFilters

A set of criteria that can be used to filter a list of `SkyInlineFormHarness` instances.

**Package:** `@skyux/inline-form/testing`

#### SkyPhoneFieldHarnessFilters

A set of criteria that can be used to filter a list of SkyPhoneFieldHarness instances.

**Package:** `@skyux/phone-field/testing`

#### SkyFilterBarComponent

The top-level filter bar component.

**Selector:** `sky-filter-bar`

**Package:** `@skyux/filter-bar`

**Inputs:**

- `appliedFilters`: `ModelSignal<undefined | SkyFilterBarFilterItem[]>` - An array of filter items containing the IDs and values of the filters that have been set.
- `selectedFilterIds`: `ModelSignal<undefined | string[]>` - An array of filter IDs that the user has selected using the built-in selection modal. Setting this input to undefined results in all filters being displayed.

#### SkyFilterBarModule

**Package:** `@skyux/filter-bar`

#### SkyFilterItemModalComponent

A filter bar item that opens a modal for complex filter configuration.
Use this component when your filter requires a rich UI with multiple inputs,
date pickers, or other complex controls that don't fit in an inline filter.

**Selector:** `sky-filter-item-modal`

**Package:** `@skyux/filter-bar`

**Inputs:**

- `filterId`: `InputSignal<string>` - A unique identifier for the filter item. **[Required]**
- `labelText`: `InputSignal<string>` - The label to display for the filter item. **[Required]**
- `modalComponent`: `InputSignal<Type<SkyFilterItemModal<TData>>>` - The modal component to display when the user selects the filter.
The component needs to inject a `SkyFilterItemModalInstance` object on instantiation to receive the modal instance and context from the modal service.
The return value of the modal save action needs to be a `SkyFilterBarFilterValue`. **[Required]**
- `modalSize`: `InputSignal<SkyFilterItemModalSizeType>` - The size of the modal to display. The valid options are `"small"`, `"medium"`, `"large"`, and `"fullScreen"`.

**Outputs:**

- `modalOpened`: `EventEmitter<SkyFilterItemModalOpenedArgs<TData>>` - Fires when the user clicks the filter item. To pass additional context data to a filter modal, consumers
must subscribe to this event and return the context using the observable property on the event args.

#### SkyFilterBarFilterItem

Represents a specific filter item and its selected value, if any.

**Package:** `@skyux/filter-bar`

#### SkyFilterBarFilterValue

Represents a value for a filter item.

**Package:** `@skyux/filter-bar`

#### SkyFilterItemModalContext

The context object that is provided to a filter modal.

**Package:** `@skyux/filter-bar`

#### SkyFilterItemModalInstance

A specialized `SkyModalInstance` wrapper.

**Package:** `@skyux/filter-bar`

#### SkyFilterItemModalOpenedArgs

Arguments passed to a filter modal when it opens.

**Package:** `@skyux/filter-bar`

#### SkyFilterItemModalSavedArgs

Arguments passed back from a filter modal when the user has saved.

**Package:** `@skyux/filter-bar`

#### SkyFilterItemModalSizeType

**Package:** `@skyux/filter-bar`

#### SkyFilterItemModal

A type marker for passing context object data types into the filter modal component.

**Package:** `@skyux/filter-bar`

#### SkyFilterBarHarnessFilters

A set of criteria that can be used to filter a list of `SkyFilterBarHarness` instances.

**Package:** `@skyux/filter-bar/testing`

#### SkyFilterBarHarness

Harness for interacting with a filter bar component in tests.

**Package:** `@skyux/filter-bar/testing`

#### SkyFilterItemHarnessFilters

A set of criteria that can be used to filter a list of `SkyFilterItemHarness` instances.

**Package:** `@skyux/filter-bar/testing`

#### SkyFilterItemHarness

Harness to interact with a filter item component in tests.

**Package:** `@skyux/filter-bar/testing`

#### SkyAlertHarnessFilters

A set of criteria that can be used to filter a list of SkyAlertHarness instances.

**Package:** `@skyux/indicators/testing`

#### SkyHelpInlineHarnessFilters

A set of criteria that can be used to filter a list of SkyHelpInlineHarness instances.

**Package:** `@skyux/indicators/testing`

⚠️ **This component is deprecated.**

#### SkyIllustrationHarnessFilters

A set of criteria that can be used to filter a list of `SkyIllustrationHarness` instances.

**Package:** `@skyux/indicators/testing`

#### SkyKeyInfoHarnessFilters

A set of criteria that can be used to filter a list of SkyKeyInfoHarness instances.

**Package:** `@skyux/indicators/testing`

#### SkyLabelHarnessFilters

A set of criteria that can be used to filter a list of `SkyLabelHarness` instances.

**Package:** `@skyux/indicators/testing`

#### SkyStatusIndicatorHarnessFilters

A set of criteria that can be used to filter a list of SkyStatusIndicatorHarness instances.

**Package:** `@skyux/indicators/testing`

#### SkyTextHighlightHarnessFilters

A set of criteria that can be used to filter a list of SkyTextHighlightHarness instances.

**Package:** `@skyux/indicators/testing`

#### SkyTokenHarnessFilters

A set of criteria that can be used to filter a list of `SkyTokenHarness` instances.

**Package:** `@skyux/indicators/testing`

#### SkyTokensHarnessFilters

A set of criteria that can be used to filter a list of `SkyTokensHarness` instances.

**Package:** `@skyux/indicators/testing`

#### SkyWaitHarnessFilters

A set of criteria that can be used to filter a list of SkyWaitHarness instances.

**Package:** `@skyux/indicators/testing`

#### SkySplitViewHarnessFilters

A set of criteria that can be used to filter a list of SkySplitViewHarness instances.

**Package:** `@skyux/split-view/testing`

#### SkyDateRangePickerFilters

A set of criteria that can be used to filter a list of `SkyDateRangePickerHarness` instances.

**Package:** `@skyux/datetime/testing`

#### SkyDatepickerCalendarHarnessFilters

A set of criteria that can be used to filter a list of `SkyDatepickerCalendarHarness` instances.

**Package:** `@skyux/datetime/testing`

#### SkyDatepickerFilters

A set of criteria that can be used to filter a list of `SkyDatepickerHarness` instances.

**Package:** `@skyux/datetime/testing`

#### SkyTimepickerFilters

A set of criteria that can be used to filter a list of `SkyTimepickerHarness` instances.

**Package:** `@skyux/datetime/testing`

#### SkyDropdownHarnessFilters

A set of criteria that can be used to filter a list of `SkyDropdownHarness` instances.

**Package:** `@skyux/popovers/testing`

#### SkyDropdownItemHarnessFilters

A set of criteria that can be used to filter a list of `SkyDropdownItemHarness` instances.

**Package:** `@skyux/popovers/testing`

#### SkyDropdownMenuHarnessFilters

A set of criteria that can be used to filter a list of `SkyDropdownMenuHarness` instances.

**Package:** `@skyux/popovers/testing`

#### SkyPopoverContentHarnessFilters

A set of criteria that can be used to filter a list of `SkyComponentHarness` instances.

**Package:** `@skyux/popovers/testing`

#### SkyPopoverHarnessFilters

A set of criteria that can be used to filter a list of SkyPopoverHarness instances.

**Package:** `@skyux/popovers/testing`

#### SkyAvatarHarnessFilters

A set of criteria that can be used to filter a list of SkyAvatarHarness instances.

**Package:** `@skyux/avatar/testing`

#### SkyErrorHarnessFilters

A set of criteria that can be used to filter a list of `SkyErrorHarness` instances.

**Package:** `@skyux/errors/testing`

#### SkyActionButtonContainerHarnessFilters

A set of criteria that can be used to filter a list of `SkyActionButtonContainerHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyActionButtonHarnessFilters

A set of criteria that can be used to filter a list of `SkyActionButtonHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyBoxHarnessFilters

A set of criteria that can be used to filter a list of `SkyBoxHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyDescriptionListHarnessFilters

A set of criteria that can be used to filter a list of `SkyDescriptionListHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyColumnHarnessFilters

A set of criteria that can be used to filter a list of `SkyColumnHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyFluidGridHarnessFilters

A set of criteria that can be used to filter a list of `SkyFluidGridHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyRowHarnessFilters

A set of criteria that can be used to filter a list of `SkyRowHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyInlineDeleteHarnessFilters

A set of criteria that can be used to filter a list of `SkyInlineDeleteHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyTextExpandRepeaterHarnessFilters

A set of criteria that can be used to filter a list of `SkyTextExpandRepeaterHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyTextExpandHarnessFilters

A set of criteria that can be used to filter a list of `SkyTextExpandHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyToolbarHarnessFilters

A set of criteria that can be used to filter a list of `SkyToolbarHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyToolbarItemHarnessFilters

A set of criteria that can be used to filter a list of `SkyToolbarItemHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyToolbarSectionHarnessFilters

A set of criteria that can be used to filter a list of `SkyToolbarSectionHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyAutocompleteSearchFunctionFilter

**Package:** `@skyux/lookup`

#### SkyAutocompleteHarnessFilters

A set of criteria that can be used to filter a list of SkyAutocompleteHarness instances.

**Package:** `@skyux/lookup/testing`

#### SkyAutocompleteSearchResultHarnessFilters

A set of criteria that can be used to filter a list of SkyAutocompleteSearchResultHarness instances.

**Package:** `@skyux/lookup/testing`

#### SkyCountryFieldHarnessFilters

A set of criteria that can be used to filter a list of `SkyCountryFieldHarness` instances.

**Package:** `@skyux/lookup/testing`

#### SkyCountryFieldSearchResultHarnessFilters

A set of criteria that can be used to filter a list of `SkyCountryFieldSearchResultHarness` instances.

**Package:** `@skyux/lookup/testing`

#### SkyLookupHarnessFilters

A set of criteria that can be used to filter a list of `SkyLookupHarness` instances.

**Package:** `@skyux/lookup/testing`

#### SkyLookupSearchResultHarnessFilters

A set of criteria that can be used to filter a list of `SkyLookupSearchResultHarness` instances.

**Package:** `@skyux/lookup/testing`

#### SkyLookupShowMorePickerHarnessFilters

A set of criteria that can be used to filter a list of `SkyLookupShowMorePickerHarness` instances.

**Package:** `@skyux/lookup/testing`

#### SkyLookupShowMorePickerSearchResultHarnessFilters

A set of criteria that can be used to filter a list of `SkyLookupShowMorePickerSearchResultHarness` instances.

**Package:** `@skyux/lookup/testing`

#### SkySearchHarnessFilters

A set of criteria that can be used to filter a list of `SkySearchHarness` instances.

**Package:** `@skyux/lookup/testing`

#### SkySelectionModalSearchResultHarnessFilters

A set of criteria that can be used to filter a list of `SkySelectionModalSearchResultHarness` instances.

**Package:** `@skyux/lookup/testing`

#### SkyConfirmButtonHarnessFilters

A set of criteria that can be used to filter a list of SkyConfirmButtonHarness instances.

**Package:** `@skyux/modals/testing`

#### SkyModalHarnessFilters

A set of criteria that can be used to filter a list of SkyModalHarness instances.

**Package:** `@skyux/modals/testing`

#### SkyNavbarHarnessFilters

A set of criteria that can be used to filter a list of `SkyNavbarHarness` instances.

**Package:** `@skyux/navbar/testing`

#### SkyNavbarItemHarnessFilters

A set of criteria that can be used to filter a list of `SkyNavbarItemHarness` instances.

**Package:** `@skyux/navbar/testing`

#### SkyHrefHarnessFilters

A set of criteria that can be used to filter a list of `SkyHrefHarness` instances.

**Package:** `@skyux/router/testing`

#### SkyCharacterCounterIndicatorHarnessFilters

A set of criteria that can be used to filter a list of SkyCharacterCounterIndicatorHarness instances.

**Package:** `@skyux/forms/testing`

#### SkyCheckboxGroupHarnessFilters

A set of criteria that can be used to filter a list of `SkyCheckboxGroupHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyCheckboxHarnessFilters

A set of criteria that can be used to filter a list of `SkyCheckboxHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyFieldGroupHarnessFilters

A set of criteria that can be used to filter a list of `SkyFieldGroupHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyFileAttachmentHarnessFilters

A set of criteria that can be used to filter a list of `SkyFileAttachmentHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyFileDropHarnessFilters

A set of criteria that can be used to filter a list of `SkyFileDropHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyFileItemHarnessFilters

A set of criteria that can be used to filter a list of `SkyFileItemHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyFormErrorHarnessFilters

A set of criteria that can be used to filter a list of `SkyFormErrorHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyFormErrorsHarnessFilters

A set of criteria that can be used to filter a list of `SkyFormErrorHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyInputBoxHarnessFilters

A set of criteria that can be used to filter a list of SkyInputBoxHarness instances.

**Package:** `@skyux/forms/testing`

#### SkyRadioGroupHarnessFilters

A set of criteria that can be used to filter a list of `SkyRadioGroupHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyRadioHarnessFilters

A set of criteria that can be used to filter a list of `SkyRadioHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkySelectionBoxGridHarnessFilters

A set of criteria that can be used to filter a list of `SkySelectionBoxGridHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkySelectionBoxHarnessFilters

A set of criteria that can be used to filter a list of `SkySelectionBoxHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyToggleSwitchHarnessFilters

A set of criteria that can be used to filter a list of `SkyToggleSwitchHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyFilterButtonComponent

**Selector:** `sky-filter-button`

**Package:** `@skyux/lists`

**Inputs:**

- `active`: `boolean | undefined` - Whether to highlight the filter button to indicate that filters were applied.
We recommend setting this property to `true` when no indication of filtering is visible
to users. For example, set it to `true` if you do not display the filter summary. (default: false)
- `ariaControls`: `string | undefined` - The ID to identify the element that contains
the filtering options that the filter button exposes.
To support [accessibility rules for disclosures](https://www.w3.org/TR/wai-aria-practices-1.1/#disclosure),
this property is necessary to set the `aria-controls` attribute when using inline filters.
For more information about the `aria-controls` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-controls).
- `ariaExpanded`: `boolean | undefined` - Whether the filtering options are exposed.
To support [accessibility rules for disclosures](https://www.w3.org/TR/wai-aria-practices-1.1/#disclosure),
this property is necessary to set the `aria-expanded` attribute when using inline filters.
For more information about the `aria-expanded` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-expanded). (default: false)
- `ariaLabel`: `string | undefined` - The ARIA label for the filter button. This sets the
filter button's `aria-label` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
Use a context-sensitive label, such as "Filter constituents." Context is especially important when multiple filter buttons are in close proximity.
In toolbars, filter buttons use the `listDescriptor` to provide context, and the ARIA label defaults to "Filter <listDescriptor>."
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `disabled`: `boolean | undefined` - Whether to disable the filter button. (default: false)
- `showButtonText`: `boolean | undefined` - Whether to display a "Filter" label beside the icon on the filter button. (default: false)
- `filterButtonId`: `string` - The ID for the filter button.

**Outputs:**

- `filterButtonClick`: `EventEmitter<void>` - Fires when the filter button is selected.

#### SkyFilterInlineItemComponent

Specifies an inline filter.

**Selector:** `sky-filter-inline-item`

**Package:** `@skyux/lists`

#### SkyFilterInlineComponent

Specifies a wrapper for the inline filters.

**Selector:** `sky-filter-inline`

**Package:** `@skyux/lists`

#### SkyFilterSummaryItemComponent

Specifies a filter that was applied.

**Selector:** `sky-filter-summary-item`

**Package:** `@skyux/lists`

**Inputs:**

- `dismissible`: `boolean` - Whether the filter summary item has a close button.

**Outputs:**

- `dismiss`: `EventEmitter<void>` - Fires when the summary item close button is selected.
- `itemClick`: `EventEmitter<void>` - Fires when the summary item is selected.

#### SkyFilterSummaryComponent

Specifies a wrapper for the filters that were applied.

**Selector:** `sky-filter-summary`

**Package:** `@skyux/lists`

#### SkyFilterModule

**Package:** `@skyux/lists`

#### SkyFilterTestingModule

**Package:** `@skyux/lists/testing`

#### SkyFilterButtonHarnessFilters

A set of criteria that can be used to filter a list of `SkyFilterButtonHarness` instances.

**Package:** `@skyux/lists/testing`

#### SkyFilterButtonHarness

Harness for interacting with a filter button component in tests.

**Package:** `@skyux/lists/testing`

#### SkyFilterInlineHarnessFilters

A set of criteria that can be used to filter a list of `SkyFilterInlineHarness` instances.

**Package:** `@skyux/lists/testing`

#### SkyFilterInlineHarness

Harness to interact with a filter inline component in tests.

**Package:** `@skyux/lists/testing`

#### SkyFilterInlineItemHarnessFilters

A set of criteria that can be used to filter a list of `SkyFilterInlineItemHarness` instances.

**Package:** `@skyux/lists/testing`

#### SkyFilterInlineItemHarness

Harness to interact with a filter inline item component in tests.

**Package:** `@skyux/lists/testing`

#### SkyFilterSummaryHarnessFilters

A set of criteria that can be used to filter a list of `SkyFilterSummaryHarness` instances.

**Package:** `@skyux/lists/testing`

#### SkyFilterSummaryHarness

Harness to interact with a filter summary component in tests.

**Package:** `@skyux/lists/testing`

#### SkyFilterSummaryItemHarnessFilters

A set of criteria that can be used to filter a list of `SkyFilterSummaryItemHarness` instances.

**Package:** `@skyux/lists/testing`

#### SkyFilterSummaryItemHarness

Harness to interact with a filter summary item component in tests.

**Package:** `@skyux/lists/testing`

#### SkyInfiniteScrollHarnessFilters

A set of criteria that can be used to filter a list of `SkyInfiniteScrollHarness` instances.

**Package:** `@skyux/lists/testing`

#### SkyPagingHarnessFilters

A set of criteria that can be used to filter a list of `SkyPagingHarness` instances.

**Package:** `@skyux/lists/testing`

#### SkyRepeaterHarnessFilters

A set of criteria that can be used to filter a list of `SkyRepeaterHarness` instances.

**Package:** `@skyux/lists/testing`

#### SkyRepeaterItemHarnessFilters

A set of criteria that can be used to filter a list of `SkyRepeaterItemHarness` instances.

**Package:** `@skyux/lists/testing`

#### SkySortHarnessFilters

A set of criteria that can be used to filter a list of `SkySortHarness` instances.

**Package:** `@skyux/lists/testing`

#### SkySortItemHarnessFilters

A set of criteria that can be used to filter a list of `SkySortItemHarness` instances.

**Package:** `@skyux/lists/testing`

#### SkyActionHubHarnessFilters

A set of criteria that can be used to filter a list of SkyActionHubHarness instances.

**Package:** `@skyux/pages/testing`

#### SkyLinkListHarnessFilters

A set of criteria that can be used to filter a list of SkyLinkListHarness instances.

**Package:** `@skyux/pages/testing`

#### SkyLinkListItemHarnessFilters

A set of criteria that can be used to filter a list of SkyLinkListItemHarness instances.

**Package:** `@skyux/pages/testing`

#### SkyNeedsAttentionHarnessFilters

A set of criteria that can be used to filter a list of SkyNeedsAttentionHarness instances.

**Package:** `@skyux/pages/testing`

#### SkyNeedsAttentionItemHarnessFilters

A set of criteria that can be used to filter a list of SkyNeedsAttentionItemHarness instances.

**Package:** `@skyux/pages/testing`

#### SkyPageHeaderHarnessFilters

A set of criteria that can be used to filter a list of SkyPageHeaderHarness instances.

**Package:** `@skyux/pages/testing`

#### SkyPageHarnessFilters

A set of criteria that can be used to filter a list of SkyPageHarness instances.

**Package:** `@skyux/pages/testing`

#### SkyTileContentSectionHarnessFilters

A set of criteria that can be used to filter a list of `SkyTileContentSectionHarness` instances.

**Package:** `@skyux/tiles/testing`

#### SkyTileDashboardHarnessFilters

A set of criteria that can be used to filter a list of `SkyTileDashboardHarness` instances.

**Package:** `@skyux/tiles/testing`

#### SkyTileHarnessFilters

A set of criteria that can be used to filter a list of `SkyTileHarness` instances.

**Package:** `@skyux/tiles/testing`

#### SkyToastHarnessFilters

A set of criteria that can be used to filter a list of `SkyToastHarness` instances.

**Package:** `@skyux/toast/testing`

#### SkyOverlayHarnessFilters

A set of criteria that can be used to filter a list of SkyOverlayHarness instances.

**Package:** `@skyux/core/testing`

#### SkyHarnessFilters

A set of criteria that can be used to filter a list of `SkyComponentHarness` instances.

**Package:** `@skyux/core/testing`

#### SkyIconHarnessFilters

A set of criteria that can be used to filter a list of SkyIconHarness instances.

**Package:** `@skyux/icon/testing`

#### SkySectionedFormHarnessFilters

A set of criteria that can be used to filter a list of `SkySectionedFormHarness` instances.

**Package:** `@skyux/tabs/testing`

#### SkySectionedFormSectionContentHarnessFilters

A set of criteria that can be used to filter a list of `SkySectionedFormSectionContentHarness` instances.

**Package:** `@skyux/tabs/testing`

#### SkySectionedFormSectionHarnessFilters

A set of criteria that can be used to filter a list of `SkySectionedFormSectionHarness` instances.

**Package:** `@skyux/tabs/testing`

#### SkyTabButtonHarnessFilters

A set of criteria that can be used to filter a list of `SkyTabButtonHarness` instances.

**Package:** `@skyux/tabs/testing`

#### SkyTabContentHarnessFilters

A set of criteria that can be used to filter a list of `SkyTabContentHarness` instances.

**Package:** `@skyux/tabs/testing`

#### SkyTabsetHarnessFilters

A set of criteria that can be used to filter a list of `SkyTabsetHarness` instances.

**Package:** `@skyux/tabs/testing`

#### SkyTabsetNavButtonHarnessFilters

A set of criteria that can be used to filter a list of `SkyTabsetNavButtonHarness` instances.

**Package:** `@skyux/tabs/testing`

#### SkyVerticalTabButtonHarnessFilters

A set of criteria that can be used to filter a list of  `SkyVerticalTabButtonHarness` instances.

**Package:** `@skyux/tabs/testing`

#### SkyVerticalTabContentHarnessFilters

A set of criteria that can be used to filter a list of `SkyVerticalTabContentHarness` instances.

**Package:** `@skyux/tabs/testing`

#### SkyVerticalTabsetGroupHarnessFilters

A set of criteria that can be used to filter a list of  `SkyVerticalTabsetGroupHarness` instances.

**Package:** `@skyux/tabs/testing`

#### SkyVerticalTabsetHarnessFilters

A set of criteria that can be used to filter a list of `SkyVerticalTabsetHarness` instances.

**Package:** `@skyux/tabs/testing`

### Code Examples

#### Filter bar basic example

**Selector:** `app-filter-bar-basic-example`

**TypeScript:**

```typescript
import { Component, model } from '@angular/core';
import {
  SkyFilterBarFilterItem,
  SkyFilterBarModule,
  SkyFilterItemModalOpenedArgs,
} from '@skyux/filter-bar';

import { of } from 'rxjs';

import { FilterItems } from './filter-items';
import { CommunityConnectionFilterModalComponent } from './filter-modals/community-connection-filter-modal.component';
import { CurrentGradeFilterModalComponent } from './filter-modals/current-grade-filter-modal.component';
import { EnteringGradeFilterModalComponent } from './filter-modals/entering-grade-filter-modal.component';
import { RoleFilterModalComponent } from './filter-modals/role-filter-modal.component';
import { StaffAssignedFilterModalComponent } from './filter-modals/staff-assigned-filter-modal.component';
import { FILTER_SELECTION_VALUES } from './filter-selection-values';

/**
 * @title Filter bar basic example
 */
@Component({
  selector: 'app-filter-bar-basic-example',
  imports: [SkyFilterBarModule],
  templateUrl: './example.component.html',
})
export class FilterBarBasicExampleComponent {
  protected readonly appliedFilters = model<
    SkyFilterBarFilterItem[] | undefined
  >();
  protected readonly selectedFilterIds = model<string[] | undefined>([
    'staff-assigned',
    'entering-grade',
    'current-grade',
  ]);

  protected communityConnectionModal = CommunityConnectionFilterModalComponent;
  protected currentGradeModal = CurrentGradeFilterModalComponent;
  protected enteringGradeModal = EnteringGradeFilterModalComponent;
  protected roleModal = RoleFilterModalComponent;
  protected staffAssignedModal = StaffAssignedFilterModalComponent;

  protected onModalOpened(
    args: SkyFilterItemModalOpenedArgs<FilterItems>,
  ): void {
    args.data = of({ items: FILTER_SELECTION_VALUES[args.filterId] });
  }
}

```

**Template:**

```html
<sky-filter-bar
  [(appliedFilters)]="appliedFilters"
  [(selectedFilterIds)]="selectedFilterIds"
>
  <sky-filter-item-modal
    filterId="community-connection"
    labelText="Community connection"
    modalSize="medium"
    [modalComponent]="communityConnectionModal"
    (modalOpened)="onModalOpened($event)"
  />
  <sky-filter-item-modal
    filterId="current-grade"
    labelText="Current grade"
    modalSize="medium"
    [modalComponent]="currentGradeModal"
    (modalOpened)="onModalOpened($event)"
  />
  <sky-filter-item-modal
    filterId="entering-grade"
    labelText="Entering grade"
    modalSize="medium"
    [modalComponent]="enteringGradeModal"
    (modalOpened)="onModalOpened($event)"
  />
  <sky-filter-item-modal
    filterId="role"
    labelText="Role"
    modalSize="medium"
    [modalComponent]="roleModal"
    (modalOpened)="onModalOpened($event)"
  />
  <sky-filter-item-modal
    filterId="staff-assigned"
    labelText="Staff assigned"
    modalSize="medium"
    [modalComponent]="staffAssignedModal"
    (modalOpened)="onModalOpened($event)"
  />
</sky-filter-bar>

```

#### Expandable inline filter

**Selector:** `app-lists-filter-inline-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { FormsModule } from '@angular/forms';
import { SkyIdModule } from '@skyux/core';
import { SkyCheckboxModule, SkyInputBoxModule } from '@skyux/forms';
import { SkyToolbarModule } from '@skyux/layout';
import { SkyFilterModule, SkyRepeaterModule } from '@skyux/lists';

interface Filter {
  name: string;
  value: string | boolean;
}

interface Fruit {
  name: string;
  type: string;
  color: string;
}

/**
 * @title Expandable inline filter
 */
@Component({
  selector: 'app-lists-filter-inline-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    SkyCheckboxModule,
    SkyIdModule,
    SkyFilterModule,
    SkyInputBoxModule,
    SkyRepeaterModule,
    SkyToolbarModule,
  ],
})
export class ListsFilterInlineExampleComponent {
  protected appliedFilters: Filter[] = [];
  protected filteredItems: Fruit[];
  protected filtersActive = false;
  protected fruitType = 'any';
  protected hideOrange = false;

  protected items: Fruit[] = [
    {
      name: 'Orange',
      type: 'citrus',
      color: 'orange',
    },
    {
      name: 'Mango',
      type: 'other',
      color: 'orange',
    },
    {
      name: 'Lime',
      type: 'citrus',
      color: 'green',
    },
    {
      name: 'Strawberry',
      type: 'berry',
      color: 'red',
    },
    {
      name: 'Blueberry',
      type: 'berry',
      color: 'blue',
    },
  ];

  protected showInlineFilters = false;

  constructor() {
    this.filteredItems = this.items.slice();
  }

  protected filterButtonClicked(): void {
    this.showInlineFilters = !this.showInlineFilters;
  }

  protected fruitTypeChange(newValue: string): void {
    this.fruitType = newValue;
    this.#setFilterActiveState();
  }

  protected hideOrangeChange(newValue: boolean): void {
    this.hideOrange = newValue;
    this.#setFilterActiveState();
  }

  #setFilterActiveState(): void {
    this.appliedFilters = [];

    if (this.fruitType !== 'any') {
      this.appliedFilters.push({
        name: 'fruitType',
        value: this.fruitType,
      });
    }

    if (this.hideOrange) {
      this.appliedFilters.push({
        name: 'hideOrange',
        value: true,
      });
    }

    this.filtersActive = this.appliedFilters.length > 0;
    this.filteredItems = this.#filterItems(this.items, this.appliedFilters);
  }

  #orangeFilterFailed(filter: Filter, item: Fruit): boolean {
    return (
      filter.name === 'hideOrange' && !!filter.value && item.color === 'orange'
    );
  }

  #fruitTypeFilterFailed(filter: Filter, item: Fruit): boolean {
    return (
      filter.name === 'fruitType' &&
      filter.value !== 'any' &&
      filter.value !== item.type
    );
  }

  #itemIsShown(filters: Filter[], item: Fruit): boolean {
    let passesFilter = true,
      j: number;

    for (j = 0; j < filters.length; j++) {
      if (this.#orangeFilterFailed(filters[j], item)) {
        passesFilter = false;
      } else if (this.#fruitTypeFilterFailed(filters[j], item)) {
        passesFilter = false;
      }
    }

    return passesFilter;
  }

  #filterItems(items: Fruit[], filters: Filter[]): Fruit[] {
    let i: number, passesFilter: boolean;
    const result: Fruit[] = [];

    for (i = 0; i < items.length; i++) {
      passesFilter = this.#itemIsShown(filters, items[i]);
      if (passesFilter) {
        result.push(items[i]);
      }
    }

    return result;
  }
}

```

**Template:**

```html
<sky-toolbar>
  <sky-toolbar-section>
    <sky-toolbar-item>
      <sky-filter-button
        data-sky-id="my-filter-button"
        [active]="filtersActive"
        [ariaControls]="inlineFilters.id"
        [ariaExpanded]="showInlineFilters"
        [showButtonText]="true"
        (filterButtonClick)="filterButtonClicked()"
      />
    </sky-toolbar-item>
  </sky-toolbar-section>
</sky-toolbar>

<div #inlineFilters skyId [hidden]="!showInlineFilters">
  <sky-filter-inline data-sky-id="filter-inline">
    <sky-filter-inline-item data-sky-id="fruit-filter">
      <sky-input-box labelText="Fruit type">
        <select [ngModel]="fruitType" (ngModelChange)="fruitTypeChange($event)">
          <option value="any">Any fruit</option>
          <option value="citrus">Citrus</option>
          <option value="berry">Berry</option>
        </select>
      </sky-input-box>
    </sky-filter-inline-item>
    <sky-filter-inline-item data-sky-id="hide-orange-filter">
      <sky-checkbox
        labelText="Hide orange fruits"
        [ngModel]="hideOrange"
        (ngModelChange)="hideOrangeChange($event)"
      />
    </sky-filter-inline-item>
  </sky-filter-inline>
</div>

<sky-repeater expandMode="none">
  @for (item of filteredItems; track item) {
    <sky-repeater-item>
      <sky-repeater-item-title>
        {{ item.name }}
      </sky-repeater-item-title>
    </sky-repeater-item>
  }
</sky-repeater>

```

#### Modal filter

**Selector:** `app-lists-filter-modal-example`

**TypeScript:**

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  inject,
} from '@angular/core';
import { SkyToolbarModule } from '@skyux/layout';
import { SkyFilterModule, SkyRepeaterModule } from '@skyux/lists';
import { SkyModalCloseArgs, SkyModalService } from '@skyux/modals';

import { Filter } from './filter';
import { FilterModalContext } from './filter-modal-context';
import { FilterModalComponent } from './filter-modal.component';
import { Fruit } from './fruit';

/**
 * @title Modal filter
 */
@Component({
  selector: 'app-lists-filter-modal-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [SkyFilterModule, SkyRepeaterModule, SkyToolbarModule],
})
export class ListsFilterModalExampleComponent {
  protected appliedFilters: Filter[] = [];
  protected filteredItems: Fruit[];
  protected items: Fruit[] = [
    {
      name: 'Orange',
      type: 'citrus',
      color: 'orange',
    },
    {
      name: 'Mango',
      type: 'other',
      color: 'orange',
    },
    {
      name: 'Lime',
      type: 'citrus',
      color: 'green',
    },
    {
      name: 'Strawberry',
      type: 'berry',
      color: 'red',
    },
    {
      name: 'Blueberry',
      type: 'berry',
      color: 'blue',
    },
  ];

  protected showInlineFilters = false;

  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #modalSvc = inject(SkyModalService);

  constructor() {
    this.filteredItems = this.items.slice();
  }

  protected onDismiss(index: number): void {
    this.appliedFilters.splice(index, 1);
    this.filteredItems = this.#filterItems(this.items, this.appliedFilters);
  }

  protected onInlineFilterButtonClicked(): void {
    this.showInlineFilters = !this.showInlineFilters;
  }

  protected onModalFilterButtonClick(): void {
    const modalInstance = this.#modalSvc.open(FilterModalComponent, [
      {
        provide: FilterModalContext,
        useValue: {
          appliedFilters: this.appliedFilters,
        },
      },
    ]);

    modalInstance.closed.subscribe((result: SkyModalCloseArgs) => {
      if (result.reason === 'save') {
        this.appliedFilters = (result.data as Filter[]).slice();
        this.filteredItems = this.#filterItems(this.items, this.appliedFilters);
        this.#changeDetectorRef.markForCheck();
      }
    });
  }

  #fruitTypeFilterFailed(filter: Filter, item: Fruit): boolean {
    return (
      filter.name === 'fruitType' &&
      filter.value !== 'any' &&
      filter.value !== item.type
    );
  }

  #itemIsShown(filters: Filter[], item: Fruit): boolean {
    let passesFilter = true,
      j: number;

    for (j = 0; j < filters.length; j++) {
      if (this.#orangeFilterFailed(filters[j], item)) {
        passesFilter = false;
      } else if (this.#fruitTypeFilterFailed(filters[j], item)) {
        passesFilter = false;
      }
    }

    return passesFilter;
  }

  #filterItems(items: Fruit[], filters: Filter[]): Fruit[] {
    let i: number, passesFilter: boolean;
    const result: Fruit[] = [];

    for (i = 0; i < items.length; i++) {
      passesFilter = this.#itemIsShown(filters, items[i]);
      if (passesFilter) {
        result.push(items[i]);
      }
    }

    return result;
  }

  #orangeFilterFailed(filter: Filter, item: Fruit): boolean {
    return (
      filter.name === 'hideOrange' && !!filter.value && item.color === 'orange'
    );
  }
}

```

**Template:**

```html
<sky-toolbar>
  <sky-toolbar-section>
    <sky-toolbar-item>
      <sky-filter-button
        data-sky-id="my-filter-button"
        [showButtonText]="true"
        (filterButtonClick)="onModalFilterButtonClick()"
      />
    </sky-toolbar-item>
  </sky-toolbar-section>
  @if (appliedFilters && appliedFilters.length > 0) {
    <sky-toolbar-section>
      <sky-filter-summary data-sky-id="filter-summary">
        @for (item of appliedFilters; track item; let i = $index) {
          <sky-filter-summary-item (dismiss)="onDismiss(i)">
            {{ item.label }}
          </sky-filter-summary-item>
        }
      </sky-filter-summary>
    </sky-toolbar-section>
  }
</sky-toolbar>
<sky-repeater expandMode="none">
  @for (item of filteredItems; track item) {
    <sky-repeater-item>
      <sky-repeater-item-title>
        {{ item.name }}
      </sky-repeater-item-title>
    </sky-repeater-item>
  }
</sky-repeater>

```

#### Autocomplete with search filters

**Selector:** `app-lookup-autocomplete-search-filters-example`

**TypeScript:**

```typescript
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

```

**Template:**

```html
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

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.