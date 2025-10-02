---
component: 'lookup'
type: 'code-examples'
description: 'Code examples for the lookup component.'
---

# Lookup Code Examples

## Advanced example

**Component:** LookupAutocompleteAdvancedExampleComponent

**Selector:** `app-lookup-autocomplete-advanced-example`

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
import {
  SkyAutocompleteModule,
  SkyAutocompleteSearchFunctionFilter,
  SkyAutocompleteSelectionChange,
} from '@skyux/lookup';

import { Planet } from './planet';

/**
 * @title Advanced example
 */
@Component({
  selector: 'app-lookup-autocomplete-advanced-example',
  templateUrl: './example.component.html',
  imports: [
    CommonModule,
    FormsModule,
    ReactiveFormsModule,
    SkyAutocompleteModule,
    SkyInputBoxModule,
  ],
})
export class LookupAutocompleteAdvancedExampleComponent {
  protected farthestPlanet: FormControl;
  protected formGroup: FormGroup;

  protected planets: Planet[] = [
    {
      name: 'Mercury',
      description: 'Mercury is a planet in our solar system.',
    },
    { name: 'Venus', description: 'Venus is a planet in our solar system.' },
    { name: 'Earth', description: 'Earth is a planet in our solar system.' },
    { name: 'Mars', description: 'Mars is a planet in our solar system.' },
    {
      name: 'Jupiter',
      description: 'Jupiter is a planet in our solar system.',
    },
    { name: 'Saturn', description: 'Saturn is a planet in our solar system.' },
    { name: 'Uranus', description: 'Uranus is a planet in our solar system.' },
    {
      name: 'Neptune',
      description: 'Neptune is a planet in our solar system.',
    },
  ];

  protected searchFilters: SkyAutocompleteSearchFunctionFilter[] = [
    (searchText: string, item: Planet): boolean => {
      return item.name !== 'Red';
    },
  ];

  readonly #formBuilder = inject(FormBuilder);

  constructor() {
    this.farthestPlanet = this.#formBuilder.control({});
    this.formGroup = this.#formBuilder.group({
      farthestPlanet: this.farthestPlanet,
    });
  }

  protected onPlanetSelection(args: SkyAutocompleteSelectionChange): void {
    alert(`You selected ${(args.selectedItem as Planet).name}`);
  }
}

```

#### planet.ts

```typescript
export interface Planet {
  name?: string;
  description?: string;
}

```

#### example.component.html

```html
<form novalidate [formGroup]="formGroup">
  <div class="sky-margin-stacked-lg">
    The following field:<br />
    <ul>
      <li>utilizes a custom search result template,</li>
      <li>searches against the name and description properties,</li>
      <li>limits the search results to two,</li>
      <li>runs the search if the query is at least three characters long,</li>
      <li>and fires an event when a selection is made.</li>
    </ul>
  </div>

  <div class="sky-margin-stacked-lg">
    <sky-input-box labelText="Farthest planet from the sun" stacked>
      <sky-autocomplete
        [data]="planets"
        [propertiesToSearch]="['name', 'description']"
        [searchResultsLimit]="2"
        [searchResultTemplate]="planetSearchResultTemplate"
        [searchTextMinimumCharacters]="3"
        (selectionChange)="onPlanetSelection($event)"
      >
        <input formControlName="farthestPlanet" skyAutocomplete type="text" />
      </sky-autocomplete>
    </sky-input-box>
  </div>
  <p class="sky-font-emphasized">Form model:</p>
  <pre>{{ formGroup.value | json }}</pre>
</form>

<ng-template #planetSearchResultTemplate let-item="item">
  <strong>
    {{ item.name }}
  </strong>
  <br />
  {{ item.description }}
</ng-template>

```

---

## Autocomplete with any value allowed

**Component:** LookupAutocompleteAnyValueExampleComponent

**Selector:** `app-lookup-autocomplete-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### color-option.ts

```typescript
export interface ColorOption {
  id?: number;
  name: string;
}

```

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyAutocompleteHarness } from '@skyux/lookup/testing';

import { of } from 'rxjs';

import { LookupAutocompleteAnyValueExampleComponent } from './example.component';
import { LookupAutocompleteAnyValueExampleService } from './example.service';

describe('Autocomplete with any value example', () => {
  let mockSvc!: jasmine.SpyObj<LookupAutocompleteAnyValueExampleService>;

  async function setupTest(options: { dataSkyId: string }): Promise<{
    harness: SkyAutocompleteHarness;
    fixture: ComponentFixture<LookupAutocompleteAnyValueExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      LookupAutocompleteAnyValueExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyAutocompleteHarness.with({ dataSkyId: options.dataSkyId }),
    );

    fixture.detectChanges();
    await fixture.whenStable();

    return { harness, fixture };
  }

  beforeEach(() => {
    // Create a mock search service. In a real-world application, the search
    // service would make a web request which should be avoided in unit tests.
    mockSvc = jasmine.createSpyObj<LookupAutocompleteAnyValueExampleService>(
      'LookupAutocompleteAnyValueExampleService',
      ['search'],
    );

    TestBed.configureTestingModule({
      imports: [LookupAutocompleteAnyValueExampleComponent],
      providers: [
        {
          provide: LookupAutocompleteAnyValueExampleService,
          useValue: mockSvc,
        },
      ],
    });
  });

  it('should set up favorite color autocomplete input', async () => {
    const { harness, fixture } = await setupTest({
      dataSkyId: 'favorite-color',
    });

    mockSvc.search.and.callFake((searchText) =>
      of({
        hasMore: false,
        colors:
          searchText === 'b'
            ? [
                {
                  id: 1,
                  name: 'Blue',
                },
              ]
            : [],
        totalCount: 1,
      }),
    );

    const ctrl = await harness.getControl();

    await ctrl.focus();
    await ctrl.setValue('b');

    const searchResultsText = await harness.getSearchResultsText();

    expect(searchResultsText[0]).toBe('b');
    expect(searchResultsText[1]).toBe('Blue');

    await ctrl.clear();
    await ctrl.setValue('Turquoise');

    const searchResults = await harness.getSearchResults();
    await expectAsync(searchResults[0].getDescriptorValue()).toBeResolvedTo(
      'Turquoise',
    );
    await expectAsync(searchResults[0].getText()).toBeResolvedTo('Turquoise');

    await searchResults[0].select();

    expect(
      (fixture.nativeElement as HTMLElement).querySelector<HTMLElement>(
        '.selected-color',
      )?.innerText,
    ).toBe('Turquoise');
  });
});

```

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import {
  SkyAutocompleteModule,
  SkyAutocompleteSearchAsyncArgs,
} from '@skyux/lookup';

import { map } from 'rxjs';

import { ColorOption } from './color-option';
import { LookupAutocompleteAnyValueExampleService } from './example.service';

/**
 * @title Autocomplete with any value allowed
 */
@Component({
  selector: 'app-lookup-autocomplete-basic-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyAutocompleteModule,
    SkyInputBoxModule,
  ],
})
export class LookupAutocompleteAnyValueExampleComponent {
  readonly #svc = inject(LookupAutocompleteAnyValueExampleService);

  protected readonly favoriteColor = new FormControl<ColorOption | undefined>(
    undefined,
  );

  public readonly formGroup = inject(FormBuilder).group({
    favoriteColor: this.favoriteColor,
  });

  protected onSearchAsync(args: SkyAutocompleteSearchAsyncArgs): void {
    // In a real-world application the search service might return an Observable
    // created by calling HttpClient.get(). Assigning that Observable to the result
    // allows the autocomplete component to cancel the web request if it does not
    // // complete before the user searches again.
    args.result = this.#svc.search(args.searchText).pipe(
      map((result) => ({
        hasMore: result.hasMore,
        items: result.colors,
        totalCount: result.totalCount,
      })),
    );
  }
}

```

#### example.service.ts

```typescript
import { Injectable } from '@angular/core';

import { Observable, delay, of } from 'rxjs';

import { ColorOption } from './color-option';
import { SearchResults } from './search-results';

const colors: ColorOption[] = [
  { id: 1, name: 'Red' },
  { id: 2, name: 'Blue' },
  { id: 3, name: 'Green' },
];

@Injectable({
  providedIn: 'root',
})
export class LookupAutocompleteAnyValueExampleService {
  public search(searchText: string): Observable<SearchResults> {
    // Simulate a network call with latency. A real-world application might
    // use Angular's HttpClient to create an Observable from a call to a
    // web service.
    searchText = searchText.toUpperCase();

    const matchingColors = colors.filter((color) =>
      color.name.toUpperCase().includes(searchText),
    );

    return of({
      hasMore: false,
      colors: matchingColors,
      totalCount: matchingColors.length,
    }).pipe(delay(800));
  }
}

```

