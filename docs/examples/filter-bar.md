---
component: 'filter-bar'
type: 'code-examples'
description: 'Code examples for the filter-bar component.'
---

# Filter Bar Code Examples

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