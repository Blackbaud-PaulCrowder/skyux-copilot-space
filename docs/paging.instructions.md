---
component: 'paging'
description: 'Design guidelines, API documentation, and usage instructions for the paging component extracted from SKY UX documentation.'
---

# Paging Component Guidelines

## Component Overview
The paging component provides pagination controls to navigate a large list of items that is split up across multiple pages.

## Usage

### ✅ Use when

Use the paging component when you need to break up a large list to avoid displaying too many items at once. Paging improves the user experience by:

- Not overwhelming users with too many items at once. In general, limit pages to 10 to 30 items.
- Avoiding wait times of more than a couple seconds while items load.
- Using less space so that the page composition better communicates the relationship between the list and other elements on the page.

### ❌ Don't use when

Don't use the paging component when users must perform multiple steps of a single task in a particular order. Use the wizard instead.

Don't use the paging component when a list is presented in a split view.

## Anatomy

- Paging content
- Previous button
- Current page
- Pages
- Next button

## Options

### Number of pages to display

If users need to navigate frequently between pages, you can increase the number of pages to display. Keep in mind that the smallest mobile devices can only fit up to seven pages on one line.

**The number of pages to display can be adjusted.**

### Number of items per page

To determine how many items to display per page:

- Optimize for performance to load items within 2 seconds.
- Account for the tasks that users perform on the list and whether they need to complete the tasks without paging.
- Consider how the list relates to the rest of the page. When space is available and the list is the primary focus, you can include more items, but when the list is just one of multiple elements on the page, include fewer items.

### Labels for accessibility

If your application uses multiple paging components on a page, use unique, descriptive labels to help users of assistive technology differentiate the components and understand what each one does.

## Behavior and states

### Focus

When users navigate to a new set of items with the pagination controls, the focus moves to the top of the paged content.

### States

### Loading new items

When users navigate to a new set of items, the list is disabled and a wait indicator appears in the paging content area until the new items finish loading.

**A wait indicator appears while new items load.**

## Related information

### Components

- Data grid
- Data manager
- Infinite scroll
- Split view
- Wizard

### Guidelines

- Filtering lists
- List page

## API Documentation

### Components and Directives

#### AgGridDataGridPagingExampleComponent

**Selector:** `app-ag-grid-data-grid-paging-example`

**Package:** `@skyux/code-examples`

#### ListsPagingBasicExampleComponent

**Selector:** `app-lists-paging-basic-example`

**Package:** `@skyux/code-examples`

#### ListsPagingWithContentExampleComponent

**Selector:** `app-lists-paging-with-content-example`

**Package:** `@skyux/code-examples`

#### SkyListPagingComponent

Displays a pagination control for a SKY UX-themed list of data.

**Selector:** `sky-list-paging`

**Package:** `@skyux/list-builder`

**Inputs:**

- `maxPages`: `number | Observable<number>` - The maximum pages to display. (default: 5)
- `pageNumber`: `number | Observable<number>` - The current page number. (default: 1)
- `pageSize`: `number | Observable<number>` - The number of list items per page. (default: 10)

⚠️ **This component is deprecated.**

#### SkyListPagingModule

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListPagingModel

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListPagingOrchestrator

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListPagingSetItemsPerPageAction

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListPagingSetMaxPagesAction

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### ListPagingSetPageNumberAction

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### SkyPagingContentComponent

**Selector:** `sky-paging-content`

**Package:** `@skyux/lists`

#### SkyPagingComponent

**Selector:** `sky-paging`

**Package:** `@skyux/lists`

**Inputs:**

- `currentPage`: `number` - The page number of the current page. Page numbers start at 1 and increment. (default: 1)
- `itemCount`: `number` - The total number of items across all pages. (default: 0)
- `maxPages`: `number` - The maximum number of pages to display in the pagination control. (default: 5)
- `pageSize`: `number` - The number of items to display per page. (default: 10)
- `pagingLabel`: `string | undefined` - The label for the pagination control when an application includes
multiple paging components on the same page. The label should be unique and descriptive
to help users of assistive technology differentiate pagination controls
and understand what each one does. (default: "Pagination")

**Outputs:**

- `contentChange`: `EventEmitter<SkyPagingContentChangeArgs>` - Fires when the current page changes and emits the new current page with a function
to call when loading the new page completes. Handling this event will display the
wait component until the callback function is called, and focus will move to the top
of the list for keyboard navigation if the list contents are placed inside the
sky-paging-content element.
- `currentPageChange`: `EventEmitter<number>` - Fires when the current page changes and emits the new current page.

