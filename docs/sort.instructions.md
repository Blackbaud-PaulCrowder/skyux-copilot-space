---
component: 'sort'
description: 'Design guidelines, API documentation, and usage instructions for the sort component extracted from SKY UX documentation.'
---

# Sort Component Guidelines

## Component Overview
The sort button and menu let users select sorting criteria.

## Usage

### ✅ Use when

Use to sort a list of items when there are templated columns in a list. This provides a way for users to sort templated columns because there are no corresponding column headings.

**✅ Do use a sort button when there are other views of the data, in addition to a data grid, to support sorting in those views (without column headers).**

### ❌ Don't use when

Do not include an additional sort button in the toolbar for a list when only data grid view is available. Column headers provide sorting in this case.

**❌ Don't use a sort button if the list only uses data grid view and not templated columns. Rely on column headers for sorting.**

## Anatomy

- Sort button
- Sort by menu
- Selected menu option
- Menu option

## Related information

### Components

- Data grid
- Repeater
- Toolbar

## API Documentation

### Components and Directives

#### ListSortFieldSelectorModel

**Package:** `@skyux/list-builder-common`

⚠️ **This component is deprecated.**

#### ListsSortBasicExampleComponent

**Selector:** `app-lists-sort-basic-example`

**Package:** `@skyux/code-examples`

#### SkyDataManagerColumnPickerSortStrategy

These options specify the sorting strategy applied to columns when `columnPickerEnabled` is enabled.

**Package:** `@skyux/data-manager`

#### SkyDataManagerSortOption

**Package:** `@skyux/data-manager`

#### SkyListToolbarSortComponent

Adds a sort dropdown to the list toolbar.

**Selector:** `sky-list-toolbar-sort`

**Package:** `@skyux/list-builder`

**Inputs:**

- `descending`: `boolean` - Whether to sort data in descending order. (default: false)
- `field`: `string` - The data field to sort the list on. **[Required]**
- `label`: `string` - The label for a sort option. **[Required]**
- `type`: `string` - The data type of the data field to sort the list on. **[Required]**

⚠️ **This component is deprecated.**

#### ListSortLabelModel

These properties are a work in progress, and we do not recommend using them.

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListSortSetAvailableAction

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListSortSetFieldSelectorsAction

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListSortSetGlobalAction

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListSortModel

Specifies a set of fields to sort by.

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListSortOrchestrator

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### SkySortItemComponent

**Selector:** `sky-sort-item`

**Package:** `@skyux/lists`

**Inputs:**

- `active`: `boolean | undefined` - Whether the sorting option is active.

**Outputs:**

- `itemSelect`: `EventEmitter<any>` - Fires when a sort item is selected.

#### SkySortComponent

**Selector:** `sky-sort`

**Package:** `@skyux/lists`

**Inputs:**

- `ariaLabel`: `string | undefined` - The ARIA label for the sort button. This sets the
sort button's `aria-label` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
Use a context-sensitive label, such as "Sort constituents." Context is especially important when multiple filter buttons are in close proximity.
In toolbars, sort buttons use the `listDescriptor` to provide context, and the ARIA label defaults to "Sort <listDescriptor>."
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `showButtonText`: `boolean | undefined` - Whether to display a "Sort" label beside the icon on the sort button. (default: false)

#### SkySortModule

**Package:** `@skyux/lists`

#### SkySortFixtureMenuItem

**Package:** `@skyux/lists/testing`

#### SkySortFixtureMenu

**Package:** `@skyux/lists/testing`

#### SkySortFixture

Provides information for and interaction with a SKY UX sort component.
By using the fixture API, a test insulates itself against updates to the internals
of a component, such as changing its DOM structure.

**Package:** `@skyux/lists/testing`

⚠️ **This component is deprecated.**

#### SkySortHarnessFilters

A set of criteria that can be used to filter a list of `SkySortHarness` instances.

**Package:** `@skyux/lists/testing`

#### SkySortHarness

Harness for interacting with a sort component in tests.

**Package:** `@skyux/lists/testing`

#### SkySortItemHarnessFilters

A set of criteria that can be used to filter a list of `SkySortItemHarness` instances.

**Package:** `@skyux/lists/testing`

#### SkySortItemHarness

Harness for interacting with a sort item component in tests.

**Package:** `@skyux/lists/testing`

### Code Examples

#### Sort with basic setup

**Selector:** `app-lists-sort-basic-example`

**TypeScript:**

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

**Template:**

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

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.