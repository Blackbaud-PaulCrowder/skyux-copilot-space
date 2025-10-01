---
component: 'inline-delete'
description: 'Design guidelines, API documentation, and usage instructions for the inline-delete component extracted from SKY UX documentation.'
---

# Inline Delete Component Guidelines

## Component Overview
The inline delete confirmation appears when users delete an item in a list and requires them to confirm that they want to delete the item.

## Usage

### ✅ Use when

Use the inline delete confirmation when users need to confirm that they want to delete an item from a list.

Keep in mind that you should not delete items from lists when they are complex enough to have their own record pages. For lists with such items, do not include delete actions in the context-menu dropdowns.

### ❌ Don't use when

Don't use inline delete confirmation when users need to confirm that they want to delete an item outside of a list. Use a confirm dialog instead.

## Anatomy

- Delete button
- Cancel button
- Overlay

## Behavior and states

### Delete button

The inline delete confirmation uses the sky-btn-danger (red) style for the Delete button to visually indicate that the action deletes existing data.

## Related information

### Components

- Confirm
- Dropdown

### Guidelines

- Manage records

## API Documentation

### Components and Directives

#### LayoutInlineDeleteCustomExampleComponent

**Selector:** `app-layout-inline-delete-custom-example`

**Package:** `@skyux/code-examples`

#### LayoutInlineDeleteRepeaterExampleComponent

**Selector:** `app-layout-inline-delete-repeater-example`

**Package:** `@skyux/code-examples`

#### SkyInlineDeleteType

The type of inline delete that is shown.

**Package:** `@skyux/layout`

#### SkyInlineDeleteComponent

**Selector:** `sky-inline-delete`

**Package:** `@skyux/layout`

**Inputs:**

- `pending`: `boolean | undefined` - Whether the deletion is pending. (default: false)

**Outputs:**

- `cancelTriggered`: `EventEmitter<void>` - Fires when users click the cancel button.
- `deleteTriggered`: `EventEmitter<void>` - Fires when users click the delete button.

#### SkyInlineDeleteModule

**Package:** `@skyux/layout`

#### SkyInlineDeleteHarnessFilters

A set of criteria that can be used to filter a list of `SkyInlineDeleteHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyInlineDeleteHarness

Harness for interacting with an inline delete component in tests.

**Package:** `@skyux/layout/testing`

### Code Examples

#### Inline delete with custom elements

**Selector:** `app-layout-inline-delete-custom-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyIconModule } from '@skyux/icon';
import { SkyInlineDeleteModule } from '@skyux/layout';

/**
 * @title Inline delete with custom elements
 */
@Component({
  selector: 'app-layout-inline-delete-custom-example',
  templateUrl: './example.component.html',
  styleUrls: ['./example.component.scss'],
  imports: [SkyIconModule, SkyInlineDeleteModule],
})
export class LayoutInlineDeleteCustomExampleComponent {
  public deleting = false;
  protected pending = false;

  protected deleteItem(): void {
    this.deleting = true;
  }

  protected onCancelTriggered(): void {
    this.deleting = false;
  }

  protected onDeleteTriggered(): void {
    setTimeout(() => {
      this.pending = false;
      this.deleting = false;

      alert(
        'Custom element deletion was triggered. In a real scenario the item would be removed. Item was not removed just for example purposes.',
      );
    }, 3000);

    this.pending = true;
  }
}

```

**Template:**

```html
<div class="inline-delete-container">
  <strong>Custom content</strong>
  <div>
    <button
      class="sky-btn sky-btn-danger inline-delete-trigger"
      type="button"
      (click)="deleteItem()"
    >
      <sky-icon iconName="delete" />
    </button>
  </div>
  @if (deleting) {
    <sky-inline-delete
      data-sky-id="inline-delete-custom"
      [pending]="pending"
      (cancelTriggered)="onCancelTriggered()"
      (deleteTriggered)="onDeleteTriggered()"
    />
  }
</div>

```

#### Inline delete with repeater

**Selector:** `app-layout-inline-delete-repeater-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyInlineDeleteModule } from '@skyux/layout';
import { SkyRepeaterModule } from '@skyux/lists';
import { SkyDropdownModule } from '@skyux/popovers';

interface InlineRepeaterDemoItem {
  title: string;
  cost: string;
  description: string;
}

/**
 * @title Inline delete with repeater
 */
@Component({
  selector: 'app-layout-inline-delete-repeater-example',
  templateUrl: './example.component.html',
  imports: [SkyDropdownModule, SkyInlineDeleteModule, SkyRepeaterModule],
})
export class LayoutInlineDeleteRepeaterExampleComponent {
  protected originalRepeaterDemoItems: InlineRepeaterDemoItem[] = [
    {
      title: 'Individual',
      cost: '$75.00',
      description: '1 ticket',
    },
    {
      title: 'Foursome',
      cost: '$250.00',
      description: '4 tickets',
    },
    {
      title: 'Hole sponsor',
      cost: '$1,000.00',
      description: '8 tickets',
    },
  ];

  public repeaterDemoItems = this.originalRepeaterDemoItems;
  protected repeaterDemoShownInlineDeletes: string[] = [];

  public showInlineDelete(title: string): void {
    this.repeaterDemoShownInlineDeletes.push(title);
  }

  protected deleteItem(title: string): void {
    this.repeaterDemoItems = this.repeaterDemoItems.filter(
      (exampleItem: InlineRepeaterDemoItem) => exampleItem.title !== title,
    );

    this.repeaterDemoShownInlineDeletes =
      this.repeaterDemoShownInlineDeletes.filter(
        (exampleItem: string) => exampleItem !== title,
      );
  }

  protected cancelDeletion(title: string): void {
    this.repeaterDemoShownInlineDeletes =
      this.repeaterDemoShownInlineDeletes.filter(
        (exampleItem: string) => exampleItem !== title,
      );
  }

  protected onResetClick(): void {
    this.repeaterDemoItems = this.originalRepeaterDemoItems;
    this.repeaterDemoShownInlineDeletes = [];
  }
}

```

**Template:**

```html
<sky-repeater>
  @for (item of repeaterDemoItems; track item) {
    <sky-repeater-item>
      <sky-repeater-item-context-menu>
        <sky-dropdown buttonType="context-menu">
          <sky-dropdown-menu>
            <sky-dropdown-item>
              <button type="button" (click)="showInlineDelete(item.title)">
                Delete
              </button>
            </sky-dropdown-item>
          </sky-dropdown-menu>
        </sky-dropdown>
      </sky-repeater-item-context-menu>
      <sky-repeater-item-title class="sky-example-inline-delete-flex">
        <div>
          {{ item.title }}
        </div>
        <div>
          {{ item.cost }}
        </div>
      </sky-repeater-item-title>
      <sky-repeater-item-content>
        {{ item.description }}
      </sky-repeater-item-content>
      @if (repeaterDemoShownInlineDeletes.indexOf(item.title) >= 0) {
        <sky-inline-delete
          (cancelTriggered)="cancelDeletion(item.title)"
          (deleteTriggered)="deleteItem(item.title)"
        />
      }
    </sky-repeater-item>
  }
</sky-repeater>

<button class="sky-btn sky-btn-primary" type="button" (click)="onResetClick()">
  Reset Repeater
</button>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.