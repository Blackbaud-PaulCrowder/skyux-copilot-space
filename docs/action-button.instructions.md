---
component: 'action-button'
description: 'Design guidelines, API documentation, and usage instructions for the action-button component extracted from SKY UX documentation.'
---

# Action Button Component Guidelines

## Component Overview
Action buttons create large buttons with icons, headers, and descriptions that present users with multiple, branching options to move forward with tasks

## Usage

### ✅ Use when

Use actions buttons when:

- Users initiate tasks, often with a page's primary action. Tasks include 2 to 6 methods of completion, and users must choose exactly one method. If tasks have more than 6 methods of completion, use a different selection input and interaction.
- Methods of completion are system-defined, not user-defined.
- Methods of completion mostly determine how tasks proceed, and this choice is made at or near the beginning of the task
- The outcome of end result will be largely the same, regardless of the method

Use action buttons when they represent a decision point within a task where users must select a method of completion. Do not use them when users can skip them, avoid them, or address them later. Present action buttons in a way that isolates the choices that they represent and removes other decisions, tasks, or content. Use the details line on the buttons to provide context or explain differences between the options.

Use action buttons immediately after users initiate tasks to differentiate the methods of completion.

Use action buttons on pages or modals when tasks are underway and the only relevant choice for users is how to complete tasks. Do not display other inputs or choices until users select an action button. Then hide the action buttons or close the modals.

### ❌ Don't use when

Don't use an action button by itself. Action buttons should not serve as primary calls-to-action on pages where other actions are available to users.

Do not use actions buttons to present different methods of completing tasks before users initiate the tasks. Action buttons should not compete against other content for user attention.

Do not use action buttons when consequential choices are not made at the beginning of tasks. Instead, use a different selection input and progressive disclosure to reveal additional content as necessary. Likewise, do not use action buttons when the methods of completion in tasks differ only in minor ways such as an extra field or two. Action buttons represent consequential decisions where the methods of completion can start and end differently and can include entirely different steps and requirements.

## Behavior and states

### Task placement

Use action buttons inside modals when tasks mostly take place within modals. For example, when tasks create records or pages that do not exist until users complete the tasks, place action buttons in modals. This is common for add processes that have multiple methods of completion and only require standard modals to create records.

- Use the default-size modal for 2 action buttons, and use a large modal for 3 or more.
- Center the action buttons inside the modal and wrap to another row if needed.
- When the user selects a choice, dismiss this modal and open whatever container is appropriate for the remainder of the task.
- If users cancel or abandon the task, do not return to the modal.
- Always provide a "Cancel" action inside a modal with action buttons.

Use action buttons directly on pages or tabs that include add or configuration processes but no other tasks. Most add processes use the modal example above.

- If necessary, include a question above the action buttons to explain the decision being made.
- Center the question and action buttons inside the page.
- When users select one of the action buttons, replace them with the next step of the task.
- If users leave the page without selecting an action button, treat the record or process as "incomplete" and place any appropriate status indicators on its parent view.
- If it is useful to include an option for users to back out of configuration processes, place an explicit "Cancel" or "Delete" action under the action buttons.

Use action buttons directly inside tabs instead of modals when users add user-defined tabs and select how populate the content.

- A "Cancel" action under the action buttons is not necessary because users can remove user-defined tabs on the tab control.

## API Documentation

### Components and Directives

#### LayoutActionButtonBasicExampleComponent

**Selector:** `app-layout-action-button-basic-example`

**Package:** `@skyux/code-examples`

#### LayoutActionButtonPermalinkExampleComponent

**Selector:** `app-layout-action-button-permalink-example`

**Package:** `@skyux/code-examples`

#### SkyActionButtonContainerComponent

Wraps action buttons to ensures that they have consistent height and spacing.

**Selector:** `sky-action-button-container`

**Package:** `@skyux/layout`

**Inputs:**

- `alignItems`: `SkyActionButtonContainerAlignItemsType` - How to display the action buttons inside the action button container.
Options are `"center"` or `"left"`. (default: "center")

#### SkyActionButtonDetailsComponent

Specifies a description to display on an action button.

**Selector:** `sky-action-button-details`

**Package:** `@skyux/layout`

#### SkyActionButtonHeaderComponent

Specifies a header to display on an action button.

**Selector:** `sky-action-button-header`

