# Development

                  Skip to Main Content

 Text highlight
==============

The text highlight directive highlights text all matching text within DOM elements.

 Installation
-------------

NPM package

`@skyux/indicators`[View in NPM](https://www.npmjs.com/package/@skyux/indicators) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/indicators/src/lib/modules/text-highlight/text-highlight.module.ts#L11) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/indicators`Copy None found.

 SkyTextHighlightModule
-----------------------

Type: Module

`import { SkyTextHighlightModule } from '@skyux/indicators';`

 SkyTextHighlightDirective
--------------------------

Type: Directive

Selector: `[skyHighlight]`

Highlights all matching text within the current DOM element.

### Inputs

#### `skyHighlight: string | string[] | undefined`

The text to highlight.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyTextHighlightHarness
------------------------

Type: Class

`import { SkyTextHighlightHarness } from '@skyux/indicators/testing';`

Harness to interact with a text highlight directive in tests.

### Methods

#### `getHighlights(): Promise<TestElement[]>`

Gets an array of all instances of highlighted text.

#### Returns

`Promise<TestElement[]>`

#### `SkyTextHighlightHarness.with(filters: SkyTextHighlightHarnessFilters): HarnessPredicate<SkyTextHighlightHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTextHighlightHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTextHighlightHarnessFilters`

#### Returns

`HarnessPredicate<SkyTextHighlightHarness>`

 SkyTextHighlightHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyTextHighlightHarness](/skyux/components/text-highlight?docs-active-tab=development#class_sky-text-highlight-harness.md) instances.

    interface SkyTextHighlightHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Examples

                    Skip to Main Content

 Text highlight
==============

The text highlight directive highlights text all matching text within DOM elements.Installation
-------------

NPM package

`@skyux/indicators`[View in NPM](https://www.npmjs.com/package/@skyux/indicators) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/indicators/src/lib/modules/text-highlight/text-highlight.module.ts#L11) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/indicators`Copy None found.

 SkyTextHighlightModule
-----------------------

Type: Module

`import { SkyTextHighlightModule } from '@skyux/indicators';`

 SkyTextHighlightDirective
--------------------------

Type: Directive

Selector: `[skyHighlight]`

Highlights all matching text within the current DOM element.

### Inputs

#### `skyHighlight: string | string[] | undefined`

The text to highlight.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyTextHighlightHarness
------------------------

Type: Class

`import { SkyTextHighlightHarness } from '@skyux/indicators/testing';`

Harness to interact with a text highlight directive in tests.

### Methods

#### `getHighlights(): Promise<TestElement[]>`

Gets an array of all instances of highlighted text.

#### Returns

`Promise<TestElement[]>`

#### `SkyTextHighlightHarness.with(filters: SkyTextHighlightHarnessFilters): HarnessPredicate<SkyTextHighlightHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTextHighlightHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTextHighlightHarnessFilters`

#### Returns

`HarnessPredicate<SkyTextHighlightHarness>`

 SkyTextHighlightHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyTextHighlightHarness](/skyux/components/text-highlight?docs-active-tab=examples#class_sky-text-highlight-harness.md) instances.

    interface SkyTextHighlightHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

### Text highlight with basic setup

Edit in StackBlitz

Text to highlight

Display additional content

The text that you enter is highlighted here.

Show code

Copy

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
Copy

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

Copy

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

# Testing

                  Skip to Main Content

 Text highlight
==============

The text highlight directive highlights text all matching text within DOM elements.

 Installation
-------------

NPM package

`@skyux/indicators`[View in NPM](https://www.npmjs.com/package/@skyux/indicators) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/indicators/src/lib/modules/text-highlight/text-highlight.module.ts#L11) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/indicators`Copy None found.

 SkyTextHighlightModule
-----------------------

Type: Module

`import { SkyTextHighlightModule } from '@skyux/indicators';`

 SkyTextHighlightDirective
--------------------------

Type: Directive

Selector: `[skyHighlight]`

Highlights all matching text within the current DOM element.

### Inputs

#### `skyHighlight: string | string[] | undefined`

The text to highlight.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyTextHighlightHarness
------------------------

Type: Class

`import { SkyTextHighlightHarness } from '@skyux/indicators/testing';`

Harness to interact with a text highlight directive in tests.

### Methods

#### `getHighlights(): Promise<TestElement[]>`

Gets an array of all instances of highlighted text.

#### Returns

`Promise<TestElement[]>`

#### `SkyTextHighlightHarness.with(filters: SkyTextHighlightHarnessFilters): HarnessPredicate<SkyTextHighlightHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyTextHighlightHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyTextHighlightHarnessFilters`

#### Returns

`HarnessPredicate<SkyTextHighlightHarness>`

 SkyTextHighlightHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyTextHighlightHarness](/skyux/components/text-highlight?docs-active-tab=testing#class_sky-text-highlight-harness.md) instances.

    interface SkyTextHighlightHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.