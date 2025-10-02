---
component: 'dropdown'
type: 'code-examples'
description: 'Code examples for the dropdown component.'
---

# Dropdown Code Examples

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