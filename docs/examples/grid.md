---
component: 'grid'
type: 'code-examples'
description: 'Code examples for the grid component.'
---

# Grid Code Examples

## Basic setup (without data manager)

**Component:** AgGridDataEntryGridBasicExampleComponent

**Selector:** `app-ag-grid-data-entry-grid-basic-example`

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
  protected contextMenuAriaLabel = '';
  protected deleteAriaLabel = '';
  protected markInactiveAriaLabel = '';
  protected moreInfoAriaLabel = '';

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
    console.error(`${action} clicked for ${this.#name}`);
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
  OnInit,
  TemplateRef,
  ViewChild,
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
  NewValueParams,
} from 'ag-grid-community';

import { AgGridDemoRow, DEPARTMENTS, JOB_TITLES } from './data';
import { EditModalContext } from './edit-modal-context';
import { MarkInactiveComponent } from './mark-inactive.component';

ModuleRegistry.registerModules([AllCommunityModule]);

@Component({
  selector: 'app-edit-modal',
  templateUrl: './edit-modal.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [
    AgGridModule,
    SkyAgGridModule,
    SkyModalModule,
    MarkInactiveComponent,
  ],
})
export class EditModalComponent implements OnInit {
  @ViewChild('markInactiveAction', { static: true })
  protected markInactiveAction: TemplateRef<unknown> | undefined;

  protected gridData: AgGridDemoRow[];
  protected gridOptions: GridOptions | undefined;

  #gridApi: GridApi | undefined;

  protected readonly instance = inject(SkyModalInstance);
  readonly #agGridSvc = inject(SkyAgGridService);
  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #context = inject(EditModalContext);

  constructor() {
    this.gridData = this.#context.gridData;
  }

  public ngOnInit(): void {
    const columnDefs: ColDef[] = [
      {
        colId: 'markInactiveAction',
        headerName: 'Mark inactive',
        type: SkyCellType.Template,
        editable: true,
        cellRendererParams: {
          template: this.markInactiveAction,
        },
      },
      {
        field: 'name',
        headerName: 'Name',
        type: SkyCellType.Text,
        cellRendererParams: {
          skyComponentProperties: {
            validator: (value: string): boolean => String(value).length <= 10,
            validatorMessage: `Value exceeds maximum length`,
          },
        },
        cellEditorParams: {
          skyComponentProperties: {
            maxlength: 10,
          },
        },
        editable: true,
      },
      {
        field: 'age',
        headerName: 'Age',
        type: SkyCellType.Number,
        cellRendererParams: {
          skyComponentProperties: {
            validator: (value: number): boolean => value >= 18,
            validatorMessage: `Age must be 18+`,
          },
        },
        maxWidth: 60,
        cellEditorParams: {
          skyComponentProperties: {
            min: 18,
          },
        },
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
          return { skyComponentProperties: { minDate: params.data.startDate } };
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
              selectionChange: (
                change: SkyAutocompleteSelectionChange,
              ): void => {
                this.#departmentSelectionChange(change, params.node);
              },
            },
          };
        },
        onCellValueChanged: (event: NewValueParams): void => {
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
            validatorMessage: 'Please enter a future date',
          },
        },
        editable: true,
      },
    ];

    this.gridOptions = {
      columnDefs: columnDefs,
      onGridReady: (gridReadyEvent): void => {
        this.onGridReady(gridReadyEvent);
      },
    };

    this.gridOptions = this.#agGridSvc.getEditableGridOptions({
      gridOptions: this.gridOptions,
    });

    this.#changeDetectorRef.markForCheck();
  }

  public onGridReady(gridReadyEvent: GridReadyEvent): void {
    this.#gridApi = gridReadyEvent.api;

    this.#changeDetectorRef.markForCheck();
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
      this.#changeDetectorRef.markForCheck();

      if (this.#gridApi) {
        this.#gridApi.refreshCells({ rowNodes: [node] });
      }
    }
  }
}

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
import { SkyModalConfigurationInterface, SkyModalService } from '@skyux/modals';

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
import { EditModalContext } from './edit-modal-context';
import { EditModalComponent } from './edit-modal.component';

