---
component: 'split-view'
type: 'code-examples'
description: 'Code examples for the split-view component.'
---

# Split View Code Examples

## Split view page with fit layout

**Component:** PagesPageSplitViewPageFitLayoutExampleComponent

**Selector:** `app-pages-page-split-view-page-fit-layout-example`

**Import Path:** `@skyux/code-examples`

### Code Files

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

import { PagesPageSplitViewPageFitLayoutExampleComponent } from './example.component';

describe('Split view page fit layout example', () => {
  async function setupTest(): Promise<{
    pageHarness: SkyPageHarness;
    fixture: ComponentFixture<PagesPageSplitViewPageFitLayoutExampleComponent>;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(
      PagesPageSplitViewPageFitLayoutExampleComponent,
    );

    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const pageHarness = await loader.getHarness(SkyPageHarness);
    const helpController = TestBed.inject(SkyHelpTestingController);

    return { pageHarness, fixture, helpController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        PagesPageSplitViewPageFitLayoutExampleComponent,
        SkyHelpTestingModule,
        NoopAnimationsModule,
      ],
      providers: [provideRouter([])],
    });
  });

  it('should have a fit layout', async () => {
    const { pageHarness, fixture } = await setupTest();

    fixture.detectChanges();

    await expectAsync(pageHarness.getLayout()).toBeResolvedTo('fit');
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
import { SkyAlertModule } from '@skyux/indicators';
import { SkyPageModule } from '@skyux/pages';

import { SplitViewPageContentComponent } from './split-view-page-content.component';

/**
 * @title Split view page with fit layout
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-page-split-view-page-fit-layout-example',
  templateUrl: './example.component.html',
  imports: [SkyAlertModule, SkyPageModule, SplitViewPageContentComponent],
})
export class PagesPageSplitViewPageFitLayoutExampleComponent {}

```

#### split-view-page-content.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { FormBuilder, FormsModule, ReactiveFormsModule } from '@angular/forms';
import { SkySummaryActionBarModule } from '@skyux/action-bars';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyDescriptionListModule } from '@skyux/layout';
import { SkyRepeaterModule } from '@skyux/lists';
import { SkyConfirmService, SkyConfirmType } from '@skyux/modals';
import {
  SkySplitViewMessage,
  SkySplitViewMessageType,
  SkySplitViewModule,
} from '@skyux/split-view';

import { Subject } from 'rxjs';

interface WorkspaceItem {
  id: number;
  amount: number;
  date: string;
  vendor: string;
  receiptImage: string;
  approvedAmount: number;
  comments: string;
}

@Component({
  selector: 'app-split-view-page-content',
  templateUrl: './split-view-page-content.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyDescriptionListModule,
    SkyInputBoxModule,
    SkyRepeaterModule,
    SkySplitViewModule,
    SkySummaryActionBarModule,
  ],
})
export class SplitViewPageContentComponent {
  protected set activeIndex(value: number) {
    this.#_activeIndex = value;
    this.activeRecord = this.items[this.#_activeIndex];
    this.#loadFormGroup(this.activeRecord);
  }

  protected get activeIndex(): number {
    return this.#_activeIndex;
  }

  protected items: WorkspaceItem[] = [
    {
      id: 1,
      amount: 73.19,
      date: '5/13/2020',
      vendor: 'amazon.com',
      receiptImage: 'amzn-office-supply-order-5-13-19.png',
      approvedAmount: 73.19,
      comments: '',
    },
    {
      id: 2,
      amount: 214.12,
      date: '5/14/2020',
      vendor: 'Office Max',
      receiptImage: 'office-max-order.png',
      approvedAmount: 214.12,
      comments: '',
    },
    {
      id: 3,
      amount: 29.99,
      date: '5/14/2020',
      vendor: 'amazon.com',
      receiptImage: 'amzn-office-supply-order-5-14-19.png',
      approvedAmount: 29.99,
      comments: '',
    },
    {
      id: 4,
      amount: 1500,
      date: '5/15/2020',
      vendor: 'Fresh Catering, LLC',
      receiptImage: 'fresh-catering-llc-order.png',
      approvedAmount: 1500,
      comments: '',
    },
    {
      id: 5,
      amount: 456.24,
      date: '5/16/2020',
      vendor: 'Wish',
      receiptImage: 'wish-delivery-order.png',
      approvedAmount: 456.24,
      comments: '',
    },
    {
      id: 6,
      amount: 62.37,
      date: '5/16/2020',
      vendor: 'Staples',
      receiptImage: 'staples-paper-bulk-order.png',
      approvedAmount: 62.37,
      comments: '',
    },
    {
      id: 7,
      amount: 51.84,
      date: '5/17/2020',
      vendor: 'amazon.com',
      receiptImage: 'amzn-office-supply-order-5-17-19.png',
      approvedAmount: 51.84,
      comments: '',
    },
    {
      id: 8,
      amount: 92.55,
      date: '5/18/2020',
      vendor: 'Home Depot',
      receiptImage: 'home-depot-order.png',
      approvedAmount: 0.0,
      comments: '',
    },
    {
      id: 9,
      amount: 38.29,
      date: '5/18/2020',
      vendor: 'Papa Johns',
      receiptImage: 'papa-johns-order.png',
      approvedAmount: 38.29,
      comments: '',
    },
  ];

  protected activeRecord = this.items[0];
  protected listWidth: number | undefined;
  protected splitViewStream = new Subject<SkySplitViewMessage>();

  protected splitViewDemoForm = inject(FormBuilder).group({
    approvedAmount: [this.activeRecord.approvedAmount],
    comments: [this.activeRecord.comments],
  });

  #_activeIndex = 0;

  #confirmSvc = inject(SkyConfirmService);

  protected onItemClick(index: number): void {
    // Prevent workspace from loading new data if the current workspace form is dirty.
    if (this.splitViewDemoForm.dirty && index !== this.activeIndex) {
      this.#openConfirmModal(index);
    } else {
      this.#loadWorkspace(index);
    }
  }

  protected onApprove(): void {
    console.log('Approved clicked!');
    this.#saveForm();
  }

  protected onDeny(): void {
    console.log('Denied clicked!');
  }

  #loadFormGroup(record: WorkspaceItem): void {
    this.splitViewDemoForm.setValue({
      approvedAmount: record.approvedAmount,
      comments: record.comments,
    });
  }

  #loadWorkspace(index: number): void {
    this.activeIndex = index;
    this.#setFocusInWorkspace();
  }

  #openConfirmModal(index: number): void {
    this.#confirmSvc
      .open({
        message:
          'You have unsaved work. Would you like to save it before you change records?',
        type: SkyConfirmType.Custom,
        buttons: [
          {
            action: 'yes',
            text: 'Yes',
            styleType: 'primary',
          },
          {
            action: 'discard',
            text: 'Discard changes',
            styleType: 'link',
          },
        ],
      })
      .closed.subscribe((closeArgs) => {
        if (closeArgs.action === 'yes') {
          this.#saveForm();
        }

        this.#loadWorkspace(index);
      });
  }

  #saveForm(): void {
    this.activeRecord = Object.assign(
      this.activeRecord,
      this.splitViewDemoForm.value,
    );

    this.splitViewDemoForm.markAsPristine();
  }

  #setFocusInWorkspace(): void {
    this.splitViewStream.next({
      type: SkySplitViewMessageType.FocusWorkspace,
    });
  }
}

```

#### example.component.html

```html
<sky-page layout="fit" helpKey="example-help">
  <sky-page-header
    pageTitle="Expenses to approve"
    [parentLink]="{
      label: 'Expenses',
      permalink: {
        route: {
          commands: ['/']
        }
      }
    }"
  >
    <sky-page-header-alerts>
      <sky-alert alertType="warning" descriptionType="warning">
        There are multiple expense approvals due soon.
      </sky-alert>
    </sky-page-header-alerts>
    <sky-page-header-actions>
      <button class="sky-btn sky-btn-default" type="button">Approve all</button>
    </sky-page-header-actions>
  </sky-page-header>
  <sky-page-content>
    <app-split-view-page-content />
  </sky-page-content>
</sky-page>

```

#### split-view-page-content.component.html

```html
<sky-split-view dock="fill" [messageStream]="splitViewStream">
  <sky-split-view-drawer [ariaLabel]="'Transaction list'" [width]="listWidth">
    <sky-repeater [activeIndex]="activeIndex">
      @for (item of items; track item.id; let i = $index) {
        <sky-repeater-item
          (click)="onItemClick(i)"
          (keyup.enter)="onItemClick(i)"
        >
          <sky-repeater-item-content>
            {{ item.amount }} <br />
            {{ item.date }} <br />
            {{ item.vendor }}
          </sky-repeater-item-content>
        </sky-repeater-item>
      }
    </sky-repeater>
  </sky-split-view-drawer>

  <sky-split-view-workspace ariaLabel="Transaction form">
    <sky-split-view-workspace-content class="sky-padding-even-xl">
      <form [formGroup]="splitViewDemoForm" (ngSubmit)="onApprove()">
        <sky-description-list class="sky-margin-stacked-xl">
          <sky-description-list-content>
            <sky-description-list-term>
              Receipt amount
            </sky-description-list-term>
            <sky-description-list-description>
              {{ activeRecord.amount }}
            </sky-description-list-description>
          </sky-description-list-content>
          <sky-description-list-content>
            <sky-description-list-term> Date </sky-description-list-term>
            <sky-description-list-description>
              {{ activeRecord.date }}
            </sky-description-list-description>
          </sky-description-list-content>
          <sky-description-list-content>
            <sky-description-list-term> Vendor </sky-description-list-term>
            <sky-description-list-description>
              {{ activeRecord.vendor }}
            </sky-description-list-description>
          </sky-description-list-content>
          <sky-description-list-content>
            <sky-description-list-term>
              Receipt image
            </sky-description-list-term>
            <sky-description-list-description>
              {{ activeRecord.receiptImage }}
            </sky-description-list-description>
          </sky-description-list-content>
        </sky-description-list>
        <div>
          <sky-input-box stacked="true" labelText="Approved amount">
            <input
              formControlName="approvedAmount"
              name="approvedAmount"
              type="text"
            />
          </sky-input-box>
        </div>

        <div>
          <sky-input-box stacked="true" labelText="Comments">
            <textarea formControlName="comments" name="comments"></textarea>
          </sky-input-box>
        </div>
      </form>
    </sky-split-view-workspace-content>
    <sky-split-view-workspace-footer>
      <sky-summary-action-bar>
        <sky-summary-action-bar-actions>
          <sky-summary-action-bar-primary-action (actionClick)="onApprove()">
            Approve expense
          </sky-summary-action-bar-primary-action>
          <sky-summary-action-bar-secondary-actions>
            <sky-summary-action-bar-secondary-action (actionClick)="onDeny()">
              Deny expense
            </sky-summary-action-bar-secondary-action>
          </sky-summary-action-bar-secondary-actions>
        </sky-summary-action-bar-actions>
      </sky-summary-action-bar>
    </sky-split-view-workspace-footer>
  </sky-split-view-workspace>
</sky-split-view>

```

---

## Split view with basic setup

**Component:** SplitViewBasicExampleComponent

**Selector:** `app-split-view-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkySummaryActionBarModule } from '@skyux/action-bars';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyDescriptionListModule } from '@skyux/layout';
import { SkyRepeaterModule } from '@skyux/lists';
import { SkyConfirmService, SkyConfirmType } from '@skyux/modals';
import {
  SkySplitViewMessage,
  SkySplitViewMessageType,
  SkySplitViewModule,
} from '@skyux/split-view';

import { Subject } from 'rxjs';

import { Record } from './record';

interface DemoForm {
  approvedAmount: FormControl<number>;
  comments: FormControl<string>;
}

/**
 * @title Split view with basic setup
 * @docsDemoHidden
 */
@Component({
  selector: 'app-split-view-basic-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyDescriptionListModule,
    SkyInputBoxModule,
    SkyRepeaterModule,
    SkySplitViewModule,
    SkySummaryActionBarModule,
  ],
})
export class SplitViewBasicExampleComponent {
  protected set activeIndex(value: number) {
    this.#_activeIndex = value;
    this.activeRecord = this.items[this.#_activeIndex];
    this.#loadFormGroup(this.activeRecord);
  }

  protected get activeIndex(): number {
    return this.#_activeIndex;
  }

  protected items = [
    {
      id: 1,
      amount: 73.19,
      date: '5/13/2020',
      vendor: 'amazon.com',
      receiptImage: 'amzn-office-supply-order-5-13-19.png',
      approvedAmount: 73.19,
      comments: '',
    },
    {
      id: 2,
      amount: 214.12,
      date: '5/14/2020',
      vendor: 'Office Max',
      receiptImage: 'office-max-order.png',
      approvedAmount: 214.12,
      comments: '',
    },
    {
      id: 3,
      amount: 29.99,
      date: '5/14/2020',
      vendor: 'amazon.com',
      receiptImage: 'amzn-office-supply-order-5-14-19.png',
      approvedAmount: 29.99,
      comments: '',
    },
    {
      id: 4,
      amount: 1500,
      date: '5/15/2020',
      vendor: 'Fresh Catering, LLC',
      receiptImage: 'fresh-catering-llc-order.png',
      approvedAmount: 1500,
      comments: '',
    },
  ];

  protected activeRecord: Record;
  protected splitViewDemoForm: FormGroup<DemoForm>;
  protected splitViewStream = new Subject<SkySplitViewMessage>();

  #_activeIndex = 0;

  readonly #confirmSvc = inject(SkyConfirmService);

  constructor() {
    // Start with the first item selected.
    this.activeIndex = 0;
    this.activeRecord = this.items[this.activeIndex];

    this.splitViewDemoForm = new FormGroup({
      approvedAmount: new FormControl(this.activeRecord.approvedAmount, {
        nonNullable: true,
      }),
      comments: new FormControl(this.activeRecord.comments, {
        nonNullable: true,
      }),
    });
  }

  protected onItemClick(index: number): void {
    // Prevent workspace from loading new data if the current workspace form is dirty.
    if (this.splitViewDemoForm.dirty && index !== this.activeIndex) {
      this.#openConfirmModal(index);
    } else {
      this.#loadWorkspace(index);
    }
  }

  protected onApprove(): void {
    console.log('Approved clicked!');
    this.#saveForm();
  }

  protected onDeny(): void {
    console.log('Denied clicked!');
  }

  #loadFormGroup(record: Record): void {
    this.splitViewDemoForm = new FormGroup({
      approvedAmount: new FormControl(record.approvedAmount, {
        nonNullable: true,
      }),
      comments: new FormControl(record.comments, { nonNullable: true }),
    });
  }

  #loadWorkspace(index: number): void {
    this.activeIndex = index;
    this.#setFocusInWorkspace();
  }

  #openConfirmModal(index: number): void {
    this.#confirmSvc
      .open({
        message:
          'You have unsaved work. Would you like to save it before you change records?',
        type: SkyConfirmType.Custom,
        buttons: [
          {
            action: 'yes',
            text: 'Yes',
            styleType: 'primary',
          },
          {
            action: 'discard',
            text: 'Discard changes',
            styleType: 'link',
          },
        ],
      })
      .closed.subscribe((closeArgs) => {
        if (closeArgs.action.toLowerCase() === 'yes') {
          this.#saveForm();
        }

        this.#loadWorkspace(index);
      });
  }

  #saveForm(): void {
    this.activeRecord.approvedAmount =
      this.splitViewDemoForm.value.approvedAmount ?? 0;
    this.activeRecord.comments = this.splitViewDemoForm.value.comments ?? '';

    this.splitViewDemoForm.reset(this.splitViewDemoForm.value);
  }

  #setFocusInWorkspace(): void {
    const message: SkySplitViewMessage = {
      type: SkySplitViewMessageType.FocusWorkspace,
    };
    this.splitViewStream.next(message);
  }
}

