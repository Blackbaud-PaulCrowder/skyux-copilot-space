# Design

                  Skip to Main Content

 Description list
================

Description lists display scannable data that pair terms with descriptions.

 Usage
------

### Use when

Use description lists to display sets of simple data that are easy to scan and where the relationships between terms and descriptions are easy to understand.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-1.cd9d25d4a6ff67708b3ad75201a39925.png)

Do use description lists to let users scan term-description pairs.

Use description lists with unordered lists to associate terms with multiple descriptions. Use line breaks or comma-separated values depending on the layout and context.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-2.afa3ae7a2e58335c03ea20c3aa99a351.png)

Do use unordered lists with line breaks where easy scanning is important.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-2-5.ae4dc162d49ae7d3ec96c8a109e88f20.png)

Do use unordered lists with commas where space is limited and scanning is less important.

Use description lists in `longDescription` mode to display glossaries or other data where the descriptions are complete sentences or longer.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-3.0cc3ac4cda974ca8558b19dad3af71bc.png)

Do use long-description lists when descriptions are complete sentences.

### Don't use when

Don't use description lists to highlight important data that the information hierarchy should emphasize. Use [key info](/skyux/components/key-info.md) or other methods [to call out information](/skyux/design/guidelines/call-out-info.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-4.44fa2b31fc7dbf8e6335b187afab4015.png)

Don't use description lists to make important information stand out.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-5.3dafa166f4532af8d6f95fd8d336d0e1.png)

Do use key info to highlight important information.

Don't use description lists when users can understand data based on its context and don't need a label.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-6.5408d327ec54dc2d7609ba534aac4ab5.png)

Don't use description lists when labels are unnecessary because of context.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-7.badaa4135e0081acd99f91e2ed97738c.png)

Do use plain text values when labels are implied or obvious from context.

 Anatomy
--------

1

Term

2

Description

3

Help inline button (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-anatomy.47b57e315dba5ce15e155968e0ed3796.png)

 Options
--------

### Help inline button

When you need to supplement a description list term with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the term to invoke contextual user assistance.

 Behavior and states
--------------------

### Responsiveness (horizontal lists)

Horizontal description lists respond to the width of their containers. When containers hit the xs breakpoint, lists collapse into 2 columns within an evenly spaced grid. If containers narrow to a point where 2 columns no longer fit, definition lists further collapse into 1 column.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-1.2aa51f84b6d5e9318498d19645f743aa.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-2.483a627c8990dacf537722b94b48760a.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-3.b4f1d59c18f61239a6240b30de35ce89.png)

### Responsiveness (long-description lists)

In long-description lists, the components respond to the width of their containers by wrapping text or stacking term-description pairs when appropriate.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-4.7c3bd00521df4b6608d6f62a5633dc1c.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-5.2fe43d9b5b07f13a1f73e3e7ad639ec8.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-6.577b737ee2014bbc4271def28f89588a.png)

 Content
--------

Don't use colons or other punctuation after description list terms.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-content-1.173ff0be49590c56d9073ac7bc281bfa.png)

Don't use unnecessary punctuation after terms.

 Layout
-------

### Horizontal lists

Use `horizontal` mode to display up to 6 term-description pairs in description lists that stand alone.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-layout-1.861e6daa4995571dbbefe1cae667c5c9.png)

Do use horizontal lists to arrange term-description pairs horizontally with even spacing between them.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-layout-2.4fd29add38eeb19a950037cc0a960266.png)

Don't use fluid grids to arrange term-description pairs horizontally. This can cause uneven spacing and excess space between items.

### Vertical lists

Use `vertical` mode to make scanning easier when containers include multiple description lists or when description lists are combined with other content. Use a [fluid grid](/skyux/components/fluid-grid.md) to arrange multiple description lists in a container.

Use descriptive headings to make scanning easier.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-layout-3.cd2bee08af2fa3d146c2701cb62324b7.png)

Use vertical lists and a fluid grid for multiple description lists in a container.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-layout-4.5d69dc437e43b6188954bf3fa373d037.png)

Don't use horizontal lists for multiple description lists in a container.

 Related information
--------------------

### Components

*   [Fluid grid](/skyux/components/fluid-grid.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Key info](/skyux/components/key-info.md)

### Guidelines

*   [Call out information](/skyux/design/guidelines/call-out-info.md)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/description-list/description-list.module.ts#L36) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyDescriptionListModule
-------------------------

Type: Module

`import { SkyDescriptionListModule } from '@skyux/layout';`

 SkyDescriptionListComponent
----------------------------

Type: Component

Selector: `sky-description-list`

Creates a description list to display term-description pairs.

### Inputs

#### `defaultDescription: string`

The default description to display when no description is provided for a term-description pair.

Default: `"None found"`

#### `listItemWidth: string | undefined`

The width of term-description pairs when `mode` is set to `"horizontal"`. By default, the width is responsive based on the width of the container element.

#### `mode: SkyDescriptionListModeType`

How to display term-description pairs within the description list.

Default: `"vertical"`

 SkyDescriptionListContentComponent
-----------------------------------

Type: Component

Selector: `sky-description-list-content`

Wraps the term-description pairs in the description list.

### Inputs

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified, a [help inline](/skyux/components/help-inline.md) button is placed beside the description list content label. Clicking the button invokes global help as configured by the application.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified, a [help inline](/skyux/components/help-inline.md) button is added to the description list content. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

 SkyDescriptionListDescriptionComponent
---------------------------------------

Type: Component

Selector: `sky-description-list-description`

Specifies the description in a term-description pair.

 SkyDescriptionListTermComponent
--------------------------------

Type: Component

Selector: `sky-description-list-term`

