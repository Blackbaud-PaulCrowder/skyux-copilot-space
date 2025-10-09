                    

 Search
======

The search input lets users enter search criteria.

 Installation
-------------

NPM package

`@skyux/lookup`[View in NPM](https://www.npmjs.com/package/@skyux/lookup) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lookup/src/lib/modules/search/search.module.ts#L26) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lookup`Copy None found.

 SkySearchModule
----------------

Type: Module

`import { SkySearchModule } from '@skyux/lookup';`

 SkySearchComponent
-------------------

Type: Component

Selector: `sky-search`

### Inputs

#### `ariaLabel: string | undefined`

The ARIA label for the search input. This sets the search input's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). Use a context-sensitive label, such as "Search constituents." Context is especially important when multiple search inputs are in close proximity. In toolbars, search inputs use the `listDescriptor` to provide context, and the ARIA label defaults to "Search <listDescriptor>." If the box includes a visible label, use `ariaLabelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `ariaLabelledBy: string | undefined`

The HTML element ID of the element that labels the search. This sets the search's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the box does not include a visible label, use `ariaLabel` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `debounceTime: number`

How many milliseconds to wait before searching after users enter text in the search input.

Default: `0`

#### `disabled: boolean`

Whether to disable the search.

Default: `false`

#### `expandMode: string`

The expand mode for the search input. The valid options include `"responsive"` to collapse the search input into a button on mobile devices, `"none"` to _not_ collapse the search input on mobile devices, and `"fit"` to extend the search input to fit the width of its container.

Default: `"responsive"`

#### `placeholderText: string | undefined`

Placeholder text to display in the search input until users enter search criteria.

Default: `"Find in this list"`

#### `searchText: string | undefined`

Default search criteria for the input.

### Outputs

#### `searchApply: EventEmitter<string>`

Fires when the search text is applied.

#### `searchChange: EventEmitter<string>`

Fires when the search text is changed.

#### `searchClear: EventEmitter<void>`

Fires when the search text is cleared.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkySearchHarness
-----------------

Type: Class

`import { SkySearchHarness } from '@skyux/lookup/testing';`

Harness for interacting with a search component in tests.

### Methods

#### `blur(): Promise<void>`

Blurs the search input.

#### Returns

`Promise<void>`

#### `clear(): Promise<void>`

Clears the search input.

#### Returns

`Promise<void>`

#### `clickClearButton(): Promise<void>`

Clicks the search input clear button.

#### Returns

`Promise<void>`

#### `clickDismissSearchButton(): Promise<void>`

Clicks search dismiss button to collapse search back to a button.

#### Returns

`Promise<void>`

#### `clickOpenSearchButton(): Promise<void>`

Clicks the search icon button that opens search input when it is collapsed.

#### Returns

`Promise<void>`

#### `clickSubmitButton(): Promise<void>`

Clicks the search submit button.

#### Returns

`Promise<void>`

#### `enterText(value: string): Promise<void>`

Enters text into the search input and performs a search.

#### Parameters

##### `value: string`

#### Returns

`Promise<void>`

#### `focus(): Promise<void>`

Focuses the search input.

#### Returns

`Promise<void>`

#### `getAriaLabel(): Promise<null | string>`

Gets the search input's `aria-label`.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledby(): Promise<null | string>`

Gets the search's aria-labelledby.

#### Returns

`Promise<null | string>`

#### `getPlaceholderText(): Promise<null | string>`

Gets the value of the input's placeholder attribute.

#### Returns

`Promise<null | string>`

#### `getValue(): Promise<string>`

Gets the value of the search input.

#### Returns

`Promise<string>`

#### `isCollapsed(): Promise<boolean>`

Whether the search input is collapsed.

#### Returns

`Promise<boolean>`

#### `isDisabled(): Promise<boolean>`

Whether the search input is disabled.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the search input is focused.

#### Returns

`Promise<boolean>`

#### `SkySearchHarness.with(filters: SkySearchHarnessFilters): HarnessPredicate<SkySearchHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySearchHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySearchHarnessFilters`

#### Returns

`HarnessPredicate<SkySearchHarness>`

 SkySearchHarnessFilters
------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkySearchHarness` instances.

    interface SkySearchHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.