---
component: 'numeric'
type: 'code-examples'
description: 'Code examples for the numeric component.'
---

# Numeric Code Examples

## Currency

**Component:** AutonumericCurrencyExampleComponent

**Selector:** `app-autonumeric-currency-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  ReactiveFormsModule,
  Validators,
} from '@angular/forms';
import {
  SkyAutonumericModule,
  SkyAutonumericOptions,
} from '@skyux/autonumeric';
import { SkyInputBoxModule } from '@skyux/forms';

/**
 * @title Currency
 */
@Component({
  selector: 'app-autonumeric-currency-example',
  templateUrl: './example.component.html',
  imports: [ReactiveFormsModule, SkyAutonumericModule, SkyInputBoxModule],
})
export class AutonumericCurrencyExampleComponent {
  protected autonumericOptions: SkyAutonumericOptions | undefined;

  protected formGroup: FormGroup;

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      donationAmount: new FormControl(1234.5678, [Validators.required]),
    });

    this.autonumericOptions = {
      currencySymbol: ' €',
      currencySymbolPlacement: 's',
      decimalPlaces: 2,
      decimalCharacter: ',',
      digitGroupSeparator: '',
    };
  }
}

```

#### example.component.html

```html
<form [formGroup]="formGroup">
  <sky-input-box labelText="Donation amount">
    <input
      formControlName="donationAmount"
      type="text"
      [skyAutonumeric]="autonumericOptions"
    />
  </sky-input-box>
</form>

```

---

## International formatting

**Component:** AutonumericInternationalFormattingExampleComponent

**Selector:** `app-autonumeric-international-formatting-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  ReactiveFormsModule,
  Validators,
} from '@angular/forms';
import {
  SkyAutonumericModule,
  SkyAutonumericOptions,
} from '@skyux/autonumeric';
import { SkyInputBoxModule } from '@skyux/forms';

/**
 * @title International formatting
 */
@Component({
  selector: 'app-autonumeric-international-formatting-example',
  templateUrl: './example.component.html',
  imports: [ReactiveFormsModule, SkyAutonumericModule, SkyInputBoxModule],
})
export class AutonumericInternationalFormattingExampleComponent {
  protected autonumericOptions: SkyAutonumericOptions | undefined;

  protected formGroup: FormGroup;

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      donationAmount: new FormControl(1234.5678, [Validators.required]),
    });

    this.autonumericOptions = {
      decimalCharacter: ',',
      decimalPlaces: 4,
      digitGroupSeparator: '',
    };
  }
}

```

#### example.component.html

```html
<form [formGroup]="formGroup">
  <sky-input-box labelText="Autonumeric value">
    <input
      formControlName="donationAmount"
      type="text"
      [skyAutonumeric]="autonumericOptions"
    />
  </sky-input-box>
</form>

```

---

## Options provider

**Component:** AutonumericOptionsProviderExampleComponent

**Selector:** `app-autonumeric-options-provider-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  ReactiveFormsModule,
  Validators,
} from '@angular/forms';
import {
  SkyAutonumericModule,
  SkyAutonumericOptions,
  SkyAutonumericOptionsProvider,
} from '@skyux/autonumeric';
import { SkyInputBoxModule } from '@skyux/forms';

import { DemoAutonumericOptionsProvider } from './options-provider';

/**
 * @title Options provider
 */
@Component({
  selector: 'app-autonumeric-options-provider-example',
  templateUrl: './example.component.html',
  providers: [
    {
      provide: SkyAutonumericOptionsProvider,
      useClass: DemoAutonumericOptionsProvider,
    },
  ],
  imports: [ReactiveFormsModule, SkyAutonumericModule, SkyInputBoxModule],
})
export class AutonumericOptionsProviderExampleComponent {
  protected donationOptions: SkyAutonumericOptions = {};

  protected formGroup: FormGroup;

  protected pledgeOptions: SkyAutonumericOptions = {
    decimalPlaces: 0,
  };

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      donationAmount: new FormControl(1234.5678, [Validators.required]),
      pledgeAmount: new FormControl(2345.6789, [Validators.required]),
    });
  }
}

```

#### options-provider.ts

```typescript
import { Injectable } from '@angular/core';
import {
  SkyAutonumericOptions,
  SkyAutonumericOptionsProvider,
} from '@skyux/autonumeric';

@Injectable()
export class DemoAutonumericOptionsProvider extends SkyAutonumericOptionsProvider {
  constructor() {
    super();
  }

  public override getConfig(): SkyAutonumericOptions {
    return {
      currencySymbol: ' €',
      currencySymbolPlacement: 's',
      decimalPlaces: 2,
      decimalCharacter: ',',
      digitGroupSeparator: '',
    };
  }
}

```

#### example.component.html