Specifies the term in a term-description pair. To display a help button beside the term, include a help button element in the sky-description-list-term element and a sky-control-help CSS class on that element.

 SkyDescriptionListModeType
---------------------------

Type: Type alias

How to display the term-description pairs within a description list.

    type SkyDescriptionListModeType = "horizontal" | "longDescription" | "vertical"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyDescriptionListHarness
--------------------------

Type: Class

`import { SkyDescriptionListHarness } from '@skyux/layout/testing';`

Harness for interacting with a description list component in tests.

### Methods

#### `getContent(): Promise<SkyDescriptionListContentHarness[]>`

Gets the description list content items.

#### Returns

`Promise<SkyDescriptionListContentHarness[]>`

#### `getMode(): Promise<SkyDescriptionListModeType>`

Gets the mode of the description list.

#### Returns

`Promise<SkyDescriptionListModeType>`

#### `SkyDescriptionListHarness.with(filters: SkyDescriptionListHarnessFilters): HarnessPredicate<SkyDescriptionListHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyDescriptionListHarness` that meets certain criteria

#### Parameters

##### `filters: SkyDescriptionListHarnessFilters`

#### Returns

`HarnessPredicate<SkyDescriptionListHarness>`

 SkyDescriptionListHarnessFilters
---------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDescriptionListHarness` instances.

    interface SkyDescriptionListHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyDescriptionListContentHarness
---------------------------------

Type: Class

`import { SkyDescriptionListContentHarness } from '@skyux/layout/testing';`

Harness for interacting with a description list content component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getDescriptionText(): Promise<string>`

Gets the description component text.

#### Returns

`Promise<string>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getTermText(): Promise<string>`

Gets the term component text.

#### Returns

`Promise<string>`

# Development

                  Skip to Main Content

 Description list
================

Description lists display scannable data that pair terms with descriptions.

 Usage
------

### Use when

Use description lists to display sets of simple data that are easy to scan and where the relationships between terms and descriptions are easy to understand.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-1.cd9d25d4a6ff67708b3ad75201a39925.png)

Do use description lists to let users scan term-description pairs.

Use description lists with unordered lists to associate terms with multiple descriptions. Use line breaks or comma-separated values depending on the layout and context.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-2.afa3ae7a2e58335c03ea20c3aa99a351.png)

Do use unordered lists with line breaks where easy scanning is important.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-2-5.ae4dc162d49ae7d3ec96c8a109e88f20.png)

Do use unordered lists with commas where space is limited and scanning is less important.

Use description lists in `longDescription` mode to display glossaries or other data where the descriptions are complete sentences or longer.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-3.0cc3ac4cda974ca8558b19dad3af71bc.png)

Do use long-description lists when descriptions are complete sentences.

### Don't use when

Don't use description lists to highlight important data that the information hierarchy should emphasize. Use [key info](/skyux/components/key-info.md) or other methods [to call out information](/skyux/design/guidelines/call-out-info.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-4.44fa2b31fc7dbf8e6335b187afab4015.png)

Don't use description lists to make important information stand out.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-5.3dafa166f4532af8d6f95fd8d336d0e1.png)

Do use key info to highlight important information.

Don't use description lists when users can understand data based on its context and don't need a label.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-6.5408d327ec54dc2d7609ba534aac4ab5.png)

Don't use description lists when labels are unnecessary because of context.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-7.badaa4135e0081acd99f91e2ed97738c.png)

Do use plain text values when labels are implied or obvious from context.

 Anatomy
--------

1

Term

2

Description

3

Help inline button (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-anatomy.47b57e315dba5ce15e155968e0ed3796.png)

 Options
--------

### Help inline button

When you need to supplement a description list term with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the term to invoke contextual user assistance.

 Behavior and states
--------------------

### Responsiveness (horizontal lists)

Horizontal description lists respond to the width of their containers. When containers hit the xs breakpoint, lists collapse into 2 columns within an evenly spaced grid. If containers narrow to a point where 2 columns no longer fit, definition lists further collapse into 1 column.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-1.2aa51f84b6d5e9318498d19645f743aa.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-2.483a627c8990dacf537722b94b48760a.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-3.b4f1d59c18f61239a6240b30de35ce89.png)

### Responsiveness (long-description lists)

In long-description lists, the components respond to the width of their containers by wrapping text or stacking term-description pairs when appropriate.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-4.7c3bd00521df4b6608d6f62a5633dc1c.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-5.2fe43d9b5b07f13a1f73e3e7ad639ec8.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-6.577b737ee2014bbc4271def28f89588a.png)

 Content
--------

Don't use colons or other punctuation after description list terms.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-content-1.173ff0be49590c56d9073ac7bc281bfa.png)

Don't use unnecessary punctuation after terms.

 Layout
-------

### Horizontal lists

Use `horizontal` mode to display up to 6 term-description pairs in description lists that stand alone.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-layout-1.861e6daa4995571dbbefe1cae667c5c9.png)

Do use horizontal lists to arrange term-description pairs horizontally with even spacing between them.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-layout-2.4fd29add38eeb19a950037cc0a960266.png)

Don't use fluid grids to arrange term-description pairs horizontally. This can cause uneven spacing and excess space between items.

### Vertical lists

Use `vertical` mode to make scanning easier when containers include multiple description lists or when description lists are combined with other content. Use a [fluid grid](/skyux/components/fluid-grid.md) to arrange multiple description lists in a container.

Use descriptive headings to make scanning easier.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-layout-3.cd2bee08af2fa3d146c2701cb62324b7.png)

Use vertical lists and a fluid grid for multiple description lists in a container.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-layout-4.5d69dc437e43b6188954bf3fa373d037.png)

Don't use horizontal lists for multiple description lists in a container.

 Related information