ModuleRegistry.registerModules([AllCommunityModule]);

/**
 * @title Basic setup (without data manager)
 */
@Component({
  selector: 'app-ag-grid-data-entry-grid-basic-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [AgGridModule, SkyAgGridModule, SkySearchModule, SkyToolbarModule],
})
export class AgGridDataEntryGridBasicExampleComponent {
  protected gridData = AG_GRID_DEMO_DATA;
  protected gridOptions: GridOptions;
  protected noRowsTemplate = `<div class="sky-font-deemphasized">No results found.</div>`;
  protected searchText = '';

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
      type: SkyCellType.Text,
      cellRendererParams: {
        skyComponentProperties: {
          validator: (value: string): boolean => String(value).length <= 10,
          validatorMessage: `Value exceeds maximum length`,
        },
      },
    },
    {
      field: 'age',
      headerName: 'Age',
      type: SkyCellType.Number,
      cellRendererParams: {
        skyComponentProperties: {
          validator: (value: number): boolean => value >= 18,
          validatorMessage: `Age must be 18+`,
        },
      },
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
      colId: 'validationCurrency',
      field: 'validationCurrency',
      headerName: 'Validation currency',
      type: [SkyCellType.CurrencyValidator],
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
          validatorMessage: 'Enter a future date',
        },
      },
    },
  ];

  #gridApi: GridApi | undefined;

  readonly #agGridSvc = inject(SkyAgGridService);
  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #modalSvc = inject(SkyModalService);

  constructor() {
    const gridOptions: GridOptions = {
      columnDefs: this.#columnDefs,
      onGridReady: (gridReadyEvent): void => {
        this.onGridReady(gridReadyEvent);
      },
    };

    this.gridOptions = this.#agGridSvc.getEditableGridOptions({
      gridOptions,
    });

    this.#changeDetectorRef.markForCheck();
  }

  public onGridReady(gridReadyEvent: GridReadyEvent): void {
    this.#gridApi = gridReadyEvent.api;
    this.#changeDetectorRef.markForCheck();
  }

  protected openModal(): void {
    const context = new EditModalContext();

    context.gridData = this.gridData;

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
        this.gridData = result.data as AgGridDemoRow[];

        if (this.#gridApi) {
          this.#gridApi.refreshCells();
        }

        alert('Saving data!');
      }
    });
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

#### mark-inactive.component.ts

```typescript
import { ChangeDetectionStrategy, Component, Input } from '@angular/core';

@Component({
  standalone: true,
  selector: 'app-mark-inactive',
  templateUrl: './mark-inactive.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class MarkInactiveComponent {
  @Input()
  public set name(value: string | undefined) {
    this.#_name = value;
    if (value) {
      this.markInactiveAriaLabel = `Mark ${value} inactive`;
    }
  }

  public get name(): string | undefined {
    return this.#_name;
  }

  protected markInactiveAriaLabel = '';

  #_name: string | undefined;

  protected markInactive(): void {
    console.error(`Mark inactive action clicked for ${this.name}`);
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
<ng-template #markInactiveAction let-value="value" let-row="row">
  <app-mark-inactive [name]="row?.name" />
</ng-template>

```

#### example.component.html

```html
<sky-toolbar>
  <sky-toolbar-item>
    <button class="sky-btn sky-btn-primary" type="button" (click)="openModal()">
      Edit
    </button>
  </sky-toolbar-item>
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

#### mark-inactive.component.html

```html
<button
  type="button"
  class="sky-btn sky-btn-link-inline"
  [attr.aria-label]="markInactiveAriaLabel"
  (click)="markInactive()"
>
  Mark inactive
</button>

