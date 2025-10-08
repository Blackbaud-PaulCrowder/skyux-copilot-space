# Design

                   Skip to Main Content

 Character count
===============

The character count indicator extends a text input to apply a character limit and display the number of characters entered and the character limit.

 Usage
------

### Use when

Use character count indicators when users are likely to exceed character limits. Indicators are useful when technical requirements lead to restrictive character limits or when user entries are freeform and could be very long.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-usage-1.8e79a2112b6194f5331735bbed6d7ffb.png)

Do use character count indicators on input fields where users may realistically exceed character limits.

### Don't use when

Don't use character count indicators when character limits are apparent or implied by the data type.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-usage-2.9b9830a2dbe15378ee72d3cf4f25ae44.png)

Don't use character count indicators on input fields where user entries follow expected or standard lengths.

Don't use character count indicators on inputs when users are unlikely to exceed character limits. Use [normal form validation](/skyux/design/guidelines/form-design#validation-and-error-handling.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-usage-3.17dcdab2217ed1f6e1aee34dd9d4e3ca.png)

Don't use character count indicators on input fields where users should not realistically exceed character limits.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-usage-4.98bdaa3f7d1cb893abbfba04e6e8ec1b.png)

Do use normal form validation for edge cases where users exceed character limits.

 Anatomy
--------

1

Input field

2

[Status indicator](/skyux/components/status-indicator.md) (danger)

3

Character count indicator (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-anatomy.1153f353f3226ebf3f4d487a79e930cd.png)

 Options
--------

### Character count indicator

The character count indicator displays the number of characters that users enter, the character limit, and a danger icon if users exceed the limit. For inputs where users are unlikely to reach the character limit, you don't need to display the character count indicator.

 Behavior and states
--------------------

The character count indicator component extends the form classes that define styles and the appearance of input field states.

Empty field

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-state-1.e5bc816ce3b83ad3c040e3ea8f62b3cb.png)

Adding text

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-state-2.f99f02c213fd6ebfb2288546787c5f34.png)

At the character limit

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-state-3.8721dc7c64aff3a02ede8101f09cc9ba.png)

Over the character limit

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-state-4.b4189b6795194360a850ec5a952a70a6.png)

 Content
--------

For validation messages when users exceed character limits, use the following format:

**Limit <input field label> to <n> characters.**

 Layout
-------

The character count indicator always appears in the top right above the input field. Long field labels do not displace indicators. The labels wrap to multiple lines instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-layout.edab30d4d4a87a01e935ec16149f47d6.png)

 Related information
--------------------

### Components

*   [Input box](/skyux/components/input-box.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/character-counter/character-counter.module.ts#L28) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 SkyCharacterCounterModule
--------------------------

Type: Module

`import { SkyCharacterCounterModule } from '@skyux/forms';`

 SkyCharacterCounterIndicatorComponent
--------------------------------------

Type: Component

Selector: `sky-character-counter-indicator`

 SkyCharacterCounterInputDirective
----------------------------------

Type: Directive

Selector: `[skyCharacterCounter]`

Creates an input field that validates the number of characters. Place this directive on an `input` or `textarea` element. If users enter more characters than allowed, then the input field is invalid and the component displays an error indicator.

### Inputs

#### `skyCharacterCounterLimit: number | undefined`

Required

The maximum number of characters allowed in the input field. Place this directive on an `input` or `textarea` element. This property accepts `number` values.

#### `skyCharacterCounterIndicator: SkyCharacterCounterIndicatorComponent | undefined`

The character count indicator component that displays the character count, character limit, and over-the-limit indicator. Place this directive on an `input` or `textarea` element.

 SkyCharacterCounterScreenReaderPipe
------------------------------------

Type: Pipe

Pipe name: `skyCharacterCounterScreenReader`

### Methods

#### `transform(characterCount: number | undefined, characterCountLimit: number | undefined): string`

#### Parameters

##### `characterCount: number | undefined`

##### `characterCountLimit: number | undefined`

#### Returns

`string`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyCharacterCounterIndicatorHarness
------------------------------------

Type: Class

`import { SkyCharacterCounterIndicatorHarness } from '@skyux/forms/testing';`

Harness for interacting with a character counter indicator component in tests.

### Methods

#### `getCharacterCount(): Promise<number>`

Gets the current character count.

#### Returns

`Promise<number>`

#### `getCharacterCountLimit(): Promise<number>`

Gets the character counter limit.

#### Returns

`Promise<number>`

#### `isOverLimit(): Promise<boolean>`

Indicates whether the character counter is in an error state because the current character count is greater than the limit.

#### Returns

`Promise<boolean>`

#### `SkyCharacterCounterIndicatorHarness.with(filters: SkyCharacterCounterIndicatorHarnessFilters): HarnessPredicate<SkyCharacterCounterIndicatorHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyCharacterCounterIndicatorHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyCharacterCounterIndicatorHarnessFilters`

#### Returns

`HarnessPredicate<SkyCharacterCounterIndicatorHarness>`

 SkyCharacterCounterIndicatorHarnessFilters
-------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyCharacterCounterIndicatorHarness](/skyux/components/character-count?docs-active-tab=design#class_sky-character-counter-indicator-harness.md) instances.

    interface SkyCharacterCounterIndicatorHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Development

                   Skip to Main Content

 Character count
===============

The character count indicator extends a text input to apply a character limit and display the number of characters entered and the character limit.

 Usage
------

### Use when

Use character count indicators when users are likely to exceed character limits. Indicators are useful when technical requirements lead to restrictive character limits or when user entries are freeform and could be very long.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-usage-1.8e79a2112b6194f5331735bbed6d7ffb.png)

