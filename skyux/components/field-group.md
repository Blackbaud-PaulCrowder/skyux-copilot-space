# Design

                   Skip to Main Content

 Field group
===========

Field groups organize related form inputs and controls into semantic and visual groups on long or complex forms.

 Usage
------

### Use when

Use field groups to divide long or complex forms into groups of related inputs and controls. Field groups create semantic and visual groups to communicate context and relationships between the elements on a form.

Semantically, a field group creates an HTML `fieldset` element for its contents. It also creates a `legend` element and an `h3` or `h4` heading using the field group label.

Not every form requires field groups. Simple forms with a small number of inputs can use the modal title to establish context and don't require a field group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-usage-1.9c5fb738cc3acb80690aede56c460330.png)

Do use field groups to divide long forms into groups of related elements.

Use nested field groups to organize related elements into subgroups in form sections. To communicate hierarchy, adjust heading tags and the visual style of field group labels. For example, you can nest two field groups with `h4` headings in a form section with an `h3` heading. For more details, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-usage-2.9d5c6a752d1582abe0109b3e141aac4d.png)

Do use nested field groups to create subgroups in form sections.

### Don't use when

Don't use field groups when short or simple forms contain a small number of elements and don't require groups.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-usage-3.2c8b9e2befabac4b99d1ae8f7fa947a7.png)

Don't use field groups on short or simple forms that don't require groups.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-usage-4.fd2f6f7c180e0325938ad6f3aca13a38.png)

Do create short, simple forms without using field groups.

Don't use field groups to divide a complex task into multiple steps that users should complete in a particular order. Use a [wizard](/skyux/components/tabs-wizard.md) instead.

Don't use field groups for very long forms, especially when users don't need to interact with every group of inputs. Consider using a [sectioned form](/skyux/components/sectioned-form.md) instead.

 Anatomy
--------

1

Heading

2

Help inline button (optional)

3

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-anatomy.b2c9872f792c9bb6a30a47dc2e9bac3a.png)

 Options
--------

### Heading level and style

By default, field group headings create `h3` headings with a `sky-font-heading-3` visual style. When nesting field groups, adjust the semantic heading tag and the font style to maintain the semantic and visual hierarchy of the form. For more details, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

### Help inline button

When you need to supplement a field group with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a field group, use hint text. This persistent inline help can explain details such as:

*   The correct format
*   Any constraints on the inputs
*   Additional instructions or context, such as how data is used

### Stacked margin

To provide consistent vertical spacing between field groups, use `stacked`. This adds a bottom margin to visually separate a field group from another field group or other form content below it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-stacked-margin.925715bfc9929d4e3b9fd4d4f7eca4ab.png)

 Content
--------

### Headings

Make field group headings succinct and descriptive. Use nouns for field group headings. Don't use verbs or sentences.

For details about the styling for field group headings, see the "Heading level and style" section on this page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-1.67c0a533653a193e500ed16961fc62bf.png)

Don't use full sentences or questions for field group headings.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-2.6257780e012c55f65d8137e03fa86a92.png)

Do use succinct headings.

### Checkbox and radio button groups

Don't use a field group when the only content is a lone checkbox group or radio button group. Instead, adjust the heading level and heading style on the label for the checkbox group or radio button group. For more details, see [checkboxes](/skyux/components/checkbox.md) and [radio buttons](/skyux/components/radio.md).

For example, if a "General" field group is followed by a "Supported credit cards" section that only includes a checkbox group, use the checkbox group's label to provide an `h3` heading with a `sky-font-heading-3` visual style. An additional heading from a field group would be unnecessary and confusing.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-3.cda3119ef1124310e92465ec16b410c6.png)

Don't use a field group with a lone checkbox group or radio button group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-4.89ae1ef70d7f469b5185f490a8e4edf2.png)

Do adjust the heading level and heading style of the label of a lone checkbox group or radio button group.

Use a field group to organize multiple related checkbox groups or radio button groups and also to organize a checkbox group or radio button group with other form fields. To maintain visual hierarchy within the field group, use the label of the checkbox group or radio button group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-5.06dea142be1d1fc3d03ff70344a33d61.png)

Do use a field group with multiple checkbox groups or radio button groups.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-6.da1778c68b08ba804d9629731ad9ffd6.png)

Do use a field group with a checkbox group or radio button group and other fields, such as input boxes.

 Related information
--------------------

### Components

