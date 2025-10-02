---
component: 'data-grid'
type: 'code-examples'
description: 'Code examples for the data-grid component.'
---

# Data Grid Code Examples

## Basic multiselect setup (without data manager)

**Component:** AgGridDataGridBasicMultiselectExampleComponent

**Selector:** `app-ag-grid-data-grid-basic-multiselect-example`

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
    selected: false,
    name: 'Billy Bob',
    age: 55,
    startDate: new Date('12/1/1994'),
    department: DEPARTMENTS[3],
    jobTitle: JOB_TITLES['Customer Support'][1],
  },
  {
    selected: false,
    name: 'Jane Deere',
    age: 33,
    startDate: new Date('7/15/2009'),
    department: DEPARTMENTS[2],
    jobTitle: JOB_TITLES['Engineering'][2],
  },
  {
    selected: false,
    name: 'John Doe',
    age: 38,
    startDate: new Date('9/1/2017'),
    endDate: new Date('9/30/2017'),
    department: DEPARTMENTS[1],
  },
  {
    selected: false,
    name: 'David Smith',
    age: 51,
    startDate: new Date('1/1/2012'),
    endDate: new Date('6/15/2018'),
    department: DEPARTMENTS[2],
    jobTitle: JOB_TITLES['Engineering'][4],
  },
  {
    selected: true,
    name: 'Emily Johnson',
    age: 41,
    startDate: new Date('1/15/2014'),
    department: DEPARTMENTS[0],
    jobTitle: JOB_TITLES['Marketing'][2],
  },
  {
    selected: false,
    name: 'Nicole Davidson',
    age: 22,
    startDate: new Date('11/1/2019'),
    department: DEPARTMENTS[2],
    jobTitle: JOB_TITLES['Engineering'][0],
  },
  {
    selected: false,
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
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import { SkyAgGridModule, SkyAgGridService, SkyCellType } from '@skyux/ag-grid';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ColDef,
  GridOptions,
  ModuleRegistry,
  ValueFormatterParams,
} from 'ag-grid-community';
import { of } from 'rxjs';

import { ContextMenuComponent } from './context-menu.component';
import { AG_GRID_DEMO_DATA, AgGridDemoRow } from './data';

ModuleRegistry.registerModules([AllCommunityModule]);

/**
 * @title Basic multiselect setup (without data manager)
 */
@Component({
  selector: 'app-ag-grid-data-grid-basic-multiselect-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [AgGridModule, SkyAgGridModule],
})
export class AgGridDataGridBasicMultiselectExampleComponent {
  protected gridData = AG_GRID_DEMO_DATA;
  protected gridOptions: GridOptions;

  #columnDefs: ColDef[] = [
    {
      field: 'selected',
      type: SkyCellType.RowSelector,
      cellRendererParams: {
        // Could be a SkyAppResourcesService.getString call that returns an observable.
        label: (data: AgGridDemoRow) => of(`Select ${data.name}`),
      },
    },
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

  readonly #agGridSvc = inject(SkyAgGridService);

  constructor() {
    const gridOptions: GridOptions = {
      columnDefs: this.#columnDefs,
    };

    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions,
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

```

---

## Basic setup (without data manager)

**Component:** AgGridDataGridBasicExampleComponent

**Selector:** `app-ag-grid-data-grid-basic-example`

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
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import { SkyAgGridModule, SkyAgGridService, SkyCellType } from '@skyux/ag-grid';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ColDef,
  GridOptions,
  ModuleRegistry,
  ValueFormatterParams,
} from 'ag-grid-community';

import { ContextMenuComponent } from './context-menu.component';
import { AG_GRID_DEMO_DATA, AgGridDemoRow } from './data';

ModuleRegistry.registerModules([AllCommunityModule]);

/**
 * @title Basic setup (without data manager)
 */
@Component({
  selector: 'app-ag-grid-data-grid-basic-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [AgGridModule, SkyAgGridModule],
})
export class AgGridDataGridBasicExampleComponent {
  protected gridData = AG_GRID_DEMO_DATA;
  protected gridOptions: GridOptions;

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

  readonly #agGridSvc = inject(SkyAgGridService);

  constructor() {
    const gridOptions: GridOptions = {
      columnDefs: this.#columnDefs,
      rowSelection: { mode: 'singleRow' },
    };

    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions,
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

```

---

## Data manager multiselect setup

**Component:** AgGridDataGridDataManagerMultiselectExampleComponent

**Selector:** `app-ag-grid-data-grid-data-manager-multiselect-example`

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
    selected: false,
    name: 'Billy Bob',
    age: 55,
    startDate: new Date('12/1/1994'),
    department: DEPARTMENTS[3],
    jobTitle: JOB_TITLES['Customer Support'][1],
  },
  {
    selected: false,
    name: 'Jane Deere',
    age: 33,
    startDate: new Date('7/15/2009'),
    department: DEPARTMENTS[2],
    jobTitle: JOB_TITLES['Engineering'][2],
  },
  {
    selected: false,
    name: 'John Doe',
    age: 38,
    startDate: new Date('9/1/2017'),
    endDate: new Date('9/30/2017'),
    department: DEPARTMENTS[1],
    jobTitle: JOB_TITLES['Sales'][1],
  },
  {
    selected: false,
    name: 'David Smith',
    age: 51,
    startDate: new Date('1/1/2012'),
    endDate: new Date('6/15/2018'),
    department: DEPARTMENTS[2],
    jobTitle: JOB_TITLES['Engineering'][4],
  },
  {
    selected: true,
    name: 'Emily Johnson',
    age: 41,
    startDate: new Date('1/15/2014'),
    department: DEPARTMENTS[0],
    jobTitle: JOB_TITLES['Marketing'][2],
  },
  {
    selected: false,
    name: 'Nicole Davidson',
    age: 22,
    startDate: new Date('11/1/2019'),
    department: DEPARTMENTS[2],
    jobTitle: JOB_TITLES['Engineering'][0],
  },
  {
    selected: false,
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
import {
  SkyDataManagerConfig,
  SkyDataManagerModule,
  SkyDataManagerService,
  SkyDataManagerState,
} from '@skyux/data-manager';

import { Subject, takeUntil } from 'rxjs';

import { AG_GRID_DEMO_DATA } from './data';
import { FilterModalComponent } from './filter-modal.component';
import { Filters } from './filters';
import { ViewGridComponent } from './view-grid.component';

/**
 * @title Data manager multiselect setup
 */
@Component({
  selector: 'app-ag-grid-data-grid-data-manager-multiselect-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  providers: [SkyDataManagerService],
  imports: [SkyDataManagerModule, ViewGridComponent],
})
export class AgGridDataGridDataManagerMultiselectExampleComponent
  implements OnInit, OnDestroy
{
  protected items = AG_GRID_DEMO_DATA;

  #dataManagerConfig: SkyDataManagerConfig = {
    filterModalComponent: FilterModalComponent,
    sortOptions: [
      {
        id: 'az',
        label: 'Name (A - Z)',
        descending: false,
        propertyName: 'name',
      },
      {
        id: 'za',
        label: 'Name (Z - A)',
        descending: true,
        propertyName: 'name',
      },
    ],
  };

  #defaultDataState = new SkyDataManagerState({
    filterData: {
      filtersApplied: false,
      filters: {
        hideSales: false,
        jobTitle: 'any',
      } satisfies Filters,
    },
    views: [
      {
        viewId: 'dataGridMultiselectWithDataManagerView',
        displayedColumnIds: [
          'selected',
          'context',
          'name',
          'age',
          'startDate',
          'endDate',
          'department',
          'jobTitle',
        ],
      },
    ],
  });

  #activeViewId = 'dataGridMultiselectWithDataManagerView';
  #ngUnsubscribe = new Subject<void>();

  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #dataManagerSvc = inject(SkyDataManagerService);

  constructor() {
    this.#dataManagerSvc
      .getActiveViewIdUpdates()
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((activeViewId) => {
        this.#activeViewId = activeViewId;
        this.#changeDetectorRef.detectChanges();
      });
  }

  public ngOnInit(): void {
    this.#dataManagerSvc.initDataManager({
      activeViewId: this.#activeViewId,
      dataManagerConfig: this.#dataManagerConfig,
      defaultDataState: this.#defaultDataState,
    });
  }

  public ngOnDestroy(): void {
    this.#ngUnsubscribe.next();
    this.#ngUnsubscribe.complete();
  }
}