```

---

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

## Setting initial focus for keyboard navigation

**Component:** AgGridDataEntryGridFocusExampleComponent

**Selector:** `app-ag-grid-data-entry-grid-focus-example`

**Import Path:** `@skyux/code-examples`

### Code Files

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
import { SkyInputBoxModule } from '@skyux/forms';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ModuleRegistry,
  ValueFormatterParams,
} from 'ag-grid-community';

import { AG_GRID_DEMO_DATA, AgGridDemoRow } from './data';

ModuleRegistry.registerModules([AllCommunityModule]);

/**
 * @title Setting initial focus for keyboard navigation
 */
@Component({
  selector: 'app-ag-grid-data-entry-grid-focus-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [AgGridModule, SkyAgGridModule, SkyInputBoxModule],
})
export class AgGridDataEntryGridFocusExampleComponent {
  protected gridData = AG_GRID_DEMO_DATA;
  protected gridOptions = inject(SkyAgGridService).getEditableGridOptions({
    gridOptions: {
      columnDefs: [
        {
          field: 'name',
          headerName: 'Name',
          type: SkyCellType.Text,
          editable: true,
          cellRendererParams: {
            skyComponentProperties: {
              validator: (value: string): boolean => String(value).length <= 10,
              validatorMessage: `Value exceeds maximum length`,
            },
          },
        },
        {
          field: 'age',
          headerName: 'Age',
          type: SkyCellType.Number,
          editable: true,
          cellRendererParams: {
            skyComponentProperties: {
              validator: (value: number): boolean => value >= 18,
              validatorMessage: `Age must be 18+`,
            },
          },
          maxWidth: 60,
        },
        {
          field: 'startDate',
          headerName: 'Start date',
          type: SkyCellType.Date,
          editable: true,
          sort: 'asc',
        },
        {
          field: 'endDate',
          headerName: 'End date',
          type: SkyCellType.Date,
          editable: true,
          valueFormatter: (
            params: ValueFormatterParams<AgGridDemoRow, Date>,
          ): string => this.#endDateFormatter(params),
        },
        {
          field: 'department',
          headerName: 'Department',
          type: SkyCellType.Autocomplete,
          editable: true,
        },
        {
          field: 'jobTitle',
          headerName: 'Title',
          type: SkyCellType.Autocomplete,
          editable: true,
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
          editable: true,
          cellRendererParams: {
            skyComponentProperties: {
              validator: (value: Date): boolean =>
                !!value && value > new Date(1985, 9, 26),
              validatorMessage: 'Enter a future date',
            },
          },
        },
      ],
      focusGridInnerElement: (params) => {
        params.api.startEditingCell({
          rowIndex: 0,
          colKey: 'name',
        });
        return true;
      },
    },
  });

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

#### example.component.html

```html
<sky-input-box
  labelText="Start here"
  helpPopoverContent="Then tab to the grid"
  stacked
>
  <input type="text" />
</sky-input-box>
<div class="sky-margin-stacked-md">
  <sky-ag-grid-wrapper>
    <ag-grid-angular
      class="sky-ag-grid-editable"
      [gridOptions]="gridOptions"
      [rowData]="gridData"
    />
  </sky-ag-grid-wrapper>
</div>
<sky-input-box
  labelText="Or start here"
  helpPopoverContent="Then tab backwards to the grid"
  stacked
>
  <input type="text" />
</sky-input-box>

