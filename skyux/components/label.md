# Design

                 Skip to Main Content

 Label
=====

Labels provide compact, eye-catching design elements to draw attention to time-sensitive status information that users need to address. Statuses indicate a state or condition within one of four categories: info, success, warning, and danger.

 Usage
------

### Use when

Use labels when statuses are crucial to user tasks. If not, use regular text.

 Options
--------

### Label type

Label type

When to use

Example

`danger`

Use the danger label to indicate error states on records.

Error: Expired

`warning`

Use the warning label to indicate records in states that could have minor consequences if not acted on or avoided.

Warning: Overdue

`success`

Use the success label to indicate records in a positive of successful state.

Success: Completed

`info`

Use the info alert to call attention to a state or property on a record that needs to be elevated in the information hierarchy but does not require user action.

Attention: Board member

### Description type

Use a description type with labels to include a text equivalent for the icon and color information. This ensures that people who use assistive technologies receive equivalent information.

Label type

Description type

When to use

Example

Danger

`error`

Use when the label calls attention to an error state.  
Includes the text "Error: ".

Error: No longer validError: Declined

`important-warning`

Use when the label calls attention to information about a current status or situation that users should be aware of or that could have serious consequences.  
Includes the text "Important warning: ".

Important warning: Expired

`danger`

Use when the label calls attention to information that could users help someone avoid potentially serious consequences if an action is taken.  
Includes the text "Danger: ".

Danger: Do not print

Warning

`warning`

Use when the label calls attention to information about a current status or situation that has potentially minor consequences.  
Includes the text "Warning: ".

Warning: Overdue

`caution`

Use when the label calls attention to information that could help users avoid potentially minor consequences.  
Includes the text "Caution: ".

Caution: Hold application

Success

`success`

Use when the label calls attention to information that communicates a successful result or positive state. state.  
Includes the text "Success: ".

Success: Application accepted

Info

`attention`

Use when the label calls attention to information that should be elevated in the information hierarchy but does not require user action.  
Includes the text "Attention: ".

Attention: Top earner

Any

`custom`

Set your own label when none of the other description types are the text equivalent for what the icon and color communicate in your context.  
Includes the text "\[Custom text\]: ".

 Layout
-------

### Label placement

Use labels in a summary context. For example, you can place a label in a page summary. To convey statuses inline to indicate that they are tied to specific pieces of data, use [status indicators](/skyux/components/status-indicator.md) instead.

 Related information
--------------------

### Guidelines

*   [Call out information](/skyux/design/guidelines/call-out-info.md)

 Installation
-------------

NPM package

