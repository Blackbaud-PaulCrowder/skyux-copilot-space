# Development

                 Skip to Main Content

 Text expand
===========

The text expand component truncates long blocks of text with an ellipsis and a link to expand the text.

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/text-expand/text-expand.module.ts#L9) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyTextExpandModule
--------------------

Type: Module

`import { SkyTextExpandModule } from '@skyux/layout';`

 SkyTextExpandComponent
-----------------------

Type: Component

Selector: `sky-text-expand`

### Inputs

#### `expandModalTitle: string | undefined`

The title to display when the component expands the full text in a modal.

Default: `"Expanded view"`

#### `maxExpandedLength: number`

The maximum number of text characters to display inline when users select the link to expand the full text. If the text exceeds this limit, then the component expands the full text in a modal instead.

Default: `600`

#### `maxExpandedNewlines: number`

The maximum number of newline characters to display inline when users select the link to expand the full text. If the text exceeds this limit, then the component expands the full text in a modal view instead.

Default: `2`

#### `maxLength: number`

The number of text characters to display before truncating the text. To avoid truncating text in the middle of a word, the component looks for a space in the 10 characters before the last character.

Default: `200`

#### `text: string`

The text to truncate.

#### `truncateNewlines: boolean`

Whether to replace newline characters in truncated text with spaces.

Default: `true`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyTextExpandHarness
---------------------

Type: Class

`import { SkyTextExpandHarness } from '@skyux/layout/testing';`

Harness for interacting with a text expand component in tests.

### Methods

#### `clickExpandCollapseButton(): Promise<void>`

Clicks the button element that expands or collapses text.

#### Returns

`Promise<void>`

#### `getExpandedViewModal(): Promise<SkyTextExpandModalHarness>`

Gets the harness to interact with the modal expanded view.

#### Returns

`Promise<SkyTextExpandModalHarness>`

#### `getText(): Promise<string>`

Gets the text content of the text expand.

#### Returns

`Promise<string>`

#### `isExpanded(): Promise<boolean>`

Whether the text is expanded.

#### Returns

`Promise<boolean>`

#### `textExpandsToModal(): Promise<boolean>`

Whether the text will expand to a modal.

#### Returns

`Promise<boolean>`

#### `SkyTextExpandHarness.with(filters: SkyTextExpandHarnessFilters): HarnessPredicate<SkyTextExpandHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTextExpandHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTextExpandHarnessFilters`

#### Returns

`HarnessPredicate<SkyTextExpandHarness>`

 SkyTextExpandHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTextExpandHarness` instances.

    interface SkyTextExpandHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyTextExpandModalHarness
--------------------------

Type: Class

`import { SkyTextExpandModalHarness } from '@skyux/layout/testing';`

Harness for interacting with a text expand modal component in tests.

### Methods

#### `clickCloseButton(): Promise<void>`

Clicks the modal close button.

#### Returns

`Promise<void>`

#### `getExpandModalTitle(): Promise<string>`

Gets the modal title.

#### Returns

`Promise<string>`

#### `getText(): Promise<string>`

Gets the expanded text in the modal.

#### Returns

`Promise<string>`

# Examples

                   Skip to Main Content

 Text expand
===========

The text expand component truncates long blocks of text with an ellipsis and a link to expand the text.Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/text-expand/text-expand.module.ts#L9) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyTextExpandModule
--------------------

Type: Module

`import { SkyTextExpandModule } from '@skyux/layout';`

 SkyTextExpandComponent
-----------------------

Type: Component

Selector: `sky-text-expand`

### Inputs

#### `expandModalTitle: string | undefined`

The title to display when the component expands the full text in a modal.

Default: `"Expanded view"`

#### `maxExpandedLength: number`

The maximum number of text characters to display inline when users select the link to expand the full text. If the text exceeds this limit, then the component expands the full text in a modal instead.

Default: `600`

#### `maxExpandedNewlines: number`

The maximum number of newline characters to display inline when users select the link to expand the full text. If the text exceeds this limit, then the component expands the full text in a modal view instead.

Default: `2`

#### `maxLength: number`

The number of text characters to display before truncating the text. To avoid truncating text in the middle of a word, the component looks for a space in the 10 characters before the last character.

Default: `200`

#### `text: string`

The text to truncate.

#### `truncateNewlines: boolean`

Whether to replace newline characters in truncated text with spaces.

Default: `true`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyTextExpandHarness
---------------------

Type: Class

`import { SkyTextExpandHarness } from '@skyux/layout/testing';`

Harness for interacting with a text expand component in tests.

### Methods

#### `clickExpandCollapseButton(): Promise<void>`

Clicks the button element that expands or collapses text.

#### Returns

`Promise<void>`

#### `getExpandedViewModal(): Promise<SkyTextExpandModalHarness>`

Gets the harness to interact with the modal expanded view.

#### Returns

`Promise<SkyTextExpandModalHarness>`

#### `getText(): Promise<string>`

Gets the text content of the text expand.

#### Returns

`Promise<string>`

#### `isExpanded(): Promise<boolean>`

Whether the text is expanded.

#### Returns

`Promise<boolean>`

#### `textExpandsToModal(): Promise<boolean>`

Whether the text will expand to a modal.

#### Returns

`Promise<boolean>`

#### `SkyTextExpandHarness.with(filters: SkyTextExpandHarnessFilters): HarnessPredicate<SkyTextExpandHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTextExpandHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTextExpandHarnessFilters`

#### Returns

`HarnessPredicate<SkyTextExpandHarness>`

 SkyTextExpandHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTextExpandHarness` instances.

    interface SkyTextExpandHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyTextExpandModalHarness
--------------------------

Type: Class

`import { SkyTextExpandModalHarness } from '@skyux/layout/testing';`

Harness for interacting with a text expand modal component in tests.

### Methods

#### `clickCloseButton(): Promise<void>`

Clicks the modal close button.

#### Returns

`Promise<void>`

#### `getExpandModalTitle(): Promise<string>`

Gets the modal title.

#### Returns

`Promise<string>`

#### `getText(): Promise<string>`

Gets the expanded text in the modal.

#### Returns

`Promise<string>`

### Text expand with inline text

Edit in StackBlitz

The text expand component truncates long blocks of text with an ellipsis and a link to expand the text. Users select the link to expand the full text inline unless it exceeds limits on text characters... See more

Show code

Copy

    <sky-text-expand [text]="longText" />
Copy

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

Copy

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
### Text expand with a modal

Edit in StackBlitz

The text expand component truncates long blocks of text with an ellipsis and a link to expand the text. Users select the link to expand the full text inline unless it exceeds limits on text characters... See more

Show code

Copy

    <sky-text-expand [text]="longText" [maxExpandedLength]="100" />
Copy

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

Copy

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
### Text expand with new lines

Edit in StackBlitz

The text expand component truncates long blocks of text with an ellipsis and a link to expand the text. Users select the link to expand the full text inline unless it exceeds limits on text characters... See more

Show code

Copy

    <sky-text-expand [text]="newlinesText" [truncateNewlines]="false" />

Copy

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

# Testing

                 Skip to Main Content

 Text expand
===========

The text expand component truncates long blocks of text with an ellipsis and a link to expand the text.

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/text-expand/text-expand.module.ts#L9) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyTextExpandModule
--------------------

Type: Module

`import { SkyTextExpandModule } from '@skyux/layout';`

 SkyTextExpandComponent
-----------------------

Type: Component

Selector: `sky-text-expand`

### Inputs

#### `expandModalTitle: string | undefined`

The title to display when the component expands the full text in a modal.

Default: `"Expanded view"`

#### `maxExpandedLength: number`

The maximum number of text characters to display inline when users select the link to expand the full text. If the text exceeds this limit, then the component expands the full text in a modal instead.

Default: `600`

#### `maxExpandedNewlines: number`

The maximum number of newline characters to display inline when users select the link to expand the full text. If the text exceeds this limit, then the component expands the full text in a modal view instead.

Default: `2`

#### `maxLength: number`

The number of text characters to display before truncating the text. To avoid truncating text in the middle of a word, the component looks for a space in the 10 characters before the last character.

Default: `200`

#### `text: string`

The text to truncate.

#### `truncateNewlines: boolean`

Whether to replace newline characters in truncated text with spaces.

Default: `true`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyTextExpandHarness
---------------------

Type: Class

`import { SkyTextExpandHarness } from '@skyux/layout/testing';`

Harness for interacting with a text expand component in tests.

### Methods

#### `clickExpandCollapseButton(): Promise<void>`

Clicks the button element that expands or collapses text.

#### Returns

`Promise<void>`

#### `getExpandedViewModal(): Promise<SkyTextExpandModalHarness>`

Gets the harness to interact with the modal expanded view.

#### Returns

`Promise<SkyTextExpandModalHarness>`

#### `getText(): Promise<string>`

Gets the text content of the text expand.

#### Returns

`Promise<string>`

#### `isExpanded(): Promise<boolean>`

Whether the text is expanded.

#### Returns

`Promise<boolean>`

#### `textExpandsToModal(): Promise<boolean>`

Whether the text will expand to a modal.

#### Returns

`Promise<boolean>`

#### `SkyTextExpandHarness.with(filters: SkyTextExpandHarnessFilters): HarnessPredicate<SkyTextExpandHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTextExpandHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTextExpandHarnessFilters`

#### Returns

`HarnessPredicate<SkyTextExpandHarness>`

 SkyTextExpandHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyTextExpandHarness` instances.

    interface SkyTextExpandHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyTextExpandModalHarness
--------------------------

Type: Class

`import { SkyTextExpandModalHarness } from '@skyux/layout/testing';`

Harness for interacting with a text expand modal component in tests.

### Methods

#### `clickCloseButton(): Promise<void>`

Clicks the modal close button.

#### Returns

`Promise<void>`

#### `getExpandModalTitle(): Promise<string>`

Gets the modal title.

#### Returns

`Promise<string>`

#### `getText(): Promise<string>`

Gets the expanded text in the modal.

#### Returns

`Promise<string>`