---
component: 'sort'
type: 'code-examples'
description: 'Code examples for the sort component.'
---

# Sort Code Examples

## Sort with basic setup

**Component:** ListsSortBasicExampleComponent

**Selector:** `app-lists-sort-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkySortHarness } from '@skyux/lists/testing';

import { ListsSortBasicExampleComponent } from './example.component';

describe('Sort demo', () => {
  async function setupTest(
    options: {
      dataSkyId?: string;
    } = {},
  ): Promise<{
    sortHarness: SkySortHarness;
    fixture: ComponentFixture<ListsSortBasicExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [ListsSortBasicExampleComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(ListsSortBasicExampleComponent);
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const sortHarness: SkySortHarness = options.dataSkyId
      ? await loader.getHarness(
          SkySortHarness.with({
            dataSkyId: options.dataSkyId,
          }),
        )
      : await loader.getHarness(SkySortHarness);

    return { sortHarness, fixture };
  }

  it('should set up the component', async () => {
    const { sortHarness } = await setupTest();

    await sortHarness.click();

    const items = await sortHarness.getItems();

    await expectAsync(items[0].isActive()).toBeResolvedTo(false);
    await expectAsync(items[1].getText()).toBeResolvedTo('Assigned to (Z - A)');
    await expectAsync(items[2].isActive()).toBeResolvedTo(true);

    await items[3].click();

    await expectAsync(items[3].isActive()).toBeResolvedTo(true);
  });
});

```

#### example.component.ts

```typescript
import { CommonModule } from '@angular/common';
import { Component, OnInit } from '@angular/core';
import { SkyToolbarModule } from '@skyux/layout';
import { SkyRepeaterModule, SkySortModule } from '@skyux/lists';

interface Item {
  title: string;
  note: string;
  assignee: string;
  date: Date;
}

interface SortOption {
  id: number;
  label: string;
  name: keyof Item;
  descending: boolean;
}

/**
 * @title Sort with basic setup
 */
@Component({
  selector: 'app-lists-sort-basic-example',
  styles: `
    .item-wrapper {
      display: flex;
      justify-content: space-between;
    }
  `,
  templateUrl: './example.component.html',
  imports: [CommonModule, SkyRepeaterModule, SkySortModule, SkyToolbarModule],
})
export class ListsSortBasicExampleComponent implements OnInit {
  protected initialState = 3;

  protected sortedItems: Item[] = [
    {
      title: 'Call Robert Hernandez',
      note: 'Robert recently gave a very generous gift. We should call to thank him.',
      assignee: 'Debby Fowler',
      date: new Date('12/22/2015'),
    },
    {
      title: 'Send invitation to ball',
      note: "The Spring Ball is coming up soon. Let's get those invitations out!",
      assignee: 'Debby Fowler',
      date: new Date('1/1/2016'),
    },
    {
      title: 'Clean up desk',
      note: 'File and organize papers.',
      assignee: 'Tim Howard',
      date: new Date('2/2/2016'),
    },
    {
      title: 'Investigate leads',
      note: 'Check out leads for important charity event funding.',
      assignee: 'Larry Williams',
      date: new Date('4/5/2016'),
    },
    {
      title: 'Send thank you note',
      note: 'Send a thank you note to Timothy for his donation.',
      assignee: 'Catherine Hooper',
      date: new Date('11/11/2015'),
    },
  ];

  protected sortOptions: SortOption[] = [
    {
      id: 1,
      label: 'Assigned to (A - Z)',
      name: 'assignee',
      descending: false,
    },
    {
      id: 2,
      label: 'Assigned to (Z - A)',
      name: 'assignee',
      descending: true,
    },
    {
      id: 3,
      label: 'Date created (newest first)',
      name: 'date',
      descending: true,
    },
    {
      id: 4,
      label: 'Date created (oldest first)',
      name: 'date',
      descending: false,
    },
    {
      id: 5,
      label: 'Note title (A - Z)',
      name: 'title',
      descending: false,
    },
    {
      id: 6,
      label: 'Note title (Z - A)',
      name: 'title',
      descending: true,
    },
  ];

  public ngOnInit(): void {
    this.sortItems(this.sortOptions[2]);
  }

  protected sortItems(option: SortOption): void {
    this.sortedItems = this.sortedItems.sort((a, b) => {
      const descending = option.descending ? -1 : 1;
      const sortProperty: keyof typeof a = option.name;

      if (a[sortProperty] > b[sortProperty]) {
        return descending;
      } else if (a[sortProperty] < b[sortProperty]) {
        return -1 * descending;
      } else {
        return 0;
      }
    });
  }
}

```

#### example.component.html

```html
<sky-toolbar>
  <sky-toolbar-item>
    <sky-sort [showButtonText]="true">
      @for (item of sortOptions; track item) {
        <sky-sort-item
          [active]="initialState === item.id"
          (itemSelect)="sortItems(item)"
        >
          {{ item.label }}
        </sky-sort-item>
      }
    </sky-sort>
  </sky-toolbar-item>
</sky-toolbar>
<sky-repeater expandMode="none">
  @for (item of sortedItems; track item) {
    <sky-repeater-item>
      <sky-repeater-item-title>
        {{ item.title }}
      </sky-repeater-item-title>
      <sky-repeater-item-content>
        <div class="item-wrapper">
          <div>Assigned to {{ item.assignee }}</div>
          <div>Created {{ item.date | date }}</div>
        </div>
        <div>
          {{ item.note }}
        </div>
      </sky-repeater-item-content>
    </sky-repeater-item>
  }
</sky-repeater>

```

---