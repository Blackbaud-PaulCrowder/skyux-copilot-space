---
component: 'progress-indicator-waterfall'
description: 'Design guidelines, API documentation, and usage instructions for the progress-indicator-waterfall component extracted from SKY UX documentation.'
---

# Progress Indicator Waterfall Component Guidelines

## Component Overview
Waterfall progress indicators walk users through sequential steps in lengthy or complex tasks.

## Usage

### ✅ Use when

Use waterfall progress indicators for long or complex setup processes with at least three steps that users typically complete only once. Waterfall indicators are ideal when events outside of the system force users to complete tasks in multiple sittings or when users must enter large amounts of data.

**✅ Do use waterfall progress indicators for complex configuration processes that users may complete in stages.**

Use waterfall progress indicators when the complexity of steps varies drastically. For example, one step may require a full-screen modal for complex interactions, while another step requires a small modal for a few simple inputs. Waterfall steps can open wizards if necessary.

**✅ Do use modals of the appropriate size for the interactions in each waterfall step.**

### ❌ Don't use when

Don't use waterfall progress indicators when users monitor a sequence of events but are not responsible for completing the steps. Use passive progress indicators instead.

**❌ Don't use waterfall progress indicators for steps outside of user control.**

Don't use waterfall progress indicators when users perform tasks repeatedly or when tasks are best presented as multiple steps but only require a single sitting. Use wizards instead.

**❌ Don't use waterfall progress indicators for brief interactions, even when they are best divided into multiple steps.**

Don't use waterfall progress indicators when processes include fewer than three steps or when the number or order of steps may change. If early decisions branch in different directions, arrange the workflow so that users make those decisions before the progress indicator.

**❌ Don't present waterfall progress indicators before the extent of tasks is known.**

Don't use waterfall progress indicators to edit properties after completing configuration processes. Use modals instead.

If configuration properties are interrelated and require users to reexamine all or most properties, then reframe the editing task as “starting over” and restart the waterfall process.

**❌ Don't revert finished states to edit properties in waterfall progress indicators.**

## Anatomy

- Waterfall title
- Step indicator
- Step label
- Completed step action
- Active step action
- Step details
- Help inline button
- Start-over action

## Options

### Waterfall title

We strongly recommend including a waterfall title to reflect the context of the overall task. Do not use a left-aligned page title when you include a waterfall title. The waterfall title does not change when users progress through the waterfall steps.

### Help inline button

When you need to supplement a waterfall title with additional information but don't require persistent inline help, you can place a help inline button beside the title to invoke contextual user assistance.

### Step details

You can provide additional details about completed steps, but limit details to single pieces of information. Don't go overboard because users can reopen modals to review choices as necessary.

### Start-over action

You can include a start-over action to let users erase all saved data from the waterfall process. This returns users to the first step or to an earlier point in the workflow if decisions occurred before the waterfall progress indicator.

## Behavior & states

Waterfall progress indicators guide users through one active step at a time. When users complete a step, the progress indicator updates its step indicator and step action to the completed state and updates the next step indicator and step action to the active state. Users can review and edit completed steps, but this does not undo the completed state.

The final step summarizes the changes and requests user confirmation. You do not need to include all data that users enter in the summary, but confirmation is required. After users complete the final step, replace the waterfall progress indicator with a page that displays the finished or active state of the system.

## Content

Use a waterfall title in place of an ordinary page title to provide context for the overall task. Follow the same pattern as modal titles and start the waterfall title with a verb that indicates the action that occurs when users complete the waterfall steps.

For step labels, start with a number and concisely describe the objective using the <verb> <direct object> format. In the label for the last step, describe the cumulative change that occurs at the end of the process.

Step action (button) labels closely follow step labels and use the same <verb> <direct object> format, but they do not need to be identical. For the first step action label, be generic and conversational (“Get started”), and for completed step actions, use verbs appropriate to post hoc actions (“Change”, “Edit”).

### Layout

Waterfall progress indicators are 400 pixels wide and centered inside the page. The waterfall title is the page title. Do not combine waterfall indicators with other content or actions. If waterfall indicators require extra context such as descriptions, links, or instructions, include it after the waterfall title and before the first step.

**✅ Do use waterfall progress indicators as the only content on a page while users complete them.**

## Related information

### Components

- Help inline button
- Modal
- Passive progress indicator
- Wizard (Tabs)

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### ProgressIndicatorWaterfallIndicatorBasicExampleComponent

**Selector:** `app-progress-indicator-waterfall-indicator-basic-example`

**Package:** `@skyux/code-examples`

### Code Examples

#### Waterfall progress indicator

**Selector:** `app-progress-indicator-waterfall-indicator-basic-example`

**TypeScript:**

