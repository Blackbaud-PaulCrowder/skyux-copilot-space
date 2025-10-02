---
component: 'progress-indicator-waterfall'
type: 'code-examples'
description: 'Code examples for the progress-indicator-waterfall component.'
---

# Progress Indicator Waterfall Code Examples

## Waterfall progress indicator

**Component:** ProgressIndicatorWaterfallIndicatorBasicExampleComponent

**Selector:** `app-progress-indicator-waterfall-indicator-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyProgressIndicatorHarness } from '@skyux/progress-indicator/testing';

import { ProgressIndicatorWaterfallIndicatorBasicExampleComponent } from './example.component';

describe('Basic passive progress indicator example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    harness: SkyProgressIndicatorHarness;
    fixture: ComponentFixture<ProgressIndicatorWaterfallIndicatorBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      ProgressIndicatorWaterfallIndicatorBasicExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const harness = await loader.getHarness(
      SkyProgressIndicatorHarness.with({ dataSkyId: options.dataSkyId }),
    );

    fixture.detectChanges();
    await fixture.whenStable();

    return { harness, fixture };
  }

  it('should have the initial progress set', async () => {
    const { harness } = await setupTest({
      dataSkyId: 'example-progress-indicator',
    });

    await expectAsync(harness.getTitle()).toBeResolvedTo(
      'Set up my connection',
    );

    const items = await harness.getItems();

    expect(items.length).toBe(4);

    const configureStep = harness.getItem({
      dataSkyId: 'configure-connection',
    });
    await expectAsync((await configureStep).getTitle()).toBeResolvedTo(
      'Configure connection',
    );
  });

  it('should reset connection setup', async () => {
    const { harness } = await setupTest({
      dataSkyId: 'example-progress-indicator',
    });

    await harness.clickResetButton();
    const firstStep = (await harness.getItems())[0];
    await expectAsync(firstStep.isCompleted()).toBeResolvedTo(false);
  });
});

```

#### example.component.ts

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

#### modal-context.ts

```typescript
export class ModalContext {
  public title = '';
  public buttonText = '';
}

```

#### modal.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';

import { ModalContext } from './modal-context';

@Component({
  selector: 'app-modal',
  templateUrl: './modal.component.html',
  imports: [SkyModalModule],
})
export class ModalComponent {
  protected readonly context = inject(ModalContext);
  protected readonly instance = inject(SkyModalInstance);

  protected submit(): void {
    this.instance.close(undefined, 'save');
  }
}

```

#### example.component.html

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

#### modal.component.html

```html
<sky-modal [headingText]="context.title">
  <sky-modal-content>
    <br />
    <br />
  </sky-modal-content>
  <sky-modal-footer>
    <button class="sky-btn sky-btn-primary" type="button" (click)="submit()">
      {{ context.buttonText }}
    </button>
  </sky-modal-footer>
</sky-modal>

```

---