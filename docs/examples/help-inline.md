---
component: 'help-inline'
type: 'code-examples'
description: 'Code examples for the help-inline component.'
---

# Help Inline Code Examples

## Help inline button with action click

**Component:** HelpInlineActionClickExampleComponent

**Selector:** `app-help-inline-action-click-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyHelpInlineHarness } from '@skyux/help-inline/testing';

import { HelpInlineActionClickExampleComponent } from './example.component';

describe('Help inline with action click', () => {
  async function setupTest(): Promise<{
    helpInlineHarness: SkyHelpInlineHarness;
    fixture: ComponentFixture<HelpInlineActionClickExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      HelpInlineActionClickExampleComponent,
    );
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
      imports: [HelpInlineActionClickExampleComponent],
    });
  });

  it('should click the help inline button', async () => {
    const { fixture, helpInlineHarness } = await setupTest();
    fixture.detectChanges();

    const clickSpy = spyOn(fixture.componentInstance, 'onActionClick');
    await helpInlineHarness.click();
    expect(clickSpy).toHaveBeenCalled();
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyHelpInlineModule } from '@skyux/help-inline';

/**
 * @title Help inline button with action click
 */
@Component({
  imports: [SkyHelpInlineModule],
  selector: 'app-help-inline-action-click-example',
  templateUrl: './example.component.html',
})
export class HelpInlineActionClickExampleComponent {
  public onActionClick(): void {
    alert('Use help inline to show supplemental information to the user.');
  }
}

```

#### example.component.html

```html
<h3>
  Projected revenue
  <sky-help-inline
    ariaLabel="Information about Projected revenue"
    data-sky-id="help-inline-example"
    (actionClick)="onActionClick()"
  />
</h3>

```

---

## Help inline with help key

**Component:** HelpInlineHelpKeyExampleComponent

**Selector:** `app-help-inline-help-key-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { provideNoopAnimations } from '@angular/platform-browser/animations';
import {
  SkyHelpTestingController,
  SkyHelpTestingModule,
} from '@skyux/core/testing';
import { SkyHelpInlineHarness } from '@skyux/help-inline/testing';

import { HelpInlineHelpKeyExampleComponent } from './example.component';

describe('Help inline with help key', () => {
  async function setupTest(): Promise<{
    fixture: ComponentFixture<HelpInlineHelpKeyExampleComponent>;
    helpController: SkyHelpTestingController;
    helpInlineHarness: SkyHelpInlineHarness;
  }> {
    const fixture = TestBed.createComponent(HelpInlineHelpKeyExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const helpInlineHarness = await loader.getHarness(
      SkyHelpInlineHarness.with({
        dataSkyId: 'help-inline-example',
      }),
    );

    const helpController = TestBed.inject(SkyHelpTestingController);

    return { fixture, helpController, helpInlineHarness };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [HelpInlineHelpKeyExampleComponent, SkyHelpTestingModule],
      providers: [provideNoopAnimations()],
    });
  });

  it('should have a help key', async () => {
    const { fixture, helpController, helpInlineHarness } = await setupTest();

    fixture.detectChanges();

    await helpInlineHarness.click();

    helpController.expectCurrentHelpKey('projected-revenue');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyHelpInlineModule } from '@skyux/help-inline';

/**
 * @title Help inline with help key
 */
@Component({
  imports: [SkyHelpInlineModule],
  selector: 'app-help-inline-help-key-example',
  templateUrl: './example.component.html',
})
export class HelpInlineHelpKeyExampleComponent {}

```

#### example.component.html

```html
<h3>
  Projected revenue
  <sky-help-inline
    ariaLabel="Information about Projected revenue"
    data-sky-id="help-inline-example"
    helpKey="projected-revenue"
  />
</h3>

```

---

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