```

#### filter-modal.component.ts

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  inject,
} from '@angular/core';
import { FormsModule } from '@angular/forms';
import { SkyIdModule } from '@skyux/core';
import {
  SkyDataManagerFilterData,
  SkyDataManagerFilterModalContext,
} from '@skyux/data-manager';
import { SkyCheckboxModule } from '@skyux/forms';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';

import { Filters } from './filters';

@Component({
  selector: 'app-filter-modal',
  templateUrl: './filter-modal.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [FormsModule, SkyCheckboxModule, SkyIdModule, SkyModalModule],
})
export class FilterModalComponent {
  protected hideSales = false;
  protected jobTitle = '';

  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #context = inject(SkyDataManagerFilterModalContext);
  readonly #instance = inject(SkyModalInstance);

  constructor() {
    if (this.#context.filterData && this.#context.filterData.filters) {
      const filters = this.#context.filterData.filters as Filters;

      this.jobTitle = filters.jobTitle ?? 'any';
      this.hideSales = filters.hideSales ?? false;
    }

    this.#changeDetectorRef.markForCheck();
  }

  protected applyFilters(): void {
    const result: SkyDataManagerFilterData = {};

    result.filtersApplied = this.jobTitle !== 'any' || this.hideSales;
    result.filters = {
      jobTitle: this.jobTitle,
      hideSales: this.hideSales,
    } satisfies Filters;

    this.#changeDetectorRef.markForCheck();
    this.#instance.save(result);
  }

  protected clearAllFilters(): void {
    this.hideSales = false;
    this.jobTitle = 'any';
    this.#changeDetectorRef.markForCheck();
  }

  protected cancel(): void {
    this.#instance.cancel();
  }
}

```

#### filters.ts

```typescript
export interface Filters {
  jobTitle?: string;
  hideSales?: boolean;
}

```

#### view-grid.component.ts

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  Input,
  OnDestroy,
  OnInit,
  inject,
} from '@angular/core';
import { SkyAgGridModule, SkyAgGridService, SkyCellType } from '@skyux/ag-grid';
import {
  SkyDataManagerColumnPickerOption,
  SkyDataManagerService,
  SkyDataManagerState,
  SkyDataViewConfig,
  SkyDataViewState,
} from '@skyux/data-manager';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ColDef,
  GridApi,
  GridOptions,
  GridReadyEvent,
  ModuleRegistry,
  RowSelectedEvent,
  ValueFormatterParams,
} from 'ag-grid-community';
import { Subject, of, takeUntil } from 'rxjs';

import { ContextMenuComponent } from './context-menu.component';
import { AgGridDemoRow } from './data';
import { Filters } from './filters';

ModuleRegistry.registerModules([AllCommunityModule]);

@Component({
  selector: 'app-view-grid',
  templateUrl: './view-grid.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [AgGridModule, SkyAgGridModule],
})
export class ViewGridComponent implements OnInit, OnDestroy {
  @Input()
  public items: AgGridDemoRow[] = [];

  protected displayedItems: AgGridDemoRow[] = [];
  protected gridOptions!: GridOptions;
  protected isGridReadyForInitialization = false;
  protected isViewActive = false;
  protected noRowsTemplate = `<div class="sky-deemphasized">No results found.</div>`;
  protected viewConfig: SkyDataViewConfig;

