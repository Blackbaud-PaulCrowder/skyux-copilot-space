---
component: 'data-manager'
type: 'code-examples'
description: 'Code examples for the data-manager component.'
---

# Data Manager Code Examples

## Data manager setup

**Component:** AgGridDataEntryGridDataManagerAddedExampleComponent

**Selector:** `app-ag-grid-data-entry-grid-data-manager-added-example`

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

export const AG_GRID_DEMO_DATA: AgGridDemoRow[] = [
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

#### edit-modal-context.ts

```typescript
import { AgGridDemoRow } from './data';

export class EditModalContext {
  public gridData: AgGridDemoRow[] = [];
}

```

#### edit-modal.component.ts

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  inject,
} from '@angular/core';
import {
  SkyAgGridAutocompleteProperties,
  SkyAgGridDatepickerProperties,
  SkyAgGridModule,
  SkyAgGridService,
  SkyCellType,
} from '@skyux/ag-grid';
import { SkyAutocompleteSelectionChange } from '@skyux/lookup';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ColDef,
  GridApi,
  GridOptions,
  GridReadyEvent,
  ICellEditorParams,
  IRowNode,
  ModuleRegistry,
} from 'ag-grid-community';

import { AgGridDemoRow, DEPARTMENTS, JOB_TITLES } from './data';
import { EditModalContext } from './edit-modal-context';

ModuleRegistry.registerModules([AllCommunityModule]);

@Component({
  selector: 'app-edit-modal',
  templateUrl: './edit-modal.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [AgGridModule, SkyAgGridModule, SkyModalModule],
})
export class EditModalComponent {
  protected gridData: AgGridDemoRow[];
  protected gridOptions: GridOptions;

  #columnDefs: ColDef[];
  #gridApi: GridApi | undefined;

  protected readonly instance = inject(SkyModalInstance);
  readonly #agGridService = inject(SkyAgGridService);
  readonly #changeDetector = inject(ChangeDetectorRef);
  readonly #context = inject(EditModalContext);

  constructor() {
    this.#columnDefs = [
      {
        field: 'name',
        headerName: 'Name',
      },
      {
        field: 'age',
        headerName: 'Age',
        type: SkyCellType.Number,
        maxWidth: 60,
        editable: true,
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
        editable: true,
        cellEditorParams: (
          params: ICellEditorParams<AgGridDemoRow>,
        ): { skyComponentProperties: SkyAgGridDatepickerProperties } => {
          return {
            skyComponentProperties: {
              minDate: params.data.startDate,
            },
          };
        },
      },
      {
        field: 'department',
        headerName: 'Department',
        type: SkyCellType.Autocomplete,
        editable: true,
        cellEditorParams: (
          params: ICellEditorParams<AgGridDemoRow>,
        ): { skyComponentProperties: SkyAgGridAutocompleteProperties } => {
          return {
            skyComponentProperties: {
              data: DEPARTMENTS,
              selectionChange: (change): void => {
                this.#departmentSelectionChange(change, params.node);
              },
            },
          };
        },
        onCellValueChanged: (event): void => {
          if (event.newValue !== event.oldValue) {
            this.#clearJobTitle(event.node);
          }
        },
      },
      {
        field: 'jobTitle',
        headerName: 'Title',
        type: SkyCellType.Autocomplete,
        editable: true,
        cellEditorParams: (
          params: ICellEditorParams<AgGridDemoRow>,
        ): { skyComponentProperties: SkyAgGridAutocompleteProperties } => {
          const selectedDepartment = params.data?.department?.name;

          const editParams: {
            skyComponentProperties: SkyAgGridAutocompleteProperties;
          } = { skyComponentProperties: { data: [] } };

          if (selectedDepartment) {
            editParams.skyComponentProperties.data =
              JOB_TITLES[selectedDepartment];
          }

          return editParams;
        },
      },
      {
        colId: 'validationCurrency',
        field: 'validationCurrency',
        headerName: 'Validation currency',
        type: [SkyCellType.CurrencyValidator],
        editable: true,
      },
      {
        colId: 'validationDate',
        field: 'validationDate',
        headerName: 'Validation date',
        type: [SkyCellType.Date, SkyCellType.Validator],
        cellRendererParams: {
          skyComponentProperties: {
            validator: (value: Date): boolean =>
              !!value && value > new Date(1985, 9, 26),
            validatorMessage: 'Enter a future date.',
          },
        },
        editable: true,
      },
    ];

    this.gridData = this.#context.gridData;

