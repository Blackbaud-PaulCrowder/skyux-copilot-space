---
component: 'action-button'
type: 'code-examples'
description: 'Code examples for the action-button component.'
---

# Action Button Code Examples

## Basic action buttons

**Component:** LayoutActionButtonBasicExampleComponent

**Selector:** `app-layout-action-button-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyActionButtonModule } from '@skyux/layout';

/**
 * @title Basic action buttons
 */
@Component({
  selector: 'app-layout-action-button-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyActionButtonModule],
})
export class LayoutActionButtonBasicExampleComponent {
  protected filterActionClick(): void {
    alert('Filter action clicked');
  }

  protected openActionClick(): void {
    alert('Open action clicked');
  }
}

```

#### example.component.html

```html
<sky-action-button-container>
  <sky-action-button (actionClick)="filterActionClick()">
    <sky-action-button-icon iconName="filter" />
    <sky-action-button-header> Build a new list </sky-action-button-header>
    <sky-action-button-details>
      Start from scratch and fine-tune with filters.
    </sky-action-button-details>
  </sky-action-button>

  <sky-action-button (actionClick)="openActionClick()">
    <sky-action-button-icon iconName="folder-open" />
    <sky-action-button-header> Open a saved list </sky-action-button-header>
    <sky-action-button-details>
      Open a list with filters saved in the web view.
    </sky-action-button-details>
  </sky-action-button>
</sky-action-button-container>

```

---

## Action button with permalinks

**Component:** LayoutActionButtonPermalinkExampleComponent

**Selector:** `app-layout-action-button-permalink-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyActionButtonModule, SkyActionButtonPermalink } from '@skyux/layout';

/**
 * @title Action button with permalinks
 */
@Component({
  selector: 'app-layout-action-button-permalink-example',
  templateUrl: './example.component.html',
  imports: [SkyActionButtonModule],
})
export class LayoutActionButtonPermalinkExampleComponent {
  protected routerlink: SkyActionButtonPermalink = {
    route: {
      commands: [],
      extras: {
        queryParams: {
          component: 'MyComponent',
        },
      },
    },
  };

  protected url: SkyActionButtonPermalink = {
    url: 'https://www.stackblitz.com',
  };
}

```

#### example.component.html

```html
<sky-action-button-container>
  <sky-action-button [permalink]="url">
    <sky-action-button-icon iconName="link" />
    <sky-action-button-header> Open a link </sky-action-button-header>
    <sky-action-button-details> Open a link. </sky-action-button-details>
  </sky-action-button>

  <sky-action-button [permalink]="routerlink">
    <sky-action-button-icon iconName="link" />
    <sky-action-button-header> Open a router link </sky-action-button-header>
    <sky-action-button-details> Open a router link. </sky-action-button-details>
  </sky-action-button>
</sky-action-button-container>

```

---