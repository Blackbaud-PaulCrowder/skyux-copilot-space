---
component: 'lookup'
description: 'Design guidelines, API documentation, and usage instructions for the lookup component extracted from SKY UX documentation.'
---

# Lookup Component Guidelines

## Component Overview
The lookup text input lets users search a long list of options and make selections. Lookup fields must be wrapped in input boxes to provide styling, ordering, and positioning within forms.

## Usage

### ✅ Use when

Use lookup fields when users must choose one or more options from a very long list or from an unpredictable list with unfamiliar options. Lookup fields allow users to enter search criteria to narrow their options, so they are useful when lists are unique to the system. For example, use lookup fields for user-defined lists such as code tables where the options are unpredictable and for system-defined lists such as templates where the options are unique to the organization.

Use lookup fields when users can choose multiple options from a long list.

Use lookup fields when users can add options to the list during their tasks.

### ❌ Don't use when

Don't use lookup fields when short lists include 5 options or fewer, especially if it is valuable for users to see all options at once. Use checkboxes or radio buttons instead.

Don't use lookup fields when options are highly predictable or when users can easily browse options in an expected order. Use HTML select fields instead. For example, while a list of states is long, it's predictable and most users are familiar with the options, so the native HTML select field is the preferable option.

Don't use lookup fields when users need to interact with the selected options or when the options require more depth than lookup tokens provide. Instead, use a button to open a selection modal where users can select options, and then display selections in whatever format is needed.

## Anatomy

### Search results

- Label
- Search button
- Input field
- Required field marker
- Help inline button
- Hint text

## Options

### Single-select and multi-select

Use a single-select to let users select a single option and multi-select to let users select multiple options.

### Required field marker

When a lookup field is required, a red asterisk appears to the right of the label. It includes the appropriate ARIA attributes to support users of assistive technologies. For more information about required fields, see the form design guidelines.

### Help inline button

When you need to supplement a lookup field with additional information but don't require persistent inline help, you can place a help inline button beside the label to invoke contextual user assistance.

### Hint text

To highlight important considerations about a lookup field, use hint text. This persistent inline help can explain details such as:

- The correct format
- Any constraints on the input
- Additional instructions or context, such as how data is used

### Stacked margin

For consistent vertical spacing when a lookup field is immediately followed by another form input, use stacked to add a bottom margin that visually separates the lookup from the form input under it. For more information about spacing on forms, see the form layout guidelines.

Don't use stacked when the lookup:

- Is the last input before a field group
- Is the last input on a form
- Is followed by one or more conditional fields (use sky-margin-stacked-sm instead for closely related fields)

### Button to view all options

The 'Show all/matches' button in the lookup menu lets users open a picker that either displays all options or just the options that match their search string. This button is technically optional for backwards compatibility, but we strongly recommend that you enable it in all instances.

### Custom results template

Use a custom results template when users need more information in the search results to help them select the correct options.

### Custom picker

By default, the search and "Show all/matches" buttons display a selection modal with a selectable repeater. When different presentations are valuable, use custom pickers, such as custom repeaters or tree views. By default, both the native picker and custom pickers format options based on the same template as the dropdown list, but you can specify a different template to format the picker options as necessary.

## Behavior and states

### Behavior

When users place focus on lookup fields, the lookup menu displays the 'Show all #' button. It also displays the 'New' button if that is enabled.

When users enter the minimum number of characters for search, the lookup menu displays search results and highlights the search string. The “Show all #” button label changes to “Show matches (#)."

At any time, users can select the search or 'Show all/matches' buttons to open a picker that either displays all options or the options that match their search string.

When users choose an option in single-select mode, the lookup menu or picker closes, and the selected option appears as text in the lookup field.

When users choose options in multi-select mode, the selected options appear as tokens in the text input field, and focus returns to the lookup field. The lookup menu displays the 'Show all #' button but does not display search results until users enter the minimum number of characters.

When users remove focus before selecting an option, the lookup field deletes any text.

## Related information

### Components

- Checkbox
- Field group
- Help inline button
- Input box
- Radio button
- Selection modal

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

#### LookupCountryFieldBasicExampleComponent

**Selector:** `app-lookup-country-field-basic-example`

**Package:** `@skyux/code-examples`

#### LookupAddItemExampleComponent

**Selector:** `app-lookup-add-item-example`

**Package:** `@skyux/code-examples`

#### LookupCustomPickerExampleComponent

**Selector:** `app-lookup-custom-picker-example`

**Package:** `@skyux/code-examples`

#### LookupMultiSelectExampleComponent

**Selector:** `app-lookup-multi-select-example`

**Package:** `@skyux/code-examples`

