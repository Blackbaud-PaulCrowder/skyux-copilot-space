---
component: 'filter'
type: 'api-documentation'
description: 'API documentation for the filter component including components, interfaces, and types.'
---

# Filter API Documentation

## Components and Directives

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

#### SkyListFilterButtonComponent

Contains a filter button for the list toolbar. Place a
[`sky-filter-button`](https://developer.blackbaud.com/skyux/components/filter)
component inside this component to open a modal with filtering options.
To apply filter options, use the
[list component's](https://developer.blackbaud.com/skyux/components/list/overview#list-properties)
`appliedFilters` property.

**Selector:** `sky-list-filter-button`

**Package:** `@skyux/list-builder`

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
- `name`: `string` - The name of the filter.
- `template`: `TemplateRef<unknown>` - The template for the filter. The template can access the `filter`
variable that contains the `value` of the filter control, which should be bound to
`ngModel`, and the `changed` function, which should be called when the model changes.
- `value`: `any` - The current value of the filter.

#### SkyListFilterInlineComponent

Creates an inline filter area for the list. Place each filter
in a `sky-list-filter-inline-item` component.

**Selector:** `sky-list-filter-inline`

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

#### SkyFilterBarComponent

The top-level filter bar component.

**Selector:** `sky-filter-bar`

**Package:** `@skyux/filter-bar`

**Inputs:**

- `appliedFilters`: `ModelSignal<undefined | SkyFilterBarFilterItem[]>` - An array of filter items containing the IDs and values of the filters that have been set.
- `selectedFilterIds`: `ModelSignal<undefined | string[]>` - An array of filter IDs that the user has selected using the built-in selection modal. Setting this input to undefined results in all filters being displayed.

#### SkyFilterItemModalComponent

A filter bar item that opens a modal for complex filter configuration.
Use this component when your filter requires a rich UI with multiple inputs,
date pickers, or other complex controls that don't fit in an inline filter.

**Selector:** `sky-filter-item-modal`

**Package:** `@skyux/filter-bar`

**Inputs:**

- `filterId`: `InputSignal<string>` - A unique identifier for the filter item.
- `labelText`: `InputSignal<string>` - The label to display for the filter item.
- `modalComponent`: `InputSignal<Type<SkyFilterItemModal<TData>>>` - The modal component to display when the user selects the filter.
The component needs to inject a `SkyFilterItemModalInstance` object on instantiation to receive the modal instance and context from the modal service.
The return value of the modal save action needs to be a `SkyFilterBarFilterValue`.
- `modalSize`: `InputSignal<SkyFilterItemModalSizeType>` - The size of the modal to display. The valid options are `"small"`, `"medium"`, `"large"`, and `"fullScreen"`.

**Outputs:**

- `modalOpened`: `EventEmitter<SkyFilterItemModalOpenedArgs<TData>>` - Fires when the user clicks the filter item. To pass additional context data to a filter modal, consumers
must subscribe to this event and return the context using the observable property on the event args.

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