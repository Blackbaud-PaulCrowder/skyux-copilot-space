                     

 Inline delete confirmation
==========================

The inline delete confirmation appears when users delete an item in a list and requires them to confirm that they want to delete the item.

 Usage
------

### Use when

Use the inline delete confirmation when users need to confirm that they want to delete an item from a list.

Keep in mind that you should not delete items from lists when they are complex enough to have their own record pages. For lists with such items, do not include delete actions in the [context-menu dropdowns](/skyux/components/dropdown.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/inline-delete/inline-delete-usage-1.5c68033daca05cdfa1b81dfe3c46b6d7.png)

Do use inline delete confirmation when deleting an item from a list.

### Don't use when

Don't use inline delete confirmation when users need to confirm that they want to delete an item outside of a list. Use a [confirm dialog](/skyux/components/confirm.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/inline-delete/inline-delete-usage-2.1450df1653090b1bfb5a9c2e91c086c4.png)

Don't use inline delete confirmation for an item outside of a list.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/inline-delete/inline-delete-usage-3.99e556579bf8d2211385e2349d2aaf66.png)

Do use a confirm dialog when users need to confirm that they want to delete an item outside of a list.

 Anatomy
--------

1

Delete button

2

Cancel button

3

Overlay

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/inline-delete/inline-delete-anatomy.44c968caff3612b51bb533560258a2f9.png)

 Behavior and states
--------------------

### Delete button

The inline delete confirmation uses the `sky-btn-danger` (red) style for the Delete button to visually indicate that the action deletes existing data.

 Related information
--------------------

### Components

*   [Confirm](/skyux/components/confirm.md)
*   [Dropdown](/skyux/components/dropdown.md)

### Guidelines

*   [Manage records](/skyux/design/guidelines/managing-records.md)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/inline-delete/inline-delete.module.ts#L13) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyInlineDeleteModule
----------------------

Type: Module

`import { SkyInlineDeleteModule } from '@skyux/layout';`

 SkyInlineDeleteComponent
-------------------------

Type: Component

Selector: `sky-inline-delete`

### Inputs

#### `pending: boolean | undefined`

Whether the deletion is pending.

Default: `false`

### Outputs

#### `cancelTriggered: EventEmitter<void>`

Fires when users click the cancel button.

#### `deleteTriggered: EventEmitter<void>`

Fires when users click the delete button.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyInlineDeleteHarness
-----------------------

Type: Class

`import { SkyInlineDeleteHarness } from '@skyux/layout/testing';`

Harness for interacting with an inline delete component in tests.

### Methods

#### `clickCancelButton(): Promise<void>`

Clicks the cancel button.

#### Returns

`Promise<void>`

#### `clickDeleteButton(): Promise<void>`

Clicks the delete button.

#### Returns

`Promise<void>`

#### `isPending(): Promise<boolean>`

Whether the inline delete is pending.

#### Returns

`Promise<boolean>`

#### `SkyInlineDeleteHarness.with(filters: SkyInlineDeleteHarnessFilters): HarnessPredicate<SkyInlineDeleteHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyInlineDeleteHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyInlineDeleteHarnessFilters`

#### Returns

`HarnessPredicate<SkyInlineDeleteHarness>`

 SkyInlineDeleteHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyInlineDeleteHarness` instances.

    interface SkyInlineDeleteHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value. 

Context menu for Context menu for Context menu for