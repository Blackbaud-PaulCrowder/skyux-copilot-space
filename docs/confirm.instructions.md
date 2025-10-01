---
component: 'confirm'
description: 'Design guidelines, API documentation, and usage instructions for the confirm component extracted from SKY UX documentation.'
---

# Confirm Component Guidelines

## Component Overview
The confirm service launches simple confirmation dialogs that prompt users to confirm actions.

## Usage

### ✅ Use when

Use confirmation dialogs to focus user attention when actions are destructive or could be costly if performed by mistake. Prompt users to confirm an action with a single question and provide terminal actions to answer the question.

Use confirmation dialogs with a lone terminal action when users need to acknowledge important information but don't need to make a decision, such as when they need to know why they can't perform an action.

### ❌ Don't use when

Don't use confirmation dialogs when user responses require input fields.

Don't use confirmation dialogs when the context requires significant explanation, illustration, or dynamic feedback from downstream consequences.

## Anatomy

- Modal
- Heading
- Actions
- Body text

## Options

### Actions

Include up to three terminal actions to answer the question in the heading. And for confirmation dialogs that present important information without requiring a decision, include a lone action that acknowledges the information.

- A primary button triggers the recommended or most-common action.
- A secondary button triggers a less-common action.
- A link button cancels the action.
- Each button closes the dialog.

#### Primary actions that delete existing data

When a confirmation dialog's primary action deletes existing data, such as records or settings, use the sky-btn-danger style for a red background. Don't use this style for any other buttons, including actions that delete unsaved data and secondary actions that delete existing data.

### Body text

Use body text to provide context and describe potential consequences.

## Content

### Heading

Limit the confirmation dialog's heading to a single sentence. In most cases, the heading poses a question that users answer when they select an action.

- Be concise and direct. Don't use confirmation dialogs when the context requires significant explanation, illustration, or dynamic feedback from downstream consequences.
- Avoid verbose or complicated phrasing. For example, only start questions with "Are you sure you want to" when the results of an action might be unexpected and it's important for users to think twice before they proceed. When a confirmation dialog appears after users select a delete button, a question such as "Delete this account?" is sufficient because the action is usually intentional. However, when deleting data is likely an unintended consequence of another action, such as closing a modal with unsaved data, the extra verbiage of "Are you sure you want to delete this account?" can prompt users to think twice before they confirm.

### Body text

If a confirmation message requires additional context or an explanation of potential consequences, include body text. Body text can be more than one sentence. It can help users answer the question in the heading and explain what will happen if they proceed.

### Actions

Use labels that clearly indicate what happens when users select buttons. For example, if a confirmation dialog asks users to confirm that they want to delete something, use "Delete" for the primary button.

## Related information

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### SkyListViewGridRowDeleteConfirmArgs

**Package:** `@skyux/list-builder-view-grids`

⚠️ **This component is deprecated.**

#### ModalsConfirmBasicWithControllerExampleComponent

**Selector:** `app-modals-confirm-basic-with-controller-example`

**Package:** `@skyux/code-examples`

#### ModalsConfirmBasicWithHarnessExampleComponent

**Selector:** `app-modals-confirm-basic-with-harness-example`

**Package:** `@skyux/code-examples`

#### SkyAgGridRowDeleteConfirmArgs

Information regarding a row whose deletion has been confirmed.

**Package:** `@skyux/ag-grid`

#### SkyConfirmButtonAction

**Package:** `@skyux/modals`

#### SkyConfirmButtonConfig

**Package:** `@skyux/modals`

#### SkyConfirmButtonStyleType

**Package:** `@skyux/modals`

#### SkyConfirmCloseEventArgs

**Package:** `@skyux/modals`

#### SkyConfirmConfig

**Package:** `@skyux/modals`

#### SkyConfirmInstance

**Package:** `@skyux/modals`

#### SkyConfirmServiceInterface

**Package:** `@skyux/modals`

#### SkyConfirmType

**Package:** `@skyux/modals`

#### SkyConfirmComponent

**Selector:** `sky-confirm`

**Package:** `@skyux/modals`

#### SkyConfirmModule

**Package:** `@skyux/modals`

⚠️ **This component is deprecated.**

#### SkyConfirmService

Launches a dialog.

**Package:** `@skyux/modals`

#### SkyConfirmButtonHarnessFilters

A set of criteria that can be used to filter a list of SkyConfirmButtonHarness instances.

**Package:** `@skyux/modals/testing`

#### SkyConfirmButtonHarness

Harness for interacting with a confirm component in tests.

**Package:** `@skyux/modals/testing`

#### SkyConfirmHarness

Harness for interacting with a confirm component in tests.

**Package:** `@skyux/modals/testing`

#### SkyConfirmTestingController

A controller to be injected into tests, which mocks the confirm service
and handles interactions with confirm dialogs.

**Package:** `@skyux/modals/testing`

#### SkyConfirmTestingModule

Configures the `SkyConfirmTestingController` as the backend for the `SkyConfirmService`.

**Package:** `@skyux/modals/testing`

#### SkyGridRowDeleteConfirmArgs

