# Development

                 Skip to Main Content

 Tokens
======

Tokens display a series of specified objects that users can interact with. They can navigate through a list of tokens and remove tokens from the list.

 Installation
-------------

NPM package

`@skyux/indicators`[View in NPM](https://www.npmjs.com/package/@skyux/indicators) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/indicators/src/lib/modules/tokens/tokens.module.ts#L22) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/indicators`Copy None found.

 SkyTokensModule
----------------

Type: Module

`import { SkyTokensModule } from '@skyux/indicators';`

 SkyTokensComponent
-------------------

Type: Component

Selector: `sky-tokens`

Creates a container that enables navigation between tokens using keyboard arrow keys. This is useful when combined with other components where the <kbd>Tab</kbd> key is reserved for other functions, such as the SKY UX Lookup component.

### Inputs

#### `disabled: boolean`

Whether to disable the tokens list to prevent users from selecting tokens, dismissing tokens, or navigating through the list with the arrow keys. When the tokens list is disabled, users can still place focus on items in the list using the `Tab` key.

Default: `false`

#### `dismissible: boolean`

Whether users can remove a token from the list by selecting a token's close button.

Default: `true`

#### `displayWith: string`

The token property to display for each item in the tokens list.

Default: `"name"`

#### `focusable: boolean`

Whether users can place focus on tokens in the list using the `Tab` key. This does not affect the ability of users to select tokens, dismiss tokens, or navigate through the list with the arrow keys.

Default: `true`

#### `messageStream: Subject<SkyTokensMessage>`

The observable of `SkyTokensMessage` that can place focus on a particular token or remove the active token from the list.

#### `tokens: SkyToken<any>[]`

The array of tokens to include in the list.

#### `trackWith: string | undefined`

The token property that represents the token's unique identifier. When this property is set, animations are enabled when dismissing tokens.

### Outputs

#### `focusIndexOverRange: EventEmitter<void>`

Fires when users navigate through the tokens list with the `Tab` key and attempt to move past the final token in the list.

#### `focusIndexUnderRange: EventEmitter<void>`

Fires when users navigate through the tokens list with the `Tab` key and attempt to move before the first token in the list.

#### `tokensChange: EventEmitter<SkyToken<any>[]>`

Fires when the tokens in the list change. This event emits an array of the tokens in the updated list.

#### `tokenSelected: EventEmitter<SkyTokenSelectedEventArgs<any>>`

Fires when users select a token in the list. This event emits the selected token.

 SkyTokenComponent
------------------

Type: Component

Selector: `sky-token`

### Inputs

#### `ariaLabel: string | undefined`

The ARIA label for the token's close button. This sets the button's `aria-label` to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

Default: `"Remove item"`

#### `disabled: boolean`

Whether to disable the token to prevent users from selecting it, dismissing it, or navigating to it with the arrow keys. When the token is disabled, users can still place focus on it using the `Tab` key.

Default: `false`

#### `dismissible: boolean`

Whether users can remove the token from the list by selecting the close button.

Default: `true`

#### `focusable: boolean | undefined`

Whether users can place focus on the token using the `Tab`. This does not affect the ability to select the token, dismiss it, or navigate to it with the arrow keys.

Default: `true`

### Outputs

#### `dismiss: EventEmitter<void>`

Fires when users click the close button.

#### `tokenFocus: EventEmitter<void>`

Fires when users place focus on the token by navigating to it with the `Tab` key.

 SkyToken
---------

Type: Interface

    interface SkyToken {
      value: T;
    }

### Properties

#### `value: T`

The token's value. The `sky-tokens` component uses its `displayWith` property to determine which of the value's properties to use as the token's label.

 SkyTokenSelectedEventArgs
--------------------------

Type: Interface

    interface SkyTokenSelectedEventArgs {
      token?: SkyToken<T>;
    }

### Properties

#### `token?: SkyToken<T>`

The currently selected token.

 SkyTokensMessage
-----------------

Type: Interface

    interface SkyTokensMessage {
      type?: SkyTokensMessageType;
    }

### Properties

#### `type?: SkyTokensMessageType`

The type of message.

 SkyTokensMessageType
---------------------

Type: Enumeration

    enum SkyTokensMessageType {
      FocusActiveToken = 1,
      FocusLastToken = 0,
      FocusNextToken = 3,
      FocusPreviousToken = 2,
      RemoveActiveToken = 4,
    }

### Properties

#### `SkyTokensMessageType.FocusActiveToken`

Places focus on the token that is currently selected.

#### `SkyTokensMessageType.FocusLastToken`

Places focus on the last token in the list.

#### `SkyTokensMessageType.FocusNextToken`

Places focus on the token after the currently selected token.

#### `SkyTokensMessageType.FocusPreviousToken`

Places focus on the token before the currently selected token.

#### `SkyTokensMessageType.RemoveActiveToken`

Removes the token that is currently selected from the list of tokens.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyTokensHarness
-----------------

Type: Class

`import { SkyTokensHarness } from '@skyux/indicators/testing';`

Harness for interacting with a tokens component in tests.

### Methods

#### `dismissTokens(filters?: SkyTokenHarnessFilters): Promise<void>`

Dismisses all tokens, or tokens that meet certain criteria.

#### Parameters

##### `filters?: SkyTokenHarnessFilters`

#### Returns

`Promise<void>`

#### `getToken(filter: SkyTokenHarnessFilters): Promise<SkyTokenHarness>`

Gets a specific token based on the filter criteria.

#### Parameters

##### `filter: SkyTokenHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyTokenHarness>`

#### `getTokens(filters?: SkyTokenHarnessFilters): Promise<SkyTokenHarness[]>`

Gets an array of tokens based on the filter criteria. If no filter is provided, returns all tokens.

#### Parameters

##### `filters?: SkyTokenHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyTokenHarness[]>`

#### `getTokensText(): Promise<string[]>`

Returns the text content of all tokens.

#### Returns

`Promise<string[]>`

#### `SkyTokensHarness.with(filters: SkyTokensHarnessFilters): HarnessPredicate<SkyTokensHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTokensHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTokensHarnessFilters`

#### Returns

`HarnessPredicate<SkyTokensHarness>`

 SkyTokensHarnessFilters
------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTokensHarness` instances.

    interface SkyTokensHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyTokenHarness
----------------

Type: Class

`import { SkyTokenHarness } from '@skyux/indicators/testing';`

Harness for interacting with a token component in tests.

### Methods

#### `dismiss(): Promise<void>`

Dismisses the token.

#### Returns

`Promise<void>`

#### `getText(): Promise<string>`

Returns the text content of the token.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the token is disabled.

#### Returns

`Promise<boolean>`

#### `isDismissible(): Promise<boolean>`

Whether the token is dismissible.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the token is focused.

#### Returns

`Promise<boolean>`

#### `select(): Promise<void>`

Selects the token.

#### Returns

`Promise<void>`

#### `SkyTokenHarness.with(filters: SkyTokenHarnessFilters): HarnessPredicate<SkyTokenHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTokenHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTokenHarnessFilters`

#### Returns

`HarnessPredicate<SkyTokenHarness>`

 SkyTokenHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTokenHarness` instances.

    interface SkyTokenHarnessFilters {
      text?: string | RegExp;
    }

### Properties

#### `text?: string | RegExp`

Only find instances whose text content matches the given value. 

Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove

# Examples

                   Skip to Main Content

 Tokens
======

Tokens display a series of specified objects that users can interact with. They can navigate through a list of tokens and remove tokens from the list.Installation
-------------

NPM package

`@skyux/indicators`[View in NPM](https://www.npmjs.com/package/@skyux/indicators) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/indicators/src/lib/modules/tokens/tokens.module.ts#L22) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/indicators`Copy None found.

 SkyTokensModule
----------------

Type: Module

`import { SkyTokensModule } from '@skyux/indicators';`

 SkyTokensComponent
-------------------

Type: Component

Selector: `sky-tokens`

Creates a container that enables navigation between tokens using keyboard arrow keys. This is useful when combined with other components where the <kbd>Tab</kbd> key is reserved for other functions, such as the SKY UX Lookup component.

### Inputs

#### `disabled: boolean`

Whether to disable the tokens list to prevent users from selecting tokens, dismissing tokens, or navigating through the list with the arrow keys. When the tokens list is disabled, users can still place focus on items in the list using the `Tab` key.

Default: `false`

#### `dismissible: boolean`

Whether users can remove a token from the list by selecting a token's close button.

Default: `true`

#### `displayWith: string`

The token property to display for each item in the tokens list.

Default: `"name"`

#### `focusable: boolean`

Whether users can place focus on tokens in the list using the `Tab` key. This does not affect the ability of users to select tokens, dismiss tokens, or navigate through the list with the arrow keys.

Default: `true`

#### `messageStream: Subject<SkyTokensMessage>`

The observable of `SkyTokensMessage` that can place focus on a particular token or remove the active token from the list.

#### `tokens: SkyToken<any>[]`

The array of tokens to include in the list.

#### `trackWith: string | undefined`

The token property that represents the token's unique identifier. When this property is set, animations are enabled when dismissing tokens.

### Outputs

#### `focusIndexOverRange: EventEmitter<void>`

Fires when users navigate through the tokens list with the `Tab` key and attempt to move past the final token in the list.

#### `focusIndexUnderRange: EventEmitter<void>`

Fires when users navigate through the tokens list with the `Tab` key and attempt to move before the first token in the list.

#### `tokensChange: EventEmitter<SkyToken<any>[]>`

Fires when the tokens in the list change. This event emits an array of the tokens in the updated list.

#### `tokenSelected: EventEmitter<SkyTokenSelectedEventArgs<any>>`

Fires when users select a token in the list. This event emits the selected token.

 SkyTokenComponent
------------------

Type: Component

Selector: `sky-token`

### Inputs

#### `ariaLabel: string | undefined`

The ARIA label for the token's close button. This sets the button's `aria-label` to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

Default: `"Remove item"`

#### `disabled: boolean`

Whether to disable the token to prevent users from selecting it, dismissing it, or navigating to it with the arrow keys. When the token is disabled, users can still place focus on it using the `Tab` key.

Default: `false`

#### `dismissible: boolean`

Whether users can remove the token from the list by selecting the close button.

Default: `true`

#### `focusable: boolean | undefined`

Whether users can place focus on the token using the `Tab`. This does not affect the ability to select the token, dismiss it, or navigate to it with the arrow keys.

Default: `true`

### Outputs

#### `dismiss: EventEmitter<void>`

Fires when users click the close button.

#### `tokenFocus: EventEmitter<void>`

Fires when users place focus on the token by navigating to it with the `Tab` key.

 SkyToken
---------

Type: Interface

    interface SkyToken {
      value: T;
    }

### Properties

#### `value: T`

The token's value. The `sky-tokens` component uses its `displayWith` property to determine which of the value's properties to use as the token's label.

 SkyTokenSelectedEventArgs
--------------------------

Type: Interface

    interface SkyTokenSelectedEventArgs {
      token?: SkyToken<T>;
    }

### Properties

#### `token?: SkyToken<T>`

The currently selected token.

 SkyTokensMessage
-----------------

Type: Interface

    interface SkyTokensMessage {
      type?: SkyTokensMessageType;
    }

### Properties

#### `type?: SkyTokensMessageType`

The type of message.

 SkyTokensMessageType
---------------------

Type: Enumeration

    enum SkyTokensMessageType {
      FocusActiveToken = 1,
      FocusLastToken = 0,
      FocusNextToken = 3,
      FocusPreviousToken = 2,
      RemoveActiveToken = 4,
    }

### Properties

#### `SkyTokensMessageType.FocusActiveToken`

Places focus on the token that is currently selected.

#### `SkyTokensMessageType.FocusLastToken`

Places focus on the last token in the list.

#### `SkyTokensMessageType.FocusNextToken`

Places focus on the token after the currently selected token.

#### `SkyTokensMessageType.FocusPreviousToken`

Places focus on the token before the currently selected token.

#### `SkyTokensMessageType.RemoveActiveToken`

Removes the token that is currently selected from the list of tokens.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyTokensHarness
-----------------

Type: Class

`import { SkyTokensHarness } from '@skyux/indicators/testing';`

Harness for interacting with a tokens component in tests.

### Methods

#### `dismissTokens(filters?: SkyTokenHarnessFilters): Promise<void>`

Dismisses all tokens, or tokens that meet certain criteria.

#### Parameters

##### `filters?: SkyTokenHarnessFilters`

#### Returns

`Promise<void>`

#### `getToken(filter: SkyTokenHarnessFilters): Promise<SkyTokenHarness>`

Gets a specific token based on the filter criteria.

#### Parameters

##### `filter: SkyTokenHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyTokenHarness>`

#### `getTokens(filters?: SkyTokenHarnessFilters): Promise<SkyTokenHarness[]>`

Gets an array of tokens based on the filter criteria. If no filter is provided, returns all tokens.

#### Parameters

##### `filters?: SkyTokenHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyTokenHarness[]>`

#### `getTokensText(): Promise<string[]>`

Returns the text content of all tokens.

#### Returns

`Promise<string[]>`

#### `SkyTokensHarness.with(filters: SkyTokensHarnessFilters): HarnessPredicate<SkyTokensHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTokensHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTokensHarnessFilters`

#### Returns

`HarnessPredicate<SkyTokensHarness>`

 SkyTokensHarnessFilters
------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTokensHarness` instances.

    interface SkyTokensHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyTokenHarness
----------------

Type: Class

`import { SkyTokenHarness } from '@skyux/indicators/testing';`

Harness for interacting with a token component in tests.

### Methods

#### `dismiss(): Promise<void>`

Dismisses the token.

#### Returns

`Promise<void>`

#### `getText(): Promise<string>`

Returns the text content of the token.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the token is disabled.

#### Returns

`Promise<boolean>`

#### `isDismissible(): Promise<boolean>`

Whether the token is dismissible.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the token is focused.

#### Returns

`Promise<boolean>`

#### `select(): Promise<void>`

Selects the token.

#### Returns

`Promise<void>`

#### `SkyTokenHarness.with(filters: SkyTokenHarnessFilters): HarnessPredicate<SkyTokenHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTokenHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTokenHarnessFilters`

#### Returns

`HarnessPredicate<SkyTokenHarness>`

 SkyTokenHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTokenHarness` instances.

    interface SkyTokenHarnessFilters {
      text?: string | RegExp;
    }

### Properties

#### `text?: string | RegExp`

Only find instances whose text content matches the given value.

### Tokens with basic setup

Edit in StackBlitz

Red

Black

Blue

Brown

Green

Orange

Pink

Purple

Turquoise

White

Yellow

Show code

Copy

    <sky-tokens data-sky-id="color-tokens" [(tokens)]="colors" />
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyToken } from '@skyux/indicators';
    import { SkyTokensHarness } from '@skyux/indicators/testing';
    
    import { IndicatorsTokensBasicExampleComponent } from './example.component';
    
    describe('Tokens basic example', () => {
      async function setupTest(): Promise<{
        tokensHarness: SkyTokensHarness;
        fixture: ComponentFixture<IndicatorsTokensBasicExampleComponent>;
      }> {
        const fixture = TestBed.createComponent(
          IndicatorsTokensBasicExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const tokensHarness = await loader.getHarness(
          SkyTokensHarness.with({ dataSkyId: 'color-tokens' }),
        );
    
        return { tokensHarness, fixture };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [NoopAnimationsModule, IndicatorsTokensBasicExampleComponent],
        });
      });
    
      it('should display the expected initial tokens', async () => {
        const { tokensHarness } = await setupTest();
    
        await expectAsync(tokensHarness.getTokensText()).toBeResolvedTo([
          'Red',
          'Black',
          'Blue',
          'Brown',
          'Green',
          'Orange',
          'Pink',
          'Purple',
          'Turquoise',
          'White',
          'Yellow',
        ]);
      });
    
      it('should update the tokens array when one is dismissed', async () => {
        const { tokensHarness, fixture } = await setupTest();
    
        const blueToken: SkyToken<{ name: string }> = {
          value: { name: 'Blue' },
        };
    
        expect(fixture.componentInstance.colors).toContain(blueToken);
    
        await tokensHarness.dismissTokens({
          text: 'Blue',
        });
    
        expect(fixture.componentInstance.colors).not.toContain(blueToken);
      });
    });

