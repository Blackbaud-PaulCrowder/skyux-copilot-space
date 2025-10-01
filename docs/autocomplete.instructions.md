---
component: 'autocomplete'
description: 'Design guidelines, API documentation, and usage instructions for the autocomplete component extracted from SKY UX documentation.'
---

# Autocomplete Component Guidelines

## Component Overview
The autocomplete text input filters a data source based on user entries and then displays search results in a dropdown list.

## Usage

### ✅ Use when

Use the autocomplete component when users know what they are looking for and can select a single item. For guidance on which selection inputs to use in other scenarios, see the form design guidelines.

## Related information

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### LookupAutocompleteAdvancedExampleComponent

**Selector:** `app-lookup-autocomplete-advanced-example`

**Package:** `@skyux/code-examples`

#### LookupAutocompleteAnyValueExampleComponent

**Selector:** `app-lookup-autocomplete-basic-example`

**Package:** `@skyux/code-examples`

#### LookupAutocompleteBasicExampleComponent

**Selector:** `app-lookup-autocomplete-basic-example`

**Package:** `@skyux/code-examples`

#### LookupAutocompleteCustomSearchExampleComponent

**Selector:** `app-lookup-autocomplete-custom-search-example`

**Package:** `@skyux/code-examples`

#### LookupAutocompleteSearchFiltersExampleComponent

**Selector:** `app-lookup-autocomplete-search-filters-example`

**Package:** `@skyux/code-examples`

#### SkyAgGridCellEditorAutocompleteComponent

**Selector:** `sky-ag-grid-cell-editor-autocomplete`

**Package:** `@skyux/ag-grid`

#### SkyAgGridAutocompleteProperties

**Package:** `@skyux/ag-grid`

#### SkyAutocompleteProperties

**Package:** `@skyux/ag-grid`

⚠️ **This component is deprecated.**

#### SkyCellEditorAutocompleteParams

**Package:** `@skyux/ag-grid`

#### SkyAutocompleteInputDirective

**Selector:** `input[skyAutocomplete], textarea[skyAutocomplete]`

**Package:** `@skyux/lookup`

**Inputs:**

- `autocompleteAttribute`: `string` - The value for the `autocomplete` attribute on the form input. (default: "off")
- `disabled`: `boolean` - Whether to disable the autocomplete field on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync.
To set the disabled state on reactive forms, use the `FormControl` instead. (default: false)

#### SkyAutocompleteComponent

**Selector:** `sky-autocomplete`

**Package:** `@skyux/lookup`

**Inputs:**

- `allowAnyValue`: `InputSignalWithTransform<boolean, unknown>` - When using `searchAsync`, allows the user to specify arbitrary
values not in the search results. This only works in combination
with `searchAsync`. (default: false)
- `ariaLabelledBy`: `string | undefined` - The HTML element ID of the element that labels
the autocomplete text input. This sets the input's `aria-labelledby` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).
- `dropdownHintText`: `string | undefined` - Hint text to show in the dropdown
- `highlightSearchText`: `InputSignalWithTransform<boolean, unknown>` - Highlights the search text in each search result. Set this to false
when your search finds results that are not exact text matches, e.g.
returning "Bob" for the term "Robert." (default: true)
- `noResultsFoundText`: `string | undefined` - The text to display when no search results are found. (default: "No matches found")
- `searchAsyncDisabled`: `boolean | undefined` - Allows async search to be disabled even when a listener is specified for
the `searchAsync` output. (default: false)
- `searchResultTemplate`: `TemplateRef<unknown> | undefined` - The template that formats each search result in the dropdown list.
The autocomplete component injects search result values into the template
as `item` variables that reference all of the object properties of the search results.
- `wrapperClass`: `string | undefined`
- `data`: `any[]` - The static data source for the autocomplete component to search
when users enter text. For a dynamic data source such as an array that
changes due to server calls, use `search` or `searchAsync` instead.
- `debounceTime`: `number` - How many milliseconds to wait before searching while users
enter text in the autocomplete field. (default: 0)
- `descriptorProperty`: `string` - The object property to display in the text input after users
select an item in the dropdown list. (default: "name")
- `enableShowMore`: `boolean` - Whether to display a button in the dropdown that opens a picker where users can view all options.
- `messageStream`: `Subject<SkyAutocompleteMessage>` - The observable of `SkyAutocompleteMessage` that can close the dropdown.
- `propertiesToSearch`: `string[]` - The object properties to search. (default: ["name"])
- `search`: `SkyAutocompleteSearchFunction | undefined` - The function that dynamically manages the data source when users
change the text in the autocomplete field. The search function must return
an array or a promise of an array. The `search` property is particularly
useful when the data source does not live in the source code.
- `searchFilters`: `SkyAutocompleteSearchFunctionFilter[] | undefined` - The array of functions to call against each search result in order
to filter the search results when using the default search function. When
using the `search` property to specify a custom search function, you must
manually apply filters inside that function. The function must return `true`
or `false` for each result to indicate whether to display it in the dropdown list.
- `searchResultsLimit`: `number` - The maximum number of search results to display in the dropdown list.
By default, the component displays all matching results.
- `searchTextMinimumCharacters`: `number` - The minimum number of characters that users must enter before
the autocomplete component searches the data source and displays search
results in the dropdown list. (default: 1)
- `showAddButton`: `boolean` - Whether to display a button that lets users add options to the data source. (default: false)