*   [Checkbox](/skyux/components/checkbox.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Input box](/skyux/components/input-box.md)
*   [Radio button](/skyux/components/radio.md)
*   [Sectioned form](/skyux/components/sectioned-form.md)
*   [Wizard](/skyux/components/tabs-wizard.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/field-group/field-group.module.ts#L9) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 SkyFieldGroupModule
--------------------

Type: Module

`import { SkyFieldGroupModule } from '@skyux/forms';`

 SkyFieldGroupComponent
-----------------------

Type: Component

Selector: `sky-field-group`

Organizes form fields into a group.

### Inputs

#### `headingHidden: boolean`

Indicates whether to hide the `headingText`.

Default: `false`

#### `headingLevel: SkyFieldGroupHeadingLevel`

The semantic heading level in the document structure.

Default: `3`

#### `headingStyle: SkyFieldGroupHeadingStyle`

The heading [font style](/skyux/design/styles/typography#headings.md).

Default: `3`

#### `headingText: string`

The text to display as the field group's heading.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the field group heading. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `headingText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to the field group heading. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `stacked: boolean`

Whether the field group is stacked on another field group. When specified, the appropriate vertical spacing is automatically added to the field group.

Default: `false`

 SkyFieldGroupHeadingLevel
--------------------------

Type: Type alias

    type SkyFieldGroupHeadingLevel = 3 | 4

 SkyFieldGroupHeadingStyle
--------------------------

Type: Type alias

    type SkyFieldGroupHeadingStyle = 3 | 4

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyFieldGroupHarness
---------------------

Type: Class

`import { SkyFieldGroupHarness } from '@skyux/forms/testing';`

Harness for interacting with a field group component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getHeadingHidden(): Promise<boolean>`

Whether the heading is hidden.

#### Returns

`Promise<boolean>`

#### `getHeadingLevel(): Promise<SkyFieldGroupHeadingLevel>`

The semantic heading level used for the field group.

#### Returns

`Promise<SkyFieldGroupHeadingLevel>`

#### `getHeadingStyle(): Promise<SkyFieldGroupHeadingStyle>`

The heading style used for the field group.

#### Returns

`Promise<SkyFieldGroupHeadingStyle>`

#### `getHeadingText(): Promise<undefined | string>`

Gets the field group's heading text. If `headingHidden` is true, the text will still be returned.

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

#### `getHintText(): Promise<string>`

Gets the field group's hint text.

#### Returns

`Promise<string>`

#### `getStacked(): Promise<boolean>`

Whether the field group is stacked.

#### Returns

`Promise<boolean>`

#### `SkyFieldGroupHarness.with(filters: SkyFieldGroupHarnessFilters): HarnessPredicate<SkyFieldGroupHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFieldGroupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFieldGroupHarnessFilters`

#### Returns

`HarnessPredicate<SkyFieldGroupHarness>`

 SkyFieldGroupHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFieldGroupHarness` instances.

    interface SkyFieldGroupHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Development

                   Skip to Main Content

 Field group
===========

Field groups organize related form inputs and controls into semantic and visual groups on long or complex forms.

 Usage
------

### Use when

Use field groups to divide long or complex forms into groups of related inputs and controls. Field groups create semantic and visual groups to communicate context and relationships between the elements on a form.

Semantically, a field group creates an HTML `fieldset` element for its contents. It also creates a `legend` element and an `h3` or `h4` heading using the field group label.

Not every form requires field groups. Simple forms with a small number of inputs can use the modal title to establish context and don't require a field group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-usage-1.9c5fb738cc3acb80690aede56c460330.png)

Do use field groups to divide long forms into groups of related elements.

Use nested field groups to organize related elements into subgroups in form sections. To communicate hierarchy, adjust heading tags and the visual style of field group labels. For example, you can nest two field groups with `h4` headings in a form section with an `h3` heading. For more details, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-usage-2.9d5c6a752d1582abe0109b3e141aac4d.png)

Do use nested field groups to create subgroups in form sections.

### Don't use when

Don't use field groups when short or simple forms contain a small number of elements and don't require groups.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-usage-3.2c8b9e2befabac4b99d1ae8f7fa947a7.png)

Don't use field groups on short or simple forms that don't require groups.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-usage-4.fd2f6f7c180e0325938ad6f3aca13a38.png)

Do create short, simple forms without using field groups.

Don't use field groups to divide a complex task into multiple steps that users should complete in a particular order. Use a [wizard](/skyux/components/tabs-wizard.md) instead.

Don't use field groups for very long forms, especially when users don't need to interact with every group of inputs. Consider using a [sectioned form](/skyux/components/sectioned-form.md) instead.

 Anatomy
--------

1

Heading

2

Help inline button (optional)

3

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-anatomy.b2c9872f792c9bb6a30a47dc2e9bac3a.png)

 Options
--------

### Heading level and style

By default, field group headings create `h3` headings with a `sky-font-heading-3` visual style. When nesting field groups, adjust the semantic heading tag and the font style to maintain the semantic and visual hierarchy of the form. For more details, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

### Help inline button

When you need to supplement a field group with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a field group, use hint text. This persistent inline help can explain details such as:

*   The correct format
*   Any constraints on the inputs
*   Additional instructions or context, such as how data is used

