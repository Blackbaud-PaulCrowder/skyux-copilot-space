---
component: 'tokens'
type: 'code-examples'
description: 'Code examples for the tokens component.'
---

# Tokens Code Examples

## Tokens with basic setup

**Component:** IndicatorsTokensBasicExampleComponent

**Selector:** `app-indicators-tokens-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyToken } from '@skyux/indicators';
import { SkyTokensHarness } from '@skyux/indicators/testing';

import { IndicatorsTokensBasicExampleComponent } from './example.component';

describe('Tokens basic example', () => {
  async function setupTest(): Promise<{
    tokensHarness: SkyTokensHarness;
    fixture: ComponentFixture<IndicatorsTokensBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      IndicatorsTokensBasicExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const tokensHarness = await loader.getHarness(
      SkyTokensHarness.with({ dataSkyId: 'color-tokens' }),
    );

    return { tokensHarness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [NoopAnimationsModule, IndicatorsTokensBasicExampleComponent],
    });
  });

  it('should display the expected initial tokens', async () => {
    const { tokensHarness } = await setupTest();

    await expectAsync(tokensHarness.getTokensText()).toBeResolvedTo([
      'Red',
      'Black',
      'Blue',
      'Brown',
      'Green',
      'Orange',
      'Pink',
      'Purple',
      'Turquoise',
      'White',
      'Yellow',
    ]);
  });

  it('should update the tokens array when one is dismissed', async () => {
    const { tokensHarness, fixture } = await setupTest();

    const blueToken: SkyToken<{ name: string }> = {
      value: { name: 'Blue' },
    };

    expect(fixture.componentInstance.colors).toContain(blueToken);

    await tokensHarness.dismissTokens({
      text: 'Blue',
    });

    expect(fixture.componentInstance.colors).not.toContain(blueToken);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyToken, SkyTokensModule } from '@skyux/indicators';

/**
 * @title Tokens with basic setup
 */
@Component({
  selector: 'app-indicators-tokens-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyTokensModule],
})
export class IndicatorsTokensBasicExampleComponent {
  public colors: SkyToken<{
    name: string;
  }>[] = [
    { value: { name: 'Red' } },
    { value: { name: 'Black' } },
    { value: { name: 'Blue' } },
    { value: { name: 'Brown' } },
    { value: { name: 'Green' } },
    { value: { name: 'Orange' } },
    { value: { name: 'Pink' } },
    { value: { name: 'Purple' } },
    { value: { name: 'Turquoise' } },
    { value: { name: 'White' } },
    { value: { name: 'Yellow' } },
  ];
}

```

#### example.component.html

```html
<sky-tokens data-sky-id="color-tokens" [(tokens)]="colors" />

```

---

## IndicatorsTokensCustomExampleComponent

**Selector:** `app-indicators-tokens-custom-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyTokensHarness } from '@skyux/indicators/testing';

import { IndicatorsTokensCustomExampleComponent } from './example.component';

describe('Tokens basic example', () => {
  let initialTokenLabels: string[];

  async function setupTest(): Promise<{
    tokensHarness: SkyTokensHarness;
    fixture: ComponentFixture<IndicatorsTokensCustomExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      IndicatorsTokensCustomExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const tokensHarness = await loader.getHarness(
      SkyTokensHarness.with({ dataSkyId: 'example-tokens' }),
    );

    return { tokensHarness, fixture };
  }

  function clickButton(
    fixture: ComponentFixture<IndicatorsTokensCustomExampleComponent>,
    buttonName: 'change' | 'destroy' | 'focus-last' | 'reset',
  ): void {
    const btn = (
      fixture.nativeElement as HTMLElement
    ).querySelector<HTMLButtonElement>(`.tokens-example-${buttonName}-btn`);

    btn?.click();
  }

  beforeEach(() => {
    initialTokenLabels = [
      'Canada',
      'Older than 55',
      'Employed',
      'Added before 2018',
    ];

    TestBed.configureTestingModule({
      imports: [NoopAnimationsModule, IndicatorsTokensCustomExampleComponent],
    });
  });

  it('should display the expected initial tokens', async () => {
    const { tokensHarness } = await setupTest();

    await expectAsync(tokensHarness.getTokensText()).toBeResolvedTo(
      initialTokenLabels,
    );
  });

  it('should display the selected token label when the user selects a token', async () => {
    const { tokensHarness, fixture } = await setupTest();

    const employedToken = (await tokensHarness.getTokens())[2];
    await employedToken.select();

    expect(
      (fixture.nativeElement as HTMLElement).querySelector(
        '.tokens-example-selected',
      )?.textContent,
    ).toEqual('Employed');
  });

  it('should change tokens when the user clicks the "Change tokens" button', async () => {
    const { tokensHarness, fixture } = await setupTest();

    clickButton(fixture, 'change');

    await expectAsync(tokensHarness.getTokensText()).toBeResolvedTo([
      'Paid',
      'Pending',
      'Past due',
    ]);
  });

  it('should reset tokens when the user clicks the "Reset tokens" button', async () => {
    const { tokensHarness, fixture } = await setupTest();

    clickButton(fixture, 'change');

    await expectAsync(tokensHarness.getTokensText()).not.toBeResolvedTo(
      initialTokenLabels,
    );

    clickButton(fixture, 'reset');

    await expectAsync(tokensHarness.getTokensText()).toBeResolvedTo(
      initialTokenLabels,
    );
  });

  it('should destroy tokens when the user clicks the "Destroy tokens" button', async () => {
    const { tokensHarness, fixture } = await setupTest();

    clickButton(fixture, 'destroy');

    await expectAsync(tokensHarness.getTokens()).toBeResolvedTo([]);
  });

  it('should focus the last token when the user clicks the "Focus last token" button', async () => {
    const { tokensHarness, fixture } = await setupTest();

    const tokens = await tokensHarness.getTokens();
    const lastToken = tokens[tokens.length - 1];

    await expectAsync(lastToken.isFocused()).toBeResolvedTo(false);

    clickButton(fixture, 'focus-last');

    await expectAsync(lastToken.isFocused()).toBeResolvedTo(true);
  });
});

```

