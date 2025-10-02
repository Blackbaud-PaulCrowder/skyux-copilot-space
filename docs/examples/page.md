---
component: 'page'
type: 'code-examples'
description: 'Code examples for the page component.'
---

# Page Code Examples

## Wait applied to a page

**Component:** IndicatorsWaitPageExampleComponent

**Selector:** `app-indicators-wait-page-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { SkyWaitHarness } from '@skyux/indicators/testing';

import { IndicatorsWaitPageExampleComponent } from './example.component';

describe('Page wait', () => {
  function setupTest(): {
    rootLoader: HarnessLoader;
    el: HTMLElement;
    fixture: ComponentFixture<IndicatorsWaitPageExampleComponent>;
  } {
    const fixture = TestBed.createComponent(IndicatorsWaitPageExampleComponent);
    const rootLoader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const el = fixture.nativeElement as HTMLElement;

    return { rootLoader, el, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [IndicatorsWaitPageExampleComponent],
    });
  });

  it('should show the page wait component when the user performs an action', async () => {
    const { rootLoader, el } = setupTest();

    const buttons = el.querySelectorAll<HTMLButtonElement>('.sky-btn');

    buttons[0].click();

    const waitHarness = await rootLoader.getHarness(
      SkyWaitHarness.with({ servicePageWaitType: 'blocking' }),
    );

    await expectAsync(waitHarness.isWaiting()).toBeResolvedTo(true);
    await expectAsync(waitHarness.isFullPage()).toBeResolvedTo(true);
    await expectAsync(waitHarness.isNonBlocking()).toBeResolvedTo(false);
  });

  it('should show the non-blocking page wait component when the user performs an action', async () => {
    const { rootLoader, el } = setupTest();

    const buttons = el.querySelectorAll<HTMLButtonElement>('.sky-btn');

    buttons[1].click();

    const waitHarness = await rootLoader.getHarness(
      SkyWaitHarness.with({ servicePageWaitType: 'non-blocking' }),
    );

    await expectAsync(waitHarness.isWaiting()).toBeResolvedTo(true);
    await expectAsync(waitHarness.isFullPage()).toBeResolvedTo(true);
    await expectAsync(waitHarness.isNonBlocking()).toBeResolvedTo(true);
  });
});

```

#### example.component.ts

```typescript
import { Component, OnDestroy, inject } from '@angular/core';
import { SkyWaitService } from '@skyux/indicators';

/**
 * @title Wait applied to a page
 */
@Component({
  standalone: true,
  selector: 'app-indicators-wait-page-example',
  templateUrl: './example.component.html',
})
export class IndicatorsWaitPageExampleComponent implements OnDestroy {
  protected isWaiting = false;

  readonly #waitSvc = inject(SkyWaitService);

  public ngOnDestroy(): void {
    this.#waitSvc.dispose();
  }

  protected togglePageWait(isBlocking: boolean): void {
    if (!this.isWaiting) {
      if (isBlocking) {
        this.#waitSvc.beginBlockingPageWait();
      } else {
        this.#waitSvc.beginNonBlockingPageWait();
      }
    } else if (isBlocking) {
      this.#waitSvc.endBlockingPageWait();
    } else {
      this.#waitSvc.endNonBlockingPageWait();
    }

    this.isWaiting = !this.isWaiting;
  }
}

```

#### example.component.html

```html
<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="togglePageWait(true)"
>
  Show page wait
</button>

<button
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="togglePageWait(false)"
>
  Show non-blocking page wait
</button>

```

---

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

## Action hub with basic setup

**Component:** PagesActionHubExampleComponent

**Selector:** `app-pages-action-hub-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ApplicationRef } from '@angular/core';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import {
  SkyModalTestingController,
  SkyModalTestingModule,
} from '@skyux/modals/testing';
import { SkyActionHubHarness } from '@skyux/pages/testing';

import { PagesActionHubExampleComponent } from './example.component';
import { SettingsModalComponent } from './settings-modal.component';

describe('Action hub', () => {
  async function setupTest(): Promise<{
    actionHubHarness: SkyActionHubHarness;
    fixture: ComponentFixture<PagesActionHubExampleComponent>;
    loader: HarnessLoader;
  }> {
    const fixture = TestBed.createComponent(PagesActionHubExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const actionHubHarness = await loader.getHarness(
      SkyActionHubHarness.with({
        dataSkyId: 'action-hub',
      }),
    );

    return { actionHubHarness, fixture, loader };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [PagesActionHubExampleComponent, SkyModalTestingModule],
    });
  });

  it('should have correct page title', async () => {
    const { actionHubHarness } = await setupTest();

    expect(await actionHubHarness.getTitle()).toBe('Active accounts');
  });

  it('should show needs-attention items', async () => {
    const { actionHubHarness } = await setupTest();

    expect(
      await actionHubHarness
        .getNeedsAttentionItems()
        .then(
          async (items) =>
            await Promise.all(items.map((item) => item.getText())),
        ),
    ).toEqual([
      '9 updates from portal',
      '8 new messages from online donation',
      '7 possible duplicates from constituent lists',
      '6 updates from portal',
      '5 new messages from online donation',
      '4 possible duplicates from constituent lists',
      '3 update from portal',
      '2 new messages from online donation',
      '1 possible duplicate from constituent lists',
    ]);
  });

  it('should show recent links', async () => {
    const { actionHubHarness } = await setupTest();

    const linkListHarness = await actionHubHarness.getRecentLinks();
    const listItems = await linkListHarness.getListItems();
    expect(await Promise.all(listItems.map((item) => item.getText()))).toEqual([
      'Recent 1',
      'Recent 2',
      'Recent 3',
      'Recent 4',
      'Recent 5',
    ]);
  });

  it('should show related links', async () => {
    const { actionHubHarness } = await setupTest();

    const linkListHarness = await actionHubHarness.getRelatedLinks();
    const listItems = await linkListHarness.getListItems();
    expect(await Promise.all(listItems.map((item) => item.getText()))).toEqual([
      'Link 1',
      'Link 2',
      'Link 3',
    ]);
  });

  it('should show settings links', async () => {
    const { actionHubHarness } = await setupTest();

    const linkListHarness = await actionHubHarness.getSettingsLinks();
    const listItems = await linkListHarness.getListItems();
    expect(await Promise.all(listItems.map((item) => item.getText()))).toEqual([
      'Number',
      'Color',
    ]);
    const modalController = TestBed.inject(SkyModalTestingController);
    modalController.expectNone();
    await listItems[0].click();
    const app = TestBed.inject(ApplicationRef);
    app.tick();
    await app.whenStable();
    modalController.expectCount(1);
    modalController.expectOpen(SettingsModalComponent);
  });
});

```

#### example.component.ts

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

#### modal-title-token.ts

```typescript
import { InjectionToken } from '@angular/core';

export const MODAL_TITLE = new InjectionToken<string>('MODAL_TITLE');

```

#### settings-modal.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyModalHarness } from '@skyux/modals/testing';
import { SkyActionHubHarness } from '@skyux/pages/testing';

import { PagesActionHubExampleComponent } from './example.component';
import { MODAL_TITLE } from './modal-title-token';

describe('SettingsModalComponent', () => {
  async function setupTest(): Promise<{
    actionHubHarness: SkyActionHubHarness;
    fixture: ComponentFixture<PagesActionHubExampleComponent>;
    loader: HarnessLoader;
    rootLoader: HarnessLoader;
  }> {
    const fixture = TestBed.createComponent(PagesActionHubExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const rootLoader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const actionHubHarness = await loader.getHarness(
      SkyActionHubHarness.with({
        dataSkyId: 'action-hub',
      }),
    );

    return { actionHubHarness, rootLoader, fixture, loader };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [PagesActionHubExampleComponent, NoopAnimationsModule],
      providers: [
        {
          provide: MODAL_TITLE,
          useValue: 'Settings Modal Test',
        },
      ],
    });
  });

  it('should show settings modal', async () => {
    const { actionHubHarness, rootLoader } = await setupTest();
    const settingsLinksHarness = await actionHubHarness.getSettingsLinks();
    const settingsLinks = await settingsLinksHarness.getListItems();
    expect(settingsLinks).toHaveSize(2);
    await settingsLinks[1].click();
    const modalHarness = await rootLoader.getHarness(
      SkyModalHarness.with({
        dataSkyId: 'settings-modal',
      }),
    );
    expect(await modalHarness.getHeadingText()).toBe('Color');
    const consoleSpy = spyOn(console, 'log').and.stub();
    const modalElement = TestbedHarnessEnvironment.getNativeElement(
      await modalHarness.host(),
    );
    const submit = modalElement.querySelector('button[type="submit"]');
    expect(submit).toBeTruthy();
    expect(submit?.textContent?.trim()).toBe('Save');
    (submit as HTMLButtonElement).click();
    expect(consoleSpy).toHaveBeenCalledWith({
      'Color 1': '',
      'Color 2': '',
      'Color 3': '',
      'Color 4': '',
      'Color 5': '',
    });
  });
});

```

#### settings-modal.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  AbstractControl,
  FormBuilder,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyColorpickerModule } from '@skyux/colorpicker';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyModalInstance, SkyModalModule } from '@skyux/modals';

import { MODAL_TITLE } from './modal-title-token';

@Component({
  selector: 'app-settings-modal',
  templateUrl: './settings-modal.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyColorpickerModule,
    SkyInputBoxModule,
    SkyModalModule,
  ],
})
export class SettingsModalComponent {
  protected formGroup: FormGroup;
  protected fields: string[] = [];

  protected readonly modalInstance = inject(SkyModalInstance);
  protected readonly title = inject(MODAL_TITLE);
  readonly #formBuilder = inject(FormBuilder);

  constructor() {
    const controls: Record<string, AbstractControl> = {};

    for (let i = 1; i <= 5; i++) {
      const field = `${this.title} ${i}`;
      this.fields.push(field);
      controls[field] = this.#formBuilder.control('');
    }

    this.formGroup = this.#formBuilder.group(controls);

    this.modalInstance.closed.subscribe((args) => {
      if (args.reason === 'save') {
        console.log(this.formGroup.value);
      }
    });
  }
}

```

#### example.component.html

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

#### settings-modal.component.html

```html
<form [formGroup]="formGroup" (submit)="modalInstance.save()">
  <sky-modal data-sky-id="settings-modal" [headingText]="title">
    <sky-modal-content>
      @for (field of fields; track field) {
        <ng-container class="row">
          @switch (title) {
            @case ('Color') {
              <sky-colorpicker #colorPicker stacked [labelText]="field">
                <input
                  type="text"
                  [formControlName]="field"
                  [skyColorpickerInput]="colorPicker"
                />
              </sky-colorpicker>
            }
            @default {
              <sky-input-box stacked [labelText]="field">
                <input type="text" [formControlName]="field" />
              </sky-input-box>
            }
          }
        </ng-container>
      }
    </sky-modal-content>
    <sky-modal-footer>
      <button
        class="sky-btn sky-btn-primary sky-margin-inline-sm"
        type="submit"
      >
        Save
      </button>
      <button
        class="sky-btn sky-btn-link"
        type="button"
        (click)="modalInstance.close()"
      >
        Close
      </button>
    </sky-modal-footer>
  </sky-modal>
</form>

```

---

## Home page with blocks layout, using tile dashboard and recently accessed links

**Component:** PagesPageHomePageBlocksLayoutExampleComponent

