# Design

                 Skip to Main Content

 Media queries
=============

The media queries service subscribes to screen size changes at different breakpoints.

### Styles

*   [Responsiveness](/skyux/design/styles/responsiveness.md)

 Installation
-------------

NPM package

`@skyux/core`[View in NPM](https://www.npmjs.com/package/@skyux/core) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/core/src/lib/modules/media-query/media-query.service.ts#L21) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/core`Copy None found.

 SkyMediaQueryService
---------------------

Type: Service

Utility used to subscribe to viewport and container breakpoint changes.

### Properties

#### `static lg: string`

The size for the `lg` breakpoint.

Default: `"(min-width: 1200px)"`

#### `static md: string`

The size for the `md` breakpoint.

Default: `"(min-width: 992px) and (max-width: 1199px)"`

#### `static sm: string`

The size for the `sm` breakpoint.

Default: `"(min-width: 768px) and (max-width: 991px)"`

#### `static xs: string`

The size for the `xs` breakpoint.

Default: `"(max-width: 767px)"`

#### `breakpointChange: Observable<"xs" | "sm" | "md" | "lg">`

Emits when the breakpoint changes.

#### `current: SkyMediaBreakpoints`

Warning: **Deprecated.** Subscribe to the `breakpointChange` observable instead.

Returns the current breakpoint.

### Methods

#### `subscribe(listener: SkyMediaQueryListener): Subscription`

Warning: **Deprecated.** Subscribe to the `breakpointChange` observable instead.

Subscribes to screen size changes.

#### Parameters

##### `listener: SkyMediaQueryListener`

Specifies a function that is called when breakpoints change.

#### Returns

`Subscription`

 SkyMediaBreakpoints
--------------------

Type: Enumeration

Warning: **Deprecated.** Use `SkyBreakpoint` instead.

Represents all available media breakpoints.

    enum SkyMediaBreakpoints {
      lg = 4,
      md = 3,
      sm = 2,
      xs = 1,
    }

### Properties

#### `SkyMediaBreakpoints.lg`

Screen widths of 1200px or greater.

#### `SkyMediaBreakpoints.md`

Screen widths of 992px to 1199px.

#### `SkyMediaBreakpoints.sm`

Screen widths of 768px to 991px.

#### `SkyMediaBreakpoints.xs`

Screen widths of 767px or less.

 SkyMediaQueryListener
----------------------

Type: Type alias

Warning: **Deprecated.** Subscribe to the `breakpointChange` observable instead.

The function that is called when the breakpoints change. It is called with a `SkyMediaBreakpoints` argument, which is an enum that represents the new breakpoint.

    type SkyMediaQueryListener = (args: SkyMediaBreakpoints) => void

 SkyBreakpoint
--------------

Type: Type alias

The name of a viewport or container breakpoint.

    type SkyBreakpoint = readonly ["xs", "sm", "md", "lg"]

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 provideSkyMediaQueryTesting
----------------------------

Type: Function

Adds mocks to allow interactions with breakpoints in tests.

    function provideSkyMediaQueryTesting(): Provider[]

 SkyMediaQueryTestingController
-------------------------------

Type: Service

A controller to be injected into tests, which mocks the `SkyMediaQueryService` and handles interactions with breakpoints.

### Methods

#### `setBreakpoint(breakpoint: "xs" | "sm" | "md" | "lg"): void`

Emits the provided breakpoint to all subscribers.

#### Parameters

##### `breakpoint: "xs" | "sm" | "md" | "lg"`

#### Returns

`void`

# Development

                 Skip to Main Content

 Media queries
=============

The media queries service subscribes to screen size changes at different breakpoints.

### Styles

*   [Responsiveness](/skyux/design/styles/responsiveness.md)

 Installation
-------------

NPM package

`@skyux/core`[View in NPM](https://www.npmjs.com/package/@skyux/core) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/core/src/lib/modules/media-query/media-query.service.ts#L21) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/core`Copy None found.

 SkyMediaQueryService
---------------------

Type: Service

Utility used to subscribe to viewport and container breakpoint changes.

### Properties

#### `static lg: string`

The size for the `lg` breakpoint.

Default: `"(min-width: 1200px)"`

#### `static md: string`

The size for the `md` breakpoint.

Default: `"(min-width: 992px) and (max-width: 1199px)"`

#### `static sm: string`

The size for the `sm` breakpoint.

Default: `"(min-width: 768px) and (max-width: 991px)"`

#### `static xs: string`

The size for the `xs` breakpoint.

Default: `"(max-width: 767px)"`

#### `breakpointChange: Observable<"xs" | "sm" | "md" | "lg">`

Emits when the breakpoint changes.

#### `current: SkyMediaBreakpoints`

Warning: **Deprecated.** Subscribe to the `breakpointChange` observable instead.

Returns the current breakpoint.

### Methods

#### `subscribe(listener: SkyMediaQueryListener): Subscription`

Warning: **Deprecated.** Subscribe to the `breakpointChange` observable instead.

Subscribes to screen size changes.

#### Parameters

##### `listener: SkyMediaQueryListener`

Specifies a function that is called when breakpoints change.

#### Returns

`Subscription`

 SkyMediaBreakpoints
--------------------

Type: Enumeration

Warning: **Deprecated.** Use `SkyBreakpoint` instead.

Represents all available media breakpoints.

    enum SkyMediaBreakpoints {
      lg = 4,
      md = 3,
      sm = 2,
      xs = 1,
    }

### Properties

#### `SkyMediaBreakpoints.lg`

Screen widths of 1200px or greater.

#### `SkyMediaBreakpoints.md`

Screen widths of 992px to 1199px.

#### `SkyMediaBreakpoints.sm`

Screen widths of 768px to 991px.

#### `SkyMediaBreakpoints.xs`

Screen widths of 767px or less.

 SkyMediaQueryListener
----------------------

Type: Type alias

Warning: **Deprecated.** Subscribe to the `breakpointChange` observable instead.

The function that is called when the breakpoints change. It is called with a `SkyMediaBreakpoints` argument, which is an enum that represents the new breakpoint.

    type SkyMediaQueryListener = (args: SkyMediaBreakpoints) => void

 SkyBreakpoint
--------------

Type: Type alias

The name of a viewport or container breakpoint.

    type SkyBreakpoint = readonly ["xs", "sm", "md", "lg"]

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 provideSkyMediaQueryTesting
----------------------------

Type: Function

Adds mocks to allow interactions with breakpoints in tests.

    function provideSkyMediaQueryTesting(): Provider[]

 SkyMediaQueryTestingController
-------------------------------

Type: Service

A controller to be injected into tests, which mocks the `SkyMediaQueryService` and handles interactions with breakpoints.

### Methods

#### `setBreakpoint(breakpoint: "xs" | "sm" | "md" | "lg"): void`

Emits the provided breakpoint to all subscribers.

#### Parameters

##### `breakpoint: "xs" | "sm" | "md" | "lg"`

#### Returns

`void`

# Examples

                   Skip to Main Content

 Media queries
=============

The media queries service subscribes to screen size changes at different breakpoints.### Styles

*   [Responsiveness](/skyux/design/styles/responsiveness.md)

 Installation
-------------

NPM package

`@skyux/core`[View in NPM](https://www.npmjs.com/package/@skyux/core) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/core/src/lib/modules/media-query/media-query.service.ts#L21) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/core`Copy None found.

 SkyMediaQueryService
---------------------

Type: Service

Utility used to subscribe to viewport and container breakpoint changes.

### Properties

#### `static lg: string`

The size for the `lg` breakpoint.

Default: `"(min-width: 1200px)"`

#### `static md: string`

The size for the `md` breakpoint.

Default: `"(min-width: 992px) and (max-width: 1199px)"`

#### `static sm: string`

The size for the `sm` breakpoint.

Default: `"(min-width: 768px) and (max-width: 991px)"`

#### `static xs: string`

The size for the `xs` breakpoint.

Default: `"(max-width: 767px)"`

#### `breakpointChange: Observable<"xs" | "sm" | "md" | "lg">`

Emits when the breakpoint changes.

#### `current: SkyMediaBreakpoints`

Warning: **Deprecated.** Subscribe to the `breakpointChange` observable instead.

Returns the current breakpoint.

### Methods

#### `subscribe(listener: SkyMediaQueryListener): Subscription`

Warning: **Deprecated.** Subscribe to the `breakpointChange` observable instead.

Subscribes to screen size changes.

#### Parameters

##### `listener: SkyMediaQueryListener`

Specifies a function that is called when breakpoints change.

#### Returns

`Subscription`

 SkyMediaBreakpoints
--------------------

Type: Enumeration

Warning: **Deprecated.** Use `SkyBreakpoint` instead.

Represents all available media breakpoints.

    enum SkyMediaBreakpoints {
      lg = 4,
      md = 3,
      sm = 2,
      xs = 1,
    }

### Properties

#### `SkyMediaBreakpoints.lg`

Screen widths of 1200px or greater.

#### `SkyMediaBreakpoints.md`

Screen widths of 992px to 1199px.

#### `SkyMediaBreakpoints.sm`

Screen widths of 768px to 991px.

#### `SkyMediaBreakpoints.xs`

Screen widths of 767px or less.

 SkyMediaQueryListener
----------------------

Type: Type alias

Warning: **Deprecated.** Subscribe to the `breakpointChange` observable instead.

The function that is called when the breakpoints change. It is called with a `SkyMediaBreakpoints` argument, which is an enum that represents the new breakpoint.

    type SkyMediaQueryListener = (args: SkyMediaBreakpoints) => void

 SkyBreakpoint
--------------

Type: Type alias

The name of a viewport or container breakpoint.

    type SkyBreakpoint = readonly ["xs", "sm", "md", "lg"]

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 provideSkyMediaQueryTesting
----------------------------

Type: Function

Adds mocks to allow interactions with breakpoints in tests.

    function provideSkyMediaQueryTesting(): Provider[]

 SkyMediaQueryTestingController
-------------------------------

Type: Service

A controller to be injected into tests, which mocks the `SkyMediaQueryService` and handles interactions with breakpoints.

### Methods

#### `setBreakpoint(breakpoint: "xs" | "sm" | "md" | "lg"): void`

Emits the provided breakpoint to all subscribers.

#### Parameters

##### `breakpoint: "xs" | "sm" | "md" | "lg"`

#### Returns

`void`

### Media query service with basic setup

Edit in StackBlitz

Current media breakpoint: sm

*   [Home](#)

Show code

Copy

    <p>Current media breakpoint: {{ breakpoint() }}</p>
    
    @if (breakpoint() === 'xs') {
      <nav class="my-nav-mobile">
        <ul>
          <li>
            <button aria-label="Home" type="button">
              <sky-icon iconName="building" />
            </button>
          </li>
        </ul>
      </nav>
    } @else {
      <nav class="my-nav-desktop">
        <ul>
          <li>
            <a href="#">Home</a>
          </li>
        </ul>
      </nav>
    }
Copy

    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import {
      SkyMediaQueryTestingController,
      provideSkyMediaQueryTesting,
    } from '@skyux/core/testing';
    
    import { CoreMediaQueryBasicExampleComponent } from './example.component';
    
    describe('Media query example', () => {
      function setupTest(): {
        fixture: ComponentFixture<CoreMediaQueryBasicExampleComponent>;
        mediaController: SkyMediaQueryTestingController;
      } {
        const fixture = TestBed.createComponent(
          CoreMediaQueryBasicExampleComponent,
        );
        const mediaController = TestBed.inject(SkyMediaQueryTestingController);
    
        return { fixture, mediaController };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          providers: [provideSkyMediaQueryTesting()],
        });
      });
    
      it('should change the breakpoint', () => {
        const { fixture, mediaController } = setupTest();
    
        const el = fixture.nativeElement as HTMLElement;
    
        mediaController.setBreakpoint('xs');
        fixture.detectChanges();
    
        expect(el.querySelector('.my-nav-mobile')).toBeTruthy();
    
        mediaController.setBreakpoint('lg');
        fixture.detectChanges();
    
        expect(el.querySelector('.my-nav-desktop')).toBeTruthy();
      });
    });

Copy

    import { Component, inject } from '@angular/core';
    import { toSignal } from '@angular/core/rxjs-interop';
    import { SkyMediaQueryService } from '@skyux/core';
    import { SkyIconModule } from '@skyux/icon';
    
    /**
     * @title Media query service with basic setup
     */
    @Component({
      imports: [SkyIconModule],
      selector: 'app-core-media-query-basic-example',
      templateUrl: './example.component.html',
    })
    export class CoreMediaQueryBasicExampleComponent {
      protected breakpoint = toSignal(
        inject(SkyMediaQueryService).breakpointChange,
      );
    }
### Media query service using a responsive host container

Edit in StackBlitz

Viewport breakpoint: sm

#### Creating a responsive host using the host directive

Breakpoint within container: sm

#### Creating a responsive host using the directive attribute

Breakpoint within container: xs

#### Creating a responsive host that wraps embedded views

The responsive host's injector must be passed to the embedded view manually.

Breakpoint within container: sm

Breakpoint for child: sm

Show code

Copy

    import { Component, inject } from '@angular/core';
    import { toSignal } from '@angular/core/rxjs-interop';
    import { SkyMediaQueryService } from '@skyux/core';
    
    @Component({
      selector: 'app-child',
      standalone: true,
      template: `<p>Breakpoint for child: {{ breakpoint() }}</p>`,
    })
    export class DemoChildComponent {
      protected breakpoint = toSignal(
        inject(SkyMediaQueryService).breakpointChange,
      );
    }
Copy

    import { Component, inject } from '@angular/core';
    import { toSignal } from '@angular/core/rxjs-interop';
    import { SkyMediaQueryService, SkyResponsiveHostDirective } from '@skyux/core';
    
    @Component({
      hostDirectives: [SkyResponsiveHostDirective],
      selector: 'app-container',
      standalone: true,
      styles: `
        :host {
          border: 1px solid var(--sky-border-color-neutral-medium-dark);
          display: block;
          margin: 0 auto;
          max-width: 800px;
        }
      `,
      template: `
        <p>Breakpoint within container: {{ breakpoint() }}</p>
        <ng-content />
      `,
    })
    export class DemoContainerComponent {
      protected breakpoint = toSignal(
        inject(SkyMediaQueryService).breakpointChange,
      );
    }
Copy

    <p>Viewport breakpoint: {{ breakpoint() }}</p>
    
    <h4>Creating a responsive host using the host directive</h4>
    
    <app-container data-sky-id="container-w-host-directive" />
    
    <h4>Creating a responsive host using the directive attribute</h4>
    
    <div
      #hostRef="skyResponsiveHost"
      class="my-container"
      data-sky-id="container-w-attr"
      skyResponsiveHost
    >
      <p>Breakpoint within container: {{ hostRef.breakpointChange | async }}</p>
    </div>
    
    <h4>Creating a responsive host that wraps embedded views</h4>
    
    <p>
      The responsive host's injector must be passed to the embedded view manually.
    </p>
    
    <app-container #responsiveHost="skyResponsiveHost">
      <ng-container
        [ngTemplateOutlet]="myTemplate"
        [ngTemplateOutletInjector]="responsiveHost.injector"
      />
    </app-container>
    
    <ng-template #myTemplate>
      <app-child />
    </ng-template>
Copy

    .my-container {
      border: 1px solid var(--sky-border-color-neutral-medium-dark);
      margin: 0 auto;
      max-width: 500px;
    }
Copy

    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import {
      SkyMediaQueryTestingController,
      provideSkyMediaQueryTesting,
    } from '@skyux/core/testing';
    
    import { CoreMediaQueryResponsiveHostExampleComponent } from './example.component';
    
    describe('Media query example', () => {
      function setupTest(): {
        fixture: ComponentFixture<CoreMediaQueryResponsiveHostExampleComponent>;
        mediaController: SkyMediaQueryTestingController;
      } {
        const fixture = TestBed.createComponent(
          CoreMediaQueryResponsiveHostExampleComponent,
        );
        const mediaController = TestBed.inject(SkyMediaQueryTestingController);
    
        return { fixture, mediaController };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          providers: [provideSkyMediaQueryTesting()],
        });
      });
    
      it('should change the breakpoint', () => {
        const { fixture, mediaController } = setupTest();
    
        const el = fixture.nativeElement as HTMLElement;
    
        const containerWithHostDirective = el.querySelector<HTMLElement>(
          '[data-sky-id="container-w-host-directive"]',
        );
    
        const containerWithAttrDirective = el.querySelector<HTMLElement>(
          '[data-sky-id="container-w-attr"]',
        );
    
        mediaController.setBreakpoint('xs');
        fixture.detectChanges();
    
        expect(containerWithHostDirective).toHaveClass(
          'sky-responsive-container-xs',
        );
        expect(containerWithAttrDirective).toHaveClass(
          'sky-responsive-container-xs',
        );
    
        mediaController.setBreakpoint('lg');
        fixture.detectChanges();
    
        expect(containerWithHostDirective).toHaveClass(
          'sky-responsive-container-lg',
        );
        expect(containerWithAttrDirective).toHaveClass(
          'sky-responsive-container-lg',
        );
      });
    });