**Package:** `@skyux/grids`

⚠️ **This component is deprecated.**

### Code Examples

#### Confirm, tested with controller

**Selector:** `app-modals-confirm-basic-with-controller-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import { SkyConfirmService } from '@skyux/modals';

/**
 * @title Confirm, tested with controller
 */
@Component({
  selector: 'app-modals-confirm-basic-with-controller-example',
  standalone: true,
  template: `<button
    aria-haspopup="dialog"
    class="sky-btn sky-btn-default"
    type="button"
    (click)="launchConfirm()"
  >
    Open confirm
  </button>`,
})
export class ModalsConfirmBasicWithControllerExampleComponent {
  public selectedAction: string | undefined;

  readonly #confirmSvc = inject(SkyConfirmService);

  public launchConfirm(): void {
    const dialog = this.#confirmSvc.open({
      message: 'Are you sure?',
    });

    dialog.closed.subscribe((args) => {
      this.selectedAction = args.action;
    });
  }
}

```

#### Confirm, tested with harness

**Selector:** `app-modals-confirm-basic-with-harness-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  SkyConfirmButtonConfig,
  SkyConfirmInstance,
  SkyConfirmService,
  SkyConfirmType,
} from '@skyux/modals';

/**
 * @title Confirm, tested with harness
 */
@Component({
  selector: 'app-modals-confirm-basic-with-harness-example',
  standalone: true,
  templateUrl: './example.component.html',
})
export class ModalsConfirmBasicWithHarnessExampleComponent {
  protected selectedAction: string | undefined;
  protected selectedText: string | undefined;

  readonly #confirmSvc = inject(SkyConfirmService);

  protected openOKConfirm(): void {
    const dialog: SkyConfirmInstance = this.#confirmSvc.open({
      message:
        'Cannot delete invoice because it has vendor, credit memo, or purchase order activity.',
    });

    dialog.closed.subscribe((result) => {
      this.selectedText = undefined;
      this.selectedAction = result.action;
    });
  }

  protected openTwoActionConfirm(): void {
    const buttons: SkyConfirmButtonConfig[] = [
      { text: 'Finalize', action: 'save', styleType: 'primary' },
      { text: 'Cancel', action: 'cancel', styleType: 'link' },
    ];

    const dialog: SkyConfirmInstance = this.#confirmSvc.open({
      message: 'Finalize report cards?',
      body: 'Grades cannot be changed once the report cards are finalized.',
      type: SkyConfirmType.Custom,
      buttons,
    });

    dialog.closed.subscribe((result) => {
      this.selectedAction = result.action;

      for (const button of buttons) {
        if (button.action === result.action) {
          this.selectedText = button.text;
          break;
        }
      }
    });
  }

  protected openThreeActionConfirm(): void {
    const buttons: SkyConfirmButtonConfig[] = [
      { text: 'Save', action: 'save', styleType: 'primary' },
      { text: 'Delete', action: 'delete' },
      { text: 'Keep working', action: 'cancel', styleType: 'link' },
    ];

    const dialog = this.#confirmSvc.open({
      message: 'Save your changes before leaving?',
      type: SkyConfirmType.Custom,
      buttons,
    });

    dialog.closed.subscribe((result) => {
      this.selectedAction = result.action;

      for (const button of buttons) {
        if (button.action === result.action) {
          this.selectedText = button.text;
          break;
        }
      }
    });
  }

  protected openDeleteConfirm(): void {
    const buttons: SkyConfirmButtonConfig[] = [
      { text: 'Delete', action: 'delete', styleType: 'danger' },
      { text: 'Cancel', action: 'cancel', styleType: 'link' },
    ];

    const dialog = this.#confirmSvc.open({
      message: 'Delete this account?',
      body: 'Deleting this account may affect processes that are currently running.',
      type: SkyConfirmType.Custom,
      buttons,
    });

    dialog.closed.subscribe((result) => {
      this.selectedAction = result.action;

      for (const button of buttons) {
        if (button.action === result.action) {
          this.selectedText = button.text;
          break;
        }
      }
    });
  }
}

```

**Template:**

```html
<button
  aria-haspopup="dialog"
  class="sky-btn sky-btn-default sky-margin-inline-sm ok-confirm-btn"
  type="button"
  (click)="openOKConfirm()"
>
  OK confirm
</button>

<button
  aria-haspopup="dialog"
  class="sky-btn sky-btn-default sky-margin-inline-sm two-action-confirm-btn"
  type="button"
  (click)="openTwoActionConfirm()"
>
  Confirm with two actions
</button>

<button
  aria-haspopup="dialog"
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="openThreeActionConfirm()"
>
  Confirm with three actions
</button>

<button
  aria-haspopup="dialog"
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="openDeleteConfirm()"
>
  Confirm with delete button
</button>

@if (selectedAction) {
  @if (selectedText) {
    <p class="displayed-text">
      You selected the "{{ selectedText }}" button, which has an action of "{{
        selectedAction
      }}."
    </p>
  } @else {
    <p class="displayed-text">
      You selected the "{{ selectedAction }}" action.
    </p>
  }
}

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.