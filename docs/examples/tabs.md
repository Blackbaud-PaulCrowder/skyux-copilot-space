---
component: 'tabs'
type: 'code-examples'
description: 'Code examples for the tabs component.'
---

# Tabs Code Examples

## List page with tabs layout using data manager

**Component:** PagesPageListPageTabsLayoutExampleComponent

**Selector:** `app-pages-page-list-page-tabs-layout-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### contact-context-menu.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyDropdownModule } from '@skyux/popovers';

import { ICellRendererAngularComp } from 'ag-grid-angular';
import { ICellRendererParams } from 'ag-grid-community';

import { Contact } from './contact';

@Component({
  selector: 'app-contacts-grid-context-menu',
  templateUrl: './contact-context-menu.component.html',
  imports: [SkyDropdownModule],
})
export class ContactContextMenuComponent implements ICellRendererAngularComp {
  protected contactName = '';

  public agInit(params: ICellRendererParams<Contact>): void {
    this.contactName = params.data?.name ?? '';
  }

  public refresh(): boolean {
    return false;
  }
}

```

#### contact.ts

```typescript
export interface Contact {
  name: string;
  organization: string;
  emailAddress: string;
}

```

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { provideRouter } from '@angular/router';
import {
  SkyHelpTestingController,
  SkyHelpTestingModule,
} from '@skyux/core/testing';
import { SkyPageHarness } from '@skyux/pages/testing';

import { PagesPageListPageTabsLayoutExampleComponent } from './example.component';