```typescript
import {
  ChangeDetectionStrategy,
  ChangeDetectorRef,
  Component,
  inject,
} from '@angular/core';
import { SkyModalCloseArgs, SkyModalService } from '@skyux/modals';
import {
  SkyProgressIndicatorChange,
  SkyProgressIndicatorMessage,
  SkyProgressIndicatorMessageType,
  SkyProgressIndicatorModule,
} from '@skyux/progress-indicator';

import { Subject } from 'rxjs';
import { take } from 'rxjs/operators';

import { ModalContext } from './modal-context';
import { ModalComponent } from './modal.component';

/**
 * @title Waterfall progress indicator
 */
@Component({
  selector: 'app-progress-indicator-waterfall-indicator-basic-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
  imports: [SkyProgressIndicatorModule],
})
export class ProgressIndicatorWaterfallIndicatorBasicExampleComponent {
  protected activeIndex: number | undefined = 0;

  protected progressMessageStream = new Subject<
    SkyProgressIndicatorMessage | SkyProgressIndicatorMessageType
  >();

  readonly #changeDetectorRef = inject(ChangeDetectorRef);
  readonly #modalSvc = inject(SkyModalService);

  protected configureConnection(isProgress: boolean): void {
    this.#openModalForm(
      {
        title: 'Configure connection',
        buttonText: 'Submit connection settings',
      },
      isProgress,
    );
  }

  protected setServer(isProgress: boolean): void {
    this.#openModalForm(
      {
        title: 'Select remote server',
        buttonText: 'Submit server choice',
      },
      isProgress,
    );
  }

  protected testConnection(isProgress: boolean): void {
    this.#openModalForm(
      {
        title: 'Connection confirmed.',
        buttonText: 'OK',
      },
      isProgress,
    );
  }

  protected alertMessage(message: string): void {
    alert(message);
  }

  protected updateIndex(changes: SkyProgressIndicatorChange): void {
    this.activeIndex = changes.activeIndex;
    this.#changeDetectorRef.detectChanges();
  }

  protected resetClicked(): void {
    this.progressMessageStream.next(SkyProgressIndicatorMessageType.Reset);
  }

  private progress(): void {
    this.progressMessageStream.next(SkyProgressIndicatorMessageType.Progress);
  }

  #openModalForm(context: ModalContext, isProgress: boolean): void {
    const modalForm = this.#modalSvc.open(ModalComponent, [
      {
        provide: ModalContext,
        useValue: context,
      },
    ]);

    modalForm.closed.pipe(take(1)).subscribe((args: SkyModalCloseArgs) => {
      if (args.reason === 'save' && isProgress) {
        this.progress();
      }
    });
  }
}

```

**Template:**

```html
<sky-progress-indicator
  #progressIndicator
  data-sky-id="example-progress-indicator"
  [messageStream]="progressMessageStream"
  [startingIndex]="2"
  (progressChanges)="updateIndex($event)"
>
  <sky-progress-indicator-title>
    Set up my connection
  </sky-progress-indicator-title>

  <sky-progress-indicator-item
    data-sky-id="configure-connection"
    helpPopoverContent="Example help for configure connection"
    title="Configure connection"
  >
    <div>
      @if (activeIndex === 0) {
        <button
          class="sky-btn sky-btn-primary"
          type="button"
          (click)="configureConnection(true)"
        >
          Set up connection
        </button>
      }
      @if (activeIndex && activeIndex > 0) {
        <button
          class="sky-btn sky-btn-link"
          type="button"
          (click)="configureConnection(false)"
        >
          Edit connection
        </button>
      }
    </div>
  </sky-progress-indicator-item>

  <sky-progress-indicator-item
    helpPopoverContent="Example help for select remote server"
    helpPopoverTitle="Which server is right for me?"
    title="Select remote server"
  >
    @if (activeIndex && activeIndex >= 1) {
      <div>
        @if (activeIndex === 1) {
          <button
            class="sky-btn sky-btn-primary"
            type="button"
            (click)="setServer(true)"
          >
            Select server
          </button>
        } @else {
          <button
            class="sky-btn sky-btn-link"
            type="button"
            (click)="setServer(false)"
          >
            Change server
          </button>
        }
      </div>
    }
  </sky-progress-indicator-item>

  <sky-progress-indicator-item
    data-sky-id="test-connection"
    title="Test connection"
  >
    @if (activeIndex && activeIndex >= 2) {
      <div>
        @if (activeIndex === 2) {
          <button
            class="sky-btn sky-btn-primary"
            type="button"
            (click)="testConnection(true)"
          >
            Test connection
          </button>
        } @else {
          <button
            class="sky-btn sky-btn-link"
            type="button"
            (click)="testConnection(false)"
          >
            Retest connection
          </button>
        }
      </div>
    }
  </sky-progress-indicator-item>

  <sky-progress-indicator-item title="Turn on connection">
    @if (activeIndex && activeIndex >= 3) {
      <div>
        @if (activeIndex === 3) {
          <button
            class="sky-btn sky-btn-primary"
            type="button"
            (click)="alertMessage('Form completed')"
          >
            Turn on
          </button>
        }
      </div>
    }
  </sky-progress-indicator-item>

  <sky-progress-indicator-reset-button [progressIndicator]="progressIndicator">
    Erase all settings
  </sky-progress-indicator-reset-button>
</sky-progress-indicator>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.