# Design

                  Skip to Main Content

 Fluid grid
==========

The fluid grid component provides a responsive 12-column layout to organize content for all device sizes.

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)
*   [Page design](/skyux/design/guidelines/page-layouts.md)
*   [Spacing](/skyux/design/styles/spacing.md)

### Styles

*   [Responsiveness](/skyux/design/styles/responsiveness.md)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/fluid-grid/fluid-grid.module.ts#L13) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyFluidGridModule
-------------------

Type: Module

`import { SkyFluidGridModule } from '@skyux/layout';`

 SkyFluidGridComponent
----------------------

Type: Component

Selector: `sky-fluid-grid`

Wraps the fluid grid to ensure proper spacing. Without the wrapper, the alignment, padding, and margins do not behave as expected.

### Inputs

#### `disableMargin: boolean | undefined`

Disables the outer left and right margin of the fluid grid container.

Default: `false`

#### `gutterSize: SkyFluidGridGutterSizeType`

The type that defines the size of the padding between columns.

Default: `"large"`

 SkyRowComponent
----------------

Type: Component

Selector: `sky-row`

Displays a row within the `sky-fluid-grid` wrapper. Previously, you could display a row without a wrapper, but we no longer officially support that option.

### Inputs

#### `reverseColumnOrder: boolean | undefined`

Whether to reverse the display order for columns in the row.

Default: `false`

 SkyColumnComponent
-------------------

Type: Component

Selector: `sky-column`

Displays a column within a row of the fluid grid.

### Inputs

#### `screenLarge: number | undefined`

The number of columns (1-12) on large screens (more than 1200px). If you do not specify a value, the column inherits the `screenMedium` value.

#### `screenMedium: number | undefined`

The number of columns (1-12) on medium screens (992-1199px). If you do not specify a value, the column inherits the `screenSmall` value.

#### `screenSmall: number | undefined`

The number of columns (1-12) on small screens (768-991px). If you do not specify a value, the column inherits the `screenXSmall` value.

#### `screenXSmall: number`

The number of columns (1-12) on extra-small screens (less than 768px). If you do not specify a value, the fluid grid displays the column at the full width of the screen.

Default: `12`

 SkyFluidGridGutterSizeType
---------------------------

Type: Type alias

    type SkyFluidGridGutterSizeType = "small" | "medium" | "large"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyFluidGridHarness
--------------------

Type: Class

`import { SkyFluidGridHarness } from '@skyux/layout/testing';`

Harness for interacting with a fluid grid component in tests.

### Methods

#### `getGutterSize(): Promise<string>`

Gets the gutter size for the grid.

#### Returns

`Promise<string>`

#### `getRows(): Promise<SkyRowHarness[]>`

Gets all of the rows in the grid.

#### Returns

`Promise<SkyRowHarness[]>`

#### `hasMargin(): Promise<boolean>`

Whether the fluid grid has margin enabled.

#### Returns

`Promise<boolean>`

#### `SkyFluidGridHarness.with(filters: SkyFluidGridHarnessFilters): HarnessPredicate<SkyFluidGridHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFluidGridHarness` that meets certain criteria

#### Parameters

##### `filters: SkyFluidGridHarnessFilters`

#### Returns

`HarnessPredicate<SkyFluidGridHarness>`

 SkyFluidGridHarnessFilters
---------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFluidGridHarness` instances.

    interface SkyFluidGridHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyRowHarness
--------------

Type: Class

`import { SkyRowHarness } from '@skyux/layout/testing';`

Harness for interacting with a fluid grid column component in tests.

### Methods

#### `getColumnOrder(): Promise<string>`

Gets the ordering of the columns in the row.

#### Returns

`Promise<string>`

#### `getColumns(): Promise<SkyColumnHarness[]>`

Gets all of the columns in the row.

#### Returns

`Promise<SkyColumnHarness[]>`

#### `SkyRowHarness.with(filters: SkyRowHarnessFilters): HarnessPredicate<SkyRowHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyRowHarness` that meets certain criteria

#### Parameters

##### `filters: SkyRowHarnessFilters`

#### Returns

`HarnessPredicate<SkyRowHarness>`

 SkyRowHarnessFilters
---------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyRowHarness` instances.

    interface SkyRowHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyColumnHarness
-----------------

Type: Class

