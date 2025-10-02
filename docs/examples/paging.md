---
component: 'paging'
type: 'code-examples'
description: 'Code examples for the paging component.'
---

# Paging Code Examples

## Basic setup with paging (without data manager)

**Component:** AgGridDataGridPagingExampleComponent

**Selector:** `app-ag-grid-data-grid-paging-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### context-menu.component.ts

```typescript
import { ChangeDetectionStrategy, Component } from '@angular/core';
import { SkyDropdownModule } from '@skyux/popovers';

import { ICellRendererAngularComp } from 'ag-grid-angular';
import { ICellRendererParams } from 'ag-grid-community';

import { AgGridDemoRow } from './data';

@Component({
  selector: 'app-context-menu',
  templateUrl: './context-menu.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [SkyDropdownModule],
})
export class ContextMenuComponent implements ICellRendererAngularComp {
  public contextMenuAriaLabel = '';
  public deleteAriaLabel = '';
  public markInactiveAriaLabel = '';
  public moreInfoAriaLabel = '';

  #name: string | undefined;

  public agInit(params: ICellRendererParams<AgGridDemoRow>): void {
    this.#name = params.data?.name;
    this.contextMenuAriaLabel = `Context menu for ${this.#name}`;
    this.deleteAriaLabel = `Delete ${this.#name}`;
    this.markInactiveAriaLabel = `Mark ${this.#name} inactive`;
    this.moreInfoAriaLabel = `More info for ${this.#name}`;
  }

  public refresh(): boolean {
    return false;
  }

  protected actionClicked(action: string): void {
    alert(`${action} clicked for ${this.#name}`);
  }
}

```

#### data.ts

```typescript
export interface AutocompleteOption {
  id: string;
  name: string;
}

export const DEPARTMENTS = [
  {
    id: '1',
    name: 'Marketing',
  },
  {
    id: '2',
    name: 'Sales',
  },
  {
    id: '3',
    name: 'Engineering',
  },
  {
    id: '4',
    name: 'Customer Support',
  },
];

export const JOB_TITLES: Record<string, AutocompleteOption[]> = {
  Marketing: [
    {
      id: '1',
      name: 'Social Media Coordinator',
    },
    {
      id: '2',
      name: 'Blog Manager',
    },
    {
      id: '3',
      name: 'Events Manager',
    },
  ],
  Sales: [
    {
      id: '4',
      name: 'Business Development Representative',
    },
    {
      id: '5',
      name: 'Account Executive',
    },
  ],
  Engineering: [
    {
      id: '6',
      name: 'Software Engineer',
    },
    {
      id: '7',
      name: 'Senior Software Engineer',
    },
    {
      id: '8',
      name: 'Principal Software Engineer',
    },
    {
      id: '9',
      name: 'UX Designer',
    },
    {
      id: '10',
      name: 'Product Manager',
    },
  ],
  'Customer Support': [
    {
      id: '11',
      name: 'Customer Support Representative',
    },
    {
      id: '12',
      name: 'Account Manager',
    },
    {
      id: '13',
      name: 'Customer Support Specialist',
    },
  ],
};

export interface AgGridDemoRow {
  selected?: boolean;
  name: string;
  age: number;
  startDate: Date;
  endDate?: Date;
  department: AutocompleteOption;
  jobTitle?: AutocompleteOption;
}

export const AG_GRID_DEMO_DATA = [
  {
    name: 'Billy Bob',
    age: 55,
    startDate: new Date('12/1/1994'),
    department: DEPARTMENTS[3],
    jobTitle: JOB_TITLES['Customer Support'][1],
  },
  {
    name: 'Jane Deere',
    age: 33,
    startDate: new Date('7/15/2009'),
    department: DEPARTMENTS[2],
    jobTitle: JOB_TITLES['Engineering'][2],
  },
  {
    name: 'John Doe',
    age: 38,
    startDate: new Date('9/1/2017'),
    endDate: new Date('9/30/2017'),
    department: DEPARTMENTS[1],
  },
  {
    name: 'David Smith',
    age: 51,
    startDate: new Date('1/1/2012'),
    endDate: new Date('6/15/2018'),
    department: DEPARTMENTS[2],
    jobTitle: JOB_TITLES['Engineering'][4],
  },
  {
    name: 'Emily Johnson',
    age: 41,
    startDate: new Date('1/15/2014'),
    department: DEPARTMENTS[0],
    jobTitle: JOB_TITLES['Marketing'][2],
  },
  {
    name: 'Nicole Davidson',
    age: 22,
    startDate: new Date('11/1/2019'),
    department: DEPARTMENTS[2],
    jobTitle: JOB_TITLES['Engineering'][0],
  },
  {
    name: 'Carl Roberts',
    age: 23,
    startDate: new Date('11/1/2019'),
    department: DEPARTMENTS[2],
    jobTitle: JOB_TITLES['Engineering'][3],
  },
];

```

#### example.component.ts

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

#### context-menu.component.html

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

#### example.component.html

```html
<sky-ag-grid-wrapper>
  <ag-grid-angular [gridOptions]="gridOptions" [rowData]="gridData" />
</sky-ag-grid-wrapper>

<sky-paging
  [currentPage]="currentPage"
  [itemCount]="gridData.length"
  [pageSize]="pageSize"
  (currentPageChange)="onPageChange($event)"