**Selector:** `app-pages-page-home-page-blocks-layout-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { provideRouter } from '@angular/router';
import { SkyHelpTestingModule } from '@skyux/core/testing';
import { SkyPageHarness } from '@skyux/pages/testing';

import { PagesPageHomePageBlocksLayoutExampleComponent } from './example.component';

describe('Record page blocks layout example', () => {
  async function setupTest(): Promise<{
    pageHarness: SkyPageHarness;
    fixture: ComponentFixture<PagesPageHomePageBlocksLayoutExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(
      PagesPageHomePageBlocksLayoutExampleComponent,
    );

    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const pageHarness = await loader.getHarness(SkyPageHarness);

    return { pageHarness, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        PagesPageHomePageBlocksLayoutExampleComponent,
        SkyHelpTestingModule,
        NoopAnimationsModule,
      ],
      providers: [provideRouter([])],
    });
  });

  it('should have a blocks layout', async () => {
    const { pageHarness, fixture } = await setupTest();

    fixture.detectChanges();

    await expectAsync(pageHarness.getLayout()).toBeResolvedTo('blocks');
  });

  it('should have the correct page header text', async () => {
    const { pageHarness } = await setupTest();

    const pageHeaderHarness = await pageHarness.getPageHeader();

    await expectAsync(pageHeaderHarness.getPageTitle()).toBeResolvedTo('Home');

    await expectAsync(
      pageHeaderHarness.getParentLinkText(),
    ).toBeRejectedWithError(/No parent link was found in the page header/);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyIconModule } from '@skyux/icon';
import { SkyPageModule, SkyRecentLink } from '@skyux/pages';

import { HomePageContentComponent } from './home-page-content.component';

/**
 * @title Home page with blocks layout, using tile dashboard and recently accessed links
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-page-home-page-blocks-layout-example',
  templateUrl: './example.component.html',
  imports: [HomePageContentComponent, SkyIconModule, SkyPageModule],
})
export class PagesPageHomePageBlocksLayoutExampleComponent {
  protected readonly recentLinks: SkyRecentLink[] = [
    {
      label: 'Gift Management',
      permalink: { url: '' },
      lastAccessed: new Date(2024, 1, 1),
    },
    {
      label: 'Reporting',
      permalink: { url: '' },
      lastAccessed: new Date(2024, 1, 2),
    },
  ];
}

```

#### home-page-content.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyTileDashboardConfig, SkyTilesModule } from '@skyux/tiles';

import { TileMyActionsComponent } from './tile-my-actions.component';
import { TileUpdatesComponent } from './tile-updates.component';

@Component({
  selector: 'app-home-page-content',
  templateUrl: './home-page-content.component.html',
  imports: [SkyTilesModule],
})
export class HomePageContentComponent {
  protected dashboardConfig: SkyTileDashboardConfig = {
    tiles: [
      {
        id: 'tile-updates',
        componentType: TileUpdatesComponent,
      },
      {
        id: 'tile-my-actions',
        componentType: TileMyActionsComponent,
      },
    ],
    layout: {
      singleColumn: {
        tiles: [
          {
            id: 'tile-updates',
            isCollapsed: false,
          },
          {
            id: 'tile-my-actions',
            isCollapsed: false,
          },
        ],
      },
      multiColumn: [
        {
          tiles: [
            {
              id: 'tile-updates',
              isCollapsed: false,
            },
          ],
        },
        {
          tiles: [
            {
              id: 'tile-my-actions',
              isCollapsed: false,
            },
          ],
        },
      ],
    },
  };
}

```

#### tile-my-actions.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyRepeaterModule } from '@skyux/lists';
import { SkyDropdownModule } from '@skyux/popovers';
import { SkyTilesModule } from '@skyux/tiles';

@Component({
  selector: 'app-tile-my-actions',
  styles: `
    :host {
      display: block;
    }
  `,
  templateUrl: './tile-my-actions.component.html',
  imports: [SkyTilesModule, SkyDropdownModule, SkyRepeaterModule],
})
export class TileMyActionsComponent {
  protected items: {
    date: string;
    status?: string;
    title?: string;
    accessibilityLabel?: string;
  }[] = [
    {
      title: 'Send invitation to Spring Ball',
      date: 'Today',
    },
    {
      title: 'Review portal activity',
      date: '10/2/2024',
    },
    {
      title: 'Assign prospects',
      date: '10/3/2024',
    },
  ];
  protected onActionClicked(buttonText: string): void {
    alert(buttonText + ' was clicked!');
  }
}

```

#### tile-updates.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyTilesModule } from '@skyux/tiles';

@Component({
  selector: 'app-tile-updates',
  styles: `
    :host {
      display: block;
    }
  `,
  templateUrl: './tile-updates.component.html',
  imports: [SkyTilesModule],
})
export class TileUpdatesComponent {}

```

#### example.component.html

```html
<sky-page layout="blocks">
  <sky-page-header pageTitle="Home">
    <sky-page-header-actions>
      <button type="button" class="sky-btn sky-btn-default">
        <sky-icon iconName="add" /> New
      </button>
    </sky-page-header-actions>
  </sky-page-header>
  <sky-page-content>
    <app-home-page-content />
  </sky-page-content>

  <sky-page-links>
    <sky-link-list-recently-accessed [recentLinks]="recentLinks" />
    <sky-link-list headingText="Resources">
      <sky-link-list-item>
        <a href="#">Help</a>
      </sky-link-list-item>
      <sky-link-list-item>
        <a href="#">Support</a>
      </sky-link-list-item>
      <sky-link-list-item>
        <a href="#">Training</a>
      </sky-link-list-item>
    </sky-link-list>
  </sky-page-links>
</sky-page>

```

#### home-page-content.component.html

```html
<sky-tile-dashboard [(config)]="dashboardConfig" />

```

#### tile-my-actions.component.html

```html
<sky-tile tileName="My actions">
  <sky-tile-title> My actions </sky-tile-title>
  <sky-tile-summary> 3 </sky-tile-summary>
  <sky-tile-content>
    <sky-tile-content-section>
      <sky-repeater data-sky-id="repeater-example">
        @for (item of items; track item) {
          <sky-repeater-item [itemName]="item.accessibilityLabel">
            @if (item.title) {
              <sky-repeater-item-title class="example-repeater-flex">
                <div class="example-repeater-item-title sky-margin-stacked-sm">
                  <a href="/">{{ item.title }}</a>
                </div>
                <div class="sky-font-deemphasized">{{ item.date }}</div>
              </sky-repeater-item-title>
            }
            <sky-repeater-item-context-menu>
              <sky-dropdown buttonType="context-menu">
                <sky-dropdown-menu>
                  <sky-dropdown-item>
                    <button
                      type="button"
                      [attr.aria-label]="
                        'Action 1 for ' +
                        (item.title ?? item.accessibilityLabel)
                      "
                      (click)="onActionClicked('Action 1')"
                    >
                      Edit
                    </button>
                  </sky-dropdown-item>
                  <sky-dropdown-item>
                    <button
                      type="button"
                      [attr.aria-label]="
                        'Action 2 for ' +
                        (item.title ?? item.accessibilityLabel)
                      "
                      (click)="onActionClicked('Action 2')"
                    >
                      Mark as complete
                    </button>
                  </sky-dropdown-item>
                </sky-dropdown-menu>
              </sky-dropdown>
            </sky-repeater-item-context-menu>
          </sky-repeater-item>
        }
      </sky-repeater>
    </sky-tile-content-section>
  </sky-tile-content>
</sky-tile>

```

#### tile-updates.component.html

```html
<sky-tile tileName="Updates" [showSettings]="false">
  <sky-tile-title> Updates </sky-tile-title>
  <sky-tile-summary> 2 </sky-tile-summary>
  <sky-tile-content>
    <sky-tile-content-section>
      <h3 class="sky-font-heading-3 sky-margin-stacked-sm">
        <a href="#">Prepare for Giving Tuesday</a>
      </h3>
      <div class="sky-font-deemphasized sky-margin-stacked-sm">10/1/2025</div>
      <div>
        Tips for creating a clear and compelling message, leveraging social
        media and email marketing, and providing multiple ways for donors to
        give.
      </div>
    </sky-tile-content-section>
    <sky-tile-content-section>
      <h3 class="sky-font-heading-3 sky-margin-stacked-sm">
        <a href="#">What's new</a>
      </h3>
      <div class="sky-font-deemphasized sky-margin-stacked-sm">9/28/2025</div>
      <ul>
        <li>Enhancement visualizations in reporting capabilities</li>
        <li>New automation for routine tasks</li>
        <li>Scan attachments for viruses</li>
      </ul>
    </sky-tile-content-section>
  </sky-tile-content>
</sky-tile>

```

---

## List page with list layout using data manager

**Component:** PagesPageListPageListLayoutExampleComponent

**Selector:** `app-pages-page-list-page-list-layout-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### dashboards-grid-context-menu.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyDropdownModule } from '@skyux/popovers';

import { ICellRendererAngularComp } from 'ag-grid-angular';
import { ICellRendererParams } from 'ag-grid-community';

import { Item } from './item';

@Component({
  selector: 'app-dashboards-grid-context-menu',
  templateUrl: './dashboards-grid-context-menu.component.html',
  imports: [SkyDropdownModule],
})
export class DashboardGridContextMenuComponent
  implements ICellRendererAngularComp
{
  protected dashboardName = '';

  public agInit(params: ICellRendererParams<Item>): void {
    this.dashboardName = params.data?.dashboard ?? '';
  }

  public refresh(): boolean {
    return false;
  }
}

```

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import {
  SkyHelpTestingController,
  SkyHelpTestingModule,
} from '@skyux/core/testing';
import { SkyPageHarness } from '@skyux/pages/testing';

import { PagesPageListPageListLayoutExampleComponent } from './example.component';

describe('List page list layout example', () => {
  async function setupTest(): Promise<{
    pageHarness: SkyPageHarness;
    fixture: ComponentFixture<PagesPageListPageListLayoutExampleComponent>;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(
      PagesPageListPageListLayoutExampleComponent,
    );

    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const pageHarness = await loader.getHarness(SkyPageHarness);
    const helpController = TestBed.inject(SkyHelpTestingController);

    return { pageHarness, fixture, helpController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        PagesPageListPageListLayoutExampleComponent,
        SkyHelpTestingModule,
        NoopAnimationsModule,
      ],
    });
  });

  it('should have a list layout', async () => {
    const { pageHarness } = await setupTest();

    await expectAsync(pageHarness.getLayout()).toBeResolvedTo('list');
  });

  it('should have the correct page header text', async () => {
    const { pageHarness } = await setupTest();

    const pageHeaderHarness = await pageHarness.getPageHeader();

    await expectAsync(pageHeaderHarness.getPageTitle()).toBeResolvedTo(
      'Dashboards',
    );
  });

  it('should have the correct help key', async () => {
    const { helpController } = await setupTest();

    helpController.expectCurrentHelpKey('example-help');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyPageModule } from '@skyux/pages';

import { ListPageContentComponent } from './list-page-content.component';

/**
 * @title List page with list layout using data manager
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-page-list-page-list-layout-example',
  templateUrl: './example.component.html',
  imports: [ListPageContentComponent, SkyPageModule],
})
export class PagesPageListPageListLayoutExampleComponent {}

```

#### item.ts

```typescript
export interface Item {
  dashboard: string;
  name: string;
  lastUpdated: string;
}

```

#### list-page-content.component.ts

