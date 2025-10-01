---
component: 'tabs-wizard'
description: 'Design guidelines, API documentation, and usage instructions for the tabs-wizard component extracted from SKY UX documentation.'
---

# Tabs Wizard Component Guidelines

## Component Overview
Wizards guide users through pre-defined steps in a particular order to represent a series of related decisions in a user's direct workflow. This wizard implementation replaces a deprecated wizard that used sky-progress-indicator. We recommend this implementation that instead uses tabStyle="wizard" on the sky-tabset component.

## Usage

### ✅ Use when

Use wizards when a single task includes multiple steps that users must perform in a particular order. Wizards illustrate the step-by-step nature of tasks and reinforce progress toward final goals as users complete steps.

Use wizards when users perform tasks repeatedly or when tasks are best presented as multiple steps but only require a single sitting.

Use wizards when the interaction complexity of each step is low. For example, steps can use standard form inputs and controls.

Use wizards in large-sized modals only to ensure sufficient horizontal space for the component and its contents. Don't use smaller modal sizes.

### ❌ Don't use when

Don't use wizards for long or complex setup processes or when the complexity of steps varies drastically. Use waterfall progress indicators instead.

Don't use wizards when tasks include more than six steps or require more time than a single sitting. Use waterfall progress indicators instead.

Don't use wizards when users must be aware of sequential progress that they are not responsible for. Use passive progress indicators instead.

Don't use wizards in small- or medium-sized modals because the component requires the horizontal space that large modals provide.

## Anatomy

- Modal
- Current step indicator
- Step indicator
- Step controls
- Disabled step indicator

## Options

### Disabled step indicators

To guide users through wizards in a particular order, you can disable steps and reinforce the step-by-step nature of the tasks. In most cases, we recommend disabling future steps until users meet the requirements on the preceding step, which enables the Next button.

## Behavior and states

### Required inputs

On each step of the wizard, disable the progressive Next action until all required inputs are populated.

## Content

### Step numbers

To help guide users through the predefined steps of wizards in the correct order, include sequential numbers in the step labels.

### Step controls

## Related information

### Components

- Modal
- Passive progress indicator
- Waterfall progress indicator

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### TabsWizardBasicExampleComponent

**Selector:** `app-tabs-wizard-basic-example`

**Package:** `@skyux/code-examples`

### Code Examples

#### Wizard in a modal

**Selector:** `app-tabs-wizard-basic-example`

**TypeScript:**

```typescript
import { Component, inject } from '@angular/core';
import { SkyModalService } from '@skyux/modals';

import { ModalComponent } from './modal.component';

/**
 * @title Wizard in a modal
 */
@Component({
  standalone: true,
  selector: 'app-tabs-wizard-basic-example',
  templateUrl: './example.component.html',
})
export class TabsWizardBasicExampleComponent {
  readonly #modalSvc = inject(SkyModalService);

  #modalSize = 'large';

  protected openWizard(): void {
    this.#modalSvc.open(ModalComponent, { size: this.#modalSize });
  }
}

```

**Template:**

```html
<button type="button" class="sky-btn sky-btn-default" (click)="openWizard()">
  Open Wizard
</button>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.