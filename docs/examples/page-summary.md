---
component: 'page-summary'
type: 'code-examples'
description: 'Code examples for the page-summary component.'
---

# Page Summary Code Examples

## Page summary with basic setup

**Component:** LayoutPageSummaryBasicExampleComponent

**Selector:** `app-layout-page-summary-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

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

#### example.component.html

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

---