### Stacked margin

To provide consistent vertical spacing between field groups, use `stacked`. This adds a bottom margin to visually separate a field group from another field group or other form content below it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-stacked-margin.925715bfc9929d4e3b9fd4d4f7eca4ab.png)

 Content
--------

### Headings

Make field group headings succinct and descriptive. Use nouns for field group headings. Don't use verbs or sentences.

For details about the styling for field group headings, see the "Heading level and style" section on this page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-1.67c0a533653a193e500ed16961fc62bf.png)

Don't use full sentences or questions for field group headings.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-2.6257780e012c55f65d8137e03fa86a92.png)

Do use succinct headings.

### Checkbox and radio button groups

Don't use a field group when the only content is a lone checkbox group or radio button group. Instead, adjust the heading level and heading style on the label for the checkbox group or radio button group. For more details, see [checkboxes](/skyux/components/checkbox.md) and [radio buttons](/skyux/components/radio.md).

For example, if a "General" field group is followed by a "Supported credit cards" section that only includes a checkbox group, use the checkbox group's label to provide an `h3` heading with a `sky-font-heading-3` visual style. An additional heading from a field group would be unnecessary and confusing.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-3.cda3119ef1124310e92465ec16b410c6.png)

Don't use a field group with a lone checkbox group or radio button group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-4.89ae1ef70d7f469b5185f490a8e4edf2.png)

Do adjust the heading level and heading style of the label of a lone checkbox group or radio button group.

Use a field group to organize multiple related checkbox groups or radio button groups and also to organize a checkbox group or radio button group with other form fields. To maintain visual hierarchy within the field group, use the label of the checkbox group or radio button group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-5.06dea142be1d1fc3d03ff70344a33d61.png)

Do use a field group with multiple checkbox groups or radio button groups.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-6.da1778c68b08ba804d9629731ad9ffd6.png)

Do use a field group with a checkbox group or radio button group and other fields, such as input boxes.

 Related information
--------------------

### Components

*   [Checkbox](/skyux/components/checkbox.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Input box](/skyux/components/input-box.md)
*   [Radio button](/skyux/components/radio.md)
*   [Sectioned form](/skyux/components/sectioned-form.md)
*   [Wizard](/skyux/components/tabs-wizard.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/field-group/field-group.module.ts#L9) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 SkyFieldGroupModule
--------------------

Type: Module

`import { SkyFieldGroupModule } from '@skyux/forms';`

 SkyFieldGroupComponent
-----------------------

Type: Component

Selector: `sky-field-group`

Organizes form fields into a group.

### Inputs

#### `headingHidden: boolean`

Indicates whether to hide the `headingText`.

Default: `false`

#### `headingLevel: SkyFieldGroupHeadingLevel`

The semantic heading level in the document structure.

Default: `3`

#### `headingStyle: SkyFieldGroupHeadingStyle`

The heading [font style](/skyux/design/styles/typography#headings.md).

Default: `3`

#### `headingText: string`

The text to display as the field group's heading.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the field group heading. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `headingText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to the field group heading. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `stacked: boolean`

Whether the field group is stacked on another field group. When specified, the appropriate vertical spacing is automatically added to the field group.

Default: `false`

 SkyFieldGroupHeadingLevel
--------------------------

Type: Type alias

    type SkyFieldGroupHeadingLevel = 3 | 4

 SkyFieldGroupHeadingStyle
--------------------------

Type: Type alias

    type SkyFieldGroupHeadingStyle = 3 | 4

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyFieldGroupHarness
---------------------

Type: Class

`import { SkyFieldGroupHarness } from '@skyux/forms/testing';`

Harness for interacting with a field group component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getHeadingHidden(): Promise<boolean>`

Whether the heading is hidden.

#### Returns

`Promise<boolean>`

#### `getHeadingLevel(): Promise<SkyFieldGroupHeadingLevel>`

The semantic heading level used for the field group.

#### Returns

`Promise<SkyFieldGroupHeadingLevel>`

#### `getHeadingStyle(): Promise<SkyFieldGroupHeadingStyle>`

The heading style used for the field group.

#### Returns

`Promise<SkyFieldGroupHeadingStyle>`

#### `getHeadingText(): Promise<undefined | string>`

Gets the field group's heading text. If `headingHidden` is true, the text will still be returned.

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

#### `getHintText(): Promise<string>`

Gets the field group's hint text.

#### Returns

`Promise<string>`

#### `getStacked(): Promise<boolean>`

Whether the field group is stacked.

#### Returns

`Promise<boolean>`

#### `SkyFieldGroupHarness.with(filters: SkyFieldGroupHarnessFilters): HarnessPredicate<SkyFieldGroupHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFieldGroupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFieldGroupHarnessFilters`

#### Returns

`HarnessPredicate<SkyFieldGroupHarness>`

 SkyFieldGroupHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFieldGroupHarness` instances.

    interface SkyFieldGroupHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Examples

                     Skip to Main Content

 Field group
===========

Field groups organize related form inputs and controls into semantic and visual groups on long or complex forms.Usage
------

### Use when

Use field groups to divide long or complex forms into groups of related inputs and controls. Field groups create semantic and visual groups to communicate context and relationships between the elements on a form.

Semantically, a field group creates an HTML `fieldset` element for its contents. It also creates a `legend` element and an `h3` or `h4` heading using the field group label.

Not every form requires field groups. Simple forms with a small number of inputs can use the modal title to establish context and don't require a field group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-usage-1.9c5fb738cc3acb80690aede56c460330.png)

Do use field groups to divide long forms into groups of related elements.

Use nested field groups to organize related elements into subgroups in form sections. To communicate hierarchy, adjust heading tags and the visual style of field group labels. For example, you can nest two field groups with `h4` headings in a form section with an `h3` heading. For more details, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-usage-2.9d5c6a752d1582abe0109b3e141aac4d.png)

Do use nested field groups to create subgroups in form sections.

### Don't use when

Don't use field groups when short or simple forms contain a small number of elements and don't require groups.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-usage-3.2c8b9e2befabac4b99d1ae8f7fa947a7.png)

