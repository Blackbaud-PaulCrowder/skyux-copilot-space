---
component: 'card'
description: 'Design guidelines, API documentation, and usage instructions for the card component extracted from SKY UX documentation.'
---

# Card Component Guidelines

## Component Overview
Cards create small containers that highlight important information, and you group cards together to display information about related items. Card is deprecated in favor of other content containers. For more information, see the card deprecation instructions.

## Usage

## API Documentation

### Components and Directives

#### LayoutCardBasicExampleComponent

**Selector:** `app-layout-card-basic-example`

**Package:** `@skyux/code-examples`

#### SkyCardActionsComponent

Specifies an action that users can perform on the card.

**Selector:** `sky-card-actions`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyCardContentComponent

Specifies the content to display in the body of the card.

**Selector:** `sky-card-content`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyCardTitleComponent

Specifies a title to identify what the card represents.

**Selector:** `sky-card-title`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyCardComponent

Creates a a small container to highlight important information.

**Selector:** `sky-card`

**Package:** `@skyux/layout`

**Inputs:**

- `selectable`: `boolean | undefined` - Whether to display a checkbox to the right of the card title.
Users can select multiple checkboxes and perform actions on the selected cards. (default: false)
- `selected`: `boolean | undefined` - Whether the card is selected. This only applies to card where
`selectable` is set to `true`. (default: false)
- `size`: `string` - The size of the card. The valid options are `"large"` and `"small"`. (default: "large")

**Outputs:**

- `selectedChange`: `EventEmitter<boolean>` - Fires when users select or deselect the card.

⚠️ **This component is deprecated.**

#### SkyCardModule

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyCardFixture

Allows interaction with a SKY UX avatar component.

**Package:** `@skyux/layout/testing`

⚠️ **This component is deprecated.**

### Code Examples

#### Card with basic setup

**Selector:** `app-layout-card-basic-example`

**TypeScript:**

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

**Template:**

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

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.