describe('List page tabs layout example', () => {
  async function setupTest(): Promise<{
    pageHarness: SkyPageHarness;
    fixture: ComponentFixture<PagesPageListPageTabsLayoutExampleComponent>;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(
      PagesPageListPageTabsLayoutExampleComponent,
    );

    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const pageHarness = await loader.getHarness(SkyPageHarness);
    const helpController = TestBed.inject(SkyHelpTestingController);

    return { pageHarness, fixture, helpController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        PagesPageListPageTabsLayoutExampleComponent,
        SkyHelpTestingModule,
        NoopAnimationsModule,
      ],
      providers: [provideRouter([])],
    });
  });

  it('should have a tabs layout', async () => {
    const { pageHarness } = await setupTest();

    await expectAsync(pageHarness.getLayout()).toBeResolvedTo('tabs');
  });

  it('should have the correct page header text', async () => {
    const { pageHarness } = await setupTest();

    const pageHeaderHarness = await pageHarness.getPageHeader();

    await expectAsync(pageHeaderHarness.getPageTitle()).toBeResolvedTo(
      'Contacts',
    );
  });

  it('should have the correct help key', async () => {
    const { helpController } = await setupTest();

    helpController.expectCurrentHelpKey('example-help');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyPageModule } from '@skyux/pages';

import { ListPageContentComponent } from './list-page-content.component';

/**
 * @title List page with tabs layout using data manager
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-page-list-page-tabs-layout-example',
  templateUrl: './example.component.html',
  imports: [ListPageContentComponent, SkyPageModule],
})
export class PagesPageListPageTabsLayoutExampleComponent {}

```

#### list-page-contacts-grid.component.ts

```typescript
import { Component, Input, OnInit, inject } from '@angular/core';
import { SkyAgGridModule, SkyAgGridService } from '@skyux/ag-grid';
import {
  SkyDataManagerModule,
  SkyDataManagerService,
  SkyDataManagerState,
  SkyDataViewConfig,
} from '@skyux/data-manager';
import { SkyIconModule } from '@skyux/icon';
import { SkyKeyInfoModule } from '@skyux/indicators';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ColDef,
  GridOptions,
  ICellRendererParams,
  ModuleRegistry,
} from 'ag-grid-community';

import { ContactContextMenuComponent } from './contact-context-menu.component';

ModuleRegistry.registerModules([AllCommunityModule]);

interface Contact {
  name: string;
  organization: string;
  emailAddress: string;
}

@Component({
  selector: 'app-list-page-contacts-grid',
  templateUrl: './list-page-contacts-grid.component.html',
  providers: [SkyDataManagerService],
  imports: [
    AgGridModule,
    SkyAgGridModule,
    SkyDataManagerModule,
    SkyIconModule,
    SkyKeyInfoModule,
  ],
})
export class ListPageContactsGridComponent implements OnInit {
  @Input()
  public contacts: Contact[] = [];

  protected gridOptions: GridOptions;

  #dataManagerService = inject(SkyDataManagerService);
  #agGridSvc = inject(SkyAgGridService);

  #columnDefs: ColDef[] = [
    {
      colId: 'contextMenu',
      headerName: '',
      sortable: false,
      cellRenderer: ContactContextMenuComponent,
      maxWidth: 55,
    },
    {
      colId: 'name',
      field: 'name',
      headerName: 'Name',
      width: 150,
      cellRenderer: (params: ICellRendererParams): string => {
        return `<a href="/">${params.value}</a>`;
      },
    },
    {
      colId: 'organization',
      field: 'organization',
      headerName: 'Organization',
    },
    {
      colId: 'emailAddress',
      field: 'emailAddress',
      headerName: 'Email Address',
    },
  ];

  #viewConfig: SkyDataViewConfig = {
    id: 'gridView',
    name: 'Grid View',
    searchEnabled: true,
    columnPickerEnabled: true,
    columnOptions: [
      { id: 'contextMenu', label: 'Context menu', alwaysDisplayed: true },
      { id: 'name', label: 'Name' },
      { id: 'organization', label: 'Organization' },
      { id: 'emailAddress', label: 'Email Address' },
    ],
  };

  constructor() {
    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions: {
        columnDefs: this.#columnDefs,
      },
    });
  }

  public ngOnInit(): void {
    this.#dataManagerService.initDataManager({
      activeViewId: 'gridView',
      dataManagerConfig: {},
      defaultDataState: new SkyDataManagerState({
        views: [
          {
            viewId: 'gridView',
            displayedColumnIds: [
              'contextMenu',
              'name',
              'organization',
              'emailAddress',
            ],
          },
        ],
      }),
    });

    this.#dataManagerService.initDataView(this.#viewConfig);
  }
}

```

#### list-page-content.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyTabIndex, SkyTabsModule } from '@skyux/tabs';

import { Contact } from './contact';
import { ListPageContactsGridComponent } from './list-page-contacts-grid.component';

@Component({
  selector: 'app-list-page-content',
  templateUrl: './list-page-content.component.html',
  imports: [ListPageContactsGridComponent, SkyTabsModule],
})
export class ListPageContentComponent {
  protected activeTabIndex: SkyTabIndex = 0;

  protected myContacts: Contact[] = [
    {
      name: 'Wonda Lumpkin',
      organization: 'Riverfront College of the Arts',
      emailAddress: 'wlumpkin@yahoo.com',
    },
    {
      name: 'Eliza Vanhorn',
      organization: 'Summit School of the Arts',
      emailAddress: 'evanhorn@outlook.com',
    },
    {
      name: 'Ed Sipes',
      organization: 'Reflections Middle School',
      emailAddress: 'esipes@yahoo.com',
    },
    {
      name: 'Elwood Farris',
      organization: 'Sandy Lagoon College',
      emailAddress: 'elfarris@gmail.com',
    },
    {
      name: 'Cristen Sizemore',
      organization: 'Grafton Vision Health',
      emailAddress: 'cristen.sizemore@aol.com',
    },
    {
      name: 'Latrice Ashmore',
      organization: 'Food Bank of Rapid City',
      emailAddress: 'lashmore@gmail.com',
    },
  ];

  protected allContacts = [
    ...this.myContacts,
    {
      name: 'Kanesha Hutto',
      organization: 'Los Angeles College of the Arts',
      emailAddress: 'khutto@yahoo.com',
    },
    {
      name: 'Kristeen Lunsford',
      organization: 'Food Bank of Los Angeles',
      emailAddress: 'kristeen.lunsford@yahoo.com',
    },
    {
      name: 'Barbara Durr',
      organization: 'Riverfront Middle School',
      emailAddress: 'bdurr@gmail.com',
    },
    {
      name: 'Ilene Woo',
      organization: 'Rapid City High School',
      emailAddress: 'ilene.woo@aol.com',
    },
    {
      name: 'Darcel Lenz',
      organization: 'Riverfront College of the Arts',
      emailAddress: 'dlenz@yahoo.com',
    },
  ];
}

```

#### contact-context-menu.component.html

```html
<sky-dropdown
  buttonType="context-menu"
  [label]="'context menu for ' + contactName"
>
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Edit ' + contactName">
        Edit
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Delete ' + contactName">
        Delete
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

#### example.component.html

```html
<sky-page layout="tabs" helpKey="example-help">
  <sky-page-header pageTitle="Contacts" />
  <sky-page-content>
    <app-list-page-content />
  </sky-page-content>
</sky-page>

```

#### list-page-contacts-grid.component.html

```html
<sky-data-manager>
  <div class="sky-margin-stacked-xs">
    <sky-data-manager-toolbar>
      <sky-data-manager-toolbar-primary-item>
        <button
          aria-label="New contact"
          class="sky-btn sky-btn-default"
          type="button"
        >
          <sky-icon iconName="add" />
          New
        </button>
      </sky-data-manager-toolbar-primary-item>
    </sky-data-manager-toolbar>
  </div>
  <div class="sky-margin-stacked-sm">
    <sky-key-info layout="horizontal" class="sky-padding-horizontal-sm">
      <sky-key-info-value class="sky-font-display-4">
        {{ contacts.length }}
      </sky-key-info-value>
      <sky-key-info-label> Contacts </sky-key-info-label>
    </sky-key-info>
  </div>
  <sky-data-view skyAgGridDataManagerAdapter viewId="gridView">
    <sky-ag-grid-wrapper>
      <ag-grid-angular [gridOptions]="gridOptions" [rowData]="contacts" />
    </sky-ag-grid-wrapper>
  </sky-data-view>
</sky-data-manager>

```

#### list-page-content.component.html

```html
<sky-tabset [(active)]="activeTabIndex">
  <sky-tab tabHeading="My contacts" layout="list">
    @if (activeTabIndex === 0) {
      <app-list-page-contacts-grid [contacts]="myContacts" />
    }
  </sky-tab>
  <sky-tab tabHeading="All contacts" layout="list">
    @if (activeTabIndex === 1) {
      <app-list-page-contacts-grid [contacts]="allContacts" />
    }
  </sky-tab>
</sky-tabset>

```

---

## Record page with tabs layout using data manager

**Component:** PagesPageRecordPageTabsLayoutExampleComponent

**Selector:** `app-pages-page-record-page-tabs-layout-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### attachment.ts

```typescript
export interface Attachment {
  name: string;
  description: string;
  size: string;
  dateAdded: string;
}

```

#### attachments-grid-context-menu.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyDropdownModule } from '@skyux/popovers';

import { ICellRendererAngularComp } from 'ag-grid-angular';
import { ICellRendererParams } from 'ag-grid-community';

import { Attachment } from './attachment';

@Component({
  selector: 'app-attachments-grid-context-menu',
  templateUrl: './attachments-grid-context-menu.component.html',
  imports: [SkyDropdownModule],
})
export class AttachmentsGridContextMenuComponent
  implements ICellRendererAngularComp
{
  protected attachmentName = '';

  public agInit(params: ICellRendererParams<Attachment>): void {
    this.attachmentName = params.data?.name ?? '';
  }

  public refresh(): boolean {
    return false;
  }
}

```

#### detail.ts

```typescript
export interface Detail {
  detail: string;
  info: string;
}

```

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { provideRouter } from '@angular/router';
import {
  SkyHelpTestingController,
  SkyHelpTestingModule,
} from '@skyux/core/testing';
import { SkyPageHarness } from '@skyux/pages/testing';

import { PagesPageRecordPageTabsLayoutExampleComponent } from './example.component';

describe('Record page tabs layout example', () => {
  async function setupTest(): Promise<{
    pageHarness: SkyPageHarness;
    fixture: ComponentFixture<PagesPageRecordPageTabsLayoutExampleComponent>;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(
      PagesPageRecordPageTabsLayoutExampleComponent,
    );

    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const pageHarness = await loader.getHarness(SkyPageHarness);
    const helpController = TestBed.inject(SkyHelpTestingController);

    return { pageHarness, fixture, helpController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        PagesPageRecordPageTabsLayoutExampleComponent,
        SkyHelpTestingModule,
        NoopAnimationsModule,
      ],
      providers: [provideRouter([])],
    });
  });

  it('should have a tabs layout', async () => {
    const { pageHarness, fixture } = await setupTest();

    fixture.detectChanges();

    await expectAsync(pageHarness.getLayout()).toBeResolvedTo('tabs');
  });

  it('should have the correct page header text', async () => {
    const { pageHarness } = await setupTest();

    const pageHeaderHarness = await pageHarness.getPageHeader();

    await expectAsync(pageHeaderHarness.getPageTitle()).toBeResolvedTo(
      'Charlene Conners',
    );
  });

  it('should have the correct help key', async () => {
    const { helpController } = await setupTest();

    helpController.expectCurrentHelpKey('example-help');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyAvatarModule } from '@skyux/avatar';
import { SkyAlertModule, SkyLabelModule } from '@skyux/indicators';
import { SkyPageModule } from '@skyux/pages';

import { RecordPageContentComponent } from './record-page-content.component';

/**
 * @title Record page with tabs layout using data manager
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-page-record-page-tabs-layout-example',
  templateUrl: './example.component.html',
  imports: [
    RecordPageContentComponent,
    SkyAlertModule,
    SkyAvatarModule,
    SkyLabelModule,
    SkyPageModule,
  ],
})
export class PagesPageRecordPageTabsLayoutExampleComponent {}

```

#### record-page-attachments-tab.component.ts

```typescript
import { Component, OnInit, inject } from '@angular/core';
import { SkyAgGridModule, SkyAgGridService } from '@skyux/ag-grid';
import {
  SkyDataManagerModule,
  SkyDataManagerService,
  SkyDataManagerState,
  SkyDataViewConfig,
} from '@skyux/data-manager';
import { SkyIconModule } from '@skyux/icon';
import { SkyKeyInfoModule } from '@skyux/indicators';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ColDef,
  GridOptions,
  ICellRendererParams,
  ModuleRegistry,
} from 'ag-grid-community';

import { Attachment } from './attachment';
import { AttachmentsGridContextMenuComponent } from './attachments-grid-context-menu.component';

ModuleRegistry.registerModules([AllCommunityModule]);

@Component({
  selector: 'app-record-page-attachments-tab',
  templateUrl: './record-page-attachments-tab.component.html',
  providers: [SkyDataManagerService],
  imports: [
    AgGridModule,
    SkyAgGridModule,
    SkyDataManagerModule,
    SkyKeyInfoModule,
    SkyIconModule,
  ],
})
export class RecordPageAttachmentsTabComponent implements OnInit {
  protected items: Attachment[] = [
    {
      name: 'Agreement.pdf',
      description: 'Cardholder agreement',
      size: '10 KB',
      dateAdded: '01/28/2023',
    },
    {
      name: 'Appendix.pdf',
      description: 'Updated terms 2023',
      size: '25 KB',
      dateAdded: '05/05/2023',
    },
  ];
  protected gridOptions: GridOptions;

  #dataManagerService = inject(SkyDataManagerService);
  #agGridSvc = inject(SkyAgGridService);

  #columnDefs: ColDef[] = [
    {
      colId: 'contextMenu',
      headerName: '',
      sortable: false,
      cellRenderer: AttachmentsGridContextMenuComponent,
      maxWidth: 55,
    },
    {
      colId: 'name',
      field: 'name',
      headerName: 'Name',
      width: 150,
      cellRenderer: (params: ICellRendererParams): string => {
        return `<a href="/">${params.value}</a>`;
      },
    },
    {
      colId: 'description',
      field: 'description',
      headerName: 'Description',
    },
    {
      colId: 'size',
      field: 'size',
      headerName: 'Size',
    },
    {
      colId: 'dateAdded',
      field: 'dateAdded',
      headerName: 'Date Added',
    },
  ];

  #viewConfig: SkyDataViewConfig = {
    id: 'gridView',
    name: 'Grid View',
    searchEnabled: true,
  };

  constructor() {
    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions: {
        columnDefs: this.#columnDefs,
      },
    });
  }

  public ngOnInit(): void {
    this.#dataManagerService.initDataManager({
      activeViewId: 'gridView',
      dataManagerConfig: {},
      defaultDataState: new SkyDataManagerState({
        views: [
          {
            viewId: 'gridView',
            displayedColumnIds: [
              'contextMenu',
              'name',
              'description',
              'size',
              'dateAdded',
            ],
          },
        ],
      }),
    });

    this.#dataManagerService.initDataView(this.#viewConfig);
  }
}

```

#### record-page-content.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyTabIndex, SkyTabsModule } from '@skyux/tabs';

import { RecordPageAttachmentsTabComponent } from './record-page-attachments-tab.component';
import { RecordPageNotesTabComponent } from './record-page-notes-tab.component';
import { RecordPageOverviewTabComponent } from './record-page-overview-tab.component';

@Component({
  selector: 'app-record-page-content',
  templateUrl: './record-page-content.component.html',
  imports: [
    RecordPageAttachmentsTabComponent,
    RecordPageNotesTabComponent,
    RecordPageOverviewTabComponent,
    SkyTabsModule,
  ],
})
export class RecordPageContentComponent {
  protected activeTabIndex: SkyTabIndex = 0;
}

```

#### record-page-notes-tab.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyIconModule } from '@skyux/icon';
import { SkyKeyInfoModule } from '@skyux/indicators';
import { SkyToolbarModule } from '@skyux/layout';
import { SkyRepeaterModule, SkySortModule } from '@skyux/lists';
import { SkySearchModule } from '@skyux/lookup';
import { SkyDropdownModule } from '@skyux/popovers';

@Component({
  selector: 'app-record-page-notes-tab',
  templateUrl: './record-page-notes-tab.component.html',
  imports: [
    SkyDropdownModule,
    SkyIconModule,
    SkyKeyInfoModule,
    SkyRepeaterModule,
    SkySearchModule,
    SkySortModule,
    SkyToolbarModule,
  ],
})
export class RecordPageNotesTabComponent {
  protected notes = [
    {
      noteNumber: 1,
      content: 'Attended our gala last year and had a great time.',
      date: '11/17/2024',
    },
    {
      noteNumber: 2,
      content:
        'Is a business owner and has a lot of connections in the community.',
      date: '10/11/2024',
    },
  ];
}

```

#### record-page-overview-tab.component.ts

```typescript
import { CommonModule } from '@angular/common';
import { Component } from '@angular/core';
import { SkyIconModule } from '@skyux/icon';
import { SkyKeyInfoModule } from '@skyux/indicators';
import {
  SkyBoxModule,
  SkyDescriptionListModule,
  SkyFluidGridModule,
} from '@skyux/layout';
import { SkyRepeaterModule } from '@skyux/lists';

import { Detail } from './detail';

@Component({
  selector: 'app-record-page-overview-tab',
  templateUrl: './record-page-overview-tab.component.html',
  styleUrls: ['./record-page-overview-tab.component.scss'],
  imports: [
    CommonModule,
    SkyBoxModule,
    SkyDescriptionListModule,
    SkyFluidGridModule,
    SkyIconModule,
    SkyKeyInfoModule,
    SkyRepeaterModule,
  ],
})
export class RecordPageOverviewTabComponent {
  protected recordDetails: Detail[] = [
    {
      detail: 'Designation',
      info: 'General operating',
    },
    {
      detail: 'Source',
      info: 'Online donation form',
    },
    {
      detail: 'Status',
      info: 'Active',
    },
    {
      detail: 'Due date',
      info: '12/12/2023',
    },
    {
      detail: 'Create date',
      info: '01/05/2023',
    },
    {
      detail: 'Frequency',
      info: 'Quarterly',
    },
  ];

  protected actualPayments = [
    {
      category: 'Amount',
      value: '$845.00',
    },
    {
      category: 'Assigned',
      value: '$800.00',
    },
    {
      category: 'Applied',
      value: '$800.00',
    },
    {
      category: 'Payments',
      value: 25,
    },
  ];

  protected projectedPayments = [
    {
      category: 'Amount',
      value: '$0',
    },
    {
      category: 'Line items',
      value: 0,
    },
  ];

  protected recentActivity = [
    {
      activity: '$250.00 payment processed successfully.',
      date: '07/01/2023 12:02 am',
    },
    {
      activity: '$150.00 payment processed successfully.',
      date: '06/15/2023 12:02 am',
    },
    {
      activity: '$250.00 payment processed successfully.',
      date: '04/01/2023 12:02 am',
    },
  ];
}

```

#### attachments-grid-context-menu.component.html

```html
<sky-dropdown
  buttonType="context-menu"
  [label]="'context menu for ' + attachmentName"
>
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Edit ' + attachmentName">
        Edit
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Delete ' + attachmentName">
        Delete
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

#### example.component.html

```html
<sky-page layout="tabs" helpKey="example-help">
  <sky-page-header pageTitle="Charlene Conners">
    <sky-page-header-alerts>
      <sky-alert alertType="warning" descriptionType="warning">
        Missing phone number for Charlene Conners.
      </sky-alert>
    </sky-page-header-alerts>
    <sky-page-header-avatar>
      <sky-avatar name="Charlene Conners" />
    </sky-page-header-avatar>
    <sky-page-header-details>
      <sky-label labelType="info" descriptionType="important-info">
        VIP
      </sky-label>
    </sky-page-header-details>
    <sky-page-header-actions>
      <button class="sky-btn sky-btn-default" type="button">
        Email contact
      </button>
      <button class="sky-btn sky-btn-default" type="button">
        Add to my contacts
      </button>
    </sky-page-header-actions>
  </sky-page-header>
  <sky-page-content>
    <app-record-page-content />
  </sky-page-content>
</sky-page>

```

#### record-page-attachments-tab.component.html

```html
<sky-data-manager>
  <div class="sky-margin-stacked-xs">
    <sky-data-manager-toolbar>
      <sky-data-manager-toolbar-primary-item>
        <button
          aria-label="New attachment"
          class="sky-btn sky-btn-default"
          type="button"
        >
          <sky-icon iconName="add" />
          New
        </button>
      </sky-data-manager-toolbar-primary-item>
    </sky-data-manager-toolbar>
  </div>
  <div class="sky-margin-stacked-sm">
    <sky-key-info layout="horizontal" class="sky-padding-horizontal-sm">
      <sky-key-info-value class="sky-font-display-4">
        {{ items.length }}
      </sky-key-info-value>
      <sky-key-info-label> Attachments </sky-key-info-label>
    </sky-key-info>
  </div>
  <sky-data-view skyAgGridDataManagerAdapter viewId="gridView">
    <sky-ag-grid-wrapper>
      <ag-grid-angular [gridOptions]="gridOptions" [rowData]="items" />
    </sky-ag-grid-wrapper>
  </sky-data-view>
</sky-data-manager>

```

#### record-page-content.component.html

```html
<sky-tabset [(active)]="activeTabIndex">
  <sky-tab tabHeading="Overview" layout="blocks">
    <app-record-page-overview-tab />
  </sky-tab>
  <sky-tab tabHeading="Notes" layout="list">
    <app-record-page-notes-tab />
  </sky-tab>
  <sky-tab tabHeading="Attachments" layout="list">
    @if (activeTabIndex === 2) {
      <app-record-page-attachments-tab />
    }
  </sky-tab>
</sky-tabset>

```

#### record-page-notes-tab.component.html

```html
<div class="sky-margin-stacked-xs">
  <sky-toolbar>
    <sky-toolbar-item>
      <button
        class="sky-btn sky-btn-default"
        type="button"
        aria-label="New note"
      >
        <sky-icon iconName="add" />
        New
      </button>
    </sky-toolbar-item>
    <sky-toolbar-item>
      <sky-sort [showButtonText]="true">
        <sky-sort-item>
          <span aria-label="Sort notes by date created (newest first)">
            Date created (newest first)
          </span>
        </sky-sort-item>
        <sky-sort-item>
          <span aria-label="Sort notes by date created (oldest first)">
            Date created (oldest first)
          </span>
        </sky-sort-item>
      </sky-sort>
    </sky-toolbar-item>
    <sky-toolbar-item>
      <button
        class="sky-btn sky-btn-default"
        type="button"
        aria-label="Export notes"
      >
        <sky-icon iconName="document-xls" />
        Export
      </button>
    </sky-toolbar-item>
    <sky-toolbar-item>
      <sky-search placeholderText="Find in notes" />
    </sky-toolbar-item>
  </sky-toolbar>
</div>
<div class="sky-margin-stacked-sm">
  <sky-key-info layout="horizontal">
    <sky-key-info-value class="sky-font-display-4">
      {{ notes.length }}
    </sky-key-info-value>
    <sky-key-info-label> Notes </sky-key-info-label>
  </sky-key-info>
</div>
<sky-repeater>
  @for (note of notes; track note.noteNumber) {
    <sky-repeater-item>
      <sky-repeater-item-context-menu>
        <sky-dropdown
          buttonType="context-menu"
          [label]="
            'Context menu for note ' + note.noteNumber + ' from ' + note.date
          "
        >
          <sky-dropdown-menu>
            <sky-dropdown-item>
              <button
                type="button"
                [attr.aria-label]="
                  'Edit note ' + note.noteNumber + ' from ' + note.date
                "
              >
                Edit
              </button>
            </sky-dropdown-item>
            <sky-dropdown-item>
              <button
                type="button"
                [attr.aria-label]="
                  'Delete note ' + note.noteNumber + ' from ' + note.date
                "
              >
                Delete
              </button>
            </sky-dropdown-item>
          </sky-dropdown-menu>
        </sky-dropdown>
      </sky-repeater-item-context-menu>
      <sky-repeater-item-content>
        <div class="sky-margin-stacked-xs">
          {{ note.content }}
        </div>
        <div class="sky-font-deemphasized">{{ note.date }}</div>
      </sky-repeater-item-content>
    </sky-repeater-item>
  }
</sky-repeater>

```

#### record-page-overview-tab.component.html

```html
<sky-fluid-grid gutterSize="medium" [disableMargin]="true">
  <sky-row>
    <sky-column [screenSmall]="4" [screenXSmall]="12">
      <sky-box class="sky-margin-stacked-xl" headingText="Details">
        <sky-box-controls>
          <button
            aria-label="Edit button for details"
            class="sky-btn sky-btn-icon-borderless"
            type="button"
          >
            <sky-icon iconName="edit" />
          </button>
        </sky-box-controls>
        <sky-box-content>
          <sky-description-list mode="vertical">
            @for (recordDetail of recordDetails; track recordDetail.detail) {
              <sky-description-list-content>
                <sky-description-list-term>
                  {{ recordDetail.detail }}
                </sky-description-list-term>
                <sky-description-list-description>
                  {{ recordDetail.info }}
                </sky-description-list-description>
              </sky-description-list-content>
            }
          </sky-description-list>
        </sky-box-content>
      </sky-box>
    </sky-column>
    <sky-column [screenSmall]="4" [screenXSmall]="12">
      <sky-box class="sky-margin-stacked-xl" headingText="Payments">
        <sky-box-content>
          <div class="box-2-content">
            <div class="box-2-actuals">
              <h3 class="sky-font-heading-4">Actuals</h3>
              @for (
                actual of actualPayments;
                track actual.category;
                let i = $index
              ) {
                <sky-key-info
                  [ngClass]="{
                    'sky-margin-stacked-lg': i < actualPayments.length - 1
                  }"
                >
                  <sky-key-info-value class="sky-font-display-3">
                    {{ actual.value }}
                  </sky-key-info-value>
                  <sky-key-info-label>{{ actual.category }}</sky-key-info-label>
                </sky-key-info>
              }
            </div>
            <div class="box-2-projected">
              <h3 class="sky-font-heading-4">Projected</h3>
              @for (
                projected of projectedPayments;
                track projected;
                let i = $index
              ) {
                <sky-key-info
                  [ngClass]="{
                    'sky-margin-stacked-lg': i < projectedPayments.length - 1
                  }"
                >
                  <sky-key-info-value class="sky-font-display-3">
                    {{ projected.value }}
                  </sky-key-info-value>
                  <sky-key-info-label>
                    {{ projected.category }}
                  </sky-key-info-label>
                </sky-key-info>
              }
            </div>
          </div>
        </sky-box-content>
      </sky-box>
    </sky-column>
    <sky-column [screenSmall]="4" [screenXSmall]="12">
      <sky-box headingText="Recent activity">
        <sky-box-content>
          <sky-repeater>
            @for (activity of recentActivity; track activity.activity) {
              <sky-repeater-item>
                <sky-repeater-item-content>
                  <div class="sky-margin-stacked-xs">
                    {{ activity.activity }}
                  </div>
                  <div class="sky-font-deemphasized">{{ activity.date }}</div>
                </sky-repeater-item-content>
              </sky-repeater-item>
            }
          </sky-repeater>
        </sky-box-content>
      </sky-box>
    </sky-column>
  </sky-row>
</sky-fluid-grid>

```

#### record-page-overview-tab.component.scss

```css
.box-2-content {
  display: flex;

  div {
    display: flex;
    flex-direction: column;
    flex-grow: 1;
  }

  .box-2-actuals {
    margin-right: 60px;
  }
}

```

---

## Sectioned form inside modal

**Component:** TabsSectionedFormModalExampleComponent

**Selector:** `app-tabs-sectioned-form-modal-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### address-form.component.ts

```typescript
import { ChangeDetectionStrategy, Component } from '@angular/core';

@Component({
  standalone: true,
  selector: 'app-address-form',
  template: `<div>Address form</div>`,
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class AddressFormComponent {}

```

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyInputBoxHarness } from '@skyux/forms/testing';
import { SkySectionedFormHarness } from '@skyux/tabs/testing';

import { TabsSectionedFormModalExampleComponent } from './example.component';

describe('Sectioned form in a modal example', () => {
  async function setupTest(): Promise<{
    sectionedFormHarness: SkySectionedFormHarness;
    fixture: ComponentFixture<TabsSectionedFormModalExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [TabsSectionedFormModalExampleComponent, NoopAnimationsModule],
    }).compileComponents();
    const fixture = TestBed.createComponent(
      TabsSectionedFormModalExampleComponent,
    );
    fixture.componentInstance.openModal();

    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const sectionedFormHarness: SkySectionedFormHarness =
      await loader.getHarness(
        SkySectionedFormHarness.with({ dataSkyId: 'modal-sectioned-form' }),
      );

    return { sectionedFormHarness, fixture };
  }

  it('should set up the sectioned form', async () => {
    const { sectionedFormHarness } = await setupTest();
    let activeSection = await sectionedFormHarness.getActiveSection();
    await expectAsync(activeSection?.getSectionHeading()).toBeResolvedTo(
      'Addresses',
    );
    await expectAsync(activeSection?.getSectionItemCount()).toBeResolvedTo(2);

    await (
      await sectionedFormHarness.getSection({
        sectionHeading: 'Basic information',
      })
    ).click();

    await expectAsync(activeSection?.isActive()).toBeResolvedTo(false);

    activeSection = await sectionedFormHarness.getActiveSection();
    await expectAsync(activeSection?.getSectionHeading()).toBeResolvedTo(
      'Basic information',
    );

    const activeContent = await sectionedFormHarness.getActiveSectionContent();

    const idField = await (
      await activeContent?.queryHarness(
        SkyInputBoxHarness.with({ dataSkyId: 'id-field' }),
      )
    )?.querySelector('input');

    await expectAsync(idField?.getProperty('value')).toBeResolvedTo('5324901');
  });
});

```

#### example.component.ts

```typescript
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import { SkyModalCloseArgs, SkyModalService } from '@skyux/modals';

import { ModalComponent } from './modal.component';

/**
 * @title Sectioned form inside modal
 */
@Component({
  standalone: true,
  selector: 'app-tabs-sectioned-form-modal-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class TabsSectionedFormModalExampleComponent {
  readonly #modalSvc = inject(SkyModalService);

  public openModal(): void {
    const modalInstance = this.#modalSvc.open(ModalComponent, {
      size: 'large',
    });

    modalInstance.closed.subscribe((result: SkyModalCloseArgs) => {
      if (result.reason === 'cancel') {
        console.log(`Modal cancelled`);
      } else if (result.reason === 'save') {
        console.log(`Modal saved`);
      }
    });
  }
}

