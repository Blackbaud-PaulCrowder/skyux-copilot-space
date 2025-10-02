---
component: 'text-expand-repeater'
type: 'code-examples'
description: 'Code examples for the text-expand-repeater component.'
---

# Text Expand Repeater Code Examples

## Text expand repeater with basic setup

**Component:** LayoutTextExpandRepeaterExampleComponent

**Selector:** `app-layout-text-expand-repeater-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyTextExpandRepeaterHarness } from '@skyux/layout/testing';

import { LayoutTextExpandRepeaterExampleComponent } from './example.component';

describe('Text expand inline example', () => {
  async function setupTest(
    options: {
      dataSkyId?: string;
    } = {},
  ): Promise<{
    textExpandRepeaterHarness: SkyTextExpandRepeaterHarness;
  }> {
    await TestBed.configureTestingModule({
      imports: [LayoutTextExpandRepeaterExampleComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      LayoutTextExpandRepeaterExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const textExpandRepeaterHarness: SkyTextExpandRepeaterHarness =
      options.dataSkyId
        ? await loader.getHarness(
            SkyTextExpandRepeaterHarness.with({
              dataSkyId: options.dataSkyId,
            }),
          )
        : await loader.getHarness(SkyTextExpandRepeaterHarness);

    return { textExpandRepeaterHarness };
  }

  it('should set up the text expand repeater', async () => {
    const { textExpandRepeaterHarness } = await setupTest();

    await textExpandRepeaterHarness.clickExpandCollapseButton();

    await expectAsync(textExpandRepeaterHarness.isExpanded()).toBeResolvedTo(
      true,
    );

    const items = await textExpandRepeaterHarness.getItems();

    await expectAsync((await items[2].host()).text()).toBeResolvedTo(
      'Repeater item 3',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyTextExpandRepeaterModule } from '@skyux/layout';

/**
 * @title Text expand repeater with basic setup
 */
@Component({
  selector: 'app-layout-text-expand-repeater-example',
  templateUrl: './example.component.html',
  imports: [SkyTextExpandRepeaterModule],
})
export class LayoutTextExpandRepeaterExampleComponent {
  protected repeaterData: string[] = [
    'Repeater item 1',
    'Repeater item 2',
    'Repeater item 3',
    'Repeater item 4',
    'Repeater item 5',
  ];
}

```

#### example.component.html

```html
<sky-text-expand-repeater [data]="repeaterData" [maxItems]="2" />

```

---