Do use character count indicators on input fields where users may realistically exceed character limits.

### Don't use when

Don't use character count indicators when character limits are apparent or implied by the data type.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-usage-2.9b9830a2dbe15378ee72d3cf4f25ae44.png)

Don't use character count indicators on input fields where user entries follow expected or standard lengths.

Don't use character count indicators on inputs when users are unlikely to exceed character limits. Use [normal form validation](/skyux/design/guidelines/form-design#validation-and-error-handling.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-usage-3.17dcdab2217ed1f6e1aee34dd9d4e3ca.png)

Don't use character count indicators on input fields where users should not realistically exceed character limits.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-usage-4.98bdaa3f7d1cb893abbfba04e6e8ec1b.png)

Do use normal form validation for edge cases where users exceed character limits.

 Anatomy
--------

1

Input field

2

[Status indicator](/skyux/components/status-indicator.md) (danger)

3

Character count indicator (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-anatomy.1153f353f3226ebf3f4d487a79e930cd.png)

 Options
--------

### Character count indicator

The character count indicator displays the number of characters that users enter, the character limit, and a danger icon if users exceed the limit. For inputs where users are unlikely to reach the character limit, you don't need to display the character count indicator.

 Behavior and states
--------------------

The character count indicator component extends the form classes that define styles and the appearance of input field states.

Empty field

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-state-1.e5bc816ce3b83ad3c040e3ea8f62b3cb.png)

Adding text

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-state-2.f99f02c213fd6ebfb2288546787c5f34.png)

At the character limit

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-state-3.8721dc7c64aff3a02ede8101f09cc9ba.png)

Over the character limit

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-state-4.b4189b6795194360a850ec5a952a70a6.png)

 Content
--------

For validation messages when users exceed character limits, use the following format:

**Limit <input field label> to <n> characters.**

 Layout
-------

The character count indicator always appears in the top right above the input field. Long field labels do not displace indicators. The labels wrap to multiple lines instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-layout.edab30d4d4a87a01e935ec16149f47d6.png)

 Related information
--------------------

### Components