```typescript
import { Component, OnInit, inject } from '@angular/core';
import { SkyAgGridModule, SkyAgGridService } from '@skyux/ag-grid';
import {
  SkyDataManagerModule,
  SkyDataManagerService,
  SkyDataManagerState,
  SkyDataViewConfig,
} from '@skyux/data-manager';
import { SkyIconModule } from '@skyux/icon';
import { SkyKeyInfoModule } from '@skyux/indicators';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ColDef,
  GridOptions,
  ICellRendererParams,
  ModuleRegistry,
} from 'ag-grid-community';

import { DashboardGridContextMenuComponent } from './dashboards-grid-context-menu.component';
import { Item } from './item';

ModuleRegistry.registerModules([AllCommunityModule]);

@Component({
  selector: 'app-list-page-content',
  templateUrl: './list-page-content.component.html',
  providers: [SkyDataManagerService],
  imports: [
    AgGridModule,
    SkyAgGridModule,
    SkyDataManagerModule,
    SkyIconModule,
    SkyKeyInfoModule,
  ],
})
export class ListPageContentComponent implements OnInit {
  protected items: Item[] = [
    {
      dashboard: 'Cash Flow Tracker',
      name: 'Kanesha Hutto',
      lastUpdated: '06/21/2023',
    },
    {
      dashboard: 'Accounts Receivable Dashboard',
      name: 'Kristeen Lunsford',
      lastUpdated: '06/30/2023',
    },
    {
      dashboard: 'Accounts Payable Dashboard',
      name: 'Darcel Lenz',
      lastUpdated: '04/20/2023',
    },
    {
      dashboard: 'Budget vs. Actual',
      name: 'Barbara Durr',
      lastUpdated: '12/04/2023',
    },
    {
      dashboard: 'Balance Sheet - New',
      name: 'Ilene Woo',
      lastUpdated: '12/20/2023',
    },
    {
      dashboard: 'Debt Management',
      name: 'Tonja Sanderson',
      lastUpdated: '09/10/2023',
    },
  ];

  protected gridOptions: GridOptions;

  #columnDefs: ColDef[] = [
    {
      colId: 'contextMenu',
      headerName: '',
      sortable: false,
      cellRenderer: DashboardGridContextMenuComponent,
      maxWidth: 55,
    },
    {
      colId: 'dashboard',
      field: 'dashboard',
      headerName: 'Name',
      width: 150,
      cellRenderer: (params: ICellRendererParams): string => {
        return `<a href="/">${params.value}</a>`;
      },
    },
    {
      colId: 'name',
      field: 'name',
      headerName: 'Created By',
    },
    {
      colId: 'lastUpdated',
      field: 'lastUpdated',
      headerName: 'Last Updated',
    },
  ];

  #viewConfig: SkyDataViewConfig = {
    id: 'gridView',
    name: 'Grid View',
    searchEnabled: true,
  };

  readonly #dataManagerService = inject(SkyDataManagerService);
  readonly #agGridSvc = inject(SkyAgGridService);

  constructor() {
    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions: {
        columnDefs: this.#columnDefs,
      },
    });
  }

  public ngOnInit(): void {
    this.#dataManagerService.initDataManager({
      activeViewId: 'gridView',
      dataManagerConfig: {},
      defaultDataState: new SkyDataManagerState({
        views: [
          {
            viewId: 'gridView',
            displayedColumnIds: [
              'contextMenu',
              'dashboard',
              'name',
              'lastUpdated',
            ],
          },
        ],
      }),
    });

    this.#dataManagerService.initDataView(this.#viewConfig);
  }
}

```

#### dashboards-grid-context-menu.component.html

```html
<sky-dropdown
  buttonType="context-menu"
  [label]="'context menu for ' + dashboardName"
>
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Edit ' + dashboardName">
        Edit
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Copy ' + dashboardName">
        Copy
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Delete ' + dashboardName">
        Delete
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

#### example.component.html

```html
<sky-page layout="list" helpKey="example-help">
  <sky-page-header pageTitle="Dashboards" />
  <sky-page-content>
    <app-list-page-content />
  </sky-page-content>
</sky-page>

```

#### list-page-content.component.html

```html
<sky-data-manager>
  <div class="sky-margin-stacked-xs">
    <sky-data-manager-toolbar>
      <sky-data-manager-toolbar-primary-item>
        <button
          aria-label="New dashboard"
          class="sky-btn sky-btn-default"
          type="button"
        >
          <sky-icon iconName="add" />
          New
        </button>
      </sky-data-manager-toolbar-primary-item>
    </sky-data-manager-toolbar>
  </div>
  <div class="sky-margin-stacked-sm">
    <sky-key-info class="sky-padding-horizontal-sm" layout="horizontal">
      <sky-key-info-value class="sky-font-display-4">
        {{ items.length }}
      </sky-key-info-value>
      <sky-key-info-label> Dashboards </sky-key-info-label>
    </sky-key-info>
  </div>
  <sky-data-view skyAgGridDataManagerAdapter viewId="gridView">
    <sky-ag-grid-wrapper>
      <ag-grid-angular [gridOptions]="gridOptions" [rowData]="items" />
    </sky-ag-grid-wrapper>
  </sky-data-view>
</sky-data-manager>

```

---

## List page with tabs layout using data manager

**Component:** PagesPageListPageTabsLayoutExampleComponent

**Selector:** `app-pages-page-list-page-tabs-layout-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### contact-context-menu.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyDropdownModule } from '@skyux/popovers';

import { ICellRendererAngularComp } from 'ag-grid-angular';
import { ICellRendererParams } from 'ag-grid-community';

import { Contact } from './contact';

@Component({
  selector: 'app-contacts-grid-context-menu',
  templateUrl: './contact-context-menu.component.html',
  imports: [SkyDropdownModule],
})
export class ContactContextMenuComponent implements ICellRendererAngularComp {
  protected contactName = '';

  public agInit(params: ICellRendererParams<Contact>): void {
    this.contactName = params.data?.name ?? '';
  }

  public refresh(): boolean {
    return false;
  }
}

```

#### contact.ts

```typescript
export interface Contact {
  name: string;
  organization: string;
  emailAddress: string;
}

```

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { provideRouter } from '@angular/router';
import {
  SkyHelpTestingController,
  SkyHelpTestingModule,
} from '@skyux/core/testing';
import { SkyPageHarness } from '@skyux/pages/testing';

import { PagesPageListPageTabsLayoutExampleComponent } from './example.component';

describe('List page tabs layout example', () => {
  async function setupTest(): Promise<{
    pageHarness: SkyPageHarness;
    fixture: ComponentFixture<PagesPageListPageTabsLayoutExampleComponent>;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(
      PagesPageListPageTabsLayoutExampleComponent,
    );

    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const pageHarness = await loader.getHarness(SkyPageHarness);
    const helpController = TestBed.inject(SkyHelpTestingController);

    return { pageHarness, fixture, helpController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        PagesPageListPageTabsLayoutExampleComponent,
        SkyHelpTestingModule,
        NoopAnimationsModule,
      ],
      providers: [provideRouter([])],
    });
  });

  it('should have a tabs layout', async () => {
    const { pageHarness } = await setupTest();

    await expectAsync(pageHarness.getLayout()).toBeResolvedTo('tabs');
  });

  it('should have the correct page header text', async () => {
    const { pageHarness } = await setupTest();

    const pageHeaderHarness = await pageHarness.getPageHeader();

    await expectAsync(pageHeaderHarness.getPageTitle()).toBeResolvedTo(
      'Contacts',
    );
  });

  it('should have the correct help key', async () => {
    const { helpController } = await setupTest();

    helpController.expectCurrentHelpKey('example-help');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyPageModule } from '@skyux/pages';

import { ListPageContentComponent } from './list-page-content.component';

/**
 * @title List page with tabs layout using data manager
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-page-list-page-tabs-layout-example',
  templateUrl: './example.component.html',
  imports: [ListPageContentComponent, SkyPageModule],
})
export class PagesPageListPageTabsLayoutExampleComponent {}

```

#### list-page-contacts-grid.component.ts

```typescript
import { Component, Input, OnInit, inject } from '@angular/core';
import { SkyAgGridModule, SkyAgGridService } from '@skyux/ag-grid';
import {
  SkyDataManagerModule,
  SkyDataManagerService,
  SkyDataManagerState,
  SkyDataViewConfig,
} from '@skyux/data-manager';
import { SkyIconModule } from '@skyux/icon';
import { SkyKeyInfoModule } from '@skyux/indicators';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ColDef,
  GridOptions,
  ICellRendererParams,
  ModuleRegistry,
} from 'ag-grid-community';

import { ContactContextMenuComponent } from './contact-context-menu.component';

ModuleRegistry.registerModules([AllCommunityModule]);

interface Contact {
  name: string;
  organization: string;
  emailAddress: string;
}

@Component({
  selector: 'app-list-page-contacts-grid',
  templateUrl: './list-page-contacts-grid.component.html',
  providers: [SkyDataManagerService],
  imports: [
    AgGridModule,
    SkyAgGridModule,
    SkyDataManagerModule,
    SkyIconModule,
    SkyKeyInfoModule,
  ],
})
export class ListPageContactsGridComponent implements OnInit {
  @Input()
  public contacts: Contact[] = [];

  protected gridOptions: GridOptions;

  #dataManagerService = inject(SkyDataManagerService);
  #agGridSvc = inject(SkyAgGridService);

  #columnDefs: ColDef[] = [
    {
      colId: 'contextMenu',
      headerName: '',
      sortable: false,
      cellRenderer: ContactContextMenuComponent,
      maxWidth: 55,
    },
    {
      colId: 'name',
      field: 'name',
      headerName: 'Name',
      width: 150,
      cellRenderer: (params: ICellRendererParams): string => {
        return `<a href="/">${params.value}</a>`;
      },
    },
    {
      colId: 'organization',
      field: 'organization',
      headerName: 'Organization',
    },
    {
      colId: 'emailAddress',
      field: 'emailAddress',
      headerName: 'Email Address',
    },
  ];

  #viewConfig: SkyDataViewConfig = {
    id: 'gridView',
    name: 'Grid View',
    searchEnabled: true,
    columnPickerEnabled: true,
    columnOptions: [
      { id: 'contextMenu', label: 'Context menu', alwaysDisplayed: true },
      { id: 'name', label: 'Name' },
      { id: 'organization', label: 'Organization' },
      { id: 'emailAddress', label: 'Email Address' },
    ],
  };

  constructor() {
    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions: {
        columnDefs: this.#columnDefs,
      },
    });
  }

  public ngOnInit(): void {
    this.#dataManagerService.initDataManager({
      activeViewId: 'gridView',
      dataManagerConfig: {},
      defaultDataState: new SkyDataManagerState({
        views: [
          {
            viewId: 'gridView',
            displayedColumnIds: [
              'contextMenu',
              'name',
              'organization',
              'emailAddress',
            ],
          },
        ],
      }),
    });

    this.#dataManagerService.initDataView(this.#viewConfig);
  }
}

```

#### list-page-content.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyTabIndex, SkyTabsModule } from '@skyux/tabs';

import { Contact } from './contact';
import { ListPageContactsGridComponent } from './list-page-contacts-grid.component';

@Component({
  selector: 'app-list-page-content',
  templateUrl: './list-page-content.component.html',
  imports: [ListPageContactsGridComponent, SkyTabsModule],
})
export class ListPageContentComponent {
  protected activeTabIndex: SkyTabIndex = 0;

  protected myContacts: Contact[] = [
    {
      name: 'Wonda Lumpkin',
      organization: 'Riverfront College of the Arts',
      emailAddress: 'wlumpkin@yahoo.com',
    },
    {
      name: 'Eliza Vanhorn',
      organization: 'Summit School of the Arts',
      emailAddress: 'evanhorn@outlook.com',
    },
    {
      name: 'Ed Sipes',
      organization: 'Reflections Middle School',
      emailAddress: 'esipes@yahoo.com',
    },
    {
      name: 'Elwood Farris',
      organization: 'Sandy Lagoon College',
      emailAddress: 'elfarris@gmail.com',
    },
    {
      name: 'Cristen Sizemore',
      organization: 'Grafton Vision Health',
      emailAddress: 'cristen.sizemore@aol.com',
    },
    {
      name: 'Latrice Ashmore',
      organization: 'Food Bank of Rapid City',
      emailAddress: 'lashmore@gmail.com',
    },
  ];

