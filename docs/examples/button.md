---
component: 'button'
type: 'code-examples'
description: 'Code examples for the button component.'
---

# Button Code Examples

## Icons in buttons

**Component:** IconIconButtonExampleComponent

**Selector:** `app-icon-icon-button-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyIconHarness } from '@skyux/icon/testing';

import { IconIconButtonExampleComponent } from './example.component';

describe('Icon button', () => {
  async function setupTest(options: { dataSkyId?: string }): Promise<{
    iconHarness: SkyIconHarness;
    fixture: ComponentFixture<IconIconButtonExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(IconIconButtonExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const iconHarness = await loader.getHarness(
      SkyIconHarness.with({
        dataSkyId: options?.dataSkyId,
      }),
    );

    return { iconHarness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [IconIconButtonExampleComponent],
    });
  });

  it('should display the icon in the text icon button', async () => {
    const { iconHarness, fixture } = await setupTest({
      dataSkyId: 'text-button-icon',
    });

    fixture.detectChanges();

    await expectAsync(iconHarness.getIconName()).toBeResolvedTo('save');
  });

  it('should display the icon in the icon only button', async () => {
    const { iconHarness, fixture } = await setupTest({
      dataSkyId: 'button-icon',
    });

    fixture.detectChanges();

    await expectAsync(iconHarness.getIconName()).toBeResolvedTo('edit');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyIconModule } from '@skyux/icon';

/**
 * @title Icons in buttons
 */
@Component({
  selector: 'app-icon-icon-button-example',
  templateUrl: './example.component.html',
  imports: [SkyIconModule],
})
export class IconIconButtonExampleComponent {
  protected textButtonClick(): void {
    alert('Text with icon button clicked');
  }

  protected iconOnlyButtonClick(): void {
    alert('Icon only button clicked');
  }
}

```

#### example.component.html

```html
<button
  class="sky-btn sky-btn-default"
  type="button"
  (click)="textButtonClick()"
>
  <sky-icon data-sky-id="text-button-icon" iconName="save" />
  Save
</button>

<button
  class="sky-btn sky-btn-icon-borderless"
  type="button"
  (click)="iconOnlyButtonClick()"
>
  <sky-icon data-sky-id="button-icon" iconName="edit" />
</button>

```

---

## Inline form with custom buttons

**Component:** InlineFormCustomButtonsExampleComponent

**Selector:** `app-inline-form-custom-buttons-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyInlineFormHarness } from '@skyux/inline-form/testing';

import { InlineFormCustomButtonsExampleComponent } from './example.component';

describe('Inline form custom button demo', () => {
  async function setupTest(options: { dataSkyId?: string }): Promise<{
    harness: SkyInlineFormHarness;
    fixture: ComponentFixture<InlineFormCustomButtonsExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [InlineFormCustomButtonsExampleComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      InlineFormCustomButtonsExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const harness = await loader.getHarness(
      SkyInlineFormHarness.with({ dataSkyId: options.dataSkyId }),
    );
    return { harness, fixture };
  }

  it('should change the first name', async () => {
    const { harness, fixture } = await setupTest({
      dataSkyId: 'first-name',
    });

    // You can query components inside the inline form when closed.
    const editButton = await harness.querySelector('button.sky-btn');
    await editButton.click();

    await expectAsync(harness.isFormExpanded()).toBeResolvedTo(true);

    // You can query inline form buttons when the form is open.
    const buttons = await harness.getButtons();
    expect(fixture.componentInstance.formGroup.controls.firstName.value).toBe(
      'Jane',
    );
    await expectAsync(buttons[0].getText()).toBeResolvedTo('Save');
    await expectAsync(buttons[1].getStyleType()).toBeResolvedTo('default');

    // You can query components from the inline form template when the form is open.
    const inputHarness = await (
      await harness.getTemplate()
    ).querySelector('input');

    await inputHarness.sendKeys('t');
    await inputHarness.blur();
    fixture.detectChanges();

    await buttons[0].click();
    await expectAsync(harness.isFormExpanded()).toBeResolvedTo(false);

    await editButton.click();
    fixture.detectChanges();
    expect(fixture.componentInstance.formGroup.controls.firstName.value).toBe(
      'Janet',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component, OnInit, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyIconModule } from '@skyux/icon';
import {
  SkyInlineFormButtonLayout,
  SkyInlineFormCloseArgs,
  SkyInlineFormConfig,
  SkyInlineFormModule,
} from '@skyux/inline-form';

interface DemoForm {
  firstName: FormControl<string>;
}

/**
 * @title Inline form with custom buttons
 */
@Component({
  selector: 'app-inline-form-custom-buttons-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyIconModule,
    SkyInlineFormModule,
    SkyInputBoxModule,
  ],
})
export class InlineFormCustomButtonsExampleComponent implements OnInit {
  protected firstName = 'Jane';
  public formGroup: FormGroup<DemoForm>;

  protected inlineFormConfig: SkyInlineFormConfig = {
    buttonLayout: SkyInlineFormButtonLayout.Custom,
    buttons: [
      {
        action: 'save',
        text: 'Save',
        styleType: 'primary',
      },
      {
        action: 'clear',
        text: 'Clear',
        styleType: 'default',
      },
      {
        action: 'reset',
        text: 'Reset',
        styleType: 'default',
      },
      {
        action: 'cancel',
        text: 'Cancel',
        styleType: 'link',
      },
    ],
  };

  protected showForm = false;

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      firstName: new FormControl<string>('', { nonNullable: true }),
    });
  }

  public ngOnInit(): void {
    this.formGroup.valueChanges.subscribe(() => {
      if (
        this.inlineFormConfig.buttons &&
        this.inlineFormConfig.buttons[0].disabled !== this.formGroup.invalid
      ) {
        this.inlineFormConfig.buttons[0].disabled = this.formGroup.invalid;
        this.inlineFormConfig = { ...{}, ...this.inlineFormConfig };
      }
    });
  }

  protected onInlineFormClose(args: SkyInlineFormCloseArgs): void {
    switch (args.reason) {
      case 'save':
        this.firstName = this.formGroup.value.firstName ?? '';
        this.showForm = false;
        break;

      case 'clear':
        this.formGroup.patchValue({ firstName: '' });
        break;

      case 'reset':
        this.formGroup.setValue({ firstName: this.firstName });
        break;

      default:
        this.showForm = false;
        break;
    }
  }

  protected onInlineFormOpen(): void {
    this.showForm = true;
    this.formGroup.patchValue({
      firstName: this.firstName,
    });
  }
}

```

