---
component: 'icon'
description: 'Design guidelines, API documentation, and usage instructions for the icon component extracted from SKY UX documentation.'
---

# Icon Component Guidelines

## Component Overview
Icons represent actions, content, and ideas, and they help define the visual identity of SKY UX applications.

## Principles

### Global

Icons use well-established, universal images to visually convey meaning at a glance.

### Supplemental

Icons are paired with action labels and other text and are not used solely for decoration or visual interest.

### Specific

Icons convey a single meaning with limited variations. Each icon represents a common idea or subject that is not abstract.

## Usage

### ✅ Use when

Use icons alongside meaningful action labels to help users understand the purpose of actions at a glance.

**✅ Do use icons as a visual shorthand to supplement action labels.**

### ❌ Don't use when

Don't use icons solely for visual interest or decoration.

**❌ Don't use icons as decoration.**

Don't use icons for multiple purposes. Each icon conveys a single, specific meaning that users can understand at a glance.

**❌ Don't use icons with established meanings for other purposes.**

## Behavior and states

### Color

Icons use solid, monochromatic colors that they usually inherit from their parent components. Icon colors must meet the WCAG contrast ratio of 3:1. For more information, see the SKY UX color guidelines.

### Style

SKY UX icons have two style variations: line and solid. Use line icons for most user experiences.

### Size

Use the default icon size, medium or m, when including icons in buttons or for use with standard body copy. Only use smaller or larger icon sizes when pairing an icon with smaller or larger content to match to its paired content or better fit its context.

### Localization

SKY UX icons account for global considerations to ensure that international users from different cultures and backgrounds can understand them.

## Accessibility

## API Documentation

### Components and Directives

#### FormsCheckboxIconGroupExampleComponent

**Selector:** `app-forms-checkbox-icon-group-example`

**Package:** `@skyux/code-examples`

#### FormsRadioIconExampleComponent

**Selector:** `app-forms-radio-icon-example`

**Package:** `@skyux/code-examples`

#### IconBasicExampleComponent

**Selector:** `app-icon-basic-example`

**Package:** `@skyux/code-examples`

#### IconIconButtonExampleComponent

**Selector:** `app-icon-icon-button-example`

**Package:** `@skyux/code-examples`

#### SkyIndicatorIconType

**Package:** `@skyux/indicators`

#### SkyActionButtonIconComponent

Specifies an icon to display on the action button.

**Selector:** `sky-action-button-icon`

**Package:** `@skyux/layout`

**Inputs:**

- `iconName`: `string` - The name of the Blackbaud SVG icon to display.

#### SkyGridUIConfig

**Package:** `@skyux/grids`

⚠️ **This component is deprecated.**

#### SkyThemeIconManifestService

Provides a method for retrieving metadata about the SKY UX icon font.

**Package:** `@skyux/theme`

#### SkyThemeIconManifest

**Package:** `@skyux/theme`

#### SkyUIConfigService

**Package:** `@skyux/core`

#### MockSkyUIConfigService

**Package:** `@skyux/core/testing`

#### SkyIconSvgResolverService

**Package:** `@skyux/icon`

#### SkyIconComponent

**Selector:** `sky-icon`

**Package:** `@skyux/icon`

**Inputs:**

- `iconName`: `string` - The name of the Blackbaud SVG icon to display.
- `iconSize`: `InputSignal<undefined | SkyIconSize>` - The icon size. Size is independent of font size. (default: "m")
- `variant`: `SkyIconVariantType | undefined` - The icon variant. If the variant doesn't exist for the
specified icon, the normal icon is displayed. This property only applies when using SKY UX icons.

#### SkyIconModule

**Package:** `@skyux/icon`

#### SkyIconSize

**Package:** `@skyux/icon`

#### SkyIconVariantType

**Package:** `@skyux/icon`

#### SkyIconHarnessFilters

A set of criteria that can be used to filter a list of SkyIconHarness instances.

**Package:** `@skyux/icon/testing`

#### SkyIconHarness

Harness for interacting with an icon component in tests.

**Package:** `@skyux/icon/testing`

### Code Examples

#### Icon checkbox group

**Selector:** `app-forms-checkbox-icon-group-example`

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
import { SkyCheckboxModule } from '@skyux/forms';

/**
 * @title Icon checkbox group
 */
