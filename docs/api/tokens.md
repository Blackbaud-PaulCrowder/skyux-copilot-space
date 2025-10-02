---
component: 'tokens'
type: 'api-documentation'
description: 'API documentation for the tokens component including components, interfaces, and types.'
---

# Tokens API Documentation

## Components and Directives

#### IndicatorsTokensBasicExampleComponent

**Selector:** `app-indicators-tokens-basic-example`

**Package:** `@skyux/code-examples`

#### IndicatorsTokensCustomExampleComponent

Tokens with programmatic interactions

**Selector:** `app-indicators-tokens-custom-example`

**Package:** `@skyux/code-examples`

#### SkyTokenComponent

**Selector:** `sky-token`

**Package:** `@skyux/indicators`

**Inputs:**

- `ariaLabel`: `string | undefined` - The ARIA label for the token's close button. This sets the button's `aria-label` to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label). (default: "Remove item")
- `role`: `string | undefined` - Used by the tokens component to set the appropriate role for each token.
- `disabled`: `boolean` - Whether to disable the token to prevent users from selecting it, dismissing it,
or navigating to it with the arrow keys. When the token is disabled,
users can still place focus on it using the `Tab` key. (default: false)
- `dismissible`: `boolean` - Whether users can remove the token from the list by selecting the close button. (default: true)
- `focusable`: `boolean | undefined` - Whether users can place focus on the token using the `Tab`. This does not
affect the ability to select the token, dismiss it, or navigate to it with the arrow keys. (default: true)

**Outputs:**

- `dismiss`: `EventEmitter<void>` - Fires when users click the close button.
- `tokenFocus`: `EventEmitter<void>` - Fires when users place focus on the token by navigating to it with the `Tab` key.

#### SkyTokensComponent

Creates a container that enables navigation between tokens using keyboard arrow keys.
This is useful when combined with other components where the <kbd>Tab</kbd> key is
reserved for other functions, such as the SKY UX Lookup component.

**Selector:** `sky-tokens`

**Package:** `@skyux/indicators`

**Inputs:**

- `trackWith`: `string | undefined` - The token property that represents the token's unique identifier. When this property
is set, animations are enabled when dismissing tokens.
- `disabled`: `boolean` - Whether to disable the tokens list to prevent users from selecting tokens,
dismissing tokens, or navigating through the list with the arrow keys. When the tokens list
is disabled, users can still place focus on items in the list using the `Tab` key. (default: false)
- `dismissible`: `boolean` - Whether users can remove a token from the list by selecting a token's close button. (default: true)
- `displayWith`: `string` - The token property to display for each item in the tokens list. (default: "name")
- `focusable`: `boolean` - Whether users can place focus on tokens in the list using the `Tab` key.
This does not affect the ability of users to select tokens, dismiss tokens,
or navigate through the list with the arrow keys. (default: true)
- `messageStream`: `Subject<SkyTokensMessage>` - The observable of `SkyTokensMessage` that can place focus on a
particular token or remove the active token from the list.
- `tokens`: `SkyToken<any>[]` - The array of tokens to include in the list.

**Outputs:**

- `focusIndexOverRange`: `EventEmitter<void>` - Fires when users navigate through the tokens list with the `Tab` key
and attempt to move past the final token in the list.
- `focusIndexUnderRange`: `EventEmitter<void>` - Fires when users navigate through the tokens list with the `Tab` key
and attempt to move before the first token in the list.
- `tokensChange`: `EventEmitter<SkyToken<any>[]>` - Fires when the tokens in the list change.
This event emits an array of the tokens in the updated list.
- `tokenSelected`: `EventEmitter<SkyTokenSelectedEventArgs<any>>` - Fires when users select a token in the list. This event emits the selected token.
- `tokensRendered`: `EventEmitter<void>` - Fires when all animations on the tokens are complete.