```

---

## Basic setup with inline help (without data manager)

**Component:** AgGridDataEntryGridInlineHelpExampleComponent

**Selector:** `app-ag-grid-data-entry-grid-inline-help-example`

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
  readonly #agGridSvc = inject(SkyAgGridService);
  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #context = inject(EditModalContext);

  constructor() {
    this.#columnDefs = [
      {
        field: 'name',
        headerName: 'Name',
        type: SkyCellType.Text,
        cellRendererParams: {
          skyComponentProperties: {
            validator: (value: string): boolean => String(value).length <= 10,
            validatorMessage: `Value exceeds maximum length`,
          },
        },
        cellEditorParams: {
          skyComponentProperties: {
            maxlength: 10,
          },
        },
        editable: true,
      },
      {
        field: 'age',
        headerName: 'Age',
        type: SkyCellType.Number,
        cellRendererParams: {
          skyComponentProperties: {
            validator: (value: number): boolean => value >= 18,
            validatorMessage: `Age must be 18+`,
          },
        },
        maxWidth: 60,
        cellEditorParams: {
          skyComponentProperties: {
            min: 18,
          },
        },
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
          return { skyComponentProperties: { minDate: params.data.startDate } };
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
            validatorMessage: 'Please enter a future date',
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

    this.gridOptions = this.#agGridSvc.getEditableGridOptions({
      gridOptions,
    });

    this.#changeDetectorRef.markForCheck();
  }

  public onGridReady(gridReadyEvent: GridReadyEvent): void {
    this.#gridApi = gridReadyEvent.api;
    this.#changeDetectorRef.markForCheck();
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

      this.#changeDetectorRef.markForCheck();
      this.#gridApi?.refreshCells({ rowNodes: [node] });
    }
  }
}

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
import {
  SkyModalCloseArgs,
  SkyModalConfigurationInterface,
  SkyModalService,
} from '@skyux/modals';

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
import { EditModalContext } from './edit-modal-context';
import { EditModalComponent } from './edit-modal.component';
import { InlineHelpComponent } from './inline-help.component';

ModuleRegistry.registerModules([AllCommunityModule]);

/**
 * @title Basic setup with inline help (without data manager)
 */
@Component({
  selector: 'app-ag-grid-data-entry-grid-inline-help-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [AgGridModule, SkyAgGridModule, SkySearchModule, SkyToolbarModule],
})
export class AgGridDataEntryGridInlineHelpExampleComponent {
  protected gridData = AG_GRID_DEMO_DATA;
  protected gridOptions: GridOptions;
  protected noRowsTemplate = `<div class="sky-font-deemphasized">No results found.</div>`;
  protected searchText = '';

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
      type: SkyCellType.Text,
      cellRendererParams: {
        skyComponentProperties: {
          validator: (value: string): boolean => String(value).length <= 10,
          validatorMessage: `Value exceeds maximum length`,
        },
      },
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
    {
      field: 'age',
      headerName: 'Age',
      type: SkyCellType.Number,
      cellRendererParams: {
        skyComponentProperties: {
          validator: (value: number): boolean => value >= 18,
          validatorMessage: `Age must be 18+`,
        },
      },
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
    {
      colId: 'validationCurrency',
      field: 'validationCurrency',
      headerName: 'Validation currency',
      type: [SkyCellType.CurrencyValidator],
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
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
          validatorMessage: 'Enter a future date',
        },
      },
      headerComponentParams: {
        inlineHelpComponent: InlineHelpComponent,
      },
    },
  ];
  #gridApi: GridApi | undefined;

  readonly #agGridSvc = inject(SkyAgGridService);
  readonly #modalSvc = inject(SkyModalService);
  readonly #changeDetectorRef = inject(ChangeDetectorRef);

  constructor() {
    const gridOptions: GridOptions = {
      columnDefs: this.#columnDefs,
      onGridReady: (gridReadyEvent): void => {
        this.onGridReady(gridReadyEvent);
      },
    };

    this.gridOptions = this.#agGridSvc.getEditableGridOptions({
      gridOptions,
    });

    this.#changeDetectorRef.markForCheck();
  }

  public onGridReady(gridReadyEvent: GridReadyEvent): void {
    this.#gridApi = gridReadyEvent.api;
    this.#changeDetectorRef.markForCheck();
  }

  protected openModal(): void {
    const context = new EditModalContext();
    context.gridData = this.gridData;

    const options: SkyModalConfigurationInterface = {
      providers: [
        {
          provide: EditModalContext,
          useValue: context,
        },
      ],
      ariaDescribedBy: 'docs-edit-grid-modal-content',
      size: 'large',
    };

    const modalInstance = this.#modalSvc.open(EditModalComponent, options);

    modalInstance.closed.subscribe((result: SkyModalCloseArgs) => {
      if (result.reason === 'cancel' || result.reason === 'close') {
        alert('Edits canceled!');
      } else {
        this.gridData = result.data as AgGridDemoRow[];
        this.#gridApi?.refreshCells();

        alert('Saving data!');
      }
    });
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
<sky-toolbar>
  <sky-toolbar-item>
    <button class="sky-btn sky-btn-primary" type="button" (click)="openModal()">
      Edit
    </button>
  </sky-toolbar-item>
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
  class="sky-control-help"
  [ariaLabel]="'Information about ' + displayName"
  (actionClick)="onHelpClick()"
/>

```

