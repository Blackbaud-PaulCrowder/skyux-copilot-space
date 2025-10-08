# Design

                    Skip to Main Content

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

# Development

                    Skip to Main Content

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

# Examples

                      Skip to Main Content

 Selection box
=============

Selection boxes present users with a choice to make or a question to answer before proceeding with a one-time process.Usage
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

### Selection boxes with checkboxes

Edit in StackBlitz

Save time and effort

Automate mundane tasks and spend more time on the things that matter.

Boost engagement

Encourage supporters to interact with your organization.

Build relationships

Connect to supporters on a personal level and maintain accurate data.

Show code

Copy

    <form [formGroup]="formGroup">
      <sky-selection-box-grid>
        @for (control of checkboxControls; track control; let i = $index) {
          <sky-selection-box [control]="checkbox">
            <sky-icon [iconName]="selectionBoxes[i].iconName" />
            <sky-selection-box-header #checkboxHeaderId="skyId" skyId>
              {{ selectionBoxes[i].name }}
            </sky-selection-box-header>
            <sky-selection-box-description>
              {{ selectionBoxes[i].description }}
            </sky-selection-box-description>
            <sky-checkbox
              #checkbox
              [formControl]="control"
              [labelledBy]="checkboxHeaderId.id"
            />
          </sky-selection-box>
        }
      </sky-selection-box-grid>
    </form>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyIdService } from '@skyux/core';
    import { SkySelectionBoxGridHarness } from '@skyux/forms/testing';
    
    import { FormsSelectionBoxCheckboxExampleComponent } from './example.component';
    
    let index: number;
    
    async function setupTest(options: { dataSkyId?: string } = {}): Promise<{
      selectionBoxGridHarness: SkySelectionBoxGridHarness;
    }> {
      await TestBed.configureTestingModule({
        imports: [FormsSelectionBoxCheckboxExampleComponent, NoopAnimationsModule],
      }).compileComponents();
    
      index = 0;
      spyOn(TestBed.inject(SkyIdService), 'generateId').and.callFake(
        () => `MOCK_ID_${++index}`,
      );
    
      const fixture = TestBed.createComponent(
        FormsSelectionBoxCheckboxExampleComponent,
      );
      const loader = TestbedHarnessEnvironment.loader(fixture);
    
      const selectionBoxGridHarness: SkySelectionBoxGridHarness = options.dataSkyId
        ? await loader.getHarness(
            SkySelectionBoxGridHarness.with({
              dataSkyId: options.dataSkyId,
            }),
          )
        : await loader.getHarness(SkySelectionBoxGridHarness);
    
      return { selectionBoxGridHarness };
    }
    
    describe('Selection box checkbox example', () => {
      it('should set up the component', async () => {
        const { selectionBoxGridHarness } = await setupTest();
    
        const selectionBoxHarnesses =
          await selectionBoxGridHarness.getSelectionBoxes();
    
        expect(selectionBoxHarnesses.length).toBe(3);
    
        await expectAsync(selectionBoxHarnesses[0].getHeaderText()).toBeResolvedTo(
          'Save time and effort',
        );
        await expectAsync(
          selectionBoxHarnesses[1].getDescriptionText(),
        ).toBeResolvedTo(
          'Encourage supporters to interact with your organization.',
        );
        await expectAsync(
          (await selectionBoxHarnesses[2].getIcon())?.getIconName(),
        ).toBeResolvedTo('people-team');
    
        await (await selectionBoxHarnesses[0].getControl()).check();
      });
    });

Copy

    import { Component, inject } from '@angular/core';
    import {
      FormArray,
      FormBuilder,
      FormControl,
      FormGroup,
      FormsModule,
      ReactiveFormsModule,
    } from '@angular/forms';
    import { SkyIdModule } from '@skyux/core';
    import { SkyCheckboxModule, SkySelectionBoxModule } from '@skyux/forms';
    import { SkyIconModule } from '@skyux/icon';
    
    /**
     * @title Selection boxes with checkboxes
     */
    @Component({
      selector: 'app-forms-selection-box-checkbox-example',
      templateUrl: './example.component.html',
      imports: [
        FormsModule,
        ReactiveFormsModule,
        SkyCheckboxModule,
        SkyIconModule,
        SkyIdModule,
        SkySelectionBoxModule,
      ],
    })
    export class FormsSelectionBoxCheckboxExampleComponent {
      protected checkboxControls: FormControl[] | undefined;
    
      protected selectionBoxes: {
        description: string;
        iconName: string;
        name: string;
        selected?: boolean;
      }[] = [
        {
          name: 'Save time and effort',
          iconName: 'clock',
          description:
            'Automate mundane tasks and spend more time on the things that matter.',
        },
        {
          name: 'Boost engagement',
          iconName: 'person',
          description: 'Encourage supporters to interact with your organization.',
        },
        {
          name: 'Build relationships',
          iconName: 'people-team',
          description:
            'Connect to supporters on a personal level and maintain accurate data.',
        },
      ];
    
      protected formGroup: FormGroup;
    
      readonly #formBuilder = inject(FormBuilder);
    
      constructor() {
        const checkboxArray = this.#buildCheckboxes();
        this.checkboxControls = checkboxArray.controls as FormControl[];
    
        this.formGroup = this.#formBuilder.group({
          checkboxes: checkboxArray,
        });
      }
    
      #buildCheckboxes(): FormArray {
        const checkboxArray = this.selectionBoxes.map((checkbox) =>
          this.#formBuilder.control(checkbox.selected),
        );
    
        return this.#formBuilder.array(checkboxArray);
      }
    }