```

#### information-form.component.ts

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  OnInit,
  inject,
} from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  ReactiveFormsModule,
  Validators,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyStatusIndicatorModule } from '@skyux/indicators';
import { SkyFluidGridModule } from '@skyux/layout';
import { SkySectionedFormService } from '@skyux/tabs';

@Component({
  selector: 'app-information-form',
  templateUrl: './information-form.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [
    ReactiveFormsModule,
    SkyInputBoxModule,
    SkyFluidGridModule,
    SkyStatusIndicatorModule,
  ],
})
export class InformationFormComponent implements OnInit {
  protected id = '5324901';
  protected formGroup: FormGroup<{
    name: FormControl<string>;
    nameRequired: FormControl<boolean>;
    id: FormControl<string>;
  }>;
  protected name = '';
  protected nameRequired = false;

  readonly #sectionedFormSvc = inject(SkySectionedFormService);
  readonly #changeDetector = inject(ChangeDetectorRef);

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      name: new FormControl(this.name, { nonNullable: true }),
      nameRequired: new FormControl(this.nameRequired, { nonNullable: true }),
      id: new FormControl(this.id, {
        nonNullable: true,
        validators: [Validators.pattern('^[0-9]+$')],
      }),
    });
  }

  public ngOnInit(): void {
    this.formGroup.valueChanges.subscribe((changes) => {
      this.id = changes.id ?? '';
      this.name = changes.name ?? '';
      this.nameRequired = !!changes.nameRequired;
      this.#checkValidity();
    });

    this.#changeDetector.markForCheck();
  }

  #checkValidity(): void {
    if (this.nameRequired) {
      this.formGroup.get('name')?.setValidators([Validators.required]);
      this.#sectionedFormSvc.requiredFieldChanged(true);
    } else {
      this.formGroup.get('name')?.setValidators([]);
      this.#sectionedFormSvc.requiredFieldChanged(false);
    }

    if (!this.formGroup.get('name')?.value && this.nameRequired) {
      this.#sectionedFormSvc.invalidFieldChanged(true);
    } else {
      this.#sectionedFormSvc.invalidFieldChanged(false);
    }
  }
}

```