  #columnDefs: ColDef[] = [
    {
      field: 'selected',
      type: SkyCellType.RowSelector,
      cellRendererParams: {
        // Could be a SkyAppResourcesService.getString call that returns an observable.
        label: (data: AgGridDemoRow) => of(`Select ${data.name}`),
      },
    },
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

  #columnPickerOptions: SkyDataManagerColumnPickerOption[] = [
    {
      id: 'selected',
      label: '',
      alwaysDisplayed: true,
    },
    {
      id: 'context',
      label: '',
      alwaysDisplayed: true,
    },
    {
      id: 'name',
      label: 'Name',
      description: 'The name of the employee.',
    },
    {
      id: 'age',
      label: 'Age',
      description: 'The age of the employee.',
    },
    {
      id: 'startDate',
      label: 'Start date',
      description: 'The start date of the employee.',
    },
    {
      id: 'endDate',
      label: 'End date',
      description: 'The end date of the employee.',
    },
    {
      id: 'department',
      label: 'Department',
      description: 'The department of the employee',
    },
    {
      id: 'jobTitle',
      label: 'Title',
      description: 'The job title of the employee.',
    },
  ];

  #dataState = new SkyDataManagerState({});
  #gridApi?: GridApi;
  #ngUnsubscribe = new Subject<void>();
  #viewId = 'dataGridMultiselectWithDataManagerView';

  readonly #agGridSvc = inject(SkyAgGridService);
  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #dataManagerSvc = inject(SkyDataManagerService);

  constructor() {
    this.viewConfig = {
      id: this.#viewId,
      name: 'Data Grid View',
      iconName: 'table',
      searchEnabled: true,
      multiselectToolbarEnabled: true,
      columnPickerEnabled: true,
      filterButtonEnabled: true,
      columnOptions: this.#columnPickerOptions,
    };
  }

  public ngOnInit(): void {
    this.displayedItems = this.items;

    this.#dataManagerSvc.initDataView(this.viewConfig);

    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions: {
        columnDefs: this.#columnDefs,
        onGridReady: this.onGridReady.bind(this),
      },
    });

    this.#dataManagerSvc
      .getDataStateUpdates(this.#viewId)
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((state) => {
        this.#dataState = state;
        this.#updateColumnOrder();
        this.isGridReadyForInitialization = true;
        this.#updateDisplayedItems();
        this.#changeDetectorRef.detectChanges();
      });

    this.#dataManagerSvc
      .getActiveViewIdUpdates()
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((id) => {
        this.isViewActive = id === this.#viewId;
        this.#changeDetectorRef.detectChanges();
      });
  }

  public ngOnDestroy(): void {
    this.#ngUnsubscribe.next();
    this.#ngUnsubscribe.complete();
  }

  public onGridReady(gridReadyEvent: GridReadyEvent): void {
    this.#gridApi = gridReadyEvent.api;
    this.#updateDisplayedItems();
  }

  protected onRowSelected(
    rowSelectedEvent: RowSelectedEvent<AgGridDemoRow>,
  ): void {
    if (!rowSelectedEvent.data?.selected) {
      this.#updateDisplayedItems();
    }
  }

  #searchItems(items: AgGridDemoRow[]): AgGridDemoRow[] {
    let searchedItems = items;
    const searchText = this.#dataState && this.#dataState.searchText;

    if (searchText) {
      searchedItems = items.filter((item) => {
        let property: keyof typeof item;

        for (property in item) {
          if (
            Object.prototype.hasOwnProperty.call(item, property) &&
            property === 'name'
          ) {
            const propertyText = item[property].toLowerCase();
            if (propertyText.includes(searchText)) {
              return true;
            }
          }
        }

        return false;
      });
    }

    return searchedItems;
  }

  #filterItems(items: AgGridDemoRow[]): AgGridDemoRow[] {
    let filteredItems = items;
    const filterData = this.#dataState && this.#dataState.filterData;

    if (filterData?.filters) {
      const filters = filterData.filters as Filters;

      filteredItems = items.filter((item) => {
        return (
          (!!(filters.hideSales && item.department.name !== 'Sales') ||
            !filters.hideSales) &&
          ((filters.jobTitle !== 'any' &&
            item.jobTitle?.name === filters.jobTitle) ||
            !filters.jobTitle ||
            filters.jobTitle === 'any')
        );
      });
    }

    return filteredItems;
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

  #updateColumnOrder(): void {
    const viewState: SkyDataViewState | undefined =
      this.#dataState.getViewStateById(this.#viewId);

    if (viewState) {
      this.#columnDefs.sort((columnDefinition1, columnDefinition2) => {
        const displayedColumnIdIndex1: number =
          viewState.displayedColumnIds.findIndex(
            (aDisplayedColumnId: string) =>
              aDisplayedColumnId === columnDefinition1.field,
          );

        const displayedColumnIdIndex2: number =
          viewState.displayedColumnIds.findIndex(
            (aDisplayedColumnId: string) =>
              aDisplayedColumnId === columnDefinition2.field,
          );

        if (displayedColumnIdIndex1 === -1) {
          return 0;
        } else if (displayedColumnIdIndex2 === -1) {
          return 0;
        } else {
          return displayedColumnIdIndex1 - displayedColumnIdIndex2;
        }
      });

      this.#changeDetectorRef.markForCheck();
    }
  }

  #updateDisplayedItems(): void {
    const sortOption = this.#dataState.activeSortOption;

    if (this.#gridApi && sortOption) {
      this.#gridApi.applyColumnState({
        state: [
          {
            colId: sortOption.propertyName,
            sort: sortOption.descending ? 'desc' : 'asc',
          },
        ],
      });
    }

    this.displayedItems = this.#filterItems(this.#searchItems(this.items));

    if (this.#dataState.onlyShowSelected) {
      this.displayedItems = this.displayedItems.filter((item) => item.selected);
    }

    if (this.displayedItems.length > 0) {
      this.#gridApi?.hideOverlay();
    } else {
      this.#gridApi?.showNoRowsOverlay();
    }

    this.#dataManagerSvc.updateDataSummary(
      {
        totalItems: this.items.length,
        itemsMatching: this.displayedItems.length,
      },
      this.#viewId,
    );
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
<sky-data-manager>
  <sky-data-manager-toolbar />
  <app-view-grid [items]="items" />