### Selection boxes with radio buttons

Edit in StackBlitz

Save time and effort

Automate mundane tasks and spend more time on the things that matter.

Boost engagement

Encourage supporters to interact with your organization.

Build relationships

Connect to supporters on a personal level and maintain accurate data.

Show code

Copy

    <form novalidate [formGroup]="formGroup">
      <sky-radio-group ariaLabel="Demo options" formControlName="myOption">
        <sky-selection-box-grid>
          @for (item of items; track item) {
            <sky-selection-box [control]="radio">
              <sky-icon [iconName]="item['iconName']" />
              <sky-selection-box-header #radioHeaderId="skyId" skyId>
                {{ item['name'] }}
              </sky-selection-box-header>
              <sky-selection-box-description>
                {{ item['description'] }}
              </sky-selection-box-description>
              <sky-radio
                #radio
                [labelledBy]="radioHeaderId.id"
                [value]="item['value']"
              />
            </sky-selection-box>
          }
        </sky-selection-box-grid>
      </sky-radio-group>
    </form>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyIdService } from '@skyux/core';
    import { SkySelectionBoxGridHarness } from '@skyux/forms/testing';
    
    import { FormsSelectionBoxRadioExampleComponent } from './example.component';
    
    let index: number;
    
    async function setupTest(options: { dataSkyId?: string } = {}): Promise<{
      selectionBoxGridHarness: SkySelectionBoxGridHarness;
    }> {
      await TestBed.configureTestingModule({
        imports: [FormsSelectionBoxRadioExampleComponent, NoopAnimationsModule],
      }).compileComponents();
    
      spyOn(TestBed.inject(SkyIdService), 'generateId').and.callFake(
        () => `MOCK_ID_${++index}`,
      );
    
      index = 0;
      const fixture = TestBed.createComponent(
        FormsSelectionBoxRadioExampleComponent,
      );
      const loader = TestbedHarnessEnvironment.loader(fixture);
    
      const selectionBoxGridHarness: SkySelectionBoxGridHarness = options.dataSkyId
        ? await loader.getHarness(
            SkySelectionBoxGridHarness.with({
              dataSkyId: options.dataSkyId,
            }),
          )
        : await loader.getHarness(SkySelectionBoxGridHarness);
    
      return { selectionBoxGridHarness };
    }
    
    describe('Selection box radio example', () => {
      it('should set up the component', async () => {
        const { selectionBoxGridHarness } = await setupTest();
    
        const selectionBoxHarnesses =
          await selectionBoxGridHarness.getSelectionBoxes();
    
        expect(selectionBoxHarnesses.length).toBe(3);
    
        await expectAsync(selectionBoxHarnesses[0].getHeaderText()).toBeResolvedTo(
          'Save time and effort',
        );
        await expectAsync(
          selectionBoxHarnesses[1].getDescriptionText(),
        ).toBeResolvedTo(
          'Encourage supporters to interact with your organization.',
        );
        await expectAsync(
          (await selectionBoxHarnesses[2].getIcon())?.getIconName(),
        ).toBeResolvedTo('people-team');
    
        await (await selectionBoxHarnesses[0].getControl()).check();
      });
    });

Copy

    import { Component, inject } from '@angular/core';
    import {
      FormBuilder,
      FormGroup,
      FormsModule,
      ReactiveFormsModule,
    } from '@angular/forms';
    import { SkyIdModule } from '@skyux/core';
    import { SkyRadioModule, SkySelectionBoxModule } from '@skyux/forms';
    import { SkyIconModule } from '@skyux/icon';
    
    /**
     * @title Selection boxes with radio buttons
     */
    @Component({
      selector: 'app-forms-selection-box-radio-example',
      templateUrl: './example.component.html',
      imports: [
        FormsModule,
        ReactiveFormsModule,
        SkyIconModule,
        SkyIdModule,
        SkyRadioModule,
        SkySelectionBoxModule,
      ],
    })
    export class FormsSelectionBoxRadioExampleComponent {
      protected items: Record<string, string>[] = [
        {
          name: 'Save time and effort',
          iconName: 'clock',
          description:
            'Automate mundane tasks and spend more time on the things that matter.',
          value: 'clock',
        },
        {
          name: 'Boost engagement',
          iconName: 'person',
          description: 'Encourage supporters to interact with your organization.',
          value: 'engagement',
        },
        {
          name: 'Build relationships',
          iconName: 'people-team',
          description:
            'Connect to supporters on a personal level and maintain accurate data.',
          value: 'relationships',
        },
      ];
    
      protected formGroup: FormGroup;
    
      constructor() {
        this.formGroup = inject(FormBuilder).group({
          myOption: this.items[2]['value'],
        });
      }
    }

# Testing

                    Skip to Main Content

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