Copy

    import { Component } from '@angular/core';
    import { SkyToken, SkyTokensModule } from '@skyux/indicators';
    
    /**
     * @title Tokens with basic setup
     */
    @Component({
      selector: 'app-indicators-tokens-basic-example',
      templateUrl: './example.component.html',
      imports: [SkyTokensModule],
    })
    export class IndicatorsTokensBasicExampleComponent {
      public colors: SkyToken<{
        name: string;
      }>[] = [
        { value: { name: 'Red' } },
        { value: { name: 'Black' } },
        { value: { name: 'Blue' } },
        { value: { name: 'Brown' } },
        { value: { name: 'Green' } },
        { value: { name: 'Orange' } },
        { value: { name: 'Pink' } },
        { value: { name: 'Purple' } },
        { value: { name: 'Turquoise' } },
        { value: { name: 'White' } },
        { value: { name: 'Yellow' } },
      ];
    }
### Example

Edit in StackBlitz

These tokens define a custom property to display their values. When users select a token, it emits an event.

Canada

Older than 55

Employed

Added before 2018

(You may also include content inside the tokens component.)

Change tokens Reset tokens Destroy tokens Focus last token

Selected token:

Show code

Copy

    <p>
      These tokens define a custom property to display their values. When users
      select a token, it emits an event.
    </p>
    
    <div class="sky-margin-stacked-xl">
      <sky-tokens
        data-sky-id="example-tokens"
        displayWith="label"
        [messageStream]="tokensController"
        [(tokens)]="myTokens"
        (focusIndexOverRange)="onFocusIndexOverRange()"
        (focusIndexUnderRange)="onFocusIndexUnderRange()"
        (tokenSelected)="onTokenSelected($event)"
      >
        (You may also include content inside the tokens component.)
      </sky-tokens>
    </div>
    
    <div class="sky-margin-stacked-xl">
      <button
        class="sky-btn sky-btn-default sky-margin-inline-sm tokens-example-change-btn"
        type="button"
        (click)="changeTokens()"
      >
        Change tokens
      </button>
    
      <button
        class="sky-btn sky-btn-default sky-margin-inline-sm tokens-example-reset-btn"
        type="button"
        (click)="resetTokens()"
      >
        Reset tokens
      </button>
    
      <button
        class="sky-btn sky-btn-default sky-margin-inline-sm tokens-example-destroy-btn"
        type="button"
        (click)="destroyTokens()"
      >
        Destroy tokens
      </button>
    
      <button
        class="sky-btn sky-btn-default sky-margin-inline-sm tokens-example-focus-last-btn"
        type="button"
        (click)="focusLastToken()"
      >
        Focus last token
      </button>
    </div>
    
    <div>
      Selected token:
      <span class="tokens-example-selected">{{ selectedToken }}</span>
    </div>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyTokensHarness } from '@skyux/indicators/testing';
    
    import { IndicatorsTokensCustomExampleComponent } from './example.component';
    
    describe('Tokens basic example', () => {
      let initialTokenLabels: string[];
    
      async function setupTest(): Promise<{
        tokensHarness: SkyTokensHarness;
        fixture: ComponentFixture<IndicatorsTokensCustomExampleComponent>;
      }> {
        const fixture = TestBed.createComponent(
          IndicatorsTokensCustomExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const tokensHarness = await loader.getHarness(
          SkyTokensHarness.with({ dataSkyId: 'example-tokens' }),
        );
    
        return { tokensHarness, fixture };
      }
    
      function clickButton(
        fixture: ComponentFixture<IndicatorsTokensCustomExampleComponent>,
        buttonName: 'change' | 'destroy' | 'focus-last' | 'reset',
      ): void {
        const btn = (
          fixture.nativeElement as HTMLElement
        ).querySelector<HTMLButtonElement>(`.tokens-example-${buttonName}-btn`);
    
        btn?.click();
      }
    
      beforeEach(() => {
        initialTokenLabels = [
          'Canada',
          'Older than 55',
          'Employed',
          'Added before 2018',
        ];
    
        TestBed.configureTestingModule({
          imports: [NoopAnimationsModule, IndicatorsTokensCustomExampleComponent],
        });
      });
    
      it('should display the expected initial tokens', async () => {
        const { tokensHarness } = await setupTest();
    
        await expectAsync(tokensHarness.getTokensText()).toBeResolvedTo(
          initialTokenLabels,
        );
      });
    
      it('should display the selected token label when the user selects a token', async () => {
        const { tokensHarness, fixture } = await setupTest();
    
        const employedToken = (await tokensHarness.getTokens())[2];
        await employedToken.select();
    
        expect(
          (fixture.nativeElement as HTMLElement).querySelector(
            '.tokens-example-selected',
          )?.textContent,
        ).toEqual('Employed');
      });
    
      it('should change tokens when the user clicks the "Change tokens" button', async () => {
        const { tokensHarness, fixture } = await setupTest();
    
        clickButton(fixture, 'change');
    
        await expectAsync(tokensHarness.getTokensText()).toBeResolvedTo([
          'Paid',
          'Pending',
          'Past due',
        ]);
      });
    
      it('should reset tokens when the user clicks the "Reset tokens" button', async () => {
        const { tokensHarness, fixture } = await setupTest();
    
        clickButton(fixture, 'change');
    
        await expectAsync(tokensHarness.getTokensText()).not.toBeResolvedTo(
          initialTokenLabels,
        );
    
        clickButton(fixture, 'reset');
    
        await expectAsync(tokensHarness.getTokensText()).toBeResolvedTo(
          initialTokenLabels,
        );
      });
    
      it('should destroy tokens when the user clicks the "Destroy tokens" button', async () => {
        const { tokensHarness, fixture } = await setupTest();
    
        clickButton(fixture, 'destroy');
    
        await expectAsync(tokensHarness.getTokens()).toBeResolvedTo([]);
      });
    
      it('should focus the last token when the user clicks the "Focus last token" button', async () => {
        const { tokensHarness, fixture } = await setupTest();
    
        const tokens = await tokensHarness.getTokens();
        const lastToken = tokens[tokens.length - 1];
    
        await expectAsync(lastToken.isFocused()).toBeResolvedTo(false);
    
        clickButton(fixture, 'focus-last');
    
        await expectAsync(lastToken.isFocused()).toBeResolvedTo(true);
      });
    });

Copy

    import { Component, OnDestroy } from '@angular/core';
    import {
      SkyToken,
      SkyTokenSelectedEventArgs,
      SkyTokensMessage,
      SkyTokensMessageType,
      SkyTokensModule,
    } from '@skyux/indicators';
    
    import { Subject } from 'rxjs';
    
    interface TokenItem {
      label: string;
    }
    
    /**
     * Tokens with programmatic interactions
     */
    @Component({
      selector: 'app-indicators-tokens-custom-example',
      templateUrl: './example.component.html',
      imports: [SkyTokensModule],
    })
    export class IndicatorsTokensCustomExampleComponent implements OnDestroy {
      protected myTokens: SkyToken<TokenItem>[] | undefined;
      protected tokensController = new Subject<SkyTokensMessage>();
      protected selectedToken: string | undefined = '';
    
      #defaultItems: TokenItem[] = [
        { label: 'Canada' },
        { label: 'Older than 55' },
        { label: 'Employed' },
        { label: 'Added before 2018' },
      ];
    
      constructor() {
        this.myTokens = this.#getTokens(this.#defaultItems);
      }
    
      public ngOnDestroy(): void {
        this.tokensController.complete();
      }
    
      protected resetTokens(): void {
        this.createTokens();
      }
    
      protected changeTokens(): void {
        this.myTokens = this.#getTokens([
          { label: 'Paid' },
          { label: 'Pending' },
          { label: 'Past due' },
        ]);
      }
    
      protected destroyTokens(): void {
        this.myTokens = undefined;
      }
    
      protected createTokens(): void {
        this.myTokens = this.#getTokens(this.#defaultItems);
      }
    
      protected onTokenSelected(args: SkyTokenSelectedEventArgs<TokenItem>): void {
        this.selectedToken = args.token?.value.label;
      }
    
      protected onFocusIndexUnderRange(): void {
        console.log('Focus index was less than zero.');
      }
    
      protected onFocusIndexOverRange(): void {
        console.log('Focus index was greater than the number of tokens.');
      }
    
      protected focusLastToken(): void {
        this.tokensController.next({
          type: SkyTokensMessageType.FocusLastToken,
        });
      }
    
      #getTokens(data: TokenItem[]): SkyToken<TokenItem>[] {
        return data.map((item) => {
          return {
            value: item,
          };
        });
      }
    }
 

Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove

# Testing

                 Skip to Main Content

 Tokens
======

Tokens display a series of specified objects that users can interact with. They can navigate through a list of tokens and remove tokens from the list.

 Installation
-------------

NPM package

`@skyux/indicators`[View in NPM](https://www.npmjs.com/package/@skyux/indicators) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/indicators/src/lib/modules/tokens/tokens.module.ts#L22) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/indicators`Copy None found.

 SkyTokensModule
----------------

Type: Module

`import { SkyTokensModule } from '@skyux/indicators';`

 SkyTokensComponent
-------------------

Type: Component

Selector: `sky-tokens`

Creates a container that enables navigation between tokens using keyboard arrow keys. This is useful when combined with other components where the <kbd>Tab</kbd> key is reserved for other functions, such as the SKY UX Lookup component.

### Inputs

#### `disabled: boolean`

Whether to disable the tokens list to prevent users from selecting tokens, dismissing tokens, or navigating through the list with the arrow keys. When the tokens list is disabled, users can still place focus on items in the list using the `Tab` key.

Default: `false`

#### `dismissible: boolean`

Whether users can remove a token from the list by selecting a token's close button.

Default: `true`

#### `displayWith: string`

The token property to display for each item in the tokens list.

Default: `"name"`

#### `focusable: boolean`

Whether users can place focus on tokens in the list using the `Tab` key. This does not affect the ability of users to select tokens, dismiss tokens, or navigate through the list with the arrow keys.

Default: `true`

#### `messageStream: Subject<SkyTokensMessage>`

The observable of `SkyTokensMessage` that can place focus on a particular token or remove the active token from the list.

#### `tokens: SkyToken<any>[]`

The array of tokens to include in the list.

#### `trackWith: string | undefined`

The token property that represents the token's unique identifier. When this property is set, animations are enabled when dismissing tokens.

### Outputs

#### `focusIndexOverRange: EventEmitter<void>`

Fires when users navigate through the tokens list with the `Tab` key and attempt to move past the final token in the list.

#### `focusIndexUnderRange: EventEmitter<void>`

Fires when users navigate through the tokens list with the `Tab` key and attempt to move before the first token in the list.

#### `tokensChange: EventEmitter<SkyToken<any>[]>`

Fires when the tokens in the list change. This event emits an array of the tokens in the updated list.

#### `tokenSelected: EventEmitter<SkyTokenSelectedEventArgs<any>>`

Fires when users select a token in the list. This event emits the selected token.

 SkyTokenComponent
------------------

Type: Component

Selector: `sky-token`

### Inputs

#### `ariaLabel: string | undefined`

The ARIA label for the token's close button. This sets the button's `aria-label` to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

Default: `"Remove item"`

#### `disabled: boolean`

Whether to disable the token to prevent users from selecting it, dismissing it, or navigating to it with the arrow keys. When the token is disabled, users can still place focus on it using the `Tab` key.

Default: `false`

#### `dismissible: boolean`

Whether users can remove the token from the list by selecting the close button.

Default: `true`

#### `focusable: boolean | undefined`

Whether users can place focus on the token using the `Tab`. This does not affect the ability to select the token, dismiss it, or navigate to it with the arrow keys.

Default: `true`

### Outputs

#### `dismiss: EventEmitter<void>`

Fires when users click the close button.

#### `tokenFocus: EventEmitter<void>`

Fires when users place focus on the token by navigating to it with the `Tab` key.

 SkyToken
---------

Type: Interface

    interface SkyToken {
      value: T;
    }

### Properties

#### `value: T`

The token's value. The `sky-tokens` component uses its `displayWith` property to determine which of the value's properties to use as the token's label.

 SkyTokenSelectedEventArgs
--------------------------

Type: Interface

    interface SkyTokenSelectedEventArgs {
      token?: SkyToken<T>;
    }

### Properties

#### `token?: SkyToken<T>`

The currently selected token.

 SkyTokensMessage
-----------------

Type: Interface

    interface SkyTokensMessage {
      type?: SkyTokensMessageType;
    }

### Properties

#### `type?: SkyTokensMessageType`

The type of message.

 SkyTokensMessageType
---------------------

Type: Enumeration

    enum SkyTokensMessageType {
      FocusActiveToken = 1,
      FocusLastToken = 0,
      FocusNextToken = 3,
      FocusPreviousToken = 2,
      RemoveActiveToken = 4,
    }

### Properties

#### `SkyTokensMessageType.FocusActiveToken`

Places focus on the token that is currently selected.

#### `SkyTokensMessageType.FocusLastToken`

Places focus on the last token in the list.

#### `SkyTokensMessageType.FocusNextToken`

Places focus on the token after the currently selected token.

#### `SkyTokensMessageType.FocusPreviousToken`

Places focus on the token before the currently selected token.

#### `SkyTokensMessageType.RemoveActiveToken`

Removes the token that is currently selected from the list of tokens.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyTokensHarness
-----------------

Type: Class

`import { SkyTokensHarness } from '@skyux/indicators/testing';`

Harness for interacting with a tokens component in tests.

### Methods

#### `dismissTokens(filters?: SkyTokenHarnessFilters): Promise<void>`

Dismisses all tokens, or tokens that meet certain criteria.

#### Parameters

##### `filters?: SkyTokenHarnessFilters`

#### Returns

`Promise<void>`

#### `getToken(filter: SkyTokenHarnessFilters): Promise<SkyTokenHarness>`

Gets a specific token based on the filter criteria.

#### Parameters

##### `filter: SkyTokenHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyTokenHarness>`

#### `getTokens(filters?: SkyTokenHarnessFilters): Promise<SkyTokenHarness[]>`

Gets an array of tokens based on the filter criteria. If no filter is provided, returns all tokens.

#### Parameters

##### `filters?: SkyTokenHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyTokenHarness[]>`

#### `getTokensText(): Promise<string[]>`

Returns the text content of all tokens.

#### Returns

`Promise<string[]>`

#### `SkyTokensHarness.with(filters: SkyTokensHarnessFilters): HarnessPredicate<SkyTokensHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTokensHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTokensHarnessFilters`

#### Returns

`HarnessPredicate<SkyTokensHarness>`

 SkyTokensHarnessFilters
------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTokensHarness` instances.

    interface SkyTokensHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyTokenHarness
----------------

Type: Class

`import { SkyTokenHarness } from '@skyux/indicators/testing';`

Harness for interacting with a token component in tests.

### Methods

#### `dismiss(): Promise<void>`

Dismisses the token.

#### Returns

`Promise<void>`

#### `getText(): Promise<string>`

Returns the text content of the token.

#### Returns

`Promise<string>`

#### `isDisabled(): Promise<boolean>`

Whether the token is disabled.

#### Returns

`Promise<boolean>`

#### `isDismissible(): Promise<boolean>`

Whether the token is dismissible.

#### Returns

`Promise<boolean>`

#### `isFocused(): Promise<boolean>`

Whether the token is focused.

#### Returns

`Promise<boolean>`

#### `select(): Promise<void>`

Selects the token.

#### Returns

`Promise<void>`

#### `SkyTokenHarness.with(filters: SkyTokenHarnessFilters): HarnessPredicate<SkyTokenHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTokenHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTokenHarnessFilters`

#### Returns

`HarnessPredicate<SkyTokenHarness>`

 SkyTokenHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTokenHarness` instances.

    interface SkyTokenHarnessFilters {
      text?: string | RegExp;
    }

### Properties

#### `text?: string | RegExp`

Only find instances whose text content matches the given value. 

Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove Remove