#### example.component.ts

```typescript
import { Component, OnDestroy } from '@angular/core';
import {
  SkyToken,
  SkyTokenSelectedEventArgs,
  SkyTokensMessage,
  SkyTokensMessageType,
  SkyTokensModule,
} from '@skyux/indicators';

import { Subject } from 'rxjs';

interface TokenItem {
  label: string;
}

/**
 * Tokens with programmatic interactions
 */
@Component({
  selector: 'app-indicators-tokens-custom-example',
  templateUrl: './example.component.html',
  imports: [SkyTokensModule],
})
export class IndicatorsTokensCustomExampleComponent implements OnDestroy {
  protected myTokens: SkyToken<TokenItem>[] | undefined;
  protected tokensController = new Subject<SkyTokensMessage>();
  protected selectedToken: string | undefined = '';

  #defaultItems: TokenItem[] = [
    { label: 'Canada' },
    { label: 'Older than 55' },
    { label: 'Employed' },
    { label: 'Added before 2018' },
  ];

  constructor() {
    this.myTokens = this.#getTokens(this.#defaultItems);
  }

  public ngOnDestroy(): void {
    this.tokensController.complete();
  }

  protected resetTokens(): void {
    this.createTokens();
  }

  protected changeTokens(): void {
    this.myTokens = this.#getTokens([
      { label: 'Paid' },
      { label: 'Pending' },
      { label: 'Past due' },
    ]);
  }

  protected destroyTokens(): void {
    this.myTokens = undefined;
  }

  protected createTokens(): void {
    this.myTokens = this.#getTokens(this.#defaultItems);
  }

  protected onTokenSelected(args: SkyTokenSelectedEventArgs<TokenItem>): void {
    this.selectedToken = args.token?.value.label;
  }

  protected onFocusIndexUnderRange(): void {
    console.log('Focus index was less than zero.');
  }

  protected onFocusIndexOverRange(): void {
    console.log('Focus index was greater than the number of tokens.');
  }

  protected focusLastToken(): void {
    this.tokensController.next({
      type: SkyTokensMessageType.FocusLastToken,
    });
  }

  #getTokens(data: TokenItem[]): SkyToken<TokenItem>[] {
    return data.map((item) => {
      return {
        value: item,
      };
    });
  }
}

```

#### example.component.html

```html
<p>
  These tokens define a custom property to display their values. When users
  select a token, it emits an event.
</p>

<div class="sky-margin-stacked-xl">
  <sky-tokens
    data-sky-id="example-tokens"
    displayWith="label"
    [messageStream]="tokensController"
    [(tokens)]="myTokens"
    (focusIndexOverRange)="onFocusIndexOverRange()"
    (focusIndexUnderRange)="onFocusIndexUnderRange()"
    (tokenSelected)="onTokenSelected($event)"
  >
    (You may also include content inside the tokens component.)
  </sky-tokens>
</div>

<div class="sky-margin-stacked-xl">
  <button
    class="sky-btn sky-btn-default sky-margin-inline-sm tokens-example-change-btn"
    type="button"
    (click)="changeTokens()"
  >
    Change tokens
  </button>

  <button
    class="sky-btn sky-btn-default sky-margin-inline-sm tokens-example-reset-btn"
    type="button"
    (click)="resetTokens()"
  >
    Reset tokens
  </button>

  <button
    class="sky-btn sky-btn-default sky-margin-inline-sm tokens-example-destroy-btn"
    type="button"
    (click)="destroyTokens()"
  >
    Destroy tokens
  </button>

  <button
    class="sky-btn sky-btn-default sky-margin-inline-sm tokens-example-focus-last-btn"
    type="button"
    (click)="focusLastToken()"
  >
    Focus last token
  </button>
</div>

<div>
  Selected token:
  <span class="tokens-example-selected">{{ selectedToken }}</span>
</div>

```

---