#### modal.component.ts

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  inject,
} from '@angular/core';
import { SkyIconModule } from '@skyux/icon';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';
import {
  SkySectionedFormMessage,
  SkySectionedFormMessageType,
  SkySectionedFormModule,
} from '@skyux/tabs';

import { Subject } from 'rxjs';

import { AddressFormComponent } from './address-form.component';
import { InformationFormComponent } from './information-form.component';
import { PhoneFormComponent } from './phone-form.component';

@Component({
  selector: 'app-modal',
  templateUrl: './modal.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [
    AddressFormComponent,
    InformationFormComponent,
    PhoneFormComponent,
    SkyIconModule,
    SkyModalModule,
    SkySectionedFormModule,
  ],
})
export class ModalComponent {
  protected activeIndexDisplay: number | undefined;
  protected activeTab = true;
  protected sectionedFormController = new Subject<SkySectionedFormMessage>();
  protected tabsHidden = false;

  protected readonly modalInstance = inject(SkyModalInstance);
  readonly #changeDetector = inject(ChangeDetectorRef);

  protected onIndexChanged(newIndex: number): void {
    this.activeIndexDisplay = newIndex;
    this.#changeDetector.markForCheck();
  }

  protected onTabsVisibleChanged(visible: boolean): void {
    this.tabsHidden = !visible;
  }

