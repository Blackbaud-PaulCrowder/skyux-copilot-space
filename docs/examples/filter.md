---
component: 'filter'
type: 'code-examples'
description: 'Code examples for the filter component.'
---

# Filter Code Examples

## Filter bar basic example

**Component:** FilterBarBasicExampleComponent

**Selector:** `app-filter-bar-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { expect } from '@skyux-sdk/testing';
import { SkyFilterBarHarness } from '@skyux/filter-bar/testing';
import { SkyModalHarness } from '@skyux/modals/testing';

import { FilterBarBasicExampleComponent } from './example.component';
import { FilterModalHarness } from './filter-modal-harness';

describe('Basic filter bar', () => {
  async function setupTest(): Promise<{
    filterBarHarness: SkyFilterBarHarness;
    fixture: ComponentFixture<FilterBarBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(FilterBarBasicExampleComponent);
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const filterBarHarness = await loader.getHarness(SkyFilterBarHarness);

    return { filterBarHarness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [FilterBarBasicExampleComponent],
    });
  });

  it('should display the filter bar with initial filters', async () => {
    const { filterBarHarness, fixture } = await setupTest();

    fixture.detectChanges();

    // Check that filter bar has active filters initially
    await expectAsync(filterBarHarness.hasActiveFilters()).toBeResolvedTo(
      false, // Initially no filters are applied
    );

    // Get all filter items
    const filterItems = await filterBarHarness.getItems();
    expect(filterItems).toHaveSize(3);

    // Check specific filter items exist
    const staffAssignedFilter = await filterBarHarness.getItem({
      filterId: 'staff-assigned',
    });
    await expectAsync(staffAssignedFilter.getLabelText()).toBeResolvedTo(
      'Staff assigned',
    );

    const currentGradeFilter = await filterBarHarness.getItem({
      filterId: 'current-grade',
    });
    await expectAsync(currentGradeFilter.getLabelText()).toBeResolvedTo(
      'Current grade',
    );
  });

  it('should open filter modal and interact with form controls using custom harness', async () => {
    const { filterBarHarness, fixture } = await setupTest();
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    fixture.detectChanges();

    // Click on the Role filter to open its modal
    const staffAssignedFilter = await filterBarHarness.getItem({
      filterId: 'staff-assigned',
    });

    await expectAsync(staffAssignedFilter.getFilterValue()).toBeResolvedTo(
      undefined,
    );

    await staffAssignedFilter.click();

    // Get the modal and our custom filter modal harness
    const modal = await loader.getHarness(SkyModalHarness);
    const filterModalHarness = await loader.getHarness(FilterModalHarness);

    // Verify the modal opened
    await expectAsync(modal.getSize()).toBeResolvedTo('medium');

    // Select an option and verify it's selected
    await filterModalHarness.selectOption(2);

    await expectAsync(staffAssignedFilter.getFilterValue()).toBeResolvedTo(
      'Kanesha Hutto',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component, model } from '@angular/core';
import {
  SkyFilterBarFilterItem,
  SkyFilterBarModule,
  SkyFilterItemModalOpenedArgs,
} from '@skyux/filter-bar';

import { of } from 'rxjs';

import { FilterItems } from './filter-items';
import { CommunityConnectionFilterModalComponent } from './filter-modals/community-connection-filter-modal.component';
import { CurrentGradeFilterModalComponent } from './filter-modals/current-grade-filter-modal.component';
import { EnteringGradeFilterModalComponent } from './filter-modals/entering-grade-filter-modal.component';
import { RoleFilterModalComponent } from './filter-modals/role-filter-modal.component';
import { StaffAssignedFilterModalComponent } from './filter-modals/staff-assigned-filter-modal.component';
import { FILTER_SELECTION_VALUES } from './filter-selection-values';

/**
 * @title Filter bar basic example
 */
@Component({
  selector: 'app-filter-bar-basic-example',
  imports: [SkyFilterBarModule],
  templateUrl: './example.component.html',
})
export class FilterBarBasicExampleComponent {
  protected readonly appliedFilters = model<
    SkyFilterBarFilterItem[] | undefined
  >();
  protected readonly selectedFilterIds = model<string[] | undefined>([
    'staff-assigned',
    'entering-grade',
    'current-grade',
  ]);

  protected communityConnectionModal = CommunityConnectionFilterModalComponent;
  protected currentGradeModal = CurrentGradeFilterModalComponent;
  protected enteringGradeModal = EnteringGradeFilterModalComponent;
  protected roleModal = RoleFilterModalComponent;
  protected staffAssignedModal = StaffAssignedFilterModalComponent;

  protected onModalOpened(
    args: SkyFilterItemModalOpenedArgs<FilterItems>,
  ): void {
    args.data = of({ items: FILTER_SELECTION_VALUES[args.filterId] });
  }
}

```

