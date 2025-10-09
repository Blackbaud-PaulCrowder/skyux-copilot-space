                 

 ID
==

The ID directive assigns a unique ID to an element and provides that ID to other elements.

 Usage
------

### Use when

Use the ID directive when one HTML element must be associated with another HTML element by its `id` attribute. For example, `input` and `label` elements must be associated by a unique ID so that clicking on the label sets focus to the input. Associating a label to its input also enables assistive technologies to describe the input to the user using the label text.

### Don't use when

Don't use the ID directive when an element does not need to be referenced by its ID attribute because doing so adds unnecessary overhead to an application.

Don't assign hard-coded IDs to elements because this causes collisions if IDs are not unique. Always use the ID directive to assign IDs because it guarantees that IDs are unique.

 Installation
-------------

NPM package

`@skyux/core`[View in NPM](https://www.npmjs.com/package/@skyux/core) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/core/src/lib/modules/id/id.module.ts#L9) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/core`Copy None found.

 SkyIdModule
------------

Type: Module

`import { SkyIdModule } from '@skyux/core';`

 SkyIdDirective
---------------

Type: Directive

Selector: `[skyId]`

Sets the element's `id` attribute to a unique ID. To reference this unique ID on other elements, such as in a `label` element's `for` attribute, assign this directive to a template reference variable, then use its `id` property.

 SkyIdService
-------------

Type: Service

Generates unique IDs to be used with HTML elements.

### Methods

#### `generateId(): string`

#### Returns

`string`