#### search-results.ts

```typescript
import { ColorOption } from './color-option';

export interface SearchResults {
  hasMore: boolean;
  colors: ColorOption[];
  totalCount: number;
}

```

#### example.component.html

```html
<form novalidate [formGroup]="formGroup">
  <sky-input-box labelText="Favorite color" stacked>
    <sky-autocomplete
      data-sky-id="favorite-color"
      allowAnyValue="true"
      highlightSearchText="false"
      (searchAsync)="onSearchAsync($event)"
    >
      <input formControlName="favoriteColor" skyAutocomplete type="text" />
    </sky-autocomplete>
  </sky-input-box>

  <span class="selected-color">{{
    formGroup.get('favoriteColor')?.value?.name
  }}</span>
</form>

```

---

## Autocomplete with basic setup

**Component:** LookupAutocompleteBasicExampleComponent

**Selector:** `app-lookup-autocomplete-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyAutocompleteHarness } from '@skyux/lookup/testing';

import { LookupAutocompleteBasicExampleComponent } from './example.component';

describe('Basic autocomplete example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    harness: SkyAutocompleteHarness;
    fixture: ComponentFixture<LookupAutocompleteBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      LookupAutocompleteBasicExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyAutocompleteHarness.with({ dataSkyId: options.dataSkyId }),
    );

    fixture.detectChanges();
    await fixture.whenStable();

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [LookupAutocompleteBasicExampleComponent],
    });
  });

  it('should set up favorite color autocomplete input', async () => {
    const { harness, fixture } = await setupTest({
      dataSkyId: 'favorite-color',
    });

    await harness.focus();
    await harness.enterText('b');

    const searchResultsText = await harness.getSearchResultsText();

    expect(searchResultsText.length).toBe(3);

    await harness.clear();
    await harness.enterText('blu');

    const searchResults = await harness.getSearchResults();
    await expectAsync(searchResults[0].getDescriptorValue()).toBeResolvedTo(
      'Blue',
    );
    await expectAsync(searchResults[0].getText()).toBeResolvedTo('Blue');

    await searchResults[0].select();
    const value =
      fixture.componentInstance.formGroup.get('favoriteColor')?.value;
    expect(value?.name).toBe('Blue');
  });
});

```

#### example.component.ts

```typescript
import { CommonModule } from '@angular/common';
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyIdModule } from '@skyux/core';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyAutocompleteModule } from '@skyux/lookup';

/**
 * @title Autocomplete with basic setup
 */
@Component({
  selector: 'app-lookup-autocomplete-basic-example',
  templateUrl: './example.component.html',
  imports: [
    CommonModule,
    FormsModule,
    ReactiveFormsModule,
    SkyAutocompleteModule,
    SkyIdModule,
    SkyInputBoxModule,
  ],
})
export class LookupAutocompleteBasicExampleComponent {
  public colors: { name: string }[] = [
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

  public formGroup = inject(FormBuilder).group({
    favoriteColor: new FormControl<{ name: string } | undefined>(undefined),
  });
}

```

#### example.component.html

```html
<form novalidate [formGroup]="formGroup">
  <sky-input-box labelText="Favorite color" stacked>
    <sky-autocomplete data-sky-id="favorite-color" [data]="colors">
      <input formControlName="favoriteColor" type="text" skyAutocomplete />
    </sky-autocomplete>
  </sky-input-box>
  <p class="sky-font-emphasized">Form model:</p>
  <pre>{{ formGroup.value | json }}</pre>
</form>

```

---

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

## Country field with basic setup

**Component:** LookupCountryFieldBasicExampleComponent

**Selector:** `app-lookup-country-field-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyInputBoxHarness } from '@skyux/forms/testing';
import { SkyCountryFieldHarness } from '@skyux/lookup/testing';

import { LookupCountryFieldBasicExampleComponent } from './example.component';

describe('Basic country field example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    harness: SkyCountryFieldHarness;
    fixture: ComponentFixture<LookupCountryFieldBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      LookupCountryFieldBasicExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await (
      await loader.getHarness(
        SkyInputBoxHarness.with({ dataSkyId: options.dataSkyId }),
      )
    ).queryHarness(SkyCountryFieldHarness);

    fixture.detectChanges();
    await fixture.whenStable();

    return { harness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [LookupCountryFieldBasicExampleComponent],
    });
  });

  it('should set up country field input', async () => {
    const { harness, fixture } = await setupTest({
      dataSkyId: 'country-field',
    });

    await harness.focus();
    await harness.enterText('ger');

    const searchResultsText = await harness.getSearchResultsText();

    expect(searchResultsText.length).toBe(4);

    await harness.clear();
    await harness.enterText('can');

    const searchResults = await harness.getSearchResults();
    await expectAsync(searchResults[1].getText()).toBeResolvedTo('Canada');

    await searchResults[1].select();
    const value = fixture.componentInstance.countryForm.get('country')?.value;
    expect(value?.name).toBe('Canada');
  });
});

```

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  AbstractControl,
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
  ValidationErrors,
  Validators,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyCountryFieldCountry, SkyCountryFieldModule } from '@skyux/lookup';

interface DemoForm {
  country: FormControl<SkyCountryFieldCountry | undefined>;
}

function validateCountry(
  control: AbstractControl<SkyCountryFieldCountry | undefined>,
): ValidationErrors | null {
  return control.value?.name === 'Mexico' ? { invalidCountry: true } : null;
}

/**
 * @title Country field with basic setup
 */
@Component({
  selector: 'app-lookup-country-field-basic-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyCountryFieldModule,
    SkyInputBoxModule,
  ],
})
export class LookupCountryFieldBasicExampleComponent {
  protected countryControl: FormControl<SkyCountryFieldCountry | undefined>;
  public countryForm: FormGroup<DemoForm>;

  protected helpPopoverContent =
    'We use the country to validate your passport within 10 business days. You can update it at any time.';

  #formBuilder = inject(FormBuilder);

  constructor() {
    this.countryControl = new FormControl(
      {
        name: 'Australia',
        iso2: 'au',
      },
      {
        nonNullable: true,
        validators: [validateCountry, Validators.required],
      },
    );

    this.countryForm = this.#formBuilder.group({
      country: this.countryControl,
    });
  }
}

```

#### example.component.html

```html
<form [formGroup]="countryForm">
  <sky-input-box
    data-sky-id="country-field"
    hintText="If you have multiple countries, choose your primary country."
    labelText="Country"
    [helpPopoverContent]="helpPopoverContent"
  >
    <sky-country-field formControlName="country" />
    @if (countryControl.errors?.['invalidCountry']) {
      <sky-form-error
        errorName="invalidCountry"
        errorText="This country is no longer available for the date you selected."
      />
    }
  </sky-input-box>
</form>

```

---

## Lookup with add item button

**Component:** LookupAddItemExampleComponent

**Selector:** `app-lookup-add-item-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### add-item-modal.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
  Validators,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';

let nextId = 21;

