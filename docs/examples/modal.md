---
component: 'modal'
type: 'code-examples'
description: 'Code examples for the modal component.'
---

# Modal Code Examples

## Modal with summary action bar

**Component:** ActionBarsSummaryActionBarModalExampleComponent

**Selector:** `app-action-bars-summary-action-bar-modal-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { SkyModalService } from '@skyux/modals';

import { ModalComponent } from './modal.component';

/**
 * @title Modal with summary action bar
 */
@Component({
  standalone: true,
  selector: 'app-action-bars-summary-action-bar-modal-example',
  templateUrl: './example.component.html',
})
export class ActionBarsSummaryActionBarModalExampleComponent {
  readonly #modalSvc = inject(SkyModalService);

  protected openModal(): void {
    this.#modalSvc.open(ModalComponent, {
      size: 'large',
    });
  }
}

```

#### modal.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkySummaryActionBarHarness } from '@skyux/action-bars/testing';
import { SkyKeyInfoHarness } from '@skyux/indicators/testing';
import { SkyModalInstance } from '@skyux/modals';

import { ModalComponent } from './modal.component';

describe('Modal summary action bar example', () => {
  async function setupTest(): Promise<{
    harness: SkySummaryActionBarHarness;
    fixture: ComponentFixture<ModalComponent>;
  }> {
    const fixture = TestBed.createComponent(ModalComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkySummaryActionBarHarness.with({ dataSkyId: 'donation-summary' }),
    );

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [ModalComponent, NoopAnimationsModule],
      providers: [SkyModalInstance],
    });
  });

  it('should set up primary actions', async () => {
    const { harness, fixture } = await setupTest();

    const primaryActionHarness = await harness.getPrimaryAction();
    await expectAsync(primaryActionHarness.getText()).toBeResolvedTo(
      'Primary action',
    );

    const spy = spyOn(fixture.componentInstance, 'save');
    await primaryActionHarness.click();
    expect(spy).toHaveBeenCalled();
  });

  it('should set up secondary actions', async () => {
    const { harness, fixture } = await setupTest();

    const secondaryActions = await harness.getSecondaryActions();
    const actions = await secondaryActions.getActions();
    expect(actions.length).toBe(2);

    const spy1 = spyOn(fixture.componentInstance, 'onSecondaryActionClick');
    const spy2 = spyOn(fixture.componentInstance, 'onSecondaryAction2Click');

    await actions[1].click();
    expect(spy2).toHaveBeenCalled();

    const secondaryAction = await secondaryActions.getAction({
      dataSkyId: 'secondary-action',
    });
    await secondaryAction.click();
    expect(spy1).toHaveBeenCalled();
  });

  it('should set up the summary', async () => {
    const { harness } = await setupTest();

    const summary = await harness.getSummary();
    const keyInfos = await summary.queryHarnesses(SkyKeyInfoHarness);
    expect(keyInfos.length).toBe(3);
  });
});

```

#### modal.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { SkySummaryActionBarModule } from '@skyux/action-bars';
import { SkyKeyInfoModule } from '@skyux/indicators';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';

@Component({
  selector: 'app-modal',
  templateUrl: './modal.component.html',
  imports: [SkyKeyInfoModule, SkyModalModule, SkySummaryActionBarModule],
})
export class ModalComponent {
  readonly #modalInstance = inject(SkyModalInstance);

  public onSecondaryActionClick(): void {
    alert('Secondary action button clicked.');
  }

  public onSecondaryAction2Click(): void {
    alert('Secondary action 2 button clicked.');
  }

  protected cancel(): void {
    this.#modalInstance.cancel();
  }

  public save(): void {
    this.#modalInstance.save();
  }
}

```

#### example.component.html

```html
<button class="sky-btn sky-btn-primary" type="button" (click)="openModal()">
  Open modal
</button>

```

#### modal.component.html

```html
<sky-modal headingText="Modal with summary action bar">
  <sky-modal-content> Hello world! </sky-modal-content>
  <sky-modal-footer>
    <sky-summary-action-bar data-sky-id="donation-summary">
      <sky-summary-action-bar-actions>
        <sky-summary-action-bar-primary-action (actionClick)="save()">
          Primary action
        </sky-summary-action-bar-primary-action>
        <sky-summary-action-bar-secondary-actions>
          <sky-summary-action-bar-secondary-action
            data-sky-id="secondary-action"
            (actionClick)="onSecondaryActionClick()"
          >
            Secondary action
          </sky-summary-action-bar-secondary-action>
          <sky-summary-action-bar-secondary-action
            data-sky-id="secondary-action-2"
            (actionClick)="onSecondaryAction2Click()"
          >
            Secondary action 2
          </sky-summary-action-bar-secondary-action>
        </sky-summary-action-bar-secondary-actions>
        <sky-summary-action-bar-cancel (actionClick)="cancel()">
          Cancel
        </sky-summary-action-bar-cancel>
      </sky-summary-action-bar-actions>
      <sky-summary-action-bar-summary>
        <sky-key-info>
          <sky-key-info-value>$250</sky-key-info-value>
          <sky-key-info-label>Given this month</sky-key-info-label>
        </sky-key-info>
        <sky-key-info>
          <sky-key-info-value>$1,000</sky-key-info-value>
          <sky-key-info-label>Given this year</sky-key-info-label>
        </sky-key-info>
        <sky-key-info>
          <sky-key-info-value>$1,300</sky-key-info-value>
          <sky-key-info-label>Given all time</sky-key-info-label>
        </sky-key-info>
      </sky-summary-action-bar-summary>
    </sky-summary-action-bar>
  </sky-modal-footer>
</sky-modal>

```

---

## Show an error inside a modal

**Component:** ErrorsErrorModalExampleComponent

**Selector:** `app-errors-error-modal-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { SkyErrorModalService } from '@skyux/errors';

/**
 * @title Show an error inside a modal
 */
@Component({
  standalone: true,
  selector: 'app-errors-error-modal-example',
  templateUrl: './example.component.html',
})
export class ErrorsErrorModalExampleComponent {
  readonly #errorSvc = inject(SkyErrorModalService);

  public openErrorModal(): void {
    this.#errorSvc.open({
      errorTitle: 'Something went wrong.',
      errorDescription: 'Close the modal, and come back later.',
      errorCloseText: 'Close',
    });
  }
}

```

#### example.component.html

```html
<button
  class="sky-btn sky-btn-default"
  type="button"
  (click)="openErrorModal()"
>
  Open error modal
</button>

```

---

## Text expand with a modal

**Component:** LayoutTextExpandModalExampleComponent

**Selector:** `app-layout-text-expand-modal-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyTextExpandHarness } from '@skyux/layout/testing';

import { LayoutTextExpandModalExampleComponent } from './example.component';

describe('Text expand modal example', () => {
  async function setupTest(
    options: {
      dataSkyId?: string;
    } = {},
  ): Promise<{
    textExpandHarness: SkyTextExpandHarness;
  }> {
    await TestBed.configureTestingModule({
      imports: [LayoutTextExpandModalExampleComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      LayoutTextExpandModalExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const textExpandHarness: SkyTextExpandHarness = options.dataSkyId
      ? await loader.getHarness(
          SkyTextExpandHarness.with({
            dataSkyId: options.dataSkyId,
          }),
        )
      : await loader.getHarness(SkyTextExpandHarness);

    return { textExpandHarness };
  }

  it('should open and close the text expand modal', async () => {
    const { textExpandHarness } = await setupTest();

    await expectAsync(textExpandHarness.textExpandsToModal()).toBeResolvedTo(
      true,
    );
    await expectAsync(textExpandHarness.isExpanded()).toBeResolvedTo(false);

    await textExpandHarness.clickExpandCollapseButton();
    const modal = await textExpandHarness.getExpandedViewModal();

    await expectAsync(modal.getText()).toBeResolvedTo(
      'The text expand component truncates long blocks of text with an ellipsis and a link to expand the text. Users select the link to expand the full text inline unless it exceeds limits on text characters or newline characters. If the text exceeds those limits, then it expands in a modal view instead. The component does not truncate text that is shorter than a specified threshold, and by default, it removes newline characters from truncated text.',
    );
    await expectAsync(modal.getExpandModalTitle()).toBeResolvedTo(
      'Expanded view',
    );
    await expectAsync(textExpandHarness.isExpanded()).toBeResolvedTo(true);

    await modal.clickCloseButton();

    await expectAsync(
      textExpandHarness.getExpandedViewModal(),
    ).toBeRejectedWithError('Could not find text expand modal.');
    await expectAsync(textExpandHarness.isExpanded()).toBeResolvedTo(false);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyTextExpandModule } from '@skyux/layout';

/**
 * @title Text expand with a modal
 */
@Component({
  selector: 'app-layout-text-expand-modal-example',
  templateUrl: './example.component.html',
  imports: [SkyTextExpandModule],
})
export class LayoutTextExpandModalExampleComponent {
  protected longText =
    'The text expand component truncates long blocks of text with an ellipsis and a link to expand the text. Users select the link to expand the full text inline unless it exceeds limits on text characters or newline characters. If the text exceeds those limits, then it expands in a modal view instead. The component does not truncate text that is shorter than a specified threshold, and by default, it removes newline characters from truncated text.';
}

```