  protected allContacts = [
    ...this.myContacts,
    {
      name: 'Kanesha Hutto',
      organization: 'Los Angeles College of the Arts',
      emailAddress: 'khutto@yahoo.com',
    },
    {
      name: 'Kristeen Lunsford',
      organization: 'Food Bank of Los Angeles',
      emailAddress: 'kristeen.lunsford@yahoo.com',
    },
    {
      name: 'Barbara Durr',
      organization: 'Riverfront Middle School',
      emailAddress: 'bdurr@gmail.com',
    },
    {
      name: 'Ilene Woo',
      organization: 'Rapid City High School',
      emailAddress: 'ilene.woo@aol.com',
    },
    {
      name: 'Darcel Lenz',
      organization: 'Riverfront College of the Arts',
      emailAddress: 'dlenz@yahoo.com',
    },
  ];
}

```

#### contact-context-menu.component.html

```html
<sky-dropdown
  buttonType="context-menu"
  [label]="'context menu for ' + contactName"
>
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Edit ' + contactName">
        Edit
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Delete ' + contactName">
        Delete
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

#### example.component.html

```html
<sky-page layout="tabs" helpKey="example-help">
  <sky-page-header pageTitle="Contacts" />
  <sky-page-content>
    <app-list-page-content />
  </sky-page-content>
</sky-page>

```

#### list-page-contacts-grid.component.html

```html
<sky-data-manager>
  <div class="sky-margin-stacked-xs">
    <sky-data-manager-toolbar>
      <sky-data-manager-toolbar-primary-item>
        <button
          aria-label="New contact"
          class="sky-btn sky-btn-default"
          type="button"
        >
          <sky-icon iconName="add" />
          New
        </button>
      </sky-data-manager-toolbar-primary-item>
    </sky-data-manager-toolbar>
  </div>
  <div class="sky-margin-stacked-sm">
    <sky-key-info layout="horizontal" class="sky-padding-horizontal-sm">
      <sky-key-info-value class="sky-font-display-4">
        {{ contacts.length }}
      </sky-key-info-value>
      <sky-key-info-label> Contacts </sky-key-info-label>
    </sky-key-info>
  </div>
  <sky-data-view skyAgGridDataManagerAdapter viewId="gridView">
    <sky-ag-grid-wrapper>
      <ag-grid-angular [gridOptions]="gridOptions" [rowData]="contacts" />
    </sky-ag-grid-wrapper>
  </sky-data-view>
</sky-data-manager>

```

#### list-page-content.component.html

```html
<sky-tabset [(active)]="activeTabIndex">
  <sky-tab tabHeading="My contacts" layout="list">
    @if (activeTabIndex === 0) {
      <app-list-page-contacts-grid [contacts]="myContacts" />
    }
  </sky-tab>
  <sky-tab tabHeading="All contacts" layout="list">
    @if (activeTabIndex === 1) {
      <app-list-page-contacts-grid [contacts]="allContacts" />
    }
  </sky-tab>
</sky-tabset>

```

---

## Record page with blocks layout using box components

**Component:** PagesPageRecordPageBlocksLayoutExampleComponent

**Selector:** `app-pages-page-record-page-blocks-layout-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { provideRouter } from '@angular/router';
import {
  SkyHelpTestingController,
  SkyHelpTestingModule,
} from '@skyux/core/testing';
import { SkyPageHarness } from '@skyux/pages/testing';

import { PagesPageRecordPageBlocksLayoutExampleComponent } from './example.component';

describe('Record page blocks layout example', () => {
  async function setupTest(): Promise<{
    pageHarness: SkyPageHarness;
    fixture: ComponentFixture<PagesPageRecordPageBlocksLayoutExampleComponent>;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(
      PagesPageRecordPageBlocksLayoutExampleComponent,
    );

    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const pageHarness = await loader.getHarness(SkyPageHarness);
    const helpController = TestBed.inject(SkyHelpTestingController);

    return { pageHarness, fixture, helpController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        PagesPageRecordPageBlocksLayoutExampleComponent,
        SkyHelpTestingModule,
        NoopAnimationsModule,
      ],
      providers: [provideRouter([])],
    });
  });

  it('should have a blocks layout', async () => {
    const { pageHarness, fixture } = await setupTest();

    fixture.detectChanges();

    await expectAsync(pageHarness.getLayout()).toBeResolvedTo('blocks');
  });

  it('should have the correct page header text', async () => {
    const { pageHarness } = await setupTest();

    const pageHeaderHarness = await pageHarness.getPageHeader();

    await expectAsync(pageHeaderHarness.getPageTitle()).toBeResolvedTo(
      '$500 pledge',
    );

    await expectAsync(pageHeaderHarness.getParentLinkText()).toBeResolvedTo(
      'Pledges',
    );
  });

  it('should have the correct help key', async () => {
    const { helpController } = await setupTest();

    helpController.expectCurrentHelpKey('example-help');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyPageModule } from '@skyux/pages';

import { RecordPageContentComponent } from './record-page-content.component';

/**
 * @title Record page with blocks layout using box components
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-page-record-page-blocks-layout-example',
  templateUrl: './example.component.html',
  imports: [RecordPageContentComponent, SkyPageModule],
})
export class PagesPageRecordPageBlocksLayoutExampleComponent {
  protected readonly recentLinks = [
    {
      label: 'Gift Management',
      permalink: { url: '' },
      lastAccessed: new Date(2024, 1, 1),
    },
    {
      label: 'Reporting',
      permalink: { url: '' },
      lastAccessed: new Date(2024, 1, 2),
    },
  ];
}

```

#### record-page-content.component.ts

```typescript
import { CommonModule } from '@angular/common';
import { Component } from '@angular/core';
import { SkyIconModule } from '@skyux/icon';
import { SkyKeyInfoModule } from '@skyux/indicators';
import {
  SkyBoxModule,
  SkyDescriptionListModule,
  SkyFluidGridModule,
} from '@skyux/layout';
import { SkyRepeaterModule } from '@skyux/lists';

@Component({
  selector: 'app-record-page-content',
  templateUrl: './record-page-content.component.html',
  styleUrls: ['./record-page-content.component.scss'],
  imports: [
    CommonModule,
    SkyBoxModule,
    SkyDescriptionListModule,
    SkyFluidGridModule,
    SkyIconModule,
    SkyKeyInfoModule,
    SkyRepeaterModule,
  ],
})
export class RecordPageContentComponent {
  protected recordDetails = [
    {
      detail: 'Designation',
      info: 'General operating',
    },
    {
      detail: 'Source',
      info: 'Online donation form',
    },
    {
      detail: 'Status',
      info: 'Active',
    },
    {
      detail: 'Due date',
      info: '12/12/2023',
    },
    {
      detail: 'Create date',
      info: '01/05/2023',
    },
    {
      detail: 'Frequency',
      info: 'Quarterly',
    },
  ];

  protected actualPayments = [
    {
      category: 'Amount',
      value: '$845.00',
    },
    {
      category: 'Assigned',
      value: '$800.00',
    },
    {
      category: 'Applied',
      value: '$800.00',
    },
    {
      category: 'Payments',
      value: 25,
    },
  ];

  protected projectedPayments = [
    {
      category: 'Amount',
      value: '$0',
    },
    {
      category: 'Line items',
      value: 0,
    },
  ];

  protected recentActivity = [
    {
      activity: '$250.00 payment processed successfully.',
      date: '07/01/2023 12:02 am',
    },
    {
      activity: '$150.00 payment processed successfully.',
      date: '06/15/2023 12:02 am',
    },
    {
      activity: '$250.00 payment processed successfully.',
      date: '04/01/2023 12:02 am',
    },
  ];
}

```

#### example.component.html

```html
<sky-page layout="blocks" helpKey="example-help">
  <sky-page-header
    pageTitle="$500 pledge"
    [parentLink]="{
      label: 'Pledges',
      permalink: {
        route: {
          commands: ['/']
        }
      }
    }"
  />
  <sky-page-content>
    <app-record-page-content />
  </sky-page-content>
  <sky-page-links>
    <sky-link-list-recently-accessed [recentLinks]="recentLinks" />
    <sky-link-list headingText="Related links">
      <sky-link-list-item>
        <a href="#">Analysis</a>
      </sky-link-list-item>
      <sky-link-list-item>
        <a href="#">Tools</a>
      </sky-link-list-item>
      <sky-link-list-item>
        <button type="button" class="sky-btn-link-inline">Settings</button>
      </sky-link-list-item>
    </sky-link-list>
  </sky-page-links>
</sky-page>

```

#### record-page-content.component.html

```html
<sky-fluid-grid gutterSize="medium" [disableMargin]="true">
  <sky-row>
    <sky-column [screenMedium]="4" [screenSmall]="12">
      <sky-box class="sky-margin-stacked-xl" headingText="Details">
        <sky-box-controls>
          <button
            aria-label="Edit button for details"
            class="sky-btn sky-btn-icon-borderless"
            type="button"
          >
            <sky-icon iconName="edit" />
          </button>
        </sky-box-controls>
        <sky-box-content>
          <sky-description-list mode="vertical">
            @for (recordDetail of recordDetails; track recordDetail.detail) {
              <sky-description-list-content>
                <sky-description-list-term>
                  {{ recordDetail.detail }}
                </sky-description-list-term>
                <sky-description-list-description>
                  {{ recordDetail.info }}
                </sky-description-list-description>
              </sky-description-list-content>
            }
          </sky-description-list>
        </sky-box-content>
      </sky-box>
    </sky-column>
    <sky-column [screenMedium]="4" [screenSmall]="12">
      <sky-box class="sky-margin-stacked-xl" headingText="Payments">
        <sky-box-content>
          <div class="box-2-content">
            <div class="box-2-actuals">
              <h3 class="sky-font-heading-4">Actuals</h3>
              @for (
                actual of actualPayments;
                track actual.category;
                let i = $index
              ) {
                <sky-key-info
                  [ngClass]="{
                    'sky-margin-stacked-lg': i < actualPayments.length - 1
                  }"
                >
                  <sky-key-info-value class="sky-font-display-3">
                    {{ actual.value }}
                  </sky-key-info-value>
                  <sky-key-info-label>{{ actual.category }}</sky-key-info-label>
                </sky-key-info>
              }
            </div>
            <div class="box-2-projected">
              <h3 class="sky-font-heading-4">Projected</h3>
              @for (
                projected of projectedPayments;
                track projected;
                let i = $index
              ) {
                <sky-key-info
                  [ngClass]="{
                    'sky-margin-stacked-lg': i < projectedPayments.length - 1
                  }"
                >
                  <sky-key-info-value class="sky-font-display-3">
                    {{ projected.value }}
                  </sky-key-info-value>
                  <sky-key-info-label>
                    {{ projected.category }}
                  </sky-key-info-label>
                </sky-key-info>
              }
            </div>
          </div>
        </sky-box-content>
      </sky-box>
    </sky-column>
    <sky-column [screenMedium]="4" [screenSmall]="12">
      <sky-box headingText="Recent activity">
        <sky-box-content>
          <sky-repeater>
            @for (activity of recentActivity; track activity.activity) {
              <sky-repeater-item>
                <sky-repeater-item-content>
                  <div class="sky-margin-stacked-xs">
                    {{ activity.activity }}
                  </div>
                  <div class="sky-font-deemphasized">{{ activity.date }}</div>
                </sky-repeater-item-content>
              </sky-repeater-item>
            }
          </sky-repeater>
        </sky-box-content>
      </sky-box>
    </sky-column>
  </sky-row>
</sky-fluid-grid>

```