--------------------

### Components

*   [Fluid grid](/skyux/components/fluid-grid.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Key info](/skyux/components/key-info.md)

### Guidelines

*   [Call out information](/skyux/design/guidelines/call-out-info.md)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/description-list/description-list.module.ts#L36) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyDescriptionListModule
-------------------------

Type: Module

`import { SkyDescriptionListModule } from '@skyux/layout';`

 SkyDescriptionListComponent
----------------------------

Type: Component

Selector: `sky-description-list`

Creates a description list to display term-description pairs.

### Inputs

#### `defaultDescription: string`

The default description to display when no description is provided for a term-description pair.

Default: `"None found"`

#### `listItemWidth: string | undefined`

The width of term-description pairs when `mode` is set to `"horizontal"`. By default, the width is responsive based on the width of the container element.

#### `mode: SkyDescriptionListModeType`

How to display term-description pairs within the description list.

Default: `"vertical"`

 SkyDescriptionListContentComponent
-----------------------------------

Type: Component

Selector: `sky-description-list-content`

Wraps the term-description pairs in the description list.

### Inputs

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified, a [help inline](/skyux/components/help-inline.md) button is placed beside the description list content label. Clicking the button invokes global help as configured by the application.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified, a [help inline](/skyux/components/help-inline.md) button is added to the description list content. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

 SkyDescriptionListDescriptionComponent
---------------------------------------

Type: Component

Selector: `sky-description-list-description`

Specifies the description in a term-description pair.

 SkyDescriptionListTermComponent
--------------------------------

Type: Component

Selector: `sky-description-list-term`

Specifies the term in a term-description pair. To display a help button beside the term, include a help button element in the sky-description-list-term element and a sky-control-help CSS class on that element.

 SkyDescriptionListModeType
---------------------------

Type: Type alias

How to display the term-description pairs within a description list.

    type SkyDescriptionListModeType = "horizontal" | "longDescription" | "vertical"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyDescriptionListHarness
--------------------------

Type: Class

`import { SkyDescriptionListHarness } from '@skyux/layout/testing';`

Harness for interacting with a description list component in tests.

### Methods

#### `getContent(): Promise<SkyDescriptionListContentHarness[]>`

Gets the description list content items.

#### Returns

`Promise<SkyDescriptionListContentHarness[]>`

#### `getMode(): Promise<SkyDescriptionListModeType>`

Gets the mode of the description list.

#### Returns

`Promise<SkyDescriptionListModeType>`

#### `SkyDescriptionListHarness.with(filters: SkyDescriptionListHarnessFilters): HarnessPredicate<SkyDescriptionListHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyDescriptionListHarness` that meets certain criteria

#### Parameters

##### `filters: SkyDescriptionListHarnessFilters`

#### Returns

`HarnessPredicate<SkyDescriptionListHarness>`

 SkyDescriptionListHarnessFilters
---------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDescriptionListHarness` instances.

    interface SkyDescriptionListHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyDescriptionListContentHarness
---------------------------------

Type: Class

`import { SkyDescriptionListContentHarness } from '@skyux/layout/testing';`

Harness for interacting with a description list content component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getDescriptionText(): Promise<string>`

Gets the description component text.

#### Returns

`Promise<string>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getTermText(): Promise<string>`

Gets the term component text.

#### Returns

`Promise<string>`

# Examples

                    Skip to Main Content

 Description list
================

Description lists display scannable data that pair terms with descriptions.Usage
------

### Use when

Use description lists to display sets of simple data that are easy to scan and where the relationships between terms and descriptions are easy to understand.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-1.cd9d25d4a6ff67708b3ad75201a39925.png)

Do use description lists to let users scan term-description pairs.

Use description lists with unordered lists to associate terms with multiple descriptions. Use line breaks or comma-separated values depending on the layout and context.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-2.afa3ae7a2e58335c03ea20c3aa99a351.png)

Do use unordered lists with line breaks where easy scanning is important.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-2-5.ae4dc162d49ae7d3ec96c8a109e88f20.png)

Do use unordered lists with commas where space is limited and scanning is less important.

Use description lists in `longDescription` mode to display glossaries or other data where the descriptions are complete sentences or longer.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-3.0cc3ac4cda974ca8558b19dad3af71bc.png)

Do use long-description lists when descriptions are complete sentences.

### Don't use when

Don't use description lists to highlight important data that the information hierarchy should emphasize. Use [key info](/skyux/components/key-info.md) or other methods [to call out information](/skyux/design/guidelines/call-out-info.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-4.44fa2b31fc7dbf8e6335b187afab4015.png)

Don't use description lists to make important information stand out.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-5.3dafa166f4532af8d6f95fd8d336d0e1.png)

Do use key info to highlight important information.

Don't use description lists when users can understand data based on its context and don't need a label.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-6.5408d327ec54dc2d7609ba534aac4ab5.png)

Don't use description lists when labels are unnecessary because of context.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-7.badaa4135e0081acd99f91e2ed97738c.png)

Do use plain text values when labels are implied or obvious from context.

 Anatomy
--------

1

Term

2

Description

3

Help inline button (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-anatomy.47b57e315dba5ce15e155968e0ed3796.png)

 Options
--------

### Help inline button

When you need to supplement a description list term with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the term to invoke contextual user assistance.

 Behavior and states
--------------------

### Responsiveness (horizontal lists)

Horizontal description lists respond to the width of their containers. When containers hit the xs breakpoint, lists collapse into 2 columns within an evenly spaced grid. If containers narrow to a point where 2 columns no longer fit, definition lists further collapse into 1 column.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-1.2aa51f84b6d5e9318498d19645f743aa.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-2.483a627c8990dacf537722b94b48760a.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-3.b4f1d59c18f61239a6240b30de35ce89.png)