@Component({
  selector: 'app-forms-checkbox-icon-group-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyCheckboxModule],
})
export class FormsCheckboxIconGroupExampleComponent {
  protected formGroup: FormGroup;

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      bold: new FormControl(false),
      italic: new FormControl(false),
      underline: new FormControl(false),
    });
  }

  public onSubmit(): void {
    console.log(this.formGroup.value);
  }
}

```

**Template:**

```html
<form [formGroup]="formGroup" (ngSubmit)="onSubmit()">
  <sky-checkbox-group
    headingText="Text formatting"
    [formGroup]="formGroup"
    [headingHidden]="true"
    [stacked]="true"
  >
    <sky-checkbox
      formControlName="bold"
      iconName="text-bold"
      labelHidden="true"
      labelText="Bold"
    />
    <sky-checkbox
      formControlName="italic"
      iconName="text-italic"
      labelHidden="true"
      labelText="Italic"
    />
    <sky-checkbox
      formControlName="underline"
      iconName="text-underline"
      labelHidden="true"
      labelText="Underline"
    />
  </sky-checkbox-group>
  <button class="sky-btn sky-btn-primary" type="submit">Submit</button>
</form>

```

#### Radio group with icons

**Selector:** `app-forms-radio-icon-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyRadioModule } from '@skyux/forms';

interface Item {
  iconName: string;
  label: string;
  name: string;
}

/**
 * @title Radio group with icons
 */
@Component({
  selector: 'app-forms-radio-icon-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyRadioModule],
})
export class FormsRadioIconExampleComponent {
  protected formGroup: FormGroup;

  protected views: Item[] = [
    { iconName: 'table', label: 'Table', name: 'table' },
    { iconName: 'text-number-list-ltr', label: 'List', name: 'list' },
    { iconName: 'location', label: 'Map', name: 'map' },
  ];

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      myView: this.views[0].name,
    });
  }
}

```

**Template:**

```html
<form [formGroup]="formGroup">
  <sky-radio-group
    class="sky-switch-icon-group"
    formControlName="myView"
    headingHidden="true"
    headingText="View"
  >
    @for (view of views; track view) {
      <sky-radio
        [labelHidden]="true"
        [iconName]="view.iconName"
        [labelText]="view.label"
        [value]="view.name"
      />
    }
  </sky-radio-group>
</form>

```

#### Icon with basic setup

**Selector:** `app-icon-basic-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyIconModule } from '@skyux/icon';

/**
 * @title Icon with basic setup
 */
@Component({
  selector: 'app-icon-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyIconModule],
})
export class IconBasicExampleComponent {}

```

**Template:**

```html
<sky-icon iconName="calendar-ltr" iconSize="xxxs" />
<sky-icon iconName="calendar-ltr" iconSize="xxs" />
<sky-icon iconName="calendar-ltr" iconSize="xs" />
<sky-icon iconName="calendar-ltr" iconSize="s" />
<sky-icon iconName="calendar-ltr" />
<sky-icon iconName="calendar-ltr" iconSize="l" />
<sky-icon iconName="calendar-ltr" iconSize="xl" />
<sky-icon iconName="calendar-ltr" iconSize="xxl" />
<sky-icon iconName="calendar-ltr" iconSize="xxxl" />
<sky-icon
  data-sky-id="icon-example"
  iconName="calendar-ltr"
  variant="solid"
  iconSize="xl"
/>

<div>
  <sky-icon iconName="navigation" iconSize="xl" />
</div>

<div>
  <sky-icon iconName="chevron-down" iconSize="xl" />
</div>

```

#### Icons in buttons

**Selector:** `app-icon-icon-button-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyIconModule } from '@skyux/icon';

/**
 * @title Icons in buttons
 */
@Component({
  selector: 'app-icon-icon-button-example',
  templateUrl: './example.component.html',
  imports: [SkyIconModule],
})
export class IconIconButtonExampleComponent {
  protected textButtonClick(): void {
    alert('Text with icon button clicked');
  }

  protected iconOnlyButtonClick(): void {
    alert('Icon only button clicked');
  }
}

```

**Template:**

```html
<button
  class="sky-btn sky-btn-default"
  type="button"
  (click)="textButtonClick()"
>
  <sky-icon data-sky-id="text-button-icon" iconName="save" />
  Save
</button>

<button
  class="sky-btn sky-btn-icon-borderless"
  type="button"
  (click)="iconOnlyButtonClick()"
>
  <sky-icon data-sky-id="button-icon" iconName="edit" />
</button>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.