@Component({
  selector: 'app-add-item-modal',
  templateUrl: './add-item-modal.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyInputBoxModule,
    SkyModalModule,
  ],
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
import { SkyInputBoxHarness } from '@skyux/forms/testing';
import { SkyLookupHarness } from '@skyux/lookup/testing';

import { of } from 'rxjs';

import { LookupAddItemExampleComponent } from './example.component';
import { DemoService } from './example.service';

describe('Lookup asynchronous search example', () => {
  let mockSvc!: jasmine.SpyObj<DemoService>;

  async function setupTest(): Promise<{
    lookupHarness: SkyLookupHarness;
    fixture: ComponentFixture<LookupAddItemExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(LookupAddItemExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const lookupHarness = await (
      await loader.getHarness(
        SkyInputBoxHarness.with({ dataSkyId: 'favorite-names-field' }),
      )
    ).queryHarness(SkyLookupHarness);

    return { lookupHarness, fixture };
  }

  beforeEach(() => {
    // Create a mock search service. In a real-world application, the search
    // service would make a web request which should be avoided in unit tests.
    mockSvc = jasmine.createSpyObj<DemoService>('DemoService', ['search']);

    TestBed.configureTestingModule({
      imports: [LookupAddItemExampleComponent, NoopAnimationsModule],
      providers: [
        {
          provide: DemoService,
          useValue: mockSvc,
        },
      ],
    });
  });

  it('should set the expected initial value', async () => {
    const { lookupHarness } = await setupTest();

    await expectAsync(lookupHarness.getSelectionsText()).toBeResolvedTo([
      'Shirley',
    ]);
  });

  it('should update the form control when a favorite name is selected', async () => {
    const { lookupHarness, fixture } = await setupTest();

    mockSvc.search.and.callFake((searchText) =>
      of({
        hasMore: false,
        people:
          searchText === 'b'
            ? [
                {
                  id: '21',
                  name: 'Bernard',
                },
              ]
            : [],
        totalCount: 1,
      }),
    );

    await lookupHarness.enterText('b');
    await lookupHarness.selectSearchResult({
      text: 'Bernard',
    });

    expect(fixture.componentInstance.favoritesForm.value.favoriteNames).toEqual(
      [
        { id: '16', name: 'Shirley' },
        { id: '21', name: 'Bernard' },
      ],
    );
  });

  it('should respect the selection descriptor', async () => {
    const { lookupHarness } = await setupTest();

    mockSvc.search.and.callFake(() =>
      of({
        hasMore: false,
        people: [
          {
            id: '21',
            name: 'Bernard',
          },
        ],
        totalCount: 1,
      }),
    );

    await lookupHarness.clickShowMoreButton();

    const picker = await lookupHarness.getShowMorePicker();

    await expectAsync(picker.getSearchAriaLabel()).toBeResolvedTo(
      'Search names',
    );
    await expectAsync(picker.getSaveButtonAriaLabel()).toBeResolvedTo(
      'Select names',
    );
  });
});

```

#### example.component.ts

```typescript
import { CommonModule } from '@angular/common';
import { Component, OnDestroy, OnInit, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyIdModule } from '@skyux/core';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyWaitService } from '@skyux/indicators';
import {
  SkyAutocompleteSearchAsyncArgs,
  SkyLookupAddClickEventArgs,
  SkyLookupModule,
  SkyLookupShowMoreConfig,
} from '@skyux/lookup';
import { SkyModalService } from '@skyux/modals';

import { Subscription } from 'rxjs';
import { map } from 'rxjs/operators';

import { AddItemModalComponent } from './add-item-modal.component';
import { DemoService } from './example.service';
import { Person } from './person';

/**
 * @title Lookup with add item button
 */
@Component({
  selector: 'app-lookup-add-item-example',
  templateUrl: './example.component.html',
  imports: [
    CommonModule,
    FormsModule,
    ReactiveFormsModule,
    SkyIdModule,
    SkyInputBoxModule,
    SkyLookupModule,
  ],
})
export class LookupAddItemExampleComponent implements OnInit, OnDestroy {
  public favoritesForm: FormGroup<{
    favoriteNames: FormControl<Person[] | null>;
  }>;

  public showMoreConfig: SkyLookupShowMoreConfig = {
    nativePickerConfig: {
      selectionDescriptor: 'names',
    },
  };

  #subscriptions = new Subscription();

  readonly #svc = inject(DemoService);
  readonly #modalSvc = inject(SkyModalService);
  readonly #waitSvc = inject(SkyWaitService);

  constructor() {
    const names = new FormControl<Person[]>([{ id: '16', name: 'Shirley' }]);

    this.favoritesForm = inject(FormBuilder).group({
      favoriteNames: names,
    });
  }

  public ngOnInit(): void {
    // If you need to execute some logic after the lookup values change,
    // subscribe to Angular's built-in value changes observable.
    this.favoritesForm.valueChanges.subscribe((changes) => {
      console.log('Lookup value changes:', changes);
    });
  }

  public ngOnDestroy(): void {
    this.#subscriptions.unsubscribe();
  }

  public onSubmit(): void {
    alert('Form submitted with: ' + JSON.stringify(this.favoritesForm.value));
  }

  public searchAsync(args: SkyAutocompleteSearchAsyncArgs): void {
    // In a real-world application the search service might return an Observable
    // created by calling HttpClient.get(). Assigning that Observable to the result
    // allows the lookup component to cancel the web request if it does not complete
    // before the user searches again.
    args.result = this.#svc.search(args.searchText).pipe(
      map((result) => ({
        hasMore: result.hasMore,
        items: result.people,
        totalCount: result.totalCount,
      })),
    );
  }

  public addClick(args: SkyLookupAddClickEventArgs): void {
    const modal = this.#modalSvc.open(AddItemModalComponent);

    this.#subscriptions.add(
      modal.closed.subscribe((close) => {
        if (close.reason === 'save') {
          const person = close.data as Person;

          this.#subscriptions.add(
            this.#waitSvc
              .blockingWrap(this.#svc.addPerson(person))
              .subscribe((data) => {
                args.itemAdded({
                  item: person,
                  data,
                });
              }),
          );
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
export class DemoService {
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

  public addPerson(person: Person): Observable<Person[]> {
    // Simulate adding a person with a network call.
    if (!people.some((item) => item.name === person.name)) {
      people.unshift(person);
    }

    return of(people.slice()).pipe(delay(800));
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
      <sky-input-box
        labelText="Name"
        hintText="Find an individual by first name"
      >
        <input
          type="text"
          autocapitalize="words"
          autocomplete="off"
          formControlName="name"
        />
      </sky-input-box>
    </sky-modal-content>
    <sky-modal-footer>
      <button class="sky-btn sky-btn-default" type="button" (click)="close()">
        Cancel
      </button>
      <button class="sky-btn sky-btn-primary" type="submit">Add</button>
    </sky-modal-footer>
  </sky-modal>
</form>

```

#### example.component.html

```html
<form
  class="sky-padding-even-md"
  novalidate
  [formGroup]="favoritesForm"
  (ngSubmit)="onSubmit()"
>
  <sky-input-box
    data-sky-id="favorite-names-field"
    helpPopoverContent="A name can be selected from the list or added as a new name."
    hintText="Choose a name from the list or add a new name."
    labelText="Favorite name(s)"
    stacked
  >
    <sky-lookup
      formControlName="favoriteNames"
      idProperty="name"
      [enableShowMore]="true"
      [showAddButton]="true"
      [showMoreConfig]="showMoreConfig"
      (addClick)="addClick($event)"
      (searchAsync)="searchAsync($event)"
    />
  </sky-input-box>
  <div
    class="sky-border-dark sky-rounded-corners sky-padding-even-md sky-margin-stacked-lg"
  >
    <strong>Form model:</strong>
    <pre>{{ favoritesForm.value | json }}</pre>
  </div>
  <button class="sky-btn sky-btn-default" type="submit">Submit</button>
</form>

```

---

## Lookup with a custom picker

**Component:** LookupCustomPickerExampleComponent

**Selector:** `app-lookup-custom-picker-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyInputBoxHarness } from '@skyux/forms/testing';
import { SkyLookupHarness } from '@skyux/lookup/testing';

import { of } from 'rxjs';

import { LookupCustomPickerExampleComponent } from './example.component';
import { DemoService } from './example.service';
import { Person } from './person';
import { PickerHarness } from './picker-harness';

const people: Person[] = [
  {
    name: 'Abed',
    formal: 'Mr. Nadir',
  },
  {
    name: 'Alex',
    formal: 'Mr. Osbourne',
  },
  {
    name: 'Ben',
    formal: 'Mr. Chang',
  },
  {
    name: 'Britta',
    formal: 'Ms. Perry',
  },
  {
    name: 'Buzz',
    formal: 'Mr. Hickey',
  },
  {
    name: 'Craig',
    formal: 'Mr. Pelton',
  },
  {
    name: 'Elroy',
    formal: 'Mr. Patashnik',
  },
  {
    name: 'Garrett',
    formal: 'Mr. Lambert',
  },
  {
    name: 'Ian',
    formal: 'Mr. Duncan',
  },
  {
    name: 'Jeff',
    formal: 'Mr. Winger',
  },
  {
    name: 'Leonard',
    formal: 'Mr. Rodriguez',
  },
  {
    name: 'Neil',
    formal: 'Mr. Neil',
  },
  {
    name: 'Pierce',
    formal: 'Mr. Hawthorne',
  },
  {
    name: 'Preston',
    formal: 'Mr. Koogler',
  },
  {
    name: 'Rachel',
    formal: 'Ms. Rachel',
  },
  {
    name: 'Shirley',
    formal: 'Ms. Bennett',
  },
  {
    name: 'Todd',
    formal: 'Mr. Jacobson',
  },
  {
    name: 'Troy',
    formal: 'Mr. Barnes',
  },
  {
    name: 'Vaughn',
    formal: 'Mr. Miller',
  },
  {
    name: 'Vicki',
    formal: 'Ms. Jenkins',
  },
];

describe('Lookup custom picker example', () => {
  let mockSvc!: jasmine.SpyObj<DemoService>;

  async function setupTest(): Promise<{
    lookupHarness: SkyLookupHarness;
    fixture: ComponentFixture<LookupCustomPickerExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(LookupCustomPickerExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const lookupHarness = await (
      await loader.getHarness(
        SkyInputBoxHarness.with({ dataSkyId: 'favorite-names-field' }),
      )
    ).queryHarness(SkyLookupHarness);

    return { lookupHarness, fixture };
  }

  beforeEach(() => {
    // Create a mock search service. In a real-world application, the search
    // service would make a web request which should be avoided in unit tests.
    mockSvc = jasmine.createSpyObj<DemoService>('DemoService', ['search']);

    TestBed.configureTestingModule({
      imports: [LookupCustomPickerExampleComponent, NoopAnimationsModule],
      providers: [
        {
          provide: DemoService,
          useValue: mockSvc,
        },
      ],
    });
  });

  it('should set the expected initial value', async () => {
    const { lookupHarness } = await setupTest();

    await expectAsync(lookupHarness.getSelectionsText()).toBeResolvedTo([
      'Shirley',
    ]);
  });

  it('should update the form control when a favorite name is selected', async () => {
    const { lookupHarness, fixture } = await setupTest();

    mockSvc.search.and.callFake(() =>
      of({
        hasMore: false,
        people: [
          {
            name: 'Abed',
            formal: 'Mr. Nadir',
          },
        ],
        totalCount: 1,
      }),
    );

    await lookupHarness.enterText('Be');

    const allResultHarnesses = await lookupHarness.getSearchResults();
    const firstResultHarness = allResultHarnesses[0];

    if (firstResultHarness) {
      await firstResultHarness.select();
    }

    expect(fixture.componentInstance.favoritesForm.value.favoriteNames).toEqual(
      [
        { name: 'Shirley', formal: 'Ms. Bennett' },
        { name: 'Abed', formal: 'Mr. Nadir' },
      ],
    );
  });

  it('should use a custom picker', async () => {
    const { lookupHarness, fixture } = await setupTest();

    mockSvc.search.and.callFake(() =>
      of({
        hasMore: false,
        people: people,
        totalCount: 20,
      }),
    );

    // Show the custom picker.
    await lookupHarness.clickShowMoreButton();

    // Use the custom picker harness to validate that selecting/deselecting items
    // updates the lookup form field.
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const customPickerHarness = await loader.getHarness(PickerHarness);

    await customPickerHarness.checkItemAt(2); // Ben (Mr. Chang)
    await customPickerHarness.checkItemAt(7); // Garret (Mr. Lambert)
    await customPickerHarness.uncheckItemAt(15); // Shirley (Ms. Bennett)

    await customPickerHarness.save();

    expect(fixture.componentInstance.favoritesForm.value.favoriteNames).toEqual(
      [
        { name: 'Ben', formal: 'Mr. Chang' },
        { name: 'Garrett', formal: 'Mr. Lambert' },
      ],
    );
  });
});

```

#### example.component.ts

```typescript
import { CommonModule } from '@angular/common';
import { Component, OnInit, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyWaitService } from '@skyux/indicators';
import {
  SkyAutocompleteSearchAsyncArgs,
  SkyLookupAddClickEventArgs,
  SkyLookupModule,
  SkyLookupShowMoreConfig,
  SkyLookupShowMoreCustomPickerContext,
} from '@skyux/lookup';
import { SkyModalService } from '@skyux/modals';

import { map } from 'rxjs/operators';

import { DemoService } from './example.service';
import { Person } from './person';
import { PickerModalComponent } from './picker-modal.component';

/**
 * @title Lookup with a custom picker
 */
@Component({
  selector: 'app-lookup-custom-picker-example',
  templateUrl: './example.component.html',
  imports: [
    CommonModule,
    FormsModule,
    ReactiveFormsModule,
    SkyInputBoxModule,
    SkyLookupModule,
  ],
})
export class LookupCustomPickerExampleComponent implements OnInit {
  public favoritesForm: FormGroup<{
    favoriteNames: FormControl<Person[] | null>;
  }>;

  protected showMoreConfig: SkyLookupShowMoreConfig;

  readonly #modalSvc = inject(SkyModalService);
  readonly #svc = inject(DemoService);
  readonly #waitSvc = inject(SkyWaitService);

  constructor() {
    const names = new FormControl<Person[]>([
      {
        name: 'Shirley',
        formal: 'Ms. Bennett',
      },
    ]);

    this.favoritesForm = inject(FormBuilder).group({
      favoriteNames: names,
    });

    this.showMoreConfig = {
      customPicker: {
        open: (context): void => {
          const instance = this.#modalSvc.open(PickerModalComponent, {
            providers: [
              {
                provide: SkyLookupShowMoreCustomPickerContext,
                useValue: context,
              },
            ],
            size: 'large',
          });

          instance.closed.subscribe((closeArgs) => {
            if (closeArgs.reason === 'save') {
              this.favoritesForm.controls.favoriteNames.setValue(
                closeArgs.data as Person[],
              );
            }
          });
        },
      },
    };
  }

  public ngOnInit(): void {
    // If you need to execute some logic after the lookup values change,
    // subscribe to Angular's built-in value changes observable.
    this.favoritesForm.valueChanges.subscribe((changes) => {
      console.log('Lookup value changes:', changes);
    });
  }

  protected searchAsync(args: SkyAutocompleteSearchAsyncArgs): void {
    // In a real-world application the search service might return an Observable
    // created by calling HttpClient.get(). Assigning that Observable to the result
    // allows the lookup component to cancel the web request if it does not complete
    // before the user searches again.
    args.result = this.#svc.search(args.searchText).pipe(
      map((result) => ({
        hasMore: result.hasMore,
        items: result.people,
        totalCount: result.totalCount,
      })),
    );
  }

  protected addClick(args: SkyLookupAddClickEventArgs): void {
    const person: Person = {
      name: 'Newman',
      formal: 'Mr. Parker',
    };

    this.#waitSvc.blockingWrap(this.#svc.addPerson(person)).subscribe(() => {
      args.itemAdded({
        item: person,
      });
    });
  }

  protected onSubmit(): void {
    alert('Form submitted with: ' + JSON.stringify(this.favoritesForm.value));
  }
}

```

#### example.service.ts

```typescript
import { Injectable } from '@angular/core';

import { Observable, of } from 'rxjs';
import { delay } from 'rxjs/operators';

import { Person } from './person';
import { LookupAsyncDemoSearchResults } from './search-results';

const people: Person[] = [
  {
    name: 'Abed',
    formal: 'Mr. Nadir',
  },
  {
    name: 'Alex',
    formal: 'Mr. Osbourne',
  },
  {
    name: 'Ben',
    formal: 'Mr. Chang',
  },
  {
    name: 'Britta',
    formal: 'Ms. Perry',
  },
  {
    name: 'Buzz',
    formal: 'Mr. Hickey',
  },
  {
    name: 'Craig',
    formal: 'Mr. Pelton',
  },
  {
    name: 'Elroy',
    formal: 'Mr. Patashnik',
  },
  {
    name: 'Garrett',
    formal: 'Mr. Lambert',
  },
  {
    name: 'Ian',
    formal: 'Mr. Duncan',
  },
  {
    name: 'Jeff',
    formal: 'Mr. Winger',
  },
  {
    name: 'Leonard',
    formal: 'Mr. Rodriguez',
  },
  {
    name: 'Neil',
    formal: 'Mr. Neil',
  },
  {
    name: 'Pierce',
    formal: 'Mr. Hawthorne',
  },
  {
    name: 'Preston',
    formal: 'Mr. Koogler',
  },
  {
    name: 'Rachel',
    formal: 'Ms. Rachel',
  },
  {
    name: 'Shirley',
    formal: 'Ms. Bennett',
  },
  {
    name: 'Todd',
    formal: 'Mr. Jacobson',
  },
  {
    name: 'Troy',
    formal: 'Mr. Barnes',
  },
  {
    name: 'Vaughn',
    formal: 'Mr. Miller',
  },
  {
    name: 'Vicki',
    formal: 'Ms. Jenkins',
  },
];

@Injectable({
  providedIn: 'root',
})
export class DemoService {
  public search(searchText: string): Observable<LookupAsyncDemoSearchResults> {
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

  public addPerson(person: Person): Observable<number> {
    // Simulate adding a person with a network call.
    if (!people.some((item) => item.name === person.name)) {
      people.unshift(person);
    }

    return of(1).pipe(delay(800));
  }
}

```

#### person.ts

```typescript
export interface Person {
  name: string;
  formal?: string;
}

```

#### picker-harness.ts

```typescript
import { ComponentHarness } from '@angular/cdk/testing';
import { SkyCheckboxHarness } from '@skyux/forms/testing';

export class PickerHarness extends ComponentHarness {
  /**
   * @internal
   */
  public static hostSelector = '.lookup-custom-picker-modal';

  #getCheckboxes = this.locatorForAll(SkyCheckboxHarness);
  #getSaveButton = this.locatorFor('.lookup-custom-picker-save-button');

  public async checkItemAt(index: number): Promise<void> {
    await (await this.#getCheckboxes())[index].check();
  }

  public async uncheckItemAt(index: number): Promise<void> {
    await (await this.#getCheckboxes())[index].uncheck();
  }

  public async save(): Promise<void> {
    await (await this.#getSaveButton()).click();
  }
}

```

#### picker-modal.component.ts

```typescript
import { ChangeDetectorRef, Component, inject } from '@angular/core';
import {
  FormArray,
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyCheckboxModule, SkySelectionBoxModule } from '@skyux/forms';
import { SkyIconModule } from '@skyux/icon';
import { SkyWaitModule } from '@skyux/indicators';
import { SkyLookupShowMoreCustomPickerContext } from '@skyux/lookup';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';

import { take } from 'rxjs/operators';

import { DemoService } from './example.service';
import { Person } from './person';

@Component({
  selector: 'app-picker-modal',
  templateUrl: './picker-modal.component.html',
  styleUrls: ['./picker-modal.component.scss'],
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyCheckboxModule,
    SkyIconModule,
    SkyModalModule,
    SkySelectionBoxModule,
    SkyWaitModule,
  ],
})
export class PickerModalComponent {
  protected peopleForm?: FormGroup<{
    people: FormArray<FormControl<boolean>>;
  }>;

  protected people: Person[] = [];

  protected readonly context = inject(SkyLookupShowMoreCustomPickerContext);
  readonly #changeDetector = inject(ChangeDetectorRef);
  readonly #formBuilder = inject(FormBuilder);
  readonly #modalInstance = inject(SkyModalInstance);
  readonly #svc = inject(DemoService);

  constructor() {
    // This list of people will be rendered as selection boxes.
    this.#svc
      .search('')
      .pipe(take(1))
      .subscribe((results) => {
        this.people = results.people;

        // Create a control for each selection box.
        this.peopleForm = this.#formBuilder.group({
          people: this.#formBuilder.array(
            this.people.map((item: Person) =>
              this.#formBuilder.control(
                (this.context.initialValue as Person[]).findIndex(
                  (initialItem) => initialItem.name === item.name,
                ) >= 0,
                { nonNullable: true },
              ),
            ),
          ),
        });
        this.#changeDetector.markForCheck();
      });
  }

  protected save(): void {
    // Return a list of selected people to the lookup component.
    const selectedPeople = this.people.filter(
      (_, index) => this.peopleForm?.value.people?.[index],
    );

    this.#modalInstance.save(selectedPeople);
  }
}

```

#### search-results.ts

```typescript
import { Person } from './person';

export interface LookupAsyncDemoSearchResults {
  hasMore: boolean;
  people: Person[];
  totalCount: number;
}

```

#### example.component.html

```html
<form
  class="sky-padding-even-md"
  novalidate
  [formGroup]="favoritesForm"
  (ngSubmit)="onSubmit()"
>
  <sky-input-box
    data-sky-id="favorite-names-field"
    helpPopoverContent="A name can be selected from the list or added as a new name."
    hintText="Choose a name from the list or add a new name."
    labelText="Favorite names"
    stacked
  >
    <sky-lookup
      formControlName="favoriteNames"
      [enableShowMore]="true"
      [showAddButton]="true"
      [showMoreConfig]="showMoreConfig"
      (searchAsync)="searchAsync($event)"
      (addClick)="addClick($event)"
    />
  </sky-input-box>
  <div
    class="sky-border-dark sky-rounded-corners sky-padding-even-md sky-margin-stacked-lg"
  >
    <strong>Form model:</strong>
    <pre>{{ favoritesForm.value | json }}</pre>
  </div>
  <button class="sky-btn sky-btn-default" type="submit">Submit</button>
</form>

```

#### picker-modal.component.html

```html
<sky-modal class="lookup-custom-picker-modal" headingText="Names">
  <sky-modal-content>
    @if (peopleForm) {
      <form [formGroup]="peopleForm">
        <sky-selection-box-grid>
          @for (
            personControl of peopleForm.controls.people.controls;
            track personControl;
            let i = $index
          ) {
            <sky-selection-box [control]="checkbox">
              <sky-icon iconName="person" />
              <sky-selection-box-header>
                {{ people[i].name }}
              </sky-selection-box-header>
              <sky-selection-box-description>
                {{ people[i].formal }}
              </sky-selection-box-description>
              <sky-checkbox #checkbox [formControl]="personControl" />
            </sky-selection-box>
          }
        </sky-selection-box-grid>
      </form>
    } @else {
      <div class="wait-container">
        <sky-wait [isWaiting]="true" />
      </div>
    }
  </sky-modal-content>
  <sky-modal-footer>
    <button
      class="sky-btn sky-btn-primary lookup-custom-picker-save-button"
      type="button"
      (click)="save()"
    >
      Save
    </button>
  </sky-modal-footer>
</sky-modal>

```

#### picker-modal.component.scss

```css
.wait-container {
  height: 100px;
}

```

---

## Lookup in multiple select mode

**Component:** LookupMultiSelectExampleComponent

**Selector:** `app-lookup-multi-select-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyInputBoxHarness } from '@skyux/forms/testing';
import { SkyLookupHarness } from '@skyux/lookup/testing';