#### filter-items.ts

```typescript
import { SkyFilterBarFilterValue } from '@skyux/filter-bar';

export interface FilterItems {
  items: SkyFilterBarFilterValue[];
}

```

#### filter-modal-harness.ts

```typescript
import { HarnessPredicate } from '@angular/cdk/testing';
import { SkyComponentHarness } from '@skyux/core/testing';

/**
 * Custom harness for interacting with the filter modal component in tests.
 */
export class FilterModalHarness extends SkyComponentHarness {
  public static hostSelector = '.filter-modal-demo-form';

  #getSelectElement = this.locatorFor(
    'select[formControlName="selectedOption"]',
  );
  #getSaveButton = this.locatorFor('button.sky-btn-primary');
  #getCancelButton = this.locatorFor('button.sky-btn-link');

  public static with(): HarnessPredicate<FilterModalHarness> {
    return new HarnessPredicate(FilterModalHarness, {});
  }

  /**
   * Selects an option and saves the modal.
   */
  public async selectOption(value: number): Promise<void> {
    const select = await this.#getSelectElement();
    await select.selectOptions(value);

    const saveButton = await this.#getSaveButton();
    await saveButton.click();
  }

  /**
   * Clicks the Cancel button.
   */
  public async clickCancel(): Promise<void> {
    const cancelButton = await this.#getCancelButton();
    await cancelButton.click();
  }
}

```

#### filter-modals/community-connection-filter-modal.component.ts

```typescript
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import {
  SkyFilterItemModal,
  SkyFilterItemModalInstance,
} from '@skyux/filter-bar';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyRepeaterModule } from '@skyux/lists';
import { SkyModalModule } from '@skyux/modals';

import { FilterItems } from '../filter-items';

@Component({
  selector: 'app-community-connection-filter-modal',
  templateUrl: './community-connection-filter-modal.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyInputBoxModule,
    SkyModalModule,
    SkyRepeaterModule,
  ],
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class CommunityConnectionFilterModalComponent
  implements SkyFilterItemModal<FilterItems>
{
  public readonly modalInstance = inject<
    SkyFilterItemModalInstance<FilterItems>
  >(SkyFilterItemModalInstance);
  readonly #context = this.modalInstance.context;
  readonly #formBuilder: FormBuilder = inject(FormBuilder);
  protected headingText = this.#context.filterLabelText;
  protected items = this.#context.additionalContext!.items;
  protected selectedValue = this.#context.filterValue;

  protected formGroup: FormGroup = this.#formBuilder.group({
    selectedOption: this.#formBuilder.control(this.selectedValue?.value),
  });

  protected save(): void {
    const selectedValue = this.formGroup.get('selectedOption')?.value as string;

    if (selectedValue) {
      // Map the primitive value back to the full object
      const selectedItem = this.items.find(
        (item) => item.value === selectedValue,
      );
      this.modalInstance.save({ filterValue: selectedItem });
    } else {
      this.modalInstance.save({ filterValue: undefined });
    }
  }
}

```

#### filter-modals/current-grade-filter-modal.component.ts