</sky-data-manager>

```

#### filter-modal.component.html

```html
<sky-modal headingText="Filter employees">
  <sky-modal-content>
    <label [for]="jobTitleInput.id">Job Title</label>
    <select
      #jobTitleInput
      class="sky-form-control"
      skyId="jobTitleInput"
      [(ngModel)]="jobTitle"
    >
      <option value="any">Any job title</option>
      <option value="Product Manager">Product Manager</option>
      <option value="Software Engineer">Software Engineer</option>
    </select>
    <div class="sky-margin-stacked-lg">
      <sky-checkbox labelText="Hide Sales employees" [(ngModel)]="hideSales" />
    </div>
  </sky-modal-content>
  <sky-modal-footer>
    <button
      class="sky-btn sky-btn-primary"
      type="button"
      (click)="applyFilters()"
    >
      Apply filters
    </button>
    <button
      class="sky-btn sky-btn-link"
      type="button"
      (click)="clearAllFilters()"
    >
      Clear all filters
    </button>
    <button class="sky-btn sky-btn-link" type="button" (click)="cancel()">
      Cancel
    </button>
  </sky-modal-footer>
</sky-modal>

```

#### view-grid.component.html

```html
<sky-data-view skyAgGridDataManagerAdapter [viewId]="viewConfig.id">
  @if (isViewActive && isGridReadyForInitialization) {
    <sky-ag-grid-wrapper>
      <ag-grid-angular
        [gridOptions]="gridOptions"
        [rowData]="displayedItems"
        [overlayNoRowsTemplate]="noRowsTemplate"
        (rowSelected)="onRowSelected($event)"
      />
    </sky-ag-grid-wrapper>
  }
</sky-data-view>

```

---

## Data manager setup

**Component:** AgGridDataGridDataManagerExampleComponent

**Selector:** `app-ag-grid-data-grid-data-manager-example`

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
    jobTitle: JOB_TITLES['Sales'][1],
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
import {
  SkyDataManagerModule,
  SkyDataManagerService,
  SkyDataManagerState,
} from '@skyux/data-manager';

import { Subject, takeUntil } from 'rxjs';

import { AG_GRID_DEMO_DATA } from './data';
import { FilterModalComponent } from './filter-modal.component';
import { Filters } from './filters';
import { ViewGridComponent } from './view-grid.component';

/**
 * @title Data manager setup
 */
@Component({
  selector: 'app-ag-grid-data-grid-data-manager-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  providers: [SkyDataManagerService],
  imports: [SkyDataManagerModule, ViewGridComponent],
})
export class AgGridDataGridDataManagerExampleComponent
  implements OnInit, OnDestroy
{
  protected items = AG_GRID_DEMO_DATA;

  #activeViewId = 'dataGridWithDataManagerView';

  #dataManagerConfig = {
    filterModalComponent: FilterModalComponent,
    sortOptions: [
      {
        id: 'az',
        label: 'Name (A - Z)',
        descending: false,
        propertyName: 'name',
      },
      {
        id: 'za',
        label: 'Name (Z - A)',
        descending: true,
        propertyName: 'name',
      },
    ],
  };

  #defaultDataState = new SkyDataManagerState({
    filterData: {
      filtersApplied: false,
      filters: {
        hideSales: false,
        jobTitle: 'any',
      } satisfies Filters,
    },
    views: [
      {
        viewId: 'dataGridWithDataManagerView',
        displayedColumnIds: [
          'context',
          'name',
          'age',
          'startDate',
          'endDate',
          'department',
          'jobTitle',
        ],
      },
    ],
  });

  #ngUnsubscribe = new Subject<void>();

  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #dataManagerSvc = inject(SkyDataManagerService);

  constructor() {
    this.#dataManagerSvc
      .getActiveViewIdUpdates()
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((activeViewId) => {
        this.#activeViewId = activeViewId;
        this.#changeDetectorRef.detectChanges();
      });
  }

  public ngOnInit(): void {
    this.#dataManagerSvc.initDataManager({
      activeViewId: this.#activeViewId,
      dataManagerConfig: this.#dataManagerConfig,
      defaultDataState: this.#defaultDataState,
    });
  }

  public ngOnDestroy(): void {
    this.#ngUnsubscribe.next();
    this.#ngUnsubscribe.complete();
  }
}

```

#### filter-modal.component.ts

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  inject,
} from '@angular/core';
import { FormsModule } from '@angular/forms';
import { SkyIdModule } from '@skyux/core';
import {
  SkyDataManagerFilterData,
  SkyDataManagerFilterModalContext,
} from '@skyux/data-manager';
import { SkyCheckboxModule } from '@skyux/forms';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';

import { Filters } from './filters';

@Component({
  selector: 'app-filter-modal',
  templateUrl: './filter-modal.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [FormsModule, SkyCheckboxModule, SkyIdModule, SkyModalModule],
})
export class FilterModalComponent {
  protected hideSales = false;
  protected jobTitle = '';

  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #context = inject(SkyDataManagerFilterModalContext);
  readonly #instance = inject(SkyModalInstance);

  constructor() {
    if (this.#context.filterData && this.#context.filterData.filters) {
      const filters = this.#context.filterData.filters as Filters;

      this.jobTitle = filters.jobTitle ?? 'any';
      this.hideSales = filters.hideSales ?? false;
    }

    this.#changeDetectorRef.markForCheck();
  }

