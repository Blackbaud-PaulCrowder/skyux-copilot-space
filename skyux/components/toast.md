                 

 Toast
=====

Toasts display messages over page content and provide a common look and feel.

 Usage
------

### Use when

Use toasts when users need to know about changes in system state due to background processes.

Use toasts when information is important enough to notify users regardless of their current tasks or context.

 Content
--------

Toasts provide lightweight, time-sensitive information that is relevant to users when it appears. They guide users on actions to take and should include links for those actions whenever possible.

The text must be clear and concise, and punctuation is subjective depending on the scenario.

 Behavior and states
--------------------

If a toast is the only place users can see a message, display the toast until users manually close it. Only close toasts automatically if users can access the messages after the toasts close.

 Related information
--------------------

### Guidelines

*   [Calling out information](/skyux/design/guidelines/call-out-info.md)
*   [Content containers](/skyux/design/guidelines/content-containers.md)
*   [Error handling](/skyux/design/guidelines/error-handling.md)

 Installation
-------------

NPM package

`@skyux/toast`[View in NPM](https://www.npmjs.com/package/@skyux/toast) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/toast/src/lib/modules/toast/toast.service.ts#L27) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/toast`Copy None found.

 SkyToastService
----------------

Type: Service

### Methods

#### `closeAll(): void`

Closes all active toast components.

#### Returns

`void`

#### `openComponent(component: Type<unknown>, config?: SkyToastConfig, providers = []): SkyToastInstance`

Opens a new toast using a custom component.

#### Parameters

##### `component: Type<unknown>`

Specifies an Angular component to inject into the toast body,

##### `config?: SkyToastConfig`

Specifies additional configuration options for the toast.

##### `providers = []`

Specifies an array of custom providers to pass to the custom component's constructor.

#### Returns

`SkyToastInstance`

#### `openMessage(message: string, config?: SkyToastConfig): SkyToastInstance`

Opens a new toast and displays the specified message.

#### Parameters

##### `message: string`

Specifies the text to display in the toast.

##### `config?: SkyToastConfig`

Specifies additional configuration options for the toast.

#### Returns

`SkyToastInstance`

 SkyToastConfig
---------------

Type: Interface

Specifies the configuration options to set up a toast.

    interface SkyToastConfig {
      autoClose?: boolean;
      type?: SkyToastType;
    }

### Properties

#### `autoClose?: boolean`

Whether to automatically close the toast. Only close toasts automatically if users can access the messages after the toasts close.

#### `type?: SkyToastType`

The `SkyToastType` type that determines the color and icon for the toast. This property defaults to `Info`.

 SkyToastType
-------------

Type: Enumeration

    enum SkyToastType {
      Danger = 0,
      Info = 1,
      Success = 2,
      Warning = 3,
    }

### Properties

#### `SkyToastType.Danger`

Sets the toast's icon and background color to the `danger` style.

#### `SkyToastType.Info`

Sets the toast's icon and background color to the `info` style.

#### `SkyToastType.Success`

Sets the toast's icon and background color to the `success` style.

#### `SkyToastType.Warning`

Sets the toast's icon and background color to the `warning` style.

 SkyToastInstance
-----------------

Type: Class

### Properties

#### `closed: Observable<void>`

An observable that indicates when the toast is closed.

### Methods

#### `close(): void`

Closes the toast component.

#### Returns

`void`

 SkyToastContainerOptions
-------------------------

Type: Class

Global configuration options for displaying toast components.

### Properties

#### `displayDirection: SkyToastDisplayDirection | undefined`

Order in which toasts should appear in the page's toast container.

 SkyToastDisplayDirection
-------------------------

Type: Enumeration

    enum SkyToastDisplayDirection {
      NewestOnTop = 1,
      OldestOnTop = 0,
    }

### Properties

#### `SkyToastDisplayDirection.NewestOnTop`

Displays new toasts on top of previous toasts.

#### `SkyToastDisplayDirection.OldestOnTop`

Displays new toasts below previous toasts.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyToasterHarness
------------------

Type: Class

`import { SkyToasterHarness } from '@skyux/toast/testing';`

Harness for interacting with toasts' host component in tests. Use this harness to query and interact with `SkyToastHarness` for open toast components.

### Methods

#### `getNumberOfToasts(): Promise<number>`

#### Returns

`Promise<number>`

#### `getToastByMessage(message: string): Promise<SkyToastHarness>`

Gets a toast harness that matches the `message`.

#### Parameters

##### `message: string`

#### Returns

`Promise<SkyToastHarness>`

#### `getToasts(): Promise<SkyToastHarness[]>`

Gets all open toast harnesses.

#### Returns

`Promise<SkyToastHarness[]>`

 SkyToastHarness
----------------

Type: Class

`import { SkyToastHarness } from '@skyux/toast/testing';`

Harness for interacting with the toast component in tests.

### Methods

#### `close(): Promise<void>`

Clicks the toast close button.

#### Returns

`Promise<void>`

#### `getMessage(): Promise<string>`

Gets the toast message.

#### Returns

`Promise<string>`

#### `getType(): Promise<SkyToastType>`

Gets the toast type.

#### Returns

`Promise<SkyToastType>`

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

#### `SkyToastHarness.with(filters: SkyToastHarnessFilters): HarnessPredicate<SkyToastHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyToastHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyToastHarnessFilters`

#### Returns

`HarnessPredicate<SkyToastHarness>`

 SkyToastHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyToastHarness` instances.

    interface SkyToastHarnessFilters {
      message?: string;
    }

### Properties

#### `message?: string`

Finds toasts with the matching text.