    const gridOptions: GridOptions = {
      columnDefs: this.#columnDefs,
      onGridReady: (gridReadyEvent): void => {
        this.onGridReady(gridReadyEvent);
      },
    };

    this.gridOptions = this.#agGridService.getEditableGridOptions({
      gridOptions,
    });

    this.#changeDetector.markForCheck();
  }

  public onGridReady(gridReadyEvent: GridReadyEvent): void {
    this.#gridApi = gridReadyEvent.api;
    this.#changeDetector.markForCheck();
  }

  #departmentSelectionChange(
    change: SkyAutocompleteSelectionChange,
    node: IRowNode<AgGridDemoRow>,
  ): void {
    if (change.selectedItem && change.selectedItem !== node.data?.department) {
      this.#clearJobTitle(node);
    }
  }

  #clearJobTitle(node: IRowNode<AgGridDemoRow> | null): void {
    if (node?.data) {
      node.data.jobTitle = undefined;

      if (this.#gridApi) {
        this.#gridApi.refreshCells({
          rowNodes: [node],
        });
      }
    }

    this.#changeDetector.markForCheck();
  }
}

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
import { SkyModalConfigurationInterface, SkyModalService } from '@skyux/modals';

import { Subject, takeUntil } from 'rxjs';

import { AG_GRID_DEMO_DATA, AgGridDemoRow } from './data';
import { EditModalContext } from './edit-modal-context';
import { EditModalComponent } from './edit-modal.component';
import { FilterModalComponent } from './filter-modal.component';
import { ViewGridComponent } from './view-grid.component';

/**
 * @title Data manager setup
 */
