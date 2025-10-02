---
component: 'angular-tree'
type: 'api-documentation'
description: 'API documentation for the angular-tree component including components, interfaces, and types.'
---

# Angular Tree API Documentation

## Components and Directives

#### SkyAngularTreeNodeComponent

Replaces the default tree node template with a SKY UX node as part of the `SkyAngularTreeModule` that
provides SKY UX components and styles to complement the `angular-tree-component` library and apply SKY UX
themes and functionality to hierarchical list views. You must wrap this component in an `ng-template`
tag with the template reference variable `#treeNodeFullTemplate`. For information about tree node templates,
see the [Angular tree component documentation](https://angular2-tree.readme.io/docs/templates).
To display context menus with actions for individual items in hierarchical lists, place
[dropdowns](https://developer.blackbaud.com/skyux-popovers/docs/dropdown?docs-active-tab=design) inside the
Angular tree node component, which automatically handles styling and positioning for context menus.

**Selector:** `sky-angular-tree-node`

**Package:** `@skyux/angular-tree-component`

**Inputs:**

- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the tree node label. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the tree node. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `index`: `number | undefined` - The `index` property from the parent `ng-template`.
- `node`: `TreeNode | undefined` - The `node` property from the parent `ng-template`. For information about the `TreeNode` object, see the
[Angular tree component documentation](https://angular2-tree.readme.io/docs/api).
- `templates`: `any` - The `templates` property from the parent `ng-template`.

#### SkyAngularTreeWrapperComponent

Wraps the Angular `tree-root` component as part of the `SkyAngularTreeModule` that provides
SKY UX components and styles to complement the `angular-tree-component` library and apply SKY UX
themes and functionality to hierarchical list views. For information about the `tree-root` component, see the
[Angular tree component documentation](https://angular2-tree.readme.io/docs).

**Selector:** `sky-angular-tree-wrapper`

**Package:** `@skyux/angular-tree-component`

**Inputs:**

- `readOnly`: `boolean | undefined` - Whether to render the tree view in read-only mode.
This mode disables selected and active states on the tree view nodes. (default: false)
- `selectLeafNodesOnly`: `boolean | undefined` - Whether to use leaf-only selection mode. For tree views with
[checkboxes](https://angular2-tree.readme.io/docs/tri-state-checkboxes),
this mode limits user selections to leaf nodes and prevents users from selecting parent nodes. (default: false)
- `selectSingle`: `boolean | undefined` - Whether to use single-select mode. For tree views with
[checkboxes](https://angular2-tree.readme.io/docs/tri-state-checkboxes),
this mode limits user selections to one node at a time. (default: false)
- `showToolbar`: `boolean | undefined` - Whether to display a toolbar with buttons to expand and collapse all nodes and buttons to select and clear all checkboxes.
The select and clear buttons only appear when you enable checkboxes.
To enable [checkboxes](https://angular2-tree.readme.io/docs/tri-state-checkboxes). (default: false)

#### AngularTreeComponentAngularTreeBasicExampleComponent

**Selector:** `app-angular-tree-component-angular-tree-basic-example`

**Package:** `@skyux/code-examples`

#### AngularTreeComponentAngularTreeHelpKeyExampleComponent

**Selector:** `app-angular-tree-component-angular-tree-help-key-example`

**Package:** `@skyux/code-examples`