import { of } from 'rxjs';

import { LookupMultiSelectExampleComponent } from './example.component';
import { DemoService } from './example.service';

describe('Lookup multi-select example', () => {
  let mockSvc!: jasmine.SpyObj<DemoService>;

  async function setupTest(): Promise<{
    lookupHarness: SkyLookupHarness;
    fixture: ComponentFixture<LookupMultiSelectExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(LookupMultiSelectExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const lookupHarness = await (
      await loader.getHarness(
        SkyInputBoxHarness.with({ dataSkyId: 'favorite-names-field' }),
      )
    ).queryHarness(SkyLookupHarness);

    return { lookupHarness, fixture };
  }

  beforeEach(() => {
    // Create a mock search service. In a real-world application, the search
    // service would make a web request which should be avoided in unit tests.
    mockSvc = jasmine.createSpyObj<DemoService>('DemoService', ['search']);

    TestBed.configureTestingModule({
      imports: [LookupMultiSelectExampleComponent, NoopAnimationsModule],
      providers: [
        {
          provide: DemoService,
          useValue: mockSvc,
        },
      ],
    });
  });

  it('should set the expected initial value', async () => {
    const { lookupHarness } = await setupTest();

    await expectAsync(lookupHarness.getSelectionsText()).toBeResolvedTo([
      'Shirley',
    ]);
  });

  it('should update the form control when a favorite name is selected', async () => {
    const { lookupHarness, fixture } = await setupTest();

    mockSvc.search.and.callFake((searchText) =>
      of({
        hasMore: false,
        people:
          searchText === 'b'
            ? [
                {
                  name: 'Bernard',
                },
              ]
            : [],
        totalCount: 1,
      }),
    );

    await lookupHarness.enterText('b');
    await lookupHarness.selectSearchResult({
      text: 'Bernard',
    });

    expect(fixture.componentInstance.favoritesForm.value.favoriteNames).toEqual(
      [{ name: 'Shirley' }, { name: 'Bernard' }],
    );
  });

  it('should respect the selection descriptor', async () => {
    const { lookupHarness } = await setupTest();

    mockSvc.search.and.callFake(() =>
      of({
        hasMore: false,
        people: [
          {
            id: '21',
            name: 'Bernard',
          },
        ],
        totalCount: 1,
      }),
    );

    await lookupHarness.clickShowMoreButton();

    const picker = await lookupHarness.getShowMorePicker();

    await expectAsync(picker.getSearchAriaLabel()).toBeResolvedTo(
      'Search names',
    );
    await expectAsync(picker.getSaveButtonAriaLabel()).toBeResolvedTo(
      'Select names',
    );
  });
});

```

#### example.component.ts

```typescript
import { CommonModule } from '@angular/common';
import { Component, OnInit, inject } from '@angular/core';
import {
  AbstractControl,
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
  ValidationErrors,
} from '@angular/forms';
import { SkyFormErrorModule, SkyInputBoxModule } from '@skyux/forms';
import { SkyWaitService } from '@skyux/indicators';
import {
  SkyAutocompleteSearchAsyncArgs,
  SkyLookupAddClickEventArgs,
  SkyLookupModule,
  SkyLookupShowMoreConfig,
} from '@skyux/lookup';

import { map } from 'rxjs/operators';

import { DemoService } from './example.service';
import { Person } from './person';

/**
 * @title Lookup in multiple select mode
 */
@Component({
  selector: 'app-lookup-multi-select-example',
  templateUrl: './example.component.html',
  imports: [
    CommonModule,
    FormsModule,
    ReactiveFormsModule,
    SkyFormErrorModule,
    SkyInputBoxModule,
    SkyLookupModule,
  ],
})
export class LookupMultiSelectExampleComponent implements OnInit {
  public favoritesForm: FormGroup<{
    favoriteNames: FormControl<Person[] | null>;
  }>;

  public showMoreConfig: SkyLookupShowMoreConfig = {
    nativePickerConfig: {
      selectionDescriptor: 'names',
    },
  };

  readonly #svc = inject(DemoService);
  readonly #waitSvc = inject(SkyWaitService);

  constructor() {
    const names = new FormControl<Person[]>([{ name: 'Shirley' }], {
      validators: [
        (control: AbstractControl<Person[] | null>): ValidationErrors => {
          if (
            control.value?.some((person) => /e/i.exec(person.name) === null)
          ) {
            return { letterE: true };
          }

          return {};
        },
      ],
    });

    this.favoritesForm = inject(FormBuilder).group({
      favoriteNames: names,
    });
  }

  public ngOnInit(): void {
    // If you need to execute some logic after the lookup values change,
    // subscribe to Angular's built-in value changes observable.
    this.favoritesForm.valueChanges.subscribe((changes) => {
      console.log('Lookup value changes:', changes);
    });
  }

  protected onSubmit(): void {
    alert('Form submitted with: ' + JSON.stringify(this.favoritesForm.value));
  }

  protected searchAsync(args: SkyAutocompleteSearchAsyncArgs): void {
    // In a real-world application the search service might return an Observable
    // created by calling HttpClient.get(). Assigning that Observable to the result
    // allows the lookup component to cancel the web request if it does not complete
    // before the user searches again.
    args.result = this.#svc.search(args.searchText).pipe(
      map((result) => ({
        hasMore: result.hasMore,
        items: result.people,
        totalCount: result.totalCount,
      })),
    );
  }

  protected addClick(args: SkyLookupAddClickEventArgs): void {
    const person: Person = {
      name: 'Newman',
    };

    this.#waitSvc.blockingWrap(this.#svc.addPerson(person)).subscribe(() => {
      args.itemAdded({
        item: person,
      });
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
import { LookupAsyncDemoSearchResults } from './search-results';

const people: Person[] = [
  { name: 'Abed' },
  { name: 'Alex' },
  { name: 'Ben' },
  { name: 'Britta' },
  { name: 'Buzz' },
  { name: 'Craig' },
  { name: 'Elroy' },
  { name: 'Garrett' },
  { name: 'Ian' },
  { name: 'Jeff' },
  { name: 'Leonard' },
  { name: 'Neil' },
  { name: 'Pierce' },
  { name: 'Preston' },
  { name: 'Rachel' },
  { name: 'Shirley' },
  { name: 'Todd' },
  { name: 'Troy' },
  { name: 'Vaughn' },
  { name: 'Vicki' },
];

@Injectable({
  providedIn: 'root',
})
export class DemoService {
  public search(searchText: string): Observable<LookupAsyncDemoSearchResults> {
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

  public addPerson(person: Person): Observable<number> {
    // Simulate adding a person with a network call.
    if (!people.some((item) => item.name === person.name)) {
      people.unshift(person);
    }

    return of(1).pipe(delay(800));
  }
}

```

#### person.ts

```typescript
export interface Person {
  name: string;
}

```

#### search-results.ts

```typescript
import { Person } from './person';

export interface LookupAsyncDemoSearchResults {
  hasMore: boolean;
  people: Person[];
  totalCount: number;
}

```

#### example.component.html

```html
<form
  class="sky-padding-even-md"
  novalidate
  [formGroup]="favoritesForm"
  (ngSubmit)="onSubmit()"
>
  <sky-input-box
    data-sky-id="favorite-names-field"
    helpPopoverContent="A name can be selected from the list or added as a new name."
    hintText="Choose a name from the list or add a new name."
    labelText="Favorite name(s)"
    stacked
  >
    <sky-lookup
      formControlName="favoriteNames"
      idProperty="name"
      [enableShowMore]="true"
      [showAddButton]="true"
      [showMoreConfig]="showMoreConfig"
      (searchAsync)="searchAsync($event)"
      (addClick)="addClick($event)"
    />
    @if (favoritesForm.controls.favoriteNames.errors?.['letterE']) {
      <sky-form-error
        errorName="letterE"
        errorText="Please only choose names that contain the letter E"
      />
    }
  </sky-input-box>
  <div
    class="sky-border-dark sky-rounded-corners sky-padding-even-md sky-margin-stacked-lg"
  >
    <strong>Form model:</strong>
    <pre>{{ favoritesForm.value | json }}</pre>
  </div>
  <button class="sky-btn sky-btn-default" type="submit">Submit</button>
</form>

```

---

## Lookup with custom search results template

**Component:** LookupResultTemplatesExampleComponent

**Selector:** `app-lookup-result-templates-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyInputBoxHarness } from '@skyux/forms/testing';
import { SkyLookupHarness } from '@skyux/lookup/testing';

import { of } from 'rxjs';

import { LookupResultTemplatesExampleComponent } from './example.component';
import { DemoService } from './example.service';
import { ItemHarness } from './item-harness';

describe('Lookup result templates example', () => {
  let mockSvc!: jasmine.SpyObj<DemoService>;

  async function setupTest(): Promise<{
    lookupHarness: SkyLookupHarness;
    fixture: ComponentFixture<LookupResultTemplatesExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      LookupResultTemplatesExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const lookupHarness = await (
      await loader.getHarness(
        SkyInputBoxHarness.with({ dataSkyId: 'favorite-names-field' }),
      )
    ).queryHarness(SkyLookupHarness);

    return { lookupHarness, fixture };
  }

  beforeEach(() => {
    // Create a mock search service. In a real-world application, the search
    // service would make a web request which should be avoided in unit tests.
    mockSvc = jasmine.createSpyObj<DemoService>('DemoService', ['search']);

    TestBed.configureTestingModule({
      imports: [LookupResultTemplatesExampleComponent, NoopAnimationsModule],
      providers: [
        {
          provide: DemoService,
          useValue: mockSvc,
        },
      ],
    });
  });

  it('should set the expected initial value', async () => {
    const { lookupHarness } = await setupTest();

    await expectAsync(lookupHarness.getSelectionsText()).toBeResolvedTo([
      'Shirley',
    ]);
  });

  it('should use the expected dropdown item template', async () => {
    const { lookupHarness } = await setupTest();

    mockSvc.search.and.callFake(() =>
      of({
        hasMore: false,
        people: [
          {
            name: 'Abed',
            formal: 'Mr. Nadir',
          },
        ],
        totalCount: 1,
      }),
    );

    await lookupHarness.enterText('be');

    const results = await lookupHarness.getSearchResults();
    const templateItemHarness =
      results && (await results[0].queryHarness(ItemHarness));

    await expectAsync(templateItemHarness.getName()).toBeResolvedTo('Abed');
    await expectAsync(templateItemHarness.getFormalName()).toBeResolvedTo(
      'Mr. Nadir',
    );
  });

  it('should use the expected modal item template', async () => {
    const { lookupHarness } = await setupTest();

    mockSvc.search.and.callFake(() =>
      of({
        hasMore: false,
        people: [
          {
            name: 'Abed',
            formal: 'Mr. Nadir',
          },
        ],
        totalCount: 1,
      }),
    );

    await lookupHarness.clickShowMoreButton();

    const pickerHarness = await lookupHarness.getShowMorePicker();
    await pickerHarness.enterSearchText('be');

    const results = await pickerHarness.getSearchResults();
    const templateItemHarness =
      results && (await results[0].queryHarness(ItemHarness));

    await expectAsync(templateItemHarness.getName()).toBeResolvedTo('Abed');
    await expectAsync(templateItemHarness.getFormalName()).toBeResolvedTo(
      'Mr. Nadir',
    );
  });

  it('should update the form control when a favorite name is selected', async () => {
    const { lookupHarness, fixture } = await setupTest();

    mockSvc.search.and.callFake(() =>
      of({
        hasMore: false,
        people: [
          {
            name: 'Abed',
            formal: 'Mr. Nadir',
          },
        ],
        totalCount: 1,
      }),
    );

    await lookupHarness.enterText('be');

    const allResultHarnesses = await lookupHarness.getSearchResults();
    const firstResultHarness = allResultHarnesses[0];
    await firstResultHarness.select();

    expect(
      fixture.componentInstance.favoritesForm.controls.favoriteNames.value,
    ).toEqual([
      { name: 'Shirley', formal: 'Ms. Bennett' },
      { name: 'Abed', formal: 'Mr. Nadir' },
    ]);
  });

  it('should respect the selection descriptor', async () => {
    const { lookupHarness } = await setupTest();

    mockSvc.search.and.callFake(() =>
      of({
        hasMore: false,
        people: [
          {
            name: 'Abed',
            formal: 'Mr. Nadir',
          },
        ],
        totalCount: 1,
      }),
    );

    await lookupHarness.clickShowMoreButton();

    const picker = await lookupHarness.getShowMorePicker();

    await expectAsync(picker.getSearchAriaLabel()).toBeResolvedTo(
      'Search names',
    );
    await expectAsync(picker.getSaveButtonAriaLabel()).toBeResolvedTo(
      'Select names',
    );
  });
});

```

#### example.component.ts

```typescript
import { CommonModule } from '@angular/common';
import {
  Component,
  OnInit,
  TemplateRef,
  ViewChild,
  inject,
} from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyWaitService } from '@skyux/indicators';
import {
  SkyAutocompleteSearchAsyncArgs,
  SkyLookupAddClickEventArgs,
  SkyLookupModule,
  SkyLookupShowMoreConfig,
} from '@skyux/lookup';

import { map } from 'rxjs/operators';

import { DemoService } from './example.service';
import { Person } from './person';

/**
 * @title Lookup with custom search results template
 */
@Component({
  selector: 'app-lookup-result-templates-example',
  templateUrl: './example.component.html',
  imports: [
    CommonModule,
    FormsModule,
    ReactiveFormsModule,
    SkyInputBoxModule,
    SkyLookupModule,
  ],
})
export class LookupResultTemplatesExampleComponent implements OnInit {
  public favoritesForm: FormGroup<{
    favoriteNames: FormControl<Person[] | null>;
  }>;

  protected showMoreConfig: SkyLookupShowMoreConfig = {
    nativePickerConfig: {
      selectionDescriptor: 'names',
    },
  };

  @ViewChild('modalItemTemplate')
  protected set modalItemTemplate(template: TemplateRef<unknown>) {
    if (this.showMoreConfig.nativePickerConfig) {
      this.showMoreConfig.nativePickerConfig.itemTemplate = template;
    } else {
      this.showMoreConfig.nativePickerConfig = { itemTemplate: template };
    }
  }

  readonly #svc = inject(DemoService);
  readonly #waitSvc = inject(SkyWaitService);

  constructor() {
    const names = new FormControl<Person[]>([
      {
        name: 'Shirley',
        formal: 'Ms. Bennett',
      },
    ]);

    this.favoritesForm = inject(FormBuilder).group({
      favoriteNames: names,
    });
  }

  public ngOnInit(): void {
    // If you need to execute some logic after the lookup values change,
    // subscribe to Angular's built-in value changes observable.
    this.favoritesForm.valueChanges.subscribe((changes) => {
      console.log('Lookup value changes:', changes);
    });
  }

  protected searchAsync(args: SkyAutocompleteSearchAsyncArgs): void {
    // In a real-world application the search service might return an Observable
    // created by calling HttpClient.get(). Assigning that Observable to the result
    // allows the lookup component to cancel the web request if it does not complete
    // before the user searches again.
    args.result = this.#svc.search(args.searchText).pipe(
      map((result) => ({
        hasMore: result.hasMore,
        items: result.people,
        totalCount: result.totalCount,
      })),
    );
  }

  protected addClick(args: SkyLookupAddClickEventArgs): void {
    const person: Person = {
      name: 'Newman',
      formal: 'Mr. Parker',
    };

    this.#waitSvc.blockingWrap(this.#svc.addPerson(person)).subscribe(() => {
      args.itemAdded({
        item: person,
      });
    });
  }

  protected onSubmit(): void {
    alert('Form submitted with: ' + JSON.stringify(this.favoritesForm.value));
  }
}

