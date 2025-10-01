---
component: 'page-summary'
description: 'Design guidelines, API documentation, and usage instructions for the page-summary component extracted from SKY UX documentation.'
---

# Page Summary Component Guidelines

## Component Overview
The page summary displays critical information and actions for users to access quickly and frequently. Page summary is deprecated in favor of page's sky-page-header component. For more information, see the page summary deprecation instructions.

## Usage

### ✅ Use when

Use page summary effectively by limiting the number of items included. The page summary is prime real estate on the page, and when you limit the number of items, you magnify the impact of each one.

## Options

### Toolbar

Use the toolbar component a to add page summary actions in a SKY UX-themed toolbar. Only include actions that relate to the page as a whole, and exclude actions that are specific to the tiles on the page. Limit the number of actions in the toolbar. If the page summary requires many actions, re-examine the tasks and consider alternative workflows.

Display the toolbar below the page summary. Place frequently used actions directly in the toolbar, and place less-frequently used actions in a more actions menu. Actions to collapse and expand all tiles on the record are docked on the right side of the toolbar.

## Content

### Title and subtitle

You can display a title and subtitle in the summary to uniquely identify the page content. You can pull data for the title from multiple sources, and you can combine multiple pieces of data in the title. The data to use depends on your users and the context in which they visit the page. You can display additional information in the subtitle. For example, you can display a record's natural language name in the title and its system-generated or coded identifier in the subtitle.

### Image

You can display an image in the summary to help users identify a record or complete a core task. We recommend that you do not include images just for decorative purposes because they are likely to distract users and interfere with task completion.

### Status

You can display important status information about a page's content with labels in the status section of the page summary.

### Arbitrary content

You can highlight important information about a page's content in the key information section of the page summary. This section can display any type of content, but it generally highlights a key information block such as important summary numbers.

### Alert

You can display messages that require immediate attention as alerts within the page summary. For example, you can display system-generated messages when certain criteria are met.

## Related information

### Components

- Toolbar

## API Documentation

### Components and Directives

#### LayoutPageSummaryBasicExampleComponent

**Selector:** `app-layout-page-summary-basic-example`

**Package:** `@skyux/code-examples`

#### SkyPageSummaryAlertComponent

Displays messages that require immediate attention as [alerts](https://developer.blackbaud.com/skyux/components/alert) within
the page summary.

**Selector:** `sky-page-summary-alert`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyPageSummaryContentComponent

Displays content in the arbitrary section of the page summary.

**Selector:** `sky-page-summary-content`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyPageSummaryImageComponent

Displays an image in the page summary to identify a record
or help users complete a core task.

**Selector:** `sky-page-summary-image`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyPageSummaryKeyInfoComponent

Highlights important information about a page in the key information section of the
page summary.

**Selector:** `sky-page-summary-key-info`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyPageSummaryStatusComponent

Displays [labels](https://developer.blackbaud.com/skyux/components/label)
to highlight important status information about a page's content.

**Selector:** `sky-page-summary-status`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyPageSummarySubtitleComponent

Specifies a subtitle to identify the page content.

**Selector:** `sky-page-summary-subtitle`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyPageSummaryTitleComponent

Specifies a title to identify the page content.

**Selector:** `sky-page-summary-title`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyPageSummaryComponent

Specifies the components to display in the page summary.

**Selector:** `sky-page-summary`

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyPageSummaryModule

**Package:** `@skyux/layout`

⚠️ **This component is deprecated.**

#### SkyPageSummaryFixture

Allows interaction with a SKY UX page summary component.

**Package:** `@skyux/layout/testing`

⚠️ **This component is deprecated.**

### Code Examples

#### Page summary with basic setup

**Selector:** `app-layout-page-summary-basic-example`

**TypeScript:**

```typescript
import { Component } from '@angular/core';
import { FormsModule } from '@angular/forms';
import { SkyAvatarModule } from '@skyux/avatar';
import { SkyCheckboxModule } from '@skyux/forms';
import {
  SkyAlertModule,
  SkyKeyInfoModule,
  SkyLabelModule,
} from '@skyux/indicators';
import { SkyPageSummaryModule } from '@skyux/layout';

/**
 * @title Page summary with basic setup
 */
@Component({
  selector: 'app-layout-page-summary-basic-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    SkyAlertModule,
    SkyAvatarModule,
    SkyCheckboxModule,
    SkyKeyInfoModule,
    SkyLabelModule,
    SkyPageSummaryModule,
  ],
})
export class LayoutPageSummaryBasicExampleComponent {
  protected name = 'Robert C. Hernandez';
  protected showAlert = true;
  protected showContent = true;
  protected showImage = true;
  protected showKeyInfo = true;
  protected showStatus = true;
  protected showSubtitle = true;
  protected showTitle = true;
}

```

**Template:**

```html
<sky-page-summary>
  @if (showAlert) {
    <sky-page-summary-alert>
      <sky-alert alertType="info"> This is an alert. </sky-alert>
    </sky-page-summary-alert>
  }
  @if (showImage) {
    <sky-page-summary-image>
      <sky-avatar [name]="name" [canChange]="true" />
    </sky-page-summary-image>
  }
  @if (showTitle) {
    <sky-page-summary-title>
      {{ name }}
    </sky-page-summary-title>
  }
  @if (showSubtitle) {
    <sky-page-summary-subtitle> Board member </sky-page-summary-subtitle>
  }
  @if (showStatus) {
    <sky-page-summary-status>
      <sky-label labelType="success"> Fundraiser </sky-label>
      <sky-label> Inactive </sky-label>
    </sky-page-summary-status>
  }
  @if (showContent) {
    <sky-page-summary-content>
      This is the arbitrary content section. You can display any kind of content
      to complement the content on a page. We recommend that you display content
      to support the key tasks of users of users who visit the page. We also
      recommend that you keep in mind the context of how users will use the
      content and limit the amount of content to avoid overloading the summary.
    </sky-page-summary-content>
  }
  @if (showKeyInfo) {
    <sky-page-summary-key-info>
      <sky-key-info>
        <sky-key-info-value> $1,500 </sky-key-info-value>
        <sky-key-info-label> Largest gift </sky-key-info-label>
      </sky-key-info>
      <sky-key-info>
        <sky-key-info-value> 37 </sky-key-info-value>
        <sky-key-info-label> Total gifts </sky-key-info-label>
      </sky-key-info>
    </sky-page-summary-key-info>
  }
</sky-page-summary>

<ul class="sky-list-unstyled">
  <li>
    <sky-checkbox labelText="Show title" [(ngModel)]="showTitle" />
  </li>
  <li>
    <sky-checkbox labelText="Show subtitle" [(ngModel)]="showSubtitle" />
  </li>
  <li>
    <sky-checkbox labelText="Show image" [(ngModel)]="showImage" />
  </li>
  <li>
    <sky-checkbox labelText="Show record status" [(ngModel)]="showStatus" />
  </li>
  <li>
    <sky-checkbox labelText="Show key information" [(ngModel)]="showKeyInfo" />
  </li>
  <li>
    <sky-checkbox
      labelText="Show arbitrary content"
      [(ngModel)]="showContent"
    />
  </li>
  <li>
    <sky-checkbox labelText="Show alert" [(ngModel)]="showAlert" />
  </li>
</ul>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.