`@skyux/indicators`[View in NPM](https://www.npmjs.com/package/@skyux/indicators) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/indicators/src/lib/modules/label/label.module.ts#L20) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/indicators`Copy None found.

 SkyLabelModule
---------------

Type: Module

`import { SkyLabelModule } from '@skyux/indicators';`

 SkyLabelComponent
------------------

Type: Component

Selector: `sky-label`

### Inputs

#### `customDescription: string | undefined`

The text to be read by screen readers for users who cannot see the indicator icon when `descriptionType` is `custom`.

#### `descriptionType: SkyIndicatorDescriptionType | undefined`

The predefined text to be read by screen readers for users who cannot see the indicator icon. This property is optional but will be required in future versions of SKY UX.

#### `labelType: SkyLabelType | undefined`

The type of label to display.

Default: `'info'`

 SkyLabelType
-------------

Type: Type alias

    type SkyLabelType = "danger" | "info" | "success" | "warning"

 SkyIndicatorDescriptionType
----------------------------

Type: Type alias

    type SkyIndicatorDescriptionType = "attention" | "caution" | "completed" | "custom" | "danger" | "error" | "important-info" | "important-warning" | "none" | "success" | "warning"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyLabelHarness
----------------

Type: Class

`import { SkyLabelHarness } from '@skyux/indicators/testing';`

Harness for interacting with a label component in tests.

### Methods

#### `getCustomDescription(): Promise<string>`

Gets the custom text used for the screen reader description of the label component icon.

#### Returns

`Promise<string>`

#### `getDescriptionType(): Promise<SkyIndicatorDescriptionType>`

Gets the `descriptionType` of the label component.

#### Returns

`Promise<SkyIndicatorDescriptionType>`

#### `getLabelText(): Promise<string>`

Gets the text of the label component.

#### Returns

`Promise<string>`

#### `getLabelType(): Promise<SkyLabelType>`

Gets the `labelType` of the label component.

#### Returns

`Promise<SkyLabelType>`

#### `SkyLabelHarness.with(filters: SkyLabelHarnessFilters): HarnessPredicate<SkyLabelHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyLookupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyLabelHarnessFilters`

#### Returns

`HarnessPredicate<SkyLabelHarness>`

 SkyLabelHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyLabelHarness` instances.

    interface SkyLabelHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Development

                 Skip to Main Content

 Label
=====

Labels provide compact, eye-catching design elements to draw attention to time-sensitive status information that users need to address. Statuses indicate a state or condition within one of four categories: info, success, warning, and danger.

 Usage
------

### Use when

Use labels when statuses are crucial to user tasks. If not, use regular text.

 Options
--------

### Label type

Label type

When to use

Example

`danger`

Use the danger label to indicate error states on records.

Error: Expired

`warning`

Use the warning label to indicate records in states that could have minor consequences if not acted on or avoided.

Warning: Overdue

`success`

Use the success label to indicate records in a positive of successful state.

Success: Completed

`info`

Use the info alert to call attention to a state or property on a record that needs to be elevated in the information hierarchy but does not require user action.

Attention: Board member

### Description type

Use a description type with labels to include a text equivalent for the icon and color information. This ensures that people who use assistive technologies receive equivalent information.

Label type

Description type

When to use

Example

Danger

`error`

Use when the label calls attention to an error state.  
Includes the text "Error: ".

Error: No longer validError: Declined

`important-warning`

Use when the label calls attention to information about a current status or situation that users should be aware of or that could have serious consequences.  
Includes the text "Important warning: ".

Important warning: Expired

`danger`

Use when the label calls attention to information that could users help someone avoid potentially serious consequences if an action is taken.  
Includes the text "Danger: ".

Danger: Do not print

Warning

`warning`

Use when the label calls attention to information about a current status or situation that has potentially minor consequences.  
Includes the text "Warning: ".

Warning: Overdue

`caution`

Use when the label calls attention to information that could help users avoid potentially minor consequences.  
Includes the text "Caution: ".

Caution: Hold application

Success

`success`

Use when the label calls attention to information that communicates a successful result or positive state. state.  
Includes the text "Success: ".

Success: Application accepted

Info

`attention`

Use when the label calls attention to information that should be elevated in the information hierarchy but does not require user action.  
Includes the text "Attention: ".

Attention: Top earner

Any

`custom`

Set your own label when none of the other description types are the text equivalent for what the icon and color communicate in your context.  
Includes the text "\[Custom text\]: ".

 Layout
-------

### Label placement

Use labels in a summary context. For example, you can place a label in a page summary. To convey statuses inline to indicate that they are tied to specific pieces of data, use [status indicators](/skyux/components/status-indicator.md) instead.

 Related information
--------------------

### Guidelines

*   [Call out information](/skyux/design/guidelines/call-out-info.md)

 Installation
-------------

NPM package

`@skyux/indicators`[View in NPM](https://www.npmjs.com/package/@skyux/indicators) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/indicators/src/lib/modules/label/label.module.ts#L20) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/indicators`Copy None found.

 SkyLabelModule
---------------

Type: Module

`import { SkyLabelModule } from '@skyux/indicators';`

 SkyLabelComponent
------------------

Type: Component

Selector: `sky-label`

### Inputs

#### `customDescription: string | undefined`

The text to be read by screen readers for users who cannot see the indicator icon when `descriptionType` is `custom`.

#### `descriptionType: SkyIndicatorDescriptionType | undefined`

The predefined text to be read by screen readers for users who cannot see the indicator icon. This property is optional but will be required in future versions of SKY UX.

#### `labelType: SkyLabelType | undefined`

The type of label to display.

Default: `'info'`

 SkyLabelType
-------------

Type: Type alias

    type SkyLabelType = "danger" | "info" | "success" | "warning"

 SkyIndicatorDescriptionType
----------------------------

Type: Type alias

    type SkyIndicatorDescriptionType = "attention" | "caution" | "completed" | "custom" | "danger" | "error" | "important-info" | "important-warning" | "none" | "success" | "warning"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyLabelHarness
----------------

Type: Class

`import { SkyLabelHarness } from '@skyux/indicators/testing';`

Harness for interacting with a label component in tests.

### Methods

#### `getCustomDescription(): Promise<string>`

Gets the custom text used for the screen reader description of the label component icon.

#### Returns

`Promise<string>`

#### `getDescriptionType(): Promise<SkyIndicatorDescriptionType>`

Gets the `descriptionType` of the label component.

#### Returns

`Promise<SkyIndicatorDescriptionType>`

#### `getLabelText(): Promise<string>`

Gets the text of the label component.

#### Returns

`Promise<string>`

#### `getLabelType(): Promise<SkyLabelType>`

Gets the `labelType` of the label component.

#### Returns

`Promise<SkyLabelType>`

#### `SkyLabelHarness.with(filters: SkyLabelHarnessFilters): HarnessPredicate<SkyLabelHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyLookupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyLabelHarnessFilters`

#### Returns

`HarnessPredicate<SkyLabelHarness>`

 SkyLabelHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyLabelHarness` instances.

    interface SkyLabelHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Examples

                   Skip to Main Content

 Label
=====

Labels provide compact, eye-catching design elements to draw attention to time-sensitive status information that users need to address. Statuses indicate a state or condition within one of four categories: info, success, warning, and danger.Usage
------

### Use when

Use labels when statuses are crucial to user tasks. If not, use regular text.

 Options
--------

### Label type

Label type

When to use

Example

`danger`

Use the danger label to indicate error states on records.

Error: Expired

`warning`

Use the warning label to indicate records in states that could have minor consequences if not acted on or avoided.

Warning: Overdue

`success`

Use the success label to indicate records in a positive of successful state.

Success: Completed

`info`

Use the info alert to call attention to a state or property on a record that needs to be elevated in the information hierarchy but does not require user action.

Attention: Board member

### Description type

Use a description type with labels to include a text equivalent for the icon and color information. This ensures that people who use assistive technologies receive equivalent information.

Label type

Description type

When to use

Example

Danger

`error`

Use when the label calls attention to an error state.  
Includes the text "Error: ".

Error: No longer validError: Declined

`important-warning`

Use when the label calls attention to information about a current status or situation that users should be aware of or that could have serious consequences.  
Includes the text "Important warning: ".

Important warning: Expired

`danger`

Use when the label calls attention to information that could users help someone avoid potentially serious consequences if an action is taken.  
Includes the text "Danger: ".

Danger: Do not print

Warning

`warning`

Use when the label calls attention to information about a current status or situation that has potentially minor consequences.  
Includes the text "Warning: ".

Warning: Overdue

`caution`

Use when the label calls attention to information that could help users avoid potentially minor consequences.  
Includes the text "Caution: ".

Caution: Hold application

Success

`success`

Use when the label calls attention to information that communicates a successful result or positive state. state.  
Includes the text "Success: ".

Success: Application accepted

Info

`attention`

Use when the label calls attention to information that should be elevated in the information hierarchy but does not require user action.  
Includes the text "Attention: ".

Attention: Top earner

Any

`custom`

Set your own label when none of the other description types are the text equivalent for what the icon and color communicate in your context.  
Includes the text "\[Custom text\]: ".

 Layout
-------

### Label placement

Use labels in a summary context. For example, you can place a label in a page summary. To convey statuses inline to indicate that they are tied to specific pieces of data, use [status indicators](/skyux/components/status-indicator.md) instead.

 Related information
--------------------

### Guidelines

*   [Call out information](/skyux/design/guidelines/call-out-info.md)

 Installation
-------------

NPM package

`@skyux/indicators`[View in NPM](https://www.npmjs.com/package/@skyux/indicators) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/indicators/src/lib/modules/label/label.module.ts#L20) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/indicators`Copy None found.

 SkyLabelModule
---------------

Type: Module

`import { SkyLabelModule } from '@skyux/indicators';`

 SkyLabelComponent
------------------

Type: Component

Selector: `sky-label`

### Inputs

#### `customDescription: string | undefined`

The text to be read by screen readers for users who cannot see the indicator icon when `descriptionType` is `custom`.

#### `descriptionType: SkyIndicatorDescriptionType | undefined`

The predefined text to be read by screen readers for users who cannot see the indicator icon. This property is optional but will be required in future versions of SKY UX.

#### `labelType: SkyLabelType | undefined`

The type of label to display.

Default: `'info'`

 SkyLabelType
-------------

Type: Type alias

    type SkyLabelType = "danger" | "info" | "success" | "warning"

 SkyIndicatorDescriptionType
----------------------------

Type: Type alias

    type SkyIndicatorDescriptionType = "attention" | "caution" | "completed" | "custom" | "danger" | "error" | "important-info" | "important-warning" | "none" | "success" | "warning"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyLabelHarness
----------------

Type: Class

`import { SkyLabelHarness } from '@skyux/indicators/testing';`

Harness for interacting with a label component in tests.

### Methods

#### `getCustomDescription(): Promise<string>`

Gets the custom text used for the screen reader description of the label component icon.

#### Returns

`Promise<string>`

#### `getDescriptionType(): Promise<SkyIndicatorDescriptionType>`

Gets the `descriptionType` of the label component.

#### Returns

`Promise<SkyIndicatorDescriptionType>`

#### `getLabelText(): Promise<string>`

Gets the text of the label component.

#### Returns

`Promise<string>`

#### `getLabelType(): Promise<SkyLabelType>`

Gets the `labelType` of the label component.

#### Returns

`Promise<SkyLabelType>`

#### `SkyLabelHarness.with(filters: SkyLabelHarnessFilters): HarnessPredicate<SkyLabelHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyLookupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyLabelHarnessFilters`

#### Returns

`HarnessPredicate<SkyLabelHarness>`

 SkyLabelHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyLabelHarness` instances.

    interface SkyLabelHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

### Label with basic setup

Edit in StackBlitz

Attention: Incomplete

Show code

Copy

    <sky-label
      data-sky-id="label-example"
      [descriptionType]="descriptionType"
      [labelType]="labelType"
    >
      {{ labelText }}
    </sky-label>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { SkyLabelHarness } from '@skyux/indicators/testing';
    
    import { IndicatorsLabelBasicExampleComponent } from './example.component';
    
    describe('Basic label', () => {
      async function setupTest(options?: {
        daysUntilDue?: number;
        submitted?: boolean;
      }): Promise<{
        labelHarness: SkyLabelHarness;
        fixture: ComponentFixture<IndicatorsLabelBasicExampleComponent>;
      }> {
        const fixture = TestBed.createComponent(
          IndicatorsLabelBasicExampleComponent,
        );
    
        if (options?.daysUntilDue !== undefined) {
          fixture.componentInstance.daysUntilDue = options.daysUntilDue;
        }
    
        if (options?.submitted !== undefined) {
          fixture.componentInstance.submitted = options.submitted;
        }
    
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const labelHarness = await loader.getHarness(
          SkyLabelHarness.with({ dataSkyId: 'label-example' }),
        );
    
        return { labelHarness, fixture };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [IndicatorsLabelBasicExampleComponent],
        });
      });
    
      it('should show an info label when submitted is false and there is more than a week until due', async () => {
        const { labelHarness, fixture } = await setupTest({ daysUntilDue: 8 });
        fixture.detectChanges();
    
        await expectAsync(labelHarness.getLabelType()).toBeResolvedTo('info');
        await expectAsync(labelHarness.getDescriptionType()).toBeResolvedTo(
          'attention',
        );
        await expectAsync(labelHarness.getLabelText()).toBeResolvedTo('Incomplete');
      });
    
      it('should show a warning label when submitted is false and there is less than a week until due', async () => {
        const { labelHarness, fixture } = await setupTest({ daysUntilDue: 6 });
        fixture.detectChanges();
    
        await expectAsync(labelHarness.getLabelType()).toBeResolvedTo('warning');
        await expectAsync(labelHarness.getDescriptionType()).toBeResolvedTo(
          'important-warning',
        );
        await expectAsync(labelHarness.getLabelText()).toBeResolvedTo('Due soon');
      });
    
      it('should show a danger label when submitted is false and it is past due', async () => {
        const { labelHarness, fixture } = await setupTest({ daysUntilDue: -1 });
        fixture.detectChanges();
    
        await expectAsync(labelHarness.getLabelType()).toBeResolvedTo('danger');
        await expectAsync(labelHarness.getDescriptionType()).toBeResolvedTo(
          'danger',
        );
        await expectAsync(labelHarness.getLabelText()).toBeResolvedTo('Overdue');
      });
    
      it('should show a success label when submitted is true', async () => {
        const { labelHarness, fixture } = await setupTest({ submitted: true });
        fixture.detectChanges();
    
        await expectAsync(labelHarness.getLabelType()).toBeResolvedTo('success');
        await expectAsync(labelHarness.getDescriptionType()).toBeResolvedTo(
          'completed',
        );
        await expectAsync(labelHarness.getLabelText()).toBeResolvedTo('Submitted');
      });
    });

Copy

    import { Component, Input } from '@angular/core';
    import {
      SkyIndicatorDescriptionType,
      SkyLabelModule,
      SkyLabelType,
    } from '@skyux/indicators';
    
    /**
     * @title Label with basic setup
     */
    @Component({
      selector: 'app-indicators-label-basic-example',
      templateUrl: './example.component.html',
      imports: [SkyLabelModule],
    })
    export class IndicatorsLabelBasicExampleComponent {
      @Input()
      public get daysUntilDue(): number {
        return this.#_daysUntilDue;
      }
    
      public set daysUntilDue(days: number) {
        this.#_daysUntilDue = days;
        this.#updateLabelProperties(this.submitted, days);
      }
    
      @Input()
      public get submitted(): boolean {
        return this.#_submitted;
      }
    
      public set submitted(submitted: boolean) {
        this.#_submitted = submitted;
        this.#updateLabelProperties(submitted, this.daysUntilDue);
      }
    
      protected descriptionType: SkyIndicatorDescriptionType = 'attention';
      protected labelText = 'Incomplete';
      protected labelType: SkyLabelType = 'info';
    
      #_daysUntilDue = 14;
      #_submitted = false;
    
      #updateLabelProperties(submitted: boolean, days: number): void {
        if (submitted) {
          this.labelType = 'success';
          this.descriptionType = 'completed';
          this.labelText = 'Submitted';
        } else if (days <= 0) {
          this.labelType = 'danger';
          this.descriptionType = 'danger';
          this.labelText = 'Overdue';
        } else if (days <= 7) {
          this.labelType = 'warning';
          this.descriptionType = 'important-warning';
          this.labelText = 'Due soon';
        } else {
          this.labelType = 'info';
          this.descriptionType = 'attention';
          this.labelText = 'Incomplete';
        }
      }
    }

# Testing

                 Skip to Main Content

 Label
=====

Labels provide compact, eye-catching design elements to draw attention to time-sensitive status information that users need to address. Statuses indicate a state or condition within one of four categories: info, success, warning, and danger.

 Usage
------

### Use when

Use labels when statuses are crucial to user tasks. If not, use regular text.

 Options
--------

### Label type

Label type

When to use

Example

`danger`

Use the danger label to indicate error states on records.

Error: Expired

`warning`

Use the warning label to indicate records in states that could have minor consequences if not acted on or avoided.

Warning: Overdue

`success`

Use the success label to indicate records in a positive of successful state.

Success: Completed

`info`

Use the info alert to call attention to a state or property on a record that needs to be elevated in the information hierarchy but does not require user action.

Attention: Board member

### Description type

Use a description type with labels to include a text equivalent for the icon and color information. This ensures that people who use assistive technologies receive equivalent information.

Label type

Description type

When to use

Example

Danger

`error`

Use when the label calls attention to an error state.  
Includes the text "Error: ".

Error: No longer validError: Declined

`important-warning`

Use when the label calls attention to information about a current status or situation that users should be aware of or that could have serious consequences.  
Includes the text "Important warning: ".

Important warning: Expired

`danger`

Use when the label calls attention to information that could users help someone avoid potentially serious consequences if an action is taken.  
Includes the text "Danger: ".

Danger: Do not print

Warning

`warning`

Use when the label calls attention to information about a current status or situation that has potentially minor consequences.  
Includes the text "Warning: ".

Warning: Overdue

`caution`

Use when the label calls attention to information that could help users avoid potentially minor consequences.  
Includes the text "Caution: ".

Caution: Hold application

Success

`success`

Use when the label calls attention to information that communicates a successful result or positive state. state.  
Includes the text "Success: ".

Success: Application accepted

Info

`attention`

Use when the label calls attention to information that should be elevated in the information hierarchy but does not require user action.  
Includes the text "Attention: ".

Attention: Top earner

Any

`custom`

Set your own label when none of the other description types are the text equivalent for what the icon and color communicate in your context.  
Includes the text "\[Custom text\]: ".

 Layout
-------

### Label placement

Use labels in a summary context. For example, you can place a label in a page summary. To convey statuses inline to indicate that they are tied to specific pieces of data, use [status indicators](/skyux/components/status-indicator.md) instead.

 Related information
--------------------

### Guidelines

*   [Call out information](/skyux/design/guidelines/call-out-info.md)

 Installation
-------------

NPM package

`@skyux/indicators`[View in NPM](https://www.npmjs.com/package/@skyux/indicators) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/indicators/src/lib/modules/label/label.module.ts#L20) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/indicators`Copy None found.

 SkyLabelModule
---------------

Type: Module

`import { SkyLabelModule } from '@skyux/indicators';`

 SkyLabelComponent
------------------

Type: Component

Selector: `sky-label`

### Inputs

#### `customDescription: string | undefined`

The text to be read by screen readers for users who cannot see the indicator icon when `descriptionType` is `custom`.

#### `descriptionType: SkyIndicatorDescriptionType | undefined`

The predefined text to be read by screen readers for users who cannot see the indicator icon. This property is optional but will be required in future versions of SKY UX.

#### `labelType: SkyLabelType | undefined`

The type of label to display.

Default: `'info'`

 SkyLabelType
-------------

Type: Type alias

    type SkyLabelType = "danger" | "info" | "success" | "warning"

 SkyIndicatorDescriptionType
----------------------------

Type: Type alias

    type SkyIndicatorDescriptionType = "attention" | "caution" | "completed" | "custom" | "danger" | "error" | "important-info" | "important-warning" | "none" | "success" | "warning"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyLabelHarness
----------------

Type: Class

`import { SkyLabelHarness } from '@skyux/indicators/testing';`

Harness for interacting with a label component in tests.

### Methods

#### `getCustomDescription(): Promise<string>`

Gets the custom text used for the screen reader description of the label component icon.

#### Returns

`Promise<string>`

#### `getDescriptionType(): Promise<SkyIndicatorDescriptionType>`

Gets the `descriptionType` of the label component.

#### Returns

`Promise<SkyIndicatorDescriptionType>`

#### `getLabelText(): Promise<string>`

Gets the text of the label component.

#### Returns

`Promise<string>`

#### `getLabelType(): Promise<SkyLabelType>`

Gets the `labelType` of the label component.

#### Returns

`Promise<SkyLabelType>`

#### `SkyLabelHarness.with(filters: SkyLabelHarnessFilters): HarnessPredicate<SkyLabelHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyLookupHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyLabelHarnessFilters`

#### Returns

`HarnessPredicate<SkyLabelHarness>`

 SkyLabelHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyLabelHarness` instances.

    interface SkyLabelHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.