### Responsiveness (long-description lists)

In long-description lists, the components respond to the width of their containers by wrapping text or stacking term-description pairs when appropriate.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-4.7c3bd00521df4b6608d6f62a5633dc1c.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-5.2fe43d9b5b07f13a1f73e3e7ad639ec8.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-6.577b737ee2014bbc4271def28f89588a.png)

 Content
--------

Don't use colons or other punctuation after description list terms.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-content-1.173ff0be49590c56d9073ac7bc281bfa.png)

Don't use unnecessary punctuation after terms.

 Layout
-------

### Horizontal lists

Use `horizontal` mode to display up to 6 term-description pairs in description lists that stand alone.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-layout-1.861e6daa4995571dbbefe1cae667c5c9.png)

Do use horizontal lists to arrange term-description pairs horizontally with even spacing between them.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-layout-2.4fd29add38eeb19a950037cc0a960266.png)

Don't use fluid grids to arrange term-description pairs horizontally. This can cause uneven spacing and excess space between items.

### Vertical lists

Use `vertical` mode to make scanning easier when containers include multiple description lists or when description lists are combined with other content. Use a [fluid grid](/skyux/components/fluid-grid.md) to arrange multiple description lists in a container.

Use descriptive headings to make scanning easier.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-layout-3.cd2bee08af2fa3d146c2701cb62324b7.png)

Use vertical lists and a fluid grid for multiple description lists in a container.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-layout-4.5d69dc437e43b6188954bf3fa373d037.png)

Don't use horizontal lists for multiple description lists in a container.

 Related information
--------------------

### Components

*   [Fluid grid](/skyux/components/fluid-grid.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Key info](/skyux/components/key-info.md)

### Guidelines

*   [Call out information](/skyux/design/guidelines/call-out-info.md)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/description-list/description-list.module.ts#L36) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyDescriptionListModule
-------------------------

Type: Module

`import { SkyDescriptionListModule } from '@skyux/layout';`

 SkyDescriptionListComponent
----------------------------

Type: Component

Selector: `sky-description-list`

Creates a description list to display term-description pairs.

### Inputs

#### `defaultDescription: string`

The default description to display when no description is provided for a term-description pair.

Default: `"None found"`

#### `listItemWidth: string | undefined`

The width of term-description pairs when `mode` is set to `"horizontal"`. By default, the width is responsive based on the width of the container element.

#### `mode: SkyDescriptionListModeType`

How to display term-description pairs within the description list.

Default: `"vertical"`

 SkyDescriptionListContentComponent
-----------------------------------

Type: Component

Selector: `sky-description-list-content`

Wraps the term-description pairs in the description list.

### Inputs

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified, a [help inline](/skyux/components/help-inline.md) button is placed beside the description list content label. Clicking the button invokes global help as configured by the application.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified, a [help inline](/skyux/components/help-inline.md) button is added to the description list content. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

 SkyDescriptionListDescriptionComponent
---------------------------------------

Type: Component

Selector: `sky-description-list-description`

Specifies the description in a term-description pair.

 SkyDescriptionListTermComponent
--------------------------------

Type: Component

Selector: `sky-description-list-term`

Specifies the term in a term-description pair. To display a help button beside the term, include a help button element in the sky-description-list-term element and a sky-control-help CSS class on that element.

 SkyDescriptionListModeType
---------------------------

Type: Type alias

How to display the term-description pairs within a description list.

    type SkyDescriptionListModeType = "horizontal" | "longDescription" | "vertical"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyDescriptionListHarness
--------------------------

Type: Class

`import { SkyDescriptionListHarness } from '@skyux/layout/testing';`

Harness for interacting with a description list component in tests.

### Methods

#### `getContent(): Promise<SkyDescriptionListContentHarness[]>`

Gets the description list content items.

#### Returns

`Promise<SkyDescriptionListContentHarness[]>`

#### `getMode(): Promise<SkyDescriptionListModeType>`

Gets the mode of the description list.

#### Returns

`Promise<SkyDescriptionListModeType>`

#### `SkyDescriptionListHarness.with(filters: SkyDescriptionListHarnessFilters): HarnessPredicate<SkyDescriptionListHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyDescriptionListHarness` that meets certain criteria

#### Parameters

##### `filters: SkyDescriptionListHarnessFilters`

#### Returns

`HarnessPredicate<SkyDescriptionListHarness>`

 SkyDescriptionListHarnessFilters
---------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDescriptionListHarness` instances.

    interface SkyDescriptionListHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyDescriptionListContentHarness
---------------------------------

Type: Class

`import { SkyDescriptionListContentHarness } from '@skyux/layout/testing';`

Harness for interacting with a description list content component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getDescriptionText(): Promise<string>`

Gets the description component text.

#### Returns

`Promise<string>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getTermText(): Promise<string>`

Gets the term component text.

#### Returns

`Promise<string>`

### Horizontal mode

Edit in StackBlitz

College

Humanities and Social Sciences None found.

Department

Anthropology None found.

AdvisorShow help content for

Cathy Green None found.

Class year

2024 None found.

Show code

