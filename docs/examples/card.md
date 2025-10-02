---
component: 'card'
type: 'code-examples'
description: 'Code examples for the card component.'
---

# Card Code Examples

## Card with basic setup

**Component:** LayoutCardBasicExampleComponent

**Selector:** `app-layout-card-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { FormsModule } from '@angular/forms';
import { SkyCheckboxModule } from '@skyux/forms';
import { SkyCardModule } from '@skyux/layout';
import { SkyDropdownModule } from '@skyux/popovers';

/**
 * @title Card with basic setup
 */
@Component({
  selector: 'app-layout-card-basic-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, SkyCardModule, SkyCheckboxModule, SkyDropdownModule],
})
export class LayoutCardBasicExampleComponent {
  protected showAction = true;
  protected showCheckbox = true;
  protected showContent = true;
  protected showTitle = true;

  protected triggerAlert(): void {
    alert('Action clicked!');
  }
}

```

#### example.component.html

```html
<sky-card [selectable]="showCheckbox">
  @if (showTitle) {
    <sky-card-title> Large card </sky-card-title>
  }
  @if (showContent) {
    <sky-card-content>
      This card examplenstrates the amount of space that is available for a card
      that uses the default large size. If the content does not require this
      much space, you can set the card size to small. The type of content to
      display in the body of a card varies based on what the card represents and
      whether it prompts users to action.
    </sky-card-content>
  }
  @if (showAction) {
    <sky-card-actions>
      <button
        class="sky-btn sky-btn-default"
        type="button"
        (click)="triggerAlert()"
      >
        Action
      </button>
    </sky-card-actions>
  }
</sky-card>
<sky-card size="small" [selectable]="showCheckbox">
  @if (showTitle) {
    <sky-card-title> Small card </sky-card-title>
  }
  @if (showContent) {
    <sky-card-content>
      This card examplenstrates the reduced amount of space that is available
      when you set the card size to small.
    </sky-card-content>
  }
  @if (showAction) {
    <sky-card-actions>
      <sky-dropdown buttonType="context-menu">
        <sky-dropdown-menu>
          <sky-dropdown-item>
            <button type="button" (click)="triggerAlert()">Action</button>
          </sky-dropdown-item>
        </sky-dropdown-menu>
      </sky-dropdown>
    </sky-card-actions>
  }
</sky-card>

<ul class="sky-list-unstyled">
  <li>
    <sky-checkbox labelText="Show title" [(ngModel)]="showTitle" />
  </li>
  <li>
    <sky-checkbox labelText="Show content" [(ngModel)]="showContent" />
  </li>
  <li>
    <sky-checkbox labelText="Show action" [(ngModel)]="showAction" />
  </li>
  <li>
    <sky-checkbox labelText="Show checkbox" [(ngModel)]="showCheckbox" />
  </li>
</ul>

```

---