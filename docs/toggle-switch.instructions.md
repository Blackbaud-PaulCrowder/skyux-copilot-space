---
component: 'toggle-switch'
description: 'Design guidelines, API documentation, and usage instructions for the toggle-switch component extracted from SKY UX documentation.'
---

# Toggle Switch Component Guidelines

## Component Overview
The toggle switch lets users turn a SKY UX-themed switch "on" or "off." The change takes effect immediately.

## Usage

### ✅ Use when

Use toggles when users can toggle between two states or options, and the changes take effect immediately.

**✅ Do use toggles to alternate between two states when changes take effect immediately.**

### ❌ Don't use when

Don't use toggles when the options have significant consequences that the users need to confirm before changes take effect. Use a workflow where users must confirm the changes instead.

**❌ Don't use toggles for states with significant consequences.**

Don't use toggles when the input is presented in a modal. Use checkboxes instead.

**❌ Don't use toggles inside modals where they won't take effect immediately.**

## Anatomy

- Toggle switch
- Label
- Help inline button

## Options

### Label

Text labels describe the properties that toggles control, and you can provide labels for both the selected and unselected states. Always include text labels unless other text clearly indicates the purpose of toggles. For example, when toggles are in grids, you can rely on column headings instead of text labels.

In scenarios where toggles may become disabled, always include labels for both the selected and unselected states to make those states clear to users.

### Help inline button

When you need to supplement a toggle switch label with additional information, you can place a help inline button beside the label to invoke contextual user assistance.

## Related information

### Components

- Checkbox
- Help inline button
- Radio button

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### FormsToggleSwitchBasicExampleComponent

**Selector:** `app-forms-toggle-switch-basic-example`

**Package:** `@skyux/code-examples`

#### FormsToggleSwitchHelpKeyExampleComponent

**Selector:** `app-forms-toggle-switch-help-key-example`

**Package:** `@skyux/code-examples`

#### SkyToggleSwitchLabelComponent

Specifies the label to display beside the toggle switch. To display a help button beside the label, include a help
button element, such as `sky-help-inline`, in the `sky-toggle-switch` element and a `sky-control-help` CSS class on
that help button element.

**Selector:** `sky-toggle-switch-label`

**Package:** `@skyux/forms`

⚠️ **This component is deprecated.**

#### SkyToggleSwitchComponent

**Selector:** `sky-toggle-switch`

**Package:** `@skyux/forms`

**Inputs:**

- `disabled`: `boolean | undefined` - Whether to disable the toggle switch on template-driven forms. Don't use this input on reactive forms because they may overwrite the input or leave the control out of sync.
To set the disabled state on reactive forms, use the `FormControl` instead. (default: false)
- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is placed beside the toggle switch label. Clicking the button invokes [global help](https://developer.blackbaud.com/skyux/learn/develop/global-help)
as configured by the application. This property only applies when `labelText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `labelText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the toggle switch. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `labelText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `labelHidden`: `boolean` - Whether to hide `labelText` from view. (default: false)
- `labelText`: `string | undefined` - The text to display as the toggle switch's label.
- `tabIndex`: `number | undefined` - The tab index for the toggle switch. If not defined, the index is set to the position
of the toggle switch on load. (default: 0)
- `ariaLabel`: `string | undefined` - The ARIA label for the toggle switch. This sets the `aria-label`
attribute to provide a text equivalent for screen readers [to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
Use a context-sensitive label, such as "Activate annual fundraiser" for a toggle switch that activates and deactivates an annual fundraiser. Context is especially important if multiple toggle switches are in close proximity.
When the `sky-toggle-switch-label` component displays a visible label, this property is only necessary if that label requires extra context.
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `checked`: `boolean` - Whether the toggle switch is selected. (default: false)

**Outputs:**

- `toggleChange`: `EventEmitter<SkyToggleSwitchChange>` - Fires when the checked state of a toggle switch changes.

#### SkyToggleSwitchModule

**Package:** `@skyux/forms`

#### SkyToggleSwitchChange

Indicates whether the toggle switch is selected.

**Package:** `@skyux/forms`

#### SkyToggleSwitchHarnessFilters

A set of criteria that can be used to filter a list of `SkyToggleSwitchHarness` instances.

**Package:** `@skyux/forms/testing`

#### SkyToggleSwitchHarness

Harness for interacting with a toggle switch component in tests.

**Package:** `@skyux/forms/testing`

### Code Examples

#### Toggle switch with basic setup

**Selector:** `app-forms-toggle-switch-basic-example`

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
import { SkyToggleSwitchModule } from '@skyux/forms';

interface ToggleSwitchFormType {
  registration: FormControl<boolean | null>;
}

/**
 * @title Toggle switch with basic setup
 */
@Component({
  selector: 'app-forms-toggle-switch-basic-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyToggleSwitchModule],
})
export class FormsToggleSwitchBasicExampleComponent {
  protected formGroup: FormGroup;
  protected helpPopoverContent =
    'When you open an event, a registration page becomes available online, and admins are able to register people to attend.';

  constructor() {
    this.formGroup = inject(FormBuilder).group<ToggleSwitchFormType>({
      registration: new FormControl(false),
    });
  }
}

```

**Template:**

```html
<form [formGroup]="formGroup">
  <sky-toggle-switch
    data-sky-id="toggle-switch"
    formControlName="registration"
    labelText="Open for registration"
    [helpPopoverContent]="helpPopoverContent"
  />
</form>

```

#### Toggle switch with help key

**Selector:** `app-forms-toggle-switch-help-key-example`

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
import { SkyToggleSwitchModule } from '@skyux/forms';

interface ToggleSwitchFormType {
  registration: FormControl<boolean | null>;
}

/**
 * @title Toggle switch with help key
 */
@Component({
  selector: 'app-forms-toggle-switch-help-key-example',
  templateUrl: './example.component.html',
  imports: [FormsModule, ReactiveFormsModule, SkyToggleSwitchModule],
})
export class FormsToggleSwitchHelpKeyExampleComponent {
  protected formGroup: FormGroup;

  constructor() {
    this.formGroup = inject(FormBuilder).group<ToggleSwitchFormType>({
      registration: new FormControl(false),
    });
  }
}

```

**Template:**

```html
<form [formGroup]="formGroup">
  <sky-toggle-switch
    data-sky-id="toggle-switch"
    formControlName="registration"
    helpKey="registration-help"
    labelText="Open for registration"
  />
</form>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.