  protected showTabs(): void {
    this.sectionedFormController.next({
      type: SkySectionedFormMessageType.ShowTabs,
    });
  }
}

```

#### phone-form.component.ts

```typescript
import { ChangeDetectionStrategy, Component } from '@angular/core';

@Component({
  standalone: true,
  selector: 'app-phone-form',
  template: `<div>Phone form</div>`,
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class PhoneFormComponent {}

```

#### example.component.html

```html
<button class="sky-btn sky-btn-default" type="button" (click)="openModal()">
  Open sectioned form
</button>

```

#### information-form.component.html

```html
<form novalidate [formGroup]="formGroup">
  <sky-fluid-grid gutterSize="small" [disableMargin]="true">
    <sky-row>
      <sky-column [screenXSmall]="6">
        <sky-input-box data-sky-id="name-field" labelText="Name" stacked="true">
          <input formControlName="name" type="text" />
        </sky-input-box>
      </sky-column>
      <sky-column [screenXSmall]="6">
        <sky-input-box data-sky-id="id-field" labelText="ID" stacked="true">
          <input formControlName="id" type="text" />
          <span class="sky-error-indicator">
            @if (formGroup.get('id')?.invalid) {
              <sky-status-indicator
                indicatorType="danger"
                descriptionType="error"
              >
                Enter a valid value.
              </sky-status-indicator>
            }
          </span>
        </sky-input-box>
      </sky-column>
    </sky-row>
  </sky-fluid-grid>
</form>

```

#### modal.component.html

```html
<sky-modal [headingText]="'Sectioned form — Index: ' + activeIndexDisplay">
  <sky-modal-content>
    <sky-sectioned-form
      data-sky-id="modal-sectioned-form"
      [messageStream]="sectionedFormController"
      (indexChanged)="onIndexChanged($event)"
      (tabsVisibleChanged)="onTabsVisibleChanged($event)"
    >
      <sky-sectioned-form-section heading="Basic information">
        <app-information-form />
      </sky-sectioned-form-section>
      <sky-sectioned-form-section
        heading="Addresses"
        [itemCount]="2"
        [active]="activeTab"
      >
        <app-address-form />
      </sky-sectioned-form-section>
      <sky-sectioned-form-section heading="Phone numbers" [itemCount]="3">
        <app-phone-form />
      </sky-sectioned-form-section>
    </sky-sectioned-form>
  </sky-modal-content>
  <sky-modal-footer>
    @if (tabsHidden) {
      <button
        class="sky-btn sky-btn-default"
        type="button"
        (click)="showTabs()"
      >
        <sky-icon iconName="chevron-left" />
        Show sections
      </button>
    }
    <button
      class="sky-btn sky-btn-primary"
      type="button"
      (click)="modalInstance.save()"
    >
      Save
    </button>
    <button
      class="sky-btn sky-btn-link"
      type="button"
      (click)="modalInstance.cancel()"
    >
      Cancel
    </button>
  </sky-modal-footer>
</sky-modal>

```

---

## Tabs bound to an array, with add and close buttons

**Component:** TabsDynamicAddCloseExampleComponent

**Selector:** `app-tabs-dynamic-add-close-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { provideRouter } from '@angular/router';
import { SkyTabsetHarness } from '@skyux/tabs/testing';

import { TabsDynamicAddCloseExampleComponent } from './example.component';

describe('Static tabs demo with add and close', () => {
  async function setupTest(options: { dataSkyId?: string }): Promise<{
    harness: SkyTabsetHarness;
    fixture: ComponentFixture<TabsDynamicAddCloseExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      providers: [provideRouter([])],
    }).compileComponents();
    const fixture = TestBed.createComponent(
      TabsDynamicAddCloseExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyTabsetHarness.with({ dataSkyId: options.dataSkyId }),
    );

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [TabsDynamicAddCloseExampleComponent],
    });
  });

  it('should set up tabs', async () => {
    const { harness } = await setupTest({ dataSkyId: 'tab-demo' });

    await harness.clickNewTabButton();
    const tabButtonHarnesses = await harness.getTabButtonHarnesses();
    expect(tabButtonHarnesses.length).toBe(4);

    const activeTab = await harness.getActiveTabButton();
    await expectAsync(activeTab?.getTabHeading()).toBeResolvedTo('Tab 1');
  });

  it('should hide Tab 3 if it is closed', async () => {
    const { harness } = await setupTest({ dataSkyId: 'tab-demo' });

    const tab3Harness = await harness.getTabButtonHarness({
      tabHeading: 'Tab 3',
    });
    await tab3Harness.clickRemoveButton();

    const tabButtons = await harness.getTabButtonHarnesses();
    expect(tabButtons.length).toBe(2);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyTabsModule } from '@skyux/tabs';

/**
 * @title Tabs bound to an array, with add and close buttons
 */
@Component({
  selector: 'app-tabs-dynamic-add-close-example',
  templateUrl: './example.component.html',
  imports: [SkyTabsModule],
})
export class TabsDynamicAddCloseExampleComponent {
  protected tabArray = [
    {
      tabHeading: 'Tab 1',
      tabContent: 'Content for Tab 1',
    },
    {
      tabHeading: 'Tab 2',
      tabContent: 'Content for Tab 2',
    },
    {
      tabHeading: 'Tab 3',
      tabContent: 'Content for Tab 3',
    },
  ];

  #tabCounter = 3;

  protected onNewTabClick(): void {
    this.#tabCounter++;

    this.tabArray.push({
      tabHeading: 'Tab ' + this.#tabCounter,
      tabContent: 'Content for Tab' + this.#tabCounter,
    });
  }

  protected onCloseClick(arrayIndex: number): void {
    this.tabArray.splice(arrayIndex, 1);
  }
}

```

#### example.component.html

```html
<sky-tabset
  ariaLabel="Tab demonstration"
  data-sky-id="tab-demo"
  (newTab)="onNewTabClick()"
>
  @for (tab of tabArray; track tab; let i = $index) {
    <sky-tab [tabHeading]="tab.tabHeading" (close)="onCloseClick(i)">
      {{ tab.tabContent }}
    </sky-tab>
  }
</sky-tabset>

```

---

## Tabs bound to an array

**Component:** TabsDynamicExampleComponent

**Selector:** `app-tabs-dynamic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { provideRouter } from '@angular/router';
import { SkyTabsetHarness } from '@skyux/tabs/testing';

import { TabsDynamicExampleComponent } from './example.component';

describe('Dynamic tabs demo with add and close', () => {
  async function setupTest(options: { dataSkyId?: string }): Promise<{
    harness: SkyTabsetHarness;
    fixture: ComponentFixture<TabsDynamicExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      providers: [provideRouter([])],
    }).compileComponents();
    const fixture = TestBed.createComponent(TabsDynamicExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyTabsetHarness.with({ dataSkyId: options.dataSkyId }),
    );

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({ imports: [TabsDynamicExampleComponent] });
  });

  it('should set up tabs', async () => {
    const { harness } = await setupTest({ dataSkyId: 'tab-demo' });

    const tabButtonHarnesses = await harness.getTabButtonHarnesses();
    expect(tabButtonHarnesses.length).toBe(3);

    const activeTab = await harness.getActiveTabButton();
    await expectAsync(activeTab?.getTabHeading()).toBeResolvedTo('Tab 1');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyTabsModule } from '@skyux/tabs';

/**
 * @title Tabs bound to an array
 */
@Component({
  selector: 'app-tabs-dynamic-example',
  templateUrl: './example.component.html',
  imports: [SkyTabsModule],
})
export class TabsDynamicExampleComponent {
  protected tabArray = [
    {
      tabHeading: 'Tab 1',
      tabContent: 'A list containing 25012 items',
    },
    {
      tabHeading: 'Tab 2',
      tabContent: 'A list containing 280 items',
    },
    {
      tabHeading: 'Tab 3',
      tabContent: "This tab doesn't have a list of items",
    },
  ];
}

```

#### example.component.html

```html
<sky-tabset ariaLabel="Tab demonstration" data-sky-id="tab-demo">
  @for (tab of tabArray; track tab) {
    <sky-tab [tabHeading]="tab.tabHeading">
      {{ tab.tabContent }}
    </sky-tab>
  }
</sky-tabset>

```

---

## Tabs with add and close buttons

**Component:** TabsStaticAddCloseExampleComponent

**Selector:** `app-tabs-static-add-close-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { provideRouter } from '@angular/router';
import { SkyTabsetHarness } from '@skyux/tabs/testing';

import { TabsStaticAddCloseExampleComponent } from './example.component';

describe('Static tabs demo with add and close', () => {
  async function setupTest(options: { dataSkyId?: string }): Promise<{
    harness: SkyTabsetHarness;
    fixture: ComponentFixture<TabsStaticAddCloseExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      providers: [provideRouter([])],
    }).compileComponents();
    const fixture = TestBed.createComponent(TabsStaticAddCloseExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyTabsetHarness.with({ dataSkyId: options.dataSkyId }),
    );

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [TabsStaticAddCloseExampleComponent],
    });
  });

  it('should set up tabs', async () => {
    const { harness, fixture } = await setupTest({ dataSkyId: 'tab-demo' });

    const spy = spyOn(fixture.componentInstance, 'onNewTabClick');
    await harness.clickNewTabButton();

    expect(spy).toHaveBeenCalled();

    const tabButtonHarnesses = await harness.getTabButtonHarnesses();
    expect(tabButtonHarnesses.length).toBe(3);

    const activeTab = await harness.getActiveTabButton();
    await expectAsync(activeTab?.getTabHeading()).toBeResolvedTo('Tab 1');
  });

  it('should hide Tab 3 if it is closed', async () => {
    const { harness } = await setupTest({ dataSkyId: 'tab-demo' });

    const tab3Harness = await harness.getTabButtonHarness({
      tabHeading: 'Tab 3',
    });
    await tab3Harness.clickRemoveButton();

    const tabButtons = await harness.getTabButtonHarnesses();
    expect(tabButtons.length).toBe(2);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyTabsModule } from '@skyux/tabs';

/**
 * @title Tabs with add and close buttons
 */
@Component({
  selector: 'app-tabs-static-add-close-example',
  templateUrl: './example.component.html',
  imports: [SkyTabsModule],
})
export class TabsStaticAddCloseExampleComponent {
  protected showTab3 = true;

  public onNewTabClick(): void {
    alert('Add tab clicked!');
  }
}

```

#### example.component.html

```html
<sky-tabset
  data-sky-id="tab-demo"
  ariaLabel="Tab demonstration"
  (newTab)="onNewTabClick()"
>
  <sky-tab [tabHeading]="'Tab 1'"> Content for Tab 1 </sky-tab>
  <sky-tab [tabHeading]="'Tab 2'"> Content for Tab 2 </sky-tab>
  @if (showTab3) {
    <sky-tab [tabHeading]="'Tab 3'" (close)="showTab3 = false">
      Content for Tab 3
    </sky-tab>
  }
</sky-tabset>

```

---

## Tabs with basic setup

**Component:** TabsStaticExampleComponent

**Selector:** `app-tabs-static-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { provideRouter } from '@angular/router';
import { SkyTabsetHarness } from '@skyux/tabs/testing';

import { TabsStaticExampleComponent } from './example.component';

describe('Static tabs demo with add and close', () => {
  async function setupTest(options: { dataSkyId?: string }): Promise<{
    harness: SkyTabsetHarness;
    fixture: ComponentFixture<TabsStaticExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      providers: [provideRouter([])],
    }).compileComponents();
    const fixture = TestBed.createComponent(TabsStaticExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyTabsetHarness.with({ dataSkyId: options.dataSkyId }),
    );

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({ imports: [TabsStaticExampleComponent] });
  });

  it('should set up tabs', async () => {
    const { harness } = await setupTest({ dataSkyId: 'tab-demo' });

    const tabButtonHarnesses = await harness.getTabButtonHarnesses();
    expect(tabButtonHarnesses.length).toBe(3);

    const activeTab = await harness.getActiveTabButton();
    await expectAsync(activeTab?.getTabHeading()).toBeResolvedTo('Tab 1');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyTabsModule } from '@skyux/tabs';

/**
 * @title Tabs with basic setup
 */
@Component({
  selector: 'app-tabs-static-example',
  templateUrl: './example.component.html',
  imports: [SkyTabsModule],
})
export class TabsStaticExampleComponent {}

```

#### example.component.html

```html
<sky-tabset ariaLabel="Tab demonstration" data-sky-id="tab-demo">
  <sky-tab [tabHeading]="'Tab 1'"> Content for Tab 1 </sky-tab>
  <sky-tab [tabHeading]="'Tab 2'"> Content for Tab 2 </sky-tab>
  <sky-tab [tabHeading]="'Tab 3'"> Content for Tab 3 </sky-tab>
</sky-tabset>

```

---

## Vertical tabs with basic setup

**Component:** TabsVerticalTabsBasicExampleComponent

**Selector:** `app-tabs-vertical-tabs-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyVerticalTabsetHarness } from '@skyux/tabs/testing';