  protected applyFilters(): void {
    const result: SkyDataManagerFilterData = {};

    result.filtersApplied = this.jobTitle !== 'any' || this.hideSales;
    result.filters = {
      jobTitle: this.jobTitle,
      hideSales: this.hideSales,
    } satisfies Filters;

    this.#changeDetectorRef.markForCheck();
    this.#instance.save(result);
  }

  protected clearAllFilters(): void {
    this.hideSales = false;
    this.jobTitle = 'any';
    this.#changeDetectorRef.markForCheck();
  }

  protected cancel(): void {
    this.#instance.cancel();
  }
}

```

#### filters.ts

```typescript
export interface Filters {
  jobTitle?: string;
  hideSales?: boolean;
}

```

#### view-grid.component.ts

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  Input,
  OnDestroy,
  OnInit,
  inject,
} from '@angular/core';
import { SkyAgGridModule, SkyAgGridService, SkyCellType } from '@skyux/ag-grid';
import {
  SkyDataManagerColumnPickerOption,
  SkyDataManagerService,
  SkyDataManagerState,
  SkyDataViewConfig,
  SkyDataViewState,
} from '@skyux/data-manager';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ColDef,
  GridApi,
  GridOptions,
  GridReadyEvent,
  ModuleRegistry,
  RowSelectedEvent,
  ValueFormatterParams,
} from 'ag-grid-community';
import { Subject, takeUntil } from 'rxjs';

import { ContextMenuComponent } from './context-menu.component';
import { AgGridDemoRow } from './data';
import { Filters } from './filters';

ModuleRegistry.registerModules([AllCommunityModule]);

@Component({
  selector: 'app-view-grid',
  templateUrl: './view-grid.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [AgGridModule, SkyAgGridModule],
})
export class ViewGridComponent implements OnInit, OnDestroy {
  @Input()
  public items: AgGridDemoRow[] = [];

  protected displayedItems: AgGridDemoRow[] = [];
  protected gridOptions!: GridOptions;
  protected isGridReadyForInitialization = false;
  protected isViewActive = false;
  protected noRowsTemplate = `<div class="sky-deemphasized">No results found.</div>`;
  protected viewConfig: SkyDataViewConfig;

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

  #columnPickerOptions: SkyDataManagerColumnPickerOption[] = [
    {
      id: 'context',
      label: '',
      alwaysDisplayed: true,
    },
    {
      id: 'name',
      label: 'Name',
      description: 'The name of the employee.',
    },
    {
      id: 'age',
      label: 'Age',
      description: 'The age of the employee.',
    },
    {
      id: 'startDate',
      label: 'Start date',
      description: 'The start date of the employee.',
    },
    {
      id: 'endDate',
      label: 'End date',
      description: 'The end date of the employee.',
    },
    {
      id: 'department',
      label: 'Department',
      description: 'The department of the employee',
    },
    {
      id: 'jobTitle',
      label: 'Title',
      description: 'The job title of the employee.',
    },
  ];

  #dataState = new SkyDataManagerState({});
  #gridApi: GridApi | undefined;
  #ngUnsubscribe = new Subject<void>();
  #viewId = 'dataGridWithDataManagerView';

  readonly #agGridSvc = inject(SkyAgGridService);
  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #dataManagerSvc = inject(SkyDataManagerService);

  constructor() {
    this.viewConfig = {
      id: this.#viewId,
      name: 'Data Grid View',
      iconName: 'table',
      searchEnabled: true,
      columnPickerEnabled: true,
      filterButtonEnabled: true,
      columnOptions: this.#columnPickerOptions,
    };
  }

  public ngOnInit(): void {
    this.displayedItems = this.items;

    this.#dataManagerSvc.initDataView(this.viewConfig);

    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions: {
        columnDefs: this.#columnDefs,
        onGridReady: this.onGridReady.bind(this),
        rowSelection: { mode: 'singleRow' },
      },
    });

    this.#dataManagerSvc
      .getDataStateUpdates(this.#viewId)
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((state) => {
        this.#dataState = state;
        this.#updateColumnOrder();
        this.isGridReadyForInitialization = true;
        this.#updateDisplayedItems();
        this.#changeDetectorRef.detectChanges();
      });

    this.#dataManagerSvc
      .getActiveViewIdUpdates()
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((id) => {
        this.isViewActive = id === this.#viewId;
        this.#changeDetectorRef.detectChanges();
      });
  }

  public ngOnDestroy(): void {
    this.#ngUnsubscribe.next();
    this.#ngUnsubscribe.complete();
  }

  public onGridReady(gridReadyEvent: GridReadyEvent): void {
    this.#gridApi = gridReadyEvent.api;
    this.#updateDisplayedItems();
  }

  protected onRowSelected(
    rowSelectedEvent: RowSelectedEvent<AgGridDemoRow>,
  ): void {
    if (!rowSelectedEvent.data?.selected) {
      this.#updateDisplayedItems();
    }
  }

  #searchItems(items: AgGridDemoRow[]): AgGridDemoRow[] {
    let searchedItems = items;
    const searchText = this.#dataState && this.#dataState.searchText;

    if (searchText) {
      searchedItems = items.filter((item: AgGridDemoRow) => {
        let property: keyof typeof item;

        for (property in item) {
          if (
            Object.prototype.hasOwnProperty.call(item, property) &&
            property === 'name'
          ) {
            const propertyText = item[property].toLowerCase();

            if (propertyText.includes(searchText)) {
              return true;
            }
          }
        }

        return false;
      });
    }

    return searchedItems;
  }

  #filterItems(items: AgGridDemoRow[]): AgGridDemoRow[] {
    let filteredItems = items;
    const filterData = this.#dataState && this.#dataState.filterData;

    if (filterData?.filters) {
      const filters = filterData.filters as Filters;

      filteredItems = items.filter((item: AgGridDemoRow) => {
        return (
          (!!(filters.hideSales && item.department.name !== 'Sales') ||
            !filters.hideSales) &&
          ((filters.jobTitle !== 'any' &&
            item.jobTitle?.name === filters.jobTitle) ||
            !filters.jobTitle ||
            filters.jobTitle === 'any')
        );
      });
    }

    return filteredItems;
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

  #updateColumnOrder(): void {
    const viewState: SkyDataViewState | undefined =
      this.#dataState.getViewStateById(this.#viewId);

    if (viewState) {
      this.#columnDefs.sort((columnDefinition1, columnDefinition2) => {
        const displayedColumnIdIndex1: number =
          viewState.displayedColumnIds.findIndex(
            (aDisplayedColumnId: string) =>
              aDisplayedColumnId === columnDefinition1.field,
          );

        const displayedColumnIdIndex2: number =
          viewState.displayedColumnIds.findIndex(
            (aDisplayedColumnId: string) =>
              aDisplayedColumnId === columnDefinition2.field,
          );

        if (displayedColumnIdIndex1 === -1) {
          return 0;
        } else if (displayedColumnIdIndex2 === -1) {
          return 0;
        } else {
          return displayedColumnIdIndex1 - displayedColumnIdIndex2;
        }
      });

      this.#changeDetectorRef.markForCheck();
    }
  }

  #updateDisplayedItems(): void {
    this.displayedItems = this.#filterItems(this.#searchItems(this.items));

    if (this.#dataState.onlyShowSelected) {
      this.displayedItems = this.displayedItems.filter((item) => item.selected);
    }

    if (this.displayedItems.length > 0) {
      this.#gridApi?.hideOverlay();
    } else {
      this.#gridApi?.showNoRowsOverlay();
    }

    this.#dataManagerSvc.updateDataSummary(
      {
        totalItems: this.items.length,
        itemsMatching: this.displayedItems.length,
      },
      this.#viewId,
    );
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
<sky-data-manager>
  <sky-data-manager-toolbar />
  <app-view-grid [items]="items" />
</sky-data-manager>

```