Copy

    <sky-description-list mode="horizontal">
      @for (item of items; track item) {
        <sky-description-list-content [helpPopoverContent]="item.helpText">
          <sky-description-list-term>
            {{ item.term }}
          </sky-description-list-term>
          <sky-description-list-description>
            {{ item.description }}
          </sky-description-list-description>
        </sky-description-list-content>
      }
    </sky-description-list>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyHelpTestingModule } from '@skyux/core/testing';
    import { SkyDescriptionListHarness } from '@skyux/layout/testing';
    
    import { LayoutDescriptionListHorizontalExampleComponent } from './example.component';
    
    describe('Horizontal description list', () => {
      async function setupTest(): Promise<{
        descriptionListHarness: SkyDescriptionListHarness;
        fixture: ComponentFixture<LayoutDescriptionListHorizontalExampleComponent>;
      }> {
        await TestBed.configureTestingModule({
          imports: [
            LayoutDescriptionListHorizontalExampleComponent,
            SkyHelpTestingModule,
            NoopAnimationsModule,
          ],
        }).compileComponents();
    
        const fixture = TestBed.createComponent(
          LayoutDescriptionListHorizontalExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    
        const descriptionListHarness: SkyDescriptionListHarness =
          await loader.getHarness(SkyDescriptionListHarness);
    
        return { descriptionListHarness, fixture };
      }
    
      it('should set up the component', async () => {
        const { descriptionListHarness, fixture } = await setupTest();
    
        await expectAsync(descriptionListHarness.getMode()).toBeResolvedTo(
          'horizontal',
        );
    
        const content = await descriptionListHarness.getContent();
    
        expect(content.length).toBe(4);
    
        await expectAsync(content[0].getTermText()).toBeResolvedTo('College');
        await expectAsync(content[0].getDescriptionText()).toBeResolvedTo(
          'Humanities and Social Sciences',
        );
    
        await content[2].clickHelpInline();
        fixture.detectChanges();
        await fixture.whenStable();
        await expectAsync(content[2].getHelpPopoverContent()).toBeResolvedTo(
          'The faculty member who advises the student.',
        );
      });
    });

Copy

    import { Component } from '@angular/core';
    import { SkyDescriptionListModule } from '@skyux/layout';
    
    /**
     * @title Horizontal mode
     */
    @Component({
      selector: 'app-layout-description-list-horizontal-example',
      templateUrl: './example.component.html',
      imports: [SkyDescriptionListModule],
    })
    export class LayoutDescriptionListHorizontalExampleComponent {
      protected items: { term: string; description: string; helpText?: string }[] =
        [
          {
            term: 'College',
            description: 'Humanities and Social Sciences',
          },
          {
            term: 'Department',
            description: 'Anthropology',
          },
          {
            term: 'Advisor',
            description: 'Cathy Green',
            helpText: 'The faculty member who advises the student.',
          },
          {
            term: 'Class year',
            description: '2024',
          },
        ];
    }
### Vertical mode

Edit in StackBlitz

College

Humanities and Social Sciences None found.

Department

Anthropology None found.

AdvisorShow help content for

Cathy Green None found.

Class year

2024 None found.

Show code

Copy

    <sky-description-list mode="vertical">
      @for (item of items; track item) {
        <sky-description-list-content [helpPopoverContent]="item.helpText">
          <sky-description-list-term>
            {{ item.term }}
          </sky-description-list-term>
          <sky-description-list-description>
            {{ item.description }}
          </sky-description-list-description>
        </sky-description-list-content>
      }
    </sky-description-list>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyHelpTestingModule } from '@skyux/core/testing';
    import { SkyDescriptionListHarness } from '@skyux/layout/testing';
    
    import { LayoutDescriptionListVerticalExampleComponent } from './example.component';
    
    describe('Vertical description list', () => {
      async function setupTest(): Promise<{
        descriptionListHarness: SkyDescriptionListHarness;
        fixture: ComponentFixture<LayoutDescriptionListVerticalExampleComponent>;
      }> {
        await TestBed.configureTestingModule({
          imports: [
            LayoutDescriptionListVerticalExampleComponent,
            SkyHelpTestingModule,
            NoopAnimationsModule,
          ],
        }).compileComponents();
    
        const fixture = TestBed.createComponent(
          LayoutDescriptionListVerticalExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    
        const descriptionListHarness: SkyDescriptionListHarness =
          await loader.getHarness(SkyDescriptionListHarness);
    
        return { descriptionListHarness, fixture };
      }
    
      it('should set up the component', async () => {
        const { descriptionListHarness, fixture } = await setupTest();
    
        await expectAsync(descriptionListHarness.getMode()).toBeResolvedTo(
          'vertical',
        );
    
        const content = await descriptionListHarness.getContent();
    
        expect(content.length).toBe(4);
    
        await expectAsync(content[0].getTermText()).toBeResolvedTo('College');
        await expectAsync(content[0].getDescriptionText()).toBeResolvedTo(
          'Humanities and Social Sciences',
        );
    
        await content[2].clickHelpInline();
        fixture.detectChanges();
        await fixture.whenStable();
        await expectAsync(content[2].getHelpPopoverContent()).toBeResolvedTo(
          'The faculty member who advises the student.',
        );
      });
    });

Copy

    import { Component } from '@angular/core';
    import { SkyDescriptionListModule } from '@skyux/layout';
    
    /**
     * @title Vertical mode
     */
    @Component({
      selector: 'app-layout-description-list-vertical-example',
      templateUrl: './example.component.html',
      imports: [SkyDescriptionListModule],
    })
    export class LayoutDescriptionListVerticalExampleComponent {
      protected items: { term: string; description: string; helpText?: string }[] =
        [
          {
            term: 'College',
            description: 'Humanities and Social Sciences',
          },
          {
            term: 'Department',
            description: 'Anthropology',
          },
          {
            term: 'Advisor',
            description: 'Cathy Green',
            helpText: 'The faculty member who advises the student.',
          },
          {
            term: 'Class year',
            description: '2024',
          },
        ];
    }
### Long-description mode

Edit in StackBlitz

Good Health and Well-being

Ensure healthy lives and promote well-being for all at all ages. None found.

Quality Education

Ensure inclusive and equitable quality education and promote lifelong learning opportunities for all. None found.

Gender Equity

Achieve gender equality and empower all women and girls. None found.

Show code

Copy

    <sky-description-list mode="longDescription">
      @for (item of items; track item) {
        <sky-description-list-content>
          <sky-description-list-term>
            {{ item.term }}
          </sky-description-list-term>
          <sky-description-list-description>
            {{ item.description }}
          </sky-description-list-description>
        </sky-description-list-content>
      }
    </sky-description-list>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyHelpTestingModule } from '@skyux/core/testing';
    import { SkyDescriptionListHarness } from '@skyux/layout/testing';
    
    import { LayoutDescriptionListLongDescriptionExampleComponent } from './example.component';
    
    describe('Long description list', () => {
      async function setupTest(): Promise<{
        descriptionListHarness: SkyDescriptionListHarness;
        fixture: ComponentFixture<LayoutDescriptionListLongDescriptionExampleComponent>;
      }> {
        await TestBed.configureTestingModule({
          imports: [
            LayoutDescriptionListLongDescriptionExampleComponent,
            SkyHelpTestingModule,
            NoopAnimationsModule,
          ],
        }).compileComponents();
    
        const fixture = TestBed.createComponent(
          LayoutDescriptionListLongDescriptionExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    
        const descriptionListHarness: SkyDescriptionListHarness =
          await loader.getHarness(SkyDescriptionListHarness);
    
        return { descriptionListHarness, fixture };
      }
    
      it('should set up the component', async () => {
        const { descriptionListHarness } = await setupTest();
    
        await expectAsync(descriptionListHarness.getMode()).toBeResolvedTo(
          'longDescription',
        );
    
        const content = await descriptionListHarness.getContent();
    
        expect(content.length).toBe(3);
    
        await expectAsync(content[0].getTermText()).toBeResolvedTo(
          'Good Health and Well-being',
        );
        await expectAsync(content[0].getDescriptionText()).toBeResolvedTo(
          'Ensure healthy lives and promote well-being for all at all ages.',
        );
      });
    });

Copy

    import { Component } from '@angular/core';
    import { SkyDescriptionListModule } from '@skyux/layout';
    
    /**
     * @title Long-description mode
     */
    @Component({
      selector: 'app-layout-description-list-long-description-example',
      templateUrl: './example.component.html',
      imports: [SkyDescriptionListModule],
    })
    export class LayoutDescriptionListLongDescriptionExampleComponent {
      protected items: { term: string; description: string }[] = [
        {
          term: 'Good Health and Well-being',
          description:
            'Ensure healthy lives and promote well-being for all at all ages.',
        },
        {
          term: 'Quality Education',
          description:
            'Ensure inclusive and equitable quality education and promote lifelong learning opportunities for all.',
        },
        {
          term: 'Gender Equity',
          description: 'Achieve gender equality and empower all women and girls.',
        },
      ];
    }
### Description list with inline help

Edit in StackBlitz

CollegeShow help content for

Humanities and Social Sciences None found.

DepartmentShow help content for

Anthropology None found.

AdvisorShow help content for

Cathy Green None found.

Class yearShow help content for

2024 None found.

Show code

Copy

    <sky-description-list mode="horizontal">
      @for (item of items; track item) {
        <sky-description-list-content [helpPopoverContent]="item.helpText">
          <sky-description-list-term>
            {{ item.term }}
            <sky-help-inline
              ariaLabel="Information about {{ item.term }}"
              class="sky-control-help"
              (actionClick)="onActionClick()"
            />
          </sky-description-list-term>
          <sky-description-list-description>
            {{ item.description }}
          </sky-description-list-description>
        </sky-description-list-content>
      }
    </sky-description-list>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyHelpTestingModule } from '@skyux/core/testing';
    import { SkyDescriptionListHarness } from '@skyux/layout/testing';
    
    import { LayoutDescriptionListInlineHelpExampleComponent } from './example.component';
    
    describe('Horizontal description list', () => {
      async function setupTest(): Promise<{
        descriptionListHarness: SkyDescriptionListHarness;
        fixture: ComponentFixture<LayoutDescriptionListInlineHelpExampleComponent>;
      }> {
        await TestBed.configureTestingModule({
          imports: [
            LayoutDescriptionListInlineHelpExampleComponent,
            SkyHelpTestingModule,
            NoopAnimationsModule,
          ],
        }).compileComponents();
    
        const fixture = TestBed.createComponent(
          LayoutDescriptionListInlineHelpExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    
        const descriptionListHarness: SkyDescriptionListHarness =
          await loader.getHarness(SkyDescriptionListHarness);
    
        return { descriptionListHarness, fixture };
      }
    
      it('should set up the component', async () => {
        const { descriptionListHarness, fixture } = await setupTest();
    
        await expectAsync(descriptionListHarness.getMode()).toBeResolvedTo(
          'horizontal',
        );
    
        const content = await descriptionListHarness.getContent();
    
        expect(content.length).toBe(4);
    
        await expectAsync(content[0].getTermText()).toBeResolvedTo('College');
        await expectAsync(content[0].getDescriptionText()).toBeResolvedTo(
          'Humanities and Social Sciences',
        );
    
        await content[2].clickHelpInline();
        fixture.detectChanges();
        await fixture.whenStable();
        await expectAsync(content[2].getHelpPopoverContent()).toBeResolvedTo(
          'The faculty member who advises the student.',
        );
      });
    });

Copy

    import { Component } from '@angular/core';
    import { SkyHelpInlineModule } from '@skyux/help-inline';
    import { SkyDescriptionListModule } from '@skyux/layout';
    
    /**
     * @title Description list with inline help
     */
    @Component({
      selector: 'app-layout-description-list-inline-help-example',
      templateUrl: './example.component.html',
      imports: [SkyDescriptionListModule, SkyHelpInlineModule],
    })
    export class LayoutDescriptionListInlineHelpExampleComponent {
      protected items: { term: string; description: string; helpText?: string }[] =
        [
          {
            term: 'College',
            description: 'Humanities and Social Sciences',
          },
          {
            term: 'Department',
            description: 'Anthropology',
          },
          {
            term: 'Advisor',
            description: 'Cathy Green',
            helpText: 'The faculty member who advises the student.',
          },
          {
            term: 'Class year',
            description: '2024',
          },
        ];
    
      protected onActionClick(): void {
        alert('Help inline button clicked!');
      }
    }
### Description list with help key

Edit in StackBlitz

CollegeShow help content for

Humanities and Social Sciences None found.

Department

Anthropology None found.

Advisor

Cathy Green None found.

Class year

2024 None found.

Show code

Copy

    <sky-description-list mode="horizontal">
      @for (item of items; track item) {
        <sky-description-list-content [helpKey]="item.helpKey">
          <sky-description-list-term>
            {{ item.term }}
          </sky-description-list-term>
          <sky-description-list-description>
            {{ item.description }}
          </sky-description-list-description>
        </sky-description-list-content>
      }
    </sky-description-list>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import {
      SkyHelpTestingController,
      SkyHelpTestingModule,
    } from '@skyux/core/testing';
    import { SkyDescriptionListHarness } from '@skyux/layout/testing';
    
    import { LayoutDescriptionListHelpKeyExampleComponent } from './example.component';
    
    describe('Help key description list', () => {
      async function setupTest(): Promise<{
        descriptionListHarness: SkyDescriptionListHarness;
        fixture: ComponentFixture<LayoutDescriptionListHelpKeyExampleComponent>;
        helpController: SkyHelpTestingController;
      }> {
        await TestBed.configureTestingModule({
          imports: [
            LayoutDescriptionListHelpKeyExampleComponent,
            SkyHelpTestingModule,
            NoopAnimationsModule,
          ],
        }).compileComponents();
    
        const fixture = TestBed.createComponent(
          LayoutDescriptionListHelpKeyExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
        const helpController = TestBed.inject(SkyHelpTestingController);
    
        const descriptionListHarness: SkyDescriptionListHarness =
          await loader.getHarness(SkyDescriptionListHarness);
    
        return { descriptionListHarness, fixture, helpController };
      }
    
      it('should set up the component', async () => {
        const { descriptionListHarness, fixture, helpController } =
          await setupTest();
    
        await expectAsync(descriptionListHarness.getMode()).toBeResolvedTo(
          'horizontal',
        );
    
        const content = await descriptionListHarness.getContent();
    
        expect(content.length).toBe(4);
    
        await expectAsync(content[0].getTermText()).toBeResolvedTo('College');
        await expectAsync(content[0].getDescriptionText()).toBeResolvedTo(
          'Humanities and Social Sciences',
        );
    
        await content[0].clickHelpInline();
        fixture.detectChanges();
        await fixture.whenStable();
    
        helpController.expectCurrentHelpKey('college-help');
      });
    });

Copy

    import { Component } from '@angular/core';
    import { SkyDescriptionListModule } from '@skyux/layout';
    
    /**
     * @title Description list with help key
     */
    @Component({
      selector: 'app-layout-description-list-help-key-example',
      templateUrl: './example.component.html',
      imports: [SkyDescriptionListModule],
    })
    export class LayoutDescriptionListHelpKeyExampleComponent {
      protected items: { term: string; description: string; helpKey?: string }[] = [
        {
          term: 'College',
          description: 'Humanities and Social Sciences',
          helpKey: 'college-help',
        },
        {
          term: 'Department',
          description: 'Anthropology',
        },
        {
          term: 'Advisor',
          description: 'Cathy Green',
        },
        {
          term: 'Class year',
          description: '2024',
        },
      ];
    }

# Testing

                  Skip to Main Content

 Description list
================

Description lists display scannable data that pair terms with descriptions.

 Usage
------

### Use when

Use description lists to display sets of simple data that are easy to scan and where the relationships between terms and descriptions are easy to understand.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-1.cd9d25d4a6ff67708b3ad75201a39925.png)

Do use description lists to let users scan term-description pairs.

Use description lists with unordered lists to associate terms with multiple descriptions. Use line breaks or comma-separated values depending on the layout and context.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-2.afa3ae7a2e58335c03ea20c3aa99a351.png)