`import { SkyColumnHarness } from '@skyux/layout/testing';`

Harness for interacting with a fluid grid column component in tests.

### Methods

#### `getLargeSize(): Promise<number>`

Gets the size of the column in a Large responsive context.

#### Returns

`Promise<number>`

#### `getMediumSize(): Promise<number>`

Gets the size of the column in a Medium responsive context.

#### Returns

`Promise<number>`

#### `getSmallSize(): Promise<number>`

Gets the size of the column in a Small responsive context.

#### Returns

`Promise<number>`

#### `getXSmallSize(): Promise<number>`

Gets the size of the column in an XSmall responsive context.

#### Returns

`Promise<number>`

#### `SkyColumnHarness.with(filters: SkyColumnHarnessFilters): HarnessPredicate<SkyColumnHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyColumnHarness` that meets certain criteria

#### Parameters

##### `filters: SkyColumnHarnessFilters`

#### Returns

`HarnessPredicate<SkyColumnHarness>`

 SkyColumnHarnessFilters
------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyColumnHarness` instances.

    interface SkyColumnHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Development

                  Skip to Main Content

 Fluid grid
==========

The fluid grid component provides a responsive 12-column layout to organize content for all device sizes.

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)
*   [Page design](/skyux/design/guidelines/page-layouts.md)
*   [Spacing](/skyux/design/styles/spacing.md)

### Styles

*   [Responsiveness](/skyux/design/styles/responsiveness.md)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/fluid-grid/fluid-grid.module.ts#L13) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyFluidGridModule
-------------------

Type: Module

`import { SkyFluidGridModule } from '@skyux/layout';`

 SkyFluidGridComponent
----------------------

Type: Component

Selector: `sky-fluid-grid`

Wraps the fluid grid to ensure proper spacing. Without the wrapper, the alignment, padding, and margins do not behave as expected.

### Inputs

#### `disableMargin: boolean | undefined`

Disables the outer left and right margin of the fluid grid container.

Default: `false`

#### `gutterSize: SkyFluidGridGutterSizeType`

The type that defines the size of the padding between columns.

Default: `"large"`

 SkyRowComponent
----------------

Type: Component

Selector: `sky-row`

Displays a row within the `sky-fluid-grid` wrapper. Previously, you could display a row without a wrapper, but we no longer officially support that option.

### Inputs

#### `reverseColumnOrder: boolean | undefined`

Whether to reverse the display order for columns in the row.

Default: `false`

 SkyColumnComponent
-------------------

Type: Component

Selector: `sky-column`

Displays a column within a row of the fluid grid.

### Inputs

#### `screenLarge: number | undefined`

The number of columns (1-12) on large screens (more than 1200px). If you do not specify a value, the column inherits the `screenMedium` value.

#### `screenMedium: number | undefined`

The number of columns (1-12) on medium screens (992-1199px). If you do not specify a value, the column inherits the `screenSmall` value.

#### `screenSmall: number | undefined`

The number of columns (1-12) on small screens (768-991px). If you do not specify a value, the column inherits the `screenXSmall` value.

#### `screenXSmall: number`

The number of columns (1-12) on extra-small screens (less than 768px). If you do not specify a value, the fluid grid displays the column at the full width of the screen.

Default: `12`

 SkyFluidGridGutterSizeType
---------------------------

Type: Type alias

    type SkyFluidGridGutterSizeType = "small" | "medium" | "large"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyFluidGridHarness
--------------------

Type: Class

`import { SkyFluidGridHarness } from '@skyux/layout/testing';`

Harness for interacting with a fluid grid component in tests.

### Methods

#### `getGutterSize(): Promise<string>`

Gets the gutter size for the grid.

#### Returns

`Promise<string>`

#### `getRows(): Promise<SkyRowHarness[]>`

Gets all of the rows in the grid.

#### Returns

`Promise<SkyRowHarness[]>`

#### `hasMargin(): Promise<boolean>`

Whether the fluid grid has margin enabled.

#### Returns

`Promise<boolean>`

#### `SkyFluidGridHarness.with(filters: SkyFluidGridHarnessFilters): HarnessPredicate<SkyFluidGridHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFluidGridHarness` that meets certain criteria

#### Parameters

##### `filters: SkyFluidGridHarnessFilters`

#### Returns

`HarnessPredicate<SkyFluidGridHarness>`

 SkyFluidGridHarnessFilters
---------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFluidGridHarness` instances.

    interface SkyFluidGridHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyRowHarness
--------------

Type: Class

`import { SkyRowHarness } from '@skyux/layout/testing';`

Harness for interacting with a fluid grid column component in tests.

### Methods

#### `getColumnOrder(): Promise<string>`

Gets the ordering of the columns in the row.

#### Returns

`Promise<string>`

#### `getColumns(): Promise<SkyColumnHarness[]>`

Gets all of the columns in the row.

#### Returns

`Promise<SkyColumnHarness[]>`

#### `SkyRowHarness.with(filters: SkyRowHarnessFilters): HarnessPredicate<SkyRowHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyRowHarness` that meets certain criteria

#### Parameters

##### `filters: SkyRowHarnessFilters`

#### Returns

`HarnessPredicate<SkyRowHarness>`

 SkyRowHarnessFilters
---------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyRowHarness` instances.

    interface SkyRowHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyColumnHarness
-----------------

Type: Class

`import { SkyColumnHarness } from '@skyux/layout/testing';`

Harness for interacting with a fluid grid column component in tests.

### Methods

#### `getLargeSize(): Promise<number>`

Gets the size of the column in a Large responsive context.

#### Returns

`Promise<number>`

#### `getMediumSize(): Promise<number>`

Gets the size of the column in a Medium responsive context.

#### Returns

`Promise<number>`

#### `getSmallSize(): Promise<number>`

Gets the size of the column in a Small responsive context.

#### Returns

`Promise<number>`

#### `getXSmallSize(): Promise<number>`

Gets the size of the column in an XSmall responsive context.

#### Returns

`Promise<number>`

#### `SkyColumnHarness.with(filters: SkyColumnHarnessFilters): HarnessPredicate<SkyColumnHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyColumnHarness` that meets certain criteria

#### Parameters

##### `filters: SkyColumnHarnessFilters`

#### Returns

`HarnessPredicate<SkyColumnHarness>`

 SkyColumnHarnessFilters
------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyColumnHarness` instances.

    interface SkyColumnHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Examples

                  Skip to Main Content

 Fluid grid
==========

The fluid grid component provides a responsive 12-column layout to organize content for all device sizes.

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)
*   [Page design](/skyux/design/guidelines/page-layouts.md)
*   [Spacing](/skyux/design/styles/spacing.md)

### Styles

*   [Responsiveness](/skyux/design/styles/responsiveness.md)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/fluid-grid/fluid-grid.module.ts#L13) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyFluidGridModule
-------------------

Type: Module

`import { SkyFluidGridModule } from '@skyux/layout';`

 SkyFluidGridComponent
----------------------

Type: Component

Selector: `sky-fluid-grid`

Wraps the fluid grid to ensure proper spacing. Without the wrapper, the alignment, padding, and margins do not behave as expected.

### Inputs

#### `disableMargin: boolean | undefined`

Disables the outer left and right margin of the fluid grid container.

Default: `false`

#### `gutterSize: SkyFluidGridGutterSizeType`

The type that defines the size of the padding between columns.

Default: `"large"`

 SkyRowComponent
----------------

Type: Component

Selector: `sky-row`

Displays a row within the `sky-fluid-grid` wrapper. Previously, you could display a row without a wrapper, but we no longer officially support that option.

### Inputs

#### `reverseColumnOrder: boolean | undefined`

Whether to reverse the display order for columns in the row.

Default: `false`

 SkyColumnComponent
-------------------

Type: Component

Selector: `sky-column`

Displays a column within a row of the fluid grid.

### Inputs

#### `screenLarge: number | undefined`

The number of columns (1-12) on large screens (more than 1200px). If you do not specify a value, the column inherits the `screenMedium` value.

#### `screenMedium: number | undefined`

The number of columns (1-12) on medium screens (992-1199px). If you do not specify a value, the column inherits the `screenSmall` value.

#### `screenSmall: number | undefined`

The number of columns (1-12) on small screens (768-991px). If you do not specify a value, the column inherits the `screenXSmall` value.

#### `screenXSmall: number`

The number of columns (1-12) on extra-small screens (less than 768px). If you do not specify a value, the fluid grid displays the column at the full width of the screen.