import { TabsVerticalTabsBasicExampleComponent } from './example.component';

describe('Basic vertical tabs example', () => {
  async function setupTest(options: { dataSkyId?: string }): Promise<{
    harness: SkyVerticalTabsetHarness;
    fixture: ComponentFixture<TabsVerticalTabsBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      TabsVerticalTabsBasicExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyVerticalTabsetHarness.with({ dataSkyId: options.dataSkyId }),
    );

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [TabsVerticalTabsBasicExampleComponent, NoopAnimationsModule],
    });
  });

  it('should set up vertical tabs', async () => {
    const { harness } = await setupTest({ dataSkyId: 'vertical-tabs-basic' });

    const allTabs = await harness.getTabs();
    expect(allTabs.length).toBe(3);

    const activeTab = await harness.getActiveTab();
    expect(await activeTab?.getTabHeading()).toBe('Tab 2');
    const activeTabContent = await activeTab?.getTabContent();
    expect(await activeTabContent?.isVisible()).toBeTrue();

    const disabledTab = await harness.getTab({ tabHeading: 'Tab 3' });
    expect(await disabledTab?.isDisabled()).toBeTrue();
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyVerticalTabsetModule } from '@skyux/tabs';

/**
 * @title Vertical tabs with basic setup
 */
@Component({
  selector: 'app-tabs-vertical-tabs-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyVerticalTabsetModule],
})
export class TabsVerticalTabsBasicExampleComponent {}

```

#### example.component.html

```html
<sky-vertical-tabset data-sky-id="vertical-tabs-basic">
  <sky-vertical-tab tabHeading="Tab 1"> Tab 1 content </sky-vertical-tab>
  <sky-vertical-tab tabHeading="Tab 2" [active]="true">
    Tab 2 content
  </sky-vertical-tab>
  <sky-vertical-tab tabHeading="Tab 3" [disabled]="true">
    Tab 3 content
  </sky-vertical-tab>
</sky-vertical-tabset>

```

---

## Vertical tabs with grouped tabs

**Component:** TabsVerticalTabsGroupedExampleComponent

**Selector:** `app-tabs-vertical-tabs-grouped-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyVerticalTabsetHarness } from '@skyux/tabs/testing';

import { TabsVerticalTabsGroupedExampleComponent } from './example.component';