@Component({
  selector: 'app-ag-grid-data-entry-grid-data-manager-added-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  providers: [SkyDataManagerService],
  imports: [ViewGridComponent, SkyDataManagerModule],
})
export class AgGridDataEntryGridDataManagerAddedExampleComponent
  implements OnInit, OnDestroy
{
  protected items = AG_GRID_DEMO_DATA;

  #activeViewId = 'dataEntryGridWithDataManagerView';

  #defaultDataState = new SkyDataManagerState({
    filterData: {
      filtersApplied: false,
      filters: {
        hideSales: false,
      },
    },
    views: [
      {
        viewId: 'dataEntryGridWithDataManagerView',
        displayedColumnIds: [
          'selected',
          'context',
          'name',
          'age',
          'startDate',
          'endDate',
          'department',
          'jobTitle',
          'validationCurrency',
          'validationDate',
        ],
      },
    ],
  });

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

  #ngUnsubscribe = new Subject<void>();

  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #dataManagerSvc = inject(SkyDataManagerService);
  readonly #modalSvc = inject(SkyModalService);

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

  protected openModal(): void {
    const context = new EditModalContext();
    context.gridData = this.items.slice();

    this.#changeDetectorRef.markForCheck();

    const options: SkyModalConfigurationInterface = {
      ariaDescribedBy: 'docs-edit-grid-modal-content',
      providers: [
        {
          provide: EditModalContext,
          useValue: context,
        },
      ],
      size: 'large',
    };

    const modalInstance = this.#modalSvc.open(EditModalComponent, options);

    modalInstance.closed.subscribe((result) => {
      if (result.reason === 'cancel' || result.reason === 'close') {
        alert('Edits canceled!');
      } else {
        this.items = result.data as AgGridDemoRow[];
        alert('Saving data!');
      }

      this.#changeDetectorRef.markForCheck();
    });
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

  readonly #changeDetector = inject(ChangeDetectorRef);
  readonly #context = inject(SkyDataManagerFilterModalContext);
  readonly #instance = inject(SkyModalInstance);

  constructor() {
    if (this.#context.filterData?.filters) {
      const filters = this.#context.filterData.filters as Filters;

      this.jobTitle = filters.jobTitle ?? 'any';
      this.hideSales = filters.hideSales ?? false;
    }

    this.#changeDetector.markForCheck();
  }

  protected applyFilters(): void {
    const result: SkyDataManagerFilterData = {};

    result.filtersApplied = this.jobTitle !== 'any' || this.hideSales;
    result.filters = {
      jobTitle: this.jobTitle,
      hideSales: this.hideSales,
    } satisfies Filters;

    this.#changeDetector.markForCheck();
    this.#instance.save(result);
  }

  protected clearAllFilters(): void {
    this.hideSales = false;
    this.jobTitle = 'any';
    this.#changeDetector.markForCheck();
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
  SkyDataManagerService,
  SkyDataManagerState,
  SkyDataViewConfig,
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
  public set items(value: AgGridDemoRow[]) {
    this.#_items = value;
    this.#changeDetectorRef.markForCheck();
    this.#gridApi?.refreshCells();
  }

  public get items(): AgGridDemoRow[] {
    return this.#_items;
  }

  #viewId = 'dataEntryGridWithDataManagerView';

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
      headerName: 'Context menu',
      headerComponentParams: {
        headerHidden: true,
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
    {
      field: 'validationCurrency',
      headerName: 'Validation currency',
      type: [SkyCellType.CurrencyValidator],
    },
    {
      field: 'validationDate',
      headerName: 'Validation date',
      type: [SkyCellType.Date, SkyCellType.Validator],
      cellRendererParams: {
        skyComponentProperties: {
          validator: (value: Date): boolean =>
            !!value && value > new Date(1985, 9, 26),
          validatorMessage: 'Please enter a future date',
        },
      },
    },
  ];

  protected displayedItems: AgGridDemoRow[] = [];
  protected gridOptions: GridOptions;
  protected isActive = false;
  protected isGridInitialized = false;
  protected noRowsTemplate = `<div class="sky-font-deemphasized">No results found.</div>`;
  protected viewConfig: SkyDataViewConfig = {
    id: this.#viewId,
    name: 'Data Grid View',
    iconName: 'table',
    searchEnabled: true,
    multiselectToolbarEnabled: true,
    columnPickerEnabled: true,
    filterButtonEnabled: true,
    columnOptions: [
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
      {
        id: 'validationCurrency',
        label: 'Validation currency',
        description: 'An example column for currency validation.',
      },
      {
        id: 'validationDate',
        label: 'Validation date',
        description: 'An example column for date validation.',
      },
    ],
  };

  #_items: AgGridDemoRow[] = [];

  #dataState = new SkyDataManagerState({});
  #gridApi: GridApi | undefined;
  #ngUnsubscribe = new Subject<void>();

  readonly #agGridSvc = inject(SkyAgGridService);
  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #dataManagerSvc = inject(SkyDataManagerService);

  constructor() {
    this.gridOptions = this.#agGridSvc.getEditableGridOptions({
      gridOptions: {
        columnDefs: this.#columnDefs,
        onGridReady: this.onGridReady.bind(this),
      },
    });
  }

  public ngOnInit(): void {
    this.displayedItems = this.items;

    this.#dataManagerSvc.initDataView(this.viewConfig);

    this.#dataManagerSvc
      .getDataStateUpdates(this.#viewId)
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((state) => {
        this.#dataState = state;
        this.#setInitialColumnOrder();
        this.#updateData();
        this.#changeDetectorRef.detectChanges();
      });

    this.#dataManagerSvc
      .getActiveViewIdUpdates()
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((id) => {
        this.isActive = id === this.#viewId;
        this.#changeDetectorRef.detectChanges();
      });
  }

  public ngOnDestroy(): void {
    this.#ngUnsubscribe.next();
    this.#ngUnsubscribe.complete();
  }

  protected onGridReady(gridReadyEvent: GridReadyEvent): void {
    this.#gridApi = gridReadyEvent.api;
    this.#updateData();
    this.#changeDetectorRef.markForCheck();
  }

  protected onRowSelected(
    rowSelectedEvent: RowSelectedEvent<AgGridDemoRow>,
  ): void {
    if (!rowSelectedEvent.data?.selected) {
      this.#updateData();
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

  #filterItems(items: AgGridDemoRow[]): AgGridDemoRow[] {
    let filteredItems = items;
    const filterData = this.#dataState.filterData;

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

  #searchItems(items: AgGridDemoRow[]): AgGridDemoRow[] {
    let searchedItems = items;
    const searchText = this.#dataState.searchText;

    if (searchText) {
      searchedItems = items.filter((item) => {
        let property: keyof typeof item;
        for (property in item) {
          if (
            Object.prototype.hasOwnProperty.call(item, property) &&
            property === 'name'
          ) {
            const propertyText = item[property]?.toLowerCase();
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

  #setInitialColumnOrder(): void {
    const viewState = this.#dataState.getViewStateById(this.#viewId);
    const visibleColumns = viewState?.displayedColumnIds ?? [];

    this.#columnDefs.sort((col1, col2) => {
      const col1Index = visibleColumns.findIndex(
        (colId: string) => colId === col1.colId,
      );
      const col2Index = visibleColumns.findIndex(
        (colId: string) => colId === col2.colId,
      );

      if (col1Index === -1) {
        col1.hide = true;
        return 0;
      } else if (col2Index === -1) {
        col2.hide = true;
        return 0;
      } else {
        return col1Index - col2Index;
      }
    });

    this.isGridInitialized = true;
    this.#changeDetectorRef.markForCheck();
  }

  #updateData(): void {
    this.displayedItems = this.#filterItems(this.#searchItems(this.items));

    if (this.#dataState.onlyShowSelected) {
      this.displayedItems = this.displayedItems.filter((item) => item.selected);
    }

    if (this.displayedItems.length > 0) {
      this.#gridApi?.hideOverlay();
    } else {
      this.#gridApi?.showNoRowsOverlay();
    }

    this.#changeDetectorRef.markForCheck();
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

#### edit-modal.component.html

```html
<sky-modal headingText="Edit employee information">
  <sky-modal-content>
    <sky-ag-grid-wrapper>
      <ag-grid-angular
        class="sky-ag-grid-editable"
        [gridOptions]="gridOptions"
        [rowData]="gridData"
      />
    </sky-ag-grid-wrapper>
  </sky-modal-content>
  <sky-modal-footer>
    <button
      class="sky-btn sky-btn-primary"
      type="button"
      (click)="instance.save(gridData)"
    >
      Save
    </button>
    <button
      class="sky-btn sky-btn-link"
      type="button"
      (click)="instance.cancel()"
    >
      Cancel
    </button>
  </sky-modal-footer>
</sky-modal>

```

#### example.component.html

```html
<sky-data-manager>
  <sky-data-manager-toolbar>
    <sky-data-manager-toolbar-left-item>
      <button
        class="sky-btn sky-btn-primary"
        type="button"
        (click)="openModal()"
      >
        Edit
      </button>
    </sky-data-manager-toolbar-left-item>
  </sky-data-manager-toolbar>
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
  @if (isActive && isGridInitialized) {
    <sky-ag-grid-wrapper>
      <ag-grid-angular
        [gridOptions]="gridOptions"
        [overlayNoRowsTemplate]="noRowsTemplate"
        [rowData]="displayedItems"
        (rowSelected)="onRowSelected($event)"
      />
    </sky-ag-grid-wrapper>
  }
</sky-data-view>

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

## Data manager with basic setup

**Component:** DataManagerBasicExampleComponent

**Selector:** `app-data-manager-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### data.ts

```typescript
export interface DataManagerDemoRow {
  selected?: boolean;
  id: string;
  name: string;
  description: string;
  type: string;
  color: string;
}

export const DATA_MANAGER_DEMO_DATA: DataManagerDemoRow[] = [
  {
    id: '1',
    name: 'Orange',
    description: 'A round, orange fruit. A great source of vitamin C.',
    type: 'citrus',
    color: 'orange',
  },
  {
    id: '2',
    name: 'Mango',
    description:
      "Very difficult to peel. Delicious in smoothies, but don't eat the skin.",
    type: 'other',
    color: 'orange',
  },
  {
    id: '3',
    name: 'Lime',
    description: 'A sour, green fruit used in many drinks. It grows on trees.',
    type: 'citrus',
    color: 'green',
  },
  {
    id: '4',
    name: 'Strawberry',
    description:
      'A red fruit that goes well with shortcake. It is the name of both the fruit and the plant!',
    type: 'berry',
    color: 'red',
  },
  {
    id: '5',
    name: 'Blueberry',
    description:
      'A small, blue fruit often found in muffins. When not ripe, they can be sour.',
    type: 'berry',
    color: 'blue',
  },
  {
    id: '6',
    name: 'Banana',
    description:
      'A yellow fruit with a thick skin. Monkeys love them, and in some countries it is customary to eat the peel.',
    type: 'other',
    color: 'yellow',
  },
];

```

#### example.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { provideNoopAnimations } from '@angular/platform-browser/animations';
import { SkyDataManagerHarness } from '@skyux/data-manager/testing';
import { SkyRepeaterHarness } from '@skyux/lists/testing';

import { DataManagerBasicExampleComponent } from './example.component';

describe('Data manager basic example', () => {
  async function setupTest(options?: { dataSkyId: string }): Promise<{
    dataManagerHarness: SkyDataManagerHarness;
    fixture: ComponentFixture<DataManagerBasicExampleComponent>;
    loader: HarnessLoader;
  }> {
    await TestBed.configureTestingModule({
      imports: [DataManagerBasicExampleComponent],
      providers: [provideNoopAnimations()],
    }).compileComponents();

    const fixture = TestBed.createComponent(DataManagerBasicExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const dataManagerHarness = options?.dataSkyId
      ? await loader.getHarness(
          SkyDataManagerHarness.with({ dataSkyId: options.dataSkyId }),
        )
      : await loader.getHarness(SkyDataManagerHarness);

    return { dataManagerHarness, fixture, loader };
  }

  it('should set up the component', async () => {
    const { dataManagerHarness, fixture } = await setupTest();

    const toolbarHarness = await dataManagerHarness.getToolbar();
    await toolbarHarness.clickSelectAll();

    const sortButtonHarness = await toolbarHarness.getSortButton();
    expect(sortButtonHarness).not.toBeNull();

    const repeaterView = await dataManagerHarness.getView({
      viewId: 'repeaterView',
    });
    const repeaterHarness = await repeaterView.queryHarness(SkyRepeaterHarness);
    const repeaterItems = await repeaterHarness.getRepeaterItems();
    expect(repeaterItems.length).toBe(4);

    for (const item of repeaterItems) {
      await expectAsync(item.isSelected()).toBeResolvedTo(true);
    }

    const viewActionsHarness = await toolbarHarness.getViewActions();
    expect(viewActionsHarness).not.toBeNull();

    const views = await viewActionsHarness?.getRadioButtons();
    await views?.[1].check();
    fixture.detectChanges();
    await fixture.whenStable();

    const filterButtonHarness = await toolbarHarness.getFilterButton();
    expect(filterButtonHarness).not.toBeNull();

    const searchHarness = await toolbarHarness.getSearch();
    expect(searchHarness).not.toBeNull();

    const columnPicker = await toolbarHarness.openColumnPicker();
    const columns = await columnPicker.getColumns();
    expect(columns.length).toBe(2);
  });
});

```

#### example.component.ts

```typescript
import {
  ChangeDetectionStrategy,
  Component,
  OnInit,
  inject,
} from '@angular/core';
import { SkyUIConfigService } from '@skyux/core';
import {
  SkyDataManagerModule,
  SkyDataManagerService,
  SkyDataManagerState,
} from '@skyux/data-manager';

import { DATA_MANAGER_DEMO_DATA, DataManagerDemoRow } from './data';
import { FilterModalComponent } from './filter-modal.component';
import { Filters } from './filters';
import { ViewGridComponent } from './view-grid.component';
import { ViewRepeaterComponent } from './view-repeater.component';

/**
 * @title Data manager with basic setup
 */
@Component({
  selector: 'app-data-manager-basic-example',
  templateUrl: './example.component.html',
  providers: [SkyDataManagerService, SkyUIConfigService],
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [SkyDataManagerModule, ViewGridComponent, ViewRepeaterComponent],
})
export class DataManagerBasicExampleComponent implements OnInit {
  protected items: DataManagerDemoRow[] = DATA_MANAGER_DEMO_DATA;

  readonly #dataManagerSvc = inject(SkyDataManagerService);

  public ngOnInit(): void {
    this.#dataManagerSvc.initDataManager({
      activeViewId: 'repeaterView',
      dataManagerConfig: {
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
      },
      defaultDataState: new SkyDataManagerState({
        filterData: {
          filtersApplied: true,
          filters: {
            hideOrange: true,
          } satisfies Filters,
        },
        views: [
          {
            viewId: 'gridView',
            displayedColumnIds: ['selected', 'name', 'description'],
          },
        ],
      }),
    });
  }
}

```

#### filter-modal.component.ts

```typescript
import { Component, OnInit, inject } from '@angular/core';
import { FormsModule, ReactiveFormsModule } from '@angular/forms';
import {
  SkyDataManagerFilterData,
  SkyDataManagerFilterModalContext,
} from '@skyux/data-manager';
import { SkyCheckboxModule, SkyInputBoxModule } from '@skyux/forms';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';

import { Filters } from './filters';

@Component({
  selector: 'app-filter-modal',
  templateUrl: './filter-modal.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyCheckboxModule,
    SkyInputBoxModule,
    SkyModalModule,
  ],
})
export class FilterModalComponent implements OnInit {
  protected fruitType: string | undefined;
  protected hideOrange: boolean | undefined;

  readonly #context = inject(SkyDataManagerFilterModalContext);
  readonly #instance = inject(SkyModalInstance);

  public ngOnInit(): void {
    if (this.#context.filterData?.filters) {
      const filters = this.#context.filterData.filters as Filters;

      this.fruitType = filters.type ?? 'any';
      this.hideOrange = filters.hideOrange ?? false;
    }
  }

  protected applyFilters(): void {
    const result: SkyDataManagerFilterData = {};

    result.filtersApplied = this.fruitType !== 'any' || this.hideOrange;
    result.filters = {
      type: this.fruitType,
      hideOrange: this.hideOrange,
    } satisfies Filters;

    this.#instance.save(result);
  }

  protected clearAllFilters(): void {
    this.hideOrange = false;
    this.fruitType = 'any';
  }

  protected cancel(): void {
    this.#instance.cancel();
  }
}

```

#### filters.ts

```typescript
export interface Filters {
  hideOrange?: boolean;
  type?: string;
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
  SkyDataManagerService,
  SkyDataManagerState,
  SkyDataViewConfig,
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
} from 'ag-grid-community';
import { Subject, of } from 'rxjs';
import { takeUntil } from 'rxjs/operators';

import { DataManagerDemoRow } from './data';
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
  public items: DataManagerDemoRow[] = [];

  protected displayedItems: DataManagerDemoRow[] = [];
  protected gridOptions: GridOptions;
  protected isActive = false;
  protected isGridInitialized = false;
  protected noRowsTemplate = `<div class="sky-font-deemphasized">No results found.</div>`;

  protected readonly viewId = 'gridView';

  #columnDefs: ColDef[] = [
    {
      colId: 'selected',
      field: 'selected',
      headerName: '',
      maxWidth: 50,
      type: SkyCellType.RowSelector,
      suppressMovable: true,
      lockPosition: true,
      lockVisible: true,
      cellRendererParams: {
        // Could be a SkyAppResourcesService.getString call that returns an observable.
        label: (data: DataManagerDemoRow) => of(`Select ${data.name}`),
      },
    },
    {
      colId: 'name',
      field: 'name',
      headerName: 'Fruit name',
      width: 150,
    },
    {
      colId: 'description',
      field: 'description',
      headerName: 'Description',
    },
  ];

  #dataState = new SkyDataManagerState({});
  #gridApi: GridApi | undefined;
  #ngUnsubscribe = new Subject<void>();

  #viewConfig: SkyDataViewConfig = {
    id: this.viewId,
    name: 'Grid View',
    iconName: 'table',
    searchEnabled: true,
    multiselectToolbarEnabled: true,
    columnPickerEnabled: true,
    filterButtonEnabled: true,
    columnOptions: [
      {
        id: 'selected',
        alwaysDisplayed: true,
        label: 'selected',
      },
      {
        id: 'name',
        label: 'Fruit name',
        description: 'The name of the fruit.',
      },
      {
        id: 'description',
        label: 'Description',
        description: 'Some information about the fruit.',
      },
    ],
  };

  readonly #agGridSvc = inject(SkyAgGridService);
  readonly #changeDetector = inject(ChangeDetectorRef);
  readonly #dataManagerSvc = inject(SkyDataManagerService);

  constructor() {
    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions: {
        columnDefs: this.#columnDefs,
        onGridReady: (args) => {
          this.#onGridReady(args);
        },
      },
    });
  }

  public ngOnInit(): void {
    this.displayedItems = this.items;

    this.#dataManagerSvc.initDataView(this.#viewConfig);

    this.#dataManagerSvc
      .getDataStateUpdates(this.viewId)
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((state) => {
        this.#dataState = state;
        this.#setInitialColumnOrder();
        this.#updateData();
        this.#changeDetector.markForCheck();
      });

    this.#dataManagerSvc
      .getActiveViewIdUpdates()
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((id) => {
        this.isActive = id === this.viewId;
        this.#changeDetector.markForCheck();
      });
  }

  public ngOnDestroy(): void {
    this.#ngUnsubscribe.next();
    this.#ngUnsubscribe.complete();
  }

  protected onRowSelected(
    rowSelectedEvent: RowSelectedEvent<DataManagerDemoRow>,
  ): void {
    if (!rowSelectedEvent.data?.selected) {
      this.#updateData();
    }
  }

  #filterItems(items: DataManagerDemoRow[]): DataManagerDemoRow[] {
    let filteredItems = items;

    const filterData = this.#dataState && this.#dataState.filterData;

    if (filterData?.filters) {
      const filters = filterData.filters as Filters;

      filteredItems = items.filter((item) => {
        return (
          ((filters.hideOrange && item.color !== 'orange') ??
            !filters.hideOrange) &&
          ((filters.type !== 'any' && item.type === filters.type) ||
            !filters.type ||
            filters.type === 'any')
        );
      });
    }

    return filteredItems;
  }

  #onGridReady(event: GridReadyEvent): void {
    this.#gridApi = event.api;
    this.#updateData();
  }

  #searchItems(items: DataManagerDemoRow[]): DataManagerDemoRow[] {
    let searchedItems = items;
    const searchText = this.#dataState && this.#dataState.searchText;

    if (searchText) {
      searchedItems = items.filter((item: DataManagerDemoRow) => {
        let property: keyof typeof item;

        for (property in item) {
          if (
            Object.prototype.hasOwnProperty.call(item, property) &&
            (property === 'name' || property === 'description')
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

  #setInitialColumnOrder(): void {
    const viewState = this.#dataState.getViewStateById(this.viewId);
    const visibleColumns = viewState?.displayedColumnIds ?? [];

    this.#columnDefs.sort((col1, col2) => {
      const col1Index = visibleColumns.findIndex(
        (colId: string) => colId === col1.colId,
      );
      const col2Index = visibleColumns.findIndex(
        (colId: string) => colId === col2.colId,
      );

      if (col1Index === -1) {
        col1.hide = true;
        return 0;
      } else if (col2Index === -1) {
        col2.hide = true;
        return 0;
      } else {
        return col1Index - col2Index;
      }
    });

    this.isGridInitialized = true;
  }

  #updateData(): void {
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
      this.viewId,
    );
  }
}