#### record-page-content.component.scss

```css
.box-2-content {
  display: flex;

  div {
    display: flex;
    flex-direction: column;
    flex-grow: 1;
  }

  .box-2-actuals {
    margin-right: 60px;
  }
}

```

---

## Record page with tabs layout using data manager

**Component:** PagesPageRecordPageTabsLayoutExampleComponent

**Selector:** `app-pages-page-record-page-tabs-layout-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### attachment.ts

```typescript
export interface Attachment {
  name: string;
  description: string;
  size: string;
  dateAdded: string;
}

```

#### attachments-grid-context-menu.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyDropdownModule } from '@skyux/popovers';

import { ICellRendererAngularComp } from 'ag-grid-angular';
import { ICellRendererParams } from 'ag-grid-community';

import { Attachment } from './attachment';

@Component({
  selector: 'app-attachments-grid-context-menu',
  templateUrl: './attachments-grid-context-menu.component.html',
  imports: [SkyDropdownModule],
})
export class AttachmentsGridContextMenuComponent
  implements ICellRendererAngularComp
{
  protected attachmentName = '';

  public agInit(params: ICellRendererParams<Attachment>): void {
    this.attachmentName = params.data?.name ?? '';
  }

  public refresh(): boolean {
    return false;
  }
}

```

#### detail.ts

```typescript
export interface Detail {
  detail: string;
  info: string;
}

```

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { provideRouter } from '@angular/router';
import {
  SkyHelpTestingController,
  SkyHelpTestingModule,
} from '@skyux/core/testing';
import { SkyPageHarness } from '@skyux/pages/testing';

import { PagesPageRecordPageTabsLayoutExampleComponent } from './example.component';

