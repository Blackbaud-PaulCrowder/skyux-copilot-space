---
component: 'sectioned-form'
description: 'Design guidelines, API documentation, and usage instructions for the sectioned-form component extracted from SKY UX documentation.'
---

# Sectioned Form Component Guidelines

## Component Overview
Sectioned forms combine multiple forms and display large amounts of related information inside large modals.

## Usage

### ✅ Use when

Use sectioned forms when users navigate into a hierarchy and you expect them to know what they are looking for. This is common for editing pieces of a larger record and for tasks such as applying filters.

Use sectioned forms when it's beneficial to group related but independent forms to simplify the UI on the page. For example, use an Add filters button to open a sectioned form with multiple filter options instead of separate buttons and separate forms to access options to filter by giving, status, constituent code, ratings, or other options.

Use sectioned forms in large-sized and full-screen modals to ensure sufficient horizontal space for the component and its contents. Don't use smaller modal sizes.

### ❌ Don't use when

Don't use sectioned forms when choices on one tab can affect other tabs because changes are potentially invisible or unpredictable to users.

Don't use sectioned forms in small- or medium-sized modals because the component requires the horizontal space that large-sized and full-screen modals provide.

## Behavior

### Responsiveness

Sectioned forms are partially responsive by default. The tab pane is hidden when a small enough breakpoint size is reached, which leaves the user only viewing currently selected form.

Because of this behavior, the user needs a way to view the tab pane so they can change which form tab they are viewing. This behavior must be configured manually, using a button in the footer of the modal, as is done in the Behavioral Demo above, and is shown in the Code Examples in the Development pane.

## Related information

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### TabsSectionedFormModalExampleComponent

**Selector:** `app-tabs-sectioned-form-modal-example`

**Package:** `@skyux/code-examples`

#### SkySectionedFormSectionComponent

Creates an individual form to display as a section within the sectioned form.

**Selector:** `sky-sectioned-form-section`

**Package:** `@skyux/tabs`

**Inputs:**

- `active`: `boolean | undefined` - Whether the section is active when the form loads. (default: false)
- `heading`: `string | undefined` - The section header. **[Required]**
- `itemCount`: `number | undefined` - The number of items within the section. A counter appears beside the section header.

#### SkySectionedFormComponent

Creates a container for the sectioned forms.

**Selector:** `sky-sectioned-form`

**Package:** `@skyux/tabs`

**Inputs:**

- `maintainSectionContent`: `boolean | undefined` - Whether the sectioned form loads section content during initialization so that it
displays content without moving around elements in the content container. (default: false)
- `messageStream`: `Subject<SkySectionedFormMessage>`

**Outputs:**

- `indexChanged`: `EventEmitter<number>` - Fires when the active tab changes and emits the index of the active
section. The index is based on the section's position when the form loads.
- `tabsVisibleChanged`: `EventEmitter<boolean>` - Fires when the sectioned form tabs are shown or hidden.

#### SkySectionedFormModule

**Package:** `@skyux/tabs`

#### SkySectionedFormService

**Package:** `@skyux/tabs`

#### SkySectionedFormMessageType

**Package:** `@skyux/tabs`

#### SkySectionedFormMessage

**Package:** `@skyux/tabs`

#### SkySectionedFormHarnessFilters

A set of criteria that can be used to filter a list of `SkySectionedFormHarness` instances.

**Package:** `@skyux/tabs/testing`

#### SkySectionedFormHarness

Harness for interacting with a sectioned form component in tests.

**Package:** `@skyux/tabs/testing`

#### SkySectionedFormSectionContentHarnessFilters

A set of criteria that can be used to filter a list of `SkySectionedFormSectionContentHarness` instances.

**Package:** `@skyux/tabs/testing`

#### SkySectionedFormSectionContentHarness

Harness for interacting with a sectioned form content in tests.

**Package:** `@skyux/tabs/testing`

#### SkySectionedFormSectionHarnessFilters

A set of criteria that can be used to filter a list of `SkySectionedFormSectionHarness` instances.

**Package:** `@skyux/tabs/testing`

#### SkySectionedFormSectionHarness

Harness for interacting with a sectioned form section component in tests.

**Package:** `@skyux/tabs/testing`

### Code Examples

#### Sectioned form inside modal

**Selector:** `app-tabs-sectioned-form-modal-example`

**TypeScript:**

```typescript
import { ChangeDetectionStrategy, Component, inject } from '@angular/core';
import { SkyModalCloseArgs, SkyModalService } from '@skyux/modals';

import { ModalComponent } from './modal.component';

/**
 * @title Sectioned form inside modal
 */
@Component({
  standalone: true,
  selector: 'app-tabs-sectioned-form-modal-example',
  templateUrl: './example.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class TabsSectionedFormModalExampleComponent {
  readonly #modalSvc = inject(SkyModalService);

  public openModal(): void {
    const modalInstance = this.#modalSvc.open(ModalComponent, {
      size: 'large',
    });

    modalInstance.closed.subscribe((result: SkyModalCloseArgs) => {
      if (result.reason === 'cancel') {
        console.log(`Modal cancelled`);
      } else if (result.reason === 'save') {
        console.log(`Modal saved`);
      }
    });
  }
}

```

**Template:**

```html
<button class="sky-btn sky-btn-default" type="button" (click)="openModal()">
  Open sectioned form
</button>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.