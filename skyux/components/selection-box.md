                    

 Selection box
=============

Selection boxes present users with a choice to make or a question to answer before proceeding with a one-time process.

 Usage
------

### Use when

Use selection boxes when users must make a choice or answer a standalone question before proceeding with a one-time process such as a setup or configuration task. Selection boxes represent the only decision on a page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/selection-box/selection-box-usage-1.7992f55cbd8885d638b37deefe2eae6c.png)

Do use selection boxes to present standalone options during a one-time process such as onboarding.

Use selection boxes when options are abstract or potentially unfamiliar to users. Use icons and descriptions to provide additional insight.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/selection-box/selection-box-usage-2.57ab3fd84077774719fc9849af65fa7b.png)

Do use selection boxes to present options or categories that are unfamiliar to users.

### Don't use when

Don't use selection boxes for repeatable tasks such as data entry. Use other selection controls, such as [checkboxes](/skyux/components/checkbox.md) or [radio buttons](/skyux/components/radio.md), instead.

Don't use selection boxes for fewer than 3 options or more than 12 options. Use other selection controls instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/selection-box/selection-box-usage-3.4523aeceec1093423cdeb9899cda2f66.png)

Don't use selection boxes in tasks or workflows that users complete repeatedly.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/selection-box/selection-box-usage-4.bbbda5099dbd2c0573ed30ea7f252cde.png)

Do use other selection inputs for data entry.

Don't use selection boxes for fewer than 3 options or more than 12 options. Use other selection controls instead.

 Anatomy
--------

1

Box

2

Checkbox or radio button

3

Header

4

Icon (optional)

5

Description (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/selection-box/selection-box-anatomy.e76a146668450413a44b1914bab24a35.png)

 Options
--------

### Icons

Use icons to add meaning and help users distinguish between options.

*   Don't use icons if they don't add useful information.
*   Don't reuse icons within a group of selection boxes.
*   Don't use icons with some selection boxes in a group but not others.
*   Don't use selection boxes with titles only. If neither icons nor descriptions are necessary, use [other selection controls](/skyux/design/guidelines/form-design.md) instead.

### Descriptions

Use descriptions to add meaning and help users distinguish between options.

*   Don't use descriptions if they don't add useful information.
*   Don't use descriptions with some selection boxes in a group but not others.
*   Don't use selection boxes with titles only. If neither icons nor descriptions are necessary, use [other selection controls](/skyux/design/guidelines/form-design#selection-inputs.md) instead.

 Behavior and states
--------------------

### Responsiveness

On smaller viewports, selection boxes hide their icons and use smaller typography and tighter spacing.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/selection-box/selection-box-behavior-1.8486ea0cedfa6305ba73599479bf4450.png)

### States

Unselected

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/selection-box/selection-box-states-base.f683ff53cf2c5395937f894c1e30e49c.png)

Hover

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/selection-box/selection-box-states-hover.9af23e34ca3c9aa16ab67d7717204ecc.png)

Focus

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/selection-box/selection-box-states-focus.73a41e893ba3d51daedce9017e5fd886.png)

Selected

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/selection-box/selection-box-states-selected.7622a46dca6c39e3698008ddac094777.png)

Disabled

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/selection-box/selection-box-states-disabled.0bc6b0370d7deefbe262f45d368b8aeb.png)

 Content
--------

Keep headers and descriptions short and concise. Descriptions can be partial or complete sentences, but don't use more than a single sentence.

 Layout
-------

Selection boxes are center-aligned within a container based on the number of options and the container's width. Don't use other layouts with selection boxes.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/selection-box/selection-box-layout-1.f3ea4fa6bdfb155bc915c895db3fe7bc.png)

Do center-align selection boxes and use matching heights.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/selection-box/selection-box-layout-2.e44da91aba638091edf68e7237d4a400.png)

Don't use custom layouts to arrange selection boxes.

 Related information
--------------------

### Components

*   [Checkbox](/skyux/components/checkbox.md)
*   [Icon](/skyux/components/icon.md)
*   [Radio button](/skyux/components/radio.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/selection-box/selection-box.module.ts#L27) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 SkySelectionBoxModule
----------------------

Type: Module

`import { SkySelectionBoxModule } from '@skyux/forms';`

 SkySelectionBoxComponent
-------------------------

Type: Component

Selector: `sky-selection-box`

Creates a button to present users with a choice or question before proceeding with a one-time process.

### Inputs

#### `control: SkyCheckboxComponent | SkyRadioComponent | undefined`

Required

The radio button or checkbox to display in the selection box.

 SkySelectionBoxHeaderComponent
-------------------------------

Type: Component

Selector: `sky-selection-box-header`

Specifies the header to display in a selection box.

 SkySelectionBoxDescriptionComponent
------------------------------------

Type: Component

Selector: `sky-selection-box-description`

Specifies the description to display in a selection box.

 SkySelectionBoxGridComponent
-----------------------------

Type: Component

Selector: `sky-selection-box-grid`

Creates a grid layout for an array of selection boxes.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkySelectionBoxHarness
-----------------------

Type: Class

`import { SkySelectionBoxHarness } from '@skyux/forms/testing';`

Harness to interact with a selection box component in tests.

### Methods

#### `getControl(): Promise<SkyCheckboxHarness | SkyRadioHarness>`

Gets the checkbox or radio harness for the selection box form control.

#### Returns

`Promise<SkyCheckboxHarness | SkyRadioHarness>`

#### `getDescriptionText(): Promise<string>`

Gets the selection box description text.

#### Returns

`Promise<string>`

#### `getHeaderText(): Promise<string>`

Gets the selection box header text.

#### Returns

`Promise<string>`

#### `getIcon(): Promise<null | SkyIconHarness>`

Gets the selection box icon, if it exists.

#### Returns

`Promise<null | SkyIconHarness>`

#### `SkySelectionBoxHarness.with(filters: SkySelectionBoxHarnessFilters): HarnessPredicate<SkySelectionBoxHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySelectionBoxHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySelectionBoxHarnessFilters`

#### Returns

`HarnessPredicate<SkySelectionBoxHarness>`

 SkySelectionBoxHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkySelectionBoxHarness` instances.

    interface SkySelectionBoxHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkySelectionBoxGridHarness
---------------------------

Type: Class

`import { SkySelectionBoxGridHarness } from '@skyux/forms/testing';`

Harness for interacting with a selection box grid component in tests.

### Methods

#### `getSelectionBox(filter: SkySelectionBoxHarnessFilters): Promise<SkySelectionBoxHarness>`

Gets a specific selection box based on the filter criteria.

#### Parameters

##### `filter: SkySelectionBoxHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkySelectionBoxHarness>`

#### `getSelectionBoxes(filters?: SkySelectionBoxHarnessFilters): Promise<SkySelectionBoxHarness[]>`

Gets an array of selection boxes based on the filter criteria. If no filter is provided, returns all selection boxes.

#### Parameters

##### `filters?: SkySelectionBoxHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkySelectionBoxHarness[]>`

#### `SkySelectionBoxGridHarness.with(filters: SkySelectionBoxGridHarnessFilters): HarnessPredicate<SkySelectionBoxGridHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkySelectionBoxGridHarness` that meets certain criteria.

#### Parameters

##### `filters: SkySelectionBoxGridHarnessFilters`

#### Returns

`HarnessPredicate<SkySelectionBoxGridHarness>`

 SkySelectionBoxGridHarnessFilters
----------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkySelectionBoxGridHarness` instances.

    interface SkySelectionBoxGridHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.