#### example.component.html

```html
<sky-text-expand [text]="longText" [maxExpandedLength]="100" />

```

---

## Modal filter

**Component:** ListsFilterModalExampleComponent

**Selector:** `app-lists-filter-modal-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import {
  SkyFilterButtonHarness,
  SkyFilterSummaryHarness,
} from '@skyux/lists/testing';
import {
  SkyModalTestingController,
  SkyModalTestingModule,
} from '@skyux/modals/testing';

import { ListsFilterModalExampleComponent } from './example.component';
import { Filter } from './filter';
import { FilterModalComponent } from './filter-modal.component';

describe('Filter modal example', () => {
  async function setupTest(
    options: {
      dataSkyId?: string;
    } = {},
  ): Promise<{
    filterButtonHarness: SkyFilterButtonHarness;
    fixture: ComponentFixture<ListsFilterModalExampleComponent>;
    loader: HarnessLoader;
  }> {
    await TestBed.configureTestingModule({
      imports: [
        ListsFilterModalExampleComponent,
        SkyModalTestingModule,
        NoopAnimationsModule,
      ],
    }).compileComponents();

    const fixture = TestBed.createComponent(ListsFilterModalExampleComponent);
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const filterButtonHarness: SkyFilterButtonHarness = options.dataSkyId
      ? await loader.getHarness(
          SkyFilterButtonHarness.with({
            dataSkyId: options.dataSkyId,
          }),
        )
      : await loader.getHarness(SkyFilterButtonHarness);

    return { filterButtonHarness, fixture, loader };
  }

  it('should set up the component', async () => {
    const { filterButtonHarness, fixture, loader } = await setupTest({
      dataSkyId: 'my-filter-button',
    });

    const modalController = TestBed.inject(SkyModalTestingController);

    await filterButtonHarness.clickFilterButton();
    fixture.detectChanges();
    await fixture.whenStable();

    const saveData: Filter[] = [
      {
        name: 'fruitType',
        value: 'citrus',
        label: 'citrus',
      },
      {
        name: 'hideOrange',
        value: true,
        label: 'hide orange fruits',
      },
    ];
    modalController.expectCount(1);
    modalController.expectOpen(FilterModalComponent);
    modalController.closeTopModal({ data: saveData, reason: 'save' });

    const filterSummaryHarness = await loader.getHarness(
      SkyFilterSummaryHarness.with({ dataSkyId: 'filter-summary' }),
    );

    let filterSummaryItemHarnesses = await filterSummaryHarness.getItems();

    expect(filterSummaryItemHarnesses.length).toBe(2);

    await filterSummaryItemHarnesses[0].dismiss();

    filterSummaryItemHarnesses = await filterSummaryHarness.getItems();

    expect(filterSummaryItemHarnesses.length).toBe(1);
  });
});

```

#### example.component.ts

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  inject,
} from '@angular/core';
import { SkyToolbarModule } from '@skyux/layout';
import { SkyFilterModule, SkyRepeaterModule } from '@skyux/lists';
import { SkyModalCloseArgs, SkyModalService } from '@skyux/modals';

import { Filter } from './filter';
import { FilterModalContext } from './filter-modal-context';
import { FilterModalComponent } from './filter-modal.component';
import { Fruit } from './fruit';

/**
 * @title Modal filter
 */
@Component({
  selector: 'app-lists-filter-modal-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [SkyFilterModule, SkyRepeaterModule, SkyToolbarModule],
})
export class ListsFilterModalExampleComponent {
  protected appliedFilters: Filter[] = [];
  protected filteredItems: Fruit[];
  protected items: Fruit[] = [
    {
      name: 'Orange',
      type: 'citrus',
      color: 'orange',
    },
    {
      name: 'Mango',
      type: 'other',
      color: 'orange',
    },
    {
      name: 'Lime',
      type: 'citrus',
      color: 'green',
    },
    {
      name: 'Strawberry',
      type: 'berry',
      color: 'red',
    },
    {
      name: 'Blueberry',
      type: 'berry',
      color: 'blue',
    },
  ];

  protected showInlineFilters = false;

  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #modalSvc = inject(SkyModalService);

  constructor() {
    this.filteredItems = this.items.slice();
  }

  protected onDismiss(index: number): void {
    this.appliedFilters.splice(index, 1);
    this.filteredItems = this.#filterItems(this.items, this.appliedFilters);
  }

  protected onInlineFilterButtonClicked(): void {
    this.showInlineFilters = !this.showInlineFilters;
  }

  protected onModalFilterButtonClick(): void {
    const modalInstance = this.#modalSvc.open(FilterModalComponent, [
      {
        provide: FilterModalContext,
        useValue: {
          appliedFilters: this.appliedFilters,
        },
      },
    ]);

    modalInstance.closed.subscribe((result: SkyModalCloseArgs) => {
      if (result.reason === 'save') {
        this.appliedFilters = (result.data as Filter[]).slice();
        this.filteredItems = this.#filterItems(this.items, this.appliedFilters);
        this.#changeDetectorRef.markForCheck();
      }
    });
  }

  #fruitTypeFilterFailed(filter: Filter, item: Fruit): boolean {
    return (
      filter.name === 'fruitType' &&
      filter.value !== 'any' &&
      filter.value !== item.type
    );
  }

  #itemIsShown(filters: Filter[], item: Fruit): boolean {
    let passesFilter = true,
      j: number;

    for (j = 0; j < filters.length; j++) {
      if (this.#orangeFilterFailed(filters[j], item)) {
        passesFilter = false;
      } else if (this.#fruitTypeFilterFailed(filters[j], item)) {
        passesFilter = false;
      }
    }

    return passesFilter;
  }

  #filterItems(items: Fruit[], filters: Filter[]): Fruit[] {
    let i: number, passesFilter: boolean;
    const result: Fruit[] = [];

    for (i = 0; i < items.length; i++) {
      passesFilter = this.#itemIsShown(filters, items[i]);
      if (passesFilter) {
        result.push(items[i]);
      }
    }

    return result;
  }

  #orangeFilterFailed(filter: Filter, item: Fruit): boolean {
    return (
      filter.name === 'hideOrange' && !!filter.value && item.color === 'orange'
    );
  }
}

```

#### filter-modal-context.ts

```typescript
import { Filter } from './filter';

export class FilterModalContext {
  public appliedFilters: Filter[] = [];
}

```

#### filter-modal.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { FormsModule } from '@angular/forms';
import { SkyCheckboxModule, SkyInputBoxModule } from '@skyux/forms';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';

import { Filter } from './filter';
import { FilterModalContext } from './filter-modal-context';

@Component({
  selector: 'app-filter-modal',
  templateUrl: './filter-modal.component.html',
  imports: [FormsModule, SkyCheckboxModule, SkyInputBoxModule, SkyModalModule],
})
export class FilterModalComponent {
  protected hideOrange = false;
  protected fruitType = 'any';

  protected readonly context = inject(FilterModalContext);
  protected readonly instance = inject(SkyModalInstance);

  constructor() {
    if (this.context.appliedFilters.length > 0) {
      this.#setFormFilters(this.context.appliedFilters);
    } else {
      this.clearAllFilters();
    }
  }

  protected applyFilters(): void {
    const result = this.#getAppliedFiltersArray();
    this.instance.save(result);
  }

  protected cancel(): void {
    this.instance.cancel();
  }

  protected clearAllFilters(): void {
    this.hideOrange = false;
    this.fruitType = 'any';
  }

  #getAppliedFiltersArray(): Filter[] {
    const appliedFilters: Filter[] = [];

    if (this.fruitType !== 'any') {
      appliedFilters.push({
        name: 'fruitType',
        value: this.fruitType,
        label: this.fruitType,
      });
    }

    if (this.hideOrange) {
      appliedFilters.push({
        name: 'hideOrange',
        value: true,
        label: 'hide orange fruits',
      });
    }

    return appliedFilters;
  }

  #setFormFilters(appliedFilters: Filter[]): void {
    for (const appliedFilter of appliedFilters) {
      if (appliedFilter.name === 'fruitType') {
        this.fruitType = `${appliedFilter.value}`;
      }

      if (appliedFilter.name === 'hideOrange') {
        this.hideOrange = !!appliedFilter.value;
      }
    }
  }
}

```

#### filter.ts

```typescript
export interface Filter {
  name: string;
  value: string | boolean;
  label: string;
}

```

#### fruit.ts

```typescript
export interface Fruit {
  name: string;
  type: string;
  color: string;
}

```

#### example.component.html

