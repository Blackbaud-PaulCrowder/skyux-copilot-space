               

 Definition list (deprecated)
============================

Definition lists display label-value pairs.

Definition list is deprecated in favor of [description list](/skyux/components/description-list.md). For more information, see the [definition list deprecation instructions](/skyux/learn/develop/deprecation/definition-list.md).

 Content
--------

Don't use colons after definition list labels.

 Related information
--------------------

### Components

*   [Alert](/skyux/components/alert.md)
*   [Toolbar](/skyux/components/toolbar.md)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/definition-list/definition-list.module.ts#L32) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyDefinitionListModule
------------------------

Type: Module

`import { SkyDefinitionListModule } from '@skyux/layout';`

Warning: **Deprecated.** Use `SkyDescriptionListModule` instead.

 SkyDefinitionListComponent
---------------------------

Type: Component

Selector: `sky-definition-list`

Warning: **Deprecated.** Use `SkyDescriptionListComponent` instead.

Creates a definition list to display label-value pairs.

### Inputs

#### `defaultValue: string | undefined`

The default value to display when no value is provided for a label-value pair.

Default: `"None found"`

#### `labelWidth: string | undefined`

The width of the label portion of the definition list.

Default: `"90px"`

 SkyDefinitionListHeadingComponent
----------------------------------

Type: Component

Selector: `sky-definition-list-heading`

Specifies a title for the definition list.

 SkyDefinitionListContentComponent
----------------------------------

Type: Component

Selector: `sky-definition-list-content`

Warning: **Deprecated.** Use `SkyDescriptionListContentComponent` instead.

Wraps the label-value pairs in the definition list.

 SkyDefinitionListLabelComponent
--------------------------------

Type: Component

Selector: `sky-definition-list-label`

Warning: **Deprecated.** Use `SkyDescriptionListTermComponent` instead.

Specifies the label in a label-value pair.

 SkyDefinitionListValueComponent
--------------------------------

Type: Component

Selector: `sky-definition-list-value`

Warning: **Deprecated.** Use `SkyDescriptionListDescriptionComponent` instead.

Specifies the value in a label-value pair.