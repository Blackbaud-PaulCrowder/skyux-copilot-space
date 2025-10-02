---
component: 'search'
type: 'code-examples'
description: 'Code examples for the search component.'
---

# Search Code Examples

## Autocomplete with custom search

**Component:** LookupAutocompleteCustomSearchExampleComponent

**Selector:** `app-lookup-autocomplete-custom-search-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { CommonModule } from '@angular/common';
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyIconModule } from '@skyux/icon';
import {
  SkyAutocompleteModule,
  SkyAutocompleteSearchFunction,
  SkyAutocompleteSearchFunctionResponse,
} from '@skyux/lookup';

import { Ocean } from './ocean';

/**
 * @title Autocomplete with custom search
 */
@Component({
  selector: 'app-lookup-autocomplete-custom-search-example',
  templateUrl: './example.component.html',
  imports: [
    CommonModule,
    FormsModule,
    ReactiveFormsModule,
    SkyAutocompleteModule,
    SkyIconModule,
    SkyInputBoxModule,
  ],
})
export class LookupAutocompleteCustomSearchExampleComponent {
  protected formGroup: FormGroup;
  protected largestOcean: FormControl;

  protected oceans: Ocean[] = [
    { title: 'Arctic', id: 1 },
    { title: 'Atlantic', id: 2 },
    { title: 'Indian', id: 3 },
    { title: 'Pacific', id: 4 },
  ];

  readonly #formBuilder = inject(FormBuilder);

  constructor() {
    this.largestOcean = this.#formBuilder.control({ title: 'Arctic', id: 1 });
    this.formGroup = this.#formBuilder.group({
      largestOcean: this.largestOcean,
    });
  }

  protected getOceanSearchFunction(): SkyAutocompleteSearchFunction {
    const searchFunction = (
      searchText: string,
      oceans: Ocean[],
    ): SkyAutocompleteSearchFunctionResponse => {
      return new Promise((resolve) => {
        const searchTextLower = searchText.toLowerCase();

        const results = oceans.filter((ocean: Ocean) => {
          const val = ocean.title;
          return !!val?.toString().toLowerCase().includes(searchTextLower);
        });

        // Simulate an async request.
        setTimeout(() => {
          resolve(results);
        }, 500);
      });
    };

    return searchFunction;
  }
}

```

#### ocean.ts

```typescript
export interface Ocean {
  id: number;
  title: string;
}

```

#### example.component.html

```html
<form novalidate [formGroup]="formGroup">
  <p>
    The following field has a preselected value and utilizes a custom search
    function, as well as a custom template for the search results.
  </p>
  <div class="sky-margin-stacked-lg">
    <sky-input-box labelText="Largest ocean" stacked>
      <sky-autocomplete
        descriptorProperty="title"
        [data]="oceans"
        [search]="getOceanSearchFunction()"
        [searchResultTemplate]="oceanSearchResultTemplate"
      >
        <input formControlName="largestOcean" type="text" skyAutocomplete />
      </sky-autocomplete>
    </sky-input-box>
  </div>
  <p class="sky-font-emphasized">Form model:</p>
  <pre>{{ formGroup.value | json }}</pre>
</form>

<ng-template #oceanSearchResultTemplate let-item="item">
  <sky-icon iconName="arrow-right" />
  {{ item.title }} &bull; ID {{ item.id }}
</ng-template>

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

## Search with basic setup

**Component:** LookupSearchBasicExampleComponent

**Selector:** `app-lookup-search-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkySearchHarness } from '@skyux/lookup/testing';

import { LookupSearchBasicExampleComponent } from './example.component';

describe('Basic search example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    harness: SkySearchHarness;
    fixture: ComponentFixture<LookupSearchBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(LookupSearchBasicExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkySearchHarness.with({ dataSkyId: options.dataSkyId }),
    );

    fixture.detectChanges();
    await fixture.whenStable();

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [NoopAnimationsModule, LookupSearchBasicExampleComponent],
    });
  });

  it('should setup search component', async () => {
    const { harness } = await setupTest({
      dataSkyId: 'example-search',
    });

    await expectAsync(harness.getAriaLabel()).toBeResolvedTo(
      'Search reminders',
    );
    await expectAsync(harness.getPlaceholderText()).toBeResolvedTo(
      'Search through reminders.',
    );
  });

  it('should interact with search function', async () => {
    const { harness } = await setupTest({
      dataSkyId: 'example-search',
    });

    await harness.enterText('Send');
    await expectAsync(harness.getValue()).toBeResolvedTo('Send');

    await harness.clickClearButton();
    await expectAsync(harness.getValue()).toBeResolvedTo('');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyToolbarModule } from '@skyux/layout';
import { SkyRepeaterModule } from '@skyux/lists';
import { SkySearchModule } from '@skyux/lookup';

import { Item } from './item';

/**
 * @title Search with basic setup
 */
@Component({
  selector: 'app-lookup-search-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyRepeaterModule, SkySearchModule, SkyToolbarModule],
})
export class LookupSearchBasicExampleComponent {
  protected displayedItems: Item[];

  private items: Item[] = [
    {
      title: 'Call Robert Hernandez',
      note: 'Robert recently gave a very generous gift. We should call to thank him.',
    },
    {
      title: 'Send invitation to ball',
      note: "The Spring Ball is coming up soon. Let's get those invitations out!",
    },
    {
      title: 'Clean up desk',
      note: 'File and organize papers.',
    },
    {
      title: 'Investigate leads',
      note: 'Check out leads for important charity event funding.',
    },
    {
      title: 'Send thank you note',
      note: 'Send a thank you note to Timothy for his donation.',
    },
  ];

  protected placeholderText = 'Search through reminders.';
  protected searchAriaLabel = 'Search reminders';
  protected searchText = '';

  constructor() {
    this.displayedItems = this.items;
  }

  protected searchApplied(searchText: string): void {
    let filteredItems = this.items;
    this.searchText = searchText;

    if (searchText) {
      filteredItems = this.items.filter((item: Item) => {
        let property: keyof typeof item;

        for (property in item) {
          if (
            Object.prototype.hasOwnProperty.call(item, property) &&
            (property === 'title' || property === 'note')
          ) {
            if (item[property].includes(searchText)) {
              return true;
            }
          }
        }

        return false;
      });
    }

    this.displayedItems = filteredItems;
  }
}

```

#### item.ts

```typescript
export interface Item {
  title: string;
  note: string;
}

```

#### example.component.html

```html
<sky-toolbar>
  <sky-toolbar-item>
    <button
      class="sky-btn sky-btn-default sky-example-search-bar-item"
      type="button"
      (click)="searchApplied('Robert')"
    >
      Predefined search text
    </button>
  </sky-toolbar-item>
  <sky-toolbar-item>
    <sky-search
      data-sky-id="example-search"
      [ariaLabel]="searchAriaLabel"
      [searchText]="searchText"
      [debounceTime]="250"
      [placeholderText]="placeholderText"
      (searchApply)="searchApplied($event)"
      (searchChange)="searchApplied($event)"
    />
  </sky-toolbar-item>
</sky-toolbar>
<sky-repeater expandMode="none">
  @for (item of displayedItems; track item) {
    <sky-repeater-item>
      <sky-repeater-item-title>
        {{ item.title }}
      </sky-repeater-item-title>
      <sky-repeater-item-content>
        <div>
          {{ item.note }}
        </div>
      </sky-repeater-item-content>
    </sky-repeater-item>
  }
</sky-repeater>

```

---