```typescript
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import {
  SkyFilterItemModal,
  SkyFilterItemModalInstance,
} from '@skyux/filter-bar';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyRepeaterModule } from '@skyux/lists';
import { SkyModalModule } from '@skyux/modals';

import { FilterItems } from '../filter-items';

@Component({
  selector: 'app-current-grade-filter-modal',
  templateUrl: './current-grade-filter-modal.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyInputBoxModule,
    SkyModalModule,
    SkyRepeaterModule,
  ],
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class CurrentGradeFilterModalComponent
  implements SkyFilterItemModal<FilterItems>
{
  public readonly modalInstance = inject<
    SkyFilterItemModalInstance<FilterItems>
  >(SkyFilterItemModalInstance);
  readonly #context = this.modalInstance.context;
  readonly #formBuilder: FormBuilder = inject(FormBuilder);
  protected headingText = this.#context.filterLabelText;
  protected items = this.#context.additionalContext!.items;
  protected selectedValue = this.#context.filterValue;

  protected formGroup: FormGroup = this.#formBuilder.group({
    selectedOption: this.#formBuilder.control(this.selectedValue?.value),
  });

  protected save(): void {
    const selectedValue = this.formGroup.get('selectedOption')?.value as string;

    if (selectedValue) {
      const selectedItem = this.items.find(
        (item) => item.value === selectedValue,
      );
      this.modalInstance.save({ filterValue: selectedItem });
    } else {
      this.modalInstance.save({ filterValue: undefined });
    }
  }
}

```

#### filter-modals/entering-grade-filter-modal.component.ts

```typescript
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import {
  SkyFilterItemModal,
  SkyFilterItemModalInstance,
} from '@skyux/filter-bar';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyRepeaterModule } from '@skyux/lists';
import { SkyModalModule } from '@skyux/modals';

import { FilterItems } from '../filter-items';

@Component({
  selector: 'app-entering-grade-filter-modal',
  templateUrl: './entering-grade-filter-modal.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyInputBoxModule,
    SkyModalModule,
    SkyRepeaterModule,
  ],
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class EnteringGradeFilterModalComponent
  implements SkyFilterItemModal<FilterItems>
{
  public readonly modalInstance = inject<
    SkyFilterItemModalInstance<FilterItems>
  >(SkyFilterItemModalInstance);
  readonly #context = this.modalInstance.context;
  readonly #formBuilder: FormBuilder = inject(FormBuilder);
  protected headingText = this.#context.filterLabelText;
  protected items = this.#context.additionalContext!.items;
  protected selectedValue = this.#context.filterValue;

  protected formGroup: FormGroup = this.#formBuilder.group({
    selectedOption: this.#formBuilder.control(this.selectedValue?.value),
  });

  protected save(): void {
    const selectedValue = this.formGroup.get('selectedOption')?.value as string;

    if (selectedValue) {
      const selectedItem = this.items.find(
        (item) => item.value === selectedValue,
      );
      this.modalInstance.save({ filterValue: selectedItem });
    } else {
      this.modalInstance.save({ filterValue: undefined });
    }
  }
}

```

#### filter-modals/role-filter-modal.component.ts

```typescript
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import {
  SkyFilterItemModal,
  SkyFilterItemModalInstance,
} from '@skyux/filter-bar';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyRepeaterModule } from '@skyux/lists';
import { SkyModalModule } from '@skyux/modals';

import { FilterItems } from '../filter-items';

@Component({
  selector: 'app-role-filter-modal',
  templateUrl: './role-filter-modal.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyInputBoxModule,
    SkyModalModule,
    SkyRepeaterModule,
  ],
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class RoleFilterModalComponent
  implements SkyFilterItemModal<FilterItems>
{
  public readonly modalInstance = inject<
    SkyFilterItemModalInstance<FilterItems>
  >(SkyFilterItemModalInstance);
  readonly #context = this.modalInstance.context;
  readonly #formBuilder: FormBuilder = inject(FormBuilder);
  protected headingText = this.#context.filterLabelText;
  protected items = this.#context.additionalContext!.items;
  protected selectedValue = this.#context.filterValue;

  protected formGroup: FormGroup = this.#formBuilder.group({
    selectedOption: this.#formBuilder.control(this.selectedValue?.value),
  });

  protected save(): void {
    const selectedValue = this.formGroup.get('selectedOption')?.value as string;

    if (selectedValue) {
      const selectedItem = this.items.find(
        (item) => item.value === selectedValue,
      );
      this.modalInstance.save({ filterValue: selectedItem });
    } else {
      this.modalInstance.save({ filterValue: undefined });
    }
  }
}

```

#### filter-modals/staff-assigned-filter-modal.component.ts

