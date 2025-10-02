---
component: 'popover'
type: 'code-examples'
description: 'Code examples for the popover component.'
---

# Popover Code Examples

## Help inline button with popover

**Component:** HelpInlinePopoverExampleComponent

**Selector:** `app-help-inline-popover-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { provideNoopAnimations } from '@angular/platform-browser/animations';
import { SkyHelpInlineHarness } from '@skyux/help-inline/testing';

import { HelpInlinePopoverExampleComponent } from './example.component';

describe('Help inline with popover', () => {
  async function setupTest(): Promise<{
    helpInlineHarness: SkyHelpInlineHarness;
    fixture: ComponentFixture<HelpInlinePopoverExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(HelpInlinePopoverExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const helpInlineHarness = await loader.getHarness(
      SkyHelpInlineHarness.with({
        dataSkyId: 'help-inline-example',
      }),
    );

    return { fixture, helpInlineHarness };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [HelpInlinePopoverExampleComponent],
      providers: [provideNoopAnimations()],
    });
  });

  it('should launch a popover', async () => {
    const { fixture, helpInlineHarness } = await setupTest();

    fixture.detectChanges();

    await helpInlineHarness.click();
    fixture.detectChanges();
    await fixture.whenStable();

    await expectAsync(helpInlineHarness.getPopoverContent()).toBeResolvedTo(
      'The estimated income expected for the current year.',
    );

    await expectAsync(helpInlineHarness.getPopoverTitle()).toBeResolvedTo(
      'Projected revenue',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyHelpInlineModule } from '@skyux/help-inline';

/**
 * @title Help inline button with popover
 */
@Component({
  imports: [SkyHelpInlineModule],
  selector: 'app-help-inline-popover-example',
  templateUrl: './example.component.html',
})
export class HelpInlinePopoverExampleComponent {}

```

#### example.component.html

```html
<h3>
  Projected revenue
  <sky-help-inline
    ariaLabel="Information about Projected revenue"
    data-sky-id="help-inline-example"
    popoverContent="The estimated income expected for the current year."
    popoverTitle="Projected revenue"
  />
</h3>

```

---

## Dropdown with basic setup

**Component:** PopoversDropdownBasicExampleComponent

**Selector:** `app-popovers-dropdown-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { expect } from '@skyux-sdk/testing';
import { SkyDropdownHarness } from '@skyux/popovers/testing';

import { PopoversDropdownBasicExampleComponent } from './example.component';

describe('Basic dropdown', () => {
  async function setupTest(): Promise<{
    dropdownHarness: SkyDropdownHarness;
    fixture: ComponentFixture<PopoversDropdownBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      PopoversDropdownBasicExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const dropdownHarness = await loader.getHarness(
      SkyDropdownHarness.with({
        dataSkyId: 'dropdown-example',
      }),
    );

    return { dropdownHarness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [PopoversDropdownBasicExampleComponent],
    });
  });

  it('should display the correct dropdown', async () => {
    const { dropdownHarness, fixture } = await setupTest();

    fixture.detectChanges();

    await expectAsync(dropdownHarness.getButtonStyle()).toBeResolvedTo(
      'default',
    );
    await expectAsync(dropdownHarness.getButtonType()).toBeResolvedTo('select');
    await expectAsync(dropdownHarness.isDisabled()).toBeResolvedTo(false);
    await expectAsync(dropdownHarness.getAriaLabel()).toBeResolvedTo(
      'Test dropdown',
    );
    await expectAsync(dropdownHarness.getTitle()).toBeResolvedTo(null);
    await expectAsync(dropdownHarness.isOpen()).toBeResolvedTo(false);
  });

  it('should open the correct dropdown menu', async () => {
    const { dropdownHarness, fixture } = await setupTest();

    fixture.detectChanges();
    await dropdownHarness.clickDropdownButton();
    fixture.detectChanges();

    const dropdownMenu = await dropdownHarness.getDropdownMenu();
    const dropdownMenuItems = await dropdownMenu.getItems();

    await expectAsync(dropdownHarness.isOpen()).toBeResolvedTo(true);
    await expectAsync(dropdownMenu.getAriaRole()).toBeResolvedTo('menu');

    await expectAsync(dropdownMenuItems?.[0].getText()).toBeResolvedTo(
      'Option 1',
    );
  });

  it('should click the correct dropdown menu item', async () => {
    const { dropdownHarness, fixture } = await setupTest();

    const clickSpy = spyOn(fixture.componentInstance, 'actionClicked');
    fixture.detectChanges();
    await dropdownHarness.clickDropdownButton();
    fixture.detectChanges();

    const dropdownMenu = await dropdownHarness.getDropdownMenu();
    const dropdownMenuItem = await dropdownMenu.getItem({ text: 'Option 1' });

    await dropdownMenuItem?.click();

    expect(clickSpy).toHaveBeenCalledWith('Option 1');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyDropdownModule } from '@skyux/popovers';

interface DropdownItem {
  name: string;
  disabled: boolean;
}

/**
 * @title Dropdown with basic setup
 */
@Component({
  selector: 'app-popovers-dropdown-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyDropdownModule],
})
export class PopoversDropdownBasicExampleComponent {
  protected items: DropdownItem[] = [
    { name: 'Option 1', disabled: false },
    { name: 'Disabled option', disabled: true },
    { name: 'Option 3', disabled: false },
    { name: 'Option 4', disabled: false },
    { name: 'Option 5', disabled: false },
  ];

  public actionClicked(action: string): void {
    alert(`You selected ${action}.`);
  }
}

```