Don't use field groups on short or simple forms that don't require groups.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-usage-4.fd2f6f7c180e0325938ad6f3aca13a38.png)

Do create short, simple forms without using field groups.

Don't use field groups to divide a complex task into multiple steps that users should complete in a particular order. Use a [wizard](/skyux/components/tabs-wizard.md) instead.

Don't use field groups for very long forms, especially when users don't need to interact with every group of inputs. Consider using a [sectioned form](/skyux/components/sectioned-form.md) instead.

 Anatomy
--------

1

Heading

2

Help inline button (optional)

3

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-anatomy.b2c9872f792c9bb6a30a47dc2e9bac3a.png)

 Options
--------

### Heading level and style

By default, field group headings create `h3` headings with a `sky-font-heading-3` visual style. When nesting field groups, adjust the semantic heading tag and the font style to maintain the semantic and visual hierarchy of the form. For more details, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

### Help inline button

When you need to supplement a field group with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a field group, use hint text. This persistent inline help can explain details such as:

*   The correct format
*   Any constraints on the inputs
*   Additional instructions or context, such as how data is used

### Stacked margin

To provide consistent vertical spacing between field groups, use `stacked`. This adds a bottom margin to visually separate a field group from another field group or other form content below it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-stacked-margin.925715bfc9929d4e3b9fd4d4f7eca4ab.png)

 Content
--------

### Headings

Make field group headings succinct and descriptive. Use nouns for field group headings. Don't use verbs or sentences.

For details about the styling for field group headings, see the "Heading level and style" section on this page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-1.67c0a533653a193e500ed16961fc62bf.png)

Don't use full sentences or questions for field group headings.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-2.6257780e012c55f65d8137e03fa86a92.png)

Do use succinct headings.

### Checkbox and radio button groups

Don't use a field group when the only content is a lone checkbox group or radio button group. Instead, adjust the heading level and heading style on the label for the checkbox group or radio button group. For more details, see [checkboxes](/skyux/components/checkbox.md) and [radio buttons](/skyux/components/radio.md).

For example, if a "General" field group is followed by a "Supported credit cards" section that only includes a checkbox group, use the checkbox group's label to provide an `h3` heading with a `sky-font-heading-3` visual style. An additional heading from a field group would be unnecessary and confusing.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-3.cda3119ef1124310e92465ec16b410c6.png)

Don't use a field group with a lone checkbox group or radio button group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-4.89ae1ef70d7f469b5185f490a8e4edf2.png)

Do adjust the heading level and heading style of the label of a lone checkbox group or radio button group.

Use a field group to organize multiple related checkbox groups or radio button groups and also to organize a checkbox group or radio button group with other form fields. To maintain visual hierarchy within the field group, use the label of the checkbox group or radio button group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-5.06dea142be1d1fc3d03ff70344a33d61.png)

Do use a field group with multiple checkbox groups or radio button groups.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-6.da1778c68b08ba804d9629731ad9ffd6.png)

Do use a field group with a checkbox group or radio button group and other fields, such as input boxes.

 Related information
--------------------

### Components

