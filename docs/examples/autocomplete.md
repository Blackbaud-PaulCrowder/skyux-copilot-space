---
component: 'autocomplete'
type: 'code-examples'
description: 'Code examples for the autocomplete component.'
---

# Autocomplete Code Examples

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