#### LookupResultTemplatesExampleComponent

**Selector:** `app-lookup-result-templates-example`

**Package:** `@skyux/code-examples`

#### LookupSingleSelectExampleComponent

**Selector:** `app-lookup-single-select-example`

**Package:** `@skyux/code-examples`

#### LookupSearchBasicExampleComponent

**Selector:** `app-lookup-search-basic-example`

**Package:** `@skyux/code-examples`

#### LookupSelectionModalAddItemExampleComponent

**Selector:** `app-lookup-selection-modal-add-item-example`

**Package:** `@skyux/code-examples`

#### LookupSelectionModalBasicExampleComponent

**Selector:** `app-lookup-selection-modal-basic-example`

**Package:** `@skyux/code-examples`

#### SkyAgGridCellEditorLookupComponent

**Selector:** `sky-ag-grid-cell-editor-lookup`

**Package:** `@skyux/ag-grid`

#### SkyAgGridCellRendererLookupComponent

**Selector:** `sky-cell-renderer-lookup`

**Package:** `@skyux/ag-grid`

#### SkyCellEditorLookupParams

**Package:** `@skyux/ag-grid`

#### SkyAgGridLookupProperties

**Package:** `@skyux/ag-grid`

#### SkyLookupComponent

**Selector:** `sky-lookup`

**Package:** `@skyux/lookup`

**Inputs:**

- `ariaLabel`: `string | undefined` - The ARIA label for the typeahead search input. This sets the input's `aria-label` attribute to provide a text equivalent for
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the input includes a visible label, use `ariaLabelledBy` instead.
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `ariaLabelledBy`: `string | undefined` - The HTML element ID of the element that labels
the typeahead search input. This sets the input's `aria-labelledby` attribute to provide a text equivalent for
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the input does not include a visible label, use `ariaLabel` instead.
For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).
- `autocompleteAttribute`: `string | undefined` - The value for the `autocomplete` attribute on the form input. (default: 'off')
- `debounceTime`: `number | undefined` - How many milliseconds to wait before searching while users
enter text in the lookup field. (default: 0)
- `disabled`: `boolean` - Whether to disable the lookup field on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync.
To set the disabled state on reactive forms, use the `FormControl` instead. (default: false)
- `enableShowMore`: `boolean` - Whether to enable users to open a picker where they can view all options. (default: false)
- `idProperty`: `string | undefined` - The object property that represents the object's unique identifier.
Specifying this property enables token animations and more efficient rendering.
This property is required when using `enableShowMore` and `searchAsync` together.
- `placeholderText`: `string | undefined` - Placeholder text to display in the lookup field.
- `searchResultsLimit`: `number | undefined` - The maximum number of search results to display in the dropdown
list. By default, the lookup component displays all matching results.
This property has no effect on the results in the "Show more" picker.
- `searchResultTemplate`: `TemplateRef<unknown> | undefined` - The template that formats each option in the dropdown list. The lookup component
injects values into the template as `item` variables that reference all the object
properties of the options.
- `searchTextMinimumCharacters`: `number | undefined` - The minimum number of characters that users must enter before
the lookup component searches the data source and displays search results
in the dropdown list. (default: 1)
- `showAddButton`: `boolean` - Whether to display a button that lets users add options to the list. (default: false)
- `showMoreConfig`: `SkyLookupShowMoreConfig | undefined` - Configuration options for the picker that displays all options.
- `wrapperClass`: `string | undefined`
- `data`: `any[]` - The data source for the lookup component to search when users
enter text. You can specify static data such as an array of objects, or
you can pull data from a database. (default: [])
- `descriptorProperty`: `string` - The object property to display in the text input after users
select an item in the dropdown list. (default: "name")
- `propertiesToSearch`: `string[]` - The array of object properties to search when utilizing the `data` property and the built-in search function. (default: ["name"])
- `required`: `boolean` - Whether the lookup field is required. (default: false)
- `search`: `SkyAutocompleteSearchFunction | undefined` - The function to dynamically manage the data source when users
change the text in the lookup field. The search function must return
an array or a promise of an array. The `search` property is particularly
useful when the data source does not live in the source code.
- `searchFilters`: `SkyAutocompleteSearchFunctionFilter[] | undefined` - The array of functions to call against each search result in order
to filter the search results when using the `data` input and the default search function. When
using a custom search function via the `search` property filters must be
applied manually inside that function. The function must return `true` or
`false` for each result to indicate whether to display it in the dropdown list.
- `selectMode`: `SkyLookupSelectModeType` - The ability for users to select one option or multiple options. (default: "multiple")

**Outputs:**

