---
component: 'repeater'
type: 'code-examples'
description: 'Code examples for the repeater component.'
---

# Repeater Code Examples

## Inline form with repeater

**Component:** InlineFormRepeatersExampleComponent

**Selector:** `app-inline-form-repeaters-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyInlineFormHarness } from '@skyux/inline-form/testing';
import { SkyRepeaterHarness } from '@skyux/lists/testing';

import { InlineFormRepeatersExampleComponent } from './example.component';

describe('Inline form with repeater demo', () => {
  async function setupTest(options: { itemId: number }): Promise<{
    repeaterHarness: SkyRepeaterHarness;
    inlineFormHarness: SkyInlineFormHarness;
    fixture: ComponentFixture<InlineFormRepeatersExampleComponent>;
  }> {
    await TestBed.configureTestingModule({
      imports: [InlineFormRepeatersExampleComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      InlineFormRepeatersExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);
    const repeaterHarness = await loader.getHarness(SkyRepeaterHarness);
    const item = await repeaterHarness.getRepeaterItems();
    const inlineFormHarness =
      await item[options.itemId].queryHarness(SkyInlineFormHarness);

    return { repeaterHarness, inlineFormHarness, fixture };
  }

  it('should set up the spring gala item inline form', async () => {
    const { inlineFormHarness } = await setupTest({
      itemId: 1,
    });
    const editButton = await inlineFormHarness?.querySelector('button.sky-btn');
    await editButton?.click();
    await expectAsync(inlineFormHarness?.isFormExpanded()).toBeResolvedTo(true);

    // You can query inline form buttons when the form is open.
    const buttons = await inlineFormHarness?.getButtons();
    await expectAsync(buttons[0].getText()).toBeResolvedTo('Save');
    const cancelButton = buttons[1];

    await cancelButton.click();
    await expectAsync(inlineFormHarness?.isFormExpanded()).toBeResolvedTo(
      false,
    );
  });
});

```

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyIconModule } from '@skyux/icon';
import {
  SkyInlineFormButtonLayout,
  SkyInlineFormCloseArgs,
  SkyInlineFormConfig,
} from '@skyux/inline-form';
import { SkyRepeaterModule } from '@skyux/lists';

interface DemoForm {
  id: FormControl<string>;
  note: FormControl<string>;
  title: FormControl<string>;
}

interface Item {
  id: string;
  title: string | undefined;
  note: string | undefined;
}

/**
 * @title Inline form with repeater
 */
@Component({
  selector: 'app-inline-form-repeaters-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyIconModule,
    SkyInputBoxModule,
    SkyRepeaterModule,
  ],
})
export class InlineFormRepeatersExampleComponent {
  protected activeInlineFormId: string | undefined;
  protected formGroup: FormGroup<DemoForm>;

  protected inlineFormConfig: SkyInlineFormConfig = {
    buttonLayout: SkyInlineFormButtonLayout.SaveCancel,
  };

  protected items: Item[] = [
    {
      id: '1',
      title: '2019 Spring Gala',
      note: 'Gala for friends and family',
    },
    {
      id: '2',
      title: '2019 Special Winter Event',
      note: 'A special event',
    },
    {
      id: '3',
      title: '2019 Donor Appreciation Event',
      note: 'Event for all donors and families',
    },
    {
      id: '4',
      title: '2020 Spring Gala',
      note: 'Gala for friends and family',
    },
  ];

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      id: new FormControl('', { nonNullable: true }),
      title: new FormControl('', { nonNullable: true }),
      note: new FormControl('', { nonNullable: true }),
    });
  }

  protected showInlineForm(item: Item): void {
    this.activeInlineFormId = item.id;
    this.formGroup.patchValue({
      note: item.note,
      title: item.title,
    });
  }

  protected onInlineFormClose(args: SkyInlineFormCloseArgs): void {
    if (args.reason === 'save') {
      const found = this.items.find(
        (item) => item.id === this.activeInlineFormId,
      );

      if (found) {
        found.note = this.formGroup.value.note;
        found.title = this.formGroup.value.title;
      }
    }

    this.formGroup.patchValue({
      note: undefined,
      title: undefined,
    });

    // Close the active form.
    this.activeInlineFormId = undefined;
  }
}

```

#### example.component.html

```html
<sky-repeater>
  @for (item of items; track item) {
    <sky-repeater-item
      [inlineFormConfig]="inlineFormConfig"
      [inlineFormTemplate]="inlineFormTemplate"
      [showInlineForm]="activeInlineFormId === item.id"
      (inlineFormClose)="onInlineFormClose($event)"
    >
      <sky-repeater-item-title>
        <div class="sky-font-emphasized">
          {{ item.title }}
        </div>
      </sky-repeater-item-title>
      <sky-repeater-item-context-menu>
        <button
          aria-label="Edit"
          class="sky-btn sky-btn-icon-borderless"
          type="button"
          (click)="showInlineForm(item)"
        >
          <sky-icon iconName="edit" />
        </button>
      </sky-repeater-item-context-menu>

      <sky-repeater-item-content>
        {{ item.note }}
      </sky-repeater-item-content>
    </sky-repeater-item>
  }