```typescript
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import {
  SkyFilterItemModal,
  SkyFilterItemModalInstance,
} from '@skyux/filter-bar';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyRepeaterModule } from '@skyux/lists';
import { SkyModalModule } from '@skyux/modals';

import { FilterItems } from '../filter-items';

@Component({
  selector: 'app-staff-assigned-filter-modal',
  templateUrl: './staff-assigned-filter-modal.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyInputBoxModule,
    SkyModalModule,
    SkyRepeaterModule,
  ],
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class StaffAssignedFilterModalComponent
  implements SkyFilterItemModal<FilterItems>
{
  public readonly modalInstance = inject<
    SkyFilterItemModalInstance<FilterItems>
  >(SkyFilterItemModalInstance);
  readonly #context = this.modalInstance.context;
  readonly #formBuilder: FormBuilder = inject(FormBuilder);
  protected headingText = this.#context.filterLabelText;
  protected items = this.#context.additionalContext!.items;
  protected selectedValue = this.#context.filterValue;

  protected formGroup: FormGroup = this.#formBuilder.group({
    selectedOption: this.#formBuilder.control(this.selectedValue?.value),
  });

  protected save(): void {
    const selectedValue = this.formGroup.get('selectedOption')?.value as string;

    if (selectedValue) {
      const selectedItem = this.items.find(
        (item) => item.value === selectedValue,
      );
      this.modalInstance.save({ filterValue: selectedItem });
    } else {
      this.modalInstance.save({ filterValue: undefined });
    }
  }
}

```

#### filter-selection-values.ts

```typescript
import { SkyFilterBarFilterValue } from '@skyux/filter-bar';

// eslint-disable @cspell/spellchecker
export const FILTER_SELECTION_VALUES: Record<
  string,
  SkyFilterBarFilterValue[]
> = {
  'community-connection': [
    { value: 'child-of-faculty', displayValue: 'Child of faculty' },
    { value: 'child-of-alum', displayValue: 'Child of alum' },
    { value: 'grandparent-is-alum', displayValue: 'Grandchild of alum' },
    { value: 'related-to-trustee', displayValue: 'Related to trustee' },
    { value: 'sibling-candidate', displayValue: 'Sibling is candidate' },
    {
      value: 'sibling-past-candidate',
      displayValue: 'Sibling is past candidate',
    },
    { value: 'sibling-student', displayValue: 'Sibling is student' },
    { value: 'sibling alum', displayValue: 'Sibling is alum' },
    {
      value: 'sibling-incoming',
      displayValue: 'Sibling is incoming student',
    },
  ],
  'current-grade': [
    { value: 'pre-k', displayValue: 'Pre-k' },
    { value: 'kindergarten', displayValue: 'Kindergarten' },
    { value: 'grade-1', displayValue: '1st grade' },
    { value: 'grade-2', displayValue: '2nd grade' },
    { value: 'grade-3', displayValue: '3rd grade' },
    { value: 'grade-4', displayValue: '4th grade' },
    { value: 'grade-5', displayValue: '5th grade' },
    { value: 'grade-6', displayValue: '6th grade' },
    { value: 'grade-7', displayValue: '7th grade' },
    { value: 'grade-8', displayValue: '8th grade' },
    { value: 'grade-9', displayValue: '9th grade' },
    { value: 'grade-10', displayValue: '10th grade' },
    { value: 'grade-11', displayValue: '11th grade' },
    { value: 'grade-12', displayValue: '12th grade' },
  ],
  'entering-grade': [
    { value: 'pre-k', displayValue: 'Pre-k' },
    { value: 'kindergarten', displayValue: 'Kindergarten' },
    { value: 'grade-1', displayValue: '1st grade' },
    { value: 'grade-2', displayValue: '2nd grade' },
    { value: 'grade-3', displayValue: '3rd grade' },
    { value: 'grade-4', displayValue: '4th grade' },
    { value: 'grade-5', displayValue: '5th grade' },
    { value: 'grade-6', displayValue: '6th grade' },
    { value: 'grade-7', displayValue: '7th grade' },
    { value: 'grade-8', displayValue: '8th grade' },
    { value: 'grade-9', displayValue: '9th grade' },
    { value: 'grade-10', displayValue: '10th grade' },
    { value: 'grade-11', displayValue: '11th grade' },
    { value: 'grade-12', displayValue: '12th grade' },
  ],
  role: [
    { value: 'candidate', displayValue: 'Candidate' },
    { value: 'incoming-student', displayValue: 'Incoming student' },
    { value: 'student', displayValue: 'Student' },
  ],
  'staff-assigned': [
    { value: '1', displayValue: 'Solomon Hurley' },
    { value: '2', displayValue: 'Kanesha Hutto' },
    { value: '3', displayValue: 'Darcel Lenz' },
    { value: '4', displayValue: 'Cheyenne Lightfoot' },
    { value: '5', displayValue: 'Jack Lovett' },
    { value: '6', displayValue: 'Wonda Lumpkin' },
    { value: '7', displayValue: 'Kristeen Lunsford' },
    { value: '8', displayValue: 'Clarice Overton' },
    { value: '9', displayValue: 'Martine Rocha' },
    { value: '10', displayValue: 'Tonja Sanderson' },
    { value: '11', displayValue: 'Molly Seymour' },
    { value: '12', displayValue: 'Ed Sipes' },
    { value: '13', displayValue: 'Cristen Sizemore' },
    { value: '14', displayValue: 'Rod Tomlinson' },
    { value: '15', displayValue: 'Eliza Vanhorn' },
    { value: '16', displayValue: 'Jessy Witherspoon' },
    { value: '17', displayValue: 'Ilene Woo' },
  ],
};

```

