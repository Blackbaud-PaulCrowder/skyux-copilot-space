                    

 Repeater
========

Repeaters display information in containers for a list of objects. Repeater lists are effective alternatives to grids in mobile-intensive contexts and other scenarios that require the compact display of information.

 Installation
-------------

NPM package

`@skyux/lists`[View in NPM](https://www.npmjs.com/package/@skyux/lists) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/lists/src/lib/modules/repeater/repeater.module.ts#L48) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/lists`Copy None found.

 SkyRepeaterModule
------------------

Type: Module

`import { SkyRepeaterModule } from '@skyux/lists';`

 SkyRepeaterComponent
---------------------

Type: Component

Selector: `sky-repeater`

Creates a container to display repeater items.

### Inputs

#### `activeIndex: number | undefined`

The index of the repeater item to visually highlight as active. For example, use this property in conjunction with the [split view component](/skyux/components/split-view.md) to highlight a repeater item while users edit it. Only one item can be active at a time.

#### `ariaLabel: string | undefined`

The ARIA label for the repeater list. This sets the repeater list's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

Default: `"List of items"`

#### `expandMode: SkyRepeaterExpandModeType`

The layout that determines which repeater items are expanded by default and whether repeater items are expandable and collapsible. Collapsed items display titles only. The valid options are `multiple`, `none`, and `single`.

*   `multiple` loads repeater items in an expanded state unless `isExpanded` is set to `false` for a repeater item. This layout allows users to expand and collapse as many repeater items as necessary. It is best-suited to repeater items where body content is important but users don't always need to see it.
*   `none` loads all repeater items in an expanded state and does not allow users to collapse them. This default layout provides the quickest access to the details in the repeater items. It is best-suited to repeater items with concise content that users need to view frequently.
*   `single` loads one repeater item in an expanded state and collapses all others. The expanded repeater item is the first one where `isExpanded` is set to `true`. This layout allows users to expand one item at a time. It provides the most compact view and is best-suited to repeater items where the most important information is in the titles and users only occasionally need to view the body content.

Default: `"none"`

#### `reorderable: boolean | undefined`

Whether users can change the order of items in the repeater list. Each repeater item also has `reorderable` property to indicate whether users can change its order.

Default: `false`

### Outputs

#### `activeIndexChange: EventEmitter<number>`

Fires when the active repeater item changes.

#### `orderChange: EventEmitter<any[]>`

Fires when users change the order of repeater items. This event emits an ordered array of the `tag` properties that the consumer provides for each repeater item.

 SkyRepeaterItemComponent
-------------------------

Type: Component

Selector: `sky-repeater-item`

Creates an individual repeater item.

### Inputs

#### `disabled: boolean | undefined`

Whether to disable a selectable repeater item.

#### `inlineFormConfig: SkyInlineFormConfig | undefined`

Configuration options for the buttons to display on an inline form within the repeater. This property accepts [a `SkyInlineFormConfig` object](/skyux/components/inline-form#skyinlineformconfig-properties.md).

#### `inlineFormTemplate: TemplateRef<unknown> | undefined`

Specifies [an Angular `TemplateRef`](https://angular.io/api/core/TemplateRef) to use as a template to instantiate an inline form within the repeater.

#### `isExpanded: boolean`

Whether the repeater item is expanded.

Default: `true`

#### `isSelected: boolean | undefined`

Whether the repeater item's checkbox is selected. When users select the repeater item, the specified property on your model is updated accordingly.

Default: `false`

#### `itemName: string | undefined`

The human-readable name for the repeater item that is available for multiple purposes, such as accessibility and instrumentation. For example, the component uses the name to construct ARIA labels for the repeater item controls to [support accessibility](/skyux/learn/accessibility.md). If not specified, the repeater item's title will be used for this value. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `selectable: boolean | undefined`

Whether to display a checkbox in the left of the repeater item.

Default: `false`

#### `showInlineForm: boolean | undefined`

Whether to display an inline form within the repeater. Users can toggle between displaying and hiding the inline form.

Default: `false`

#### `tag: any`

The object that the repeater component returns for this repeater item when the `orderChange` event fires. This is required if you set the `reorderable` property to `true`.

### Outputs

#### `collapse: EventEmitter<void>`

Fires when users collapse the repeater item.

#### `expand: EventEmitter<void>`

Fires when users expand the repeater item.

#### `inlineFormClose: EventEmitter<SkyInlineFormCloseArgs>`

Fires when the repeater includes an inline form and users close it. This event emits [a `SkyInlineFormCloseArgs` type](/skyux/components/inline-form#skyinlineformcloseargs-properties.md).

#### `isSelectedChange: EventEmitter<boolean>`

Fires when users select or clear the checkbox for the repeater item.

 SkyRepeaterItemTitleComponent
------------------------------

Type: Component

Selector: `sky-repeater-item-title`

Displays a header inside the repeater item.

 SkyRepeaterItemContentComponent
--------------------------------

Type: Component

Selector: `sky-repeater-item-content`

Displays content text when the repeater is expanded.

 SkyRepeaterItemContextMenuComponent
------------------------------------

Type: Component

Selector: `sky-repeater-item-context-menu`

Wraps and styles a [`skyux-dropdown` component](https://developer.blackbaud.com/skyux-popovers/docs/dropdown).

 SkyRepeaterExpandModeType
--------------------------

Type: Type alias

    type SkyRepeaterExpandModeType = "single" | "multiple" | "none"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyRepeaterHarness
-------------------

Type: Class

`import { SkyRepeaterHarness } from '@skyux/lists/testing';`

Harness for interacting with a repeater component in tests.

### Methods

#### `getAriaLabel(): Promise<null | string>`

Gets the aria-label for the repeater list

#### Returns

`Promise<null | string>`

#### `getRepeaterItem(filter: SkyRepeaterItemHarnessFilters): Promise<SkyRepeaterItemHarness>`

Gets a specific repeater item based on the filter criteria.

#### Parameters

##### `filter: SkyRepeaterItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyRepeaterItemHarness>`

#### `getRepeaterItems(filters?: SkyRepeaterItemHarnessFilters): Promise<SkyRepeaterItemHarness[]>`

Gets an array of repeater items based on the filter criteria. If no filter is provided, returns all repeater items.

#### Parameters

##### `filters?: SkyRepeaterItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyRepeaterItemHarness[]>`

#### `SkyRepeaterHarness.with(filters: SkyRepeaterHarnessFilters): HarnessPredicate<SkyRepeaterHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyRepeaterHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyRepeaterHarnessFilters`

#### Returns

`HarnessPredicate<SkyRepeaterHarness>`

 SkyRepeaterHarnessFilters
--------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyRepeaterHarness` instances.

    interface SkyRepeaterHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyRepeaterItemHarness
-----------------------

Type: Class

`import { SkyRepeaterItemHarness } from '@skyux/lists/testing';`

Harness for interacting with a repeater item component in tests.

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

#### `SkyRepeaterItemHarness.with(filters: SkyRepeaterItemHarnessFilters): HarnessPredicate<SkyRepeaterItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyRepeaterItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyRepeaterItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyRepeaterItemHarness>`

 SkyRepeaterItemHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyRepeaterItemHarness` instances.

    interface SkyRepeaterItemHarnessFilters {
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

Context menu for Context menu for Context menu for Context menu for