#### SkyPagingModule

**Package:** `@skyux/lists`

#### SkyPagingContentChangeArgs

Information about the paged content to load.

**Package:** `@skyux/lists`

#### SkyPagingFixtureButton

**Package:** `@skyux/lists/testing`

#### SkyPagingFixture

Provides information for and interaction with a SKY UX paging component.
By using the fixture API, a test insulates itself against updates to the internals
of a component, such as changing its DOM structure.

**Package:** `@skyux/lists/testing`

⚠️ **This component is deprecated.**

#### SkyPagingContentHarness

Harness to interact with a paging content component in tests.

**Package:** `@skyux/lists/testing`

#### SkyPagingHarnessFilters

A set of criteria that can be used to filter a list of `SkyPagingHarness` instances.

**Package:** `@skyux/lists/testing`

#### SkyPagingHarness

Harness for interacting with a paging component in tests.

**Package:** `@skyux/lists/testing`

### Code Examples

#### Basic setup with paging (without data manager)

**Selector:** `app-ag-grid-data-grid-paging-example`

**TypeScript:**

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  OnDestroy,
  OnInit,
  inject,
} from '@angular/core';
import { ActivatedRoute, NavigationEnd, Router } from '@angular/router';
import { SkyAgGridModule, SkyAgGridService, SkyCellType } from '@skyux/ag-grid';
import { SkyPagingModule } from '@skyux/lists';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ColDef,
  GridApi,
  GridOptions,
  GridReadyEvent,
  ModuleRegistry,
  ValueFormatterParams,
} from 'ag-grid-community';
import { Subscription } from 'rxjs';
import { filter, map } from 'rxjs/operators';

import { ContextMenuComponent } from './context-menu.component';
import { AG_GRID_DEMO_DATA, AgGridDemoRow } from './data';

ModuleRegistry.registerModules([AllCommunityModule]);

/**
 * @title Basic setup with paging (without data manager)
 */
@Component({
  selector: 'app-ag-grid-data-grid-paging-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [AgGridModule, SkyAgGridModule, SkyPagingModule],
})
export class AgGridDataGridPagingExampleComponent implements OnInit, OnDestroy {
  protected currentPage = 1;

  protected readonly pageSize = 3;

  #columnDefs: ColDef[] = [
    {
      colId: 'context',
      maxWidth: 50,
      sortable: false,
      cellRenderer: ContextMenuComponent,
    },
    {
      field: 'name',
      headerName: 'Name',
    },
    {
      field: 'age',
      headerName: 'Age',
      type: SkyCellType.Number,
      maxWidth: 60,
    },
    {
      field: 'startDate',
      headerName: 'Start date',
      type: SkyCellType.Date,
      sort: 'asc',
    },
    {
      field: 'endDate',
      headerName: 'End date',
      type: SkyCellType.Date,
      valueFormatter: (params: ValueFormatterParams<AgGridDemoRow, Date>) =>
        this.#endDateFormatter(params),
    },
    {
      field: 'department',
      headerName: 'Department',
      type: SkyCellType.Autocomplete,
    },
    {
      field: 'jobTitle',
      headerName: 'Title',
      type: SkyCellType.Autocomplete,
    },
  ];

  protected gridData = AG_GRID_DEMO_DATA;
  protected gridOptions: GridOptions;

  #gridApi: GridApi | undefined;
  #subscriptions = new Subscription();

  readonly #activatedRoute = inject(ActivatedRoute);
  readonly #agGridSvc = inject(SkyAgGridService);
  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #router = inject(Router);

  constructor() {
    const gridOptions: GridOptions = {
      columnDefs: this.#columnDefs,
      onGridReady: (gridReadyEvent): void => {
        this.onGridReady(gridReadyEvent);
      },
      rowSelection: { mode: 'singleRow' },
      pagination: true,
      suppressPaginationPanel: true,
      paginationPageSize: this.pageSize,
    };

    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions,
    });
  }

  public ngOnInit(): void {
    this.#subscriptions.add(
      this.#activatedRoute.queryParamMap
        .pipe(map((params) => params.get('page') ?? '1'))
        .subscribe((page) => {
          this.currentPage = Number(page);
          this.#gridApi?.paginationGoToPage(this.currentPage - 1);
          this.#changeDetectorRef.detectChanges();
        }),
    );

    this.#subscriptions.add(
      this.#router.events
        .pipe(filter((event) => event instanceof NavigationEnd))
        .subscribe(() => {
          const page = this.#activatedRoute.snapshot.paramMap.get('page');

          if (page) {
            this.currentPage = Number(page);
          }

          this.#gridApi?.paginationGoToPage(this.currentPage - 1);
          this.#changeDetectorRef.detectChanges();
        }),
    );
  }

  public ngOnDestroy(): void {
    this.#subscriptions.unsubscribe();
  }

  public onGridReady(gridReadyEvent: GridReadyEvent): void {
    this.#gridApi = gridReadyEvent.api;
    this.#gridApi.paginationGoToPage(this.currentPage - 1);
  }

  protected async onPageChange(page: number): Promise<void> {
    await this.#router.navigate(['.'], {
      relativeTo: this.#activatedRoute,
      queryParams: { page: page.toString(10) },
      queryParamsHandling: 'merge',
    });
  }

  #endDateFormatter(params: ValueFormatterParams<AgGridDemoRow, Date>): string {
    return params.value
      ? params.value.toLocaleDateString('en-us', {
          year: 'numeric',
          month: '2-digit',
          day: '2-digit',
        })
      : 'N/A';
  }
}

