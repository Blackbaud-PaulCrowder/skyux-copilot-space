---
component: 'summary-action-bar'
type: 'api-documentation'
description: 'API documentation for the summary-action-bar component including components, interfaces, and types.'
---

# Summary Action Bar API Documentation

## Components and Directives

#### ActionBarsSummaryActionBarBasicExampleComponent

**Selector:** `app-action-bars-summary-action-bar-basic-example`

**Package:** `@skyux/code-examples`

#### ActionBarsSummaryActionBarErrorExampleComponent

**Selector:** `app-action-bars-summary-action-bar-error-example`

**Package:** `@skyux/code-examples`

#### ActionBarsSummaryActionBarModalExampleComponent

**Selector:** `app-action-bars-summary-action-bar-modal-example`

**Package:** `@skyux/code-examples`

#### ActionBarsSummaryActionBarTabExampleComponent

**Selector:** `app-action-bars-summary-action-bar-tab-example`

**Package:** `@skyux/code-examples`

#### SkySummaryActionBarActionsComponent

Contains actions for the `sky-summary-action-bar` component.

**Selector:** `sky-summary-action-bar-actions`

**Package:** `@skyux/action-bars`

#### SkySummaryActionBarCancelComponent

Displays a cancel action.

**Selector:** `sky-summary-action-bar-cancel`

**Package:** `@skyux/action-bars`

**Inputs:**

- `disabled`: `boolean` - Whether to disable the cancel action. (default: false)

**Outputs:**

- `actionClick`: `EventEmitter<void>` - Fires when users select the cancel action.

#### SkySummaryActionBarPrimaryActionComponent

Displays a primary button.

**Selector:** `sky-summary-action-bar-primary-action`

**Package:** `@skyux/action-bars`

**Inputs:**

- `disabled`: `boolean` - Whether to disable the primary action. (default: false)

**Outputs:**

- `actionClick`: `EventEmitter<void>` - Fires when users select the primary action.

#### SkySummaryActionBarSecondaryActionComponent

Specifies secondary actions.

**Selector:** `sky-summary-action-bar-secondary-action`

**Package:** `@skyux/action-bars`

**Inputs:**

- `disabled`: `boolean` - Whether to disable a secondary action. (default: false)

**Outputs:**

- `actionClick`: `EventEmitter<void>` - Fires when users select a secondary action.

#### SkySummaryActionBarSecondaryActionsComponent

Contains secondary actions specified with `sky-summary-action-bar-secondary-action`
components.

**Selector:** `sky-summary-action-bar-secondary-actions`

**Package:** `@skyux/action-bars`

#### SkySummaryActionBarComponent

Contains the `sky-summary-action-bar-actions` and
`sky-summary-action-bar-summary` components.

**Selector:** `sky-summary-action-bar`

**Package:** `@skyux/action-bars`

**Inputs:**

- `formErrors`: `SkySummaryActionBarError[] | undefined`

#### SkySummaryActionBarSummaryComponent

Specifies the summary information to display.

**Selector:** `sky-summary-action-bar-summary`

**Package:** `@skyux/action-bars`