describe('Group vertical tabs example', () => {
  async function setupTest(options: { dataSkyId?: string }): Promise<{
    harness: SkyVerticalTabsetHarness;
    fixture: ComponentFixture<TabsVerticalTabsGroupedExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      TabsVerticalTabsGroupedExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyVerticalTabsetHarness.with({ dataSkyId: options.dataSkyId }),
    );

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [TabsVerticalTabsGroupedExampleComponent, NoopAnimationsModule],
    });
  });

  it('should set up vertical tabs', async () => {
    const { harness } = await setupTest({ dataSkyId: 'vertical-tabs-group' });

    const allTabs = await harness.getTabs();
    expect(allTabs.length).toBe(4);

    const groups = await harness.getGroups();
    expect(groups.length).toBe(3);

    const disabledGroup = await harness.getGroup({
      groupHeading: 'Disabled',
    });
    await expectAsync(disabledGroup?.isDisabled()).toBeResolvedTo(true);

    const group1Tab2 = await harness.getTab({ tabHeading: 'Group 1 — Tab 2' });
    await expectAsync(group1Tab2.getTabHeaderCount()).toBeResolvedTo(7);
  });

  it('should have active tab as the first tab in group 2', async () => {
    const { harness } = await setupTest({ dataSkyId: 'vertical-tabs-group' });

    // Two ways to get a tab inside a group
    // Through tabset harness
    const activeTab = await harness.getActiveTab();

    // Through group harness
    const group2 = await harness.getGroup({ groupHeading: 'Group 2' });
    await expectAsync(group2?.isActive()).toBeResolvedTo(true);

    const tab1 = await group2?.getVerticalTab({
      tabHeading: 'Group 2 — Tab 1',
    });

    const check =
      (await activeTab?.getTabHeading()) === (await tab1?.getTabHeading());
    expect(check).toBe(true);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyVerticalTabsetModule } from '@skyux/tabs';

import { TabGroup } from './group';

/**
 * @title Vertical tabs with grouped tabs
 */
@Component({
  selector: 'app-tabs-vertical-tabs-grouped-example',
  templateUrl: './example.component.html',
  imports: [SkyVerticalTabsetModule],
})
export class TabsVerticalTabsGroupedExampleComponent {
  protected groups: TabGroup[] = [
    {
      heading: 'Group 1',
      isOpen: false,
      isDisabled: false,
      subTabs: [
        { tabHeading: 'Group 1 — Tab 1', content: 'Group 1 — Tab 1 Content' },
        {
          tabHeading: 'Group 1 — Tab 2',
          content: 'Group 1 — Tab 2 Content',
          tabHeaderCount: 7,
        },
      ],
    },
    {
      heading: 'Group 2',
      isOpen: true,
      isDisabled: false,
      subTabs: [
        {
          tabHeading: 'Group 2 — Tab 1',
          content: 'Group 2 — Tab 1 Content',
          active: true,
        },
        {
          tabHeading: 'Group 2 — Tab 2 — Disabled',
          content: 'Group 2 — Tab 2 Content',
          disabled: true,
        },
      ],
    },
    {
      heading: 'Disabled',
      isOpen: false,
      isDisabled: true,
      subTabs: [],
    },
  ];
}

```

#### group.ts

```typescript
export interface TabGroup {
  heading: string;
  isOpen: boolean;
  isDisabled: boolean;
  subTabs: {
    tabHeading: string;
    content: string;
    tabHeaderCount?: number;
    active?: boolean;
    disabled?: boolean;
  }[];
}

```

#### example.component.html

```html
<sky-vertical-tabset data-sky-id="vertical-tabs-group" showTabsText="Tab list">
  @for (group of groups; track group) {
    <sky-vertical-tabset-group
      [groupHeading]="group.heading"
      [open]="group.isOpen"
      [disabled]="group.isDisabled"
    >
      @for (tab of group.subTabs; track tab) {
        <sky-vertical-tab
          [active]="tab.active"
          [tabHeading]="tab.tabHeading"
          [tabHeaderCount]="tab.tabHeaderCount"
          [disabled]="tab.disabled"
        >
          {{ tab.content }}
        </sky-vertical-tab>
      }
    </sky-vertical-tabset-group>
  }
</sky-vertical-tabset>

```

---

## Vertical tabs with grouped and ungrouped tabs

**Component:** TabsVerticalTabsMixedExampleComponent

**Selector:** `app-tabs-vertical-tabs-mixed-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyVerticalTabsetHarness } from '@skyux/tabs/testing';

import { TabsVerticalTabsMixedExampleComponent } from './example.component';