#### example.component.html

```html
<sky-filter-bar
  [(appliedFilters)]="appliedFilters"
  [(selectedFilterIds)]="selectedFilterIds"
>
  <sky-filter-item-modal
    filterId="community-connection"
    labelText="Community connection"
    modalSize="medium"
    [modalComponent]="communityConnectionModal"
    (modalOpened)="onModalOpened($event)"
  />
  <sky-filter-item-modal
    filterId="current-grade"
    labelText="Current grade"
    modalSize="medium"
    [modalComponent]="currentGradeModal"
    (modalOpened)="onModalOpened($event)"
  />
  <sky-filter-item-modal
    filterId="entering-grade"
    labelText="Entering grade"
    modalSize="medium"
    [modalComponent]="enteringGradeModal"
    (modalOpened)="onModalOpened($event)"
  />
  <sky-filter-item-modal
    filterId="role"
    labelText="Role"
    modalSize="medium"
    [modalComponent]="roleModal"
    (modalOpened)="onModalOpened($event)"
  />
  <sky-filter-item-modal
    filterId="staff-assigned"
    labelText="Staff assigned"
    modalSize="medium"
    [modalComponent]="staffAssignedModal"
    (modalOpened)="onModalOpened($event)"
  />
</sky-filter-bar>

```

#### filter-modals/community-connection-filter-modal.component.html

```html
<form class="filter-modal-demo-form" novalidate [formGroup]="formGroup">
  <sky-modal [headingText]="headingText">
    <sky-modal-content>
      <sky-input-box [labelText]="headingText">
        <select formControlName="selectedOption" class="sky-form-control">
          <option [value]="null">-- Select an option --</option>
          @for (item of items; track item.value) {
            <option [value]="item.value">
              {{ item.displayValue }}
            </option>
          }
        </select>
      </sky-input-box>
    </sky-modal-content>
    <sky-modal-footer>
      <button class="sky-btn sky-btn-primary" type="button" (click)="save()">
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
</form>

```

#### filter-modals/current-grade-filter-modal.component.html

```html
<form class="filter-modal-demo-form" novalidate [formGroup]="formGroup">
  <sky-modal [headingText]="headingText">
    <sky-modal-content>
      <sky-input-box [labelText]="headingText">
        <select formControlName="selectedOption" class="sky-form-control">
          <option [value]="null">-- Select an option --</option>
          @for (item of items; track item.value) {
            <option [value]="item.value">
              {{ item.displayValue }}
            </option>
          }
        </select>
      </sky-input-box>
    </sky-modal-content>
    <sky-modal-footer>
      <button class="sky-btn sky-btn-primary" type="button" (click)="save()">
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
</form>

```

#### filter-modals/entering-grade-filter-modal.component.html

```html
<form class="filter-modal-demo-form" novalidate [formGroup]="formGroup">
  <sky-modal [headingText]="headingText">
    <sky-modal-content>
      <sky-input-box [labelText]="headingText">
        <select formControlName="selectedOption" class="sky-form-control">
          <option [value]="null">-- Select an option --</option>
          @for (item of items; track item.value) {
            <option [value]="item.value">
              {{ item.displayValue }}
            </option>
          }
        </select>
      </sky-input-box>
    </sky-modal-content>
    <sky-modal-footer>
      <button class="sky-btn sky-btn-primary" type="button" (click)="save()">
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
</form>

```

