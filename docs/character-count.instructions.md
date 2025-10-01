---
component: 'character-count'
description: 'Design guidelines, API documentation, and usage instructions for the character-count component extracted from SKY UX documentation.'
---

# Character Count Component Guidelines

## Component Overview
The character count indicator extends a text input to apply a character limit and display the number of characters entered and the character limit.

## Usage

### ✅ Use when

Use character count indicators when users are likely to exceed character limits. Indicators are useful when technical requirements lead to restrictive character limits or when user entries are freeform and could be very long.

### ❌ Don't use when

Don't use character count indicators when character limits are apparent or implied by the data type.

Don't use character count indicators on inputs when users are unlikely to exceed character limits. Use normal form validation instead.

## Anatomy

- Input field
- Status indicator (danger)
- Character count indicator

## Options

### Character count indicator

The character count indicator displays the number of characters that users enter, the character limit, and a danger icon if users exceed the limit. For inputs where users are unlikely to reach the character limit, you don't need to display the character count indicator.

## Behavior and states

The character count indicator component extends the form classes that define styles and the appearance of input field states.

## Content

## Layout

The character count indicator always appears in the top right above the input field. Long field labels do not displace indicators. The labels wrap to multiple lines instead.

## Related information

### Components

- Input box

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### FormsCharacterCountExampleComponent

**Selector:** `app-forms-character-count-example`

**Package:** `@skyux/code-examples`

#### SkyCharacterCounterIndicatorComponent

**Selector:** `sky-character-counter-indicator`

**Package:** `@skyux/forms`

#### SkyCharacterCounterScreenReaderPipe

**Package:** `@skyux/forms`

#### SkyCharacterCounterInputDirective

Creates an input field that validates the number of characters. Place this directive on
an `input` or `textarea` element. If users enter more characters than allowed, then the
input field is invalid and the component displays an error indicator.

**Selector:** `[skyCharacterCounter]`

**Package:** `@skyux/forms`

**Inputs:**

- `skyCharacterCounterIndicator`: `SkyCharacterCounterIndicatorComponent | undefined` - The character count indicator component that displays the character count,
character limit, and over-the-limit indicator. Place this directive on an `input` or
`textarea` element.
- `skyCharacterCounterLimit`: `number | undefined` - The maximum number of characters allowed in the input field. Place this directive
on an `input` or `textarea` element. This property accepts `number` values. **[Required]**

#### SkyCharacterCounterModule

**Package:** `@skyux/forms`

#### SkyCharacterCounterIndicatorHarnessFilters

A set of criteria that can be used to filter a list of SkyCharacterCounterIndicatorHarness instances.

**Package:** `@skyux/forms/testing`

#### SkyCharacterCounterIndicatorHarness

Harness for interacting with a character counter indicator component in tests.

**Package:** `@skyux/forms/testing`

### Code Examples

#### Character count with basic setup

**Selector:** `app-forms-character-count-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyIdModule } from '@skyux/core';
import { SkyCharacterCounterModule, SkyInputBoxModule } from '@skyux/forms';
import { SkyStatusIndicatorModule } from '@skyux/indicators';

/**
 * @title Character count with basic setup
 */
@Component({
  selector: 'app-forms-character-count-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyCharacterCounterModule,
    SkyIdModule,
    SkyInputBoxModule,
    SkyStatusIndicatorModule,
  ],
})
export class FormsCharacterCountExampleComponent {
  protected description: FormControl;
  protected formGroup: FormGroup;
  protected maxDescriptionCharacterCount = 50;

  readonly #formBuilder = inject(FormBuilder);

  constructor() {
    this.description = this.#formBuilder.control(
      'Boys and Girls Club of South Carolina donation',
    );

    this.formGroup = this.#formBuilder.group({
      description: this.description,
    });
  }
}

```

**Template:**

```html
<form [formGroup]="formGroup">
  <sky-input-box stacked="true" labelText="Transaction description">
    <sky-character-counter-indicator
      #descriptionIndicator
      data-sky-id="description-indicator"
    />

    <input
      #descriptionInput="skyId"
      class="sky-form-control description-input"
      formControlName="description"
      skyCharacterCounter
      skyId
      type="text"
      [attr.aria-describedby]="characterCountError.id"
      [skyCharacterCounterIndicator]="descriptionIndicator"
      [skyCharacterCounterLimit]="maxDescriptionCharacterCount"
    />

    <span #characterCountError="skyId" class="sky-error-indicator" skyId>
      @if (description.errors?.['skyCharacterCounter']) {
        <sky-status-indicator
          data-sky-id="description-status-indicator-over-limit"
          descriptionType="error"
          indicatorType="danger"
        >
          Limit Transaction description to
          {{ maxDescriptionCharacterCount }} characters.
        </sky-status-indicator>
      }
    </span>
  </sky-input-box>
</form>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.