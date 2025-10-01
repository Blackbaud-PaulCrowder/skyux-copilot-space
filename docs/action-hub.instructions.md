---
component: 'action-hub'
description: 'Design guidelines, API documentation, and usage instructions for the action-hub component extracted from SKY UX documentation.'
---

# Action Hub Component Guidelines

## Component Overview
Action hubs direct user attention to important actions and provide quick access to common tasks. They aggregate entry points into tasks that might otherwise be spread across multiple pages.

## Usage

### ✅ Use when

Use action hubs to present prescriptive calls to action for things users must, should, or could do within an area of the system. They are often appropriate as landing pages for main navigation items but can also be descendant pages.

### ❌ Don't use when

Don't use action hubs to present information that is not actionable. Analyze information for users to provide context and make it actionable.

## Anatomy

- Page heading
- Related links
- Needs attention
- Recently accessed
- Content area
- Common actions
- Settings

## Options

### Common actions

You can include up to three secondary buttons to provide quick access to common tasks, such as adding a record. If you need to group multiple related actions, use a menu button.

## Content

### Needs attention

Display actions that users must perform based on business requirements or best practices, and link users to the place where they can complete the action, such as a modal, split view page, or record page.

Start each item in the list with a verb that communicates the action to perform. After the verb, include the number of items that require attention and a succinct description.

Order the items by workflow order, or by importance if they are not part of the same workflow.

### Content area

Additional content should reflect one of the following sets of principles.

#### Operational but optional

Content that is operational but optional should:

- be operational in nature, reflecting work that the user does on a regular basis to run the business
- provide contextual information to help the user decide whether to act
- be elevated to a needs attention item after a specific threshold is met

#### Strategic and prescriptive

Content that is strategic and prescriptive should:

- be strategic in nature, oriented towards longer term organizational goals rather than day to day tasks
- prescribe one or more actions which may take place inside or outside the system
- be synthesized and provide a context for comparison — don't require the user to figure out what the information means

#### Strategic and tied to a needs attention item

Content that is strategic and tied to a needs attention item should:

- be strategic in nature, oriented towards longer term organizational goals rather than day to day tasks
- represent progress towards an outcome that is impacted by a least one existing needs attention item
- be synthesized and provide a context for comparison — don't require the user to figure out what the information means

#### Key information call to action

Use key information calls to action when the condition for prescribing an action can be distilled to a single piece of information.

#### Charts

Action hubs are not intended for analytical tasks. If you include charts, scope the data set to the appropriate strategic or operational view for the user. You can use one filter if necessary to swap between relevant contexts.

### Page links

Groups of links to include and display in the following order.

#### Related links

Display up to 10 links to related pages in alphabetical order.

#### Recently accessed

Display up to five items in reverse chronological order to indicate what users accessed most recently.

#### Settings

Optionally include links to the settings applicable to functionality within the action hub and its descendant pages.

## Behavior and states

### Needs attention

#### Navigation

Link needs attention items to the place where users can complete the action, such as a modal, split view page, or record page.

#### Empty state

When no needs attention items are available, an empty state message indicates that users are caught up.

#### Columns

When more than six needs attention items are available in a viewpoint that is 768 pixels or larger, the content splits into two columns.

### Settings

Open settings forms in modals.

### Responsiveness

Action hubs reflow content in small viewports.

## Related information

### Guidelines

- Record page
- Split view page

### Components

- Modal

## API Documentation

### Components and Directives

#### PagesActionHubExampleComponent

**Selector:** `app-pages-action-hub-example`

**Package:** `@skyux/code-examples`

#### SkyActionHubButtonsComponent

Displays buttons after the page title.

**Selector:** `sky-action-hub-buttons`

**Package:** `@skyux/pages`

#### SkyActionHubContentComponent

Displays additional content after the action items.

**Selector:** `sky-action-hub-content`

**Package:** `@skyux/pages`

#### SkyActionHubComponent

Creates an action hub to direct user attention to important
actions and provide quick access to common tasks.

**Selector:** `sky-action-hub`

**Package:** `@skyux/pages`

**Inputs:**

- `parentLink`: `SkyPageLink | undefined` - Links back to a parent page.
- `recentLinks`: `SkyRecentLinksInput` - The list of recently accessed links, or `"loading"` to display a wait indicator. (default: [])
- `relatedLinks`: `SkyPageLinksInput` - The list of related links, or `"loading"` to display a wait indicator. (default: [])
- `settingsLinks`: `SkyPageModalLinksInput` - The list of settings with modal parameters, or `"loading"` to display a wait indicator. (default: [])
- `title`: `string` - The page title. (default: "")
- `needsAttention`: `SkyActionHubNeedsAttentionInput | undefined` - The list of actions that users must perform based on business requirements or best practices, or `"loading"` to display a wait indicator.

#### SkyActionHubModule

**Package:** `@skyux/pages`

#### SkyActionHubNeedsAttentionClickHandlerArgs

**Package:** `@skyux/pages`

#### SkyActionHubNeedsAttentionClickHandler

**Package:** `@skyux/pages`