describe('Mixed vertical tabs example', () => {
  async function setupTest(options: { dataSkyId?: string }): Promise<{
    harness: SkyVerticalTabsetHarness;
    fixture: ComponentFixture<TabsVerticalTabsMixedExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      TabsVerticalTabsMixedExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyVerticalTabsetHarness.with({ dataSkyId: options.dataSkyId }),
    );

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [TabsVerticalTabsMixedExampleComponent, NoopAnimationsModule],
    });
  });

  it('should show grouped and ungrouped tabs', async () => {
    const { harness } = await setupTest({ dataSkyId: 'vertical-tabs-mixed' });

    // Test grouped tabs
    const group1 = await harness.getGroup({ groupHeading: 'Group 1' });
    expect(group1).toBeTruthy();
    expect(await group1?.isOpen()).toBe(true);

    const group2 = await harness.getGroup({ groupHeading: 'Group 2' });
    expect(group2).toBeTruthy();
    expect(await group2?.isOpen()).toBe(false);

    // Test ungrouped tabs
    const tab1 = await harness.getTab({ tabHeading: 'Tab 1' });
    expect(tab1).toBeTruthy();

    const tab2 = await harness.getTab({ tabHeading: 'Tab 2' });
    expect(tab2).toBeTruthy();
    expect(await tab2?.getTabHeaderCount()).toBe(3);

    const tab3 = await harness.getTab({ tabHeading: 'Tab 3' });
    expect(tab3).toBeTruthy();
    expect(await tab3?.isDisabled()).toBe(true);
  });

  it('should have the group 1 tab 1 active by default', async () => {
    const { harness } = await setupTest({ dataSkyId: 'vertical-tabs-mixed' });

    const group1Tab1 = await harness.getTab({ tabHeading: 'Group 1 — Tab 1' });
    expect(group1Tab1).toBeTruthy();
    expect(await group1Tab1?.isActive()).toBe(true);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyVerticalTabsetModule } from '@skyux/tabs';

import { TabGroup } from './group';

/**
 * @title Vertical tabs with grouped and ungrouped tabs
 */
@Component({
  selector: 'app-tabs-vertical-tabs-mixed-example',
  templateUrl: './example.component.html',
  imports: [SkyVerticalTabsetModule],
})
export class TabsVerticalTabsMixedExampleComponent {
  protected groupedTabs: TabGroup[] = [
    {
      heading: 'Group 1',
      isOpen: true,
      subTabs: [
        {
          tabHeading: 'Group 1 — Tab 1',
          content: 'Group 1 — Tab 1 Content',
          active: true,
        },
        {
          tabHeading: 'Group 1 — Tab 2',
          content: 'Group 1 — Tab 2 Content',
        },
      ],
    },
    {
      heading: 'Group 2',
      isOpen: false,
      subTabs: [
        {
          tabHeading: 'Group 2 — Tab 1',
          content: 'Group 2 — Tab 1 Content',
        },
        {
          tabHeading: 'Group 2 — Tab 2',
          content: 'Group 2 — Tab 2 Content',
        },
      ],
    },
    {
      heading: 'Group 3 - disabled',
      isOpen: false,
      isDisabled: true,
      subTabs: [
        {
          tabHeading: 'Group 3 — Tab 1',
          content: 'Group 3 — Tab 1 Content',
        },
        {
          tabHeading: 'Group 3 — Tab 2',
          content: 'Group 3 — Tab 2 Content',
        },
      ],
    },
  ];
}

```

#### group.ts

```typescript
export interface TabGroup {
  heading: string;
  isOpen: boolean;
  isDisabled?: boolean;
  subTabs: {
    tabHeading: string;
    content: string;
    tabHeaderCount?: number;
    active?: boolean;
    disabled?: boolean;
  }[];
}

```

#### example.component.html

```html
<sky-vertical-tabset data-sky-id="vertical-tabs-mixed" showTabsText="Tab list">
  @for (group of groupedTabs; track group) {
    <sky-vertical-tabset-group
      [groupHeading]="group.heading"
      [open]="group.isOpen"
      [disabled]="group.isDisabled"
    >
      @for (tab of group.subTabs; track tab) {
        <sky-vertical-tab [active]="tab.active" [tabHeading]="tab.tabHeading">
          {{ tab.content }}
        </sky-vertical-tab>
      }
    </sky-vertical-tabset-group>
  }

  <sky-vertical-tab tabHeading="Tab 1"> Tab 1 Content </sky-vertical-tab>

  <sky-vertical-tab tabHeading="Tab 2" [tabHeaderCount]="3">
    Tab 2 Content
  </sky-vertical-tab>

  <sky-vertical-tab tabHeading="Tab 3" [disabled]="true">
    Tab 3 Content
  </sky-vertical-tab>
</sky-vertical-tabset>

```

---

## Wizard in a modal

**Component:** TabsWizardBasicExampleComponent

**Selector:** `app-tabs-wizard-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { SkyModalService } from '@skyux/modals';

import { ModalComponent } from './modal.component';

/**
 * @title Wizard in a modal
 */
@Component({
  standalone: true,
  selector: 'app-tabs-wizard-basic-example',
  templateUrl: './example.component.html',
})
export class TabsWizardBasicExampleComponent {
  readonly #modalSvc = inject(SkyModalService);

  #modalSize = 'large';

  protected openWizard(): void {
    this.#modalSvc.open(ModalComponent, { size: this.#modalSize });
  }
}

```

#### modal.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { provideRouter } from '@angular/router';
import { SkyInputBoxHarness } from '@skyux/forms/testing';
import { SkyModalInstance } from '@skyux/modals';
import {
  SkyTabsetHarness,
  SkyTabsetNavButtonHarness,
} from '@skyux/tabs/testing';

import { ModalComponent } from './modal.component';

describe('Wizard tabset demo', () => {
  async function setupTest(options: { dataSkyId?: string }): Promise<{
    harness: SkyTabsetHarness;
    fixture: ComponentFixture<ModalComponent>;
    loader: HarnessLoader;
  }> {
    await TestBed.configureTestingModule({
      providers: [provideRouter([]), SkyModalInstance],
      imports: [ModalComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(ModalComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const harness = await loader.getHarness(
      SkyTabsetHarness.with({ dataSkyId: options.dataSkyId }),
    );
    return { harness, fixture, loader };
  }

  it('should set up the tabset wizard', async () => {
    const { harness, loader } = await setupTest({
      dataSkyId: 'sign-up-wizard',
    });

    // You can get all tab button harnesses from the tabset harness.
    const tabs = await harness.getTabButtonHarnesses();
    expect(tabs.length).toBe(3);
    await expectAsync(tabs[1].isDisabled()).toBeResolvedTo(true);

    // You can get the tab button harness from its `tabHeading`
    const tab2 = await harness.getTabButtonHarness({
      tabHeading: '2. Contact Information',
    });
    await expectAsync(tab2.isActive()).toBeResolvedTo(false);

    // You can get the active tab button's harness.
    const activeTab = await harness.getActiveTabButton();
    await expectAsync(activeTab?.getTabHeading()).toBeResolvedTo(
      '1. Biographical Details',
    );

    // You can get the tabset nav button harnesses by their `buttonType`.
    const previousButton = await loader.getHarness(
      SkyTabsetNavButtonHarness.with({
        buttonType: 'previous',
      }),
    );
    const nextButton = await loader.getHarness(
      SkyTabsetNavButtonHarness.with({
        buttonType: 'next',
      }),
    );

    await expectAsync(previousButton.isDisabled()).toBeResolvedTo(true);
    await expectAsync(nextButton.isDisabled()).toBeResolvedTo(true);
  });

  it('should enable the second step once the first step is complete', async () => {
    const { harness, loader, fixture } = await setupTest({
      dataSkyId: 'sign-up-wizard',
    });

    const tab1Harness = await harness.getActiveTabButton();

    // You can query the tab content harness' internal harnesses.
    const inputHarnesses = await (
      await tab1Harness?.getTabContentHarness()
    )?.queryHarnesses(SkyInputBoxHarness);
    expect(inputHarnesses?.length).toBe(3);

    fixture.componentInstance.formGroup.get('firstName')?.setValue('John');
    fixture.componentInstance.formGroup.get('lastName')?.setValue('Doe');
    fixture.detectChanges();

    // If changes in the test causes the tabset to swap to dropdown mode
    // open the dropdown to access tab button harnesses
    if ((await harness.getMode()) === 'dropdown') {
      await harness.clickDropdownTab();
    }

    const tab2 = await harness.getTabButtonHarness({
      tabHeading: '2. Contact Information',
    });
    expect(await tab2.isDisabled()).toBe(false);

    const nextButton = await loader.getHarness(
      SkyTabsetNavButtonHarness.with({ buttonType: 'next' }),
    );
    expect(await nextButton.isDisabled()).toBe(false);

    await nextButton.click();
    await expectAsync(tab2.isActive()).toBeResolvedTo(true);
  });
});

```

#### modal.component.ts

```typescript
import { Component, OnInit, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  ReactiveFormsModule,
  Validators,
} from '@angular/forms';
import { SkyCheckboxModule, SkyInputBoxModule } from '@skyux/forms';
import { SkyFluidGridModule } from '@skyux/layout';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';
import { SkyPhoneFieldModule } from '@skyux/phone-field';
import { SkyTabIndex, SkyTabsModule } from '@skyux/tabs';

@Component({
  selector: 'app-modal',
  templateUrl: './modal.component.html',
  imports: [
    ReactiveFormsModule,
    SkyCheckboxModule,
    SkyFluidGridModule,
    SkyInputBoxModule,
    SkyModalModule,
    SkyPhoneFieldModule,
    SkyTabsModule,
  ],
})
export class ModalComponent implements OnInit {
  protected activeIndex: SkyTabIndex = 0;
  public formGroup: FormGroup;
  protected isSaveDisabled = true;
  protected isStep2Disabled = true;
  protected isStep3Disabled = true;
  protected title = 'New Member Sign-up';

  readonly #instance = inject(SkyModalInstance);

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      firstName: new FormControl('', Validators.required),
      middleName: new FormControl(''),
      lastName: new FormControl('', Validators.required),
      phoneNumber: new FormControl('', Validators.required),
      email: new FormControl('', Validators.required),
      termsAccepted: new FormControl(false),
      mailingList: new FormControl(false),
    });
  }

  public ngOnInit(): void {
    this.formGroup.valueChanges.subscribe(() => {
      this.#checkRequirementsMet();
    });
  }

  protected onCancelClick(): void {
    this.#instance.cancel();
  }

  protected onSave(): void {
    this.#instance.save();
  }

  #checkRequirementsMet(): void {
    this.isStep2Disabled = !(
      this.formGroup?.get('firstName')?.value &&
      this.formGroup?.get('lastName')?.value
    );

    this.isStep3Disabled = !(
      this.formGroup?.get('phoneNumber')?.value &&
      this.formGroup?.get('phoneNumber')?.valid &&
      this.formGroup?.get('email')?.value
    );

    this.isSaveDisabled = !this.formGroup?.get('termsAccepted')?.value;
  }
}

```

#### example.component.html

```html
<button type="button" class="sky-btn sky-btn-default" (click)="openWizard()">
  Open Wizard
</button>

```

#### modal.component.html

```html
<form [formGroup]="formGroup" (ngSubmit)="onSave()">
  <sky-modal [headingText]="title">
    <sky-modal-content>
      <sky-tabset
        #wizardDemo
        ariaLabel="Sign-up steps"
        data-sky-id="sign-up-wizard"
        tabStyle="wizard"
        [(active)]="activeIndex"
      >
        <sky-tab tabHeading="1. Biographical Details">
          <sky-fluid-grid gutterSize="small" [disableMargin]="true">
            <sky-row>
              <sky-column [screenSmall]="12" [screenMedium]="4">
                <sky-input-box labelText="First name" [stacked]="true">
                  <input type="text" formControlName="firstName" />
                </sky-input-box>
              </sky-column>
              <sky-column [screenSmall]="12" [screenMedium]="4">
                <sky-input-box labelText="Middle name" [stacked]="true">
                  <input type="text" formControlName="middleName" />
                </sky-input-box>
              </sky-column>
              <sky-column [screenSmall]="12" [screenMedium]="4">
                <sky-input-box labelText="Last name">
                  <input type="text" formControlName="lastName" />
                </sky-input-box>
              </sky-column>
            </sky-row>
          </sky-fluid-grid>
        </sky-tab>
        <sky-tab
          tabHeading="2. Contact Information"
          [disabled]="isStep2Disabled"
        >
          <sky-fluid-grid gutterSize="small" [disableMargin]="true">
            <sky-row>
              <sky-column [screenSmall]="12" [screenMedium]="6">
                <sky-input-box labelText="Phone Number" [stacked]="true">
                  <sky-phone-field defaultCountry="us">
                    <input formControlName="phoneNumber" skyPhoneFieldInput />
                  </sky-phone-field>
                </sky-input-box>
              </sky-column>
              <sky-column [screenSmall]="12" [screenMedium]="6">
                <sky-input-box labelText="Email">
                  <input type="email" formControlName="email" />
                </sky-input-box>
              </sky-column>
            </sky-row>
          </sky-fluid-grid>
        </sky-tab>
        <sky-tab tabHeading="3. More Information" [disabled]="isStep3Disabled">
          <sky-fluid-grid gutterSize="small" [disableMargin]="true">
            <sky-row>
              <sky-column [screenSmall]="12">
                <sky-checkbox
                  formControlName="termsAccepted"
                  labelText="Accept terms and conditions"
                  required
                />
              </sky-column>
              <sky-column [screenSmall]="12">
                <sky-checkbox
                  formControlName="mailingList"
                  labelText="Sign up for our email newsletter"
                />
              </sky-column>
            </sky-row>
          </sky-fluid-grid>
        </sky-tab>
      </sky-tabset>
    </sky-modal-content>
    <sky-modal-footer>
      <sky-tabset-nav-button buttonType="previous" [tabset]="wizardDemo" />
      <sky-tabset-nav-button buttonType="next" [tabset]="wizardDemo" />
      <sky-tabset-nav-button
        buttonType="finish"
        [tabset]="wizardDemo"
        [disabled]="isSaveDisabled"
      />
      <button
        class="sky-btn sky-btn-link"
        type="button"
        (click)="onCancelClick()"
      >
        Cancel
      </button>
    </sky-modal-footer>
  </sky-modal>
</form>

```

---