</sky-repeater>

<ng-template #inlineFormTemplate>
  <form novalidate [formGroup]="formGroup">
    <sky-input-box labelTex="Title" stacked="true">
      <input formControlName="title" type="text" />
    </sky-input-box>
    <sky-input-box labelText="Note">
      <input formControlName="note" type="text" />
    </sky-input-box>
  </form>
</ng-template>

```

---

## Repeater with back to top directive

**Component:** LayoutBackToTopRepeaterExampleComponent

**Selector:** `app-layout-back-to-top-repeater-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyAppTestUtility } from '@skyux-sdk/testing';
import { SkyBackToTopHarness } from '@skyux/layout/testing';

import { LayoutBackToTopRepeaterExampleComponent } from './example.component';

describe('Back to top repeater example', () => {
  function getBackToTopTarget(): HTMLElement | null {
    return document.querySelector('.target');
  }

  function isElementInView(element: HTMLElement | null): boolean {
    if (element) {
      const elementRect = element.getBoundingClientRect();
      return elementRect.top >= 0 && elementRect.bottom <= window.innerHeight;
    }
    return false;
  }

  it('should set up the component', async () => {
    await TestBed.configureTestingModule({
      imports: [LayoutBackToTopRepeaterExampleComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      LayoutBackToTopRepeaterExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const target = getBackToTopTarget();

    expect(isElementInView(target)).toBe(true);
    await expectAsync(loader.getHarness(SkyBackToTopHarness)).toBeRejected();

    window.scrollTo(0, document.body.scrollHeight);
    SkyAppTestUtility.fireDomEvent(window, 'scroll');
    fixture.detectChanges();
    await fixture.whenStable();

    expect(isElementInView(target)).toBe(false);
    const backToTopHarness: SkyBackToTopHarness =
      await loader.getHarness(SkyBackToTopHarness);

    await backToTopHarness.clickBackToTop();

    fixture.detectChanges();
    await fixture.whenStable();

    expect(isElementInView(target)).toBe(true);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyBackToTopModule } from '@skyux/layout';
import { SkyRepeaterModule } from '@skyux/lists';

/**
 * @title Repeater with back to top directive
 * @docsDemoHidden
 */
@Component({
  selector: 'app-layout-back-to-top-repeater-example',
  templateUrl: './example.component.html',
  imports: [SkyBackToTopModule, SkyRepeaterModule],
})
export class LayoutBackToTopRepeaterExampleComponent {
  public personList = [
    {
      name: 'Barbara Durr',
      address: '7436 Fieldstone Court',
    },
    {
      name: 'Colton Chamberlain',
      address: '342 Foster Court',
    },
    {
      name: 'Alva Clifford',
      address: '657 West Rockville Street',
    },
    {
      name: 'Tonja Sanderson',
      address: '7004 Third Street',
    },
    {
      name: 'Paulene Baum',
      address: '9309 Mammoth Street',
    },
    {
      name: 'Jessy Witherspoon',
      address: '43 Canal Street',
    },
    {
      name: 'Solomon Hurley',
      address: '667 Wakehurst Circle',
    },
    {
      name: 'Calandra Geer',
      address: '164 Applegate Drive',
    },
    {
      name: 'Latrice Ashmore',
      address: '7965 Lake Road',
    },
    {
      name: 'Rod Tomlinson',
      address: '9664 Newport Drive',
    },
    {
      name: 'Cristen Sizemore',
      address: '17 Edgefield Street',
    },
    {
      name: 'Kristeen Lunsford',
      address: '245 Green Lake Street',
    },
    {
      name: 'Jack Lovett',
      address: '73 Academy Street',
    },
    {
      name: 'Elwood Farris',
      address: '90 Smoky Hollow Court',
    },
    {
      name: 'Ilene Woo',
      address: '71 Pumpkin Hill Street',
    },
    {
      name: 'Kanesha Hutto',
      address: '107 East Cooper Street',
    },
    {
      name: 'Nick Bourne',
      address: '62 Evergreen Street',
    },
    {
      name: 'Ed Sipes',
      address: '8824 Hill Street',
    },
    {
      name: 'Wonda Lumpkin',
      address: '134 North Warren Street',
    },
    {
      name: 'Cheyenne Lightfoot',
      address: '184 Pierce Avenue',
    },
    {
      name: 'Darcel Lenz',
      address: '9408 Beechwood Street',
    },
    {
      name: 'Martine Rocha',
      address: '871 Shadow Brook Street',
    },
    {
      name: 'Cherelle Connell',
      address: '649 Glenwood Street',
    },
    {
      name: 'Molly Seymour',
      address: '386 E. George Street',
    },
    {
      name: 'Clarice Overton',
      address: '16 Manchester Street',
    },
    {
      name: 'Eliza Vanhorn',
      address: '8232 S. Augusta Street',
    },
  ];
}

```

#### example.component.html

```html
<div class="target"></div>
<sky-repeater skyBackToTop>
  @for (person of personList; track person) {
    <sky-repeater-item>
      <sky-repeater-item-title>
        {{ person.name }}
      </sky-repeater-item-title>
      <sky-repeater-item-content>
        {{ person.address }}
      </sky-repeater-item-content>
    </sky-repeater-item>
  }
</sky-repeater>

```

---

## Inline delete with repeater

**Component:** LayoutInlineDeleteRepeaterExampleComponent

**Selector:** `app-layout-inline-delete-repeater-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyInlineDeleteHarness } from '@skyux/layout/testing';

import { LayoutInlineDeleteRepeaterExampleComponent } from './example.component';

describe('Custom component inline delete example', () => {
  async function setupTest(options: { itemTitle: string }): Promise<{
    deleteHarness: SkyInlineDeleteHarness;
    fixture: ComponentFixture<LayoutInlineDeleteRepeaterExampleComponent>;
  }> {
    TestBed.configureTestingModule({
      imports: [
        LayoutInlineDeleteRepeaterExampleComponent,
        NoopAnimationsModule,
      ],
    });
    const fixture = TestBed.createComponent(
      LayoutInlineDeleteRepeaterExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    fixture.componentInstance.showInlineDelete(options.itemTitle);
    fixture.detectChanges();

    const deleteHarness = await loader.getHarness(SkyInlineDeleteHarness);

    return { deleteHarness, fixture };
  }

  it('should setup inline delete for repeater item', async () => {
    const { deleteHarness, fixture } = await setupTest({
      itemTitle: 'Individual',
    });

    await deleteHarness.clickDeleteButton();

    expect(fixture.componentInstance.repeaterDemoItems.length).toBe(2);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyInlineDeleteModule } from '@skyux/layout';
import { SkyRepeaterModule } from '@skyux/lists';
import { SkyDropdownModule } from '@skyux/popovers';

interface InlineRepeaterDemoItem {
  title: string;
  cost: string;
  description: string;
}

/**
 * @title Inline delete with repeater
 */
@Component({
  selector: 'app-layout-inline-delete-repeater-example',
  templateUrl: './example.component.html',
  imports: [SkyDropdownModule, SkyInlineDeleteModule, SkyRepeaterModule],
})
export class LayoutInlineDeleteRepeaterExampleComponent {
  protected originalRepeaterDemoItems: InlineRepeaterDemoItem[] = [
    {
      title: 'Individual',
      cost: '$75.00',
      description: '1 ticket',
    },
    {
      title: 'Foursome',
      cost: '$250.00',
      description: '4 tickets',
    },
    {
      title: 'Hole sponsor',
      cost: '$1,000.00',
      description: '8 tickets',
    },
  ];

  public repeaterDemoItems = this.originalRepeaterDemoItems;
  protected repeaterDemoShownInlineDeletes: string[] = [];

  public showInlineDelete(title: string): void {
    this.repeaterDemoShownInlineDeletes.push(title);
  }

  protected deleteItem(title: string): void {
    this.repeaterDemoItems = this.repeaterDemoItems.filter(
      (exampleItem: InlineRepeaterDemoItem) => exampleItem.title !== title,
    );

    this.repeaterDemoShownInlineDeletes =
      this.repeaterDemoShownInlineDeletes.filter(
        (exampleItem: string) => exampleItem !== title,
      );
  }

  protected cancelDeletion(title: string): void {
    this.repeaterDemoShownInlineDeletes =
      this.repeaterDemoShownInlineDeletes.filter(
        (exampleItem: string) => exampleItem !== title,
      );
  }

  protected onResetClick(): void {
    this.repeaterDemoItems = this.originalRepeaterDemoItems;
    this.repeaterDemoShownInlineDeletes = [];
  }
}

```

#### example.component.html

```html
<sky-repeater>
  @for (item of repeaterDemoItems; track item) {
    <sky-repeater-item>
      <sky-repeater-item-context-menu>
        <sky-dropdown buttonType="context-menu">
          <sky-dropdown-menu>
            <sky-dropdown-item>
              <button type="button" (click)="showInlineDelete(item.title)">
                Delete
              </button>
            </sky-dropdown-item>
          </sky-dropdown-menu>
        </sky-dropdown>
      </sky-repeater-item-context-menu>
      <sky-repeater-item-title class="sky-example-inline-delete-flex">
        <div>
          {{ item.title }}
        </div>
        <div>
          {{ item.cost }}
        </div>
      </sky-repeater-item-title>
      <sky-repeater-item-content>
        {{ item.description }}
      </sky-repeater-item-content>
      @if (repeaterDemoShownInlineDeletes.indexOf(item.title) >= 0) {
        <sky-inline-delete
          (cancelTriggered)="cancelDeletion(item.title)"
          (deleteTriggered)="deleteItem(item.title)"
        />
      }
    </sky-repeater-item>
  }
</sky-repeater>

<button class="sky-btn sky-btn-primary" type="button" (click)="onResetClick()">
  Reset Repeater
</button>

```

---

## Text expand repeater with basic setup

**Component:** LayoutTextExpandRepeaterExampleComponent

**Selector:** `app-layout-text-expand-repeater-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyTextExpandRepeaterHarness } from '@skyux/layout/testing';

import { LayoutTextExpandRepeaterExampleComponent } from './example.component';

describe('Text expand inline example', () => {
  async function setupTest(
    options: {
      dataSkyId?: string;
    } = {},
  ): Promise<{
    textExpandRepeaterHarness: SkyTextExpandRepeaterHarness;
  }> {
    await TestBed.configureTestingModule({
      imports: [LayoutTextExpandRepeaterExampleComponent, NoopAnimationsModule],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      LayoutTextExpandRepeaterExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const textExpandRepeaterHarness: SkyTextExpandRepeaterHarness =
      options.dataSkyId
        ? await loader.getHarness(
            SkyTextExpandRepeaterHarness.with({
              dataSkyId: options.dataSkyId,
            }),
          )
        : await loader.getHarness(SkyTextExpandRepeaterHarness);

    return { textExpandRepeaterHarness };
  }

  it('should set up the text expand repeater', async () => {
    const { textExpandRepeaterHarness } = await setupTest();

    await textExpandRepeaterHarness.clickExpandCollapseButton();

    await expectAsync(textExpandRepeaterHarness.isExpanded()).toBeResolvedTo(
      true,
    );

    const items = await textExpandRepeaterHarness.getItems();

    await expectAsync((await items[2].host()).text()).toBeResolvedTo(
      'Repeater item 3',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyTextExpandRepeaterModule } from '@skyux/layout';

/**
 * @title Text expand repeater with basic setup
 */
@Component({
  selector: 'app-layout-text-expand-repeater-example',
  templateUrl: './example.component.html',
  imports: [SkyTextExpandRepeaterModule],
})
export class LayoutTextExpandRepeaterExampleComponent {
  protected repeaterData: string[] = [
    'Repeater item 1',
    'Repeater item 2',
    'Repeater item 3',
    'Repeater item 4',
    'Repeater item 5',
  ];
}

```

#### example.component.html

```html
<sky-text-expand-repeater [data]="repeaterData" [maxItems]="2" />

```

---

## Infinite scroll with repeater

**Component:** ListsInfiniteScrollRepeaterExampleComponent

**Selector:** `app-lists-infinite-scroll-repeater-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyInfiniteScrollHarness } from '@skyux/lists/testing';

import { ListsInfiniteScrollRepeaterExampleComponent } from './example.component';

describe('Infinite scroll example', () => {
  async function setupTest(): Promise<{
    infiniteScrollHarness: SkyInfiniteScrollHarness;
  }> {
    await TestBed.configureTestingModule({
      imports: [
        ListsInfiniteScrollRepeaterExampleComponent,
        NoopAnimationsModule,
      ],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      ListsInfiniteScrollRepeaterExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);

    const infiniteScrollHarness: SkyInfiniteScrollHarness =
      await loader.getHarness(SkyInfiniteScrollHarness);

    return { infiniteScrollHarness };
  }

  it('should set up the component', async () => {
    const { infiniteScrollHarness } = await setupTest();

    await expectAsync(infiniteScrollHarness.isEnabled()).toBeResolvedTo(true);

    await infiniteScrollHarness.loadMore();

    await expectAsync(infiniteScrollHarness.isEnabled()).toBeResolvedTo(true);

    await infiniteScrollHarness.loadMore();

    await expectAsync(infiniteScrollHarness.isEnabled()).toBeResolvedTo(false);

    await expectAsync(infiniteScrollHarness.loadMore()).toBeRejectedWithError(
      'Unable to click the "Load more" button because the infinite scroll is not enabled.',
    );
  });
});

```

#### example.component.ts

```typescript
import { Component, OnInit } from '@angular/core';
import { SkyInfiniteScrollModule, SkyRepeaterModule } from '@skyux/lists';

import { InfiniteScrollDemoItem } from './item';

let nextId = 0;

/**
 * @title Infinite scroll with repeater
 */
@Component({
  selector: 'app-lists-infinite-scroll-repeater-example',
  styles: `
    .wrapper {
      overflow-y: auto;
      max-height: 500px;
      position: relative;
    }
  `,
  templateUrl: './example.component.html',
  imports: [SkyInfiniteScrollModule, SkyRepeaterModule],
})
export class ListsInfiniteScrollRepeaterExampleComponent implements OnInit {
  protected items: InfiniteScrollDemoItem[] = [];
  protected itemsHaveMore = true;

  public ngOnInit(): void {
    void this.#addData();
  }

  protected onScrollEnd(): void {
    if (this.itemsHaveMore) {
      void this.#addData();
    }
  }

  async #addData(): Promise<void> {
    const result = await this.#mockRemote();
    this.items = this.items.concat(result.data);
    this.itemsHaveMore = result.hasMore;
  }

  #mockRemote(): Promise<{
    data: InfiniteScrollDemoItem[];
    hasMore: boolean;
  }> {
    const data: InfiniteScrollDemoItem[] = [];

    for (let i = 0; i < 20; i++) {
      data.push({
        name: `Item #${++nextId}`,
      });
    }

    // Simulate async request.
    return new Promise((resolve) => {
      setTimeout(() => {
        resolve({
          data,
          hasMore: nextId < 50,
        });
      }, 1000);
    });
  }
}

```

#### item.ts

```typescript
export interface InfiniteScrollDemoItem {
  name: string;
}

```

#### example.component.html

```html
<div class="wrapper">
  <sky-repeater>
    @for (item of items; track item) {
      <sky-repeater-item>
        <sky-repeater-item-title>
          {{ item.name }}
        </sky-repeater-item-title>
      </sky-repeater-item>
    }
  </sky-repeater>
  <sky-infinite-scroll [enabled]="itemsHaveMore" (scrollEnd)="onScrollEnd()" />
</div>

```

---

## Repeater with drag and drop, removable items

**Component:** ListsRepeaterAddRemoveExampleComponent

**Selector:** `app-lists-repeater-add-remove-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyRepeaterHarness } from '@skyux/lists/testing';

import { ListsRepeaterAddRemoveExampleComponent } from './example.component';

describe('Repeater add remove example', () => {
  async function setupTest(): Promise<{
    el: HTMLElement;
    fixture: ComponentFixture<ListsRepeaterAddRemoveExampleComponent>;
    repeaterHarness: SkyRepeaterHarness;
  }> {
    const fixture = TestBed.createComponent(
      ListsRepeaterAddRemoveExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const repeaterHarness = await loader.getHarness(
      SkyRepeaterHarness.with({ dataSkyId: 'repeater-example' }),
    );

    const el = fixture.nativeElement as HTMLElement;

    return { el, fixture, repeaterHarness };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [ListsRepeaterAddRemoveExampleComponent, NoopAnimationsModule],
    });
  });

  it('should allow items to be expanded and collapsed', async () => {
    const { repeaterHarness } = await setupTest();

    const repeaterItems = await repeaterHarness.getRepeaterItems();

    let first = true;

    for (const item of repeaterItems) {
      await expectAsync(item.isCollapsible()).toBeResolvedTo(true);

      // in single expand mode, the first item is expanded by default
      await expectAsync(item.isExpanded()).toBeResolvedTo(first ? true : false);

      first = false;

      await item.collapse();
      await expectAsync(item.isExpanded()).toBeResolvedTo(false);

      await item.expand();
      await expectAsync(item.isExpanded()).toBeResolvedTo(true);
    }
  });

  it('should allow items to be reordered', async () => {
    const { repeaterHarness } = await setupTest();

    const expectedContent = [
      {
        title: 'Call Robert Hernandez  Completed',
        body: 'Robert recently gave a very generous gift. We should call him to thank him.',
      },
      {
        title: 'Send invitation to Spring Ball  Past due',
        body: "The Spring Ball is coming up soon. Let's get those invitations out!",
      },
      {
        title: 'Assign prospects  Due tomorrow',
        body: 'There are 14 new prospects who are not assigned to fundraisers.',
      },
      {
        title: 'Process gift receipts  Due next week',
        body: 'There are 28 recent gifts that are not receipted.',
      },
    ];

    let repeaterItems = await repeaterHarness.getRepeaterItems();

    expect(repeaterItems).toBeDefined();
    expect(repeaterItems.length).toBe(expectedContent.length);

    for (const item of repeaterItems) {
      await expectAsync(item.isReorderable()).toBeResolvedTo(true);
    }

    await expectAsync(repeaterItems[1].getTitleText()).toBeResolvedTo(
      expectedContent[1].title,
    );

    await repeaterItems[1].sendToTop();
    repeaterItems = await repeaterHarness.getRepeaterItems();

    await expectAsync(repeaterItems[1].getTitleText()).toBeResolvedTo(
      expectedContent[0].title,
    );
  });

  it('should allow items to be added and removed', async () => {
    const { repeaterHarness, el, fixture } = await setupTest();

    let repeaterItems = await repeaterHarness.getRepeaterItems();

    expect(repeaterItems).toBeDefined();
    expect(repeaterItems.length).toBe(4);

    for (const item of repeaterItems) {
      await expectAsync(item.isSelectable()).toBeResolvedTo(true);
    }

    const addButton = el.querySelector<HTMLButtonElement>(
      '[data-sky-id="add-button"]',
    );

    const removeButton = el.querySelector<HTMLButtonElement>(
      '[data-sky-id="remove-button"]',
    );

    addButton?.click();
    fixture.detectChanges();

    repeaterItems = await repeaterHarness.getRepeaterItems();
    expect(repeaterItems).toBeDefined();
    expect(repeaterItems.length).toBe(5);

    await expectAsync(repeaterItems[0].isSelected()).toBeResolvedTo(false);
    await repeaterItems[0].select();

    await expectAsync(repeaterItems[0].isSelected()).toBeResolvedTo(true);
    await expectAsync(repeaterItems[1].isSelected()).toBeResolvedTo(false);

    await repeaterItems[1].select();
    await expectAsync(repeaterItems[1].isSelected()).toBeResolvedTo(true);

    removeButton?.click();
    fixture.detectChanges();

    repeaterItems = await repeaterHarness.getRepeaterItems();
    expect(repeaterItems).toBeDefined();
    expect(repeaterItems.length).toBe(3);
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyRepeaterModule } from '@skyux/lists';
import { SkyDropdownModule } from '@skyux/popovers';

import { Item } from './item';

let nextId = 0;

/**
 * @title Repeater with drag and drop, removable items
 */
@Component({
  selector: 'app-lists-repeater-add-remove-example',
  templateUrl: './example.component.html',
  styleUrls: ['./example.component.scss'],
  imports: [SkyDropdownModule, SkyRepeaterModule],
})
export class ListsRepeaterAddRemoveExampleComponent {
  protected items: Item[] = [
    {
      title: 'Call Robert Hernandez',
      note: 'Robert recently gave a very generous gift. We should call him to thank him.',
      status: 'Completed',
      isSelected: false,
    },
    {
      title: 'Send invitation to Spring Ball',
      note: "The Spring Ball is coming up soon. Let's get those invitations out!",
      status: 'Past due',
      isSelected: false,
    },
    {
      title: 'Assign prospects',
      note: 'There are 14 new prospects who are not assigned to fundraisers.',
      status: 'Due tomorrow',
      isSelected: false,
    },
    {
      title: 'Process gift receipts',
      note: 'There are 28 recent gifts that are not receipted.',
      status: 'Due next week',
      isSelected: false,
    },
  ];

  protected addItem(): void {
    this.items.push({
      title: 'New reminder ' + ++nextId,
      note: 'This is a new reminder',
      status: 'Active',
      isSelected: false,
    });
  }

  protected changeItems(tags: Item[]): void {
    console.log('Tags in order ', tags);
  }

  protected onActionClicked(buttonText: string): void {
    alert(buttonText + ' was clicked!');
  }

  protected removeItems(): void {
    this.items = this.items.filter((item) => !item.isSelected);
  }
}

```

#### item.ts

```typescript
export interface Item {
  title: string;
  note: string;
  status: string;
  isSelected: boolean;
}

```

#### example.component.html

```html
<div class="sky-margin-stacked-lg">
  <sky-repeater
    data-sky-id="repeater-example"
    [expandMode]="'single'"
    [reorderable]="true"
    (orderChange)="changeItems($event)"
  >
    @for (item of items; track item) {
      <sky-repeater-item
        [selectable]="true"
        [tag]="item.note"
        [(isSelected)]="item.isSelected"
      >
        <sky-repeater-item-title class="example-repeater-flex">
          <div class="example-repeater-item-title">
            {{ item.title }}
          </div>
          <div>
            {{ item.status }}
          </div>
        </sky-repeater-item-title>
        <sky-repeater-item-context-menu>
          <sky-dropdown buttonType="context-menu">
            <sky-dropdown-menu>
              <sky-dropdown-item>
                <button type="button" (click)="onActionClicked('Action 1')">
                  Action 1
                </button>
              </sky-dropdown-item>
              <sky-dropdown-item>
                <button type="button" (click)="onActionClicked('Action 2')">
                  Action 2
                </button>
              </sky-dropdown-item>
            </sky-dropdown-menu>
          </sky-dropdown>
        </sky-repeater-item-context-menu>
        <sky-repeater-item-content>
          {{ item.note }}
        </sky-repeater-item-content>
      </sky-repeater-item>
    }
  </sky-repeater>
</div>

<button
  data-sky-id="add-button"
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="addItem()"
>
  Add item
</button>

<button
  data-sky-id="remove-button"
  class="sky-btn sky-btn-default sky-margin-inline-sm"
  type="button"
  (click)="removeItems()"
>
  Remove selected items
</button>

```

#### example.component.scss

```css
.example-repeater-flex {
  display: flex;
  flex-wrap: wrap;

  .example-repeater-item-title {
    flex-grow: 1;
  }
}

```

---

## Repeater with basic setup

**Component:** ListsRepeaterBasicExampleComponent

**Selector:** `app-lists-repeater-basic-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import {
  SkyRepeaterHarness,
  SkyRepeaterItemHarness,
} from '@skyux/lists/testing';

import { ListsRepeaterBasicExampleComponent } from './example.component';

describe('Repeater basic example', () => {
  async function setupTest(): Promise<{
    repeaterHarness: SkyRepeaterHarness | null;
    repeaterItems: SkyRepeaterItemHarness[] | null;
    fixture: ComponentFixture<ListsRepeaterBasicExampleComponent>;
  }> {
    const fixture = TestBed.createComponent(ListsRepeaterBasicExampleComponent);
    const loader = TestbedHarnessEnvironment.loader(fixture);

    const repeaterHarness = await loader.getHarness(
      SkyRepeaterHarness.with({ dataSkyId: 'repeater-example' }),
    );

    const repeaterItems = await repeaterHarness.getRepeaterItems();

    return { repeaterHarness, repeaterItems, fixture };
  }

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [ListsRepeaterBasicExampleComponent, NoopAnimationsModule],
    });
  });

  it('should display the repeater item contents', async () => {
    const { repeaterItems } = await setupTest();

    const expectedContent = [
      {
        title: 'Call Robert Hernandez  Completed',
        body: 'Robert recently gave a very generous gift. We should call him to thank him.',
      },
      {
        title: 'Send invitation to Spring Ball  Past due',
        body: "The Spring Ball is coming up soon. Let's get those invitations out!",
      },
      {
        title: 'Assign prospects  Due tomorrow',
        body: 'There are 14 new prospects who are not assigned to fundraisers.',
      },
      {
        title: 'Process gift receipts  Due next week',
        body: 'There are 28 recent gifts that are not receipted.',
      },
      {
        title: '',
        body: 'Three other tasks were not displayed',
      },
    ];

    expect(repeaterItems?.length).toBe(expectedContent.length);

    if (repeaterItems) {
      for (let i = 0; i < repeaterItems.length; i++) {
        await expectAsync(repeaterItems[i].getTitleText()).toBeResolvedTo(
          expectedContent[i].title,
        );
        await expectAsync(repeaterItems[i].getContentText()).toBeResolvedTo(
          expectedContent[i].body,
        );
      }
    }
  });
});

```

#### example.component.ts

```typescript
import { Component } from '@angular/core';
import { SkyRepeaterModule } from '@skyux/lists';
import { SkyDropdownModule } from '@skyux/popovers';

/**
 * @title Repeater with basic setup
 */
@Component({
  selector: 'app-lists-repeater-basic-example',
  templateUrl: './example.component.html',
  styleUrls: ['./example.component.scss'],
  imports: [SkyDropdownModule, SkyRepeaterModule],
})
export class ListsRepeaterBasicExampleComponent {
  protected items: {
    note: string;
    status?: string;
    title?: string;
    accessibilityLabel?: string;
  }[] = [
    {
      title: 'Call Robert Hernandez',
      note: 'Robert recently gave a very generous gift. We should call him to thank him.',
      status: 'Completed',
    },
    {
      title: 'Send invitation to Spring Ball',
      note: "The Spring Ball is coming up soon. Let's get those invitations out!",
      status: 'Past due',
    },
    {
      title: 'Assign prospects',
      note: 'There are 14 new prospects who are not assigned to fundraisers.',
      status: 'Due tomorrow',
    },
    {
      title: 'Process gift receipts',
      note: 'There are 28 recent gifts that are not receipted.',
      status: 'Due next week',
    },
    {
      note: 'Three other tasks were not displayed',
      accessibilityLabel: 'Other tasks',
    },
  ];

  protected onActionClicked(buttonText: string): void {
    alert(buttonText + ' was clicked!');
  }
}

```

#### example.component.html

```html
<sky-repeater data-sky-id="repeater-example">
  @for (item of items; track item) {
    <sky-repeater-item [itemName]="item.accessibilityLabel">
      @if (item.title) {
        <sky-repeater-item-title class="example-repeater-flex">
          <div class="example-repeater-item-title">
            {{ item.title }}
          </div>
          <div>
            {{ item.status }}
          </div>
        </sky-repeater-item-title>
      }
      <sky-repeater-item-context-menu>
        <sky-dropdown buttonType="context-menu">
          <sky-dropdown-menu>
            <sky-dropdown-item>
              <button
                type="button"
                [attr.aria-label]="
                  'Action 1 for ' + (item.title ?? item.accessibilityLabel)
                "
                (click)="onActionClicked('Action 1')"
              >
                Action 1
              </button>
            </sky-dropdown-item>
            <sky-dropdown-item>
              <button
                type="button"
                [attr.aria-label]="
                  'Action 2 for ' + (item.title ?? item.accessibilityLabel)
                "
                (click)="onActionClicked('Action 2')"
              >
                Action 2
              </button>
            </sky-dropdown-item>
          </sky-dropdown-menu>
        </sky-dropdown>
      </sky-repeater-item-context-menu>
      <sky-repeater-item-content>
        {{ item.note }}
      </sky-repeater-item-content>
    </sky-repeater-item>
  }
</sky-repeater>

```

#### example.component.scss

```css
.example-repeater-flex {
  display: flex;
  flex-wrap: wrap;

  .example-repeater-item-title {
    flex-grow: 1;
  }
}

```

---

## Repeater with inline form

**Component:** ListsRepeaterInlineFormExampleComponent

**Selector:** `app-lists-repeater-inline-form-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.ts

```typescript
import { Component, inject } from '@angular/core';
import {
  FormBuilder,
  FormControl,
  FormGroup,
  FormsModule,
  ReactiveFormsModule,
} from '@angular/forms';
import { SkyInputBoxModule } from '@skyux/forms';
import { SkyIconModule } from '@skyux/icon';
import {
  SkyInlineFormButtonLayout,
  SkyInlineFormCloseArgs,
  SkyInlineFormConfig,
} from '@skyux/inline-form';
import { SkyRepeaterModule } from '@skyux/lists';

interface DemoForm {
  id: FormControl<string>;
  note: FormControl<string>;
  title: FormControl<string>;
}

interface Item {
  id: string;
  title: string | undefined;
  note: string | undefined;
}

/**
 * @title Repeater with inline form
 */
@Component({
  selector: 'app-lists-repeater-inline-form-example',
  templateUrl: './example.component.html',
  imports: [
    FormsModule,
    ReactiveFormsModule,
    SkyIconModule,
    SkyInputBoxModule,
    SkyRepeaterModule,
  ],
})
export class ListsRepeaterInlineFormExampleComponent {
  protected activeInlineFormId: string | undefined;
  protected formGroup: FormGroup<DemoForm>;

  protected inlineFormConfig: SkyInlineFormConfig = {
    buttonLayout: SkyInlineFormButtonLayout.SaveCancel,
  };

  protected items: Item[] = [
    {
      id: '1',
      title: '2019 Spring Gala',
      note: 'Gala for friends and family',
    },
    {
      id: '2',
      title: '2019 Special Winter Event',
      note: 'A special event',
    },
    {
      id: '3',
      title: '2019 Donor Appreciation Event',
      note: 'Event for all donors and families',
    },
    {
      id: '4',
      title: '2020 Spring Gala',
      note: 'Gala for friends and family',
    },
  ];

  constructor() {
    this.formGroup = inject(FormBuilder).group({
      id: new FormControl('', { nonNullable: true }),
      title: new FormControl('', { nonNullable: true }),
      note: new FormControl('', { nonNullable: true }),
    });
  }

  protected showInlineForm(item: Item): void {
    this.activeInlineFormId = item.id;
    this.formGroup.patchValue({
      note: item.note,
      title: item.title,
    });
  }

  protected onInlineFormClose(args: SkyInlineFormCloseArgs): void {
    if (args.reason === 'save') {
      const found = this.items.find(
        (item) => item.id === this.activeInlineFormId,
      );
      if (found) {
        found.note = this.formGroup.value.note;
        found.title = this.formGroup.value.title;
      }
    }

    this.formGroup.patchValue({
      note: undefined,
      title: undefined,
    });

    // Close the active form.
    this.activeInlineFormId = undefined;
  }
}

```

#### example.component.html

```html
<sky-repeater>
  @for (item of items; track item) {
    <sky-repeater-item
      [inlineFormConfig]="inlineFormConfig"
      [inlineFormTemplate]="inlineFormTemplate"
      [showInlineForm]="activeInlineFormId === item.id"
      (inlineFormClose)="onInlineFormClose($event)"
    >
      <sky-repeater-item-title>
        <div class="sky-font-emphasized">
          {{ item.title }}
        </div>
      </sky-repeater-item-title>
      <sky-repeater-item-context-menu>
        <button
          aria-label="Edit"
          class="sky-btn sky-btn-icon-borderless"
          type="button"
          (click)="showInlineForm(item)"
        >
          <sky-icon iconName="edit" />
        </button>
      </sky-repeater-item-context-menu>

      <sky-repeater-item-content>
        {{ item.note }}
      </sky-repeater-item-content>
    </sky-repeater-item>
  }
</sky-repeater>

<ng-template #inlineFormTemplate>
  <form novalidate [formGroup]="formGroup">
    <sky-input-box labelText="Title" stacked="true">
      <input formControlName="title" type="text" />
    </sky-input-box>
    <sky-input-box labelText="Note">
      <input formControlName="note" type="text" />
    </sky-input-box>
  </form>
</ng-template>

```

---