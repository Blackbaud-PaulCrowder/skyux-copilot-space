---
component: 'label'
description: 'Design guidelines, API documentation, and usage instructions for the label component extracted from SKY UX documentation.'
---

# Label Component Guidelines

## Component Overview
Labels provide compact, eye-catching design elements to draw attention to time-sensitive status information that users need to address. Statuses indicate a state or condition within one of four categories: info, success, warning, and danger.

## Usage

### ✅ Use when

Use labels when statuses are crucial to user tasks. If not, use regular text.

## Options

### Label type

### Description type

Use a description type with labels to include a text equivalent for the icon and color information. This ensures that people who use assistive technologies receive equivalent information.

## Layout

### Label placement

Use labels in a summary context. For example, you can place a label in a page summary. To convey statuses inline to indicate that they are tied to specific pieces of data, use status indicators instead.

## Related information

### Guidelines

- Call out information

## API Documentation

### Components and Directives

#### IndicatorsLabelBasicExampleComponent

**Selector:** `app-indicators-label-basic-example`

**Package:** `@skyux/code-examples`

**Inputs:**

- `daysUntilDue`: `number`
- `submitted`: `boolean`

#### ListSortLabelModel

These properties are a work in progress, and we do not recommend using them.

**Package:** `@skyux/list-builder`

⚠️ **This component is deprecated.**

#### SkyKeyInfoLabelComponent

Specifies a label to display in smaller text under or beside the value.
To display a help button beside the label, include a help button element, such as `sky-help-inline`,
in the `sky-key-info` element and a `sky-control-help` CSS class on that help button element.

**Selector:** `sky-key-info-label`

**Package:** `@skyux/indicators`

#### SkyLabelType

**Package:** `@skyux/indicators`

#### SkyLabelComponent

**Selector:** `sky-label`

**Package:** `@skyux/indicators`

**Inputs:**

- `customDescription`: `string | undefined` - The text to be read by screen readers for users who cannot see
the indicator icon when `descriptionType` is `custom`.
- `descriptionType`: `SkyIndicatorDescriptionType | undefined` - The predefined text to be read by screen readers for users who cannot see the indicator icon.
This property is optional but will be required in future versions of SKY UX.
- `labelType`: `SkyLabelType | undefined` - The type of label to display. (default: 'info')

#### SkyLabelModule

**Package:** `@skyux/indicators`

#### SkyLabelFixture

Allows interaction with a SKY UX label component.

**Package:** `@skyux/indicators/testing`

⚠️ **This component is deprecated.**

#### SkyLabelHarnessFilters

A set of criteria that can be used to filter a list of `SkyLabelHarness` instances.

**Package:** `@skyux/indicators/testing`

#### SkyLabelHarness

Harness for interacting with a label component in tests.

**Package:** `@skyux/indicators/testing`

#### SkyDefinitionListLabelComponent

Specifies the label in a label-value pair.

**Selector:** `sky-definition-list-label`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyCheckboxLabelComponent

Specifies a label for the checkbox. To display a help button beside the label, include a help button element, such as
`sky-help-inline`, in the `sky-checkbox-label` element and a `sky-control-help` CSS class on that help button
element.

**Selector:** `sky-checkbox-label`

**Package:** `@skyux/forms`

⚠️ **This component is deprecated.**

#### SkyFileAttachmentLabelComponent

Displays a label above the file attachment element. To display a help button
beside the label, include a help button element, such as `sky-help-inline`,
in the `sky-file-attachment-label` element and a `sky-control-help` CSS class
on that help button element.

**Selector:** `sky-file-attachment-label`

**Package:** `@skyux/forms`

⚠️ **This component is deprecated.**

#### SkyRadioLabelComponent

Specifies a label for the radio button. To display a help button beside the label, include a help button element,
such as `sky-help-inline`, in the `sky-radio-label` element and a `sky-control-help` CSS class on that help button
element.

**Selector:** `sky-radio-label`

**Package:** `@skyux/forms`

⚠️ **This component is deprecated.**

#### SkyToggleSwitchLabelComponent

Specifies the label to display beside the toggle switch. To display a help button beside the label, include a help
button element, such as `sky-help-inline`, in the `sky-toggle-switch` element and a `sky-control-help` CSS class on
that help button element.

**Selector:** `sky-toggle-switch-label`

**Package:** `@skyux/forms`

⚠️ **This component is deprecated.**

#### SkyCheckboxLabelHarness

Harness for interacting with a checkbox label component in tests.

**Package:** `@skyux/forms/testing`

#### SkyRadioLabelHarness

Harness for interacting with a radio label component in tests.

**Package:** `@skyux/forms/testing`

#### SkyScreenReaderLabelDirective

Adds the element to a screen reader only section of the body.
This prevents components' DOM from including text only intended for screen readers.

**Selector:** `[skyScreenReaderLabel]`

**Package:** `@skyux/core`

**Inputs:**

- `createLabel`: `boolean` - Indicates if the label should be created in the DOM. (default: false)

### Code Examples

#### Label with basic setup

**Selector:** `app-indicators-label-basic-example`

**TypeScript:**

```typescript
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

```

**Template:**

```html
<sky-label
  data-sky-id="label-example"
  [descriptionType]="descriptionType"
  [labelType]="labelType"
>
  {{ labelText }}
</sky-label>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.