```

#### view-repeater.component.ts

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
import {
  SkyDataManagerModule,
  SkyDataManagerService,
  SkyDataManagerState,
  SkyDataViewConfig,
} from '@skyux/data-manager';
import { SkyRepeaterModule } from '@skyux/lists';

import { Subject } from 'rxjs';
import { takeUntil } from 'rxjs/operators';

import { DataManagerDemoRow } from './data';
import { Filters } from './filters';

@Component({
  selector: 'app-view-repeater',
  templateUrl: './view-repeater.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [SkyDataManagerModule, SkyRepeaterModule],
})
export class ViewRepeaterComponent implements OnInit, OnDestroy {
  @Input()
  public items: DataManagerDemoRow[] = [];

  protected displayedItems: DataManagerDemoRow[] = [];
  protected isActive = false;

  protected readonly viewId = 'repeaterView';

  #dataState = new SkyDataManagerState({});
  #ngUnsubscribe = new Subject<void>();

  #viewConfig: SkyDataViewConfig = {
    id: this.viewId,
    name: 'Repeater View',
    iconName: 'text-bullet-list',
    searchEnabled: true,
    sortEnabled: true,
    filterButtonEnabled: true,
    multiselectToolbarEnabled: true,
    onClearAllClick: () => {
      this.#clearAll();
    },
    onSelectAllClick: () => {
      this.#selectAll();
    },
  };

  readonly #changeDetector = inject(ChangeDetectorRef);
  readonly #dataManagerSvc = inject(SkyDataManagerService);

  public ngOnInit(): void {
    this.displayedItems = this.items;

    this.#dataManagerSvc.initDataView(this.#viewConfig);

    this.#dataManagerSvc
      .getDataStateUpdates(this.viewId)
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((state) => {
        this.#dataState = state;
        this.#updateData();
      });

    this.#dataManagerSvc
      .getActiveViewIdUpdates()
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((id) => {
        this.isActive = id === this.viewId;
        this.#changeDetector.markForCheck();
      });
  }

  public ngOnDestroy(): void {
    this.#ngUnsubscribe.next();
    this.#ngUnsubscribe.complete();
  }

  protected onItemSelect(isSelected: boolean, item: DataManagerDemoRow): void {
    const selectedItems = this.#dataState.selectedIds ?? [];
    const itemIndex = selectedItems.indexOf(item.id);

    if (isSelected && itemIndex === -1) {
      selectedItems.push(item.id);
    } else if (!isSelected && itemIndex !== -1) {
      selectedItems.splice(itemIndex, 1);
    }

    this.#dataState.selectedIds = selectedItems;
    this.#dataManagerSvc.updateDataState(this.#dataState, this.viewId);

    if (this.#dataState.onlyShowSelected && this.displayedItems) {
      this.displayedItems = this.displayedItems.filter((itm) => itm.selected);
      this.#changeDetector.markForCheck();
    }
  }

  #updateData(): void {
    const selectedIds = this.#dataState.selectedIds ?? [];

    this.items.forEach((item) => {
      item.selected = selectedIds.includes(item.id);
    });

    this.displayedItems = this.#filterItems(this.#searchItems(this.items));

    if (this.#dataState.onlyShowSelected) {
      this.displayedItems = this.displayedItems.filter((item) => item.selected);
    }

    this.#dataManagerSvc.updateDataSummary(
      {
        totalItems: this.items.length,
        itemsMatching: this.displayedItems.length,
      },
      this.viewId,
    );

    this.#changeDetector.markForCheck();
  }

  #searchItems(items: DataManagerDemoRow[]): DataManagerDemoRow[] {
    let searchedItems = items;
    const searchText =
      this.#dataState && this.#dataState.searchText?.toUpperCase();

    if (searchText) {
      searchedItems = items.filter((item: DataManagerDemoRow) => {
        let property: keyof typeof item;

        for (property in item) {
          if (
            Object.prototype.hasOwnProperty.call(item, property) &&
            (property === 'name' || property === 'description')
          ) {
            const propertyText = item[property].toUpperCase();
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

  #filterItems(items: DataManagerDemoRow[]): DataManagerDemoRow[] {
    let filteredItems = items;
    const filterData = this.#dataState && this.#dataState.filterData;

    if (filterData?.filters) {
      const filters = filterData.filters as Filters;

      filteredItems = items.filter((item: DataManagerDemoRow) => {
        if (
          ((filters.hideOrange && item.color !== 'orange') ??
            !filters.hideOrange) &&
          ((filters.type !== 'any' && item.type === filters.type) ||
            !filters.type ||
            filters.type === 'any')
        ) {
          return true;
        }

        return false;
      });
    }

    return filteredItems;
  }

  #selectAll(): void {
    const selectedIds = this.#dataState.selectedIds ?? [];

    this.displayedItems.forEach((item) => {
      if (!item.selected) {
        item.selected = true;
        selectedIds.push(item.id);
      }
    });

    this.#dataState.selectedIds = selectedIds;
    this.#dataManagerSvc.updateDataState(this.#dataState, this.viewId);
    this.#changeDetector.markForCheck();
  }

  #clearAll(): void {
    const selectedIds = this.#dataState.selectedIds ?? [];

    this.displayedItems.forEach((item) => {
      if (item.selected) {
        const itemIndex = selectedIds.indexOf(item.id);
        item.selected = false;
        selectedIds.splice(itemIndex, 1);
      }
    });

    if (this.#dataState.onlyShowSelected) {
      this.displayedItems = [];
    }

    this.#dataState.selectedIds = selectedIds;
    this.#dataManagerSvc.updateDataState(this.#dataState, this.viewId);
    this.#changeDetector.markForCheck();
  }
}

```

