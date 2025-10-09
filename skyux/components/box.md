                   

 Box
===

Boxes provide containers to group related content and actions.

 Usage
------

### Use when

Use boxes as containers for related content and actions on pages such [action hubs](/skyux/design/guidelines/page-layouts/action-hub.md) and [record pages](/skyux/design/guidelines/page-layouts/record-page.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/box/box-use-action-hub.a7dc2ea0a0ef88f69bc928554455555b.png)

Do use boxes to organize content on action hubs.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/box/box-use-record.068ff87e3820e394cd0872366dd81953.png)

Do use boxes to organize content on record pages.

### Don't use when

Don't use boxes to separate individual items in a list. Use [repeaters](/skyux/components/repeater.md) or other layout approaches instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/box/box-dont-individual-element.b6d1ec98dbfb5079bc1b0f1e4ea506c8.png)

Don't use boxes to separate individual items in a list.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/box/box-group-related.5e971bb0f37db91837ef2314fc8ec7c9.png)

Do use boxes to group related items in a section.

Don't use boxes to organize content in [modal forms](/skyux/components/modal.md) or [split view workspaces](/skyux/components/split-view.md). Use headers and spacing instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/box/box-dont-form.a9581d9c1df441bdee17ad0a578bed1a.png)

Don't use boxes to organize content in forms.

Don't add boxes to pre-defined sections of page layouts. For example, don't add boxes around lists on [list pages](/skyux/design/guidelines/page-layouts/list-page.md) or around related links on [action hubs](/skyux/design/guidelines/page-layouts/action-hub.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/box/box-dont-related-recent.81c9b967deb8a7b56b484a85b39ee6e7.png)

Don't add boxes to the sections in the top right of action hubs.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/box/box-dont-list.2820277b5388a62afda7b8cf0d4b0e31.png)

Don't add boxes to list pages.

 Anatomy
--------

1

Container

2

Content

3

Heading (optional)

4

Help inline button (optional)

5

Control button (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/box/box-anatomy.9eb66b7a31a94c8fd23955fc6bd0b2e2.png)

 Options
--------

### Heading

In general, boxes should include short headings to describe their contents. However, headings are optional so that consumers can exclude them when boxes contain content that doesn't require headings, such as visualizations or multimedia content.

To match to a page's semantic and visual hierarchy, adjust the box heading's `headingLevel` and `headingStyle` properties. In most cases, box headings follow the page heading in the page hierarchy, and these properties should be set to `2`.

### Help inline button

When you need to supplement a box with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the heading to invoke contextual user assistance.

### Control button

You can include a button in the top right to provide an edit action or a context menu with multiple actions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/box/box-option-1.463354ca7f78665bc756df8e2f3aac7a.png)

Do include an edit button for editable content.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/box/box-option-2.924d795b1d06d1015c6134c47e522d10.png)

Do include a context menu for multiple actions.

Don't include multiple buttons in boxes. Instead, break up content so that boxes only contain related content that users can manage together.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/box/box-option-3.ecb483035999b094f378231f539ea79b.png)

Don't include multiple buttons.

 Layout
-------

Use proper spacing between boxes. Depending on your scenario, you can use [fluid grid](/skyux/components/fluid-grid.md), [CSS flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/), CSS Grid or [spacing classes](/skyux/design/styles/spacing.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/box/box-layout-margin.24200bec24770059400d9810d8613ee4.png)

Use proper spacing between boxes.

 Related information
--------------------

### Components

*   [Action hub](/skyux/components/action-hub.md)
*   [Fluid grid](/skyux/components/fluid-grid.md)
*   [Help inline button](/skyux/components/help-inline.md)

### Guidelines

*   [Action hub page](/skyux/design/guidelines/page-layouts/action-hub.md)
*   [Record page](/skyux/design/guidelines/page-layouts/record-page.md)
*   [Spacing](/skyux/design/styles/spacing.md)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/box/box.module.ts#L26) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyBoxModule
-------------