```html
<form [formGroup]="formGroup">
  <sky-input-box labelText="Donation amount" stacked="true">
    <input
      formControlName="donationAmount"
      type="text"
      [skyAutonumeric]="donationOptions"
    />
  </sky-input-box>
  <sky-input-box labelText="Pledge amount">
    <input
      formControlName="pledgeAmount"
      type="text"
      [skyAutonumeric]="pledgeOptions"
    />
  </sky-input-box>
</form>

```

---

## Predefined options

**Component:** AutonumericPresetExampleComponent

**Selector:** `app-autonumeric-preset-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  ReactiveFormsModule,
  Validators,
} from '@angular/forms';
import {
  SkyAutonumericModule,
  SkyAutonumericOptions,
} from '@skyux/autonumeric';
import { SkyInputBoxModule } from '@skyux/forms';

/**
 * @title Predefined options
 */
@Component({
  selector: 'app-autonumeric-preset-example',
  templateUrl: './example.component.html',
  imports: [ReactiveFormsModule, SkyAutonumericModule, SkyInputBoxModule],
})
export class AutonumericPresetExampleComponent {
  protected autonumericOptions: SkyAutonumericOptions = 'Chinese';

  protected formGroup: FormGroup;

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      donationAmount: new FormControl(1234.5678, [Validators.required]),
    });
  }
}

```

#### example.component.html

```html
<form [formGroup]="formGroup">
  <sky-input-box labelText="Donation amount">
    <input
      formControlName="donationAmount"
      type="text"
      [skyAutonumeric]="autonumericOptions"
    />
  </sky-input-box>
</form>

```

---

## Numeric pipe with basic setup

**Component:** CoreNumericBasicExampleComponent

**Selector:** `app-core-numeric-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyNumericOptions } from '@skyux/core';

import { CoreNumericBasicExampleComponent } from './example.component';

describe('Basic numeric options', () => {
  async function setupTest(options?: {
    defaultValue?: number;
    configuredValue?: number;
    config?: SkyNumericOptions;
  }): Promise<{ fixture: ComponentFixture<CoreNumericBasicExampleComponent> }> {
    const fixture = TestBed.createComponent(CoreNumericBasicExampleComponent);

    if (options?.defaultValue !== undefined) {
      fixture.componentInstance.defaultValue = options.defaultValue;
    }

    if (options?.configuredValue !== undefined) {
      fixture.componentInstance.configuredValue = options.configuredValue;
    }

    if (options?.config !== undefined) {
      fixture.componentInstance.numericOptions = options.config;
    }

    fixture.detectChanges();
    await fixture.whenStable();

    return { fixture };
  }

  function getTextContent(
    fixture: ComponentFixture<CoreNumericBasicExampleComponent>,
    selector: string,
  ): string {
    const el = (
      fixture.nativeElement as HTMLElement
    ).querySelector<HTMLSpanElement>(selector);

    return el?.textContent?.trim() ?? '';
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [CoreNumericBasicExampleComponent],
    });
  });

  it('should show the expected number in the default format', async () => {
    const { fixture } = await setupTest({ defaultValue: 123456 });

    fixture.detectChanges();

    expect(getTextContent(fixture, '.default-value')).toEqual('123.5K');
  });

  it('should show the expected number in a specified format', async () => {
    const { fixture } = await setupTest({
      configuredValue: 5000000,
      config: { truncate: false },
    });

    expect(getTextContent(fixture, '.configured-value')).toEqual('5,000,000');
  });
});

```

#### example.component.ts

```typescript
import { Component, Input } from '@angular/core';
import { SkyNumericModule, SkyNumericOptions } from '@skyux/core';
import { SkyDescriptionListModule } from '@skyux/layout';

/**
 * @title Numeric pipe with basic setup
 */
@Component({
  selector: 'app-core-numeric-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyDescriptionListModule, SkyNumericModule],
})
export class CoreNumericBasicExampleComponent {
  @Input()
  public defaultValue = 1000000;

  @Input()
  public configuredValue = 1234567;

  @Input()
  public numericOptions: SkyNumericOptions = {
    digits: 3,
    format: 'currency',
    iso: 'JPY',
  };
}

```

#### example.component.html

```html
<sky-description-list mode="vertical">
  <sky-description-list-content>
    <sky-description-list-term> Default setup </sky-description-list-term>
    <sky-description-list-description>
      <span class="default-value">
        {{ defaultValue | skyNumeric }}
      </span>
    </sky-description-list-description>
  </sky-description-list-content>
  <sky-description-list-content>
    <sky-description-list-term> With options </sky-description-list-term>
    <sky-description-list-description>
      <span class="configured-value">
        {{ configuredValue | skyNumeric: numericOptions }}
      </span>
    </sky-description-list-description>
  </sky-description-list-content>
</sky-description-list>

```

---