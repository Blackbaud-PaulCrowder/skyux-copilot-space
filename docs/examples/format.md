---
component: 'format'
type: 'code-examples'
description: 'Code examples for the format component.'
---

# Format Code Examples

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

## Format service basic usage

**Component:** LayoutFormatExampleComponent

**Selector:** `app-layout-format-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyFormatModule } from '@skyux/layout';

/**
 * @title Format service basic usage
 */
@Component({
  selector: 'app-layout-format-example',
  templateUrl: './example.component.html',
  styleUrls: ['./example.component.scss'],
  imports: [SkyFormatModule],
})
export class LayoutFormatExampleComponent {}

```

#### example.component.html

```html
<sky-format
  text="{0} is an important number. {1} is important, too, but not as important as {0}."
  [args]="[value1, value2]"
/>

<ng-template #value1>
  <strong class="number-large">39,210</strong>
</ng-template>

<ng-template #value2>
  <strong class="number-medium">78</strong>
</ng-template>

```

#### example.component.scss

```css
.number-large {
  font-size: 18px;
}

.number-medium {
  font-size: 16px;
}

```

---