```html
<sky-toolbar>
  <sky-toolbar-section>
    <sky-toolbar-item>
      <sky-filter-button
        data-sky-id="my-filter-button"
        [showButtonText]="true"
        (filterButtonClick)="onModalFilterButtonClick()"
      />
    </sky-toolbar-item>
  </sky-toolbar-section>
  @if (appliedFilters && appliedFilters.length > 0) {
    <sky-toolbar-section>
      <sky-filter-summary data-sky-id="filter-summary">
        @for (item of appliedFilters; track item; let i = $index) {
          <sky-filter-summary-item (dismiss)="onDismiss(i)">
            {{ item.label }}
          </sky-filter-summary-item>
        }
      </sky-filter-summary>
    </sky-toolbar-section>
  }
</sky-toolbar>
<sky-repeater expandMode="none">
  @for (item of filteredItems; track item) {
    <sky-repeater-item>
      <sky-repeater-item-title>
        {{ item.name }}
      </sky-repeater-item-title>
    </sky-repeater-item>
  }
</sky-repeater>

```

#### filter-modal.component.html

```html
<sky-modal headingText="Filter food preferences">
  <sky-modal-content>
    <sky-input-box labelText="Fruit type" stacked="true">
      <select [(ngModel)]="fruitType">
        <option value="any">Any fruit</option>
        <option value="citrus">Citrus</option>
        <option value="berry">Berry</option>
      </select>
    </sky-input-box>
    <sky-checkbox labelText="Hide orange fruits" [(ngModel)]="hideOrange" />
  </sky-modal-content>
  <sky-modal-footer>
    <button
      class="sky-btn sky-btn-primary"
      type="button"
      (click)="applyFilters()"
    >
      Apply
    </button>
    <button
      class="sky-btn sky-btn-link"
      type="button"
      (click)="clearAllFilters()"
    >
      Clear
    </button>
    <button class="sky-btn sky-btn-link" type="button" (click)="cancel()">
      Cancel
    </button>
  </sky-modal-footer>
</sky-modal>

```

---

## Selection modal with add item functionality

**Component:** LookupSelectionModalAddItemExampleComponent

**Selector:** `app-lookup-selection-modal-add-item-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### add-item-modal.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormGroup,
  ReactiveFormsModule,
  Validators,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';

let nextId = 21;

@Component({
  selector: 'app-add-item-modal',
  templateUrl: './add-item-modal.component.html',
  imports: [ReactiveFormsModule, SkyInputBoxModule, SkyModalModule],
})
export class AddItemModalComponent {
  protected readonly formGroup: FormGroup;

  readonly #modal = inject(SkyModalInstance);

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      id: [`${nextId++}`],
      name: ['', Validators.required],
    });
  }

  protected close(): void {
    this.#modal.close();
  }

  protected save(): void {
    if (this.formGroup.valid) {
      this.#modal.close(this.formGroup.value, 'save');
    } else {
      this.formGroup.markAllAsTouched();
    }
  }
}

```

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkySelectionModalHarness } from '@skyux/lookup/testing';

import { of } from 'rxjs';

import { LookupSelectionModalAddItemExampleComponent } from './example.component';
import { ExampleService } from './example.service';

describe('Selection modal example', () => {
  let mockSvc: jasmine.SpyObj<ExampleService>;

  async function setupTest(): Promise<{
    harness: SkySelectionModalHarness;
    el: HTMLElement;
    fixture: ComponentFixture<LookupSelectionModalAddItemExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      LookupSelectionModalAddItemExampleComponent,
    );
    const el = fixture.nativeElement as HTMLElement;

    const openBtn = el.querySelector<HTMLButtonElement>(
      '.selection-modal-example-show-btn',
    );

    openBtn?.click();
    fixture.detectChanges();

    const rootLoader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const harness = await rootLoader.getHarness(SkySelectionModalHarness);
    return { harness, el, fixture };
  }

  beforeEach(() => {
    // Create a mock search service. In a real-world application, the search
    // service would make a web request which should be avoided in unit tests.
    mockSvc = jasmine.createSpyObj<ExampleService>('ExampleService', [
      'search',
    ]);

    mockSvc.search.and.callFake((searchText) => {
      return of({
        hasMore: false,
        people:
          searchText === 'ra'
            ? [
                {
                  id: '1',
                  name: 'Rachel',
                },
              ]
            : [],
        totalCount: 1,
      });
    });

    TestBed.configureTestingModule({
      imports: [
        LookupSelectionModalAddItemExampleComponent,
        NoopAnimationsModule,
      ],
      providers: [{ provide: ExampleService, useValue: mockSvc }],
    });
  });

  it('should update the selected items list when an item is selected', async () => {
    const { harness, el } = await setupTest();

    await harness.enterSearchText('ra');
    await harness.selectSearchResult({
      contentText: 'Rachel',
    });
    await harness.saveAndClose();

    const selectedItemEls = el.querySelectorAll<HTMLLIElement>(
      '.selection-modal-example-selected li',
    );

    expect(selectedItemEls).toHaveSize(1);
    expect(selectedItemEls[0].innerText.trim()).toBe('Rachel');
  });

  it('should not update the selected items list when the user cancels the selection modal', async () => {
    const { harness, el } = await setupTest();

    await harness.enterSearchText('ra');
    await harness.selectSearchResult({
      contentText: 'Rachel',
    });
    await harness.cancel();

    const selectedItemEls = el.querySelectorAll<HTMLLIElement>(
      '.selection-modal-example-selected li',
    );

    expect(selectedItemEls).toHaveSize(0);
  });

  it('should respect the selection descriptor', async () => {
    const { harness } = await setupTest();

    await expectAsync(harness.getSearchAriaLabel()).toBeResolvedTo(
      'Search person',
    );
    await expectAsync(harness.getSaveButtonAriaLabel()).toBeResolvedTo(
      'Select person',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component, OnDestroy, inject } from '@angular/core';
import {
  SkySelectionModalAddClickEventArgs,
  SkySelectionModalCloseArgs,
  SkySelectionModalSearchResult,
  SkySelectionModalService,
} from '@skyux/lookup';
import { SkyModalService } from '@skyux/modals';

import { Subscription } from 'rxjs';
import { map } from 'rxjs/operators';

import { AddItemModalComponent } from './add-item-modal.component';
import { ExampleService } from './example.service';
import { Person } from './person';

/**
 * @title Selection modal with add item functionality
 */
@Component({
  standalone: true,
  selector: 'app-lookup-selection-modal-add-item-example',
  templateUrl: './example.component.html',
})
export class LookupSelectionModalAddItemExampleComponent implements OnDestroy {
  protected selectedPeople: Person[] | undefined;

  #subscriptions = new Subscription();

  readonly #modalSvc = inject(SkyModalService);
  readonly #searchSvc = inject(ExampleService);
  readonly #selectionModalSvc = inject(SkySelectionModalService);

  public ngOnDestroy(): void {
    this.#subscriptions.unsubscribe();
  }

  protected showSelectionModal(): void {
    const instance = this.#selectionModalSvc.open({
      descriptorProperty: 'name',
      idProperty: 'id',
      selectionDescriptor: 'person',
      searchAsync: (args) =>
        this.#searchSvc.search(args.searchText).pipe(
          map(
            (results): SkySelectionModalSearchResult => ({
              hasMore: results.hasMore,
              items: results.people,
              totalCount: results.totalCount,
            }),
          ),
        ),
      selectMode: 'single',
      showAddButton: true,
      addClick: (args: SkySelectionModalAddClickEventArgs) => {
        const modal = this.#modalSvc.open(AddItemModalComponent);

        this.#subscriptions.add(
          modal.closed.subscribe((close) => {
            if (close.reason === 'save') {
              const person = close.data as Person;
              this.#searchSvc.addItem(person);
              args.itemAdded({ item: person });
            }
          }),
        );
      },
    });

    this.#subscriptions.add(
      instance.closed.subscribe((args: SkySelectionModalCloseArgs) => {
        if (args.reason === 'save') {
          this.selectedPeople = args.selectedItems as Person[];
        }
      }),
    );
  }
}

```

#### example.service.ts

```typescript
import { Injectable } from '@angular/core';

import { Observable, of } from 'rxjs';
import { delay } from 'rxjs/operators';

import { Person } from './person';
import { SearchResults } from './search-results';

const people: Person[] = [
  { id: '1', name: 'Abed' },
  { id: '2', name: 'Alex' },
  { id: '3', name: 'Ben' },
  { id: '4', name: 'Britta' },
  { id: '5', name: 'Buzz' },
  { id: '6', name: 'Craig' },
  { id: '7', name: 'Elroy' },
  { id: '8', name: 'Garrett' },
  { id: '9', name: 'Ian' },
  { id: '10', name: 'Jeff' },
  { id: '11', name: 'Leonard' },
  { id: '12', name: 'Neil' },
  { id: '13', name: 'Pierce' },
  { id: '14', name: 'Preston' },
  { id: '15', name: 'Rachel' },
  { id: '16', name: 'Shirley' },
  { id: '17', name: 'Todd' },
  { id: '18', name: 'Troy' },
  { id: '19', name: 'Vaughn' },
  { id: '20', name: 'Vicki' },
];

