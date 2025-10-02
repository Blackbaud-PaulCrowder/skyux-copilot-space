---
component: 'search'
type: 'api-documentation'
description: 'API documentation for the search component including components, interfaces, and types.'
---

# Search API Documentation

## Components and Directives

#### LookupAutocompleteCustomSearchExampleComponent

**Selector:** `app-lookup-autocomplete-custom-search-example`

**Package:** `@skyux/code-examples`

#### LookupAutocompleteSearchFiltersExampleComponent

**Selector:** `app-lookup-autocomplete-search-filters-example`

**Package:** `@skyux/code-examples`

#### LookupSearchBasicExampleComponent

**Selector:** `app-lookup-search-basic-example`

**Package:** `@skyux/code-examples`

#### SkyListToolbarSearchActionsComponent

Displays custom actions in the toolbar beside to the search bar.

**Selector:** `sky-list-toolbar-search-actions`

**Package:** `@skyux/list-builder`

#### SkySearchComponent

**Selector:** `sky-search`

**Package:** `@skyux/lookup`

**Inputs:**

- `ariaLabel`: `string | undefined` - The ARIA label for the search input. This sets the search input's `aria-label` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
Use a context-sensitive label, such as "Search constituents." Context is especially important when multiple search inputs are in close proximity.
In toolbars, search inputs use the `listDescriptor` to provide context, and the ARIA label defaults to "Search <listDescriptor>."
If the box includes a visible label, use `ariaLabelledBy` instead.
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `ariaLabelledBy`: `string | undefined` - The HTML element ID of the element that labels
the search. This sets the search's `aria-labelledby` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the box does not include a visible label, use `ariaLabel` instead.
For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).
- `placeholderText`: `string | undefined` - Placeholder text to display in the search input until users
enter search criteria. (default: "Find in this list")
- `searchText`: `string | undefined` - Default search criteria for the input.
- `debounceTime`: `number` - How many milliseconds to wait before searching after users enter text in the search input. (default: 0)
- `disabled`: `boolean` - Whether to disable the search. (default: false)
- `expandMode`: `string` - The expand mode for the search input. The valid options
include `"responsive"` to collapse the search input into a button on
mobile devices, `"none"` to *not* collapse the search input on mobile
devices, and `"fit"` to extend the search input to fit the width of its container. (default: "responsive")

**Outputs:**

- `searchApply`: `EventEmitter<string>` - Fires when the search text is applied.
- `searchChange`: `EventEmitter<string>` - Fires when the search text is changed.
- `searchClear`: `EventEmitter<void>` - Fires when the search text is cleared.