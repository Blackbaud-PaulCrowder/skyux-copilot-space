                  

 Key info
========

The key info component highlights important summary information.

 Usage
------

### Use when

Use key info to highlight important summary information.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/key-info/key-info-usage-1.4ca5133df981810932455df8f2d46c7f.png)

Do use key info to highlight important summary information.

Use key info to show the total number of items in a list. Use the horizontal layout and place the key info at the top of the list.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/key-info/key-info-usage-2.c340f6c9461a57c27d0d7729d2398ac8.png)

Do use key info to show the total number of items in a list.

### Don't use when

Don't use key info when different data visualizations are more appropriate for large amounts of data. For example, don't group multiple key info components to track how data changes over time. Use alternative visualizations such as [data grids](/skyux/components/data-grid.md), bar charts, or line charts instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/key-info/key-info-usage-3.8a979a260f7c8fb1de19122782833725.png)

Don't use key info when other data visualizations are more appropriate.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/key-info/key-info-usage-4.12391db576c9b28d7840a8faf4f563b7.png)

Do use different visualizations for large amounts of data.

Don't use key info when data doesn't require user attention or doesn't drive user action. Use [description lists](/skyux/components/description-list.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/key-info/key-info-usage-5.2bfd592e3c310e043337bcbc9441be59.png)

Don't use key info for data that isn't important summary information.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/key-info/key-info-usage-6.a2ba2b1f02034fef59baa97ec4a76ea8.png)

Do use description lists for content that doesn't require user attention.

 Anatomy
--------

1

Value

2

Label

3

Help inline button (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/key-info/key-info-anatomy.c25d5419f0904618d9f57f98a001183c.png)

 Options
--------

### Layout

Use the default vertical layout with the label under the value in most situations.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/key-info/key-info-vertical-layout.65a7566287387811f55f3e7acdc27d48.png)

Use the horizontal layout with the label beside the value for scenarios where vertical space is at a premium. For example, use the horizontal layout and the small size to display the total number of items in a list.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/key-info/key-info-horizontal-layout.fee3df309d0205261686dfe456e1576e.png)

### Size

Use the large key info when the values need to stand out in places such as data visualizations, dashboards, and landing pages.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/key-info/key-info-options-large.251ce89341a0d6e85fe1251adadb9bf8.png)

Use the small key info to highlight information that doesn't require the large size to stand out, such as the total number of items in a list.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/key-info/key-info-options-small.1c27b06a359905d6c73b99cdb09996b9.png)

### Help inline button

When you need to supplement a key info label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

 Behavior and states
--------------------

### Link styling

You can style the key info component as a link to let users select the value to navigate to a different location.

 Layout
-------

### Horizontal layout

When laying out key info components horizontally:

*   Use `"sky-margin-inline-xxl"` for consistent spacing between elements.
*   Don't overwhelm users with more than 6 elements without headings or grouping.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/key-info/key-info-usage-1.4ca5133df981810932455df8f2d46c7f.png)

Do provide consistent space between horizontal key info components.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/key-info/key-info-layout-2.0bf51da7d8fa69ece61014b663ef7d27.png)

Use caution with fluid grid to space key info components horizontally. This can cause uneven spacing and excessive gaps between elements.

 Related information
--------------------

### Components

*   [Description list](/skyux/components/description-list.md)
*   [Help inline button](/skyux/components/help-inline.md)

### Guidelines

*   [Call out information](/skyux/design/guidelines/call-out-info.md)

 Installation
-------------

NPM package

`@skyux/indicators`[View in NPM](https://www.npmjs.com/package/@skyux/indicators) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/indicators/src/lib/modules/key-info/key-info.module.ts#L23) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/indicators`Copy None found.

 Styling
--------

Use SKY UX font styles on `key-info-value` to change the size of values based on your design. The default medium size uses `sky-font-display-3`. Use `sky-font-display-1` for large values. Use `sky-font-display-4` for small values. Refer to the key info code examples for more information.

 SkyKeyInfoModule
-----------------

Type: Module

`import { SkyKeyInfoModule } from '@skyux/indicators';`

 SkyKeyInfoComponent
--------------------

Type: Component

Selector: `sky-key-info`

### Inputs

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified, a [help inline](/skyux/components/help-inline.md) button is placed beside the key info. Clicking the button invokes global help as configured by the application.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified, a [help inline](/skyux/components/help-inline.md) button is added to the key info. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `layout: SkyKeyInfoLayoutType | undefined`

The layout for the key info. The vertical layout places the label under the value, while the horizontal layout places the label beside the value.

Default: `"vertical"`

 SkyKeyInfoLabelComponent
-------------------------

Type: Component

Selector: `sky-key-info-label`

Specifies a label to display in smaller text under or beside the value. To display a help button beside the label, include a help button element, such as `sky-help-inline`, in the `sky-key-info` element and a `sky-control-help` CSS class on that help button element.

 SkyKeyInfoValueComponent
-------------------------

Type: Component

Selector: `sky-key-info-value`

Specifies a value to display in larger, bold text.

 SkyKeyInfoLayoutType
---------------------

Type: Type alias

    type SkyKeyInfoLayoutType = "horizontal" | "vertical"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyKeyInfoHarness
------------------

Type: Class

`import { SkyKeyInfoHarness } from '@skyux/indicators/testing';`

Harness for interacting with a key info component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getLabelText(): Promise<string>`

Gets the current label text.

#### Returns

`Promise<string>`

#### `getLayout(): Promise<SkyKeyInfoLayoutType>`

Gets the current layout type.

#### Returns

`Promise<SkyKeyInfoLayoutType>`

#### `getValueText(): Promise<string>`

Gets the current value text.

#### Returns

`Promise<string>`

#### `SkyKeyInfoHarness.with(filters: SkyKeyInfoHarnessFilters): HarnessPredicate<SkyKeyInfoHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyKeyInfoHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyKeyInfoHarnessFilters`

#### Returns

`HarnessPredicate<SkyKeyInfoHarness>`

 SkyKeyInfoHarnessFilters
-------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyKeyInfoHarness](/skyux/components/key-info?docs-active-tab=design#class_sky-key-info-harness.md) instances.

    interface SkyKeyInfoHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.