@Injectable({
  providedIn: 'root',
})
export class ExampleService {
  public addItem(item: Person): void {
    people.push(item);
  }

  public search(searchText: string): Observable<SearchResults> {
    // Simulate a network call with latency. A real-world application might
    // use Angular's HttpClient to create an Observable from a call to a
    // web service.
    searchText = searchText.toUpperCase();

    const matchingPeople = people.filter((person) =>
      person.name.toUpperCase().includes(searchText),
    );

    return of({
      hasMore: false,
      people: matchingPeople,
      totalCount: matchingPeople.length,
    }).pipe(delay(800));
  }
}

```

#### person.ts

```typescript
export interface Person {
  id: string;
  name: string;
}

```

#### search-results.ts

```typescript
import { Person } from './person';

export interface SearchResults {
  hasMore: boolean;
  people: Person[];
  totalCount: number;
}

```

#### add-item-modal.component.html

```html
<form novalidate [formGroup]="formGroup" (ngSubmit)="save()">
  <sky-modal headingText="Add Item">
    <sky-modal-content>
      <sky-input-box labelText="Name">
        <input
          type="text"
          autocapitalize="words"
          autocomplete="off"
          formControlName="name"
          class="sky-form-control"
        />
      </sky-input-box>
    </sky-modal-content>
    <sky-modal-footer>
      <button class="sky-btn sky-btn-primary" type="submit">Add</button>
      <button class="sky-btn sky-btn-link" type="button" (click)="close()">
        Cancel
      </button>
    </sky-modal-footer>
  </sky-modal>
</form>

```

#### example.component.html

```html
<div class="sky-margin-stacked-xl">
  <button
    class="sky-btn sky-btn-default selection-modal-example-show-btn"
    type="button"
    (click)="showSelectionModal()"
  >
    Select a value
  </button>
</div>

@if (selectedPeople?.length) {
  <div>
    Selected people:
    <ul class="selection-modal-example-selected">
      @for (selectedPerson of selectedPeople; track selectedPerson) {
        <li>
          {{ selectedPerson.name }}
        </li>
      }
    </ul>
  </div>
}

```

---

## Selection modal with basic setup

**Component:** LookupSelectionModalBasicExampleComponent

**Selector:** `app-lookup-selection-modal-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkySelectionModalHarness } from '@skyux/lookup/testing';

import { of } from 'rxjs';

import { LookupSelectionModalBasicExampleComponent } from './example.component';
import { ExampleService } from './example.service';

describe('Selection modal example', () => {
  let mockSvc: jasmine.SpyObj<ExampleService>;

  async function setupTest(): Promise<{
    harness: SkySelectionModalHarness;
    el: HTMLElement;
    fixture: ComponentFixture<LookupSelectionModalBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      LookupSelectionModalBasicExampleComponent,
    );
    const el = fixture.nativeElement as HTMLElement;
    const openBtn = el.querySelector<HTMLButtonElement>(
      '.selection-modal-example-show-btn',
    );

    openBtn?.click();
    fixture.detectChanges();

    const rootLoader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const harness = await rootLoader.getHarness(SkySelectionModalHarness);
    return { harness, el, fixture };
  }

  beforeEach(() => {
    // Create a mock search service. In a real-world application, the search
    // service would make a web request which should be avoided in unit tests.
    mockSvc = jasmine.createSpyObj<ExampleService>('ExampleService', [
      'search',
    ]);

    mockSvc.search.and.callFake((searchText) => {
      return of({
        hasMore: false,
        people:
          searchText === 'ra'
            ? [
                {
                  id: '1',
                  name: 'Rachel',
                },
              ]
            : [],
        totalCount: 1,
      });
    });

    TestBed.configureTestingModule({
      imports: [
        LookupSelectionModalBasicExampleComponent,
        NoopAnimationsModule,
      ],
      providers: [{ provide: ExampleService, useValue: mockSvc }],
    });
  });

  it('should update the selected items list when an item is selected', async () => {
    const { harness, el } = await setupTest();

    await harness.enterSearchText('ra');
    await harness.selectSearchResult({
      contentText: 'Rachel',
    });
    await harness.saveAndClose();

    const selectedItemEls = el.querySelectorAll<HTMLLIElement>(
      '.selection-modal-example-selected li',
    );

    expect(selectedItemEls).toHaveSize(1);
    expect(selectedItemEls[0].innerText.trim()).toBe('Rachel');
  });

  it('should not update the selected items list when the user cancels the selection modal', async () => {
    const { harness, el } = await setupTest();

    await harness.enterSearchText('ra');
    await harness.selectSearchResult({
      contentText: 'Rachel',
    });
    await harness.cancel();

    const selectedItemEls = el.querySelectorAll<HTMLLIElement>(
      '.selection-modal-example-selected li',
    );

    expect(selectedItemEls).toHaveSize(0);
  });

  it('should respect the selection descriptor', async () => {
    const { harness } = await setupTest();

    await expectAsync(harness.getSearchAriaLabel()).toBeResolvedTo(
      'Search person',
    );
    await expectAsync(harness.getSaveButtonAriaLabel()).toBeResolvedTo(
      'Select person',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  SkySelectionModalSearchResult,
  SkySelectionModalService,
} from '@skyux/lookup';

import { map } from 'rxjs/operators';

import { ExampleService } from './example.service';
import { Person } from './person';

/**
 * @title Selection modal with basic setup
 */
@Component({
  standalone: true,
  selector: 'app-lookup-selection-modal-basic-example',
  templateUrl: './example.component.html',
})
export class LookupSelectionModalBasicExampleComponent {
  protected selectedPeople: Person[] | undefined;

  readonly #searchSvc = inject(ExampleService);
  readonly #selectionModalSvc = inject(SkySelectionModalService);

  protected showSelectionModal(): void {
    const instance = this.#selectionModalSvc.open({
      descriptorProperty: 'name',
      idProperty: 'id',
      selectionDescriptor: 'person',
      searchAsync: (args) =>
        this.#searchSvc.search(args.searchText).pipe(
          map(
            (results): SkySelectionModalSearchResult => ({
              hasMore: results.hasMore,
              items: results.people,
              totalCount: results.totalCount,
            }),
          ),
        ),
      selectMode: 'single',
    });

    instance.closed.subscribe((args) => {
      if (args.reason === 'save') {
        this.selectedPeople = args.selectedItems as Person[];
      }
    });
  }
}

```

#### example.service.ts

```typescript
import { Injectable } from '@angular/core';

import { Observable, of } from 'rxjs';
import { delay } from 'rxjs/operators';

import { Person } from './person';
import { SearchResults } from './search-results';

const people: Person[] = [
  { id: '1', name: 'Abed' },
  { id: '2', name: 'Alex' },
  { id: '3', name: 'Ben' },
  { id: '4', name: 'Britta' },
  { id: '5', name: 'Buzz' },
  { id: '6', name: 'Craig' },
  { id: '7', name: 'Elroy' },
  { id: '8', name: 'Garrett' },
  { id: '9', name: 'Ian' },
  { id: '10', name: 'Jeff' },
  { id: '11', name: 'Leonard' },
  { id: '12', name: 'Neil' },
  { id: '13', name: 'Pierce' },
  { id: '14', name: 'Preston' },
  { id: '15', name: 'Rachel' },
  { id: '16', name: 'Shirley' },
  { id: '17', name: 'Todd' },
  { id: '18', name: 'Troy' },
  { id: '19', name: 'Vaughn' },
  { id: '20', name: 'Vicki' },
];

@Injectable({
  providedIn: 'root',
})
export class ExampleService {
  public search(searchText: string): Observable<SearchResults> {
    // Simulate a network call with latency. A real-world application might
    // use Angular's HttpClient to create an Observable from a call to a
    // web service.
    searchText = searchText.toUpperCase();

    const matchingPeople = people.filter((person) =>
      person.name.toUpperCase().includes(searchText),
    );

    return of({
      hasMore: false,
      people: matchingPeople,
      totalCount: matchingPeople.length,
    }).pipe(delay(800));
  }
}

```

#### person.ts

```typescript
export interface Person {
  id: string;
  name: string;
}

```

#### search-results.ts

```typescript
import { Person } from './person';

export interface SearchResults {
  hasMore: boolean;
  people: Person[];
  totalCount: number;
}

```

#### example.component.html

```html
<div class="sky-margin-stacked-xl">
  <button
    type="button"
    class="sky-btn sky-btn-default selection-modal-example-show-btn"
    (click)="showSelectionModal()"
  >
    Select a value
  </button>
</div>

@if (selectedPeople?.length) {
  <div>
    Selected people:
    <ul class="selection-modal-example-selected">
      @for (selectedPerson of selectedPeople; track selectedPerson) {
        <li>
          {{ selectedPerson.name }}
        </li>
      }
    </ul>
  </div>
}

