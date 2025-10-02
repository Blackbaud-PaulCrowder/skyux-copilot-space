---
component: 'infinite-scroll'
type: 'code-examples'
description: 'Code examples for the infinite-scroll component.'
---

# Infinite Scroll Code Examples

## Infinite scroll with back to top directive

**Component:** LayoutBackToTopInfiniteScrollExampleComponent

**Selector:** `app-layout-back-to-top-infinite-scroll-example`

**Import Path:** `@skyux/code-examples`

### Code Files

#### example.component.spec.ts

```typescript
import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
import { TestBed } from '@angular/core/testing';
import { NoopAnimationsModule } from '@angular/platform-browser/animations';
import { SkyAppTestUtility } from '@skyux-sdk/testing';
import { SkyBackToTopHarness } from '@skyux/layout/testing';
import { SkyInfiniteScrollHarness } from '@skyux/lists/testing';

import { LayoutBackToTopInfiniteScrollExampleComponent } from './example.component';

describe('Back to top repeater with infinite scroll example', () => {
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
      imports: [
        LayoutBackToTopInfiniteScrollExampleComponent,
        NoopAnimationsModule,
      ],
    }).compileComponents();

    const fixture = TestBed.createComponent(
      LayoutBackToTopInfiniteScrollExampleComponent,
    );
    const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    const target = getBackToTopTarget();

    expect(isElementInView(target)).toBe(true);
    await expectAsync(loader.getHarness(SkyBackToTopHarness)).toBeRejected();

    const infiniteScrollHarness = await loader.getHarness(
      SkyInfiniteScrollHarness,
    );

    await infiniteScrollHarness.loadMore();

    fixture.detectChanges();
    await fixture.whenStable();

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
import { Component, OnInit } from '@angular/core';
import { SkyBackToTopModule } from '@skyux/layout';
import { SkyInfiniteScrollModule, SkyRepeaterModule } from '@skyux/lists';

import { Person } from './person';

/**
 * @title Infinite scroll with back to top directive
 * @docsDemoHidden
 */
@Component({
  selector: 'app-layout-back-to-top-infinite-scroll-example',
  templateUrl: './example.component.html',
  imports: [SkyBackToTopModule, SkyInfiniteScrollModule, SkyRepeaterModule],
})
export class LayoutBackToTopInfiniteScrollExampleComponent implements OnInit {
  public hasMore = true;

  public personList: Person[] = [];

  public personDataSet = [
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

  public ngOnInit(): void {
    void this.#addData(0, 10);
  }

  public onScrollEnd(): void {
    void this.#addData(this.personList.length, 10);
  }

  async #addData(start: number, rowSize: number): Promise<void> {
    if (this.hasMore) {
      const result = await this.mockRemote(start, rowSize);
      this.personList = this.personList.concat(result.data);
      this.hasMore = result.hasMore;
    }
  }

  /**
   * Simulate a remote request.
   */
  private mockRemote(
    start: number,
    rowSize: number,
  ): Promise<{ data: Person[]; hasMore: boolean }> {
    const data: Person[] = [];

    for (let i = 0; i < rowSize; i++) {
      if (this.personDataSet[start + i]) {
        data.push(this.personDataSet[start + i]);
      }
    }

    return new Promise((resolve) => {
      setTimeout(() => {
        resolve({
          data,
          hasMore: this.personList.length < this.personDataSet.length,
        });
      }, 1000);
    });
  }
}

```

#### person.ts

```typescript
export interface Person {
  name: string;
  address: string;
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
<sky-infinite-scroll [enabled]="hasMore" (scrollEnd)="onScrollEnd()" />

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