*   [Input box](/skyux/components/input-box.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/character-counter/character-counter.module.ts#L28) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 SkyCharacterCounterModule
--------------------------

Type: Module

`import { SkyCharacterCounterModule } from '@skyux/forms';`

 SkyCharacterCounterIndicatorComponent
--------------------------------------

Type: Component

Selector: `sky-character-counter-indicator`

 SkyCharacterCounterInputDirective
----------------------------------

Type: Directive

Selector: `[skyCharacterCounter]`

Creates an input field that validates the number of characters. Place this directive on an `input` or `textarea` element. If users enter more characters than allowed, then the input field is invalid and the component displays an error indicator.

### Inputs

#### `skyCharacterCounterLimit: number | undefined`

Required

The maximum number of characters allowed in the input field. Place this directive on an `input` or `textarea` element. This property accepts `number` values.

#### `skyCharacterCounterIndicator: SkyCharacterCounterIndicatorComponent | undefined`

The character count indicator component that displays the character count, character limit, and over-the-limit indicator. Place this directive on an `input` or `textarea` element.

 SkyCharacterCounterScreenReaderPipe
------------------------------------

Type: Pipe

Pipe name: `skyCharacterCounterScreenReader`

### Methods

#### `transform(characterCount: number | undefined, characterCountLimit: number | undefined): string`

#### Parameters

##### `characterCount: number | undefined`

##### `characterCountLimit: number | undefined`

#### Returns

`string`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyCharacterCounterIndicatorHarness
------------------------------------

Type: Class

`import { SkyCharacterCounterIndicatorHarness } from '@skyux/forms/testing';`

Harness for interacting with a character counter indicator component in tests.

### Methods

#### `getCharacterCount(): Promise<number>`

Gets the current character count.

#### Returns

`Promise<number>`

#### `getCharacterCountLimit(): Promise<number>`

Gets the character counter limit.

#### Returns

`Promise<number>`

#### `isOverLimit(): Promise<boolean>`

Indicates whether the character counter is in an error state because the current character count is greater than the limit.

#### Returns

`Promise<boolean>`

#### `SkyCharacterCounterIndicatorHarness.with(filters: SkyCharacterCounterIndicatorHarnessFilters): HarnessPredicate<SkyCharacterCounterIndicatorHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyCharacterCounterIndicatorHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyCharacterCounterIndicatorHarnessFilters`

#### Returns

`HarnessPredicate<SkyCharacterCounterIndicatorHarness>`

 SkyCharacterCounterIndicatorHarnessFilters
-------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyCharacterCounterIndicatorHarness](/skyux/components/character-count?docs-active-tab=development#class_sky-character-counter-indicator-harness.md) instances.

    interface SkyCharacterCounterIndicatorHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Examples

                     Skip to Main Content

 Character count
===============

The character count indicator extends a text input to apply a character limit and display the number of characters entered and the character limit.Usage
------

### Use when

Use character count indicators when users are likely to exceed character limits. Indicators are useful when technical requirements lead to restrictive character limits or when user entries are freeform and could be very long.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-usage-1.8e79a2112b6194f5331735bbed6d7ffb.png)

Do use character count indicators on input fields where users may realistically exceed character limits.

### Don't use when

Don't use character count indicators when character limits are apparent or implied by the data type.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-usage-2.9b9830a2dbe15378ee72d3cf4f25ae44.png)

Don't use character count indicators on input fields where user entries follow expected or standard lengths.

Don't use character count indicators on inputs when users are unlikely to exceed character limits. Use [normal form validation](/skyux/design/guidelines/form-design#validation-and-error-handling.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-usage-3.17dcdab2217ed1f6e1aee34dd9d4e3ca.png)

Don't use character count indicators on input fields where users should not realistically exceed character limits.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-usage-4.98bdaa3f7d1cb893abbfba04e6e8ec1b.png)

Do use normal form validation for edge cases where users exceed character limits.

 Anatomy
--------

1

Input field

2

[Status indicator](/skyux/components/status-indicator.md) (danger)

3

Character count indicator (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-anatomy.1153f353f3226ebf3f4d487a79e930cd.png)

 Options
--------

### Character count indicator

The character count indicator displays the number of characters that users enter, the character limit, and a danger icon if users exceed the limit. For inputs where users are unlikely to reach the character limit, you don't need to display the character count indicator.

 Behavior and states
--------------------

The character count indicator component extends the form classes that define styles and the appearance of input field states.

Empty field

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-state-1.e5bc816ce3b83ad3c040e3ea8f62b3cb.png)

Adding text

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-state-2.f99f02c213fd6ebfb2288546787c5f34.png)

At the character limit

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-state-3.8721dc7c64aff3a02ede8101f09cc9ba.png)

Over the character limit

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-state-4.b4189b6795194360a850ec5a952a70a6.png)

 Content
--------

For validation messages when users exceed character limits, use the following format:

**Limit <input field label> to <n> characters.**

 Layout
-------

The character count indicator always appears in the top right above the input field. Long field labels do not displace indicators. The labels wrap to multiple lines instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-layout.edab30d4d4a87a01e935ec16149f47d6.png)

 Related information
