---
component: 'confirm'
type: 'code-examples'
description: 'Code examples for the confirm component.'
---

# Confirm Code Examples

## Confirm, tested with controller

**Component:** ModalsConfirmBasicWithControllerExampleComponent

**Selector:** `app-modals-confirm-basic-with-controller-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { ComponentFixture, TestBed } from '@angular/core/testing';
import {
  SkyConfirmTestingController,
  SkyConfirmTestingModule,
} from '@skyux/modals/testing';

import { ModalsConfirmBasicWithControllerExampleComponent } from './example.component';

describe('Testing with SkyConfirmTestingController', () => {
  function setupTest(): {
    confirmController: SkyConfirmTestingController;
    fixture: ComponentFixture<ModalsConfirmBasicWithControllerExampleComponent>;
  } {
    const confirmController = TestBed.inject(SkyConfirmTestingController);
    const fixture = TestBed.createComponent(
      ModalsConfirmBasicWithControllerExampleComponent,
    );

    return { confirmController, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        SkyConfirmTestingModule,
        ModalsConfirmBasicWithControllerExampleComponent,
      ],
    });
  });

  it('should click "OK" on a confirmation dialog', () => {
    const { confirmController, fixture } = setupTest();

    fixture.componentInstance.launchConfirm();
    fixture.detectChanges();

    confirmController.expectOpen({
      message: 'Are you sure?',
    });

    confirmController.ok();
    confirmController.expectNone();

    expect(fixture.componentInstance.selectedAction).toEqual('ok');
  });

  it('should cancel the confirmation dialog', () => {
    const { confirmController, fixture } = setupTest();

    fixture.componentInstance.launchConfirm();
    fixture.detectChanges();

    confirmController.expectOpen({
      message: 'Are you sure?',
    });

    confirmController.cancel();
    confirmController.expectNone();

    expect(fixture.componentInstance.selectedAction).toEqual('cancel');
  });
});

```

#### example.component.ts

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

---

## Confirm, tested with harness

**Component:** ModalsConfirmBasicWithHarnessExampleComponent

**Selector:** `app-modals-confirm-basic-with-harness-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyConfirmHarness } from '@skyux/modals/testing';

import { ModalsConfirmBasicWithHarnessExampleComponent } from './example.component';

describe('Testing with SkyConfirmHarness', () => {
  async function setupTest(confirmBtnClass: string): Promise<{
    confirmHarness: SkyConfirmHarness;
    fixture: ComponentFixture<ModalsConfirmBasicWithHarnessExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      ModalsConfirmBasicWithHarnessExampleComponent,
    );
    const el = fixture.nativeElement as HTMLElement;
    const openBtn = el.querySelector<HTMLButtonElement>(confirmBtnClass);

    openBtn?.click();

    const rootLoader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const confirmHarness = await rootLoader.getHarness(SkyConfirmHarness);

    return { confirmHarness, fixture };
  }

  function expectDisplayedText(
    fixture: ComponentFixture<ModalsConfirmBasicWithHarnessExampleComponent>,
    expectedText: string,
  ): void {
    expect(
      (fixture.nativeElement as HTMLElement).querySelector<HTMLElement>(
        '.displayed-text',
      )?.innerText,
    ).toEqual(expectedText);
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [ModalsConfirmBasicWithHarnessExampleComponent],
    });
  });

  it('should show the correct text when OK is clicked on an OK confirm', async () => {
    const { confirmHarness, fixture } = await setupTest('.ok-confirm-btn');

    await confirmHarness.clickOkButton();

    expectDisplayedText(fixture, 'You selected the "ok" action.');

    await expectAsync(confirmHarness.getMessageText()).toBeResolvedTo(
      'Cannot delete invoice because it has vendor, credit memo, or purchase order activity.',
    );
  });

  it('should show the correct text when "Finalize" is clicked on a custom confirm', async () => {
    const { confirmHarness, fixture } = await setupTest(
      '.two-action-confirm-btn',
    );

    await confirmHarness.clickCustomButton({ text: 'Finalize' });

    expectDisplayedText(
      fixture,
      'You selected the "Finalize" button, which has an action of "save."',
    );

    await expectAsync(confirmHarness.getMessageText()).toBeResolvedTo(
      'Finalize report cards?',
    );

    await expectAsync(confirmHarness.getBodyText()).toBeResolvedTo(
      'Grades cannot be changed once the report cards are finalized.',
    );
  });
});

```

#### example.component.ts

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

#### example.component.html

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

---