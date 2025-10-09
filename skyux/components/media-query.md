                 

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