#### filter-modal.component.html

```html
<sky-modal headingText="Filter employees">
  <sky-modal-content>
    <label [for]="jobTitleInput.id">Job Title</label>
    <select
      #jobTitleInput
      class="sky-form-control"
      skyId="jobTitleInput"
      [(ngModel)]="jobTitle"
    >
      <option value="any">Any job title</option>
      <option value="Product Manager">Product Manager</option>
      <option value="Software Engineer">Software Engineer</option>
    </select>
    <div class="sky-margin-stacked-lg">
      <sky-checkbox labelText="Hide Sales employees" [(ngModel)]="hideSales" />
    </div>
  </sky-modal-content>
  <sky-modal-footer>
    <button
      class="sky-btn sky-btn-primary"
      type="button"
      (click)="applyFilters()"
    >
      Apply filters
    </button>
    <button
      class="sky-btn sky-btn-link"
      type="button"
      (click)="clearAllFilters()"
    >
      Clear all filters
    </button>
    <button class="sky-btn sky-btn-link" type="button" (click)="cancel()">
      Cancel
    </button>
  </sky-modal-footer>
</sky-modal>

```

#### view-grid.component.html

```html
<sky-data-view skyAgGridDataManagerAdapter [viewId]="viewConfig.id">
  @if (isViewActive && isGridReadyForInitialization) {
    <sky-ag-grid-wrapper>
      <ag-grid-angular
        [gridOptions]="gridOptions"
        [rowData]="displayedItems"
        [overlayNoRowsTemplate]="noRowsTemplate"
        (rowSelected)="onRowSelected($event)"
      />
    </sky-ag-grid-wrapper>
  }
</sky-data-view>

```

---

## Basic setup with inline help (without data manager)

**Component:** AgGridDataGridInlineHelpExampleComponent

**Selector:** `app-ag-grid-data-grid-inline-help-example`

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
  inject,
} from '@angular/core';
import { SkyAgGridModule, SkyAgGridService, SkyCellType } from '@skyux/ag-grid';
import { SkyToolbarModule } from '@skyux/layout';
import { SkySearchModule } from '@skyux/lookup';

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
import { of } from 'rxjs';

import { ContextMenuComponent } from './context-menu.component';
import { AG_GRID_DEMO_DATA, AgGridDemoRow } from './data';
import { InlineHelpComponent } from './inline-help.component';

ModuleRegistry.registerModules([AllCommunityModule]);

/**
 * @title Basic setup with inline help (without data manager)
 */
@Component({
  selector: 'app-ag-grid-data-grid-inline-help-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [AgGridModule, SkyAgGridModule, SkySearchModule, SkyToolbarModule],
})
export class AgGridDataGridInlineHelpExampleComponent {
  protected gridData = AG_GRID_DEMO_DATA;
  protected gridOptions: GridOptions;
  protected searchText = '';
  protected noRowsTemplate: string;

