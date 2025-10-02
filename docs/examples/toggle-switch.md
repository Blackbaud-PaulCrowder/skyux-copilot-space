---
component: 'toggle-switch'
type: 'code-examples'
description: 'Code examples for the toggle-switch component.'
---

# Toggle Switch Code Examples

## Toggle switch with basic setup

**Component:** FormsToggleSwitchBasicExampleComponent

**Selector:** `app-forms-toggle-switch-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyToggleSwitchHarness } from '@skyux/forms/testing';

import { FormsToggleSwitchBasicExampleComponent } from './example.component';

describe('Basic toggle switch example', () => {
  async function setupTest(options: {
    dataSkyId: string;
  }): Promise<SkyToggleSwitchHarness> {
    const fixture = TestBed.createComponent(
      FormsToggleSwitchBasicExampleComponent,
    );

    const loader = TestbedHarnessEnvironment.loader(fixture);

    const toggleSwitchHarness = await loader.getHarness(
      SkyToggleSwitchHarness.with({ dataSkyId: options.dataSkyId }),
    );

    fixture.detectChanges();
    await fixture.whenStable();

    return toggleSwitchHarness;
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [NoopAnimationsModule, FormsToggleSwitchBasicExampleComponent],
    });
  });

  it('should set up the component', async () => {
    const toggleSwitchHarness = await setupTest({ dataSkyId: 'toggle-switch' });

    await expectAsync(toggleSwitchHarness.getLabelText()).toBeResolvedTo(
      'Open for registration',
    );

    await expectAsync(toggleSwitchHarness.isChecked()).toBeResolvedTo(false);
    await toggleSwitchHarness.check();
    await expectAsync(toggleSwitchHarness.isChecked()).toBeResolvedTo(true);
    await toggleSwitchHarness.uncheck();
    await toggleSwitchHarness.blur();
    await expectAsync(toggleSwitchHarness.isChecked()).toBeResolvedTo(false);
  });

  it('should show a help popover with the expected text', async () => {
    const toggleSwitchHarness = await setupTest({
      dataSkyId: 'toggle-switch',
    });

    await toggleSwitchHarness.clickHelpInline();

    const helpPopoverContent =
      await toggleSwitchHarness.getHelpPopoverContent();
    expect(helpPopoverContent).toBe(
      `When you open an event, a registration page becomes available online, and admins are able to register people to attend.`,
    );
  });
});

```

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyToggleSwitchModule } from '@skyux/forms';

interface ToggleSwitchFormType {
  registration: FormControl<boolean | null>;
}

/**
 * @title Toggle switch with basic setup
 */
@Component({
  selector: 'app-forms-toggle-switch-basic-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyToggleSwitchModule],
})
export class FormsToggleSwitchBasicExampleComponent {
  protected formGroup: FormGroup;
  protected helpPopoverContent =
    'When you open an event, a registration page becomes available online, and admins are able to register people to attend.';

  constructor() {
    this.formGroup = inject(FormBuilder).group<ToggleSwitchFormType>({
      registration: new FormControl(false),
    });
  }
}

```

#### example.component.html

```html
<form [formGroup]="formGroup">
  <sky-toggle-switch
    data-sky-id="toggle-switch"
    formControlName="registration"
    labelText="Open for registration"
    [helpPopoverContent]="helpPopoverContent"
  />
</form>

```

---

## Toggle switch with help key

**Component:** FormsToggleSwitchHelpKeyExampleComponent

**Selector:** `app-forms-toggle-switch-help-key-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import {
  SkyHelpTestingController,
  SkyHelpTestingModule,
} from '@skyux/core/testing';
import { SkyToggleSwitchHarness } from '@skyux/forms/testing';

import { FormsToggleSwitchHelpKeyExampleComponent } from './example.component';

describe('Basic toggle switch example', () => {
  async function setupTest(options: { dataSkyId: string }): Promise<{
    toggleSwitchHarness: SkyToggleSwitchHarness;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(
      FormsToggleSwitchHelpKeyExampleComponent,
    );

    const loader = TestbedHarnessEnvironment.loader(fixture);

    const toggleSwitchHarness = await loader.getHarness(
      SkyToggleSwitchHarness.with({ dataSkyId: options.dataSkyId }),
    );

    const helpController = TestBed.inject(SkyHelpTestingController);

    fixture.detectChanges();
    await fixture.whenStable();

    return { toggleSwitchHarness, helpController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        NoopAnimationsModule,
        FormsToggleSwitchHelpKeyExampleComponent,
        SkyHelpTestingModule,
      ],
    });
  });

  it('should set up the component', async () => {
    const { toggleSwitchHarness } = await setupTest({
      dataSkyId: 'toggle-switch',
    });

    await expectAsync(toggleSwitchHarness.getLabelText()).toBeResolvedTo(
      'Open for registration',
    );

    await expectAsync(toggleSwitchHarness.isChecked()).toBeResolvedTo(false);
    await toggleSwitchHarness.check();
    await expectAsync(toggleSwitchHarness.isChecked()).toBeResolvedTo(true);
    await toggleSwitchHarness.uncheck();
    await toggleSwitchHarness.blur();
    await expectAsync(toggleSwitchHarness.isChecked()).toBeResolvedTo(false);
  });

  it('should have the correct help key for toggle switch', async () => {
    const { toggleSwitchHarness, helpController } = await setupTest({
      dataSkyId: 'toggle-switch',
    });

    await toggleSwitchHarness.clickHelpInline();

    helpController.expectCurrentHelpKey('registration-help');
  });
});

```

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyToggleSwitchModule } from '@skyux/forms';

interface ToggleSwitchFormType {
  registration: FormControl<boolean | null>;
}

/**
 * @title Toggle switch with help key
 */
@Component({
  selector: 'app-forms-toggle-switch-help-key-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyToggleSwitchModule],
})
export class FormsToggleSwitchHelpKeyExampleComponent {
  protected formGroup: FormGroup;

  constructor() {
    this.formGroup = inject(FormBuilder).group<ToggleSwitchFormType>({
      registration: new FormControl(false),
    });
  }
}

```

#### example.component.html

```html
<form [formGroup]="formGroup">
  <sky-toggle-switch
    data-sky-id="toggle-switch"
    formControlName="registration"
    helpKey="registration-help"
    labelText="Open for registration"
  />
</form>

```

---