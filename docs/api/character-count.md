---
component: 'character-count'
type: 'api-documentation'
description: 'API documentation for the character-count component including components, interfaces, and types.'
---

# Character Count API Documentation

## Components and Directives

#### FormsCharacterCountExampleComponent

**Selector:** `app-forms-character-count-example`

**Package:** `@skyux/code-examples`

#### SkyCharacterCounterIndicatorComponent

**Selector:** `sky-character-counter-indicator`

**Package:** `@skyux/forms`

#### SkyCharacterCounterInputDirective

Creates an input field that validates the number of characters. Place this directive on
an `input` or `textarea` element. If users enter more characters than allowed, then the
input field is invalid and the component displays an error indicator.

**Selector:** `[skyCharacterCounter]`

**Package:** `@skyux/forms`

**Inputs:**

- `skyCharacterCounterIndicator`: `SkyCharacterCounterIndicatorComponent | undefined` - The character count indicator component that displays the character count,
character limit, and over-the-limit indicator. Place this directive on an `input` or
`textarea` element.
- `skyCharacterCounterLimit`: `number | undefined` - The maximum number of characters allowed in the input field. Place this directive
on an `input` or `textarea` element. This property accepts `number` values.