--------------------

### Components

*   [Input box](/skyux/components/input-box.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/character-counter/character-counter.module.ts#L28) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 SkyCharacterCounterModule
--------------------------

Type: Module

`import { SkyCharacterCounterModule } from '@skyux/forms';`

 SkyCharacterCounterIndicatorComponent
--------------------------------------

Type: Component

Selector: `sky-character-counter-indicator`

 SkyCharacterCounterInputDirective
----------------------------------

Type: Directive

Selector: `[skyCharacterCounter]`

Creates an input field that validates the number of characters. Place this directive on an `input` or `textarea` element. If users enter more characters than allowed, then the input field is invalid and the component displays an error indicator.

### Inputs

#### `skyCharacterCounterLimit: number | undefined`

Required

The maximum number of characters allowed in the input field. Place this directive on an `input` or `textarea` element. This property accepts `number` values.

#### `skyCharacterCounterIndicator: SkyCharacterCounterIndicatorComponent | undefined`

The character count indicator component that displays the character count, character limit, and over-the-limit indicator. Place this directive on an `input` or `textarea` element.

 SkyCharacterCounterScreenReaderPipe
------------------------------------

Type: Pipe

Pipe name: `skyCharacterCounterScreenReader`

### Methods

#### `transform(characterCount: number | undefined, characterCountLimit: number | undefined): string`

#### Parameters

##### `characterCount: number | undefined`

##### `characterCountLimit: number | undefined`

#### Returns

`string`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyCharacterCounterIndicatorHarness
------------------------------------

Type: Class

`import { SkyCharacterCounterIndicatorHarness } from '@skyux/forms/testing';`

Harness for interacting with a character counter indicator component in tests.

### Methods

#### `getCharacterCount(): Promise<number>`

Gets the current character count.

#### Returns

`Promise<number>`

#### `getCharacterCountLimit(): Promise<number>`

Gets the character counter limit.

#### Returns

`Promise<number>`

#### `isOverLimit(): Promise<boolean>`

Indicates whether the character counter is in an error state because the current character count is greater than the limit.

#### Returns

`Promise<boolean>`

#### `SkyCharacterCounterIndicatorHarness.with(filters: SkyCharacterCounterIndicatorHarnessFilters): HarnessPredicate<SkyCharacterCounterIndicatorHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyCharacterCounterIndicatorHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyCharacterCounterIndicatorHarnessFilters`

#### Returns

`HarnessPredicate<SkyCharacterCounterIndicatorHarness>`

 SkyCharacterCounterIndicatorHarnessFilters
-------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyCharacterCounterIndicatorHarness](/skyux/components/character-count?docs-active-tab=examples#class_sky-character-counter-indicator-harness.md) instances.

    interface SkyCharacterCounterIndicatorHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

### Character count with basic setup

Edit in StackBlitz

Transaction description 46/50 46 characters out of 50

Show code

Copy

    <form [formGroup]="formGroup">
      <sky-input-box stacked="true" labelText="Transaction description">
        <sky-character-counter-indicator
          #descriptionIndicator
          data-sky-id="description-indicator"
        />
    
        <input
          #descriptionInput="skyId"
          class="sky-form-control description-input"
          formControlName="description"
          skyCharacterCounter
          skyId
          type="text"
          [attr.aria-describedby]="characterCountError.id"
          [skyCharacterCounterIndicator]="descriptionIndicator"
          [skyCharacterCounterLimit]="maxDescriptionCharacterCount"
        />
    
        <span #characterCountError="skyId" class="sky-error-indicator" skyId>
          @if (description.errors?.['skyCharacterCounter']) {
            <sky-status-indicator
              data-sky-id="description-status-indicator-over-limit"
              descriptionType="error"
              indicatorType="danger"
            >
              Limit Transaction description to
              {{ maxDescriptionCharacterCount }} characters.
            </sky-status-indicator>
          }
        </span>
      </sky-input-box>
    </form>
Copy

    import { HarnessLoader } from '@angular/cdk/testing';
    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { TestBed } from '@angular/core/testing';
    import { SkyCharacterCounterIndicatorHarness } from '@skyux/forms/testing';
    import { SkyStatusIndicatorHarness } from '@skyux/indicators/testing';
    
    import { FormsCharacterCountExampleComponent } from './example.component';
    
    describe('Character count example', () => {
      async function setupTest(): Promise<{
        harness: SkyCharacterCounterIndicatorHarness;
        loader: HarnessLoader;
      }> {
        const fixture = TestBed.createComponent(
          FormsCharacterCountExampleComponent,
        );
    
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const harness = await loader.getHarness(
          SkyCharacterCounterIndicatorHarness.with({
            dataSkyId: 'description-indicator',
          }),
        );
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        return { harness, loader };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [FormsCharacterCountExampleComponent],
        });
      });
    
      it('should allow a maximum of 50 characters', async () => {
        const { harness, loader } = await setupTest();
    
        // Validate initial state.
        await expectAsync(harness.getCharacterCountLimit()).toBeResolvedTo(50);
        await expectAsync(harness.getCharacterCount()).toBeResolvedTo(46);
        await expectAsync(harness.isOverLimit()).toBeResolvedTo(false);
    
        // Update the value to exceed the limit and validate.
        const inputEl =
          document.querySelector<HTMLInputElement>('.description-input');
    
        if (inputEl) {
          inputEl.value += ' scholarship fund';
          inputEl.dispatchEvent(new Event('input'));
        }
    
        await expectAsync(harness.getCharacterCount()).toBeResolvedTo(63);
        await expectAsync(harness.isOverLimit()).toBeResolvedTo(true);
    
        // Validate that the status indicator error displayed when limit was exceeded.
        const statusIndicator = await loader.getHarness(
          SkyStatusIndicatorHarness.with({
            dataSkyId: 'description-status-indicator-over-limit',
          }),
        );
    
        await expectAsync(statusIndicator.getDescriptionType()).toBeResolvedTo(
          'error',
        );
        await expectAsync(statusIndicator.getIndicatorType()).toBeResolvedTo(
          'danger',
        );
        await expectAsync(statusIndicator.getText()).toBeResolvedTo(
          'Limit Transaction description to 50 characters.',
        );
      });
    });

