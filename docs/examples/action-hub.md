---
component: 'action-hub'
type: 'code-examples'
description: 'Code examples for the action-hub component.'
---

# Action Hub Code Examples

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