#### example.component.html

```html
<sky-dropdown data-sky-id="dropdown-example" label="Test dropdown">
  <sky-dropdown-button> Show dropdown </sky-dropdown-button>
  <sky-dropdown-menu>
    @for (item of items; track item) {
      <sky-dropdown-item>
        <button
          type="button"
          [attr.disabled]="item.disabled ? '' : null"
          (click)="actionClicked(item.name)"
        >
          {{ item.name }}
        </button>
      </sky-dropdown-item>
    }
  </sky-dropdown-menu>
</sky-dropdown>
<br />
<sky-dropdown buttonType="context-menu" label="Code example context menu">
  <sky-dropdown-menu>
    @for (item of items; track item) {
      <sky-dropdown-item>
        <button
          type="button"
          [attr.disabled]="item.disabled ? '' : null"
          (click)="actionClicked(item.name)"
        >
          {{ item.name }}
        </button>
      </sky-dropdown-item>
    }
  </sky-dropdown-menu>
</sky-dropdown>

```

---

## Popover with basic setup

**Component:** PopoversPopoverBasicExampleComponent

**Selector:** `app-popovers-popover-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyPopoverAlignment, SkyPopoverPlacement } from '@skyux/popovers';
import { SkyPopoverHarness } from '@skyux/popovers/testing';

import { PopoversPopoverBasicExampleComponent } from './example.component';

describe('Basic popover', () => {
  async function setupTest(options?: {
    titleText?: string;
    alignment?: SkyPopoverAlignment;
    placement?: SkyPopoverPlacement;
  }): Promise<{
    popoverHarness: SkyPopoverHarness;
    fixture: ComponentFixture<PopoversPopoverBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      PopoversPopoverBasicExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    if (options) {
      fixture.componentInstance.popoverAlignment = options.alignment;
      fixture.componentInstance.popoverPlacement = options.placement;
      fixture.componentInstance.popoverTitle = options.titleText;
    }

    fixture.detectChanges();
    await fixture.whenStable();

    const popoverHarness = await loader.getHarness(
      SkyPopoverHarness.with({
        dataSkyId: 'popover-example',
      }),
    );

    return { popoverHarness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [PopoversPopoverBasicExampleComponent, NoopAnimationsModule],
    });
  });

  it('should open and close when the user interacts with the trigger', async () => {
    const { popoverHarness } = await setupTest();

    await expectAsync(popoverHarness.isOpen()).toBeResolvedTo(false);

    await popoverHarness.clickPopoverButton();
    await expectAsync(popoverHarness.isOpen()).toBeResolvedTo(true);

    await popoverHarness.clickPopoverButton();
    await expectAsync(popoverHarness.isOpen()).toBeResolvedTo(false);
  });

  it('should expose content properties when visible', async () => {
    const { popoverHarness } = await setupTest({
      titleText: 'Did you know?',
      placement: 'right',
    });

    await popoverHarness.clickPopoverButton();
    const contentHarness = await popoverHarness.getPopoverContent();

    await expectAsync(contentHarness.getTitleText()).toBeResolvedTo(
      'Did you know?',
    );
    await expectAsync(contentHarness.getBodyText()).toBeResolvedTo(
      'This is a popover.',
    );
    await expectAsync(contentHarness.getAlignment()).toBeResolvedTo('center');
    await expectAsync(contentHarness.getPlacement()).toBeResolvedTo('right');

    await popoverHarness.clickPopoverButton();
    // Attempting to call this method when the popover is closed will result in an error.
    await expectAsync(popoverHarness.getPopoverContent()).toBeRejectedWithError(
      'Unable to retrieve the popover content because the popover is not open.',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import {
  SkyPopoverAlignment,
  SkyPopoverModule,
  SkyPopoverPlacement,
} from '@skyux/popovers';

/**
 * @title Popover with basic setup
 */
@Component({
  selector: 'app-popovers-popover-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyPopoverModule],
})
export class PopoversPopoverBasicExampleComponent {
  public popoverAlignment: SkyPopoverAlignment | undefined;
  public popoverBody = 'This is a popover.';
  public popoverPlacement: SkyPopoverPlacement | undefined;
  public popoverTitle: string | undefined = 'Did you know?';
}

```