Copy

    import { Component, inject } from '@angular/core';
    import {
      FormBuilder,
      FormControl,
      FormGroup,
      FormsModule,
      ReactiveFormsModule,
    } from '@angular/forms';
    import { SkyIdModule } from '@skyux/core';
    import { SkyCharacterCounterModule, SkyInputBoxModule } from '@skyux/forms';
    import { SkyStatusIndicatorModule } from '@skyux/indicators';
    
    /**
     * @title Character count with basic setup
     */
    @Component({
      selector: 'app-forms-character-count-example',
      templateUrl: './example.component.html',
      imports: [
        FormsModule,
        ReactiveFormsModule,
        SkyCharacterCounterModule,
        SkyIdModule,
        SkyInputBoxModule,
        SkyStatusIndicatorModule,
      ],
    })
    export class FormsCharacterCountExampleComponent {
      protected description: FormControl;
      protected formGroup: FormGroup;
      protected maxDescriptionCharacterCount = 50;
    
      readonly #formBuilder = inject(FormBuilder);
    
      constructor() {
        this.description = this.#formBuilder.control(
          'Boys and Girls Club of South Carolina donation',
        );
    
        this.formGroup = this.#formBuilder.group({
          description: this.description,
        });
      }
    }

# Testing

                   Skip to Main Content

 Character count
===============

The character count indicator extends a text input to apply a character limit and display the number of characters entered and the character limit.

 Usage
------

### Use when

Use character count indicators when users are likely to exceed character limits. Indicators are useful when technical requirements lead to restrictive character limits or when user entries are freeform and could be very long.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-usage-1.8e79a2112b6194f5331735bbed6d7ffb.png)

Do use character count indicators on input fields where users may realistically exceed character limits.

### Don't use when

Don't use character count indicators when character limits are apparent or implied by the data type.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-usage-2.9b9830a2dbe15378ee72d3cf4f25ae44.png)

Don't use character count indicators on input fields where user entries follow expected or standard lengths.

Don't use character count indicators on inputs when users are unlikely to exceed character limits. Use [normal form validation](/skyux/design/guidelines/form-design#validation-and-error-handling.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-usage-3.17dcdab2217ed1f6e1aee34dd9d4e3ca.png)

Don't use character count indicators on input fields where users should not realistically exceed character limits.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-usage-4.98bdaa3f7d1cb893abbfba04e6e8ec1b.png)

