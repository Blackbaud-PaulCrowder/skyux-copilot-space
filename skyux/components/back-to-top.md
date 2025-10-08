# Design

                  Skip to Main Content

 Back to top
===========

The back to top button in the bottom left of the page returns users to an element after they scroll away from it.

 Usage
------

### Use when

Use the back to top button when users need a quick way to access the top of [infinite scroll lists](/skyux/components/infinite-scroll.md) or other long lists.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/backtotop/backtotop-usage.1fac8fef1a83c38d1299788de071cc5d.png)

Use the the back to top bar with infinite scroll lists.

 Anatomy
--------

1

Back to top button

2

Button bar

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/backtotop/backtotop-anatomy.24bd9005bf359b41c87d26c4f8eb449f.png)

 Related information
--------------------

### Components

*   [Data grid](/skyux/components/data-grid.md)
*   [Infinite scroll](/skyux/components/infinite-scroll.md)
*   [Repeater](/skyux/components/repeater.md)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/back-to-top/back-to-top.module.ts#L14) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyBackToTopModule
-------------------

Type: Module

`import { SkyBackToTopModule } from '@skyux/layout';`

 SkyBackToTopDirective
----------------------

Type: Directive

Selector: `[skyBackToTop]`

Associates a button with an element on the page and displays that button to return to the element after users scroll away.

### Inputs

#### `skyBackToTop: "" | SkyBackToTopOptions | undefined`

Configuration options for the back to top component.

#### `skyBackToTopMessageStream: Subject<SkyBackToTopMessage> | undefined`

The observable to send commands to the back to top component. The commands respect the `SkyBackToTopMessage` type.

 SkyBackToTopOptions
--------------------

Type: Interface

Specifies options for the back to top component.

    interface SkyBackToTopOptions {
      buttonHidden?: boolean;
    }

### Properties

#### `buttonHidden?: boolean`

Whether to hide the back to top button.

 SkyBackToTopMessage
--------------------

Type: Interface

Specifies messages to send to the back to top component.

    interface SkyBackToTopMessage {
      type?: BackToTop;
    }

### Properties

#### `type?: BackToTop`

The type of message to send.

 SkyBackToTopMessageType
------------------------

Type: Enumeration

The type of message to send to the back to top component.

    enum SkyBackToTopMessageType {
      BackToTop = 0,
    }

### Properties

#### `SkyBackToTopMessageType.BackToTop`

Scrolls the element back to the top.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyBackToTopHarness
--------------------

Type: Class

`import { SkyBackToTopHarness } from '@skyux/layout/testing';`

Harness for interacting with a back to top component in tests.

### Methods

#### `clickBackToTop(): Promise<void>`

Clicks the back to top button.

#### Returns

`Promise<void>`

# Development

                  Skip to Main Content

 Back to top
===========

The back to top button in the bottom left of the page returns users to an element after they scroll away from it.

 Usage
------

### Use when

Use the back to top button when users need a quick way to access the top of [infinite scroll lists](/skyux/components/infinite-scroll.md) or other long lists.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/backtotop/backtotop-usage.1fac8fef1a83c38d1299788de071cc5d.png)

Use the the back to top bar with infinite scroll lists.

 Anatomy
--------

1

Back to top button

2

Button bar

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/backtotop/backtotop-anatomy.24bd9005bf359b41c87d26c4f8eb449f.png)

 Related information
--------------------

### Components

*   [Data grid](/skyux/components/data-grid.md)
*   [Infinite scroll](/skyux/components/infinite-scroll.md)
*   [Repeater](/skyux/components/repeater.md)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/back-to-top/back-to-top.module.ts#L14) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyBackToTopModule
-------------------

Type: Module

`import { SkyBackToTopModule } from '@skyux/layout';`

 SkyBackToTopDirective
----------------------

Type: Directive

Selector: `[skyBackToTop]`

Associates a button with an element on the page and displays that button to return to the element after users scroll away.

### Inputs

#### `skyBackToTop: "" | SkyBackToTopOptions | undefined`

Configuration options for the back to top component.

#### `skyBackToTopMessageStream: Subject<SkyBackToTopMessage> | undefined`

The observable to send commands to the back to top component. The commands respect the `SkyBackToTopMessage` type.

 SkyBackToTopOptions
--------------------

Type: Interface

Specifies options for the back to top component.

    interface SkyBackToTopOptions {
      buttonHidden?: boolean;
    }

### Properties

#### `buttonHidden?: boolean`

Whether to hide the back to top button.

 SkyBackToTopMessage
--------------------

Type: Interface

Specifies messages to send to the back to top component.

    interface SkyBackToTopMessage {
      type?: BackToTop;
    }

### Properties

#### `type?: BackToTop`

The type of message to send.

 SkyBackToTopMessageType
------------------------

Type: Enumeration

The type of message to send to the back to top component.

    enum SkyBackToTopMessageType {
      BackToTop = 0,
    }

### Properties

#### `SkyBackToTopMessageType.BackToTop`

Scrolls the element back to the top.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyBackToTopHarness
--------------------

Type: Class

`import { SkyBackToTopHarness } from '@skyux/layout/testing';`

Harness for interacting with a back to top component in tests.

### Methods

#### `clickBackToTop(): Promise<void>`

Clicks the back to top button.

#### Returns

`Promise<void>`

# Examples

                    Skip to Main Content

 Back to top
===========

The back to top button in the bottom left of the page returns users to an element after they scroll away from it.Usage
------