Do use unordered lists with line breaks where easy scanning is important.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-2-5.ae4dc162d49ae7d3ec96c8a109e88f20.png)

Do use unordered lists with commas where space is limited and scanning is less important.

Use description lists in `longDescription` mode to display glossaries or other data where the descriptions are complete sentences or longer.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-3.0cc3ac4cda974ca8558b19dad3af71bc.png)

Do use long-description lists when descriptions are complete sentences.

### Don't use when

Don't use description lists to highlight important data that the information hierarchy should emphasize. Use [key info](/skyux/components/key-info.md) or other methods [to call out information](/skyux/design/guidelines/call-out-info.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-4.44fa2b31fc7dbf8e6335b187afab4015.png)

Don't use description lists to make important information stand out.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-5.3dafa166f4532af8d6f95fd8d336d0e1.png)

Do use key info to highlight important information.

Don't use description lists when users can understand data based on its context and don't need a label.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-6.5408d327ec54dc2d7609ba534aac4ab5.png)

Don't use description lists when labels are unnecessary because of context.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-usage-7.badaa4135e0081acd99f91e2ed97738c.png)

Do use plain text values when labels are implied or obvious from context.

 Anatomy
--------

1

Term

2

Description

3

Help inline button (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-anatomy.47b57e315dba5ce15e155968e0ed3796.png)

 Options
