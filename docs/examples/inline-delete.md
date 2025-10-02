---
component: 'inline-delete'
type: 'code-examples'
description: 'Code examples for the inline-delete component.'
---

# Inline Delete Code Examples

## Inline delete with custom elements

**Component:** LayoutInlineDeleteCustomExampleComponent

**Selector:** `app-layout-inline-delete-custom-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyInlineDeleteHarness } from '@skyux/layout/testing';

import { LayoutInlineDeleteCustomExampleComponent } from './example.component';

describe('Custom component inline delete example', () => {
  async function setupTest(): Promise<{
    deleteHarness: SkyInlineDeleteHarness;
    fixture: ComponentFixture<LayoutInlineDeleteCustomExampleComponent>;
  }> {
    TestBed.configureTestingModule({
      imports: [LayoutInlineDeleteCustomExampleComponent, NoopAnimationsModule],
    });
    const fixture = TestBed.createComponent(
      LayoutInlineDeleteCustomExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);
    fixture.componentInstance.deleting = true;
    fixture.detectChanges();
    const deleteHarness = await loader.getHarness(
      SkyInlineDeleteHarness.with({ dataSkyId: 'inline-delete-custom' }),
    );

    return { deleteHarness, fixture };
  }

  it('should mark delete as pending when the delete button is clicked', async () => {
    const { deleteHarness } = await setupTest();

    await deleteHarness.clickDeleteButton();
    await expectAsync(deleteHarness.isPending()).toBeResolvedTo(true);
  });
});

```

#### example.component.ts

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

#### example.component.html

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

#### example.component.scss

```css
.inline-delete-container {
  padding: 15px;
  background-color: white;
  border: black solid 1px;
  height: 400px;
  width: 400px;
  position: relative;
}

.inline-delete-trigger {
  position: absolute;
  bottom: 10px;
  left: 0;
  width: 100%;
}

```

---

## Inline delete with repeater

**Component:** LayoutInlineDeleteRepeaterExampleComponent

**Selector:** `app-layout-inline-delete-repeater-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyInlineDeleteHarness } from '@skyux/layout/testing';

import { LayoutInlineDeleteRepeaterExampleComponent } from './example.component';

describe('Custom component inline delete example', () => {
  async function setupTest(options: { itemTitle: string }): Promise<{
    deleteHarness: SkyInlineDeleteHarness;
    fixture: ComponentFixture<LayoutInlineDeleteRepeaterExampleComponent>;
  }> {
    TestBed.configureTestingModule({
      imports: [
        LayoutInlineDeleteRepeaterExampleComponent,
        NoopAnimationsModule,
      ],
    });
    const fixture = TestBed.createComponent(
      LayoutInlineDeleteRepeaterExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    fixture.componentInstance.showInlineDelete(options.itemTitle);
    fixture.detectChanges();

    const deleteHarness = await loader.getHarness(SkyInlineDeleteHarness);

    return { deleteHarness, fixture };
  }

  it('should setup inline delete for repeater item', async () => {
    const { deleteHarness, fixture } = await setupTest({
      itemTitle: 'Individual',
    });

    await deleteHarness.clickDeleteButton();

    expect(fixture.componentInstance.repeaterDemoItems.length).toBe(2);
  });
});

```

#### example.component.ts

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

#### example.component.html

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

---