```

---

## Confirm, tested with controller

**Component:** ModalsConfirmBasicWithControllerExampleComponent

**Selector:** `app-modals-confirm-basic-with-controller-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { ComponentFixture, TestBed } from '@angular/core/testing';
import {
  SkyConfirmTestingController,
  SkyConfirmTestingModule,
} from '@skyux/modals/testing';

import { ModalsConfirmBasicWithControllerExampleComponent } from './example.component';

describe('Testing with SkyConfirmTestingController', () => {
  function setupTest(): {
    confirmController: SkyConfirmTestingController;
    fixture: ComponentFixture<ModalsConfirmBasicWithControllerExampleComponent>;
  } {
    const confirmController = TestBed.inject(SkyConfirmTestingController);
    const fixture = TestBed.createComponent(
      ModalsConfirmBasicWithControllerExampleComponent,
    );

    return { confirmController, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        SkyConfirmTestingModule,
        ModalsConfirmBasicWithControllerExampleComponent,
      ],
    });
  });

  it('should click "OK" on a confirmation dialog', () => {
    const { confirmController, fixture } = setupTest();

    fixture.componentInstance.launchConfirm();
    fixture.detectChanges();

    confirmController.expectOpen({
      message: 'Are you sure?',
    });

    confirmController.ok();
    confirmController.expectNone();

    expect(fixture.componentInstance.selectedAction).toEqual('ok');
  });

  it('should cancel the confirmation dialog', () => {
    const { confirmController, fixture } = setupTest();

    fixture.componentInstance.launchConfirm();
    fixture.detectChanges();

    confirmController.expectOpen({
      message: 'Are you sure?',
    });

    confirmController.cancel();
    confirmController.expectNone();

    expect(fixture.componentInstance.selectedAction).toEqual('cancel');
  });
});

```

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { SkyConfirmService } from '@skyux/modals';

/**
 * @title Confirm, tested with controller
 */
@Component({
  selector: 'app-modals-confirm-basic-with-controller-example',
  standalone: true,
  template: `<button
    aria-haspopup="dialog"
    class="sky-btn sky-btn-default"
    type="button"
    (click)="launchConfirm()"
  >
    Open confirm
  </button>`,
})
export class ModalsConfirmBasicWithControllerExampleComponent {
  public selectedAction: string | undefined;

  readonly #confirmSvc = inject(SkyConfirmService);

  public launchConfirm(): void {
    const dialog = this.#confirmSvc.open({
      message: 'Are you sure?',
    });

    dialog.closed.subscribe((args) => {
      this.selectedAction = args.action;
    });
  }
}

```

---

## Confirm, tested with harness

**Component:** ModalsConfirmBasicWithHarnessExampleComponent

**Selector:** `app-modals-confirm-basic-with-harness-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyConfirmHarness } from '@skyux/modals/testing';

import { ModalsConfirmBasicWithHarnessExampleComponent } from './example.component';

describe('Testing with SkyConfirmHarness', () => {
  async function setupTest(confirmBtnClass: string): Promise<{
    confirmHarness: SkyConfirmHarness;
    fixture: ComponentFixture<ModalsConfirmBasicWithHarnessExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      ModalsConfirmBasicWithHarnessExampleComponent,
    );
    const el = fixture.nativeElement as HTMLElement;
    const openBtn = el.querySelector<HTMLButtonElement>(confirmBtnClass);

    openBtn?.click();

    const rootLoader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const confirmHarness = await rootLoader.getHarness(SkyConfirmHarness);

    return { confirmHarness, fixture };
  }

  function expectDisplayedText(
    fixture: ComponentFixture<ModalsConfirmBasicWithHarnessExampleComponent>,
    expectedText: string,
  ): void {
    expect(
      (fixture.nativeElement as HTMLElement).querySelector<HTMLElement>(
        '.displayed-text',
      )?.innerText,
    ).toEqual(expectedText);
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [ModalsConfirmBasicWithHarnessExampleComponent],
    });
  });

  it('should show the correct text when OK is clicked on an OK confirm', async () => {
    const { confirmHarness, fixture } = await setupTest('.ok-confirm-btn');

    await confirmHarness.clickOkButton();

    expectDisplayedText(fixture, 'You selected the "ok" action.');

    await expectAsync(confirmHarness.getMessageText()).toBeResolvedTo(
      'Cannot delete invoice because it has vendor, credit memo, or purchase order activity.',
    );
  });

  it('should show the correct text when "Finalize" is clicked on a custom confirm', async () => {
    const { confirmHarness, fixture } = await setupTest(
      '.two-action-confirm-btn',
    );

    await confirmHarness.clickCustomButton({ text: 'Finalize' });

    expectDisplayedText(
      fixture,
      'You selected the "Finalize" button, which has an action of "save."',
    );

    await expectAsync(confirmHarness.getMessageText()).toBeResolvedTo(
      'Finalize report cards?',
    );

    await expectAsync(confirmHarness.getBodyText()).toBeResolvedTo(
      'Grades cannot be changed once the report cards are finalized.',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  SkyConfirmButtonConfig,
  SkyConfirmInstance,
  SkyConfirmService,
  SkyConfirmType,
} from '@skyux/modals';

/**
 * @title Confirm, tested with harness
 */
@Component({
  selector: 'app-modals-confirm-basic-with-harness-example',
  standalone: true,
  templateUrl: './example.component.html',
})
export class ModalsConfirmBasicWithHarnessExampleComponent {
  protected selectedAction: string | undefined;
  protected selectedText: string | undefined;

  readonly #confirmSvc = inject(SkyConfirmService);

  protected openOKConfirm(): void {
    const dialog: SkyConfirmInstance = this.#confirmSvc.open({
      message:
        'Cannot delete invoice because it has vendor, credit memo, or purchase order activity.',
    });

    dialog.closed.subscribe((result) => {
      this.selectedText = undefined;
      this.selectedAction = result.action;
    });
  }

  protected openTwoActionConfirm(): void {
    const buttons: SkyConfirmButtonConfig[] = [
      { text: 'Finalize', action: 'save', styleType: 'primary' },
      { text: 'Cancel', action: 'cancel', styleType: 'link' },
    ];

    const dialog: SkyConfirmInstance = this.#confirmSvc.open({
      message: 'Finalize report cards?',
      body: 'Grades cannot be changed once the report cards are finalized.',
      type: SkyConfirmType.Custom,
      buttons,
    });

    dialog.closed.subscribe((result) => {
      this.selectedAction = result.action;

      for (const button of buttons) {
        if (button.action === result.action) {
          this.selectedText = button.text;
          break;
        }
      }
    });
  }

  protected openThreeActionConfirm(): void {
    const buttons: SkyConfirmButtonConfig[] = [
      { text: 'Save', action: 'save', styleType: 'primary' },
      { text: 'Delete', action: 'delete' },
      { text: 'Keep working', action: 'cancel', styleType: 'link' },
    ];

    const dialog = this.#confirmSvc.open({
      message: 'Save your changes before leaving?',
      type: SkyConfirmType.Custom,
      buttons,
    });

    dialog.closed.subscribe((result) => {
      this.selectedAction = result.action;

      for (const button of buttons) {
        if (button.action === result.action) {
          this.selectedText = button.text;
          break;
        }
      }
    });
  }

  protected openDeleteConfirm(): void {
    const buttons: SkyConfirmButtonConfig[] = [
      { text: 'Delete', action: 'delete', styleType: 'danger' },
      { text: 'Cancel', action: 'cancel', styleType: 'link' },
    ];

    const dialog = this.#confirmSvc.open({
      message: 'Delete this account?',
      body: 'Deleting this account may affect processes that are currently running.',
      type: SkyConfirmType.Custom,
      buttons,
    });

    dialog.closed.subscribe((result) => {
      this.selectedAction = result.action;

      for (const button of buttons) {
        if (button.action === result.action) {
          this.selectedText = button.text;
          break;
        }
      }
    });
  }
}

```

#### example.component.html

```html
<button
  aria-haspopup="dialog"
  class="sky-btn sky-btn-default sky-margin-inline-sm ok-confirm-btn"
  type="button"
  (click)="openOKConfirm()"
>
  OK confirm
</button>

<button
  aria-haspopup="dialog"
  class="sky-btn sky-btn-default sky-margin-inline-sm two-action-confirm-btn"
  type="button"
  (click)="openTwoActionConfirm()"
>
  Confirm with two actions
</button>

<button
  aria-haspopup="dialog"
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="openThreeActionConfirm()"
>
  Confirm with three actions
</button>

<button
  aria-haspopup="dialog"
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="openDeleteConfirm()"
>
  Confirm with delete button
</button>

@if (selectedAction) {
  @if (selectedText) {
    <p class="displayed-text">
      You selected the "{{ selectedText }}" button, which has an action of "{{
        selectedAction
      }}."
    </p>
  } @else {
    <p class="displayed-text">
      You selected the "{{ selectedAction }}" action.
    </p>
  }
}

```

