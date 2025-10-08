# Design

                 Skip to Main Content

 Card (deprecated)
=================

Cards create small containers that highlight important information, and you group cards together to display information about related items.

Card is deprecated in favor of other [content containers](/skyux/design/guidelines/content-containers.md). For more information, see the [card deprecation instructions](/skyux/learn/develop/deprecation/card.md).

 Usage
------

Cards can handle a variety of scenarios, but multiple cards are generally grouped together to display information about related items. For example, cards can present a stack or carousel of to-do items or a matrix of images.

Cards frequently present users with a call to action. They can use visual cues to alert users about the need for action, and they can also include actions directly on the cards.

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/card/card.module.ts#L38) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyCardModule
--------------

Type: Module

`import { SkyCardModule } from '@skyux/layout';`

Warning: **Deprecated.** `SkyCardModule` is deprecated. For other SKY UX components that group and list content, see the content containers guidelines. For more information, see [https://developer.blackbaud.com/skyux/design/guidelines/content-containers](/skyux/design/guidelines/content-containers.md).

 SkyCardComponent
-----------------

Type: Component

Selector: `sky-card`

Warning: **Deprecated.** `SkyCardComponent` is deprecated. For other SKY UX components that group and list content, see the content containers guidelines. For more information, see [https://developer.blackbaud.com/skyux/design/guidelines/content-containers](/skyux/design/guidelines/content-containers.md).

Creates a a small container to highlight important information.

### Inputs

#### `selectable: boolean | undefined`

Whether to display a checkbox to the right of the card title. Users can select multiple checkboxes and perform actions on the selected cards.

Default: `false`

#### `selected: boolean | undefined`

Whether the card is selected. This only applies to card where `selectable` is set to `true`.

Default: `false`

#### `size: string`

The size of the card. The valid options are `"large"` and `"small"`.

Default: `"large"`

### Outputs

#### `selectedChange: EventEmitter<boolean>`

Fires when users select or deselect the card.

 SkyCardTitleComponent
----------------------

Type: Component

Selector: `sky-card-title`

Specifies a title to identify what the card represents.

 SkyCardContentComponent
------------------------

Type: Component

Selector: `sky-card-content`

Specifies the content to display in the body of the card.

 SkyCardActionsComponent
------------------------

Type: Component

Selector: `sky-card-actions`

Specifies an action that users can perform on the card.

# Development

                 Skip to Main Content

 Card (deprecated)
=================

Cards create small containers that highlight important information, and you group cards together to display information about related items.

Card is deprecated in favor of other [content containers](/skyux/design/guidelines/content-containers.md). For more information, see the [card deprecation instructions](/skyux/learn/develop/deprecation/card.md).

 Usage
------

Cards can handle a variety of scenarios, but multiple cards are generally grouped together to display information about related items. For example, cards can present a stack or carousel of to-do items or a matrix of images.

Cards frequently present users with a call to action. They can use visual cues to alert users about the need for action, and they can also include actions directly on the cards.

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/card/card.module.ts#L38) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyCardModule
--------------

Type: Module

`import { SkyCardModule } from '@skyux/layout';`

Warning: **Deprecated.** `SkyCardModule` is deprecated. For other SKY UX components that group and list content, see the content containers guidelines. For more information, see [https://developer.blackbaud.com/skyux/design/guidelines/content-containers](/skyux/design/guidelines/content-containers.md).

 SkyCardComponent
-----------------

Type: Component

Selector: `sky-card`

Warning: **Deprecated.** `SkyCardComponent` is deprecated. For other SKY UX components that group and list content, see the content containers guidelines. For more information, see [https://developer.blackbaud.com/skyux/design/guidelines/content-containers](/skyux/design/guidelines/content-containers.md).

Creates a a small container to highlight important information.

### Inputs

#### `selectable: boolean | undefined`

Whether to display a checkbox to the right of the card title. Users can select multiple checkboxes and perform actions on the selected cards.

Default: `false`

#### `selected: boolean | undefined`

Whether the card is selected. This only applies to card where `selectable` is set to `true`.

Default: `false`

#### `size: string`

The size of the card. The valid options are `"large"` and `"small"`.

Default: `"large"`

### Outputs

#### `selectedChange: EventEmitter<boolean>`

Fires when users select or deselect the card.

 SkyCardTitleComponent
----------------------

Type: Component

Selector: `sky-card-title`

Specifies a title to identify what the card represents.

 SkyCardContentComponent
------------------------

Type: Component

Selector: `sky-card-content`

Specifies the content to display in the body of the card.

 SkyCardActionsComponent
------------------------

Type: Component

Selector: `sky-card-actions`

Specifies an action that users can perform on the card.

# Examples

                 Skip to Main Content

 Card (deprecated)
=================

Cards create small containers that highlight important information, and you group cards together to display information about related items.

Card is deprecated in favor of other [content containers](/skyux/design/guidelines/content-containers.md). For more information, see the [card deprecation instructions](/skyux/learn/develop/deprecation/card.md).

 Usage
------

Cards can handle a variety of scenarios, but multiple cards are generally grouped together to display information about related items. For example, cards can present a stack or carousel of to-do items or a matrix of images.

Cards frequently present users with a call to action. They can use visual cues to alert users about the need for action, and they can also include actions directly on the cards.

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/card/card.module.ts#L38) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyCardModule
--------------

Type: Module

`import { SkyCardModule } from '@skyux/layout';`

Warning: **Deprecated.** `SkyCardModule` is deprecated. For other SKY UX components that group and list content, see the content containers guidelines. For more information, see [https://developer.blackbaud.com/skyux/design/guidelines/content-containers](/skyux/design/guidelines/content-containers.md).

 SkyCardComponent
-----------------

Type: Component

Selector: `sky-card`

Warning: **Deprecated.** `SkyCardComponent` is deprecated. For other SKY UX components that group and list content, see the content containers guidelines. For more information, see [https://developer.blackbaud.com/skyux/design/guidelines/content-containers](/skyux/design/guidelines/content-containers.md).

Creates a a small container to highlight important information.

### Inputs

#### `selectable: boolean | undefined`

Whether to display a checkbox to the right of the card title. Users can select multiple checkboxes and perform actions on the selected cards.

Default: `false`

#### `selected: boolean | undefined`

Whether the card is selected. This only applies to card where `selectable` is set to `true`.

Default: `false`

#### `size: string`

The size of the card. The valid options are `"large"` and `"small"`.

Default: `"large"`

### Outputs

#### `selectedChange: EventEmitter<boolean>`

Fires when users select or deselect the card.

 SkyCardTitleComponent
----------------------

Type: Component

Selector: `sky-card-title`

Specifies a title to identify what the card represents.

 SkyCardContentComponent
------------------------

Type: Component

Selector: `sky-card-content`

Specifies the content to display in the body of the card.

 SkyCardActionsComponent
------------------------

Type: Component

Selector: `sky-card-actions`

Specifies an action that users can perform on the card.