*   [Checkbox](/skyux/components/checkbox.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Input box](/skyux/components/input-box.md)
*   [Radio button](/skyux/components/radio.md)
*   [Sectioned form](/skyux/components/sectioned-form.md)
*   [Wizard](/skyux/components/tabs-wizard.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/field-group/field-group.module.ts#L9) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 SkyFieldGroupModule
--------------------

Type: Module

`import { SkyFieldGroupModule } from '@skyux/forms';`

 SkyFieldGroupComponent
-----------------------

Type: Component

Selector: `sky-field-group`

Organizes form fields into a group.

### Inputs

#### `headingHidden: boolean`

Indicates whether to hide the `headingText`.

Default: `false`

#### `headingLevel: SkyFieldGroupHeadingLevel`

The semantic heading level in the document structure.

Default: `3`

#### `headingStyle: SkyFieldGroupHeadingStyle`

The heading [font style](/skyux/design/styles/typography#headings.md).

Default: `3`

#### `headingText: string`

The text to display as the field group's heading.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the field group heading. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `headingText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to the field group heading. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `stacked: boolean`

Whether the field group is stacked on another field group. When specified, the appropriate vertical spacing is automatically added to the field group.

Default: `false`

 SkyFieldGroupHeadingLevel
--------------------------

Type: Type alias

    type SkyFieldGroupHeadingLevel = 3 | 4

 SkyFieldGroupHeadingStyle
--------------------------

Type: Type alias

    type SkyFieldGroupHeadingStyle = 3 | 4

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyFieldGroupHarness
---------------------

Type: Class

`import { SkyFieldGroupHarness } from '@skyux/forms/testing';`

Harness for interacting with a field group component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getHeadingHidden(): Promise<boolean>`

Whether the heading is hidden.

#### Returns

`Promise<boolean>`

#### `getHeadingLevel(): Promise<SkyFieldGroupHeadingLevel>`

The semantic heading level used for the field group.

#### Returns

`Promise<SkyFieldGroupHeadingLevel>`

#### `getHeadingStyle(): Promise<SkyFieldGroupHeadingStyle>`

The heading style used for the field group.

#### Returns

`Promise<SkyFieldGroupHeadingStyle>`

#### `getHeadingText(): Promise<undefined | string>`

Gets the field group's heading text. If `headingHidden` is true, the text will still be returned.

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

#### `getHintText(): Promise<string>`

Gets the field group's hint text.

#### Returns

`Promise<string>`

#### `getStacked(): Promise<boolean>`

Whether the field group is stacked.

#### Returns

`Promise<boolean>`

#### `SkyFieldGroupHarness.with(filters: SkyFieldGroupHarnessFilters): HarnessPredicate<SkyFieldGroupHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFieldGroupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFieldGroupHarnessFilters`

#### Returns

`HarnessPredicate<SkyFieldGroupHarness>`

 SkyFieldGroupHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFieldGroupHarness` instances.

    interface SkyFieldGroupHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

### Field group with basic setup

Edit in StackBlitz

### Address

Show help content for

We use this address for your end-of-year statement.

Street address

City

State

AK AZ AL AR CA CO CT DE DC FL GA HI ID IL IN IA KS KY LA ME MD MA MI MN MS MO MT NE NV NH NJ NM NY NC ND OH OK OR PA RI SC SD TN TX UT VT VA WA WV WI WY

Zip code

Show code

Copy

    <div class="sky-padding-even-lg">
      <form [formGroup]="formGroup">
        <sky-field-group
          headingText="Address"
          hintText="We use this address for your end-of-year statement."
          [headingStyle]="4"
          [helpPopoverContent]="helpPopoverContent"
        >
          <sky-fluid-grid gutterSize="small" [disableMargin]="true">
            <sky-row>
              <sky-column [screenXSmall]="12">
                <sky-input-box labelText="Street address" stacked="true">
                  <input
                    formControlName="streetAddress"
                    spellcheck="false"
                    type="text"
                  />
                </sky-input-box>
              </sky-column>
            </sky-row>
            <sky-row>
              <sky-column [screenSmall]="5">
                <sky-input-box labelText="City" stacked="true">
                  <input formControlName="city" spellcheck="false" type="text" />
                </sky-input-box>
              </sky-column>
              <sky-column [screenSmall]="5" [screenXSmall]="8">
                <sky-input-box labelText="State" stacked="true">
                  <select formControlName="state">
                    <option [attr.value]="undefined"></option>
                    @for (state of states; track state) {
                      <option value="state">
                        {{ state }}
                      </option>
                    }
                  </select>
                </sky-input-box>
              </sky-column>
              <sky-column [screenSmall]="2" [screenXSmall]="4">
                <sky-input-box labelText="Zip code">
                  <input formControlName="zipCode" maxlength="5" type="text" />
                </sky-input-box>
              </sky-column>
            </sky-row>
          </sky-fluid-grid>
        </sky-field-group>
      </form>
    </div>

Copy

    import { Component, inject } from '@angular/core';
    import {
      FormBuilder,
      FormGroup,
      FormsModule,
      ReactiveFormsModule,
    } from '@angular/forms';
    import { SkyFieldGroupModule, SkyInputBoxModule } from '@skyux/forms';
    import { SkyFluidGridModule } from '@skyux/layout';
    
    /**
     * @title Field group with basic setup
     */
    @Component({
      selector: 'app-forms-field-group-basic-example',
      templateUrl: './example.component.html',
      imports: [
        FormsModule,
        ReactiveFormsModule,
        SkyFieldGroupModule,
        SkyFluidGridModule,
        SkyInputBoxModule,
      ],
    })
    export class FormsFieldGroupBasicExampleComponent {
      #formBuilder: FormBuilder = inject(FormBuilder);
    
      protected formGroup: FormGroup;
      protected helpPopoverContent =
        'We use your address to validate your application with regulatory agencies and to send correspondence related to your application.';
    
      protected states = [
        'AK',
        'AZ',
        'AL',
        'AR',
        'CA',
        'CO',
        'CT',
        'DE',
        'DC',
        'FL',
        'GA',
        'HI',
        'ID',
        'IL',
        'IN',
        'IA',
        'KS',
        'KY',
        'LA',
        'ME',
        'MD',
        'MA',
        'MI',
        'MN',
        'MS',
        'MO',
        'MT',
        'NE',
        'NV',
        'NH',
        'NJ',
        'NM',
        'NY',
        'NC',
        'ND',
        'OH',
        'OK',
        'OR',
        'PA',
        'RI',
        'SC',
        'SD',
        'TN',
        'TX',
        'UT',
        'VT',
        'VA',
        'WA',
        'WV',
        'WI',
        'WY',
      ];
    
      constructor() {
        this.formGroup = this.#formBuilder.group({
          streetAddress: this.#formBuilder.control(undefined),
          city: this.#formBuilder.control(undefined),
          state: this.#formBuilder.control(undefined),
          zipCode: this.#formBuilder.control(undefined),
        });
      }
    }