Default: `12`

 SkyFluidGridGutterSizeType
---------------------------

Type: Type alias

    type SkyFluidGridGutterSizeType = "small" | "medium" | "large"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyFluidGridHarness
--------------------

Type: Class

`import { SkyFluidGridHarness } from '@skyux/layout/testing';`

Harness for interacting with a fluid grid component in tests.

### Methods

#### `getGutterSize(): Promise<string>`

Gets the gutter size for the grid.

#### Returns

`Promise<string>`

#### `getRows(): Promise<SkyRowHarness[]>`

Gets all of the rows in the grid.

#### Returns

`Promise<SkyRowHarness[]>`

#### `hasMargin(): Promise<boolean>`

Whether the fluid grid has margin enabled.

#### Returns

`Promise<boolean>`

#### `SkyFluidGridHarness.with(filters: SkyFluidGridHarnessFilters): HarnessPredicate<SkyFluidGridHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFluidGridHarness` that meets certain criteria

#### Parameters

##### `filters: SkyFluidGridHarnessFilters`

#### Returns

`HarnessPredicate<SkyFluidGridHarness>`

 SkyFluidGridHarnessFilters
---------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFluidGridHarness` instances.

    interface SkyFluidGridHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyRowHarness
--------------

Type: Class

`import { SkyRowHarness } from '@skyux/layout/testing';`

Harness for interacting with a fluid grid column component in tests.

### Methods

#### `getColumnOrder(): Promise<string>`

Gets the ordering of the columns in the row.

#### Returns

`Promise<string>`

#### `getColumns(): Promise<SkyColumnHarness[]>`

Gets all of the columns in the row.

#### Returns

`Promise<SkyColumnHarness[]>`

#### `SkyRowHarness.with(filters: SkyRowHarnessFilters): HarnessPredicate<SkyRowHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyRowHarness` that meets certain criteria

#### Parameters

##### `filters: SkyRowHarnessFilters`

#### Returns

`HarnessPredicate<SkyRowHarness>`

 SkyRowHarnessFilters
---------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyRowHarness` instances.

    interface SkyRowHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyColumnHarness
-----------------

Type: Class

`import { SkyColumnHarness } from '@skyux/layout/testing';`

Harness for interacting with a fluid grid column component in tests.

### Methods

#### `getLargeSize(): Promise<number>`

Gets the size of the column in a Large responsive context.

#### Returns

`Promise<number>`

#### `getMediumSize(): Promise<number>`

Gets the size of the column in a Medium responsive context.

#### Returns

`Promise<number>`

#### `getSmallSize(): Promise<number>`

Gets the size of the column in a Small responsive context.

#### Returns

`Promise<number>`

#### `getXSmallSize(): Promise<number>`

Gets the size of the column in an XSmall responsive context.

#### Returns

`Promise<number>`

#### `SkyColumnHarness.with(filters: SkyColumnHarnessFilters): HarnessPredicate<SkyColumnHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyColumnHarness` that meets certain criteria

#### Parameters

##### `filters: SkyColumnHarnessFilters`

#### Returns

`HarnessPredicate<SkyColumnHarness>`

 SkyColumnHarnessFilters