  #columnDefs: ColDef[] = [
    {
      field: 'selected',
      type: SkyCellType.RowSelector,
      cellRendererParams: {
        // Could be a SkyAppResourcesService.getString call that returns an observable.
        label: (data: AgGridDemoRow) => of(`Select ${data.name}`),
      },
    },
    {
      colId: 'context',
      maxWidth: 50,
      sortable: false,
      cellRenderer: ContextMenuComponent,
    },
    {
      field: 'name',
      headerName: 'Name',
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
    {
      field: 'age',
      headerName: 'Age',
      type: SkyCellType.Number,
      maxWidth: 60,
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
    {
      field: 'startDate',
      headerName: 'Start date',
      type: SkyCellType.Date,
      sort: 'asc',
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
    {
      field: 'endDate',
      headerName: 'End date',
      type: SkyCellType.Date,
      valueFormatter: (params: ValueFormatterParams<AgGridDemoRow, Date>) =>
        this.#endDateFormatter(params),
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
    {
      field: 'department',
      headerName: 'Department',
      type: SkyCellType.Autocomplete,
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
    {
      field: 'jobTitle',
      headerName: 'Title',
      type: SkyCellType.Autocomplete,
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
  ];

  #gridApi: GridApi | undefined;

  readonly #agGridSvc = inject(SkyAgGridService);
  readonly #changeDetectorRef = inject(ChangeDetectorRef);

  constructor() {
    this.noRowsTemplate = `<div class="sky-font-deemphasized">No results found.</div>`;

    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions: {
        columnDefs: this.#columnDefs,
        onGridReady: this.onGridReady.bind(this),
      },
    });

    this.#changeDetectorRef.markForCheck();
  }

  public onGridReady(gridReadyEvent: GridReadyEvent): void {
    this.#gridApi = gridReadyEvent.api;
    this.#changeDetectorRef.markForCheck();
  }

  protected searchApplied(searchText: string | void): void {
    if (searchText) {
      this.searchText = searchText;
    } else {
      this.searchText = '';
    }
    if (this.#gridApi) {
      this.#gridApi.updateGridOptions({ quickFilterText: this.searchText });
      const displayedRowCount = this.#gridApi.getDisplayedRowCount();

      if (displayedRowCount > 0) {
        this.#gridApi.hideOverlay();
      } else {
        this.#gridApi.showNoRowsOverlay();
      }
    }
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

#### inline-help.component.ts

```typescript
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import { SkyAgGridHeaderInfo } from '@skyux/ag-grid';
import { SkyHelpInlineModule } from '@skyux/help-inline';

@Component({
  selector: 'app-inline-help',
  templateUrl: './inline-help.component.html',
  styles: [
    `
      :host {
        display: block;
      }
    `,
  ],
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [SkyHelpInlineModule],
})
export class InlineHelpComponent {
  protected displayName: string | undefined;
  readonly #headerInfo = inject(SkyAgGridHeaderInfo);

  constructor() {
    this.displayName = this.#headerInfo.displayName;
  }

  protected onHelpClick(): void {
    alert(`Help was clicked for ${this.displayName}.`);
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
<sky-toolbar>
  <sky-toolbar-item>
    <sky-search
      [debounceTime]="250"
      [searchText]="searchText"
      (searchApply)="searchApplied($event)"
      (searchChange)="searchApplied($event)"
      (searchClear)="searchApplied($event)"
    />
  </sky-toolbar-item>
</sky-toolbar>

<sky-ag-grid-wrapper>
  <ag-grid-angular
    [gridOptions]="gridOptions"
    [overlayNoRowsTemplate]="noRowsTemplate"
    [rowData]="gridData"
  />
</sky-ag-grid-wrapper>

```

#### inline-help.component.html

```html
<sky-help-inline
  ariaLabel="Information about {{ displayName }}"
  class="sky-control-help"
  (actionClick)="onHelpClick()"
/>

```

---

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

## Basic setup with template ref column type (without data manager)

**Component:** AgGridDataGridTemplateRefColumnExampleComponent

**Selector:** `app-ag-grid-data-grid-template-ref-column-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### data.ts

```typescript
export interface AgGridDemoRow {
  name: string;
  age: number;
  department: string;
  jobTitle: string;
}

export const AG_GRID_DEMO_DATA = [
  {
    name: 'Billy Bob',
    age: 55,
    department: 'Customer Support',
    jobTitle: 'Customer Support Representative',
    jobLevel: '🥈',
  },
  {
    name: 'Jane Deere',
    age: 33,
    department: 'Engineering',
    jobTitle: 'Software Engineer',
    jobLevel: '🥇',
  },
  {
    name: 'John Doe',
    age: 38,
    department: 'Engineering',
    jobTitle: 'UX Designer',
  },
  {
    name: 'David Smith',
    age: 51,
    department: 'Engineering',
    jobTitle: 'Software Engineer',
    jobLevel: '🥉',
  },
  {
    name: 'Emily Johnson',
    age: 41,
    department: 'Marketing',
    jobTitle: 'Customer Support Representative',
  },
  {
    name: 'Nicole Davidson',
    age: 22,
    startDate: new Date('11/1/2019'),
    department: 'Marketing',
    jobTitle: 'Account Manager',
    jobLevel: '🥈',
  },
  {
    name: 'Carl Roberts',
    age: 23,
    startDate: new Date('11/1/2019'),
    department: 'Marketing',
    jobTitle: 'Social Media Coordinator',
    jobLevel: '🥇',
  },
];

```

#### example.component.ts

```typescript
import {
  Component,
  OnInit,
  TemplateRef,
  ViewChild,
  inject,
} from '@angular/core';
import { SkyAgGridModule, SkyAgGridService, SkyCellType } from '@skyux/ag-grid';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  GridOptions,
  ModuleRegistry,
} from 'ag-grid-community';

import { AG_GRID_DEMO_DATA } from './data';

ModuleRegistry.registerModules([AllCommunityModule]);

/**
 * @title Basic setup with template ref column type (without data manager)
 */
@Component({
  selector: 'app-ag-grid-data-grid-template-ref-column-example',
  templateUrl: './example.component.html',
  imports: [AgGridModule, SkyAgGridModule],
})
export class AgGridDataGridTemplateRefColumnExampleComponent implements OnInit {
  @ViewChild('boldColumn', { static: true })
  protected boldColumn: TemplateRef<unknown> | undefined;

  @ViewChild('emphasizedColumn', { static: true })
  protected emphasizedColumn: TemplateRef<unknown> | undefined;

  protected gridData = AG_GRID_DEMO_DATA;
  protected gridOptions: GridOptions | undefined;

  readonly #agGridSvc = inject(SkyAgGridService);

  public ngOnInit(): void {
    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions: {
        columnDefs: [
          {
            field: 'name',
            headerName: 'Name',
            initialWidth: 150,
          },
          {
            field: 'age',
            headerName: 'Age',
            type: SkyCellType.Number,
            maxWidth: 80,
            resizable: false,
          },
          {
            field: 'department',
            headerName: 'Department',
            type: SkyCellType.Template,
            cellRendererParams: {
              template: this.boldColumn,
            },
            initialWidth: 220,
          },
          {
            field: 'jobTitle',
            headerName: 'Title',
            type: SkyCellType.Template,
            cellRendererParams: {
              template: this.emphasizedColumn,
            },
            initialWidth: 220,
          },
        ],
      },
    });
  }
}

```

#### example.component.html

```html
<ng-template #boldColumn let-value="value">
  <strong>{{ value }}</strong>
</ng-template>
<ng-template #emphasizedColumn let-value="value" let-row="row">
  @if (row['jobLevel']) {
    <span class="sky-margin-inline-sm sky-pull-right">{{
      row['jobLevel']
    }}</span>
  }
  <em>{{ value }}</em>
</ng-template>
<sky-ag-grid-wrapper>
  <ag-grid-angular [gridOptions]="gridOptions" [rowData]="gridData" />
</sky-ag-grid-wrapper>

```

---

## Basic setup with top scrollbar (without data manager)

**Component:** AgGridDataGridTopScrollExampleComponent

**Selector:** `app-ag-grid-data-grid-top-scroll-example`

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
    selected: true,
    name: 'Billy Bob',
    age: 55,
    startDate: new Date('12/1/1994'),
    department: DEPARTMENTS[3],
    jobTitle: JOB_TITLES['Customer Support'][1],
  },
  {
    selected: false,
    name: 'Jane Deere',
    age: 33,
    startDate: new Date('7/15/2009'),
    department: DEPARTMENTS[2],
    jobTitle: JOB_TITLES['Engineering'][2],
  },
  {
    selected: false,
    name: 'John Doe',
    age: 38,
    startDate: new Date('9/1/2017'),
    endDate: new Date('9/30/2017'),
    department: DEPARTMENTS[1],
  },
  {
    selected: false,
    name: 'David Smith',
    age: 51,
    startDate: new Date('1/1/2012'),
    endDate: new Date('6/15/2018'),
    department: DEPARTMENTS[2],
    jobTitle: JOB_TITLES['Engineering'][4],
  },
  {
    selected: true,
    name: 'Emily Johnson',
    age: 41,
    startDate: new Date('1/15/2014'),
    department: DEPARTMENTS[0],
    jobTitle: JOB_TITLES['Marketing'][2],
  },
  {
    selected: false,
    name: 'Nicole Davidson',
    age: 22,
    startDate: new Date('11/1/2019'),
    department: DEPARTMENTS[2],
    jobTitle: JOB_TITLES['Engineering'][0],
  },
  {
    selected: false,
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
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import { SkyAgGridModule, SkyAgGridService, SkyCellType } from '@skyux/ag-grid';
import { SkyToolbarModule } from '@skyux/layout';
import { SkySearchModule } from '@skyux/lookup';

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
import { of } from 'rxjs';

import { ContextMenuComponent } from './context-menu.component';
import { AG_GRID_DEMO_DATA, AgGridDemoRow } from './data';

ModuleRegistry.registerModules([AllCommunityModule]);

/**
 * @title Basic setup with top scrollbar (without data manager)
 */
@Component({
  selector: 'app-ag-grid-data-grid-top-scroll-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [AgGridModule, SkyAgGridModule, SkySearchModule, SkyToolbarModule],
})
export class AgGridDataGridTopScrollExampleComponent {
  protected gridData = AG_GRID_DEMO_DATA;
  protected gridOptions: GridOptions;
  protected searchText = '';
  protected noRowsTemplate = `<div class="sky-font-deemphasized">No results found.</div>`;

  #columnDefs: ColDef[] = [
    {
      colId: 'context',
      maxWidth: 50,
      sortable: false,
      cellRenderer: ContextMenuComponent,
    },
    {
      field: 'selected',
      type: SkyCellType.RowSelector,
      cellRendererParams: {
        // Could be a SkyAppResourcesService.getString call that returns an observable.
        label: (data: AgGridDemoRow) => of(`Select ${data.name}`),
      },
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

  #gridApi: GridApi | undefined;

  readonly #agGridSvc = inject(SkyAgGridService);

  constructor() {
    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions: {
        columnDefs: this.#columnDefs,
        onGridReady: (gridReadyEvent): void => {
          this.onGridReady(gridReadyEvent);
        },
        context: {
          enableTopScroll: true,
        },
      },
    });
  }

  public onGridReady(gridReadyEvent: GridReadyEvent): void {
    this.#gridApi = gridReadyEvent.api;
  }

  protected searchApplied(searchText: string | void): void {
    this.searchText = searchText ?? '';

    if (this.#gridApi) {
      this.#gridApi.updateGridOptions({ quickFilterText: this.searchText });
      const displayedRowCount = this.#gridApi.getDisplayedRowCount();
      if (displayedRowCount > 0) {
        this.#gridApi.hideOverlay();
      } else {
        this.#gridApi.showNoRowsOverlay();
      }
    }
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
<sky-toolbar>
  <sky-toolbar-item>
    <sky-search
      [debounceTime]="250"
      [searchText]="searchText"
      (searchApply)="searchApplied($event)"
      (searchChange)="searchApplied($event)"
      (searchClear)="searchApplied($event)"
    />
  </sky-toolbar-item>
</sky-toolbar>
<sky-ag-grid-wrapper>
  <ag-grid-angular
    [gridOptions]="gridOptions"
    [overlayNoRowsTemplate]="noRowsTemplate"
    [rowData]="gridData"
  />
</sky-ag-grid-wrapper>

```

---