Copy

    import { CommonModule } from '@angular/common';
    import { Component, inject } from '@angular/core';
    import { toSignal } from '@angular/core/rxjs-interop';
    import { SkyMediaQueryService, SkyResponsiveHostDirective } from '@skyux/core';
    import { SkyIconModule } from '@skyux/icon';
    
    import { DemoChildComponent } from './child.component';
    import { DemoContainerComponent } from './container.component';
    
    /**
     * @title Media query service using a responsive host container
     */
    @Component({
      imports: [
        CommonModule,
        DemoChildComponent,
        DemoContainerComponent,
        SkyResponsiveHostDirective,
        SkyIconModule,
      ],
      selector: 'app-core-media-query-responsive-host-example',
      styleUrl: './example.component.scss',
      templateUrl: './example.component.html',
    })
    export class CoreMediaQueryResponsiveHostExampleComponent {
      protected breakpoint = toSignal(
        inject(SkyMediaQueryService).breakpointChange,
      );
    }

# Testing

                 Skip to Main Content

 Media queries
=============

The media queries service subscribes to screen size changes at different breakpoints.

### Styles

*   [Responsiveness](/skyux/design/styles/responsiveness.md)

 Installation
-------------

NPM package

`@skyux/core`[View in NPM](https://www.npmjs.com/package/@skyux/core) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/core/src/lib/modules/media-query/media-query.service.ts#L21) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/core`Copy None found.

 SkyMediaQueryService
---------------------

Type: Service

Utility used to subscribe to viewport and container breakpoint changes.

### Properties

#### `static lg: string`

The size for the `lg` breakpoint.

Default: `"(min-width: 1200px)"`

#### `static md: string`

The size for the `md` breakpoint.

Default: `"(min-width: 992px) and (max-width: 1199px)"`

#### `static sm: string`

The size for the `sm` breakpoint.

Default: `"(min-width: 768px) and (max-width: 991px)"`

#### `static xs: string`

The size for the `xs` breakpoint.

Default: `"(max-width: 767px)"`

#### `breakpointChange: Observable<"xs" | "sm" | "md" | "lg">`

Emits when the breakpoint changes.

#### `current: SkyMediaBreakpoints`

Warning: **Deprecated.** Subscribe to the `breakpointChange` observable instead.

Returns the current breakpoint.

### Methods

#### `subscribe(listener: SkyMediaQueryListener): Subscription`

Warning: **Deprecated.** Subscribe to the `breakpointChange` observable instead.

Subscribes to screen size changes.

#### Parameters

##### `listener: SkyMediaQueryListener`

Specifies a function that is called when breakpoints change.

#### Returns

`Subscription`

 SkyMediaBreakpoints
--------------------

Type: Enumeration

Warning: **Deprecated.** Use `SkyBreakpoint` instead.

Represents all available media breakpoints.

    enum SkyMediaBreakpoints {
      lg = 4,
      md = 3,
      sm = 2,
      xs = 1,
    }

### Properties

#### `SkyMediaBreakpoints.lg`

Screen widths of 1200px or greater.

#### `SkyMediaBreakpoints.md`

Screen widths of 992px to 1199px.

#### `SkyMediaBreakpoints.sm`

Screen widths of 768px to 991px.

#### `SkyMediaBreakpoints.xs`

Screen widths of 767px or less.

 SkyMediaQueryListener
----------------------

Type: Type alias

Warning: **Deprecated.** Subscribe to the `breakpointChange` observable instead.

The function that is called when the breakpoints change. It is called with a `SkyMediaBreakpoints` argument, which is an enum that represents the new breakpoint.

    type SkyMediaQueryListener = (args: SkyMediaBreakpoints) => void

 SkyBreakpoint
--------------

Type: Type alias

The name of a viewport or container breakpoint.

    type SkyBreakpoint = readonly ["xs", "sm", "md", "lg"]

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 provideSkyMediaQueryTesting
----------------------------

Type: Function

Adds mocks to allow interactions with breakpoints in tests.

    function provideSkyMediaQueryTesting(): Provider[]

 SkyMediaQueryTestingController
-------------------------------

Type: Service

A controller to be injected into tests, which mocks the `SkyMediaQueryService` and handles interactions with breakpoints.

### Methods

#### `setBreakpoint(breakpoint: "xs" | "sm" | "md" | "lg"): void`

Emits the provided breakpoint to all subscribers.

#### Parameters

##### `breakpoint: "xs" | "sm" | "md" | "lg"`

#### Returns

`void`