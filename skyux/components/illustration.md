                   

 Spot illustration
=================

Spot illustrations orient users and focus their attention across various experiences.

Blackbaud's spot illustration library is only available for internal Blackbaud consumers. External consumers can source their own assets to use with the spot illustration component.

 Usage
------

### Use when

Use spot illustrations to focus user attention and shape visual hierarchy. Refer to the [spot illustration design guidelines](/skyux/design/guidelines/spot-illustrations.md) page to learn about their principles and role.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/spot-illustrations/spot-illustration-sizing-do.dc83872c550eeee72c8e5022d59f535d.png)

Do use spot illustrations for illustrative purposes.

### Don't use when

Don't use spot illustrations as a visual shorthand to supplement action labels. Use [icons](/skyux/components/icon.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/spot-illustrations/spot-illustration-dont-use.c6aeb65e692fd36ef0fe5a28b74a3d9d.png)

Don't use spot illustrations in place of icons.

 Options
--------

### Size

Spot illustrations have four sizes: small, medium, large, and extra large.

To determine the size to use for a spot illustration, consider its placement within a page’s visual hierarchy, its use case, and the other elements that it's paired with.

#### Small (48px)

In small containers with limited text, such as [boxes](/skyux/components/box.md) or small [modals](/skyux/components/modal.md), use the small size. Most SKY UX experiences should use small illustrations.

#### Medium (64px)

In small containers where small spot illustrations lose emphasis in the visual hierarchy due to a large amount of text, use the medium size.

#### Large (80px)

In large containers with lots of text, such as large [modals](/skyux/components/modal.md), use the large size. Also, on pages where spot illustrations stand alone with a small amount of text, use the large size.

#### Extra Large (96px)

In general, don't use the extra large size. But on pages with no other content, you can pair extra large spot illustrations with text to communicate important messages.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/spot-illustrations/spot-illustration-sizing.593800bb0ba0133e7fd511b630dc2797.png)

Spot illustrations have four size variations.

 Layout
-------

When placing spot illustrations within components or other page elements, follow the below design specifications to ensure their effectiveness.

### Background color

Spot illustrations are duotone and use Blackbaud's color palette. To ensure clarity, only use them on light backgrounds.

### Alignment

To maintain visual balance, align spot illustrations vertically or horizontally with other elements, such as text, in the components and patterns where they appear.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/spot-illustrations/spot-illustration-alignment-horizontal.e1f8e5999292509bd40b64ee003d4be5.png)

You can align spot illustrations horizontally to the left of other elements.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/spot-illustrations/spot-illustration-alignment-vertical.e0e1542e240f73017ed1cfe79e85d217.png)

Illustrations can be centered vertically on top of accompanying text.

### Standard layouts

To maintain visual balance, use SKY UX spacing values to separate elements.

#### Box call-to-action

Use small spot illustrations in this horizontal layout to draw user attention to important actions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/spot-illustrations/spot-illustration-spacing-left-aligned.4feff08a4d4d5a22468fc67cbaafb115.png)

Spacing for left-aligned illustrations and text.

#### Welcome page

Use large spot illustrations within boxes to anchor content on welcome pages.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/spot-illustrations/spot-illustration-size-spacing-scaling.cacaac9e0edee9a21470204c7f008a30.png)

Spacing values should scale with illustration size.

#### Split view empty state

Use medium spot illustrations in this vertical layout when split view lists include no remaining items.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/spot-illustrations/spot-illustration-spacing-center-aligned.ca84d2e6fe2e3409c8835672241ee17f.png)

Spacing for center-aligned illustrations and text.

 Related information
--------------------

### Components

*   [Box](/skyux/components/box.md)
*   [Icon](/skyux/components/icon.md)

### Guidelines

*   [Page design](/skyux/design/guidelines/page-layouts.md)

 Installation
-------------

NPM package

`@skyux/indicators`[View in NPM](https://www.npmjs.com/package/@skyux/indicators) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/indicators/src/lib/modules/illustration/illustration.module.ts#L9) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/indicators`Copy None found.

 SkyIllustrationModule
----------------------

Type: Module

`import { SkyIllustrationModule } from '@skyux/indicators';`

 SkyIllustrationComponent
-------------------------

Type: Component

Selector: `sky-illustration`

Displays a spot illustration at the specified size.

### Inputs

#### `name: InputSignal<string>`

Required

The name of the illustration to display.

#### `size: InputSignal<SkyIllustrationSize>`

Required

The size of the illustration.

 SkyIllustrationSize
--------------------

Type: Type alias

    type SkyIllustrationSize = "sm" | "md" | "lg" | "xl"

 SkyIllustrationResolverService
-------------------------------

Type: Service

Resolves information about spot illustrations.

### Methods

#### `resolveHref(name: string): Promise<string>`

Resolves the `href` of the SVG element to reference in `use`. If both an `href` and a URL are resolved, the SVG with `href` will be rendered.

#### Parameters

##### `name: string`

#### Returns

`Promise<string>`

#### `resolveUrl(name: string): Promise<string>`

Resolves a URL for the specified illustration name to render in an `img`.

#### Parameters

##### `name: string`

#### Returns

`Promise<string>`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyIllustrationHarness
-----------------------

Type: Class

`import { SkyIllustrationHarness } from '@skyux/indicators/testing';`

Harness for interacting with an illustration component in tests.

### Methods

#### `getName(): Promise<string>`

Gets the specified name of the illustration.

#### Returns

`Promise<string>`

#### `getSize(): Promise<SkyIllustrationSize>`

Gets the specified size of the illustration.

#### Returns

`Promise<SkyIllustrationSize>`

#### `SkyIllustrationHarness.with(filters: SkyIllustrationHarnessFilters): HarnessPredicate<SkyIllustrationHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyIllustrationHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyIllustrationHarnessFilters`

#### Returns

`HarnessPredicate<SkyIllustrationHarness>`

 SkyIllustrationHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyIllustrationHarness` instances.

    interface SkyIllustrationHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.