---

## Modal with basic setup, tested with controller

**Component:** ModalsModalBasicWithControllerExampleComponent

**Selector:** `app-modals-modal-basic-with-controller-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { ComponentFixture, TestBed } from '@angular/core/testing';
import {
  SkyModalTestingController,
  SkyModalTestingModule,
} from '@skyux/modals/testing';

import { ModalsModalBasicWithControllerExampleComponent } from './example.component';
import { ModalComponent } from './modal.component';

describe('Modal example using testing controller', () => {
  function setupTest(): {
    fixture: ComponentFixture<ModalsModalBasicWithControllerExampleComponent>;
    modalController: SkyModalTestingController;
  } {
    const fixture = TestBed.createComponent(
      ModalsModalBasicWithControllerExampleComponent,
    );
    const modalController = TestBed.inject(SkyModalTestingController);

    return { fixture, modalController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        SkyModalTestingModule,
        ModalsModalBasicWithControllerExampleComponent,
      ],
    });
  });

  it('should expect a modal to be open, close it, and expect none', () => {
    const { fixture, modalController } = setupTest();

    fixture.componentInstance.openModal();
    fixture.detectChanges();

    modalController.expectCount(1);
    modalController.expectOpen(ModalComponent);
    modalController.closeTopModal({
      data: {},
      reason: 'save',
    });
    modalController.expectNone();
  });
});

```

#### example.component.ts

```typescript
import { Component, OnDestroy, inject } from '@angular/core';
import { SkyHelpService } from '@skyux/core';
import {
  SkyModalError,
  SkyModalInstance,
  SkyModalService,
} from '@skyux/modals';

import { MyHelpService } from './help.service';
import { ModalContext } from './modal-context';
import { ModalComponent } from './modal.component';

/**
 * @title Modal with basic setup, tested with controller
 */
@Component({
  selector: 'app-modals-modal-basic-with-controller-example',
  standalone: true,
  template: `<button
    class="sky-btn sky-btn-default"
    type="button"
    (click)="openModal()"
  >
    Open modal
  </button>`,
})
export class ModalsModalBasicWithControllerExampleComponent
  implements OnDestroy
{
  public hasErrors = false;

  protected errors: SkyModalError[] = [];

  readonly #instances: SkyModalInstance[] = [];
  readonly #modalSvc = inject(SkyModalService);

  public ngOnDestroy(): void {
    this.#instances.forEach((i) => {
      i.close();
    });
  }

  public openModal(): void {
    const instance = this.#modalSvc.open(ModalComponent, {
      providers: [
        {
          provide: ModalContext,
          useValue: { value1: 'Hello!' },
        },
        // NOTE: The help service is normally provided at the application root, but
        // it is added here purely for demonstration purposes.
        // See: https://developer.blackbaud.com/skyux/learn/develop/global-help
        {
          provide: SkyHelpService,
          useExisting: MyHelpService,
        },
      ],
    });

    instance.beforeClose.subscribe((handler) => {
      if (this.hasErrors && handler.closeArgs.reason !== 'cancel') {
        this.errors = [
          {
            message: 'Something bad happened.',
          },
        ];
      } else {
        handler.closeModal();
      }
    });

    this.#instances.push(instance);
  }
}

```

#### help.service.ts

```typescript
import { Injectable } from '@angular/core';
import {
  SkyHelpOpenArgs,
  SkyHelpService,
  SkyHelpUpdateArgs,
} from '@skyux/core';

/**
 * This is a mock implementation of the help service. In a production scenario,
 * the `SkyHelpService` would be provided at the application root.
 * @see: https://developer.blackbaud.com/skyux/learn/develop/global-help
 */
@Injectable({ providedIn: 'root' })
export class MyHelpService extends SkyHelpService {
  public override openHelp(args?: SkyHelpOpenArgs): void {
    if (args) {
      console.error(`Open help panel to key: ${args.helpKey}`);
    }
  }

  public override updateHelp(args: SkyHelpUpdateArgs): void {
    if ('helpKey' in args) {
      console.error(`help key update: ${args.helpKey}`);
    }

    if ('pageDefaultHelpKey' in args) {
      console.error(`page default help key update: ${args.pageDefaultHelpKey}`);
    }
  }
}

```

#### modal-context.ts

```typescript
import { Injectable } from '@angular/core';

@Injectable()
export class ModalContext {
  public data:
    | {
        value1: string;
      }
    | undefined;
}

```

#### modal.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';

import { ModalContext } from './modal-context';

@Component({
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyInputBoxModule,
    SkyModalModule,
  ],
  template: `
    <form [formGroup]="exampleForm" (submit)="saveForm()">
      <sky-modal headingText="Modal title" helpKey="help.html">
        <sky-modal-content>
          <sky-input-box>
            <input formControlName="value1" type="text" />
          </sky-input-box>
        </sky-modal-content>
        <sky-modal-footer>
          <button class="sky-btn sky-btn-primary" type="submit">Save</button>
          <button
            class="sky-btn sky-btn-link"
            type="button"
            (click)="cancelForm()"
          >
            Cancel
          </button>
        </sky-modal-footer>
      </sky-modal>
    </form>
  `,
})
export class ModalComponent {
  protected exampleForm: FormGroup<{
    value1: FormControl<string | null | undefined>;
  }>;

  readonly #context = inject(ModalContext);
  readonly #instance = inject(SkyModalInstance);

  constructor() {
    this.exampleForm = inject(FormBuilder).group({
      value1: new FormControl(this.#context.data?.value1),
    });
  }

  protected cancelForm(): void {
    this.#instance.cancel();
  }

  protected saveForm(): void {
    this.#instance.save({});
  }
}

```

---

## Modal with a help key

**Component:** ModalsModalBasicWithHarnessHelpKeyExampleComponent

**Selector:** `app-modals-modal-basic-with-harness-help-key-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### context.ts

```typescript
import { ModalDemoData } from './data';

export class ModalDemoContext {
  constructor(public data: ModalDemoData) {}
}

```

#### data.service.ts

```typescript
import { Injectable } from '@angular/core';

import { Observable, of } from 'rxjs';
import { delay } from 'rxjs/operators';

import { ModalDemoData } from './data';

@Injectable({
  providedIn: 'root',
})
export class ModalDemoDataService {
  #data: ModalDemoData = {
    value1: 'Hello world',
  };

  public load(): Observable<ModalDemoData> {
    // Simulate a network request to get data.
    return of(this.#data).pipe(delay(1000));
  }

  public save(data: ModalDemoData): Observable<ModalDemoData> {
    this.#data = data;

    // Simulate a network request to save data.
    return of(this.#data).pipe(delay(1000));
  }
}

```

#### data.ts

```typescript
export interface ModalDemoData {
  value1?: string | null;
}

```

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import {
  SkyHelpTestingController,
  SkyHelpTestingModule,
} from '@skyux/core/testing';
import { SkyWaitService } from '@skyux/indicators';
import { SkyModalHarness } from '@skyux/modals/testing';

import { Observable, of } from 'rxjs';

import { ModalDemoDataService } from './data.service';
import { ModalsModalBasicWithHarnessHelpKeyExampleComponent } from './example.component';

class mockWaitSvc {
  public blockingWrap(data: unknown): Observable<unknown> {
    return of(data);
  }
}

describe('Basic modal', () => {
  async function setupTest(): Promise<{
    modalHarness: SkyModalHarness;
    fixture: ComponentFixture<ModalsModalBasicWithHarnessHelpKeyExampleComponent>;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(
      ModalsModalBasicWithHarnessHelpKeyExampleComponent,
    );
    fixture.componentInstance.onOpenModalClick();
    fixture.detectChanges();

    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const modalHarness = await loader.getHarness(
      SkyModalHarness.with({
        dataSkyId: 'modal-example',
      }),
    );
    const helpController = TestBed.inject(SkyHelpTestingController);

    return { modalHarness, fixture, helpController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        ModalsModalBasicWithHarnessHelpKeyExampleComponent,
        NoopAnimationsModule,
        SkyHelpTestingModule,
      ],
      providers: [
        {
          provide: SkyWaitService,
          useClass: mockWaitSvc,
        },
        ModalDemoDataService,
      ],
    });
  });

  it('should have the correct help key', async () => {
    const { modalHarness, helpController } = await setupTest();

    await modalHarness.clickHelpInline();

    helpController.expectCurrentHelpKey('modal-help');
  });
});

```

#### example.component.ts

```typescript
import { Component, OnDestroy, inject } from '@angular/core';
import { SkyWaitService } from '@skyux/indicators';
import { SkyModalConfigurationInterface, SkyModalService } from '@skyux/modals';

import { Subject } from 'rxjs';
import { takeUntil } from 'rxjs/operators';

import { ModalDemoContext } from './context';
import { ModalDemoData } from './data';
import { ModalDemoDataService } from './data.service';
import { ModalComponent } from './modal.component';

/**
 * @title Modal with a help key
 */