---

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

## Fluid grid with basic setup

**Component:** LayoutFluidGridExampleComponent

**Selector:** `app-layout-fluid-grid-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import {
  SkyColumnHarness,
  SkyFluidGridHarness,
  SkyRowHarness,
} from '@skyux/layout/testing';

import { LayoutFluidGridExampleComponent } from './example.component';

describe('Basic fluid grid', () => {
  async function setupTest(): Promise<{
    fluidGridHarness: SkyFluidGridHarness;
    fixture: ComponentFixture<LayoutFluidGridExampleComponent>;
    loader: HarnessLoader;
  }> {
    const fixture = TestBed.createComponent(LayoutFluidGridExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const fluidGridHarness = await loader.getHarness(
      SkyFluidGridHarness.with({
        dataSkyId: 'fluid-grid',
      }),
    );

    return { fluidGridHarness, fixture, loader };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [LayoutFluidGridExampleComponent],
    });
  });

  it('should display the correct fluid grid', async () => {
    const { fluidGridHarness, fixture } = await setupTest();

    fixture.detectChanges();

    const rows = await fluidGridHarness.getRows();

    expect(rows.length).toEqual(12);
  });

  it('should indicate the grid has margins', async () => {
    const { fluidGridHarness, fixture } = await setupTest();

    fixture.detectChanges();

    await expectAsync(fluidGridHarness.hasMargin()).toBeResolvedTo(true);

    fixture.componentInstance.disableMargin = true;
    fixture.detectChanges();

    await expectAsync(fluidGridHarness.hasMargin()).toBeResolvedTo(false);
  });

  it('should get the gutter size', async () => {
    const { fluidGridHarness, fixture } = await setupTest();

    fixture.detectChanges();

    await expectAsync(fluidGridHarness.getGutterSize()).toBeResolvedTo('large');

    fixture.componentInstance.gutterSize = 'medium';
    fixture.detectChanges();

    await expectAsync(fluidGridHarness.getGutterSize()).toBeResolvedTo(
      'medium',
    );

    fixture.componentInstance.gutterSize = 'small';
    fixture.detectChanges();

    await expectAsync(fluidGridHarness.getGutterSize()).toBeResolvedTo('small');
  });

  it('should get the correct row harness', async () => {
    const { fixture, loader } = await setupTest();
    const rowHarness = await loader.getHarness(
      SkyRowHarness.with({ dataSkyId: 'test-row' }),
    );

    fixture.detectChanges();

    const columns = await rowHarness.getColumns();

    expect(columns.length).toEqual(12);
    await expectAsync(rowHarness.getColumnOrder()).toBeResolvedTo('normal');
  });

  it('should get the row direction from the row harness', async () => {
    const { fixture, loader } = await setupTest();
    const rowHarness = await loader.getHarness(
      SkyRowHarness.with({ dataSkyId: 'reverse-row' }),
    );

    fixture.detectChanges();

    await expectAsync(rowHarness.getColumnOrder()).toBeResolvedTo('reverse');
  });

  it('should get the correct column harness', async () => {
    const { fixture, loader } = await setupTest();
    const columnHarness = await loader.getHarness(
      SkyColumnHarness.with({ dataSkyId: 'test-column' }),
    );

    fixture.detectChanges();

    await expectAsync(columnHarness.getXSmallSize()).toBeResolvedTo(12);
    await expectAsync(columnHarness.getLargeSize()).toBeResolvedTo(1);
  });

  it('should get the column sizes from the column harness', async () => {
    const { fixture, loader } = await setupTest();
    const columnHarness = await loader.getHarness(
      SkyColumnHarness.with({ dataSkyId: 'dynamic-column' }),
    );

    fixture.detectChanges();

    await expectAsync(columnHarness.getXSmallSize()).toBeResolvedTo(6);
    await expectAsync(columnHarness.getSmallSize()).toBeResolvedTo(8);
    await expectAsync(columnHarness.getMediumSize()).toBeResolvedTo(9);
    await expectAsync(columnHarness.getLargeSize()).toBeResolvedTo(10);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyFluidGridGutterSizeType, SkyFluidGridModule } from '@skyux/layout';

/**
 * @title Fluid grid with basic setup
 */
@Component({
  selector: 'app-layout-fluid-grid-example',
  templateUrl: './example.component.html',
  styles: [
    `
      .highlight-columns .sky-column {
        background-color: #97eced;
        border: 1px solid #56e0e1;
        overflow-wrap: break-word;
      }
    `,
  ],
  imports: [SkyFluidGridModule],
})
export class LayoutFluidGridExampleComponent {
  public gutterSize: SkyFluidGridGutterSizeType | undefined;
  public disableMargin = false;
}

```