#### filter-modals/role-filter-modal.component.html

```html
<form class="filter-modal-demo-form" novalidate [formGroup]="formGroup">
  <sky-modal [headingText]="headingText">
    <sky-modal-content>
      <sky-input-box [labelText]="headingText">
        <select formControlName="selectedOption" class="sky-form-control">
          <option [value]="null">-- Select an option --</option>
          @for (item of items; track item.value) {
            <option [value]="item.value">
              {{ item.displayValue }}
            </option>
          }
        </select>
      </sky-input-box>
    </sky-modal-content>
    <sky-modal-footer>
      <button class="sky-btn sky-btn-primary" type="button" (click)="save()">
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
</form>

```

#### filter-modals/staff-assigned-filter-modal.component.html

```html
<form class="filter-modal-demo-form" novalidate [formGroup]="formGroup">
  <sky-modal [headingText]="headingText">
    <sky-modal-content>
      <sky-input-box [labelText]="headingText">
        <select formControlName="selectedOption" class="sky-form-control">
          <option [value]="null">-- Select an option --</option>
          @for (item of items; track item.value) {
            <option [value]="item.value">
              {{ item.displayValue }}
            </option>
          }
        </select>
      </sky-input-box>
    </sky-modal-content>
    <sky-modal-footer>
      <button class="sky-btn sky-btn-primary" type="button" (click)="save()">
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
</form>

```

---

## Expandable inline filter

**Component:** ListsFilterInlineExampleComponent

**Selector:** `app-lists-filter-inline-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyCheckboxHarness } from '@skyux/forms/testing';
import {
  SkyFilterButtonHarness,
  SkyFilterInlineHarness,
} from '@skyux/lists/testing';

import { ListsFilterInlineExampleComponent } from './example.component';

describe('Filter inline example', () => {
  async function setupTest(
    options: {
      dataSkyId?: string;
    } = {},
  ): Promise<{
    filterButtonHarness: SkyFilterButtonHarness;
    fixture: ComponentFixture<ListsFilterInlineExampleComponent>;
    loader: HarnessLoader;
  }> {
    await TestBed.configureTestingModule({
      imports: [ListsFilterInlineExampleComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(ListsFilterInlineExampleComponent);
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

    await filterButtonHarness.clickFilterButton();
    fixture.detectChanges();
    await fixture.whenStable();

    const filterInlineHarness = await loader.getHarness(
      SkyFilterInlineHarness.with({ dataSkyId: 'filter-inline' }),
    );

    const itemHarness = await filterInlineHarness.getItem({
      dataSkyId: 'hide-orange-filter',
    });
    const orangeCheck = await itemHarness.queryHarness(SkyCheckboxHarness);
    await orangeCheck.check();

    fixture.detectChanges();
    await fixture.whenStable();

    await expectAsync(filterButtonHarness.isActive()).toBeResolvedTo(true);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { FormsModule } from '@angular/forms';
import { SkyIdModule } from '@skyux/core';
import { SkyCheckboxModule, SkyInputBoxModule } from '@skyux/forms';
import { SkyToolbarModule } from '@skyux/layout';
import { SkyFilterModule, SkyRepeaterModule } from '@skyux/lists';

interface Filter {
  name: string;
  value: string | boolean;
}

interface Fruit {
  name: string;
  type: string;
  color: string;
}

/**
 * @title Expandable inline filter
 */
@Component({
  selector: 'app-lists-filter-inline-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    SkyCheckboxModule,
    SkyIdModule,
    SkyFilterModule,
    SkyInputBoxModule,
    SkyRepeaterModule,
    SkyToolbarModule,
  ],
})
export class ListsFilterInlineExampleComponent {
  protected appliedFilters: Filter[] = [];
  protected filteredItems: Fruit[];
  protected filtersActive = false;
  protected fruitType = 'any';
  protected hideOrange = false;

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

  constructor() {
    this.filteredItems = this.items.slice();
  }

  protected filterButtonClicked(): void {
    this.showInlineFilters = !this.showInlineFilters;
  }

  protected fruitTypeChange(newValue: string): void {
    this.fruitType = newValue;
    this.#setFilterActiveState();
  }

  protected hideOrangeChange(newValue: boolean): void {
    this.hideOrange = newValue;
    this.#setFilterActiveState();
  }

  #setFilterActiveState(): void {
    this.appliedFilters = [];

    if (this.fruitType !== 'any') {
      this.appliedFilters.push({
        name: 'fruitType',
        value: this.fruitType,
      });
    }

    if (this.hideOrange) {
      this.appliedFilters.push({
        name: 'hideOrange',
        value: true,
      });
    }

    this.filtersActive = this.appliedFilters.length > 0;
    this.filteredItems = this.#filterItems(this.items, this.appliedFilters);
  }

  #orangeFilterFailed(filter: Filter, item: Fruit): boolean {
    return (
      filter.name === 'hideOrange' && !!filter.value && item.color === 'orange'
    );
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
}

```