```

**Template:**

```html
<sky-dropdown buttonType="context-menu" [label]="contextMenuAriaLabel">
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="deleteAriaLabel"
        (click)="actionClicked('Delete')"
      >
        Delete
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="markInactiveAriaLabel"
        (click)="actionClicked('Mark inactive')"
      >
        Mark inactive
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button
        type="button"
        [attr.aria-label]="moreInfoAriaLabel"
        (click)="actionClicked('More info')"
      >
        More info
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

#### Paging with basic setup

**Selector:** `app-lists-paging-basic-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyPagingModule } from '@skyux/lists';

/**
 * @title Paging with basic setup
 */
@Component({
  selector: 'app-lists-paging-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyPagingModule],
})
export class ListsPagingBasicExampleComponent {
  protected currentPage = 1;
}

```

**Template:**

```html
<sky-paging
  [itemCount]="8"
  [maxPages]="3"
  [pageSize]="2"
  [(currentPage)]="currentPage"
/>

<p>The current page is {{ currentPage }}.</p>

```

#### Paging with content wrapper

**Selector:** `app-lists-paging-with-content-example`

**TypeScript:**

```typescript
import { CommonModule } from '@angular/common';
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import { SkyDescriptionListModule } from '@skyux/layout';
import {
  SkyPagingContentChangeArgs,
  SkyPagingModule,
  SkyRepeaterModule,
} from '@skyux/lists';

import { Subject, shareReplay, switchMap, tap } from 'rxjs';

import { DemoDataService } from './demo-data.service';

/**
 * @title Paging with content wrapper
 */
@Component({
  selector: 'app-lists-paging-with-content-example',
  templateUrl: './example.component.html',
  imports: [
    CommonModule,
    SkyDescriptionListModule,
    SkyPagingModule,
    SkyRepeaterModule,
  ],
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class ListsPagingWithContentExampleComponent {
  #demoDataSvc = inject(DemoDataService);

  protected currentPage = 1;
  protected pageSize = 5;
  protected contentChange = new Subject<SkyPagingContentChangeArgs>();

  protected pagedData = this.contentChange.pipe(
    switchMap((args) =>
      this.#demoDataSvc.getPagedData(args.currentPage, this.pageSize).pipe(
        tap(() => {
          args.loadingComplete();
        }),
      ),
    ),
    shareReplay(1),
  );
}

```

**Template:**

```html
<sky-paging
  data-sky-id="my-paging-content"
  [itemCount]="(pagedData | async)?.totalCount ?? 0"
  [maxPages]="3"
  [pageSize]="pageSize"
  [(currentPage)]="currentPage"
  (contentChange)="contentChange.next($event)"
>
  <sky-paging-content>
    <sky-repeater>
      @for (person of (pagedData | async)?.people; track person) {
        <sky-repeater-item>
          <sky-repeater-item-title>
            {{ person.name }}
          </sky-repeater-item-title>
          <sky-repeater-item-content>
            <sky-description-list>
              <sky-description-list-content>
                <sky-description-list-term>
                  Formal name
                </sky-description-list-term>
                <sky-description-list-description>
                  {{ person.formal }}
                </sky-description-list-description>
              </sky-description-list-content>
            </sky-description-list>
          </sky-repeater-item-content>
        </sky-repeater-item>
      }
    </sky-repeater>
  </sky-paging-content>
</sky-paging>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.