#### example.component.html

```html
<div class="highlight-columns">
  <sky-fluid-grid
    data-sky-id="fluid-grid"
    [disableMargin]="disableMargin"
    [gutterSize]="gutterSize"
  >
    <sky-row data-sky-id="test-row">
      <sky-column data-sky-id="test-column" [screenSmall]="1">
        [screenSmall]="1"
      </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="3"> [screenSmall]="3" </sky-column>
      <sky-column [screenSmall]="3"> [screenSmall]="3" </sky-column>
      <sky-column [screenSmall]="3"> [screenSmall]="3" </sky-column>
      <sky-column [screenSmall]="3"> [screenSmall]="3" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="4"> [screenSmall]="4" </sky-column>
      <sky-column [screenSmall]="4"> [screenSmall]="4" </sky-column>
      <sky-column [screenSmall]="4"> [screenSmall]="4" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="5"> [screenSmall]="5" </sky-column>
      <sky-column [screenSmall]="7"> [screenSmall]="7" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="6"> [screenSmall]="6" </sky-column>
      <sky-column [screenSmall]="6"> [screenSmall]="6" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="8"> [screenSmall]="8" </sky-column>
      <sky-column [screenSmall]="4"> [screenSmall]="4" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="9"> [screenSmall]="9" </sky-column>
      <sky-column [screenSmall]="3"> [screenSmall]="3" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="10"> [screenSmall]="10" </sky-column>
      <sky-column [screenSmall]="2"> [screenSmall]="2" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column [screenSmall]="11"> [screenSmall]="11" </sky-column>
      <sky-column [screenSmall]="1"> [screenSmall]="1" </sky-column>
    </sky-row>

    <sky-row>
      <sky-column
        data-sky-id="dynamic-column"
        [screenXSmall]="6"
        [screenSmall]="8"
        [screenMedium]="9"
        [screenLarge]="10"
      >
        [screenXSmall]="6" [screenSmall]="8" [screenMedium]="9"
        [screenLarge]="10"
      </sky-column>
      <sky-column
        [screenXSmall]="6"
        [screenSmall]="4"
        [screenMedium]="3"
        [screenLarge]="2"
      >
        [screenXSmall]="6" [screenSmall]="4" [screenMedium]="3"
        [screenLarge]="2"
      </sky-column>
    </sky-row>

    <sky-row data-sky-id="reverse-row" [reverseColumnOrder]="true">
      <sky-column [screenSmall]="4"> First column </sky-column>
      <sky-column [screenSmall]="4"> Second column </sky-column>
      <sky-column [screenSmall]="4"> Third column </sky-column>
    </sky-row>
  </sky-fluid-grid>
</div>

```

---