------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyColumnHarness` instances.

    interface SkyColumnHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Testing

                  Skip to Main Content

 Fluid grid
==========

The fluid grid component provides a responsive 12-column layout to organize content for all device sizes.

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)
*   [Page design](/skyux/design/guidelines/page-layouts.md)
*   [Spacing](/skyux/design/styles/spacing.md)

### Styles

*   [Responsiveness](/skyux/design/styles/responsiveness.md)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/fluid-grid/fluid-grid.module.ts#L13) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyFluidGridModule
-------------------

Type: Module

`import { SkyFluidGridModule } from '@skyux/layout';`

 SkyFluidGridComponent
----------------------

Type: Component

Selector: `sky-fluid-grid`

Wraps the fluid grid to ensure proper spacing. Without the wrapper, the alignment, padding, and margins do not behave as expected.

### Inputs

#### `disableMargin: boolean | undefined`

Disables the outer left and right margin of the fluid grid container.

Default: `false`

#### `gutterSize: SkyFluidGridGutterSizeType`

The type that defines the size of the padding between columns.

Default: `"large"`

 SkyRowComponent
----------------

Type: Component

Selector: `sky-row`

Displays a row within the `sky-fluid-grid` wrapper. Previously, you could display a row without a wrapper, but we no longer officially support that option.

### Inputs

#### `reverseColumnOrder: boolean | undefined`

Whether to reverse the display order for columns in the row.

Default: `false`

 SkyColumnComponent
-------------------

Type: Component

Selector: `sky-column`

Displays a column within a row of the fluid grid.

### Inputs

#### `screenLarge: number | undefined`

The number of columns (1-12) on large screens (more than 1200px). If you do not specify a value, the column inherits the `screenMedium` value.

#### `screenMedium: number | undefined`

The number of columns (1-12) on medium screens (992-1199px). If you do not specify a value, the column inherits the `screenSmall` value.

#### `screenSmall: number | undefined`

The number of columns (1-12) on small screens (768-991px). If you do not specify a value, the column inherits the `screenXSmall` value.

#### `screenXSmall: number`

The number of columns (1-12) on extra-small screens (less than 768px). If you do not specify a value, the fluid grid displays the column at the full width of the screen.

Default: `12`

 SkyFluidGridGutterSizeType
---------------------------

Type: Type alias

    type SkyFluidGridGutterSizeType = "small" | "medium" | "large"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyFluidGridHarness
--------------------

Type: Class

`import { SkyFluidGridHarness } from '@skyux/layout/testing';`

Harness for interacting with a fluid grid component in tests.

### Methods

#### `getGutterSize(): Promise<string>`

Gets the gutter size for the grid.

#### Returns

`Promise<string>`

#### `getRows(): Promise<SkyRowHarness[]>`

Gets all of the rows in the grid.

#### Returns

`Promise<SkyRowHarness[]>`

#### `hasMargin(): Promise<boolean>`

Whether the fluid grid has margin enabled.

#### Returns

`Promise<boolean>`

#### `SkyFluidGridHarness.with(filters: SkyFluidGridHarnessFilters): HarnessPredicate<SkyFluidGridHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFluidGridHarness` that meets certain criteria

#### Parameters

##### `filters: SkyFluidGridHarnessFilters`

#### Returns

`HarnessPredicate<SkyFluidGridHarness>`

 SkyFluidGridHarnessFilters
---------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFluidGridHarness` instances.

    interface SkyFluidGridHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyRowHarness
--------------

Type: Class

`import { SkyRowHarness } from '@skyux/layout/testing';`

Harness for interacting with a fluid grid column component in tests.

### Methods

#### `getColumnOrder(): Promise<string>`

Gets the ordering of the columns in the row.

#### Returns

`Promise<string>`

#### `getColumns(): Promise<SkyColumnHarness[]>`

Gets all of the columns in the row.

#### Returns

`Promise<SkyColumnHarness[]>`

#### `SkyRowHarness.with(filters: SkyRowHarnessFilters): HarnessPredicate<SkyRowHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyRowHarness` that meets certain criteria

#### Parameters

##### `filters: SkyRowHarnessFilters`

#### Returns

`HarnessPredicate<SkyRowHarness>`

 SkyRowHarnessFilters
---------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyRowHarness` instances.

    interface SkyRowHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyColumnHarness
-----------------

Type: Class

`import { SkyColumnHarness } from '@skyux/layout/testing';`

Harness for interacting with a fluid grid column component in tests.

### Methods

#### `getLargeSize(): Promise<number>`

Gets the size of the column in a Large responsive context.

#### Returns

`Promise<number>`

#### `getMediumSize(): Promise<number>`

Gets the size of the column in a Medium responsive context.

#### Returns

`Promise<number>`

#### `getSmallSize(): Promise<number>`

Gets the size of the column in a Small responsive context.

#### Returns

`Promise<number>`

#### `getXSmallSize(): Promise<number>`

Gets the size of the column in an XSmall responsive context.

#### Returns

`Promise<number>`

#### `SkyColumnHarness.with(filters: SkyColumnHarnessFilters): HarnessPredicate<SkyColumnHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyColumnHarness` that meets certain criteria

#### Parameters

##### `filters: SkyColumnHarnessFilters`

#### Returns

`HarnessPredicate<SkyColumnHarness>`

 SkyColumnHarnessFilters
------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyColumnHarness` instances.

    interface SkyColumnHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.