---
component: 'angular-tree'
description: 'Design guidelines, API documentation, and usage instructions for the angular-tree component extracted from SKY UX documentation.'
---

# Angular Tree Component Guidelines

## Component Overview
Tree views provide hierarchical list views with multiple modes for selecting items in the lists.

## Usage

### ✅ Use when

Use tree views to represent hierarchical information. You can make tree views read-only or allow users to select list items.

**✅ Do use tree views for hierarchical lists.**

## Anatomy

- Expand/collapse button
- List item
- Checkbox
- Context menu
- Help inline button

## Options

### Selection mode

You can use the single-select and multiselect modes to allow users to select list items.

You can use the cascading selection mode to select descendant nodes when users select items. Use this mode when users are likely to select all descendants within nodes.

You can use the leaf-only selection mode to limit user selections to leaf nodes. Use this mode when higher-level nodes are categories that contain leaf nodes for users to select.

### Help inline button

When you need to supplement a tree view list item with additional information but don't require persistent inline help, you can place a help inline button beside the list item to invoke contextual user assistance.

### Navigation mode

When users need to work with the items in hierarchical lists and take actions, you can place tree views within split views. When users select items to work on, tree views highlight those items with the active state.

### Read-only mode

You can use the read-only mode to allow users to view hierarchical information in cases where items are not selectable and are not used for navigation. You can still include interactive elements such as hyperlinks in the list items.

### Context menus

When users need to perform actions on items in hierarchical lists, you can include context menus to provide access to those actions.

## Behavior and states

### Expand and collapse nodes

The button beside items expands and collapses the node.

### States

## Related information

### Components

- Angular tree component
- Data grid
- Dropdown
- Help inline button
- Repeater
- Split view

## API Documentation

### Components and Directives

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
- `index`: `number | undefined` - The `index` property from the parent `ng-template`. **[Required]**
- `node`: `TreeNode | undefined` - The `node` property from the parent `ng-template`. For information about the `TreeNode` object, see the
[Angular tree component documentation](https://angular2-tree.readme.io/docs/api). **[Required]**
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

#### SkyAngularTreeModule

**Package:** `@skyux/angular-tree-component`

#### AngularTreeComponentAngularTreeBasicExampleComponent

**Selector:** `app-angular-tree-component-angular-tree-basic-example`

**Package:** `@skyux/code-examples`

#### AngularTreeComponentAngularTreeHelpKeyExampleComponent

**Selector:** `app-angular-tree-component-angular-tree-help-key-example`

**Package:** `@skyux/code-examples`

### Code Examples

#### Tree view with basic setup

**Selector:** `app-angular-tree-component-angular-tree-basic-example`

**TypeScript:**

```typescript
import { ChangeDetectionStrategy, Component } from '@angular/core';
import { TreeModule } from '@blackbaud/angular-tree-component';
import { SkyAngularTreeModule } from '@skyux/angular-tree-component';
import { SkyHelpInlineModule } from '@skyux/help-inline';

/**
 * @title Tree view with basic setup
 */
@Component({
  selector: 'app-angular-tree-component-angular-tree-basic-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [SkyAngularTreeModule, SkyHelpInlineModule, TreeModule],
})
export class AngularTreeComponentAngularTreeBasicExampleComponent {
  protected nodes = [
    {
      name: 'Animals',
      isExpanded: true,
      helpPopoverContent: 'Example help content for animals.',
      children: [
        {
          name: 'Cats',
          isExpanded: true,
          helpPopoverContent: 'Example help content for cats.',
          helpPopoverTitle: 'What is a cat?',
          children: [
            { name: 'Burmese' },
            { name: 'Persian' },
            { name: 'Tabby' },
          ],
        },
        {
          name: 'Dogs',
          isExpanded: true,
          children: [
            {
              name: 'Beagle',
              helpPopoverContent: 'Example help content for beagles.',
            },
            { name: 'German shepherd' },
            { name: 'Labrador retriever' },
          ],
        },
      ],
    },
  ];
}

```

**Template:**

```html
<sky-angular-tree-wrapper>
  <tree-root #tree [nodes]="nodes">
    <ng-template
      #treeNodeFullTemplate
      let-index="index"
      let-node
      let-templates="templates"
    >
      <sky-angular-tree-node
        [helpPopoverContent]="node.data.helpPopoverContent"
        [helpPopoverTitle]="node.data.helpPopoverTitle"
        [index]="index"
        [node]="node"
        [templates]="templates"
      />
    </ng-template>
  </tree-root>
</sky-angular-tree-wrapper>

```

#### Tree view with help key

**Selector:** `app-angular-tree-component-angular-tree-help-key-example`

**TypeScript:**

```typescript
import { ChangeDetectionStrategy, Component } from '@angular/core';
import { TreeModule } from '@blackbaud/angular-tree-component';
import { SkyAngularTreeModule } from '@skyux/angular-tree-component';
import { SkyHelpInlineModule } from '@skyux/help-inline';

/**
 * @title Tree view with help key
 */
@Component({
  selector: 'app-angular-tree-component-angular-tree-help-key-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [SkyAngularTreeModule, SkyHelpInlineModule, TreeModule],
})
export class AngularTreeComponentAngularTreeHelpKeyExampleComponent {
  protected nodes = [
    {
      name: 'Animals',
      isExpanded: true,
      helpPopoverContent: 'Example help content for animals.',
      children: [
        {
          name: 'Cats',
          isExpanded: true,
          helpPopoverContent: 'Example help content for cats.',
          helpPopoverTitle: 'What is a cat?',
          children: [
            { name: 'Burmese', helpKey: 'cat-burmese' },
            { name: 'Persian', helpKey: 'cat-persian' },
            { name: 'Tabby', helpKey: 'cat-tabby' },
          ],
        },
        {
          name: 'Dogs',
          isExpanded: true,
          children: [
            {
              name: 'Beagle',
              helpPopoverContent: 'Example help content for beagles.',
            },
            { name: 'German shepherd', helpKey: 'dog-shepherd' },
            { name: 'Labrador retriever', helpKey: 'dog-lab' },
          ],
        },
      ],
    },
  ];
}

```

**Template:**

```html
<sky-angular-tree-wrapper>
  <tree-root #tree [nodes]="nodes">
    <ng-template
      #treeNodeFullTemplate
      let-index="index"
      let-node
      let-templates="templates"
    >
      <sky-angular-tree-node
        [attr.data-sky-id]="'node-' + node.data.name"
        [helpKey]="node.data.helpKey"
        [helpPopoverContent]="node.data.helpPopoverContent"
        [helpPopoverTitle]="node.data.helpPopoverTitle"
        [index]="index"
        [node]="node"
        [templates]="templates"
      />
    </ng-template>
  </tree-root>
</sky-angular-tree-wrapper>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.