```

#### record.ts

```typescript
export interface Record {
  id: number;
  amount: number;
  date: string;
  vendor: string;
  receiptImage: string;
  approvedAmount: number;
  comments: string;
}

```

#### example.component.html

```html
<sky-split-view [messageStream]="splitViewStream">
  <sky-split-view-drawer [ariaLabel]="'Transaction list'">
    <sky-repeater [activeIndex]="activeIndex">
      @for (item of items; track item; let i = $index) {
        <sky-repeater-item
          (click)="onItemClick(i)"
          (keyup.enter)="onItemClick(i)"
        >
          <sky-repeater-item-content>
            {{ item.amount }} <br />
            {{ item.date }} <br />
            {{ item.vendor }}
          </sky-repeater-item-content>
        </sky-repeater-item>
      }
    </sky-repeater>
  </sky-split-view-drawer>

  <sky-split-view-workspace ariaLabel="Transaction form">
    <sky-split-view-workspace-content class="sky-padding-even-xl">
      <form [formGroup]="splitViewDemoForm" (ngSubmit)="onApprove()">
        <sky-description-list labelWidth="150px">
          <sky-description-list-content>
            <sky-description-list-term>
              Receipt amount
            </sky-description-list-term>
            <sky-description-list-description>
              {{ activeRecord.amount }}
            </sky-description-list-description>
          </sky-description-list-content>
          <sky-description-list-content>
            <sky-description-list-term> Date </sky-description-list-term>
            <sky-description-list-description>
              {{ activeRecord.date }}
            </sky-description-list-description>
          </sky-description-list-content>
          <sky-description-list-content>
            <sky-description-list-term> Vendor </sky-description-list-term>
            <sky-description-list-description>
              {{ activeRecord.vendor }}
            </sky-description-list-description>
          </sky-description-list-content>
          <sky-description-list-content>
            <sky-description-list-term>
              Receipt image
            </sky-description-list-term>
            <sky-description-list-description>
              {{ activeRecord.receiptImage }}
            </sky-description-list-description>
          </sky-description-list-content>
        </sky-description-list>
        <sky-input-box labelText="Approved amount" stacked="true">
          <input formControlName="approvedAmount" type="text" />
        </sky-input-box>
        <sky-input-box labelText="Comments">
          <textarea formControlName="comments"></textarea>
        </sky-input-box>
      </form>
    </sky-split-view-workspace-content>
    <sky-split-view-workspace-footer>
      <sky-summary-action-bar>
        <sky-summary-action-bar-actions>
          <sky-summary-action-bar-primary-action (actionClick)="onApprove()">
            Approve expense
          </sky-summary-action-bar-primary-action>
          <sky-summary-action-bar-secondary-actions>
            <sky-summary-action-bar-secondary-action (actionClick)="onDeny()">
              Deny expense
            </sky-summary-action-bar-secondary-action>
          </sky-summary-action-bar-secondary-actions>
        </sky-summary-action-bar-actions>
      </sky-summary-action-bar>
    </sky-split-view-workspace-footer>
  </sky-split-view-workspace>