#### example.component.html

```html
<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  data-sky-id="popover-example"
  type="button"
  [skyPopover]="myPopover"
  [skyPopoverAlignment]="popoverAlignment"
  [skyPopoverPlacement]="popoverPlacement"
>
  Open popover
</button>

<sky-popover #myPopover [popoverTitle]="popoverTitle">
  {{ popoverBody }}
</sky-popover>

```

---

## Popover with programmatic interactions

**Component:** PopoversPopoverProgrammaticExampleComponent

**Selector:** `app-popovers-popover-programmatic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyHelpInlineModule } from '@skyux/help-inline';
import {
  SkyPopoverMessage,
  SkyPopoverMessageType,
  SkyPopoverModule,
} from '@skyux/popovers';

import { Subject } from 'rxjs';

/**
 * @title Popover with programmatic interactions
 */
@Component({
  selector: 'app-popovers-popover-programmatic-example',
  templateUrl: './example.component.html',
  imports: [SkyHelpInlineModule, SkyPopoverModule],
})
export class PopoversPopoverProgrammaticExampleComponent {
  protected popoverController = new Subject<SkyPopoverMessage>();

  #popoverOpen = false;

  protected onPopoverStateChange(isOpen: boolean): void {
    this.#popoverOpen = isOpen;
  }

  protected openPopover(): void {
    if (!this.#popoverOpen) {
      this.#sendMessage(SkyPopoverMessageType.Open);
    }
  }

  #sendMessage(type: SkyPopoverMessageType): void {
    const message: SkyPopoverMessage = { type };
    this.popoverController.next(message);
  }
}

```

#### example.component.html

```html
<sky-help-inline
  ariaLabel="Information about Popover using message stream"
  [skyPopover]="myPopover"
  [skyPopoverMessageStream]="popoverController"
/>

<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="openPopover()"
>
  Open popover with message stream
</button>

<sky-popover
  #myPopover
  (popoverClosed)="onPopoverStateChange(false)"
  (popoverOpened)="onPopoverStateChange(true)"
>
  This is a popover.
</sky-popover>

```

---