#### SkyActionHubNeedsAttentionInput

A list of actions that users must perform based on business requirements or best practices.

**Package:** `@skyux/pages`

#### SkyActionHubNeedsAttention

Specifies action items that require attention and directs users to pages
where they can resolve them.

**Package:** `@skyux/pages`

#### SkyActionHubHarnessFilters

A set of criteria that can be used to filter a list of SkyActionHubHarness instances.

**Package:** `@skyux/pages/testing`

#### SkyActionHubHarness

Harness for interacting with an action hub component in tests.

**Package:** `@skyux/pages/testing`

### Code Examples

#### Action hub with basic setup

**Selector:** `app-pages-action-hub-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { SkyActionHubModule, SkyPageModalLinksInput } from '@skyux/pages';

import { MODAL_TITLE } from './modal-title-token';
import { SettingsModalComponent } from './settings-modal.component';

const pastHours = Array.from(Array(5).keys()).map((i) => {
  const date = new Date();
  date.setHours(date.getHours() - (i + 1));
  return date;
});

/**
 * @title Action hub with basic setup
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-action-hub-example',
  templateUrl: './example.component.html',
  imports: [SkyActionHubModule],
})
export class PagesActionHubExampleComponent {
  public buttons = [
    {
      label: 'Action 1',
      ariaLabel: 'Accounts action 1',
      permalink: {
        url: '#',
      },
    },
    {
      label: 'Action 2',
      ariaLabel: 'Accounts action 2',
      permalink: {
        url: '#',
      },
    },
    {
      label: 'Action 3',
      ariaLabel: 'Accounts action 3',
      permalink: {
        url: '#',
      },
    },
  ];

  public needsAttention = [
    {
      title: '9',
      message: 'updates from portal',
      permalink: {
        url: '#',
      },
    },
    {
      title: '8',
      message: 'new messages from online donation',
      permalink: {
        url: '#',
      },
    },
    {
      title: '7',
      message: 'possible duplicates from constituent lists',
      permalink: {
        url: '#',
      },
    },
    {
      title: '6',
      message: 'updates from portal',
      permalink: {
        url: '#',
      },
    },
    {
      title: '5',
      message: 'new messages from online donation',
      permalink: {
        url: '#',
      },
    },
    {
      title: '4',
      message: 'possible duplicates from constituent lists',
      permalink: {
        url: '#',
      },
    },
    {
      title: '3',
      message: 'update from portal',
      permalink: {
        url: '#',
      },
    },
    {
      title: '2',
      message: 'new messages from online donation',
      permalink: {
        url: '#',
      },
    },
    {
      title: '1',
      message: 'possible duplicate from constituent lists',
      permalink: {
        url: '#',
      },
    },
  ];

  public recentLinks = [
    {
      label: 'Recent 1',
      permalink: {
        url: '#',
      },
      lastAccessed: pastHours[0],
    },
    {
      label: 'Recent 2',
      permalink: {
        url: '#',
      },
      lastAccessed: pastHours[1],
    },
    {
      label: 'Recent 3',
      permalink: {
        url: '#',
      },
      lastAccessed: pastHours[2],
    },
    {
      label: 'Recent 4',
      permalink: {
        url: '#',
      },
      lastAccessed: pastHours[3],
    },
    {
      label: 'Recent 5',
      permalink: {
        url: '#',
      },
      lastAccessed: pastHours[4],
    },
  ];

  public relatedLinks = [
    {
      label: 'Link 1',
      permalink: {
        url: '#',
      },
    },
    {
      label: 'Link 2',
      permalink: {
        url: '#',
      },
    },
    {
      label: 'Link 3',
      permalink: {
        url: '#',
      },
    },
  ];

  public settingsLinks: SkyPageModalLinksInput = [
    {
      label: 'Number',
      modal: {
        component: SettingsModalComponent,
        config: {
          size: 'large',
          providers: [
            {
              provide: MODAL_TITLE,
              useValue: 'Number',
            },
          ],
        },
      },
    },
    {
      label: 'Color',
      modal: {
        component: SettingsModalComponent,
        config: {
          size: 'large',
          providers: [
            {
              provide: MODAL_TITLE,
              useValue: 'Color',
            },
          ],
        },
      },
    },
  ];

  public title = 'Active accounts';
}

```

**Template:**

```html
<sky-action-hub
  data-sky-id="action-hub"
  [needsAttention]="needsAttention"
  [recentLinks]="recentLinks"
  [relatedLinks]="relatedLinks"
  [settingsLinks]="settingsLinks"
  [title]="title"
>
  <sky-action-hub-buttons>
    @for (button of buttons; track button) {
      <a
        class="sky-btn sky-btn-default sky-margin-inline-sm"
        [attr.aria-label]="button.ariaLabel"
        [href]="button.permalink.url"
      >
        {{ button.label }}
      </a>
    }
  </sky-action-hub-buttons>

  <sky-action-hub-content>
    <h2 class="sky-font-heading-2">Additional content</h2>
    <p>More content can go here as needed for the functional area.</p>
  </sky-action-hub-content>
</sky-action-hub>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.