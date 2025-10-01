---
component: 'progress-indicator-wizard'
description: 'Design guidelines, API documentation, and usage instructions for the progress-indicator-wizard component extracted from SKY UX documentation.'
---

# Progress Indicator Wizard Component Guidelines

## Component Overview
Wizards guide users through pre-defined steps in a particular order to represent a series of related decisions in a user's direct workflow. Progress indicator wizard is deprecated in favor of tabs wizard. For more information, see the progress indicator wizard deprecation instructions.

## Usage

### ✅ Use when

Use wizards when users must perform multiple steps in a particular order. Wizards illustrate the step-wise nature of tasks and reinforce progress toward final goals as users complete steps.

Use wizards when users perform tasks repeatedly or when tasks are best presented as multiple steps but only require a single sitting.

Use wizards when tasks do not result in records or settings with page-level views.

Use wizards when interaction complexity of each step is low. For example, steps can use standard form inputs and controls.

### ❌ Don't use when

Don't use wizards when users for long or complex setup processes or when the complexity of steps varies drastically. Use waterfall progress indicators instead.

Don't use wizards when tasks include more than six steps or require more time than a single sitting. Use waterfall progress indicators instead.

Don't use wizards when users must be aware of sequential progress that they are not responsible for. Use passive progress indicators instead.

## Related information

### Components

- Modal
- Passive progress indicator
- Waterfall progress indicator

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### ProgressIndicatorWizardBasicExampleComponent

**Selector:** `app-progress-indicator-wizard-basic-example`

**Package:** `@skyux/code-examples`

### Code Examples

#### Wizard (progress indicator)

**Selector:** `app-progress-indicator-wizard-basic-example`

**TypeScript:**

```typescript
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import { SkyModalService } from '@skyux/modals';

import { ModalComponent } from './modal.component';

/**
 * @title Wizard (progress indicator)
 */
@Component({
  standalone: true,
  selector: 'app-progress-indicator-wizard-basic-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class ProgressIndicatorWizardBasicExampleComponent {
  readonly #modalSvc = inject(SkyModalService);

  protected openWizard(): void {
    this.#modalSvc.open(ModalComponent);
  }
}

```

**Template:**

```html
<button class="sky-btn sky-btn-default" type="button" (click)="openWizard()">
  Open wizard
</button>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.