### Field group with help key

Edit in StackBlitz

### Address

Show help content for

We use this address for your end-of-year statement.

Street address

City

State

AK AZ AL AR CA CO CT DE DC FL GA HI ID IL IN IA KS KY LA ME MD MA MI MN MS MO MT NE NV NH NJ NM NY NC ND OH OK OR PA RI SC SD TN TX UT VT VA WA WV WI WY

Zip code

Show code

Copy

    <div class="sky-padding-even-lg">
      <form [formGroup]="formGroup">
        <sky-field-group
          headingText="Address"
          helpKey="address-help"
          hintText="We use this address for your end-of-year statement."
          [headingStyle]="4"
        >
          <sky-fluid-grid gutterSize="small" [disableMargin]="true">
            <sky-row>
              <sky-column [screenXSmall]="12">
                <sky-input-box labelText="Street address" stacked="true">
                  <input
                    formControlName="streetAddress"
                    spellcheck="false"
                    type="text"
                  />
                </sky-input-box>
              </sky-column>
            </sky-row>
            <sky-row>
              <sky-column [screenSmall]="5">
                <sky-input-box labelText="City" stacked="true">
                  <input formControlName="city" spellcheck="false" type="text" />
                </sky-input-box>
              </sky-column>
              <sky-column [screenSmall]="5" [screenXSmall]="8">
                <sky-input-box labelText="State" stacked="true">
                  <select formControlName="state">
                    <option [attr.value]="undefined"></option>
                    @for (state of states; track state) {
                      <option value="state">
                        {{ state }}
                      </option>
                    }
                  </select>
                </sky-input-box>
              </sky-column>
              <sky-column [screenSmall]="2" [screenXSmall]="4">
                <sky-input-box labelText="Zip code">
                  <input formControlName="zipCode" maxlength="5" type="text" />
                </sky-input-box>
              </sky-column>
            </sky-row>
          </sky-fluid-grid>
        </sky-field-group>
      </form>
    </div>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import {
      SkyHelpTestingController,
      SkyHelpTestingModule,
    } from '@skyux/core/testing';
    import { SkyFieldGroupHarness } from '@skyux/forms/testing';
    
    import { FormsFieldGroupHelpKeyExampleComponent } from './example.component';
    
    describe('Field group', () => {
      async function setupTest(): Promise<{
        fieldGroupHarness: SkyFieldGroupHarness;
        fixture: ComponentFixture<FormsFieldGroupHelpKeyExampleComponent>;
        helpController: SkyHelpTestingController;
      }> {
        const fixture = TestBed.createComponent(
          FormsFieldGroupHelpKeyExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.loader(fixture);
        const fieldGroupHarness = await loader.getHarness(SkyFieldGroupHarness);
        const helpController = TestBed.inject(SkyHelpTestingController);
    
        return { fieldGroupHarness, fixture, helpController };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [FormsFieldGroupHelpKeyExampleComponent, SkyHelpTestingModule],
        });
      });
    
      it('should have the correct help key', async () => {
        const { fieldGroupHarness, helpController } = await setupTest();
    
        await fieldGroupHarness.clickHelpInline();
    
        helpController.expectCurrentHelpKey('address-help');
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
    import { SkyFieldGroupModule, SkyInputBoxModule } from '@skyux/forms';
    import { SkyFluidGridModule } from '@skyux/layout';
    
    /**
     * @title Field group with help key
     */
    @Component({
      selector: 'app-forms-field-group-help-key-example',
      templateUrl: './example.component.html',
      imports: [
        FormsModule,
        ReactiveFormsModule,
        SkyFieldGroupModule,
        SkyFluidGridModule,
        SkyInputBoxModule,
      ],
    })
    export class FormsFieldGroupHelpKeyExampleComponent {
      #formBuilder: FormBuilder = inject(FormBuilder);
    
      protected formGroup: FormGroup;
      protected states = [
        'AK',
        'AZ',
        'AL',
        'AR',
        'CA',
        'CO',
        'CT',
        'DE',
        'DC',
        'FL',
        'GA',
        'HI',
        'ID',
        'IL',
        'IN',
        'IA',
        'KS',
        'KY',
        'LA',
        'ME',
        'MD',
        'MA',
        'MI',
        'MN',
        'MS',
        'MO',
        'MT',
        'NE',
        'NV',
        'NH',
        'NJ',
        'NM',
        'NY',
        'NC',
        'ND',
        'OH',
        'OK',
        'OR',
        'PA',
        'RI',
        'SC',
        'SD',
        'TN',
        'TX',
        'UT',
        'VT',
        'VA',
        'WA',
        'WV',
        'WI',
        'WY',
      ];
    
      constructor() {
        this.formGroup = this.#formBuilder.group({
          streetAddress: this.#formBuilder.control(undefined),
          city: this.#formBuilder.control(undefined),
          state: this.#formBuilder.control(undefined),
          zipCode: this.#formBuilder.control(undefined),
        });
      }
    }