</sky-split-view>

```

---

## Page bound split view in a page component with fit layout

**Component:** SplitViewPageBoundExampleComponent

**Selector:** `app-split-view-page-bound-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import {
  SkyMediaQueryTestingController,
  provideSkyMediaQueryTesting,
} from '@skyux/core/testing';
import { SkyInputBoxHarness } from '@skyux/forms/testing';
import { SkyRepeaterItemHarness } from '@skyux/lists/testing';
import { SkySplitViewHarness } from '@skyux/split-view/testing';

import { SplitViewPageBoundExampleComponent } from './example.component';

describe('Split view example', () => {
  async function setupTest(options: { dataSkyId?: string } = {}): Promise<{
    splitViewHarness: SkySplitViewHarness;
    mediaQueryController: SkyMediaQueryTestingController;
    fixture: ComponentFixture<SplitViewPageBoundExampleComponent>;
    loader: HarnessLoader;
  }> {
    await TestBed.configureTestingModule({
      imports: [SplitViewPageBoundExampleComponent, NoopAnimationsModule],
      providers: [provideSkyMediaQueryTesting()],
    }).compileComponents();

    const mediaQueryController = TestBed.inject(SkyMediaQueryTestingController);

    const fixture = TestBed.createComponent(SplitViewPageBoundExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const splitViewHarness: SkySplitViewHarness = options.dataSkyId
      ? await loader.getHarness(
          SkySplitViewHarness.with({ dataSkyId: options.dataSkyId }),
        )
      : await loader.getHarness(SkySplitViewHarness);

    return { splitViewHarness, mediaQueryController, fixture, loader };
  }

  it('should set up split view component and children', async () => {
    const { splitViewHarness, fixture } = await setupTest();
    fixture.detectChanges();
    await fixture.whenStable();

    // validate parent split view properties
    await expectAsync(splitViewHarness.getDockType()).toBeResolvedTo('fill');
    await expectAsync(splitViewHarness.getDrawerIsVisible()).toBeResolvedTo(
      true,
    );
    await expectAsync(splitViewHarness.getWorkspaceIsVisible()).toBeResolvedTo(
      true,
    );

    // query for drawer and workspace child components and validate properties
    const drawerHarness = await splitViewHarness.getDrawer();
    const workspaceHarness = await splitViewHarness.getWorkspace();

    await expectAsync(drawerHarness.getAriaLabel()).toBeResolvedTo(
      'Transaction list',
    );
    await expectAsync(workspaceHarness.getAriaLabel()).toBeResolvedTo(
      'Transaction form',
    );

    // query for content and footer child components and their child elements
    const contentHarness = await workspaceHarness.getContent();
    const footerHarness = await workspaceHarness.getFooter();

    await expectAsync(
      contentHarness?.queryHarnesses(SkyInputBoxHarness),
    ).toBeResolved();
    await expectAsync(
      footerHarness?.querySelector('sky-summary-action-bar-primary-action'),
    ).toBeResolved();
  });

  it('should switch between views in responsive mode', async () => {
    const { splitViewHarness, mediaQueryController, fixture } =
      await setupTest();

    // set XS breakpoint to force split view into responsive mode
    mediaQueryController.setBreakpoint('xs');

    fixture.detectChanges();
    await fixture.whenStable();

    await expectAsync(splitViewHarness.getDrawerIsVisible()).toBeResolvedTo(
      false,
    );
    await expectAsync(splitViewHarness.getWorkspaceIsVisible()).toBeResolvedTo(
      true,
    );
    await expectAsync(splitViewHarness.getBackButtonText()).toBeResolvedTo(
      'Back to list',
    );

    // switch to drawer view
    await splitViewHarness.openDrawer();

    fixture.detectChanges();
    await fixture.whenStable();

    await expectAsync(splitViewHarness.getDrawerIsVisible()).toBeResolvedTo(
      true,
    );
    await expectAsync(splitViewHarness.getWorkspaceIsVisible()).toBeResolvedTo(
      false,
    );

    const drawerHarness = await splitViewHarness.getDrawer();
    const drawerItems = await drawerHarness.queryHarnesses(
      SkyRepeaterItemHarness,
    );

    // switch back to workspace view
    await drawerItems[3].click();

    fixture.detectChanges();
    await fixture.whenStable();

    await expectAsync(splitViewHarness.getDrawerIsVisible()).toBeResolvedTo(
      false,
    );
    await expectAsync(splitViewHarness.getWorkspaceIsVisible()).toBeResolvedTo(
      true,
    );
  });
});

```

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkySummaryActionBarModule } from '@skyux/action-bars';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyAlertModule } from '@skyux/indicators';
import { SkyDescriptionListModule, SkyPageSummaryModule } from '@skyux/layout';
import { SkyRepeaterModule } from '@skyux/lists';
import { SkyConfirmService, SkyConfirmType } from '@skyux/modals';
import { SkyPageModule } from '@skyux/pages';
import {
  SkySplitViewMessage,
  SkySplitViewMessageType,
  SkySplitViewModule,
} from '@skyux/split-view';

import { Subject } from 'rxjs';

import { Record } from './record';

interface DemoForm {
  approvedAmount: FormControl<number>;
  comments: FormControl<string>;
}

/**
 * @title Page bound split view in a page component with fit layout
 * @docsDemoHidden
 */
@Component({
  selector: 'app-split-view-page-bound-example',
  templateUrl: './example.component.html',
  styleUrls: ['./example.component.scss'],
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyAlertModule,
    SkyDescriptionListModule,
    SkyInputBoxModule,
    SkyPageModule,
    SkyPageSummaryModule,
    SkyRepeaterModule,
    SkySplitViewModule,
    SkySummaryActionBarModule,
  ],
})
export class SplitViewPageBoundExampleComponent {
  protected set activeIndex(value: number) {
    this.#_activeIndex = value;
    this.activeRecord = this.items[this.#_activeIndex];
    this.#loadFormGroup(this.activeRecord);
  }

  protected get activeIndex(): number {
    return this.#_activeIndex;
  }

  protected items: Record[] = [
    {
      id: 1,
      amount: 73.19,
      date: '5/13/2020',
      vendor: 'amazon.com',
      receiptImage: 'amzn-office-supply-order-5-13-19.png',
      approvedAmount: 73.19,
      comments: '',
    },
    {
      id: 2,
      amount: 214.12,
      date: '5/14/2020',
      vendor: 'Office Max',
      receiptImage: 'office-max-order.png',
      approvedAmount: 214.12,
      comments: '',
    },
    {
      id: 3,
      amount: 29.99,
      date: '5/14/2020',
      vendor: 'amazon.com',
      receiptImage: 'amzn-office-supply-order-5-14-19.png',
      approvedAmount: 29.99,
      comments: '',
    },
    {
      id: 4,
      amount: 1500,
      date: '5/15/2020',
      vendor: 'Fresh Catering, LLC',
      receiptImage: 'fresh-catering-llc-order.png',
      approvedAmount: 1500,
      comments: '',
    },
    {
      id: 5,
      amount: 456.24,
      date: '5/16/2020',
      vendor: 'Wish',
      receiptImage: 'wish-delivery-order.png',
      approvedAmount: 456.24,
      comments: '',
    },
    {
      id: 6,
      amount: 62.37,
      date: '5/16/2020',
      vendor: 'Staples',
      receiptImage: 'staples-paper-bulk-order.png',
      approvedAmount: 62.37,
      comments: '',
    },
    {
      id: 7,
      amount: 51.84,
      date: '5/17/2020',
      vendor: 'amazon.com',
      receiptImage: 'amzn-office-supply-order-5-17-19.png',
      approvedAmount: 51.84,
      comments: '',
    },
    {
      id: 8,
      amount: 92.55,
      date: '5/18/2020',
      vendor: 'Home Depot',
      receiptImage: 'home-depot-order.png',
      approvedAmount: 0.0,
      comments: '',
    },
    {
      id: 9,
      amount: 38.29,
      date: '5/18/2020',
      vendor: 'Papa Johns',
      receiptImage: 'papa-johns-order.png',
      approvedAmount: 38.29,
      comments: '',
    },
  ];

  protected activeRecord: Record;
  protected splitViewDemoForm: FormGroup<DemoForm>;
  protected splitViewStream = new Subject<SkySplitViewMessage>();
  protected unapprovedTransaction = true;

  #_activeIndex = 0;

  readonly #confirmSvc = inject(SkyConfirmService);

  constructor() {
    // Start with the first item selected.
    this.activeIndex = 0;
    this.activeRecord = this.items[this.activeIndex];

    this.splitViewDemoForm = new FormGroup({
      approvedAmount: new FormControl(this.activeRecord.approvedAmount, {
        nonNullable: true,
      }),
      comments: new FormControl(this.activeRecord.comments, {
        nonNullable: true,
      }),
    });
  }

  protected onItemClick(index: number): void {
    // Prevent workspace from loading new data if the current workspace form is dirty.
    if (this.splitViewDemoForm.dirty && index !== this.activeIndex) {
      this.#openConfirmModal(index);
    } else {
      this.#loadWorkspace(index);
    }
  }

  protected onApprove(): void {
    console.log('Approved clicked!');
    this.#saveForm();
  }

  protected onDeny(): void {
    console.log('Denied clicked!');
  }

  #loadFormGroup(record: Record): void {
    this.splitViewDemoForm = new FormGroup({
      approvedAmount: new FormControl(record.approvedAmount, {
        nonNullable: true,
      }),
      comments: new FormControl(record.comments, { nonNullable: true }),
    });
  }

  #loadWorkspace(index: number): void {
    this.activeIndex = index;
    this.#setFocusInWorkspace();
  }

  #openConfirmModal(index: number): void {
    this.#confirmSvc
      .open({
        message:
          'You have unsaved work. Would you like to save it before you change records?',
        type: SkyConfirmType.Custom,
        buttons: [
          {
            action: 'yes',
            text: 'Yes',
            styleType: 'primary',
          },
          {
            action: 'discard',
            text: 'Discard changes',
            styleType: 'link',
          },
        ],
      })
      .closed.subscribe((closeArgs) => {
        if (closeArgs.action.toLowerCase() === 'yes') {
          this.#saveForm();
        }

        this.#loadWorkspace(index);
      });
  }

  #saveForm(): void {
    this.activeRecord.approvedAmount = parseFloat(
      `${this.splitViewDemoForm.value.approvedAmount ?? 0}`,
    );

    this.activeRecord.comments = this.splitViewDemoForm.value.comments ?? '';

    this.unapprovedTransaction =
      this.items.findIndex((item) => item.amount !== item.approvedAmount) >= 0;

    this.splitViewDemoForm.reset(this.splitViewDemoForm.value);
  }

  #setFocusInWorkspace(): void {
    const message: SkySplitViewMessage = {
      type: SkySplitViewMessageType.FocusWorkspace,
    };

    this.splitViewStream.next(message);
  }
}

```

#### record.ts

```typescript
export interface Record {
  id: number;
  amount: number;
  date: string;
  vendor: string;
  receiptImage: string;
  approvedAmount: number;
  comments: string;
}

```

#### example.component.html

```html
<sky-page layout="fit">
  <div class="page-flex">
    <div class="page-flex-header">
      <sky-page-summary>
        @if (unapprovedTransaction) {
          <sky-page-summary-alert>
            <sky-alert alertType="info"
              >There is an unapproved transaction.</sky-alert
            >
          </sky-page-summary-alert>
        }
        <sky-page-summary-title> SKY Developers, LLC </sky-page-summary-title>
        <sky-page-summary-subtitle>
          Petty Cash Transactions
        </sky-page-summary-subtitle>
        <sky-page-summary-content>
          The transactions below cover various operating expenses which do not
          fall under one of the budgets areas of expenditures.
        </sky-page-summary-content>
      </sky-page-summary>
    </div>
    <div class="page-flex-main">
      <sky-split-view dock="fill" [messageStream]="splitViewStream">
        <sky-split-view-drawer [ariaLabel]="'Transaction list'">
          <sky-repeater [activeIndex]="activeIndex">
            @for (item of items; track item; let i = $index) {
              <sky-repeater-item
                (click)="onItemClick(i)"
                (keyup.enter)="onItemClick(i)"
              >
                <sky-repeater-item-content>
                  {{ item.amount }} <br />
                  {{ item.date }} <br />
                  {{ item.vendor }}
                </sky-repeater-item-content>
              </sky-repeater-item>
            }
          </sky-repeater>
        </sky-split-view-drawer>

        <sky-split-view-workspace [ariaLabel]="'Transaction form'">
          <sky-split-view-workspace-content class="sky-padding-even-xl">
            <form [formGroup]="splitViewDemoForm" (ngSubmit)="onApprove()">
              <sky-description-list labelWidth="150px">
                <sky-description-list-content>
                  <sky-description-list-term>
                    Receipt amount
                  </sky-description-list-term>
                  <sky-description-list-description>
                    {{ activeRecord.amount }}
                  </sky-description-list-description>
                </sky-description-list-content>
                <sky-description-list-content>
                  <sky-description-list-term> Date </sky-description-list-term>
                  <sky-description-list-description>
                    {{ activeRecord.date }}
                  </sky-description-list-description>
                </sky-description-list-content>
                <sky-description-list-content>
                  <sky-description-list-term>
                    Vendor
                  </sky-description-list-term>
                  <sky-description-list-description>
                    {{ activeRecord.vendor }}
                  </sky-description-list-description>
                </sky-description-list-content>
                <sky-description-list-content>
                  <sky-description-list-term>
                    Receipt image
                  </sky-description-list-term>
                  <sky-description-list-description>
                    {{ activeRecord.receiptImage }}
                  </sky-description-list-description>
                </sky-description-list-content>
              </sky-description-list>
              <sky-input-box labelText="Approved amount" stacked="true">
                <input formControlName="approvedAmount" type="text" />
              </sky-input-box>
              <sky-input-box labelText="Comments">
                <textarea formControlName="comments"></textarea>
              </sky-input-box>
            </form>
          </sky-split-view-workspace-content>
          <sky-split-view-workspace-footer>
            <sky-summary-action-bar>
              <sky-summary-action-bar-actions>
                <sky-summary-action-bar-primary-action
                  (actionClick)="onApprove()"
                >
                  Approve expense
                </sky-summary-action-bar-primary-action>
                <sky-summary-action-bar-secondary-actions>
                  <sky-summary-action-bar-secondary-action
                    (actionClick)="onDeny()"
                  >
                    Deny expense
                  </sky-summary-action-bar-secondary-action>
                </sky-summary-action-bar-secondary-actions>
              </sky-summary-action-bar-actions>
            </sky-summary-action-bar>
          </sky-split-view-workspace-footer>
        </sky-split-view-workspace>
      </sky-split-view>
    </div>
  </div>
</sky-page>

```

#### example.component.scss

```css
.page-flex {
  display: flex;
  flex-direction: column;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}

.page-flex-header {
  flex-grow: 0;
}

.page-flex-main {
  flex-grow: 1;
  overflow: auto;
  /* Required for the split view to fill this element instead of the document */
  position: relative;
}

```

---