/>

```

---

## Paging with basic setup

**Component:** ListsPagingBasicExampleComponent

**Selector:** `app-lists-paging-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

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

#### example.component.html

```html
<sky-paging
  [itemCount]="8"
  [maxPages]="3"
  [pageSize]="2"
  [(currentPage)]="currentPage"
/>

<p>The current page is {{ currentPage }}.</p>

```

---

## Paging with content wrapper

**Component:** ListsPagingWithContentExampleComponent

**Selector:** `app-lists-paging-with-content-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### demo-data.service.ts

```typescript
import { Injectable } from '@angular/core';

import { Observable, delay, of } from 'rxjs';

import { DemoData } from './demo-data';

const people = [
  {
    name: 'Abed',
    formal: 'Mr. Nadir',
  },
  {
    name: 'Alex',
    formal: 'Mr. Osbourne',
  },
  {
    name: 'Ben',
    formal: 'Mr. Chang',
  },
  {
    name: 'Britta',
    formal: 'Ms. Perry',
  },
  {
    name: 'Buzz',
    formal: 'Mr. Hickey',
  },
  {
    name: 'Craig',
    formal: 'Mr. Pelton',
  },
  {
    name: 'Elroy',
    formal: 'Mr. Patashnik',
  },
  {
    name: 'Garrett',
    formal: 'Mr. Lambert',
  },
  {
    name: 'Ian',
    formal: 'Mr. Duncan',
  },
  {
    name: 'Jeff',
    formal: 'Mr. Winger',
  },
  {
    name: 'Leonard',
    formal: 'Mr. Rodriguez',
  },
  {
    name: 'Neil',
    formal: 'Mr. Neil',
  },
  {
    name: 'Pierce',
    formal: 'Mr. Hawthorne',
  },
  {
    name: 'Preston',
    formal: 'Mr. Koogler',
  },
  {
    name: 'Rachel',
    formal: 'Ms. Rachel',
  },
  {
    name: 'Shirley',
    formal: 'Ms. Bennett',
  },
  {
    name: 'Todd',
    formal: 'Mr. Jacobson',
  },
  {
    name: 'Troy',
    formal: 'Mr. Barnes',
  },
  {
    name: 'Vaughn',
    formal: 'Mr. Miller',
  },
  {
    name: 'Vicki',
    formal: 'Ms. Jenkins',
  },
];

@Injectable({
  providedIn: 'root',
})
export class DemoDataService {
  public getPagedData(
    pageNumber: number,
    itemCount: number,
  ): Observable<DemoData> {
    const startIndex = (pageNumber - 1) * itemCount;

    return of({
      people: people.slice(startIndex, startIndex + itemCount),
      totalCount: people.length,
    }).pipe(
      // Simulate network latency.
      delay(1000),
    );
  }
}

```

#### demo-data.ts

```typescript
import { Person } from './person';

export interface DemoData {
  people: Person[];
  totalCount: number;
}

```

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyPagingHarness, SkyRepeaterHarness } from '@skyux/lists/testing';

import { ListsPagingWithContentExampleComponent } from './example.component';

describe('Paging example', () => {
  async function setupTest(
    options: {
      dataSkyId?: string;
    } = {},
  ): Promise<{
    pagingHarness: SkyPagingHarness;
    fixture: ComponentFixture<ListsPagingWithContentExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [ListsPagingWithContentExampleComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      ListsPagingWithContentExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const pagingHarness: SkyPagingHarness = options.dataSkyId
      ? await loader.getHarness(
          SkyPagingHarness.with({
            dataSkyId: options.dataSkyId,
          }),
        )
      : await loader.getHarness(SkyPagingHarness);

    return { pagingHarness, fixture };
  }

  it('should set up the paging content', async () => {
    const { pagingHarness, fixture } = await setupTest({
      dataSkyId: 'my-paging-content',
    });

    await expectAsync(pagingHarness.getCurrentPage()).toBeResolvedTo(1);

    const contentHarness = await (
      await pagingHarness.getPagingContent()
    ).queryHarness(SkyRepeaterHarness);

    let items = await contentHarness.getRepeaterItems();

    await expectAsync(items[0].getTitleText()).toBeResolvedTo('Abed');

    await pagingHarness.clickPageButton(3);

    fixture.detectChanges();
    await fixture.whenStable();

    await expectAsync(pagingHarness.getCurrentPage()).toBeResolvedTo(3);

    items = await contentHarness.getRepeaterItems();

    await expectAsync(items[0].getTitleText()).toBeResolvedTo('Leonard');

    await pagingHarness.clickNextButton();

    fixture.detectChanges();
    await fixture.whenStable();

    await expectAsync(pagingHarness.getCurrentPage()).toBeResolvedTo(4);

    items = await contentHarness.getRepeaterItems();

    await expectAsync(items[0].getTitleText()).toBeResolvedTo('Shirley');

    await expectAsync(pagingHarness.clickNextButton()).toBeRejectedWithError(
      'Could not click the next button because it is disabled.',
    );

    await expectAsync(pagingHarness.clickPageButton(1)).toBeRejectedWithError(
      'Could not find page button 1.',
    );
  });
});

```

#### example.component.ts

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

#### person.ts

```typescript
export interface Person {
  name: string;
  formal: string;
}

```

#### example.component.html

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

---