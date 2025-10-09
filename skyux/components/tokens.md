                 

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