**Outputs:**

- `addClick`: `EventEmitter<void>` - Fires when users select the button to add options to the data source.
- `openChange`: `EventEmitter<boolean>`
- `searchAsync`: `EventEmitter<SkyAutocompleteSearchAsyncArgs>` - Fires when users enter new search information and allows results to be
returned via an observable.
- `selectionChange`: `EventEmitter<SkyAutocompleteSelectionChange>` - Fires when users select items in the dropdown list.
- `showMoreClick`: `EventEmitter<SkyAutocompleteShowMoreArgs>` - Fires when users select the button to view all options.

#### SkyAutocompleteModule

**Package:** `@skyux/lookup`

#### SkyAutocompleteDefaultSearchFunctionOptions

**Package:** `@skyux/lookup`

#### SkyAutocompleteInputTextChange

**Package:** `@skyux/lookup`

#### SkyAutocompleteSearchArgs

**Package:** `@skyux/lookup`

#### SkyAutocompleteSearchAsyncArgs

Arguments passed when an asynchronous search is executed from the
autocomplete or lookup component.

**Package:** `@skyux/lookup`

#### AutocompleteSearchAsyncResultDisplayType

**Package:** `@skyux/lookup`

#### SkyAutocompleteSearchAsyncResult

The result of searching for items to display in an autocomplete or lookup field.

**Package:** `@skyux/lookup`

#### SkyAutocompleteSearchContext

**Package:** `@skyux/lookup`

#### SkyAutocompleteSearchFunctionFilter

**Package:** `@skyux/lookup`

#### SkyAutocompleteSearchFunctionResponse

**Package:** `@skyux/lookup`

#### SkyAutocompleteSearchFunction

**Package:** `@skyux/lookup`

#### SkyAutocompleteSelectionChange

**Package:** `@skyux/lookup`

#### SkyAutocompleteHarnessFilters

A set of criteria that can be used to filter a list of SkyAutocompleteHarness instances.

**Package:** `@skyux/lookup/testing`

#### SkyAutocompleteHarness

Harness for interacting with an autocomplete component in tests.

**Package:** `@skyux/lookup/testing`

#### SkyAutocompleteInputHarness

Harness to interact with the autocomplete input harness.

**Package:** `@skyux/lookup/testing`

#### SkyAutocompleteSearchResultHarnessFilters

A set of criteria that can be used to filter a list of SkyAutocompleteSearchResultHarness instances.

**Package:** `@skyux/lookup/testing`

#### SkyAutocompleteSearchResultHarness

Harness for interacting with an autocomplete search result in tests.

**Package:** `@skyux/lookup/testing`

### Code Examples

#### Advanced example

**Selector:** `app-lookup-autocomplete-advanced-example`

**TypeScript:**

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

**Template:**

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

#### Autocomplete with any value allowed

**Selector:** `app-lookup-autocomplete-basic-example`

**TypeScript:**

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

**Template:**

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

#### Autocomplete with basic setup

**Selector:** `app-lookup-autocomplete-basic-example`

**TypeScript:**

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

**Template:**

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

#### Autocomplete with custom search

**Selector:** `app-lookup-autocomplete-custom-search-example`

**TypeScript:**

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

**Template:**

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

#### Autocomplete with search filters

**Selector:** `app-lookup-autocomplete-search-filters-example`

**TypeScript:**

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

**Template:**

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

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.