Do use normal form validation for edge cases where users exceed character limits.

 Anatomy
--------

1

Input field

2

[Status indicator](/skyux/components/status-indicator.md) (danger)

3

Character count indicator (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-anatomy.1153f353f3226ebf3f4d487a79e930cd.png)

 Options
--------

### Character count indicator

The character count indicator displays the number of characters that users enter, the character limit, and a danger icon if users exceed the limit. For inputs where users are unlikely to reach the character limit, you don't need to display the character count indicator.

 Behavior and states
--------------------

The character count indicator component extends the form classes that define styles and the appearance of input field states.

Empty field

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-state-1.e5bc816ce3b83ad3c040e3ea8f62b3cb.png)

Adding text

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-state-2.f99f02c213fd6ebfb2288546787c5f34.png)

At the character limit

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-state-3.8721dc7c64aff3a02ede8101f09cc9ba.png)

Over the character limit

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-state-4.b4189b6795194360a850ec5a952a70a6.png)

 Content
--------

For validation messages when users exceed character limits, use the following format:

**Limit <input field label> to <n> characters.**

 Layout
-------

The character count indicator always appears in the top right above the input field. Long field labels do not displace indicators. The labels wrap to multiple lines instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/character-count/character-count-layout.edab30d4d4a87a01e935ec16149f47d6.png)

 Related information
--------------------

### Components

*   [Input box](/skyux/components/input-box.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/forms`[View in NPM](https://www.npmjs.com/package/@skyux/forms) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/forms/src/lib/modules/character-counter/character-counter.module.ts#L28) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/forms`Copy None found.

 SkyCharacterCounterModule
--------------------------

Type: Module

`import { SkyCharacterCounterModule } from '@skyux/forms';`

 SkyCharacterCounterIndicatorComponent
--------------------------------------

Type: Component

Selector: `sky-character-counter-indicator`

 SkyCharacterCounterInputDirective
----------------------------------

Type: Directive

Selector: `[skyCharacterCounter]`

Creates an input field that validates the number of characters. Place this directive on an `input` or `textarea` element. If users enter more characters than allowed, then the input field is invalid and the component displays an error indicator.

### Inputs

#### `skyCharacterCounterLimit: number | undefined`

Required

The maximum number of characters allowed in the input field. Place this directive on an `input` or `textarea` element. This property accepts `number` values.

#### `skyCharacterCounterIndicator: SkyCharacterCounterIndicatorComponent | undefined`

The character count indicator component that displays the character count, character limit, and over-the-limit indicator. Place this directive on an `input` or `textarea` element.

 SkyCharacterCounterScreenReaderPipe
------------------------------------

Type: Pipe

Pipe name: `skyCharacterCounterScreenReader`

### Methods

#### `transform(characterCount: number | undefined, characterCountLimit: number | undefined): string`

#### Parameters

##### `characterCount: number | undefined`

##### `characterCountLimit: number | undefined`

#### Returns

`string`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyCharacterCounterIndicatorHarness
------------------------------------

Type: Class

`import { SkyCharacterCounterIndicatorHarness } from '@skyux/forms/testing';`

Harness for interacting with a character counter indicator component in tests.

### Methods

#### `getCharacterCount(): Promise<number>`

Gets the current character count.

#### Returns

`Promise<number>`

#### `getCharacterCountLimit(): Promise<number>`

Gets the character counter limit.

#### Returns

`Promise<number>`

#### `isOverLimit(): Promise<boolean>`

Indicates whether the character counter is in an error state because the current character count is greater than the limit.

#### Returns

`Promise<boolean>`

#### `SkyCharacterCounterIndicatorHarness.with(filters: SkyCharacterCounterIndicatorHarnessFilters): HarnessPredicate<SkyCharacterCounterIndicatorHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyCharacterCounterIndicatorHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyCharacterCounterIndicatorHarnessFilters`

#### Returns

`HarnessPredicate<SkyCharacterCounterIndicatorHarness>`

 SkyCharacterCounterIndicatorHarnessFilters
-------------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyCharacterCounterIndicatorHarness](/skyux/components/character-count?docs-active-tab=testing#class_sky-character-counter-indicator-harness.md) instances.

    interface SkyCharacterCounterIndicatorHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.