# Testing

                   Skip to Main Content

 Field group
===========

Field groups organize related form inputs and controls into semantic and visual groups on long or complex forms.

 Usage
------

### Use when

Use field groups to divide long or complex forms into groups of related inputs and controls. Field groups create semantic and visual groups to communicate context and relationships between the elements on a form.

Semantically, a field group creates an HTML `fieldset` element for its contents. It also creates a `legend` element and an `h3` or `h4` heading using the field group label.

Not every form requires field groups. Simple forms with a small number of inputs can use the modal title to establish context and don't require a field group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-usage-1.9c5fb738cc3acb80690aede56c460330.png)

Do use field groups to divide long forms into groups of related elements.

Use nested field groups to organize related elements into subgroups in form sections. To communicate hierarchy, adjust heading tags and the visual style of field group labels. For example, you can nest two field groups with `h4` headings in a form section with an `h3` heading. For more details, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-usage-2.9d5c6a752d1582abe0109b3e141aac4d.png)

Do use nested field groups to create subgroups in form sections.

### Don't use when

Don't use field groups when short or simple forms contain a small number of elements and don't require groups.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-usage-3.2c8b9e2befabac4b99d1ae8f7fa947a7.png)

Don't use field groups on short or simple forms that don't require groups.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-usage-4.fd2f6f7c180e0325938ad6f3aca13a38.png)

Do create short, simple forms without using field groups.

Don't use field groups to divide a complex task into multiple steps that users should complete in a particular order. Use a [wizard](/skyux/components/tabs-wizard.md) instead.

Don't use field groups for very long forms, especially when users don't need to interact with every group of inputs. Consider using a [sectioned form](/skyux/components/sectioned-form.md) instead.

 Anatomy
--------

1

Heading

2

Help inline button (optional)

3

Hint text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-anatomy.b2c9872f792c9bb6a30a47dc2e9bac3a.png)

 Options
--------

### Heading level and style

By default, field group headings create `h3` headings with a `sky-font-heading-3` visual style. When nesting field groups, adjust the semantic heading tag and the font style to maintain the semantic and visual hierarchy of the form. For more details, see the [form design guidelines](/skyux/design/guidelines/form-design.md).

### Help inline button

When you need to supplement a field group with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a field group, use hint text. This persistent inline help can explain details such as:

*   The correct format
*   Any constraints on the inputs
*   Additional instructions or context, such as how data is used

### Stacked margin

To provide consistent vertical spacing between field groups, use `stacked`. This adds a bottom margin to visually separate a field group from another field group or other form content below it. For more information about spacing on forms, see the [form layout guidelines](/skyux/design/guidelines/form-design.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-stacked-margin.925715bfc9929d4e3b9fd4d4f7eca4ab.png)

 Content
--------

### Headings

Make field group headings succinct and descriptive. Use nouns for field group headings. Don't use verbs or sentences.