describe('Record page tabs layout example', () => {
  async function setupTest(): Promise<{
    pageHarness: SkyPageHarness;
    fixture: ComponentFixture<PagesPageRecordPageTabsLayoutExampleComponent>;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(
      PagesPageRecordPageTabsLayoutExampleComponent,
    );

    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const pageHarness = await loader.getHarness(SkyPageHarness);
    const helpController = TestBed.inject(SkyHelpTestingController);

    return { pageHarness, fixture, helpController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        PagesPageRecordPageTabsLayoutExampleComponent,
        SkyHelpTestingModule,
        NoopAnimationsModule,
      ],
      providers: [provideRouter([])],
    });
  });

  it('should have a tabs layout', async () => {
    const { pageHarness, fixture } = await setupTest();

    fixture.detectChanges();

    await expectAsync(pageHarness.getLayout()).toBeResolvedTo('tabs');
  });

  it('should have the correct page header text', async () => {
    const { pageHarness } = await setupTest();

    const pageHeaderHarness = await pageHarness.getPageHeader();

    await expectAsync(pageHeaderHarness.getPageTitle()).toBeResolvedTo(
      'Charlene Conners',
    );
  });

  it('should have the correct help key', async () => {
    const { helpController } = await setupTest();

    helpController.expectCurrentHelpKey('example-help');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyAvatarModule } from '@skyux/avatar';
import { SkyAlertModule, SkyLabelModule } from '@skyux/indicators';
import { SkyPageModule } from '@skyux/pages';

import { RecordPageContentComponent } from './record-page-content.component';

/**
 * @title Record page with tabs layout using data manager
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-page-record-page-tabs-layout-example',
  templateUrl: './example.component.html',
  imports: [
    RecordPageContentComponent,
    SkyAlertModule,
    SkyAvatarModule,
    SkyLabelModule,
    SkyPageModule,
  ],
})
export class PagesPageRecordPageTabsLayoutExampleComponent {}

```

#### record-page-attachments-tab.component.ts

```typescript
import { Component, OnInit, inject } from '@angular/core';
import { SkyAgGridModule, SkyAgGridService } from '@skyux/ag-grid';
import {
  SkyDataManagerModule,
  SkyDataManagerService,
  SkyDataManagerState,
  SkyDataViewConfig,
} from '@skyux/data-manager';
import { SkyIconModule } from '@skyux/icon';
import { SkyKeyInfoModule } from '@skyux/indicators';

import { AgGridModule } from 'ag-grid-angular';
import {
  AllCommunityModule,
  ColDef,
  GridOptions,
  ICellRendererParams,
  ModuleRegistry,
} from 'ag-grid-community';

import { Attachment } from './attachment';
import { AttachmentsGridContextMenuComponent } from './attachments-grid-context-menu.component';

ModuleRegistry.registerModules([AllCommunityModule]);

@Component({
  selector: 'app-record-page-attachments-tab',
  templateUrl: './record-page-attachments-tab.component.html',
  providers: [SkyDataManagerService],
  imports: [
    AgGridModule,
    SkyAgGridModule,
    SkyDataManagerModule,
    SkyKeyInfoModule,
    SkyIconModule,
  ],
})
export class RecordPageAttachmentsTabComponent implements OnInit {
  protected items: Attachment[] = [
    {
      name: 'Agreement.pdf',
      description: 'Cardholder agreement',
      size: '10 KB',
      dateAdded: '01/28/2023',
    },
    {
      name: 'Appendix.pdf',
      description: 'Updated terms 2023',
      size: '25 KB',
      dateAdded: '05/05/2023',
    },
  ];
  protected gridOptions: GridOptions;

  #dataManagerService = inject(SkyDataManagerService);
  #agGridSvc = inject(SkyAgGridService);

  #columnDefs: ColDef[] = [
    {
      colId: 'contextMenu',
      headerName: '',
      sortable: false,
      cellRenderer: AttachmentsGridContextMenuComponent,
      maxWidth: 55,
    },
    {
      colId: 'name',
      field: 'name',
      headerName: 'Name',
      width: 150,
      cellRenderer: (params: ICellRendererParams): string => {
        return `<a href="/">${params.value}</a>`;
      },
    },
    {
      colId: 'description',
      field: 'description',
      headerName: 'Description',
    },
    {
      colId: 'size',
      field: 'size',
      headerName: 'Size',
    },
    {
      colId: 'dateAdded',
      field: 'dateAdded',
      headerName: 'Date Added',
    },
  ];

  #viewConfig: SkyDataViewConfig = {
    id: 'gridView',
    name: 'Grid View',
    searchEnabled: true,
  };

  constructor() {
    this.gridOptions = this.#agGridSvc.getGridOptions({
      gridOptions: {
        columnDefs: this.#columnDefs,
      },
    });
  }

  public ngOnInit(): void {
    this.#dataManagerService.initDataManager({
      activeViewId: 'gridView',
      dataManagerConfig: {},
      defaultDataState: new SkyDataManagerState({
        views: [
          {
            viewId: 'gridView',
            displayedColumnIds: [
              'contextMenu',
              'name',
              'description',
              'size',
              'dateAdded',
            ],
          },
        ],
      }),
    });

    this.#dataManagerService.initDataView(this.#viewConfig);
  }
}

```

#### record-page-content.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyTabIndex, SkyTabsModule } from '@skyux/tabs';

import { RecordPageAttachmentsTabComponent } from './record-page-attachments-tab.component';
import { RecordPageNotesTabComponent } from './record-page-notes-tab.component';
import { RecordPageOverviewTabComponent } from './record-page-overview-tab.component';

@Component({
  selector: 'app-record-page-content',
  templateUrl: './record-page-content.component.html',
  imports: [
    RecordPageAttachmentsTabComponent,
    RecordPageNotesTabComponent,
    RecordPageOverviewTabComponent,
    SkyTabsModule,
  ],
})
export class RecordPageContentComponent {
  protected activeTabIndex: SkyTabIndex = 0;
}

```

#### record-page-notes-tab.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyIconModule } from '@skyux/icon';
import { SkyKeyInfoModule } from '@skyux/indicators';
import { SkyToolbarModule } from '@skyux/layout';
import { SkyRepeaterModule, SkySortModule } from '@skyux/lists';
import { SkySearchModule } from '@skyux/lookup';
import { SkyDropdownModule } from '@skyux/popovers';

@Component({
  selector: 'app-record-page-notes-tab',
  templateUrl: './record-page-notes-tab.component.html',
  imports: [
    SkyDropdownModule,
    SkyIconModule,
    SkyKeyInfoModule,
    SkyRepeaterModule,
    SkySearchModule,
    SkySortModule,
    SkyToolbarModule,
  ],
})
export class RecordPageNotesTabComponent {
  protected notes = [
    {
      noteNumber: 1,
      content: 'Attended our gala last year and had a great time.',
      date: '11/17/2024',
    },
    {
      noteNumber: 2,
      content:
        'Is a business owner and has a lot of connections in the community.',
      date: '10/11/2024',
    },
  ];
}

```

#### record-page-overview-tab.component.ts

```typescript
import { CommonModule } from '@angular/common';
import { Component } from '@angular/core';
import { SkyIconModule } from '@skyux/icon';
import { SkyKeyInfoModule } from '@skyux/indicators';
import {
  SkyBoxModule,
  SkyDescriptionListModule,
  SkyFluidGridModule,
} from '@skyux/layout';
import { SkyRepeaterModule } from '@skyux/lists';

import { Detail } from './detail';

@Component({
  selector: 'app-record-page-overview-tab',
  templateUrl: './record-page-overview-tab.component.html',
  styleUrls: ['./record-page-overview-tab.component.scss'],
  imports: [
    CommonModule,
    SkyBoxModule,
    SkyDescriptionListModule,
    SkyFluidGridModule,
    SkyIconModule,
    SkyKeyInfoModule,
    SkyRepeaterModule,
  ],
})
export class RecordPageOverviewTabComponent {
  protected recordDetails: Detail[] = [
    {
      detail: 'Designation',
      info: 'General operating',
    },
    {
      detail: 'Source',
      info: 'Online donation form',
    },
    {
      detail: 'Status',
      info: 'Active',
    },
    {
      detail: 'Due date',
      info: '12/12/2023',
    },
    {
      detail: 'Create date',
      info: '01/05/2023',
    },
    {
      detail: 'Frequency',
      info: 'Quarterly',
    },
  ];

  protected actualPayments = [
    {
      category: 'Amount',
      value: '$845.00',
    },
    {
      category: 'Assigned',
      value: '$800.00',
    },
    {
      category: 'Applied',
      value: '$800.00',
    },
    {
      category: 'Payments',
      value: 25,
    },
  ];

  protected projectedPayments = [
    {
      category: 'Amount',
      value: '$0',
    },
    {
      category: 'Line items',
      value: 0,
    },
  ];

  protected recentActivity = [
    {
      activity: '$250.00 payment processed successfully.',
      date: '07/01/2023 12:02 am',
    },
    {
      activity: '$150.00 payment processed successfully.',
      date: '06/15/2023 12:02 am',
    },
    {
      activity: '$250.00 payment processed successfully.',
      date: '04/01/2023 12:02 am',
    },
  ];
}

```

#### attachments-grid-context-menu.component.html

```html
<sky-dropdown
  buttonType="context-menu"
  [label]="'context menu for ' + attachmentName"
>
  <sky-dropdown-menu>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Edit ' + attachmentName">
        Edit
      </button>
    </sky-dropdown-item>
    <sky-dropdown-item>
      <button type="button" [attr.aria-label]="'Delete ' + attachmentName">
        Delete
      </button>
    </sky-dropdown-item>
  </sky-dropdown-menu>
</sky-dropdown>

```

#### example.component.html

```html
<sky-page layout="tabs" helpKey="example-help">
  <sky-page-header pageTitle="Charlene Conners">
    <sky-page-header-alerts>
      <sky-alert alertType="warning" descriptionType="warning">
        Missing phone number for Charlene Conners.
      </sky-alert>
    </sky-page-header-alerts>
    <sky-page-header-avatar>
      <sky-avatar name="Charlene Conners" />
    </sky-page-header-avatar>
    <sky-page-header-details>
      <sky-label labelType="info" descriptionType="important-info">
        VIP
      </sky-label>
    </sky-page-header-details>
    <sky-page-header-actions>
      <button class="sky-btn sky-btn-default" type="button">
        Email contact
      </button>
      <button class="sky-btn sky-btn-default" type="button">
        Add to my contacts
      </button>
    </sky-page-header-actions>
  </sky-page-header>
  <sky-page-content>
    <app-record-page-content />
  </sky-page-content>
</sky-page>

```

#### record-page-attachments-tab.component.html

```html
<sky-data-manager>
  <div class="sky-margin-stacked-xs">
    <sky-data-manager-toolbar>
      <sky-data-manager-toolbar-primary-item>
        <button
          aria-label="New attachment"
          class="sky-btn sky-btn-default"
          type="button"
        >
          <sky-icon iconName="add" />
          New
        </button>
      </sky-data-manager-toolbar-primary-item>
    </sky-data-manager-toolbar>
  </div>
  <div class="sky-margin-stacked-sm">
    <sky-key-info layout="horizontal" class="sky-padding-horizontal-sm">
      <sky-key-info-value class="sky-font-display-4">
        {{ items.length }}
      </sky-key-info-value>
      <sky-key-info-label> Attachments </sky-key-info-label>
    </sky-key-info>
  </div>
  <sky-data-view skyAgGridDataManagerAdapter viewId="gridView">
    <sky-ag-grid-wrapper>
      <ag-grid-angular [gridOptions]="gridOptions" [rowData]="items" />
    </sky-ag-grid-wrapper>
  </sky-data-view>
</sky-data-manager>

```

#### record-page-content.component.html

```html
<sky-tabset [(active)]="activeTabIndex">
  <sky-tab tabHeading="Overview" layout="blocks">
    <app-record-page-overview-tab />
  </sky-tab>
  <sky-tab tabHeading="Notes" layout="list">
    <app-record-page-notes-tab />
  </sky-tab>
  <sky-tab tabHeading="Attachments" layout="list">
    @if (activeTabIndex === 2) {
      <app-record-page-attachments-tab />
    }
  </sky-tab>
</sky-tabset>

```

#### record-page-notes-tab.component.html

```html
<div class="sky-margin-stacked-xs">
  <sky-toolbar>
    <sky-toolbar-item>
      <button
        class="sky-btn sky-btn-default"
        type="button"
        aria-label="New note"
      >
        <sky-icon iconName="add" />
        New
      </button>
    </sky-toolbar-item>
    <sky-toolbar-item>
      <sky-sort [showButtonText]="true">
        <sky-sort-item>
          <span aria-label="Sort notes by date created (newest first)">
            Date created (newest first)
          </span>
        </sky-sort-item>
        <sky-sort-item>
          <span aria-label="Sort notes by date created (oldest first)">
            Date created (oldest first)
          </span>
        </sky-sort-item>
      </sky-sort>
    </sky-toolbar-item>
    <sky-toolbar-item>
      <button
        class="sky-btn sky-btn-default"
        type="button"
        aria-label="Export notes"
      >
        <sky-icon iconName="document-xls" />
        Export
      </button>
    </sky-toolbar-item>
    <sky-toolbar-item>
      <sky-search placeholderText="Find in notes" />
    </sky-toolbar-item>
  </sky-toolbar>
</div>
<div class="sky-margin-stacked-sm">
  <sky-key-info layout="horizontal">
    <sky-key-info-value class="sky-font-display-4">
      {{ notes.length }}
    </sky-key-info-value>
    <sky-key-info-label> Notes </sky-key-info-label>
  </sky-key-info>
</div>
<sky-repeater>
  @for (note of notes; track note.noteNumber) {
    <sky-repeater-item>
      <sky-repeater-item-context-menu>
        <sky-dropdown
          buttonType="context-menu"
          [label]="
            'Context menu for note ' + note.noteNumber + ' from ' + note.date
          "
        >
          <sky-dropdown-menu>
            <sky-dropdown-item>
              <button
                type="button"
                [attr.aria-label]="
                  'Edit note ' + note.noteNumber + ' from ' + note.date
                "
              >
                Edit
              </button>
            </sky-dropdown-item>
            <sky-dropdown-item>
              <button
                type="button"
                [attr.aria-label]="
                  'Delete note ' + note.noteNumber + ' from ' + note.date
                "
              >
                Delete
              </button>
            </sky-dropdown-item>
          </sky-dropdown-menu>
        </sky-dropdown>
      </sky-repeater-item-context-menu>
      <sky-repeater-item-content>
        <div class="sky-margin-stacked-xs">
          {{ note.content }}
        </div>
        <div class="sky-font-deemphasized">{{ note.date }}</div>
      </sky-repeater-item-content>
    </sky-repeater-item>
  }
</sky-repeater>

```

#### record-page-overview-tab.component.html

```html
<sky-fluid-grid gutterSize="medium" [disableMargin]="true">
  <sky-row>
    <sky-column [screenSmall]="4" [screenXSmall]="12">
      <sky-box class="sky-margin-stacked-xl" headingText="Details">
        <sky-box-controls>
          <button
            aria-label="Edit button for details"
            class="sky-btn sky-btn-icon-borderless"
            type="button"
          >
            <sky-icon iconName="edit" />
          </button>
        </sky-box-controls>
        <sky-box-content>
          <sky-description-list mode="vertical">
            @for (recordDetail of recordDetails; track recordDetail.detail) {
              <sky-description-list-content>
                <sky-description-list-term>
                  {{ recordDetail.detail }}
                </sky-description-list-term>
                <sky-description-list-description>
                  {{ recordDetail.info }}
                </sky-description-list-description>
              </sky-description-list-content>
            }
          </sky-description-list>
        </sky-box-content>
      </sky-box>
    </sky-column>
    <sky-column [screenSmall]="4" [screenXSmall]="12">
      <sky-box class="sky-margin-stacked-xl" headingText="Payments">
        <sky-box-content>
          <div class="box-2-content">
            <div class="box-2-actuals">
              <h3 class="sky-font-heading-4">Actuals</h3>
              @for (
                actual of actualPayments;
                track actual.category;
                let i = $index
              ) {
                <sky-key-info
                  [ngClass]="{
                    'sky-margin-stacked-lg': i < actualPayments.length - 1
                  }"
                >
                  <sky-key-info-value class="sky-font-display-3">
                    {{ actual.value }}
                  </sky-key-info-value>
                  <sky-key-info-label>{{ actual.category }}</sky-key-info-label>
                </sky-key-info>
              }
            </div>
            <div class="box-2-projected">
              <h3 class="sky-font-heading-4">Projected</h3>
              @for (
                projected of projectedPayments;
                track projected;
                let i = $index
              ) {
                <sky-key-info
                  [ngClass]="{
                    'sky-margin-stacked-lg': i < projectedPayments.length - 1
                  }"
                >
                  <sky-key-info-value class="sky-font-display-3">
                    {{ projected.value }}
                  </sky-key-info-value>
                  <sky-key-info-label>
                    {{ projected.category }}
                  </sky-key-info-label>
                </sky-key-info>
              }
            </div>
          </div>
        </sky-box-content>
      </sky-box>
    </sky-column>
    <sky-column [screenSmall]="4" [screenXSmall]="12">
      <sky-box headingText="Recent activity">
        <sky-box-content>
          <sky-repeater>
            @for (activity of recentActivity; track activity.activity) {
              <sky-repeater-item>
                <sky-repeater-item-content>
                  <div class="sky-margin-stacked-xs">
                    {{ activity.activity }}
                  </div>
                  <div class="sky-font-deemphasized">{{ activity.date }}</div>
                </sky-repeater-item-content>
              </sky-repeater-item>
            }
          </sky-repeater>
        </sky-box-content>
      </sky-box>
    </sky-column>
  </sky-row>
</sky-fluid-grid>

```

#### record-page-overview-tab.component.scss

```css
.box-2-content {
  display: flex;

  div {
    display: flex;
    flex-direction: column;
    flex-grow: 1;
  }

  .box-2-actuals {
    margin-right: 60px;
  }
}

```

---

## Split view page with fit layout

**Component:** PagesPageSplitViewPageFitLayoutExampleComponent

**Selector:** `app-pages-page-split-view-page-fit-layout-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { provideRouter } from '@angular/router';
import {
  SkyHelpTestingController,
  SkyHelpTestingModule,
} from '@skyux/core/testing';
import { SkyPageHarness } from '@skyux/pages/testing';

import { PagesPageSplitViewPageFitLayoutExampleComponent } from './example.component';

describe('Split view page fit layout example', () => {
  async function setupTest(): Promise<{
    pageHarness: SkyPageHarness;
    fixture: ComponentFixture<PagesPageSplitViewPageFitLayoutExampleComponent>;
    helpController: SkyHelpTestingController;
  }> {
    const fixture = TestBed.createComponent(
      PagesPageSplitViewPageFitLayoutExampleComponent,
    );

    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const pageHarness = await loader.getHarness(SkyPageHarness);
    const helpController = TestBed.inject(SkyHelpTestingController);

    return { pageHarness, fixture, helpController };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [
        PagesPageSplitViewPageFitLayoutExampleComponent,
        SkyHelpTestingModule,
        NoopAnimationsModule,
      ],
      providers: [provideRouter([])],
    });
  });

  it('should have a fit layout', async () => {
    const { pageHarness, fixture } = await setupTest();

    fixture.detectChanges();

    await expectAsync(pageHarness.getLayout()).toBeResolvedTo('fit');
  });

  it('should have the correct help key', async () => {
    const { helpController } = await setupTest();

    helpController.expectCurrentHelpKey('example-help');
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyAlertModule } from '@skyux/indicators';
import { SkyPageModule } from '@skyux/pages';

import { SplitViewPageContentComponent } from './split-view-page-content.component';

/**
 * @title Split view page with fit layout
 * @docsDemoHidden
 */
@Component({
  selector: 'app-pages-page-split-view-page-fit-layout-example',
  templateUrl: './example.component.html',
  imports: [SkyAlertModule, SkyPageModule, SplitViewPageContentComponent],
})
export class PagesPageSplitViewPageFitLayoutExampleComponent {}

```

#### split-view-page-content.component.ts

```typescript
import { Component, inject } from '@angular/core';
import { FormBuilder, FormsModule, ReactiveFormsModule } from '@angular/forms';
import { SkySummaryActionBarModule } from '@skyux/action-bars';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyDescriptionListModule } from '@skyux/layout';
import { SkyRepeaterModule } from '@skyux/lists';
import { SkyConfirmService, SkyConfirmType } from '@skyux/modals';
import {
  SkySplitViewMessage,
  SkySplitViewMessageType,
  SkySplitViewModule,
} from '@skyux/split-view';

import { Subject } from 'rxjs';

interface WorkspaceItem {
  id: number;
  amount: number;
  date: string;
  vendor: string;
  receiptImage: string;
  approvedAmount: number;
  comments: string;
}