@Component({
  standalone: true,
  selector: 'app-modals-modal-basic-with-harness-help-key-example',
  templateUrl: './example.component.html',
})
export class ModalsModalBasicWithHarnessHelpKeyExampleComponent
  implements OnDestroy
{
  protected modalSize = 'medium';
  protected exampleValue: string | null | undefined;

  #ngUnsubscribe = new Subject<void>();

  readonly #dataSvc = inject(ModalDemoDataService);
  readonly #modalSvc = inject(SkyModalService);
  readonly #waitSvc = inject(SkyWaitService);

  public ngOnDestroy(): void {
    this.#ngUnsubscribe.next();
    this.#ngUnsubscribe.complete();
  }

  public onOpenModalClick(): void {
    // Display a blocking wait while data is loaded from the data service.
    this.#waitSvc
      .blockingWrap(this.#dataSvc.load())
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((data) => {
        const options: SkyModalConfigurationInterface = {
          providers: [
            {
              provide: ModalDemoContext,
              useValue: new ModalDemoContext(data),
            },
          ],
          size: this.modalSize,
        };

        // Show the modal after data is loaded.
        const instance = this.#modalSvc.open(ModalComponent, options);

        instance.closed.subscribe((result) => {
          if (result.reason === 'save') {
            // Display the updated value.
            this.exampleValue = (result.data as ModalDemoData).value1;
          }
        });
      });
  }
}

```

#### modal.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { FormControl, FormGroup, ReactiveFormsModule } from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyWaitService } from '@skyux/indicators';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';

import { ModalDemoContext } from './context';
import { ModalDemoDataService } from './data.service';

@Component({
  selector: 'app-modal',
  templateUrl: './modal.component.html',
  imports: [ReactiveFormsModule, SkyInputBoxModule, SkyModalModule],
})
export class ModalComponent {
  protected exampleForm: FormGroup<{
    value1: FormControl<string | null | undefined>;
  }>;

  readonly #context = inject(ModalDemoContext);
  readonly #dataSvc = inject(ModalDemoDataService);
  readonly #instance = inject(SkyModalInstance);
  readonly #waitSvc = inject(SkyWaitService);

  constructor() {
    this.exampleForm = new FormGroup({
      value1: new FormControl(this.#context.data.value1),
    });
  }

  protected saveForm(): void {
    // Use the data service to save the data.

    this.#waitSvc
      .blockingWrap(this.#dataSvc.save(this.exampleForm.value))
      .subscribe((data) => {
        // Notify the modal instance that data was saved and return the saved data.
        this.#instance.save(data);
      });
  }

  protected cancelForm(): void {
    this.#instance.cancel();
  }
}

```

#### example.component.html

```html
<button
  class="sky-btn sky-btn-default"
  type="button"
  (click)="onOpenModalClick()"
>
  Open modal example
</button>
@if (exampleValue) {
  <div>The user entered {{ exampleValue }}</div>
}

```

#### modal.component.html

```html
<form [formGroup]="exampleForm" (submit)="saveForm()">
  <sky-modal
    data-sky-id="modal-example"
    headingText="Modal title"
    helpKey="modal-help"
    [isDirty]="exampleForm.dirty"
  >
    <sky-modal-content>
      <sky-input-box labelText="An input inside a modal">
        <input formControlName="value1" type="text" />
      </sky-input-box>
    </sky-modal-content>
    <sky-modal-footer>
      <button class="sky-btn sky-btn-primary" type="submit">Save</button>
      <button class="sky-btn sky-btn-link" type="button" (click)="cancelForm()">
        Cancel
      </button>
    </sky-modal-footer>
  </sky-modal>
</form>

```

---

## Modal with basic setup, tested with harness

**Component:** ModalsModalBasicWithHarnessExampleComponent

**Selector:** `app-modals-modal-basic-with-harness-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### context.ts

```typescript
import { ModalDemoData } from './data';

export class ModalDemoContext {
  constructor(public data: ModalDemoData) {}
}

```

#### data.service.ts

```typescript
import { Injectable } from '@angular/core';

import { Observable, of } from 'rxjs';
import { delay } from 'rxjs/operators';

import { ModalDemoData } from './data';

@Injectable({
  providedIn: 'root',
})
export class ModalDemoDataService {
  #data: ModalDemoData = {
    value1: 'Hello world',
  };

  public load(): Observable<ModalDemoData> {
    // Simulate a network request to get data.
    return of(this.#data).pipe(delay(1000));
  }

  public save(data: ModalDemoData): Observable<ModalDemoData> {
    this.#data = data;

    // Simulate a network request to save data.
    return of(this.#data).pipe(delay(1000));
  }
}

```

#### data.ts

```typescript
export interface ModalDemoData {
  value1?: string | null;
}

```

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyWaitService } from '@skyux/indicators';
import { SkyModalHarness } from '@skyux/modals/testing';

import { Observable, of } from 'rxjs';

import { ModalDemoDataService } from './data.service';
import { ModalsModalBasicWithHarnessExampleComponent } from './example.component';

class mockWaitSvc {
  public blockingWrap(data: unknown): Observable<unknown> {
    return of(data);
  }
}

describe('Basic modal', () => {
  async function setupTest(): Promise<{
    modalHarness: SkyModalHarness;
    fixture: ComponentFixture<ModalsModalBasicWithHarnessExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      ModalsModalBasicWithHarnessExampleComponent,
    );
    fixture.componentInstance.onOpenModalClick();
    fixture.detectChanges();

    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const modalHarness = await loader.getHarness(
      SkyModalHarness.with({
        dataSkyId: 'modal-example',
      }),
    );

    return { modalHarness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        ModalsModalBasicWithHarnessExampleComponent,
        NoopAnimationsModule,
      ],
      providers: [
        {
          provide: SkyWaitService,
          useClass: mockWaitSvc,
        },
        ModalDemoDataService,
      ],
    });
  });

  it('should open the correct modal', async () => {
    const { modalHarness, fixture } = await setupTest();

    fixture.detectChanges();

    await expectAsync(modalHarness.getAriaRole()).toBeResolvedTo('dialog');
    await expectAsync(modalHarness.getSize()).toBeResolvedTo('medium');
    await expectAsync(modalHarness.isFullPage()).toBeResolvedTo(false);
    await expectAsync(modalHarness.getHeadingText()).toBeResolvedTo(
      'Modal title',
    );

    await modalHarness.clickHelpInline();

    await expectAsync(modalHarness.getHelpPopoverContent()).toBeResolvedTo(
      'Use the help inline component to invoke contextual user assistance.',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component, OnDestroy, inject } from '@angular/core';
import { SkyWaitService } from '@skyux/indicators';
import { SkyModalConfigurationInterface, SkyModalService } from '@skyux/modals';

import { Subject } from 'rxjs';
import { takeUntil } from 'rxjs/operators';

import { ModalDemoContext } from './context';
import { ModalDemoData } from './data';
import { ModalDemoDataService } from './data.service';
import { ModalComponent } from './modal.component';

/**
 * @title Modal with basic setup, tested with harness
 */
@Component({
  standalone: true,
  selector: 'app-modals-modal-basic-with-harness-example',
  templateUrl: './example.component.html',
})
export class ModalsModalBasicWithHarnessExampleComponent implements OnDestroy {
  protected modalSize = 'medium';
  protected exampleValue: string | null | undefined;

  #ngUnsubscribe = new Subject<void>();

  readonly #dataSvc = inject(ModalDemoDataService);
  readonly #modalSvc = inject(SkyModalService);
  readonly #waitSvc = inject(SkyWaitService);

  public ngOnDestroy(): void {
    this.#ngUnsubscribe.next();
    this.#ngUnsubscribe.complete();
  }

  public onOpenModalClick(): void {
    // Display a blocking wait while data is loaded from the data service.
    this.#waitSvc
      .blockingWrap(this.#dataSvc.load())
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((data) => {
        const options: SkyModalConfigurationInterface = {
          providers: [
            {
              provide: ModalDemoContext,
              useValue: new ModalDemoContext(data),
            },
          ],
          size: this.modalSize,
        };

        // Show the modal after data is loaded.
        const instance = this.#modalSvc.open(ModalComponent, options);

        instance.closed.subscribe((result) => {
          if (result.reason === 'save') {
            // Display the updated value.
            this.exampleValue = (result.data as ModalDemoData).value1;
          }
        });
      });
  }
}

```

#### modal.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { FormControl, FormGroup, ReactiveFormsModule } from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyWaitService } from '@skyux/indicators';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';

import { ModalDemoContext } from './context';
import { ModalDemoDataService } from './data.service';

@Component({
  selector: 'app-modal',
  templateUrl: './modal.component.html',
  imports: [ReactiveFormsModule, SkyInputBoxModule, SkyModalModule],
})
export class ModalComponent {
  protected exampleForm: FormGroup<{
    value1: FormControl<string | null | undefined>;
  }>;

  readonly #context = inject(ModalDemoContext);
  readonly #dataSvc = inject(ModalDemoDataService);
  readonly #instance = inject(SkyModalInstance);
  readonly #waitSvc = inject(SkyWaitService);

  constructor() {
    this.exampleForm = new FormGroup({
      value1: new FormControl(this.#context.data.value1),
    });
  }

  protected saveForm(): void {
    // Use the data service to save the data.

    this.#waitSvc
      .blockingWrap(this.#dataSvc.save(this.exampleForm.value))
      .subscribe((data) => {
        // Notify the modal instance that data was saved and return the saved data.
        this.#instance.save(data);
      });
  }

  protected cancelForm(): void {
    this.#instance.cancel();
  }
}

```

#### example.component.html

```html
<button
  class="sky-btn sky-btn-default"
  type="button"
  (click)="onOpenModalClick()"
>
  Open modal example
</button>
@if (exampleValue) {
  <div>The user entered {{ exampleValue }}</div>
}

```

#### modal.component.html

```html
<form [formGroup]="exampleForm" (submit)="saveForm()">
  <sky-modal
    data-sky-id="modal-example"
    headingText="Modal title"
    helpPopoverContent="Use the help inline component to invoke contextual user assistance."
    [isDirty]="exampleForm.dirty"
  >
    <sky-modal-content>
      <sky-input-box labelText="An input inside a modal">
        <input formControlName="value1" type="text" />
      </sky-input-box>
    </sky-modal-content>
    <sky-modal-footer>
      <button class="sky-btn sky-btn-primary" type="submit">Save</button>
      <button class="sky-btn sky-btn-link" type="button" (click)="cancelForm()">
        Cancel
      </button>
    </sky-modal-footer>
  </sky-modal>
</form>

```

---

## Modal with form errors

**Component:** ModalsModalWithErrorExampleComponent

**Selector:** `app-modals-modal-with-error-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### context.ts

```typescript
import { ModalDemoData } from './data';

export class ModalDemoContext {
  constructor(public data: ModalDemoData) {}
}

```

#### data.service.ts

```typescript
import { Injectable } from '@angular/core';

import { Observable, of } from 'rxjs';
import { delay } from 'rxjs/operators';

import { ModalDemoData } from './data';

@Injectable({
  providedIn: 'root',
})
export class ModalDemoDataService {
  #data: ModalDemoData = {
    value1: 'Hello world',
  };

  public load(): Observable<ModalDemoData> {
    // Simulate a network request to get data.
    return of(this.#data).pipe(delay(1000));
  }

  public save(data: ModalDemoData, error = false): Observable<ModalDemoData> {
    if (!error) {
      this.#data = data;
    }

    // Simulate a network request to save data.
    return of(this.#data).pipe(delay(1000));
  }
}

```

#### data.ts

```typescript
export interface ModalDemoData {
  value1?: string | null;
}

```

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyWaitService } from '@skyux/indicators';
import { SkyModalHarness } from '@skyux/modals/testing';

import { Observable, of } from 'rxjs';

import { ModalDemoDataService } from './data.service';
import { ModalsModalWithErrorExampleComponent } from './example.component';

class mockWaitSvc {
  public blockingWrap(data: unknown): Observable<unknown> {
    return of(data);
  }
}

describe('Basic modal', () => {
  async function setupTest(): Promise<{
    modalHarness: SkyModalHarness;
    fixture: ComponentFixture<ModalsModalWithErrorExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      ModalsModalWithErrorExampleComponent,
    );
    fixture.componentInstance.onOpenModalClick();
    fixture.detectChanges();

    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const modalHarness = await loader.getHarness(
      SkyModalHarness.with({
        dataSkyId: 'modal-example',
      }),
    );

    return { modalHarness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [ModalsModalWithErrorExampleComponent],
      providers: [
        {
          provide: SkyWaitService,
          useClass: mockWaitSvc,
        },
        ModalDemoDataService,
      ],
    });
  });

  it('should open the correct modal', async () => {
    const { modalHarness, fixture } = await setupTest();

    fixture.detectChanges();

    await expectAsync(modalHarness.getAriaRole()).toBeResolvedTo('dialog');
    await expectAsync(modalHarness.getSize()).toBeResolvedTo('medium');
    await expectAsync(modalHarness.isFullPage()).toBeResolvedTo(false);
  });
});