```

#### example.service.ts

```typescript
import { Injectable } from '@angular/core';

import { Observable, of } from 'rxjs';
import { delay } from 'rxjs/operators';

import { Person } from './person';
import { LookupAsyncDemoSearchResults } from './search-results';

const people: Person[] = [
  {
    name: 'Abed',
    formal: 'Mr. Nadir',
  },
  {
    name: 'Alex',
    formal: 'Mr. Osbourne',
  },
  {
    name: 'Ben',
    formal: 'Mr. Chang',
  },
  {
    name: 'Britta',
    formal: 'Ms. Perry',
  },
  {
    name: 'Buzz',
    formal: 'Mr. Hickey',
  },
  {
    name: 'Craig',
    formal: 'Mr. Pelton',
  },
  {
    name: 'Elroy',
    formal: 'Mr. Patashnik',
  },
  {
    name: 'Garrett',
    formal: 'Mr. Lambert',
  },
  {
    name: 'Ian',
    formal: 'Mr. Duncan',
  },
  {
    name: 'Jeff',
    formal: 'Mr. Winger',
  },
  {
    name: 'Leonard',
    formal: 'Mr. Rodriguez',
  },
  {
    name: 'Neil',
    formal: 'Mr. Neil',
  },
  {
    name: 'Pierce',
    formal: 'Mr. Hawthorne',
  },
  {
    name: 'Preston',
    formal: 'Mr. Koogler',
  },
  {
    name: 'Rachel',
    formal: 'Ms. Rachel',
  },
  {
    name: 'Shirley',
    formal: 'Ms. Bennett',
  },
  {
    name: 'Todd',
    formal: 'Mr. Jacobson',
  },
  {
    name: 'Troy',
    formal: 'Mr. Barnes',
  },
  {
    name: 'Vaughn',
    formal: 'Mr. Miller',
  },
  {
    name: 'Vicki',
    formal: 'Ms. Jenkins',
  },
];