@Component({
  selector: 'app-split-view-page-content',
  templateUrl: './split-view-page-content.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyDescriptionListModule,
    SkyInputBoxModule,
    SkyRepeaterModule,
    SkySplitViewModule,
    SkySummaryActionBarModule,
  ],
})
export class SplitViewPageContentComponent {
  protected set activeIndex(value: number) {
    this.#_activeIndex = value;
    this.activeRecord = this.items[this.#_activeIndex];
    this.#loadFormGroup(this.activeRecord);
  }

  protected get activeIndex(): number {
    return this.#_activeIndex;
  }

  protected items: WorkspaceItem[] = [
    {
      id: 1,
      amount: 73.19,
      date: '5/13/2020',
      vendor: 'amazon.com',
      receiptImage: 'amzn-office-supply-order-5-13-19.png',
      approvedAmount: 73.19,
      comments: '',
    },
    {
      id: 2,
      amount: 214.12,
      date: '5/14/2020',
      vendor: 'Office Max',
      receiptImage: 'office-max-order.png',
      approvedAmount: 214.12,
      comments: '',
    },
    {
      id: 3,
      amount: 29.99,
      date: '5/14/2020',
      vendor: 'amazon.com',
      receiptImage: 'amzn-office-supply-order-5-14-19.png',
      approvedAmount: 29.99,
      comments: '',
    },
    {
      id: 4,
      amount: 1500,
      date: '5/15/2020',
      vendor: 'Fresh Catering, LLC',
      receiptImage: 'fresh-catering-llc-order.png',
      approvedAmount: 1500,
      comments: '',
    },
    {
      id: 5,
      amount: 456.24,
      date: '5/16/2020',
      vendor: 'Wish',
      receiptImage: 'wish-delivery-order.png',
      approvedAmount: 456.24,
      comments: '',
    },
    {
      id: 6,
      amount: 62.37,
      date: '5/16/2020',
      vendor: 'Staples',
      receiptImage: 'staples-paper-bulk-order.png',
      approvedAmount: 62.37,
      comments: '',
    },
    {
      id: 7,
      amount: 51.84,
      date: '5/17/2020',
      vendor: 'amazon.com',
      receiptImage: 'amzn-office-supply-order-5-17-19.png',
      approvedAmount: 51.84,
      comments: '',
    },
    {
      id: 8,
      amount: 92.55,
      date: '5/18/2020',
      vendor: 'Home Depot',
      receiptImage: 'home-depot-order.png',
      approvedAmount: 0.0,
      comments: '',
    },
    {
      id: 9,
      amount: 38.29,
      date: '5/18/2020',
      vendor: 'Papa Johns',
      receiptImage: 'papa-johns-order.png',
      approvedAmount: 38.29,
      comments: '',
    },
  ];

  protected activeRecord = this.items[0];
  protected listWidth: number | undefined;
  protected splitViewStream = new Subject<SkySplitViewMessage>();

  protected splitViewDemoForm = inject(FormBuilder).group({
    approvedAmount: [this.activeRecord.approvedAmount],
    comments: [this.activeRecord.comments],
  });

  #_activeIndex = 0;

  #confirmSvc = inject(SkyConfirmService);

  protected onItemClick(index: number): void {
    // Prevent workspace from loading new data if the current workspace form is dirty.
    if (this.splitViewDemoForm.dirty && index !== this.activeIndex) {
      this.#openConfirmModal(index);
    } else {
      this.#loadWorkspace(index);
    }
  }

  protected onApprove(): void {
    console.log('Approved clicked!');
    this.#saveForm();
  }

  protected onDeny(): void {
    console.log('Denied clicked!');
  }

  #loadFormGroup(record: WorkspaceItem): void {
    this.splitViewDemoForm.setValue({
      approvedAmount: record.approvedAmount,
      comments: record.comments,
    });
  }

  #loadWorkspace(index: number): void {
    this.activeIndex = index;
    this.#setFocusInWorkspace();
  }

  #openConfirmModal(index: number): void {
    this.#confirmSvc
      .open({
        message:
          'You have unsaved work. Would you like to save it before you change records?',
        type: SkyConfirmType.Custom,
        buttons: [
          {
            action: 'yes',
            text: 'Yes',
            styleType: 'primary',
          },
          {
            action: 'discard',
            text: 'Discard changes',
            styleType: 'link',
          },
        ],
      })
      .closed.subscribe((closeArgs) => {
        if (closeArgs.action === 'yes') {
          this.#saveForm();
        }

        this.#loadWorkspace(index);
      });
  }

  #saveForm(): void {
    this.activeRecord = Object.assign(
      this.activeRecord,
      this.splitViewDemoForm.value,
    );

    this.splitViewDemoForm.markAsPristine();
  }

  #setFocusInWorkspace(): void {
    this.splitViewStream.next({
      type: SkySplitViewMessageType.FocusWorkspace,
    });
  }
}

```

#### example.component.html

```html
<sky-page layout="fit" helpKey="example-help">
  <sky-page-header
    pageTitle="Expenses to approve"
    [parentLink]="{
      label: 'Expenses',
      permalink: {
        route: {
          commands: ['/']
        }
      }
    }"
  >
    <sky-page-header-alerts>
      <sky-alert alertType="warning" descriptionType="warning">
        There are multiple expense approvals due soon.
      </sky-alert>
    </sky-page-header-alerts>
    <sky-page-header-actions>
      <button class="sky-btn sky-btn-default" type="button">Approve all</button>
    </sky-page-header-actions>
  </sky-page-header>
  <sky-page-content>
    <app-split-view-page-content />
  </sky-page-content>
</sky-page>

```

#### split-view-page-content.component.html

```html
<sky-split-view dock="fill" [messageStream]="splitViewStream">
  <sky-split-view-drawer [ariaLabel]="'Transaction list'" [width]="listWidth">
    <sky-repeater [activeIndex]="activeIndex">
      @for (item of items; track item.id; let i = $index) {
        <sky-repeater-item
          (click)="onItemClick(i)"
          (keyup.enter)="onItemClick(i)"
        >
          <sky-repeater-item-content>
            {{ item.amount }} <br />
            {{ item.date }} <br />
            {{ item.vendor }}
          </sky-repeater-item-content>
        </sky-repeater-item>
      }
    </sky-repeater>
  </sky-split-view-drawer>

  <sky-split-view-workspace ariaLabel="Transaction form">
    <sky-split-view-workspace-content class="sky-padding-even-xl">
      <form [formGroup]="splitViewDemoForm" (ngSubmit)="onApprove()">
        <sky-description-list class="sky-margin-stacked-xl">
          <sky-description-list-content>
            <sky-description-list-term>
              Receipt amount
            </sky-description-list-term>
            <sky-description-list-description>
              {{ activeRecord.amount }}
            </sky-description-list-description>
          </sky-description-list-content>
          <sky-description-list-content>
            <sky-description-list-term> Date </sky-description-list-term>
            <sky-description-list-description>
              {{ activeRecord.date }}
            </sky-description-list-description>
          </sky-description-list-content>
          <sky-description-list-content>
            <sky-description-list-term> Vendor </sky-description-list-term>
            <sky-description-list-description>
              {{ activeRecord.vendor }}
            </sky-description-list-description>
          </sky-description-list-content>
          <sky-description-list-content>
            <sky-description-list-term>
              Receipt image
            </sky-description-list-term>
            <sky-description-list-description>
              {{ activeRecord.receiptImage }}
            </sky-description-list-description>
          </sky-description-list-content>
        </sky-description-list>
        <div>
          <sky-input-box stacked="true" labelText="Approved amount">
            <input
              formControlName="approvedAmount"
              name="approvedAmount"
              type="text"
            />
          </sky-input-box>
        </div>

        <div>
          <sky-input-box stacked="true" labelText="Comments">
            <textarea formControlName="comments" name="comments"></textarea>
          </sky-input-box>
        </div>
      </form>
    </sky-split-view-workspace-content>
    <sky-split-view-workspace-footer>
      <sky-summary-action-bar>
        <sky-summary-action-bar-actions>
          <sky-summary-action-bar-primary-action (actionClick)="onApprove()">
            Approve expense
          </sky-summary-action-bar-primary-action>
          <sky-summary-action-bar-secondary-actions>
            <sky-summary-action-bar-secondary-action (actionClick)="onDeny()">
              Deny expense
            </sky-summary-action-bar-secondary-action>
          </sky-summary-action-bar-secondary-actions>
        </sky-summary-action-bar-actions>
      </sky-summary-action-bar>
    </sky-split-view-workspace-footer>
  </sky-split-view-workspace>
</sky-split-view>

```

---

## Page bound split view in a page component with fit layout

**Component:** SplitViewPageBoundExampleComponent

**Selector:** `app-split-view-page-bound-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { HarnessLoader } from '@angular/cdk/testing';
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import {
  SkyMediaQueryTestingController,
  provideSkyMediaQueryTesting,
} from '@skyux/core/testing';
import { SkyInputBoxHarness } from '@skyux/forms/testing';
import { SkyRepeaterItemHarness } from '@skyux/lists/testing';
import { SkySplitViewHarness } from '@skyux/split-view/testing';

import { SplitViewPageBoundExampleComponent } from './example.component';