Type: Module

`import { SkyBoxModule } from '@skyux/layout';`

 SkyBoxComponent
----------------

Type: Component

Selector: `sky-box`

Provides a common look-and-feel for box content with options to display a common box header, specify body content, and display common box controls.

### Inputs

#### `ariaLabel: string | undefined`

Warning: **Deprecated.** Use `headingText` instead.

The ARIA label for the box. This sets the box's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the box includes a visible label, use `ariaLabelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `ariaLabelledBy: string | undefined`

Warning: **Deprecated.** Use `headingText` instead.

The HTML element ID of the element that labels the box. This sets the box's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the box does not include a visible label, use `ariaLabel` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `ariaRole: string | undefined`

The ARIA role for the box [to support accessibility](/skyux/learn/accessibility.md) by indicating what the box contains. For information about how an ARIA role indicates what an item represents on a web page, see the [WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles).

#### `headingHidden: boolean`

Indicates whether to hide the `headingText`.

Default: `false`

#### `headingLevel: SkyBoxHeadingLevel`

The semantic heading level in the document structure. The default is 2.

Default: `2`

#### `headingStyle: SkyBoxHeadingStyle`

The heading [font style](/skyux/design/styles/typography#headings.md).

Default: `2`

#### `headingText: string | undefined`

The text to display as the box's heading.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the box heading. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `headingText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to the box heading. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

 SkyBoxHeaderComponent
----------------------

Type: Component

Selector: `sky-box-header`

Warning: **Deprecated.** Use `headingText` input on the `sky-box` component instead.

Specifies a header for the box.

 SkyBoxContentComponent
-----------------------

Type: Component

Selector: `sky-box-content`

Specifies the body content to display inside the box and provides padding around that content.

 SkyBoxControlsComponent
------------------------

Type: Component

Selector: `sky-box-controls`

Specifies the controls to display in upper right corner of the box. These buttons typically let users edit the box content.

 SkyBoxHeadingLevel
-------------------

Type: Type alias

    type SkyBoxHeadingLevel = 2 | 3 | 4 | 5

 SkyBoxHeadingStyle
-------------------

Type: Type alias

    type SkyBoxHeadingStyle = 2 | 3 | 4 | 5

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyBoxHarness
--------------

Type: Class

`import { SkyBoxHarness } from '@skyux/layout/testing';`

Harness for interacting with a box component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getAriaLabel(): Promise<null | string>`

Gets the aria-label property of the box

#### Returns

`Promise<null | string>`

#### `getAriaLabelledby(): Promise<null | string>`

Gets the aria-labelledby property of the box

#### Returns

`Promise<null | string>`

#### `getAriaRole(): Promise<null | string>`

Gets the aria-role property of the box

#### Returns

`Promise<null | string>`

#### `getHeadingHidden(): Promise<boolean>`

Whether the heading is hidden.

#### Returns

`Promise<boolean>`

#### `getHeadingLevel(): Promise<undefined | SkyBoxHeadingLevel>`

The semantic heading level used for the checkbox group. Returns undefined if heading level is not set.

#### Returns

`Promise<undefined | SkyBoxHeadingLevel>`

#### `getHeadingStyle(): Promise<SkyBoxHeadingStyle>`

The heading style used for the checkbox group.

#### Returns

`Promise<SkyBoxHeadingStyle>`

#### `getHeadingText(): Promise<undefined | string>`

Gets the box's heading text. If `headingHidden` is true, the text will still be returned.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `SkyBoxHarness.with(filters: SkyBoxHarnessFilters): HarnessPredicate<SkyBoxHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyBoxHarness` that meets certain criteria

#### Parameters

##### `filters: SkyBoxHarnessFilters`

#### Returns

`HarnessPredicate<SkyBoxHarness>`

 SkyBoxHarnessFilters
---------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyBoxHarness` instances.

    interface SkyBoxHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.