#### example.component.html

```html
<sky-data-manager>
  <sky-data-manager-toolbar />
  <app-view-repeater [items]="items" />
  <app-view-grid [items]="items" />
</sky-data-manager>

```

#### filter-modal.component.html

```html
<sky-modal headingText="Filter your fruit">
  <sky-modal-content>
    <sky-input-box labelText="Fruit type" stacked="true">
      <select class="sky-form-control" [(ngModel)]="fruitType">
        <option value="any">Any fruit</option>
        <option value="citrus">Citrus</option>
        <option value="berry">Berry</option>
      </select>
    </sky-input-box>
    <sky-checkbox labelText="Hide orange fruits" [(ngModel)]="hideOrange" />
  </sky-modal-content>
  <sky-modal-footer>
    <button
      class="sky-btn sky-btn-primary sky-margin-inline-sm"
      type="button"
      (click)="applyFilters()"
    >
      Apply filters
    </button>
    <button
      class="sky-btn sky-btn-default sky-margin-inline-sm"
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
<sky-data-view skyAgGridDataManagerAdapter [viewId]="viewId">
  @if (isActive && isGridInitialized) {
    <sky-ag-grid-wrapper>
      <ag-grid-angular
        [gridOptions]="gridOptions"
        [overlayNoRowsTemplate]="noRowsTemplate"
        [rowData]="displayedItems"
        (rowSelected)="onRowSelected($event)"
      />
    </sky-ag-grid-wrapper>
  }
</sky-data-view>

```

#### view-repeater.component.html

```html
<sky-data-view [viewId]="viewId">
  @if (isActive) {
    <sky-repeater expandMode="none">
      @for (item of displayedItems; track item.id) {
        <sky-repeater-item
          [selectable]="true"
          [(isSelected)]="item.selected"
          (isSelectedChange)="onItemSelect($event, item)"
        >
          <sky-repeater-item-title>
            {{ item.name }}
          </sky-repeater-item-title>
          <sky-repeater-item-content>
            {{ item.description }}
          </sky-repeater-item-content>
        </sky-repeater-item>
      }
    </sky-repeater>
  }
</sky-data-view>

```

---