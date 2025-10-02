---
component: 'angular-tree'
type: 'code-examples'
description: 'Code examples for the angular-tree component.'
---

# Angular Tree Code Examples

## Tree view with basic setup

**Component:** AngularTreeComponentAngularTreeBasicExampleComponent

**Selector:** `app-angular-tree-component-angular-tree-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

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

#### example.component.html

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

---

## Tree view with help key

**Component:** AngularTreeComponentAngularTreeHelpKeyExampleComponent

**Selector:** `app-angular-tree-component-angular-tree-help-key-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

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

#### example.component.html

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

---