describe('Split view example', () => {
  async function setupTest(options: { dataSkyId?: string } = {}): Promise<{
    splitViewHarness: SkySplitViewHarness;
    mediaQueryController: SkyMediaQueryTestingController;
    fixture: ComponentFixture<SplitViewPageBoundExampleComponent>;
    loader: HarnessLoader;
  }> {
    await TestBed.configureTestingModule({
      imports: [SplitViewPageBoundExampleComponent, NoopAnimationsModule],
      providers: [provideSkyMediaQueryTesting()],
    }).compileComponents();

    const mediaQueryController = TestBed.inject(SkyMediaQueryTestingController);

    const fixture = TestBed.createComponent(SplitViewPageBoundExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const splitViewHarness: SkySplitViewHarness = options.dataSkyId
      ? await loader.getHarness(
          SkySplitViewHarness.with({ dataSkyId: options.dataSkyId }),
        )
      : await loader.getHarness(SkySplitViewHarness);

    return { splitViewHarness, mediaQueryController, fixture, loader };
  }

  it('should set up split view component and children', async () => {
    const { splitViewHarness, fixture } = await setupTest();
    fixture.detectChanges();
    await fixture.whenStable();

    // validate parent split view properties
    await expectAsync(splitViewHarness.getDockType()).toBeResolvedTo('fill');
    await expectAsync(splitViewHarness.getDrawerIsVisible()).toBeResolvedTo(
      true,
    );
    await expectAsync(splitViewHarness.getWorkspaceIsVisible()).toBeResolvedTo(
      true,
    );

    // query for drawer and workspace child components and validate properties
    const drawerHarness = await splitViewHarness.getDrawer();
    const workspaceHarness = await splitViewHarness.getWorkspace();

    await expectAsync(drawerHarness.getAriaLabel()).toBeResolvedTo(
      'Transaction list',
    );
    await expectAsync(workspaceHarness.getAriaLabel()).toBeResolvedTo(
      'Transaction form',
    );

    // query for content and footer child components and their child elements
    const contentHarness = await workspaceHarness.getContent();
    const footerHarness = await workspaceHarness.getFooter();

    await expectAsync(
      contentHarness?.queryHarnesses(SkyInputBoxHarness),
    ).toBeResolved();
    await expectAsync(
      footerHarness?.querySelector('sky-summary-action-bar-primary-action'),
    ).toBeResolved();
  });

  it('should switch between views in responsive mode', async () => {
    const { splitViewHarness, mediaQueryController, fixture } =
      await setupTest();

    // set XS breakpoint to force split view into responsive mode
    mediaQueryController.setBreakpoint('xs');

    fixture.detectChanges();
    await fixture.whenStable();

    await expectAsync(splitViewHarness.getDrawerIsVisible()).toBeResolvedTo(
      false,
    );
    await expectAsync(splitViewHarness.getWorkspaceIsVisible()).toBeResolvedTo(
      true,
    );
    await expectAsync(splitViewHarness.getBackButtonText()).toBeResolvedTo(
      'Back to list',
    );

    // switch to drawer view
    await splitViewHarness.openDrawer();

    fixture.detectChanges();
    await fixture.whenStable();

    await expectAsync(splitViewHarness.getDrawerIsVisible()).toBeResolvedTo(
      true,
    );
    await expectAsync(splitViewHarness.getWorkspaceIsVisible()).toBeResolvedTo(
      false,
    );

    const drawerHarness = await splitViewHarness.getDrawer();
    const drawerItems = await drawerHarness.queryHarnesses(
      SkyRepeaterItemHarness,
    );

    // switch back to workspace view
    await drawerItems[3].click();

    fixture.detectChanges();
    await fixture.whenStable();

    await expectAsync(splitViewHarness.getDrawerIsVisible()).toBeResolvedTo(
      false,
    );
    await expectAsync(splitViewHarness.getWorkspaceIsVisible()).toBeResolvedTo(
      true,
    );
  });
});

```

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkySummaryActionBarModule } from '@skyux/action-bars';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyAlertModule } from '@skyux/indicators';
import { SkyDescriptionListModule, SkyPageSummaryModule } from '@skyux/layout';
import { SkyRepeaterModule } from '@skyux/lists';
import { SkyConfirmService, SkyConfirmType } from '@skyux/modals';
import { SkyPageModule } from '@skyux/pages';
import {
  SkySplitViewMessage,
  SkySplitViewMessageType,
  SkySplitViewModule,
} from '@skyux/split-view';

import { Subject } from 'rxjs';

import { Record } from './record';

interface DemoForm {
  approvedAmount: FormControl<number>;
  comments: FormControl<string>;
}

/**
 * @title Page bound split view in a page component with fit layout
 * @docsDemoHidden
 */
@Component({
  selector: 'app-split-view-page-bound-example',
  templateUrl: './example.component.html',
  styleUrls: ['./example.component.scss'],
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyAlertModule,
    SkyDescriptionListModule,
    SkyInputBoxModule,
    SkyPageModule,
    SkyPageSummaryModule,
    SkyRepeaterModule,
    SkySplitViewModule,
    SkySummaryActionBarModule,
  ],
})
export class SplitViewPageBoundExampleComponent {
  protected set activeIndex(value: number) {
    this.#_activeIndex = value;
    this.activeRecord = this.items[this.#_activeIndex];
    this.#loadFormGroup(this.activeRecord);
  }

  protected get activeIndex(): number {
    return this.#_activeIndex;
  }

  protected items: Record[] = [
    {
      id: 1,
      amount: 73.19,
      date: '5/13/2020',
      vendor: 'amazon.com',
      receiptImage: 'amzn-office-supply-order-5-13-19.png',
      approvedAmount: 73.19,
      comments: '',
    },
    {
      id: 2,
      amount: 214.12,
      date: '5/14/2020',
      vendor: 'Office Max',
      receiptImage: 'office-max-order.png',
      approvedAmount: 214.12,
      comments: '',
    },
    {
      id: 3,
      amount: 29.99,
      date: '5/14/2020',
      vendor: 'amazon.com',
      receiptImage: 'amzn-office-supply-order-5-14-19.png',
      approvedAmount: 29.99,
      comments: '',
    },
    {
      id: 4,
      amount: 1500,
      date: '5/15/2020',
      vendor: 'Fresh Catering, LLC',
      receiptImage: 'fresh-catering-llc-order.png',
      approvedAmount: 1500,
      comments: '',
    },
    {
      id: 5,
      amount: 456.24,
      date: '5/16/2020',
      vendor: 'Wish',
      receiptImage: 'wish-delivery-order.png',
      approvedAmount: 456.24,
      comments: '',
    },
    {
      id: 6,
      amount: 62.37,
      date: '5/16/2020',
      vendor: 'Staples',
      receiptImage: 'staples-paper-bulk-order.png',
      approvedAmount: 62.37,
      comments: '',
    },
    {
      id: 7,
      amount: 51.84,
      date: '5/17/2020',
      vendor: 'amazon.com',
      receiptImage: 'amzn-office-supply-order-5-17-19.png',
      approvedAmount: 51.84,
      comments: '',
    },
    {
      id: 8,
      amount: 92.55,
      date: '5/18/2020',
      vendor: 'Home Depot',
      receiptImage: 'home-depot-order.png',
      approvedAmount: 0.0,
      comments: '',
    },
    {
      id: 9,
      amount: 38.29,
      date: '5/18/2020',
      vendor: 'Papa Johns',
      receiptImage: 'papa-johns-order.png',
      approvedAmount: 38.29,
      comments: '',
    },
  ];

  protected activeRecord: Record;
  protected splitViewDemoForm: FormGroup<DemoForm>;
  protected splitViewStream = new Subject<SkySplitViewMessage>();
  protected unapprovedTransaction = true;

  #_activeIndex = 0;

  readonly #confirmSvc = inject(SkyConfirmService);

  constructor() {
    // Start with the first item selected.
    this.activeIndex = 0;
    this.activeRecord = this.items[this.activeIndex];

    this.splitViewDemoForm = new FormGroup({
      approvedAmount: new FormControl(this.activeRecord.approvedAmount, {
        nonNullable: true,
      }),
      comments: new FormControl(this.activeRecord.comments, {
        nonNullable: true,
      }),
    });
  }

  protected onItemClick(index: number): void {
    // Prevent workspace from loading new data if the current workspace form is dirty.
    if (this.splitViewDemoForm.dirty && index !== this.activeIndex) {
      this.#openConfirmModal(index);
    } else {
      this.#loadWorkspace(index);
    }
  }

  protected onApprove(): void {
    console.log('Approved clicked!');
    this.#saveForm();
  }

  protected onDeny(): void {
    console.log('Denied clicked!');
  }

  #loadFormGroup(record: Record): void {
    this.splitViewDemoForm = new FormGroup({
      approvedAmount: new FormControl(record.approvedAmount, {
        nonNullable: true,
      }),
      comments: new FormControl(record.comments, { nonNullable: true }),
    });
  }

  #loadWorkspace(index: number): void {
    this.activeIndex = index;
    this.#setFocusInWorkspace();
  }

  #openConfirmModal(index: number): void {
    this.#confirmSvc
      .open({
        message:
          'You have unsaved work. Would you like to save it before you change records?',
        type: SkyConfirmType.Custom,
        buttons: [
          {
            action: 'yes',
            text: 'Yes',
            styleType: 'primary',
          },
          {
            action: 'discard',
            text: 'Discard changes',
            styleType: 'link',
          },
        ],
      })
      .closed.subscribe((closeArgs) => {
        if (closeArgs.action.toLowerCase() === 'yes') {
          this.#saveForm();
        }

        this.#loadWorkspace(index);
      });
  }

  #saveForm(): void {
    this.activeRecord.approvedAmount = parseFloat(
      `${this.splitViewDemoForm.value.approvedAmount ?? 0}`,
    );

    this.activeRecord.comments = this.splitViewDemoForm.value.comments ?? '';

    this.unapprovedTransaction =
      this.items.findIndex((item) => item.amount !== item.approvedAmount) >= 0;

    this.splitViewDemoForm.reset(this.splitViewDemoForm.value);
  }

  #setFocusInWorkspace(): void {
    const message: SkySplitViewMessage = {
      type: SkySplitViewMessageType.FocusWorkspace,
    };

    this.splitViewStream.next(message);
  }
}

```

#### record.ts

```typescript
export interface Record {
  id: number;
  amount: number;
  date: string;
  vendor: string;
  receiptImage: string;
  approvedAmount: number;
  comments: string;
}

```

#### example.component.html

```html
<sky-page layout="fit">
  <div class="page-flex">
    <div class="page-flex-header">
      <sky-page-summary>
        @if (unapprovedTransaction) {
          <sky-page-summary-alert>
            <sky-alert alertType="info"
              >There is an unapproved transaction.</sky-alert
            >
          </sky-page-summary-alert>
        }
        <sky-page-summary-title> SKY Developers, LLC </sky-page-summary-title>
        <sky-page-summary-subtitle>
          Petty Cash Transactions
        </sky-page-summary-subtitle>
        <sky-page-summary-content>
          The transactions below cover various operating expenses which do not
          fall under one of the budgets areas of expenditures.
        </sky-page-summary-content>
      </sky-page-summary>
    </div>
    <div class="page-flex-main">
      <sky-split-view dock="fill" [messageStream]="splitViewStream">
        <sky-split-view-drawer [ariaLabel]="'Transaction list'">
          <sky-repeater [activeIndex]="activeIndex">
            @for (item of items; track item; let i = $index) {
              <sky-repeater-item
                (click)="onItemClick(i)"
                (keyup.enter)="onItemClick(i)"
              >
                <sky-repeater-item-content>
                  {{ item.amount }} <br />
                  {{ item.date }} <br />
                  {{ item.vendor }}
                </sky-repeater-item-content>
              </sky-repeater-item>
            }
          </sky-repeater>
        </sky-split-view-drawer>

        <sky-split-view-workspace [ariaLabel]="'Transaction form'">
          <sky-split-view-workspace-content class="sky-padding-even-xl">
            <form [formGroup]="splitViewDemoForm" (ngSubmit)="onApprove()">
              <sky-description-list labelWidth="150px">
                <sky-description-list-content>
                  <sky-description-list-term>
                    Receipt amount
                  </sky-description-list-term>
                  <sky-description-list-description>
                    {{ activeRecord.amount }}
                  </sky-description-list-description>
                </sky-description-list-content>
                <sky-description-list-content>
                  <sky-description-list-term> Date </sky-description-list-term>
                  <sky-description-list-description>
                    {{ activeRecord.date }}
                  </sky-description-list-description>
                </sky-description-list-content>
                <sky-description-list-content>
                  <sky-description-list-term>
                    Vendor
                  </sky-description-list-term>
                  <sky-description-list-description>
                    {{ activeRecord.vendor }}
                  </sky-description-list-description>
                </sky-description-list-content>
                <sky-description-list-content>
                  <sky-description-list-term>
                    Receipt image
                  </sky-description-list-term>
                  <sky-description-list-description>
                    {{ activeRecord.receiptImage }}
                  </sky-description-list-description>
                </sky-description-list-content>
              </sky-description-list>
              <sky-input-box labelText="Approved amount" stacked="true">
                <input formControlName="approvedAmount" type="text" />
              </sky-input-box>
              <sky-input-box labelText="Comments">
                <textarea formControlName="comments"></textarea>
              </sky-input-box>
            </form>
          </sky-split-view-workspace-content>
          <sky-split-view-workspace-footer>
            <sky-summary-action-bar>
              <sky-summary-action-bar-actions>
                <sky-summary-action-bar-primary-action
                  (actionClick)="onApprove()"
                >
                  Approve expense
                </sky-summary-action-bar-primary-action>
                <sky-summary-action-bar-secondary-actions>
                  <sky-summary-action-bar-secondary-action
                    (actionClick)="onDeny()"
                  >
                    Deny expense
                  </sky-summary-action-bar-secondary-action>
                </sky-summary-action-bar-secondary-actions>
              </sky-summary-action-bar-actions>
            </sky-summary-action-bar>
          </sky-split-view-workspace-footer>
        </sky-split-view-workspace>
      </sky-split-view>
    </div>
  </div>
</sky-page>

```

#### example.component.scss

```css
.page-flex {
  display: flex;
  flex-direction: column;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}

.page-flex-header {
  flex-grow: 0;
}

.page-flex-main {
  flex-grow: 1;
  overflow: auto;
  /* Required for the split view to fill this element instead of the document */
  position: relative;
}

```

---