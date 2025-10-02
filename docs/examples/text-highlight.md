---
component: 'text-highlight'
type: 'code-examples'
description: 'Code examples for the text-highlight component.'
---

# Text Highlight Code Examples

## Text highlight with basic setup

**Component:** IndicatorsTextHighlightBasicExampleComponent

**Selector:** `app-indicators-text-highlight-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyCheckboxHarness, SkyInputBoxHarness } from '@skyux/forms/testing';
import { SkyTextHighlightHarness } from '@skyux/indicators/testing';

import { IndicatorsTextHighlightBasicExampleComponent } from './example.component';

describe('Text highlight example', () => {
  async function setupTest(options?: { dataSkyId: string }): Promise<{
    textHighlightHarness: SkyTextHighlightHarness;
    fixture: ComponentFixture<IndicatorsTextHighlightBasicExampleComponent>;
    loader: HarnessLoader;
  }> {
    await TestBed.configureTestingModule({
      imports: [IndicatorsTextHighlightBasicExampleComponent],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      IndicatorsTextHighlightBasicExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const textHighlightHarness = options?.dataSkyId
      ? await loader.getHarness(
          SkyTextHighlightHarness.with({ dataSkyId: options.dataSkyId }),
        )
      : await loader.getHarness(SkyTextHighlightHarness);

    return { textHighlightHarness, fixture, loader };
  }

  it('should set up the component', async () => {
    const { textHighlightHarness, fixture, loader } = await setupTest();

    const inputEl = await (
      await loader.getHarness(SkyInputBoxHarness)
    ).querySelector('input');

    const checkboxHarness = await loader.getHarness(SkyCheckboxHarness);

    await inputEl?.sendKeys('text');
    await inputEl?.blur();
    fixture.detectChanges();
    await fixture.whenStable();

    let highlights = await textHighlightHarness.getHighlights();
    expect(highlights.length).toBe(1);

    await checkboxHarness.check();
    fixture.detectChanges();
    await fixture.whenStable();

    await inputEl?.clear();
    await inputEl?.sendKeys('is');
    await inputEl?.blur();
    fixture.detectChanges();
    await fixture.whenStable();

    highlights = await textHighlightHarness.getHighlights();
    expect(highlights.length).toBe(3);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { FormsModule } from '@angular/forms';
import { SkyCheckboxModule, SkyInputBoxModule } from '@skyux/forms';
import { SkyTextHighlightModule } from '@skyux/indicators';

/**
 * @title Text highlight with basic setup
 */
@Component({
  selector: 'app-indicators-text-highlight-basic-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    SkyCheckboxModule,
    SkyInputBoxModule,
    SkyTextHighlightModule,
  ],
})
export class IndicatorsTextHighlightBasicExampleComponent {
  protected searchTerm = '';
  protected showAdditionalContent = false;
}

```

#### example.component.html

```html
<div class="sky-margin-stacked-lg">
  <sky-input-box labelText="Text to highlight" [stacked]="true">
    <input type="text" [(ngModel)]="searchTerm" />
  </sky-input-box>
</div>

<div class="sky-margin-stacked-lg">
  <sky-checkbox
    labelText="Display additional content"
    [(ngModel)]="showAdditionalContent"
  />
</div>

<div [skyHighlight]="searchTerm">
  The text that you enter is highlighted here.
  @if (showAdditionalContent) {
    <div>This additional content is highlighted too!</div>
  }
</div>

```

---