---
component: 'definition-list'
type: 'code-examples'
description: 'Code examples for the definition-list component.'
---

# Definition List Code Examples

## Definition list with basic setup

**Component:** LayoutDefinitionListBasicExampleComponent

**Selector:** `app-layout-definition-list-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyDefinitionListModule } from '@skyux/layout';

/**
 * @title Definition list with basic setup
 */
@Component({
  selector: 'app-layout-definition-list-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyDefinitionListModule],
})
export class LayoutDefinitionListBasicExampleComponent {
  protected items: { label: string; value?: string }[] = [
    {
      label: 'Field 1',
      value: 'Field 1 value',
    },
    {
      label: 'Field 2',
      value: 'Field 2 value',
    },
    {
      label: 'Field 3',
      value: undefined,
    },
    {
      label: 'Field 4',
      value: 'Field 4 value',
    },
  ];
}

```

#### example.component.html

```html
<sky-definition-list>
  <sky-definition-list-heading>
    Definition list heading
  </sky-definition-list-heading>
  @for (item of items; track item) {
    <sky-definition-list-content>
      <sky-definition-list-label>
        {{ item.label }}
      </sky-definition-list-label>
      <sky-definition-list-value>
        {{ item.value }}
      </sky-definition-list-value>
    </sky-definition-list-content>
  }
</sky-definition-list>

```

---