### Use when

Use the back to top button when users need a quick way to access the top of [infinite scroll lists](/skyux/components/infinite-scroll.md) or other long lists.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/backtotop/backtotop-usage.1fac8fef1a83c38d1299788de071cc5d.png)

Use the the back to top bar with infinite scroll lists.

 Anatomy
--------

1

Back to top button

2

Button bar

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/backtotop/backtotop-anatomy.24bd9005bf359b41c87d26c4f8eb449f.png)

 Related information
--------------------

### Components

*   [Data grid](/skyux/components/data-grid.md)
*   [Infinite scroll](/skyux/components/infinite-scroll.md)
*   [Repeater](/skyux/components/repeater.md)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/back-to-top/back-to-top.module.ts#L14) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyBackToTopModule
-------------------

Type: Module

`import { SkyBackToTopModule } from '@skyux/layout';`

 SkyBackToTopDirective
----------------------

Type: Directive

Selector: `[skyBackToTop]`

Associates a button with an element on the page and displays that button to return to the element after users scroll away.

### Inputs

#### `skyBackToTop: "" | SkyBackToTopOptions | undefined`

Configuration options for the back to top component.

#### `skyBackToTopMessageStream: Subject<SkyBackToTopMessage> | undefined`

The observable to send commands to the back to top component. The commands respect the `SkyBackToTopMessage` type.

 SkyBackToTopOptions
--------------------

Type: Interface

Specifies options for the back to top component.

    interface SkyBackToTopOptions {
      buttonHidden?: boolean;
    }

### Properties

#### `buttonHidden?: boolean`

Whether to hide the back to top button.

 SkyBackToTopMessage
--------------------

Type: Interface

Specifies messages to send to the back to top component.

    interface SkyBackToTopMessage {
      type?: BackToTop;
    }

### Properties

#### `type?: BackToTop`

The type of message to send.

 SkyBackToTopMessageType
------------------------

Type: Enumeration

The type of message to send to the back to top component.

    enum SkyBackToTopMessageType {
      BackToTop = 0,
    }

### Properties

#### `SkyBackToTopMessageType.BackToTop`

Scrolls the element back to the top.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyBackToTopHarness
--------------------

Type: Class

`import { SkyBackToTopHarness } from '@skyux/layout/testing';`

Harness for interacting with a back to top component in tests.

### Methods

#### `clickBackToTop(): Promise<void>`

Clicks the back to top button.

#### Returns

`Promise<void>`

### Infinite scroll with back to top directive

Edit in StackBlitz

Open this code example in StackBlitz to view the demo.

Show code

Copy

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
Copy

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
Copy

    export interface Person {
      name: string;
      address: string;
    }

Copy

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
### Repeater with back to top directive

Edit in StackBlitz

Open this code example in StackBlitz to view the demo.

Show code

Copy

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
Copy

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

Copy

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

# Testing

                  Skip to Main Content

 Back to top
===========

The back to top button in the bottom left of the page returns users to an element after they scroll away from it.

 Usage
------

### Use when

Use the back to top button when users need a quick way to access the top of [infinite scroll lists](/skyux/components/infinite-scroll.md) or other long lists.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/backtotop/backtotop-usage.1fac8fef1a83c38d1299788de071cc5d.png)

Use the the back to top bar with infinite scroll lists.

 Anatomy
--------

1

Back to top button

2

Button bar

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/backtotop/backtotop-anatomy.24bd9005bf359b41c87d26c4f8eb449f.png)

 Related information
--------------------

### Components

*   [Data grid](/skyux/components/data-grid.md)
*   [Infinite scroll](/skyux/components/infinite-scroll.md)
*   [Repeater](/skyux/components/repeater.md)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/back-to-top/back-to-top.module.ts#L14) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyBackToTopModule
-------------------

Type: Module

`import { SkyBackToTopModule } from '@skyux/layout';`

 SkyBackToTopDirective
----------------------

Type: Directive

Selector: `[skyBackToTop]`

Associates a button with an element on the page and displays that button to return to the element after users scroll away.

### Inputs

#### `skyBackToTop: "" | SkyBackToTopOptions | undefined`

Configuration options for the back to top component.

#### `skyBackToTopMessageStream: Subject<SkyBackToTopMessage> | undefined`

The observable to send commands to the back to top component. The commands respect the `SkyBackToTopMessage` type.

 SkyBackToTopOptions
--------------------

Type: Interface

Specifies options for the back to top component.

    interface SkyBackToTopOptions {
      buttonHidden?: boolean;
    }

### Properties

#### `buttonHidden?: boolean`

Whether to hide the back to top button.

 SkyBackToTopMessage
--------------------

Type: Interface

Specifies messages to send to the back to top component.

    interface SkyBackToTopMessage {
      type?: BackToTop;
    }

### Properties

#### `type?: BackToTop`

The type of message to send.

 SkyBackToTopMessageType
------------------------

Type: Enumeration

The type of message to send to the back to top component.

    enum SkyBackToTopMessageType {
      BackToTop = 0,
    }

### Properties

#### `SkyBackToTopMessageType.BackToTop`

Scrolls the element back to the top.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyBackToTopHarness
--------------------

Type: Class

`import { SkyBackToTopHarness } from '@skyux/layout/testing';`

Harness for interacting with a back to top component in tests.

### Methods

#### `clickBackToTop(): Promise<void>`

Clicks the back to top button.

#### Returns

`Promise<void>`