#### example.component.html

```html
<sky-toolbar>
  <sky-toolbar-section>
    <sky-toolbar-item>
      <sky-filter-button
        data-sky-id="my-filter-button"
        [active]="filtersActive"
        [ariaControls]="inlineFilters.id"
        [ariaExpanded]="showInlineFilters"
        [showButtonText]="true"
        (filterButtonClick)="filterButtonClicked()"
      />
    </sky-toolbar-item>
  </sky-toolbar-section>
</sky-toolbar>

<div #inlineFilters skyId [hidden]="!showInlineFilters">
  <sky-filter-inline data-sky-id="filter-inline">
    <sky-filter-inline-item data-sky-id="fruit-filter">
      <sky-input-box labelText="Fruit type">
        <select [ngModel]="fruitType" (ngModelChange)="fruitTypeChange($event)">
          <option value="any">Any fruit</option>
          <option value="citrus">Citrus</option>
          <option value="berry">Berry</option>
        </select>
      </sky-input-box>
    </sky-filter-inline-item>
    <sky-filter-inline-item data-sky-id="hide-orange-filter">
      <sky-checkbox
        labelText="Hide orange fruits"
        [ngModel]="hideOrange"
        (ngModelChange)="hideOrangeChange($event)"
      />
    </sky-filter-inline-item>
  </sky-filter-inline>
</div>

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

## Autocomplete with search filters

**Component:** LookupAutocompleteSearchFiltersExampleComponent

**Selector:** `app-lookup-autocomplete-search-filters-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { CommonModule } from '@angular/common';
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import {
  SkyAutocompleteModule,
  SkyAutocompleteSearchFunctionFilter,
} from '@skyux/lookup';

/**
 * @title Autocomplete with search filters
 */
@Component({
  selector: 'app-lookup-autocomplete-search-filters-example',
  templateUrl: './example.component.html',
  imports: [
    CommonModule,
    FormsModule,
    ReactiveFormsModule,
    SkyAutocompleteModule,
    SkyInputBoxModule,
  ],
})
export class LookupAutocompleteSearchFiltersExampleComponent {
  protected colors: { name: string }[] = [
    { name: 'Red' },
    { name: 'Blue' },
    { name: 'Green' },
    { name: 'Orange' },
    { name: 'Pink' },
    { name: 'Purple' },
    { name: 'Yellow' },
    { name: 'Brown' },
    { name: 'Turquoise' },
    { name: 'White' },
    { name: 'Black' },
  ];

  protected formGroup: FormGroup;

  protected searchFilters: SkyAutocompleteSearchFunctionFilter[] = [
    (searchText: string, item: { name: string }): boolean => {
      return item.name !== 'Red';
    },
  ];

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      favoriteColor: undefined,
    });
  }
}

```

#### example.component.html

```html
<form novalidate [formGroup]="formGroup">
  <p>
    The following field provides a custom function that filters the data before
    every search attempt.
  </p>
  <div class="sky-margin-stacked-lg">
    <sky-input-box labelText='Color ("Red" is not available)' stacked>
      <sky-autocomplete [data]="colors" [searchFilters]="searchFilters">
        <input formControlName="favoriteColor" skyAutocomplete type="text" />
      </sky-autocomplete>
    </sky-input-box>
  </div>
  <p class="sky-font-emphasized">Form model:</p>
  <pre>{{ formGroup.value | json }}</pre>
</form>

```

---