**Package:** `@skyux/layout`

#### SkyActionButtonIconComponent

Specifies an icon to display on the action button.

**Selector:** `sky-action-button-icon`

**Package:** `@skyux/layout`

**Inputs:**

- `iconName`: `string` - The name of the Blackbaud SVG icon to display.

#### SkyActionButtonPermalink

Specifies an Angular router link with the `route` property or a direct
link with the `url` property. If it provides both, the action button uses
the `route` property.

**Package:** `@skyux/layout`

#### SkyActionButtonComponent

Creates a button to present users with an option to move forward with tasks.

**Selector:** `sky-action-button`

**Package:** `@skyux/layout`

**Inputs:**

- `permalink`: `SkyActionButtonPermalink | undefined` - The link for the action button.

**Outputs:**

- `actionClick`: `EventEmitter<any>` - Fires when users select the action button.

#### SkyActionButtonModule

**Package:** `@skyux/layout`

#### SkyActionButtonContainerAlignItemsType

**Package:** `@skyux/layout`

#### SkyActionButtonContainerAlignItems

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyActionButtonFixture

Allows interaction with a SKY UX action button component.

**Package:** `@skyux/layout/testing`

⚠️ **This component is deprecated.**

#### SkyActionButtonContainerHarnessFilters

A set of criteria that can be used to filter a list of `SkyActionButtonContainerHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyActionButtonContainerHarness

Harness for interacting with a action button container component in tests.

**Package:** `@skyux/layout/testing`

#### SkyActionButtonHarnessFilters

A set of criteria that can be used to filter a list of `SkyActionButtonHarness` instances.

**Package:** `@skyux/layout/testing`

#### SkyActionButtonHarness

Harness for interacting with a action button component in tests.

**Package:** `@skyux/layout/testing`

### Code Examples

#### Basic action buttons

**Selector:** `app-layout-action-button-basic-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyActionButtonModule } from '@skyux/layout';

/**
 * @title Basic action buttons
 */
@Component({
  selector: 'app-layout-action-button-basic-example',
  templateUrl: './example.component.html',
  imports: [SkyActionButtonModule],
})
export class LayoutActionButtonBasicExampleComponent {
  protected filterActionClick(): void {
    alert('Filter action clicked');
  }

  protected openActionClick(): void {
    alert('Open action clicked');
  }
}

```

**Template:**

```html
<sky-action-button-container>
  <sky-action-button (actionClick)="filterActionClick()">
    <sky-action-button-icon iconName="filter" />
    <sky-action-button-header> Build a new list </sky-action-button-header>
    <sky-action-button-details>
      Start from scratch and fine-tune with filters.
    </sky-action-button-details>
  </sky-action-button>

  <sky-action-button (actionClick)="openActionClick()">
    <sky-action-button-icon iconName="folder-open" />
    <sky-action-button-header> Open a saved list </sky-action-button-header>
    <sky-action-button-details>
      Open a list with filters saved in the web view.
    </sky-action-button-details>
  </sky-action-button>
</sky-action-button-container>

```

#### Action button with permalinks

**Selector:** `app-layout-action-button-permalink-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyActionButtonModule, SkyActionButtonPermalink } from '@skyux/layout';

/**
 * @title Action button with permalinks
 */
@Component({
  selector: 'app-layout-action-button-permalink-example',
  templateUrl: './example.component.html',
  imports: [SkyActionButtonModule],
})
export class LayoutActionButtonPermalinkExampleComponent {
  protected routerlink: SkyActionButtonPermalink = {
    route: {
      commands: [],
      extras: {
        queryParams: {
          component: 'MyComponent',
        },
      },
    },
  };

  protected url: SkyActionButtonPermalink = {
    url: 'https://www.stackblitz.com',
  };
}

```

**Template:**

```html
<sky-action-button-container>
  <sky-action-button [permalink]="url">
    <sky-action-button-icon iconName="link" />
    <sky-action-button-header> Open a link </sky-action-button-header>
    <sky-action-button-details> Open a link. </sky-action-button-details>
  </sky-action-button>

  <sky-action-button [permalink]="routerlink">
    <sky-action-button-icon iconName="link" />
    <sky-action-button-header> Open a router link </sky-action-button-header>
    <sky-action-button-details> Open a router link. </sky-action-button-details>
  </sky-action-button>
</sky-action-button-container>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.