For details about the styling for field group headings, see the "Heading level and style" section on this page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-1.67c0a533653a193e500ed16961fc62bf.png)

Don't use full sentences or questions for field group headings.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-2.6257780e012c55f65d8137e03fa86a92.png)

Do use succinct headings.

### Checkbox and radio button groups

Don't use a field group when the only content is a lone checkbox group or radio button group. Instead, adjust the heading level and heading style on the label for the checkbox group or radio button group. For more details, see [checkboxes](/skyux/components/checkbox.md) and [radio buttons](/skyux/components/radio.md).

For example, if a "General" field group is followed by a "Supported credit cards" section that only includes a checkbox group, use the checkbox group's label to provide an `h3` heading with a `sky-font-heading-3` visual style. An additional heading from a field group would be unnecessary and confusing.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-3.cda3119ef1124310e92465ec16b410c6.png)

Don't use a field group with a lone checkbox group or radio button group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-4.89ae1ef70d7f469b5185f490a8e4edf2.png)

Do adjust the heading level and heading style of the label of a lone checkbox group or radio button group.

Use a field group to organize multiple related checkbox groups or radio button groups and also to organize a checkbox group or radio button group with other form fields. To maintain visual hierarchy within the field group, use the label of the checkbox group or radio button group.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-5.06dea142be1d1fc3d03ff70344a33d61.png)

Do use a field group with multiple checkbox groups or radio button groups.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/field-group/field-group-content-6.da1778c68b08ba804d9629731ad9ffd6.png)

Do use a field group with a checkbox group or radio button group and other fields, such as input boxes.

 Related information
--------------------

### Components

*   [Checkbox](/skyux/components/checkbox.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Input box](/skyux/components/input-box.md)
*   [Radio button](/skyux/components/radio.md)
*   [Sectioned form](/skyux/components/sectioned-form.md)
*   [Wizard](/skyux/components/tabs-wizard.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/field-group/field-group.module.ts#L9) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 SkyFieldGroupModule
--------------------

Type: Module

`import { SkyFieldGroupModule } from '@skyux/forms';`

 SkyFieldGroupComponent
-----------------------

Type: Component

Selector: `sky-field-group`

Organizes form fields into a group.

### Inputs

#### `headingHidden: boolean`

Indicates whether to hide the `headingText`.

Default: `false`

#### `headingLevel: SkyFieldGroupHeadingLevel`

The semantic heading level in the document structure.

Default: `3`

#### `headingStyle: SkyFieldGroupHeadingStyle`

The heading [font style](/skyux/design/styles/typography#headings.md).

Default: `3`

#### `headingText: string`

The text to display as the field group's heading.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is placed beside the field group heading. Clicking the button invokes [global help](/skyux/learn/develop/global-help.md) as configured by the application. This property only applies when `headingText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to the field group heading. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `hintText: string | undefined`

[Persistent inline help text](/skyux/design/guidelines/user-assistance#inline-help.md) that provides additional context to the user.

#### `stacked: boolean`

Whether the field group is stacked on another field group. When specified, the appropriate vertical spacing is automatically added to the field group.

Default: `false`

 SkyFieldGroupHeadingLevel
--------------------------

Type: Type alias

    type SkyFieldGroupHeadingLevel = 3 | 4

 SkyFieldGroupHeadingStyle
--------------------------

Type: Type alias

    type SkyFieldGroupHeadingStyle = 3 | 4

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyFieldGroupHarness
---------------------

Type: Class

`import { SkyFieldGroupHarness } from '@skyux/forms/testing';`

Harness for interacting with a field group component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getHeadingHidden(): Promise<boolean>`

Whether the heading is hidden.

#### Returns

`Promise<boolean>`

#### `getHeadingLevel(): Promise<SkyFieldGroupHeadingLevel>`

The semantic heading level used for the field group.

#### Returns

`Promise<SkyFieldGroupHeadingLevel>`

#### `getHeadingStyle(): Promise<SkyFieldGroupHeadingStyle>`

The heading style used for the field group.

#### Returns

`Promise<SkyFieldGroupHeadingStyle>`

#### `getHeadingText(): Promise<undefined | string>`

Gets the field group's heading text. If `headingHidden` is true, the text will still be returned.

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

#### `getHintText(): Promise<string>`

Gets the field group's hint text.

#### Returns

`Promise<string>`

#### `getStacked(): Promise<boolean>`

Whether the field group is stacked.

#### Returns

`Promise<boolean>`

#### `SkyFieldGroupHarness.with(filters: SkyFieldGroupHarnessFilters): HarnessPredicate<SkyFieldGroupHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyFieldGroupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyFieldGroupHarnessFilters`

#### Returns

`HarnessPredicate<SkyFieldGroupHarness>`

 SkyFieldGroupHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyFieldGroupHarness` instances.

    interface SkyFieldGroupHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.