#### example.component.html

```html
<sky-inline-form
  data-sky-id="first-name"
  [config]="inlineFormConfig"
  [showForm]="showForm"
  [template]="inlineFormTemplate"
  (close)="onInlineFormClose($event)"
>
  <table>
    <tr>
      <th>First name:</th>
      <td>
        {{ firstName }}
      </td>
      <td>
        <button
          aria-label="Edit"
          class="sky-btn sky-btn-icon-borderless"
          type="button"
          (click)="onInlineFormOpen()"
        >
          <sky-icon iconName="edit" />
        </button>
      </td>
    </tr>
  </table>
</sky-inline-form>

<ng-template #inlineFormTemplate>
  <form [formGroup]="formGroup">
    <sky-input-box labelText="First name">
      <input formControlName="firstName" required type="text" />
    </sky-input-box>
  </form>
</ng-template>

```

---

## Basic action buttons

**Component:** LayoutActionButtonBasicExampleComponent

**Selector:** `app-layout-action-button-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyActionButtonModule } from '@skyux/layout';

/**
 * @title Basic action buttons
 */
@Component({
  selector: 'app-layout-action-button-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyActionButtonModule],
})
export class LayoutActionButtonBasicExampleComponent {
  protected filterActionClick(): void {
    alert('Filter action clicked');
  }

  protected openActionClick(): void {
    alert('Open action clicked');
  }
}

```

#### example.component.html

```html
<sky-action-button-container>
  <sky-action-button (actionClick)="filterActionClick()">
    <sky-action-button-icon iconName="filter" />
    <sky-action-button-header> Build a new list </sky-action-button-header>
    <sky-action-button-details>
      Start from scratch and fine-tune with filters.
    </sky-action-button-details>
  </sky-action-button>

  <sky-action-button (actionClick)="openActionClick()">
    <sky-action-button-icon iconName="folder-open" />
    <sky-action-button-header> Open a saved list </sky-action-button-header>
    <sky-action-button-details>
      Open a list with filters saved in the web view.
    </sky-action-button-details>
  </sky-action-button>
</sky-action-button-container>

```

---

## Action button with permalinks

**Component:** LayoutActionButtonPermalinkExampleComponent

**Selector:** `app-layout-action-button-permalink-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyActionButtonModule, SkyActionButtonPermalink } from '@skyux/layout';

/**
 * @title Action button with permalinks
 */
@Component({
  selector: 'app-layout-action-button-permalink-example',
  templateUrl: './example.component.html',
  imports: [SkyActionButtonModule],
})
export class LayoutActionButtonPermalinkExampleComponent {
  protected routerlink: SkyActionButtonPermalink = {
    route: {
      commands: [],
      extras: {
        queryParams: {
          component: 'MyComponent',
        },
      },
    },
  };

  protected url: SkyActionButtonPermalink = {
    url: 'https://www.stackblitz.com',
  };
}

```

#### example.component.html

```html
<sky-action-button-container>
  <sky-action-button [permalink]="url">
    <sky-action-button-icon iconName="link" />
    <sky-action-button-header> Open a link </sky-action-button-header>
    <sky-action-button-details> Open a link. </sky-action-button-details>
  </sky-action-button>

  <sky-action-button [permalink]="routerlink">
    <sky-action-button-icon iconName="link" />
    <sky-action-button-header> Open a router link </sky-action-button-header>
    <sky-action-button-details> Open a router link. </sky-action-button-details>
  </sky-action-button>
</sky-action-button-container>

```

---