@Injectable({
  providedIn: 'root',
})
export class DemoService {
  public search(searchText: string): Observable<LookupAsyncDemoSearchResults> {
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

  public addPerson(person: Person): Observable<number> {
    // Simulate adding a person with a network call.
    if (!people.some((item) => item.name === person.name)) {
      people.unshift(person);
    }

    return of(1).pipe(delay(800));
  }
}

```

#### item-harness.ts

```typescript
import { ComponentHarness } from '@angular/cdk/testing';

/**
 * Harness for interacting with a lookup component in tests.
 * @internal
 */
export class ItemHarness extends ComponentHarness {
  /**
   * @internal
   */
  public static hostSelector = '.lookup-example-template-item';

  #getName = this.locatorFor('.lookup-example-template-name');
  #getFormalName = this.locatorFor('.lookup-example-template-formal-name');

  public async getName(): Promise<string> {
    return await (await this.#getName()).text();
  }

  public async getFormalName(): Promise<string> {
    return await (await this.#getFormalName()).text();
  }
}

```

#### person.ts

```typescript
export interface Person {
  name: string;
  formal?: string;
}

```

#### search-results.ts

```typescript
import { Person } from './person';

export interface LookupAsyncDemoSearchResults {
  hasMore: boolean;
  people: Person[];
  totalCount: number;
}

```

#### example.component.html

```html
<form
  class="lookup-example-form"
  novalidate
  [formGroup]="favoritesForm"
  (ngSubmit)="onSubmit()"
>
  <sky-input-box
    data-sky-id="favorite-names-field"
    helpPopoverContent="A name can be selected from the list or added as a new name."
    hintText="Choose a name from the list or add a new name."
    labelText="Favorite names"
    stacked
  >
    <sky-lookup
      formControlName="favoriteNames"
      idProperty="name"
      [enableShowMore]="true"
      [searchResultTemplate]="dropdownItemTemplate"
      [showAddButton]="true"
      [showMoreConfig]="showMoreConfig"
      (addClick)="addClick($event)"
      (searchAsync)="searchAsync($event)"
    />
  </sky-input-box>
  <div
    class="sky-border-dark sky-rounded-corners sky-padding-even-md sky-margin-stacked-lg"
  >
    <strong>Form model:</strong>
    <pre>{{ favoritesForm.value | json }}</pre>
  </div>
  <button class="sky-btn sky-btn-default" type="submit">Submit</button>
</form>

<ng-template #dropdownItemTemplate let-item="item">
  <span class="lookup-example-template-item">
    <strong class="lookup-example-template-name">{{ item.name }}</strong
    ><br />
    <span class="lookup-example-template-formal-name">
      {{ item.formal }}
    </span>
  </span>
</ng-template>
<ng-template #modalItemTemplate let-item="item">
  <span class="lookup-example-template-item">
    <span class="lookup-example-template-name">{{ item.name }}</span
    ><br />
    <i class="lookup-example-template-formal-name">{{ item.formal }}</i>
  </span>
</ng-template>

```

---

## Lookup in single select mode

**Component:** LookupSingleSelectExampleComponent

**Selector:** `app-lookup-single-select-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyInputBoxHarness } from '@skyux/forms/testing';
import { SkyLookupHarness } from '@skyux/lookup/testing';

import { of } from 'rxjs';

import { LookupSingleSelectExampleComponent } from './example.component';
import { DemoService } from './example.service';

describe('Lookup single-select example', () => {
  let mockSvc!: jasmine.SpyObj<DemoService>;

  async function setupTest(): Promise<{
    lookupHarness: SkyLookupHarness;
    fixture: ComponentFixture<LookupSingleSelectExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(LookupSingleSelectExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const lookupHarness = await (
      await loader.getHarness(
        SkyInputBoxHarness.with({ dataSkyId: 'favorite-names-field' }),
      )
    ).queryHarness(SkyLookupHarness);

    return { lookupHarness, fixture };
  }

  beforeEach(() => {
    // Create a mock search service. In a real-world application, the search
    // service would make a web request which should be avoided in unit tests.
    mockSvc = jasmine.createSpyObj<DemoService>('DemoService', ['search']);

    TestBed.configureTestingModule({
      imports: [LookupSingleSelectExampleComponent, NoopAnimationsModule],
      providers: [
        {
          provide: DemoService,
          useValue: mockSvc,
        },
      ],
    });
  });

  it('should set the expected initial value', async () => {
    const { lookupHarness } = await setupTest();

    await expectAsync(lookupHarness.getValue()).toBeResolvedTo('Shirley');
  });

  it('should update the form control when a favorite name is selected', async () => {
    const { lookupHarness, fixture } = await setupTest();

    mockSvc.search.and.callFake((searchText) =>
      of({
        hasMore: false,
        people:
          searchText === 'b'
            ? [
                {
                  name: 'Bernard',
                },
              ]
            : [],
        totalCount: 1,
      }),
    );

    await lookupHarness.enterText('b');
    await lookupHarness.selectSearchResult({
      text: 'Bernard',
    });

    expect(fixture.componentInstance.favoritesForm.value.favoriteName).toEqual([
      { name: 'Bernard' },
    ]);
  });

  it('should respect the selection descriptor', async () => {
    const { lookupHarness } = await setupTest();

    mockSvc.search.and.callFake(() =>
      of({
        hasMore: false,
        people: [
          {
            id: '21',
            name: 'Bernard',
          },
        ],
        totalCount: 1,
      }),
    );

    await lookupHarness.clickShowMoreButton();

    const picker = await lookupHarness.getShowMorePicker();

    await expectAsync(picker.getSearchAriaLabel()).toBeResolvedTo(
      'Search names',
    );
    await expectAsync(picker.getSaveButtonAriaLabel()).toBeResolvedTo(
      'Select names',
    );
  });
});

```

#### example.component.ts

```typescript
import { CommonModule } from '@angular/common';
import { Component, OnInit, inject } from '@angular/core';
import {
  AbstractControl,
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
  ValidationErrors,
} from '@angular/forms';
import { SkyFormErrorModule, SkyInputBoxModule } from '@skyux/forms';
import { SkyWaitService } from '@skyux/indicators';
import {
  SkyAutocompleteSearchAsyncArgs,
  SkyLookupAddClickEventArgs,
  SkyLookupModule,
  SkyLookupShowMoreConfig,
} from '@skyux/lookup';

import { map } from 'rxjs/operators';

import { DemoService } from './example.service';
import { Person } from './person';

/**
 * @title Lookup in single select mode
 */
@Component({
  selector: 'app-lookup-single-select-example',
  templateUrl: './example.component.html',
  imports: [
    CommonModule,
    FormsModule,
    ReactiveFormsModule,
    SkyFormErrorModule,
    SkyInputBoxModule,
    SkyLookupModule,
  ],
})
export class LookupSingleSelectExampleComponent implements OnInit {
  public favoritesForm: FormGroup<{
    favoriteName: FormControl<Person[] | null>;
  }>;

  public showMoreConfig: SkyLookupShowMoreConfig = {
    nativePickerConfig: {
      selectionDescriptor: 'names',
    },
  };

  readonly #svc = inject(DemoService);
  readonly #waitSvc = inject(SkyWaitService);

  constructor() {
    const name = new FormControl<Person[]>([{ name: 'Shirley' }], {
      validators: [
        (control: AbstractControl<Person[] | null>): ValidationErrors => {
          if (
            control.value?.some((person) => /e/i.exec(person.name) === null)
          ) {
            return { letterE: true };
          }

          return {};
        },
      ],
    });

    this.favoritesForm = inject(FormBuilder).group({
      favoriteName: name,
    });
  }

  public ngOnInit(): void {
    // If you need to execute some logic after the lookup values change,
    // subscribe to Angular's built-in value changes observable.
    this.favoritesForm.valueChanges.subscribe((changes) => {
      console.log('Lookup value changes:', changes);
    });
  }

  protected onSubmit(): void {
    alert('Form submitted with: ' + JSON.stringify(this.favoritesForm.value));
  }

  protected searchAsync(args: SkyAutocompleteSearchAsyncArgs): void {
    // In a real-world application the search service might return an Observable
    // created by calling HttpClient.get(). Assigning that Observable to the result
    // allows the lookup component to cancel the web request if it does not complete
    // before the user searches again.
    args.result = this.#svc.search(args.searchText).pipe(
      map((result) => ({
        hasMore: result.hasMore,
        items: result.people,
        totalCount: result.totalCount,
      })),
    );
  }

  protected addClick(args: SkyLookupAddClickEventArgs): void {
    const person: Person = {
      name: 'Newman',
    };

    this.#waitSvc.blockingWrap(this.#svc.addPerson(person)).subscribe(() => {
      args.itemAdded({
        item: person,
      });
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
import { LookupAsyncDemoSearchResults } from './search-results';

const people: Person[] = [
  { name: 'Abed' },
  { name: 'Alex' },
  { name: 'Ben' },
  { name: 'Britta' },
  { name: 'Buzz' },
  { name: 'Craig' },
  { name: 'Elroy' },
  { name: 'Garrett' },
  { name: 'Ian' },
  { name: 'Jeff' },
  { name: 'Leonard' },
  { name: 'Neil' },
  { name: 'Pierce' },
  { name: 'Preston' },
  { name: 'Rachel' },
  { name: 'Shirley' },
  { name: 'Todd' },
  { name: 'Troy' },
  { name: 'Vaughn' },
  { name: 'Vicki' },
];

@Injectable({
  providedIn: 'root',
})
export class DemoService {
  public search(searchText: string): Observable<LookupAsyncDemoSearchResults> {
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

  public addPerson(person: Person): Observable<number> {
    // Simulate adding a person with a network call.
    if (!people.some((item) => item.name === person.name)) {
      people.unshift(person);
    }

    return of(1).pipe(delay(800));
  }
}

```

#### person.ts

```typescript
export interface Person {
  name: string;
}

```

#### search-results.ts

```typescript
import { Person } from './person';

export interface LookupAsyncDemoSearchResults {
  hasMore: boolean;
  people: Person[];
  totalCount: number;
}

```

#### example.component.html

```html
<form
  class="sky-padding-even-md"
  novalidate
  [formGroup]="favoritesForm"
  (ngSubmit)="onSubmit()"
>
  <sky-input-box
    data-sky-id="favorite-names-field"
    helpPopoverContent="A name can be selected from the list or added as a new name."
    hintText="Choose a name from the list or add a new name."
    labelText="Favorite name"
    stacked
  >
    <sky-lookup
      formControlName="favoriteName"
      idProperty="name"
      [enableShowMore]="true"
      [selectMode]="'single'"
      [showAddButton]="true"
      [showMoreConfig]="showMoreConfig"
      (searchAsync)="searchAsync($event)"
      (addClick)="addClick($event)"
    />
    @if (favoritesForm.controls.favoriteName.errors?.['letterE']) {
      <sky-form-error
        errorName="letterE"
        errorText="Please only choose a name that contain the letter E"
      />
    }
  </sky-input-box>
  <div
    class="sky-border-dark sky-rounded-corners sky-padding-even-md sky-margin-stacked-lg"
  >
    <strong>Form model:</strong>
    <pre>{{ favoritesForm.value | json }}</pre>
  </div>
  <button class="sky-btn sky-btn-default" type="submit">Submit</button>
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