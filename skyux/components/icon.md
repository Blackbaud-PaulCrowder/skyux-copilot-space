                     

 Icon
====

Icons represent actions, content, and ideas, and they help define the visual identity of SKY UX applications.

### Icon sets

Standard icons

Additional icons

 Standard icons
---------------

Use standard icons for the use cases listed below. The consistent use of icons help users to quickly recognize and understand the functionality across applications where the same icons are used for the same purpose. Only use standard icons for the specified use cases.

If you need to communicate a concept or purpose that isn't listed below, see the **Additional icons** option to find an icon.

Icon

Usage

Code

 Principles
-----------

Icons follow [SKY UX design principles](/skyux/design/principles.md) to deliberately facilitate user comprehension and direct focus toward actions and other content.

### Global

Icons use well-established, universal images to visually convey meaning at a glance.

### Supplemental

Icons are paired with action labels and other text and are not used solely for decoration or visual interest.

### Specific

Icons convey a single meaning with limited variations. Each icon represents a common idea or subject that is not abstract.

 Usage
------

### Use when

Use icons alongside meaningful action labels to help users understand the purpose of actions at a glance.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/icon/img/guidelines/icons/icon-usage-1.bcf382471fa0b5d9a953e8eeba4f15da.png)

Do use icons as a visual shorthand to supplement action labels.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/icon/img/guidelines/icons/icon-usage-2.703e568b8678d66825579c49942b05e6.png)

Avoid standalone icons except when space is too tight for labels and icons are sufficient to represent actions.

### Don't use when

Don't use icons solely for visual interest or decoration.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/icon/img/guidelines/icons/icon-usage-4.7e68da2be8522c1abed456b9c12c1f1e.png)

Don't use icons as decoration.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/icon/img/guidelines/icons/icon-usage-3.6531a83af966330abe989dead4037f1b.png)

Do exclude icons when they don't facilitate user comprehension or drive focus.

Don't use icons for multiple purposes. Each icon conveys a single, specific meaning that users can understand at a glance.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/icon/img/guidelines/icons/icon-usage-6.c7fc1eadfda416f7a56ba885e56c89af.png)

Don't use icons with established meanings for other purposes.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/icon/img/guidelines/icons/icon-usage-5.4daa54018fbc0442ad1b037401672917.png)

Do use icons consistently to represent one specific idea or subject.

 Behavior and states
--------------------

SKY UX uses simple, glyphic, mono-color icons to facilitate, guide, and inform users. Icons are part of Blackbaud's brand personality and reflect a human, visionary approach that is built on SKY UX's visual language.

### Color

Icons use solid, monochromatic colors that they usually inherit from their parent components. Icon colors must meet the [WCAG contrast ratio of 3:1](https://www.w3.org/WAI/WCAG21/Techniques/general/G207.html). For more information, see the [SKY UX color guidelines](/skyux/design/styles/color.md).

### Style

SKY UX icons have two style variations: `line` and `solid`. Use line icons for most user experiences.

### Size

Use the default icon size, medium or `m`, when including icons in buttons or for use with standard body copy. Only use smaller or larger icon sizes when pairing an icon with smaller or larger content to match to its paired content or better fit its context.

iconSize

Icon size

Example

`xs`

12px

`s`

16px

`m`

20px

`l`

24px

`xl`

24px

`xxl`

32px

`xxxl`

40px

### Localization

SKY UX icons account for global considerations to ensure that international users from different cultures and backgrounds can understand them.

 Accessibility
--------------

Icons must meet [WCAG contrast standards](https://www.w3.org/WAI/WCAG21/Techniques/general/G207.html) for a 3:1 contrast ratio with the background.

 Installation
-------------

NPM package

`@skyux/icon`[View in NPM](https://www.npmjs.com/package/@skyux/icon) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/icon/src/lib/modules/icon/icon.module.ts#L12) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/icon`Copy None found.

 SkyIconModule
--------------

Type: Module

`import { SkyIconModule } from '@skyux/icon';`

 SkyIconComponent
-----------------

Type: Component

Selector: `sky-icon`

### Inputs

#### `iconName: string`

The name of the Blackbaud SVG icon to display.

#### `iconSize: InputSignal<undefined | SkyIconSize>`

The icon size. Size is independent of font size.

Default: `"m"`

#### `variant: SkyIconVariantType | undefined`

The icon variant. If the variant doesn't exist for the specified icon, the normal icon is displayed. This property only applies when using SKY UX icons.

 SkyIconVariantType
-------------------

Type: Type alias

    type SkyIconVariantType = "line" | "solid"

 SkyIconSize
------------

Type: Type alias

    type SkyIconSize = "xxxs" | "xxs" | "xs" | "s" | "m" | "l" | "xl" | "xxl" | "xxxl"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyIconHarness
---------------

Type: Class

`import { SkyIconHarness } from '@skyux/icon/testing';`

Harness for interacting with an icon component in tests.

### Methods

#### `getIconName(): Promise<undefined | string>`

Gets the icon name.

#### Returns

`Promise<undefined | string>`

#### `getIconSize(): Promise<string>`

Gets the icon size.

#### Returns

`Promise<string>`

#### `getVariant(): Promise<string>`

Gets if the icon is a variant.

#### Returns

`Promise<string>`

#### `SkyIconHarness.with(filters: SkyIconHarnessFilters): HarnessPredicate<SkyIconHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyIconHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyIconHarnessFilters`

#### Returns

`HarnessPredicate<SkyIconHarness>`

 SkyIconHarnessFilters
----------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyIconHarness](/skyux/components/icon?docs-active-tab=icons#class_sky-icon-harness.md) instances.

    interface SkyIconHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.