--------

### Help inline button

When you need to supplement a description list term with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the term to invoke contextual user assistance.

 Behavior and states
--------------------

### Responsiveness (horizontal lists)

Horizontal description lists respond to the width of their containers. When containers hit the xs breakpoint, lists collapse into 2 columns within an evenly spaced grid. If containers narrow to a point where 2 columns no longer fit, definition lists further collapse into 1 column.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-1.2aa51f84b6d5e9318498d19645f743aa.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-2.483a627c8990dacf537722b94b48760a.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-3.b4f1d59c18f61239a6240b30de35ce89.png)

### Responsiveness (long-description lists)

In long-description lists, the components respond to the width of their containers by wrapping text or stacking term-description pairs when appropriate.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-4.7c3bd00521df4b6608d6f62a5633dc1c.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-5.2fe43d9b5b07f13a1f73e3e7ad639ec8.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-behavior-6.577b737ee2014bbc4271def28f89588a.png)

 Content
--------

Don't use colons or other punctuation after description list terms.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-content-1.173ff0be49590c56d9073ac7bc281bfa.png)

Don't use unnecessary punctuation after terms.

 Layout
-------

### Horizontal lists

Use `horizontal` mode to display up to 6 term-description pairs in description lists that stand alone.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-layout-1.861e6daa4995571dbbefe1cae667c5c9.png)

