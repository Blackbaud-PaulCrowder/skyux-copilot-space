               

 List paging (deprecated)
========================

The list paging component displays a pagination control for a [SKY UX-themed list of data](/skyux/components/list-overview.md).

Lists and their features are deprecated. We will remove them in a future major version. We recommend using [data manager](/skyux/components/data-manager.md) and [paging](/skyux/components/paging.md) instead.

 Related information
--------------------

### Components

*   [List overview](/skyux/components/list-overview.md)
*   [List filters](/skyux/components/list-filters.md)
*   [List toolbar](/skyux/components/list-toolbar.md)
*   [List view checklist](/skyux/components/list-view-checklist.md)
*   [List view grid](/skyux/components/list-view-grid.md)
*   [Paging](/skyux/components/paging.md)

 Installation
-------------

NPM package

`@skyux/list-builder`[View in NPM](https://www.npmjs.com/package/@skyux/list-builder) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/list-builder/src/lib/modules/list-paging/list-paging.module.ts#L15) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/list-builder`Copy None found.

 SkyListPagingModule
--------------------

Type: Module

`import { SkyListPagingModule } from '@skyux/list-builder';`

Warning: **Deprecated.** List builder and its features are deprecated. Use data manager instead. For more information, see [https://developer.blackbaud.com/skyux/components/data-manager](/skyux/components/data-manager.md).

 SkyListPagingComponent
-----------------------

Type: Component

Selector: `sky-list-paging`

Displays a pagination control for a SKY UX-themed list of data.

### Inputs

#### `maxPages: number | Observable<number>`

The maximum pages to display.

Default: `5`

#### `pageNumber: number | Observable<number>`

The current page number.

Default: `1`

#### `pageSize: number | Observable<number>`

The number of list items per page.

Default: `10`