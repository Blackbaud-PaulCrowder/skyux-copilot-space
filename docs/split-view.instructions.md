---
component: 'split-view'
description: 'Design guidelines, API documentation, and usage instructions for the split-view component extracted from SKY UX documentation.'
---

# Split View Component Guidelines

## Component Overview
A split view displays a workspace beside a list to let users view details and take actions for the selected item.

## Usage

### ✅ Use when

Use split views when users need to work through a list of items with the intent of taking action on each item.

**✅ Do use split views when users take the same action for each item in the list.**

### ❌ Don't use when

Don't use split views when users are likely to interact with a small number of items in the list. Use regular lists instead, and follow the flyout guidelines to determine whether to use flyouts or navigate to selected records.

## Anatomy

### Large viewport

### Small viewport

- List panel
- Workspace panel
- Summary action bar

## Options

### List type

Repeaters are the most common list type because they enable flexible content layouts.

Tree views can be used when items are hierarchical. If items at different levels have different types, you can use multiple views in the workspace panel.

We recommend against using grids if possible. They do not scale well at the typically small width of the list.

**Use caution with grids because they do not perform well at narrow widths.**

### List manipulation

If users need to search for specific items in the list or show and hide items with certain statuses, include a search input or status checkbox filter in the list panel.

When possible, pre-filter the list to relevant items and pre-sort it to the expected useful order. If you can't predict how users will use the list, include a toolbar to let them add items or filter, sort, and search the list.

**Use caution when using a full toolbar with a split view. Automatically filter and sort the list when possible.**

## Behavior and states

### Automatically advance to the next item

If users are likely to work through the list sequentially, remove the selected item and automatically advance to the next item after users invoke the primary action in the workspace.

### Place focus in the workspace

When users select an item in the list, place focus on the first focusable element in the workspace so that users can start working immediately.

### Change panel width

Users can change the panel widths using drag-and-drop or keyboard interactions. If the list content is wider than the panel, a horizontal scrollbar appears.

### Responsiveness

In smaller viewports, the split view automatically switches from a side-by-side view to a panel-switching interaction where users switch between the list and the workspace.

## Content

### List item

Use up to three pieces of data to identify the item. If additional content is needed to uniquely identify the item, put it in the workspace view instead of overloading the list item.

## Layout

A split view should be the last item on a page. Do not place additional content below it.

**❌ Don't place content below the split view.**

## Related information

### Components

- Repeater
- Summary action bar

### Guidelines

- Form design
- Split view page

## API Documentation

### Components and Directives

#### PagesPageSplitViewPageFitLayoutExampleComponent

**Selector:** `app-pages-page-split-view-page-fit-layout-example`

**Package:** `@skyux/code-examples`

#### SplitViewBasicExampleComponent

**Selector:** `app-split-view-basic-example`

**Package:** `@skyux/code-examples`

#### SplitViewPageBoundExampleComponent

**Selector:** `app-split-view-page-bound-example`

**Package:** `@skyux/code-examples`

#### SkySplitViewDrawerComponent

Specifies the content to display in the split view's list panel.

**Selector:** `sky-split-view-drawer`

**Package:** `@skyux/split-view`

**Inputs:**

- `ariaLabel`: `string | undefined` - The ARIA label for the list panel. This sets the panel's `aria-label` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `width`: `number | undefined` - Sets the list panel's width in pixels. (default: 320)

#### SkySplitViewWorkspaceContentComponent

Specifies the content to display in the split view's workspace panel.

**Selector:** `sky-split-view-workspace-content`

**Package:** `@skyux/split-view`

#### SkySplitViewWorkspaceFooterComponent

Specifies the footer to display in the split view's workspace panel. This component is often used with a summary action bar.

**Selector:** `sky-split-view-workspace-footer`

**Package:** `@skyux/split-view`

#### SkySplitViewWorkspaceHeaderComponent

Specifies the header to display in the split view's workspace panel.

**Selector:** `sky-split-view-workspace-header`

**Package:** `@skyux/split-view`

#### SkySplitViewWorkspaceComponent

Contains the content, footer, and header to display in the split view's workspace panel.

**Selector:** `sky-split-view-workspace`

**Package:** `@skyux/split-view`

**Inputs:**

- `ariaLabel`: `string | undefined` - The ARIA label for the workspace panel. This sets the panel's `aria-label` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### SkySplitViewComponent

Displays a list alongside a workspace where users can view details for selected items
and take actions.

**Selector:** `sky-split-view`

**Package:** `@skyux/split-view`

**Inputs:**

- `messageStream`: `Subject<SkySplitViewMessage>` - The observable that sends commands to the split view component.
The commands should respect the `SkySplitViewMessage` type.
- `backButtonText`: `string` - The label for the button that appears in the workspace header in responsive mode.
The button returns users to the list. (default: "Back to list")
- `bindHeightToWindow`: `boolean` - Whether the split view's height is bound to the window height. (default: false)
- `dock`: `SkySplitViewDockType` - How the split view docks to its container. Use `fill` to dock
the split view to the container's size where the container is a `sky-page` component
with its `layout` input set to `fit`, or where the container is another element with
a relative or absolute position and a fixed size. (default: "none")

#### SkySplitViewModule

**Package:** `@skyux/split-view`

#### SkySplitViewDockType

**Package:** `@skyux/split-view`

#### SkySplitViewMessageType

**Package:** `@skyux/split-view`

#### SkySplitViewMessage

**Package:** `@skyux/split-view`

#### SkySplitViewDrawerHarness

Harness to interact with the split view drawer component in tests.

**Package:** `@skyux/split-view/testing`

#### SkySplitViewHarnessFilters

A set of criteria that can be used to filter a list of SkySplitViewHarness instances.

**Package:** `@skyux/split-view/testing`

#### SkySplitViewHarness

Harness for interacting with a split view component in tests.

**Package:** `@skyux/split-view/testing`

#### SkySplitViewWorkspaceContentHarness

Harness to interact with the split view workspace content component in tests.

**Package:** `@skyux/split-view/testing`

#### SkySplitViewWorkspaceFooterHarness

Harness to interact with the split view workspace footer component in tests.

**Package:** `@skyux/split-view/testing`

#### SkySplitViewWorkspaceHarness

Harness to interact with the split view workspace component in tests.

**Package:** `@skyux/split-view/testing`

### Code Examples

#### Split view page with fit layout

**Selector:** `app-pages-page-split-view-page-fit-layout-example`

**TypeScript:**

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

**Template:**

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

#### Split view with basic setup

**Selector:** `app-split-view-basic-example`

**TypeScript:**

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

**Template:**

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

#### Page bound split view in a page component with fit layout

**Selector:** `app-split-view-page-bound-example`

**TypeScript:**

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

**Template:**

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

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.