```

#### example.component.ts

```typescript
import { Component, OnDestroy, inject } from '@angular/core';
import { SkyWaitService } from '@skyux/indicators';
import { SkyModalConfigurationInterface, SkyModalService } from '@skyux/modals';

import { Subject } from 'rxjs';
import { takeUntil } from 'rxjs/operators';

import { ModalDemoContext } from './context';
import { ModalDemoData } from './data';
import { ModalDemoDataService } from './data.service';
import { ModalComponent } from './modal.component';

/**
 * @title Modal with form errors
 */
@Component({
  standalone: true,
  selector: 'app-modals-modal-with-error-example',
  templateUrl: './example.component.html',
})
export class ModalsModalWithErrorExampleComponent implements OnDestroy {
  protected modalSize = 'medium';
  protected exampleValue: string | null | undefined;

  #ngUnsubscribe = new Subject<void>();

  readonly #dataSvc = inject(ModalDemoDataService);
  readonly #modalSvc = inject(SkyModalService);
  readonly #waitSvc = inject(SkyWaitService);

  public ngOnDestroy(): void {
    this.#ngUnsubscribe.next();
    this.#ngUnsubscribe.complete();
  }

  public onOpenModalClick(): void {
    // Display a blocking wait while data is loaded from the data service.
    this.#waitSvc
      .blockingWrap(this.#dataSvc.load())
      .pipe(takeUntil(this.#ngUnsubscribe))
      .subscribe((data) => {
        const options: SkyModalConfigurationInterface = {
          providers: [
            {
              provide: ModalDemoContext,
              useValue: new ModalDemoContext(data),
            },
          ],
          size: this.modalSize,
        };

        // Show the modal after data is loaded.
        const instance = this.#modalSvc.open(ModalComponent, options);

        instance.closed.subscribe((result) => {
          if (result.reason === 'save') {
            // Display the updated value.
            this.exampleValue = (result.data as ModalDemoData).value1;
          }
        });
      });
  }
}

```

#### modal.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { FormControl, FormGroup, ReactiveFormsModule } from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyWaitService } from '@skyux/indicators';
import { SkyModalError, SkyModalInstance, SkyModalModule } from '@skyux/modals';

import { ModalDemoContext } from './context';
import { ModalDemoDataService } from './data.service';

@Component({
  selector: 'app-modal',
  templateUrl: './modal.component.html',
  imports: [ReactiveFormsModule, SkyInputBoxModule, SkyModalModule],
})
export class ModalComponent {
  protected exampleForm: FormGroup<{
    value1: FormControl<string | null | undefined>;
  }>;

  readonly #context = inject(ModalDemoContext);
  readonly #dataSvc = inject(ModalDemoDataService);
  readonly #instance = inject(SkyModalInstance);
  readonly #waitSvc = inject(SkyWaitService);

  public errors: SkyModalError[] = [];

  constructor() {
    this.exampleForm = new FormGroup({
      value1: new FormControl(this.#context.data.value1),
    });
  }

  protected saveForm(): void {
    // Use the data service to save the data.

    this.#waitSvc
      .blockingWrap(this.#dataSvc.save(this.exampleForm.value))
      .subscribe((data) => {
        // Notify the modal instance that data was saved and return the saved data.
        this.#instance.save(data);
      });
  }

  protected saveFormWithFormError(): void {
    // Use the data service to save the data.

    this.#waitSvc
      .blockingWrap(this.#dataSvc.save(this.exampleForm.value, true))
      .subscribe(() => {
        this.errors = [{ message: 'There was an error saving the form.' }];
      });
  }

  protected cancelForm(): void {
    this.#instance.cancel();
  }
}

```

#### example.component.html

```html
<button
  class="sky-btn sky-btn-default"
  type="button"
  (click)="onOpenModalClick()"
>
  Open modal example
</button>
@if (exampleValue) {
  <div>The user entered {{ exampleValue }}</div>
}

```

#### modal.component.html

```html
<form [formGroup]="exampleForm" (submit)="saveForm()">
  <sky-modal
    data-sky-id="modal-example"
    headingText="Modal title"
    [isDirty]="exampleForm.dirty"
    [formErrors]="errors"
  >
    <sky-modal-content>
      <sky-input-box labelText="An input inside a modal">
        <input formControlName="value1" type="text" />
      </sky-input-box>
    </sky-modal-content>
    <sky-modal-footer>
      <button class="sky-btn sky-btn-primary" type="submit">Save</button>
      <button
        class="sky-btn sky-btn-link"
        type="button"
        (click)="saveFormWithFormError()"
      >
        Save form with an error
      </button>
      <button class="sky-btn sky-btn-link" type="button" (click)="cancelForm()">
        Cancel
      </button>
    </sky-modal-footer>
  </sky-modal>
</form>

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