- `addClick`: `EventEmitter<SkyLookupAddClickEventArgs>` - Fires when users select the button to add options to the list.
- `openChange`: `EventEmitter<boolean>`
- `searchAsync`: `EventEmitter<SkyAutocompleteSearchAsyncArgs>` - Fires when users enter new search information and allows results to be
returned via an observable. The event is also fired with empty search text
when the "Show more" picker is opened without search text.
- `selectionModalOpenChange`: `EventEmitter<boolean>`

#### SkyLookupModule

**Package:** `@skyux/lookup`

#### SkyLookupAddCallbackArgs

Specifies the information for the callback used when adding a new item to the lookup component.

**Package:** `@skyux/lookup`

#### SkyLookupAddClickEventArgs

Specifies a callback function for the consumer to use to notify the lookup that a new item has been added.

**Package:** `@skyux/lookup`

#### SkyLookupSelectModeType

**Package:** `@skyux/lookup`

#### SkyLookupSelectMode

**Package:** `@skyux/lookup`

⚠️ **This component is deprecated.**

#### SkyLookupShowMoreConfig

Specifies configuration options for the picker to display when users select the button
to view all options. You can use a native, out-of-the-box modal picker, or you can create
a custom picker. If you provide configuration options for both, the lookup component uses
the custom configuration.

**Package:** `@skyux/lookup`

#### SkyLookupShowMoreCustomPickerContext

Specifies configuration options to launch a custom picker when users select
the button to view all options.

**Package:** `@skyux/lookup`

#### SkyLookupShowMoreCustomPicker

Defines a custom picker to display when users select the button to view all options.

**Package:** `@skyux/lookup`

#### SkyLookupShowMoreNativePickerConfig

Specifies configuration options to display the native picker when users select
the button to view all options.

**Package:** `@skyux/lookup`

#### SkyLookupHarnessFilters

A set of criteria that can be used to filter a list of `SkyLookupHarness` instances.

**Package:** `@skyux/lookup/testing`

#### SkyLookupHarness

Harness for interacting with a lookup component in tests.

**Package:** `@skyux/lookup/testing`

#### SkyLookupSearchResultHarnessFilters

A set of criteria that can be used to filter a list of `SkyLookupSearchResultHarness` instances.

**Package:** `@skyux/lookup/testing`

#### SkyLookupSearchResultHarness

Harness for interacting with an autocomplete search result in tests.

**Package:** `@skyux/lookup/testing`

#### SkyLookupSelectionHarness

Harness for interacting with a multiselect lookup selection in tests.

**Package:** `@skyux/lookup/testing`

#### SkyLookupSelectionsListHarness

Harness for interacting with multiselect lookup selections in tests.

**Package:** `@skyux/lookup/testing`

#### SkyLookupShowMorePickerHarnessFilters

A set of criteria that can be used to filter a list of `SkyLookupShowMorePickerHarness` instances.

**Package:** `@skyux/lookup/testing`

#### SkyLookupShowMorePickerHarness

Harness for interacting with a lookup's "Show more" picker in tests.

**Package:** `@skyux/lookup/testing`

#### SkyLookupShowMorePickerSearchResultHarnessFilters

A set of criteria that can be used to filter a list of `SkyLookupShowMorePickerSearchResultHarness` instances.

**Package:** `@skyux/lookup/testing`

#### SkyLookupShowMorePickerSearchResultHarness

Harness for interacting with a lookup's "Show more" picker search results in tests.

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

#### Country field with basic setup

**Selector:** `app-lookup-country-field-basic-example`

**TypeScript:**

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

**Template:**

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

#### Lookup with add item button

**Selector:** `app-lookup-add-item-example`

**TypeScript:**

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

**Template:**

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

#### Lookup with a custom picker

**Selector:** `app-lookup-custom-picker-example`

**TypeScript:**

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

**Template:**

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

#### Lookup in multiple select mode

**Selector:** `app-lookup-multi-select-example`

**TypeScript:**

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

**Template:**

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

#### Lookup with custom search results template

**Selector:** `app-lookup-result-templates-example`

**TypeScript:**

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

**Template:**

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

#### Lookup in single select mode

**Selector:** `app-lookup-single-select-example`

**TypeScript:**

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

**Template:**

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

#### Search with basic setup

**Selector:** `app-lookup-search-basic-example`

**TypeScript:**

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

**Template:**

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

#### Selection modal with add item functionality

**Selector:** `app-lookup-selection-modal-add-item-example`

**TypeScript:**

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

**Template:**

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

#### Selection modal with basic setup

**Selector:** `app-lookup-selection-modal-basic-example`

**TypeScript:**

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

**Template:**

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

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.