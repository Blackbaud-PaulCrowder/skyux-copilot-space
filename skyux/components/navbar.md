# Development

                   Skip to Main Content

 Navbar
======

The navbar displays top-level navigation items that can include sub-navigation items in dropdown menus.

 Installation
-------------

NPM package

`@skyux/navbar`[View in NPM](https://www.npmjs.com/package/@skyux/navbar) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/navbar/src/lib/modules/navbar/navbar.module.ts#L12) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/navbar`Copy None found.

 SkyNavbarModule
----------------

Type: Module

`import { SkyNavbarModule } from '@skyux/navbar';`

 SkyNavbarComponent
-------------------

Type: Component

Selector: `sky-navbar`

Displays top-level navigation.

 SkyNavbarItemComponent
-----------------------

Type: Component

Selector: `sky-navbar-item`

Displays a navigation item in the navbar. It can include sub-navigation items in a dropdown menu.

### Inputs

#### `active: boolean | undefined`

Whether the navigation item is active.

Default: `false`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyNavbarHarness
-----------------

Type: Class

`import { SkyNavbarHarness } from '@skyux/navbar/testing';`

Harness for interacting with a navbar component in tests.

### Methods

#### `getItem(filter: SkyNavbarItemHarnessFilters): Promise<SkyNavbarItemHarness>`

Gets a specific navbar item based on the filter criteria.

#### Parameters

##### `filter: SkyNavbarItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyNavbarItemHarness>`

#### `getItems(filters?: SkyNavbarItemHarnessFilters): Promise<SkyNavbarItemHarness[]>`

Gets an array of navbar items based on the filter criteria. If no filter is provided, returns all navbar items.

#### Parameters

##### `filters?: SkyNavbarItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyNavbarItemHarness[]>`

#### `SkyNavbarHarness.with(filters: SkyNavbarHarnessFilters): HarnessPredicate<SkyNavbarHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyNavbarHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyNavbarHarnessFilters`

#### Returns

`HarnessPredicate<SkyNavbarHarness>`

 SkyNavbarHarnessFilters
------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyNavbarHarness` instances.

    interface SkyNavbarHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyNavbarItemHarness
---------------------

Type: Class

`import { SkyNavbarItemHarness } from '@skyux/navbar/testing';`

Harness to interact with a navbar item component in tests.

### Methods

#### `isActive(): Promise<boolean>`

Whether the navbar item is active.

#### Returns

`Promise<boolean>`

#### `queryHarness(query: HarnessQuery<T>): Promise<T>`

Returns a child harness or throws an error if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<T>`

#### `queryHarnesses(harness: HarnessQuery<T>): Promise<T[]>`

Returns child harnesses.

#### Parameters

##### `harness: HarnessQuery<T>`

#### Returns

`Promise<T[]>`

#### `queryHarnessOrNull(query: HarnessQuery<T>): Promise<null | T>`

Returns a child harness or null if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<null | T>`

#### `querySelector(selector: string): Promise<TestElement>`

Returns a child test element or throws an error if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement>`

#### `querySelectorAll(selector: string): Promise<TestElement[]>`

Returns child test elements.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement[]>`

#### `querySelectorOrNull(selector: string): Promise<null | TestElement>`

Returns a child test element or null if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<null | TestElement>`

#### `SkyNavbarItemHarness.with(filters: SkyNavbarItemHarnessFilters): HarnessPredicate<SkyNavbarItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyNavbarItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyNavbarItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyNavbarItemHarness>`

 SkyNavbarItemHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyNavbarItemHarness` instances.

    interface SkyNavbarItemHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Examples

                     Skip to Main Content

 Navbar
======

The navbar displays top-level navigation items that can include sub-navigation items in dropdown menus.

Installation
-------------

NPM package

`@skyux/navbar`[View in NPM](https://www.npmjs.com/package/@skyux/navbar) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/navbar/src/lib/modules/navbar/navbar.module.ts#L12) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/navbar`Copy None found.

 SkyNavbarModule
----------------

Type: Module

`import { SkyNavbarModule } from '@skyux/navbar';`

 SkyNavbarComponent
-------------------

Type: Component

Selector: `sky-navbar`

Displays top-level navigation.

 SkyNavbarItemComponent
-----------------------

Type: Component

Selector: `sky-navbar-item`

Displays a navigation item in the navbar. It can include sub-navigation items in a dropdown menu.

### Inputs

#### `active: boolean | undefined`

Whether the navigation item is active.

Default: `false`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyNavbarHarness
-----------------

Type: Class

`import { SkyNavbarHarness } from '@skyux/navbar/testing';`

Harness for interacting with a navbar component in tests.

### Methods

#### `getItem(filter: SkyNavbarItemHarnessFilters): Promise<SkyNavbarItemHarness>`

Gets a specific navbar item based on the filter criteria.

#### Parameters

##### `filter: SkyNavbarItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyNavbarItemHarness>`

#### `getItems(filters?: SkyNavbarItemHarnessFilters): Promise<SkyNavbarItemHarness[]>`

Gets an array of navbar items based on the filter criteria. If no filter is provided, returns all navbar items.

#### Parameters

##### `filters?: SkyNavbarItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyNavbarItemHarness[]>`

#### `SkyNavbarHarness.with(filters: SkyNavbarHarnessFilters): HarnessPredicate<SkyNavbarHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyNavbarHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyNavbarHarnessFilters`

#### Returns

`HarnessPredicate<SkyNavbarHarness>`

 SkyNavbarHarnessFilters
------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyNavbarHarness` instances.

    interface SkyNavbarHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyNavbarItemHarness
---------------------

Type: Class

`import { SkyNavbarItemHarness } from '@skyux/navbar/testing';`

Harness to interact with a navbar item component in tests.

### Methods

#### `isActive(): Promise<boolean>`

Whether the navbar item is active.

#### Returns

`Promise<boolean>`

#### `queryHarness(query: HarnessQuery<T>): Promise<T>`

Returns a child harness or throws an error if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<T>`

#### `queryHarnesses(harness: HarnessQuery<T>): Promise<T[]>`

Returns child harnesses.

#### Parameters

##### `harness: HarnessQuery<T>`

#### Returns

`Promise<T[]>`

#### `queryHarnessOrNull(query: HarnessQuery<T>): Promise<null | T>`

Returns a child harness or null if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<null | T>`

#### `querySelector(selector: string): Promise<TestElement>`

Returns a child test element or throws an error if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement>`

#### `querySelectorAll(selector: string): Promise<TestElement[]>`

Returns child test elements.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement[]>`

#### `querySelectorOrNull(selector: string): Promise<null | TestElement>`

Returns a child test element or null if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<null | TestElement>`

#### `SkyNavbarItemHarness.with(filters: SkyNavbarItemHarnessFilters): HarnessPredicate<SkyNavbarItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyNavbarItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyNavbarItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyNavbarItemHarness>`

 SkyNavbarItemHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyNavbarItemHarness` instances.

    interface SkyNavbarItemHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

### Navbar with basic setup

Edit in StackBlitz

[Selected item](/skyux/)

Show dropdown

Show code

Copy

    <sky-navbar data-sky-id="basic-navbar">
      <sky-navbar-item data-sky-id="navbar-item-1">
        <a
          routerLink="/"
          routerLinkActive="sky-navbar-item-active"
          (click)="onItemClick('Selected item')"
        >
          Selected item
        </a>
      </sky-navbar-item>
      <sky-navbar-item data-sky-id="navbar-item-2">
        <sky-dropdown>
          <sky-dropdown-button> Show dropdown </sky-dropdown-button>
          <sky-dropdown-menu>
            <sky-dropdown-item>
              <a routerLink="/" (click)="onItemClick('Item 1')"> Item 1 </a>
            </sky-dropdown-item>
            <sky-dropdown-item>
              <a routerLink="/" (click)="onItemClick('Item 2')"> Item 2 </a>
            </sky-dropdown-item>
            <sky-dropdown-item>
              <a routerLink="/" (click)="onItemClick('Item 3')"> Item 3 </a>
            </sky-dropdown-item>
          </sky-dropdown-menu>
        </sky-dropdown>
      </sky-navbar-item>
    </sky-navbar>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { provideRouter } from '@angular/router';
    import { SkyNavbarHarness } from '@skyux/navbar/testing';
    
    import { NavbarExampleComponent } from './example.component';
    
    describe('Basic navbar example', () => {
      async function setupTest(
        options: {
          dataSkyId?: string;
        } = {},
      ): Promise<{
        navbarHarness: SkyNavbarHarness;
        fixture: ComponentFixture<NavbarExampleComponent>;
      }> {
        await TestBed.configureTestingModule({
          imports: [NavbarExampleComponent],
          providers: [provideRouter([])],
        }).compileComponents();
    
        const fixture = TestBed.createComponent(NavbarExampleComponent);
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    
        const navbarHarness: SkyNavbarHarness = options.dataSkyId
          ? await loader.getHarness(
              SkyNavbarHarness.with({
                dataSkyId: options.dataSkyId,
              }),
            )
          : await loader.getHarness(SkyNavbarHarness);
    
        return { navbarHarness, fixture };
      }
    
      it('should set up the navbar', async () => {
        const { navbarHarness, fixture } = await setupTest();
    
        const navbarItem1 = await navbarHarness.getItem({
          dataSkyId: 'navbar-item-1',
        });
        const navbarButton = await navbarItem1.querySelector('a');
    
        const clickSpy = spyOn(fixture.componentInstance, 'onItemClick');
        await navbarButton.click();
        expect(clickSpy).toHaveBeenCalledTimes(1);
      });
    });

Copy

    import { Component } from '@angular/core';
    import { RouterModule } from '@angular/router';
    import { SkyNavbarModule } from '@skyux/navbar';
    import { SkyDropdownModule } from '@skyux/popovers';
    
    /**
     * @title Navbar with basic setup
     */
    @Component({
      selector: 'app-navbar-example',
      templateUrl: './example.component.html',
      imports: [RouterModule, SkyDropdownModule, SkyNavbarModule],
    })
    export class NavbarExampleComponent {
      public onItemClick(buttonText: string): void {
        alert(buttonText + ' button clicked!');
      }
    }

# Testing

                   Skip to Main Content

 Navbar
======

The navbar displays top-level navigation items that can include sub-navigation items in dropdown menus.

 Installation
-------------

NPM package

`@skyux/navbar`[View in NPM](https://www.npmjs.com/package/@skyux/navbar) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/navbar/src/lib/modules/navbar/navbar.module.ts#L12) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/navbar`Copy None found.

 SkyNavbarModule
----------------

Type: Module

`import { SkyNavbarModule } from '@skyux/navbar';`

 SkyNavbarComponent
-------------------

Type: Component

Selector: `sky-navbar`

Displays top-level navigation.

 SkyNavbarItemComponent
-----------------------

Type: Component

Selector: `sky-navbar-item`

Displays a navigation item in the navbar. It can include sub-navigation items in a dropdown menu.

### Inputs

#### `active: boolean | undefined`

Whether the navigation item is active.

Default: `false`

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyNavbarHarness
-----------------

Type: Class

`import { SkyNavbarHarness } from '@skyux/navbar/testing';`

Harness for interacting with a navbar component in tests.

### Methods

#### `getItem(filter: SkyNavbarItemHarnessFilters): Promise<SkyNavbarItemHarness>`

Gets a specific navbar item based on the filter criteria.

#### Parameters

##### `filter: SkyNavbarItemHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyNavbarItemHarness>`

#### `getItems(filters?: SkyNavbarItemHarnessFilters): Promise<SkyNavbarItemHarness[]>`

Gets an array of navbar items based on the filter criteria. If no filter is provided, returns all navbar items.

#### Parameters

##### `filters?: SkyNavbarItemHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyNavbarItemHarness[]>`

#### `SkyNavbarHarness.with(filters: SkyNavbarHarnessFilters): HarnessPredicate<SkyNavbarHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyNavbarHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyNavbarHarnessFilters`

#### Returns

`HarnessPredicate<SkyNavbarHarness>`

 SkyNavbarHarnessFilters
------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyNavbarHarness` instances.

    interface SkyNavbarHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyNavbarItemHarness
---------------------

Type: Class

`import { SkyNavbarItemHarness } from '@skyux/navbar/testing';`

Harness to interact with a navbar item component in tests.

### Methods

#### `isActive(): Promise<boolean>`

Whether the navbar item is active.

#### Returns

`Promise<boolean>`

#### `queryHarness(query: HarnessQuery<T>): Promise<T>`

Returns a child harness or throws an error if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<T>`

#### `queryHarnesses(harness: HarnessQuery<T>): Promise<T[]>`

Returns child harnesses.

#### Parameters

##### `harness: HarnessQuery<T>`

#### Returns

`Promise<T[]>`

#### `queryHarnessOrNull(query: HarnessQuery<T>): Promise<null | T>`

Returns a child harness or null if not found.

#### Parameters

##### `query: HarnessQuery<T>`

#### Returns

`Promise<null | T>`

#### `querySelector(selector: string): Promise<TestElement>`

Returns a child test element or throws an error if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement>`

#### `querySelectorAll(selector: string): Promise<TestElement[]>`

Returns child test elements.

#### Parameters

##### `selector: string`

#### Returns

`Promise<TestElement[]>`

#### `querySelectorOrNull(selector: string): Promise<null | TestElement>`

Returns a child test element or null if not found.

#### Parameters

##### `selector: string`

#### Returns

`Promise<null | TestElement>`

#### `SkyNavbarItemHarness.with(filters: SkyNavbarItemHarnessFilters): HarnessPredicate<SkyNavbarItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyNavbarItemHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyNavbarItemHarnessFilters`

#### Returns

`HarnessPredicate<SkyNavbarItemHarness>`

 SkyNavbarItemHarnessFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyNavbarItemHarness` instances.

    interface SkyNavbarItemHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.