Do use horizontal lists to arrange term-description pairs horizontally with even spacing between them.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-layout-2.4fd29add38eeb19a950037cc0a960266.png)

Don't use fluid grids to arrange term-description pairs horizontally. This can cause uneven spacing and excess space between items.

### Vertical lists

Use `vertical` mode to make scanning easier when containers include multiple description lists or when description lists are combined with other content. Use a [fluid grid](/skyux/components/fluid-grid.md) to arrange multiple description lists in a container.

Use descriptive headings to make scanning easier.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-layout-3.cd2bee08af2fa3d146c2701cb62324b7.png)

Use vertical lists and a fluid grid for multiple description lists in a container.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/description-list/description-list-layout-4.5d69dc437e43b6188954bf3fa373d037.png)

Don't use horizontal lists for multiple description lists in a container.

 Related information
--------------------

### Components

*   [Fluid grid](/skyux/components/fluid-grid.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Key info](/skyux/components/key-info.md)

### Guidelines

*   [Call out information](/skyux/design/guidelines/call-out-info.md)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/description-list/description-list.module.ts#L36) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyDescriptionListModule
-------------------------

Type: Module

`import { SkyDescriptionListModule } from '@skyux/layout';`

 SkyDescriptionListComponent
----------------------------

Type: Component

Selector: `sky-description-list`

Creates a description list to display term-description pairs.

### Inputs

#### `defaultDescription: string`

The default description to display when no description is provided for a term-description pair.

Default: `"None found"`

#### `listItemWidth: string | undefined`

The width of term-description pairs when `mode` is set to `"horizontal"`. By default, the width is responsive based on the width of the container element.

#### `mode: SkyDescriptionListModeType`

How to display term-description pairs within the description list.

Default: `"vertical"`

 SkyDescriptionListContentComponent
-----------------------------------

Type: Component

Selector: `sky-description-list-content`

Wraps the term-description pairs in the description list.

### Inputs

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified, a [help inline](/skyux/components/help-inline.md) button is placed beside the description list content label. Clicking the button invokes global help as configured by the application.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified, a [help inline](/skyux/components/help-inline.md) button is added to the description list content. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

 SkyDescriptionListDescriptionComponent
---------------------------------------

Type: Component

Selector: `sky-description-list-description`

Specifies the description in a term-description pair.

 SkyDescriptionListTermComponent
--------------------------------

Type: Component

Selector: `sky-description-list-term`

Specifies the term in a term-description pair. To display a help button beside the term, include a help button element in the sky-description-list-term element and a sky-control-help CSS class on that element.

 SkyDescriptionListModeType
---------------------------

Type: Type alias

How to display the term-description pairs within a description list.

    type SkyDescriptionListModeType = "horizontal" | "longDescription" | "vertical"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyDescriptionListHarness
--------------------------

Type: Class

`import { SkyDescriptionListHarness } from '@skyux/layout/testing';`

Harness for interacting with a description list component in tests.

### Methods

#### `getContent(): Promise<SkyDescriptionListContentHarness[]>`

Gets the description list content items.

#### Returns

`Promise<SkyDescriptionListContentHarness[]>`

#### `getMode(): Promise<SkyDescriptionListModeType>`

Gets the mode of the description list.

#### Returns

`Promise<SkyDescriptionListModeType>`

#### `SkyDescriptionListHarness.with(filters: SkyDescriptionListHarnessFilters): HarnessPredicate<SkyDescriptionListHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyDescriptionListHarness` that meets certain criteria

#### Parameters

##### `filters: SkyDescriptionListHarnessFilters`

#### Returns

`HarnessPredicate<SkyDescriptionListHarness>`

 SkyDescriptionListHarnessFilters
---------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyDescriptionListHarness` instances.

    interface SkyDescriptionListHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyDescriptionListContentHarness
---------------------------------

Type: Class

`import { SkyDescriptionListContentHarness } from '@skyux/layout/testing';`

Harness for interacting with a description list content component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getDescriptionText(): Promise<string>`

Gets the description component text.

#### Returns

`Promise<string>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getTermText(): Promise<string>`

Gets the term component text.

#### Returns

`Promise<string>`