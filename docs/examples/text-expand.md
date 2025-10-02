---
component: 'text-expand'
type: 'code-examples'
description: 'Code examples for the text-expand component.'
---

# Text Expand Code Examples

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

## Text expand with inline text

**Component:** LayoutTextExpandInlineExampleComponent

**Selector:** `app-layout-text-expand-inline-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyTextExpandHarness } from '@skyux/layout/testing';

import { LayoutTextExpandInlineExampleComponent } from './example.component';

describe('Text expand inline example', () => {
  async function setupTest(
    options: {
      dataSkyId?: string;
    } = {},
  ): Promise<{
    textExpandHarness: SkyTextExpandHarness;
  }> {
    await TestBed.configureTestingModule({
      imports: [LayoutTextExpandInlineExampleComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      LayoutTextExpandInlineExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const textExpandHarness: SkyTextExpandHarness = options.dataSkyId
      ? await loader.getHarness(
          SkyTextExpandHarness.with({
            dataSkyId: options.dataSkyId,
          }),
        )
      : await loader.getHarness(SkyTextExpandHarness);

    return { textExpandHarness };
  }

  it('should set up the text expand', async () => {
    const { textExpandHarness } = await setupTest();

    await expectAsync(textExpandHarness.textExpandsToModal()).toBeResolvedTo(
      false,
    );

    await textExpandHarness.clickExpandCollapseButton();

    await expectAsync(textExpandHarness.getText()).toBeResolvedTo(
      'The text expand component truncates long blocks of text with an ellipsis and a link to expand the text. Users select the link to expand the full text inline unless it exceeds limits on text characters or newline characters. If the text exceeds those limits, then it expands in a modal view instead. The component does not truncate text that is shorter than a specified threshold, and by default, it removes newline characters from truncated text.',
    );
    await expectAsync(textExpandHarness.isExpanded()).toBeResolvedTo(true);

    await textExpandHarness.clickExpandCollapseButton();

    await expectAsync(textExpandHarness.getText()).toBeResolvedTo(
      'The text expand component truncates long blocks of text with an ellipsis and a link to expand the text. Users select the link to expand the full text inline unless it exceeds limits on text characters',
    );
    await expectAsync(textExpandHarness.isExpanded()).toBeResolvedTo(false);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyTextExpandModule } from '@skyux/layout';

/**
 * @title Text expand with inline text
 */
@Component({
  selector: 'app-layout-text-expand-inline-example',
  templateUrl: './example.component.html',
  imports: [SkyTextExpandModule],
})
export class LayoutTextExpandInlineExampleComponent {
  protected longText =
    'The text expand component truncates long blocks of text with an ellipsis and a link to expand the text. Users select the link to expand the full text inline unless it exceeds limits on text characters or newline characters. If the text exceeds those limits, then it expands in a modal view instead. The component does not truncate text that is shorter than a specified threshold, and by default, it removes newline characters from truncated text.';
}

```

#### example.component.html

```html
<sky-text-expand [text]="longText" />

```

---

## Text expand with a modal

**Component:** LayoutTextExpandModalExampleComponent

**Selector:** `app-layout-text-expand-modal-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyTextExpandHarness } from '@skyux/layout/testing';

import { LayoutTextExpandModalExampleComponent } from './example.component';

describe('Text expand modal example', () => {
  async function setupTest(
    options: {
      dataSkyId?: string;
    } = {},
  ): Promise<{
    textExpandHarness: SkyTextExpandHarness;
  }> {
    await TestBed.configureTestingModule({
      imports: [LayoutTextExpandModalExampleComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      LayoutTextExpandModalExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const textExpandHarness: SkyTextExpandHarness = options.dataSkyId
      ? await loader.getHarness(
          SkyTextExpandHarness.with({
            dataSkyId: options.dataSkyId,
          }),
        )
      : await loader.getHarness(SkyTextExpandHarness);

    return { textExpandHarness };
  }

  it('should open and close the text expand modal', async () => {
    const { textExpandHarness } = await setupTest();

    await expectAsync(textExpandHarness.textExpandsToModal()).toBeResolvedTo(
      true,
    );
    await expectAsync(textExpandHarness.isExpanded()).toBeResolvedTo(false);

    await textExpandHarness.clickExpandCollapseButton();
    const modal = await textExpandHarness.getExpandedViewModal();

    await expectAsync(modal.getText()).toBeResolvedTo(
      'The text expand component truncates long blocks of text with an ellipsis and a link to expand the text. Users select the link to expand the full text inline unless it exceeds limits on text characters or newline characters. If the text exceeds those limits, then it expands in a modal view instead. The component does not truncate text that is shorter than a specified threshold, and by default, it removes newline characters from truncated text.',
    );
    await expectAsync(modal.getExpandModalTitle()).toBeResolvedTo(
      'Expanded view',
    );
    await expectAsync(textExpandHarness.isExpanded()).toBeResolvedTo(true);

    await modal.clickCloseButton();

    await expectAsync(
      textExpandHarness.getExpandedViewModal(),
    ).toBeRejectedWithError('Could not find text expand modal.');
    await expectAsync(textExpandHarness.isExpanded()).toBeResolvedTo(false);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyTextExpandModule } from '@skyux/layout';

/**
 * @title Text expand with a modal
 */
@Component({
  selector: 'app-layout-text-expand-modal-example',
  templateUrl: './example.component.html',
  imports: [SkyTextExpandModule],
})
export class LayoutTextExpandModalExampleComponent {
  protected longText =
    'The text expand component truncates long blocks of text with an ellipsis and a link to expand the text. Users select the link to expand the full text inline unless it exceeds limits on text characters or newline characters. If the text exceeds those limits, then it expands in a modal view instead. The component does not truncate text that is shorter than a specified threshold, and by default, it removes newline characters from truncated text.';
}

```

#### example.component.html

```html
<sky-text-expand [text]="longText" [maxExpandedLength]="100" />

```

---

## Text expand with new lines

**Component:** LayoutTextExpandNewlineExampleComponent

**Selector:** `app-layout-text-expand-newline-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyTextExpandModule } from '@skyux/layout';

/**
 * @title Text expand with new lines
 */
@Component({
  selector: 'app-layout-text-expand-newline-example',
  templateUrl: './example.component.html',
  imports: [SkyTextExpandModule],
})
export class LayoutTextExpandNewlineExampleComponent {
  protected newlinesText =
    'The text expand component truncates long blocks of text with an ellipsis and a link to expand the text.\nUsers select the link to expand the full text inline unless it exceeds limits on text characters or newline characters.\nIf the text exceeds those limits, then it expands in a modal view instead.\nThe component does not truncate text that is shorter than a specified threshold, and by default, it removes newline characters from truncated text.';
}

```

#### example.component.html

```html
<sky-text-expand [text]="newlinesText" [truncateNewlines]="false" />

```

---