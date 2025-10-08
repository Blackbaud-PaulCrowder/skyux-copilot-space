# Design

                  Skip to Main Content

 Popover
=======

Popovers display small chunks of contextual content on pages or modals. They are similar to tooltips but provide more room for plain text, HTML content, or Angular components.

 Usage
------

### Use when

Use popovers to display additional contextual content that is valuable some of the time.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-1.5042464ef0915c66afd9a61118198795.png)

Do use popovers to provide more context that might be helpful.

### Don't use when

Don't use popovers when the content is valuable most of the time. Use [persistent inline help](/skyux/design/guidelines/user-assistance#inline-help.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-2.3a2d6eea9b772d920817575b7ad4d96b.png)

Don't use popovers to display unfamiliar input requirements or important consequences.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-3.a5c676b7c4c818c4a1d6605d872dd6b0.png)

Do use persistent inline help to display requirements or call out consequences.

Don't use popovers to display inputs or other interactions that are a necessary part of a workflow.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-4.a5c30825fccd20edda68af96f64a21f0.png)

Don't use popovers as part of completing a task.

Don't use popovers when a large amount of content is necessary. Use a [flyout](/skyux/components/flyout.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-5.007b913663855392e0ebe54752eccbe9.png)

Don't use popovers for detailed record previews.

 Anatomy
--------

1

Content area

2

Highlight border

3

Element pointer

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-anatomy.6f8c9341b7b2452f007ec1c9072ae154.png)

 Options
--------

### Positioning

You can specify the position of the popover in relation to the element it references. The default position is centered above that element.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-option-position.e2770446b8d920e6f032e693ad8df20b.png)

### Trigger

To ensure usability on touch devices, trigger user-invoked popovers on `click` actions rather than `mouseenter` actions.

You can also invoke popovers programmatically. For example, you can programmatically invoke a popover when users visit a page for the first time to highlight an important interface element that they might overlook. However, don't invoke multiple popovers on a page because this reduces their effectiveness.

 Behavior and states
--------------------

### Closing

Popovers close when users click elsewhere or focus on another element.

### Responsiveness

If a popover doesn't fit in the viewport at its current position, it automatically repositions. If the popover doesn't fit at any position, it converts to a modal that overlays the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-behavior-states.c648ae54d176161c08af7fc086b16fb6.png)

 Content
--------

Limit popovers to small chunks of contextual content. The content can include plain text, formatted HTML, or Angular components.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-content-simple.1975b621a1510106d296ace5238b1d7a.png)

Do use small chunks of plain text.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-content-html.9b93fd253add42b32ba5d6a5557be9e8.png)

Do use small chunks of formatted HTML.

Don't include a large amount of content, form inputs, or complex interactions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-5.007b913663855392e0ebe54752eccbe9.png)

Don't display large amounts of content in popovers.

 Layout
-------

In most cases, use the default placement for popovers to center them above the elements they reference. This minimizes the risk of obscuring content that users haven't seen and avoids obscuring the content that they will interact with next.

However, when the referenced elements are near the edge of the display, use a different placement option to obscure as little content as possible.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-layout.cd9a61e2942d8cde124346912e7f2499.png)

 Related information
--------------------

*   [Flyout](/skyux/components/flyout.md)

### Guidelines

*   [User assistance](/skyux/design/guidelines/user-assistance.md)

 Installation
-------------

NPM package

`@skyux/popovers`[View in NPM](https://www.npmjs.com/package/@skyux/popovers) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/popovers/src/lib/modules/popover/popover.module.ts#L32) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/popovers`Copy None found.

 SkyPopoverModule
-----------------

Type: Module

`import { SkyPopoverModule } from '@skyux/popovers';`

 SkyPopoverComponent
--------------------

Type: Component

Selector: `sky-popover`

### Inputs

#### `alignment: SkyPopoverAlignment`

The horizontal alignment of the popover in relation to the trigger element. The `skyPopoverAlignment` property on the popover directive takes precedence over this property when specified.

Default: `"center"`

#### `placement: SkyPopoverPlacement`

The placement of the popover in relation to the trigger element. The `skyPopoverPlacement` property on the popover directive takes precedence over this property when specified.

Default: `"above"`

#### `popoverTitle: string | undefined`

The title for the popover.

#### `popoverType: SkyPopoverType`

The type of popover.

Default: `"info"`

### Outputs

#### `popoverClosed: EventEmitter<SkyPopoverComponent>`

Fires when users close the popover.

#### `popoverOpened: EventEmitter<SkyPopoverComponent>`

Fires when users open the popover.

 SkyPopoverDirective
--------------------

Type: Directive

Selector: `[skyPopover]`

### Inputs

#### `skyPopover: SkyPopoverComponent | undefined`

Required

The popover component to display. Add this directive to the trigger element that opens the popover.

#### `skyPopoverAlignment: SkyPopoverAlignment | undefined`

The horizontal alignment of the popover in relation to the trigger element.

#### `skyPopoverMessageStream: Subject<SkyPopoverMessage>`

The RxJS `Subject` to send commands to the popover that respect the `SkyPopoverMessage` type.

#### `skyPopoverPlacement: SkyPopoverPlacement | undefined`

The placement of the popover in relation to the trigger element.

#### `skyPopoverTrigger: SkyPopoverTrigger`

Warning: **Deprecated.** To ensure usability on touch devices, trigger user-invoked popovers on `click` actions rather than `mouseenter` actions.

The user action that displays the popover.

 SkyPopoverAlignment
--------------------

Type: Type alias

Represents the horizontal alignment of the popover in relation to the trigger element.

    type SkyPopoverAlignment = "left" | "center" | "right"

 SkyPopoverPlacement
--------------------

Type: Type alias

Represents the placement of the popover in relation to the trigger element.

    type SkyPopoverPlacement = "above" | "below" | "right" | "left"

 SkyPopoverTrigger
------------------

Type: Type alias

Warning: **Deprecated.** To ensure usability on touch devices, trigger user-invoked popovers on `click` actions rather than `mouseenter` actions.

The user action that displays the popover.

    type SkyPopoverTrigger = "click" | "mouseenter"

 SkyPopoverType
---------------

Type: Type alias

The style type of the popover.

    type SkyPopoverType = "danger" | "info"

 SkyPopoverMessage
------------------

Type: Interface

Specifies messages to be sent to the popover component.

    interface SkyPopoverMessage {
      type?: SkyPopoverMessageType;
    }

### Properties

#### `type?: SkyPopoverMessageType`

The type of message to send.

 SkyPopoverMessageType
----------------------

Type: Enumeration

The type of message to send to the popover component.

    enum SkyPopoverMessageType {
      Close = 1,
      Focus = 3,
      Open = 0,
      Reposition = 2,
    }

### Properties

#### `SkyPopoverMessageType.Close`

Closes the popover.

#### `SkyPopoverMessageType.Focus`

Brings focus to the popover element.

#### `SkyPopoverMessageType.Open`

Opens the popover.

#### `SkyPopoverMessageType.Reposition`

Repositions the popover to the appropriate position. This is useful for when the popover's width and height change while it is open.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyPopoverHarness
------------------

Type: Class

`import { SkyPopoverHarness } from '@skyux/popovers/testing';`

Harness for interacting with a popover component in tests.

### Methods

#### `clickPopoverButton(): Promise<void>`

Toggles a popover open or closed.

#### Returns

`Promise<void>`

#### `getPopoverContent(): Promise<SkyPopoverContentHarness>`

Gets the popover content component.

#### Returns

`Promise<SkyPopoverContentHarness>`

#### `isOpen(): Promise<boolean>`

Whether the popover is open.

#### Returns

`Promise<boolean>`

#### `SkyPopoverHarness.with(filters: SkyPopoverHarnessFilters): HarnessPredicate<SkyPopoverHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPopoverHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyPopoverHarnessFilters`

#### Returns

`HarnessPredicate<SkyPopoverHarness>`

 SkyPopoverHarnessFilters
-------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyPopoverHarness](/skyux/components/popover?docs-active-tab=design#class_sky-popover-harness.md) instances.

    interface SkyPopoverHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyPopoverContentHarness
-------------------------

Type: Class

`import { SkyPopoverContentHarness } from '@skyux/popovers/testing';`

Harness for interacting with a popover content component in tests.

### Methods

#### `clickOut(): Promise<void>`

Clicks out of the popover.

#### Returns

`Promise<void>`

#### `getAlignment(): Promise<string>`

Gets the alignment of the popover content.

#### Returns

`Promise<string>`

#### `getBodyText(): Promise<string>`

Gets the text of the popover content body.

#### Returns

`Promise<string>`

#### `getPlacement(): Promise<string>`

Gets the placement of the popover content.

#### Returns

`Promise<string>`

#### `getTitleText(): Promise<undefined | string>`

Gets the text of the popover content title.

#### Returns

`Promise<undefined | string>`

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

#### `SkyPopoverContentHarness.with(filters: SkyPopoverContentHarnessFilters): HarnessPredicate<SkyPopoverContentHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPopoverContentHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyPopoverContentHarnessFilters`

#### Returns

`HarnessPredicate<SkyPopoverContentHarness>`

 SkyPopoverContentHarnessFilters
--------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyComponentHarness` instances.

    interface SkyPopoverContentHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Development

                  Skip to Main Content

 Popover
=======

Popovers display small chunks of contextual content on pages or modals. They are similar to tooltips but provide more room for plain text, HTML content, or Angular components.

 Usage
------

### Use when

Use popovers to display additional contextual content that is valuable some of the time.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-1.5042464ef0915c66afd9a61118198795.png)

Do use popovers to provide more context that might be helpful.

### Don't use when

Don't use popovers when the content is valuable most of the time. Use [persistent inline help](/skyux/design/guidelines/user-assistance#inline-help.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-2.3a2d6eea9b772d920817575b7ad4d96b.png)

Don't use popovers to display unfamiliar input requirements or important consequences.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-3.a5c676b7c4c818c4a1d6605d872dd6b0.png)

Do use persistent inline help to display requirements or call out consequences.

Don't use popovers to display inputs or other interactions that are a necessary part of a workflow.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-4.a5c30825fccd20edda68af96f64a21f0.png)

Don't use popovers as part of completing a task.

Don't use popovers when a large amount of content is necessary. Use a [flyout](/skyux/components/flyout.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-5.007b913663855392e0ebe54752eccbe9.png)

Don't use popovers for detailed record previews.

 Anatomy
--------

1

Content area

2

Highlight border

3

Element pointer

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-anatomy.6f8c9341b7b2452f007ec1c9072ae154.png)

 Options
--------

### Positioning

You can specify the position of the popover in relation to the element it references. The default position is centered above that element.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-option-position.e2770446b8d920e6f032e693ad8df20b.png)

### Trigger

To ensure usability on touch devices, trigger user-invoked popovers on `click` actions rather than `mouseenter` actions.

You can also invoke popovers programmatically. For example, you can programmatically invoke a popover when users visit a page for the first time to highlight an important interface element that they might overlook. However, don't invoke multiple popovers on a page because this reduces their effectiveness.

 Behavior and states
--------------------

### Closing

Popovers close when users click elsewhere or focus on another element.

### Responsiveness

If a popover doesn't fit in the viewport at its current position, it automatically repositions. If the popover doesn't fit at any position, it converts to a modal that overlays the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-behavior-states.c648ae54d176161c08af7fc086b16fb6.png)

 Content
--------

Limit popovers to small chunks of contextual content. The content can include plain text, formatted HTML, or Angular components.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-content-simple.1975b621a1510106d296ace5238b1d7a.png)

Do use small chunks of plain text.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-content-html.9b93fd253add42b32ba5d6a5557be9e8.png)

Do use small chunks of formatted HTML.

Don't include a large amount of content, form inputs, or complex interactions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-5.007b913663855392e0ebe54752eccbe9.png)

Don't display large amounts of content in popovers.

 Layout
-------

In most cases, use the default placement for popovers to center them above the elements they reference. This minimizes the risk of obscuring content that users haven't seen and avoids obscuring the content that they will interact with next.

However, when the referenced elements are near the edge of the display, use a different placement option to obscure as little content as possible.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-layout.cd9a61e2942d8cde124346912e7f2499.png)

 Related information
--------------------

*   [Flyout](/skyux/components/flyout.md)

### Guidelines

*   [User assistance](/skyux/design/guidelines/user-assistance.md)

 Installation
-------------

NPM package

`@skyux/popovers`[View in NPM](https://www.npmjs.com/package/@skyux/popovers) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/popovers/src/lib/modules/popover/popover.module.ts#L32) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/popovers`Copy None found.

 SkyPopoverModule
-----------------

Type: Module

`import { SkyPopoverModule } from '@skyux/popovers';`

 SkyPopoverComponent
--------------------

Type: Component

Selector: `sky-popover`

### Inputs

#### `alignment: SkyPopoverAlignment`

The horizontal alignment of the popover in relation to the trigger element. The `skyPopoverAlignment` property on the popover directive takes precedence over this property when specified.

Default: `"center"`

#### `placement: SkyPopoverPlacement`

The placement of the popover in relation to the trigger element. The `skyPopoverPlacement` property on the popover directive takes precedence over this property when specified.

Default: `"above"`

#### `popoverTitle: string | undefined`

The title for the popover.

#### `popoverType: SkyPopoverType`

The type of popover.

Default: `"info"`

### Outputs

#### `popoverClosed: EventEmitter<SkyPopoverComponent>`

Fires when users close the popover.

#### `popoverOpened: EventEmitter<SkyPopoverComponent>`

Fires when users open the popover.

 SkyPopoverDirective
--------------------

Type: Directive

Selector: `[skyPopover]`

### Inputs

#### `skyPopover: SkyPopoverComponent | undefined`

Required

The popover component to display. Add this directive to the trigger element that opens the popover.

#### `skyPopoverAlignment: SkyPopoverAlignment | undefined`

The horizontal alignment of the popover in relation to the trigger element.

#### `skyPopoverMessageStream: Subject<SkyPopoverMessage>`

The RxJS `Subject` to send commands to the popover that respect the `SkyPopoverMessage` type.

#### `skyPopoverPlacement: SkyPopoverPlacement | undefined`

The placement of the popover in relation to the trigger element.

#### `skyPopoverTrigger: SkyPopoverTrigger`

Warning: **Deprecated.** To ensure usability on touch devices, trigger user-invoked popovers on `click` actions rather than `mouseenter` actions.

The user action that displays the popover.

 SkyPopoverAlignment
--------------------

Type: Type alias

Represents the horizontal alignment of the popover in relation to the trigger element.

    type SkyPopoverAlignment = "left" | "center" | "right"

 SkyPopoverPlacement
--------------------

Type: Type alias

Represents the placement of the popover in relation to the trigger element.

    type SkyPopoverPlacement = "above" | "below" | "right" | "left"

 SkyPopoverTrigger
------------------

Type: Type alias

Warning: **Deprecated.** To ensure usability on touch devices, trigger user-invoked popovers on `click` actions rather than `mouseenter` actions.

The user action that displays the popover.

    type SkyPopoverTrigger = "click" | "mouseenter"

 SkyPopoverType
---------------

Type: Type alias

The style type of the popover.

    type SkyPopoverType = "danger" | "info"

 SkyPopoverMessage
------------------

Type: Interface

Specifies messages to be sent to the popover component.

    interface SkyPopoverMessage {
      type?: SkyPopoverMessageType;
    }

### Properties

#### `type?: SkyPopoverMessageType`

The type of message to send.

 SkyPopoverMessageType
----------------------

Type: Enumeration

The type of message to send to the popover component.

    enum SkyPopoverMessageType {
      Close = 1,
      Focus = 3,
      Open = 0,
      Reposition = 2,
    }

### Properties

#### `SkyPopoverMessageType.Close`

Closes the popover.

#### `SkyPopoverMessageType.Focus`

Brings focus to the popover element.

#### `SkyPopoverMessageType.Open`

Opens the popover.

#### `SkyPopoverMessageType.Reposition`

Repositions the popover to the appropriate position. This is useful for when the popover's width and height change while it is open.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyPopoverHarness
------------------

Type: Class

`import { SkyPopoverHarness } from '@skyux/popovers/testing';`

Harness for interacting with a popover component in tests.

### Methods

#### `clickPopoverButton(): Promise<void>`

Toggles a popover open or closed.

#### Returns

`Promise<void>`

#### `getPopoverContent(): Promise<SkyPopoverContentHarness>`

Gets the popover content component.

#### Returns

`Promise<SkyPopoverContentHarness>`

#### `isOpen(): Promise<boolean>`

Whether the popover is open.

#### Returns

`Promise<boolean>`

#### `SkyPopoverHarness.with(filters: SkyPopoverHarnessFilters): HarnessPredicate<SkyPopoverHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPopoverHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyPopoverHarnessFilters`

#### Returns

`HarnessPredicate<SkyPopoverHarness>`

 SkyPopoverHarnessFilters
-------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyPopoverHarness](/skyux/components/popover?docs-active-tab=development#class_sky-popover-harness.md) instances.

    interface SkyPopoverHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyPopoverContentHarness
-------------------------

Type: Class

`import { SkyPopoverContentHarness } from '@skyux/popovers/testing';`

Harness for interacting with a popover content component in tests.

### Methods

#### `clickOut(): Promise<void>`

Clicks out of the popover.

#### Returns

`Promise<void>`

#### `getAlignment(): Promise<string>`

Gets the alignment of the popover content.

#### Returns

`Promise<string>`

#### `getBodyText(): Promise<string>`

Gets the text of the popover content body.

#### Returns

`Promise<string>`

#### `getPlacement(): Promise<string>`

Gets the placement of the popover content.

#### Returns

`Promise<string>`

#### `getTitleText(): Promise<undefined | string>`

Gets the text of the popover content title.

#### Returns

`Promise<undefined | string>`

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

#### `SkyPopoverContentHarness.with(filters: SkyPopoverContentHarnessFilters): HarnessPredicate<SkyPopoverContentHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPopoverContentHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyPopoverContentHarnessFilters`

#### Returns

`HarnessPredicate<SkyPopoverContentHarness>`

 SkyPopoverContentHarnessFilters
--------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyComponentHarness` instances.

    interface SkyPopoverContentHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Examples

                    Skip to Main Content

 Popover
=======

Popovers display small chunks of contextual content on pages or modals. They are similar to tooltips but provide more room for plain text, HTML content, or Angular components.Usage
------

### Use when

Use popovers to display additional contextual content that is valuable some of the time.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-1.5042464ef0915c66afd9a61118198795.png)

Do use popovers to provide more context that might be helpful.

### Don't use when

Don't use popovers when the content is valuable most of the time. Use [persistent inline help](/skyux/design/guidelines/user-assistance#inline-help.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-2.3a2d6eea9b772d920817575b7ad4d96b.png)

Don't use popovers to display unfamiliar input requirements or important consequences.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-3.a5c676b7c4c818c4a1d6605d872dd6b0.png)

Do use persistent inline help to display requirements or call out consequences.

Don't use popovers to display inputs or other interactions that are a necessary part of a workflow.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-4.a5c30825fccd20edda68af96f64a21f0.png)

Don't use popovers as part of completing a task.

Don't use popovers when a large amount of content is necessary. Use a [flyout](/skyux/components/flyout.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-5.007b913663855392e0ebe54752eccbe9.png)

Don't use popovers for detailed record previews.

 Anatomy
--------

1

Content area

2

Highlight border

3

Element pointer

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-anatomy.6f8c9341b7b2452f007ec1c9072ae154.png)

 Options
--------

### Positioning

You can specify the position of the popover in relation to the element it references. The default position is centered above that element.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-option-position.e2770446b8d920e6f032e693ad8df20b.png)

### Trigger

To ensure usability on touch devices, trigger user-invoked popovers on `click` actions rather than `mouseenter` actions.

You can also invoke popovers programmatically. For example, you can programmatically invoke a popover when users visit a page for the first time to highlight an important interface element that they might overlook. However, don't invoke multiple popovers on a page because this reduces their effectiveness.

 Behavior and states
--------------------

### Closing

Popovers close when users click elsewhere or focus on another element.

### Responsiveness

If a popover doesn't fit in the viewport at its current position, it automatically repositions. If the popover doesn't fit at any position, it converts to a modal that overlays the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-behavior-states.c648ae54d176161c08af7fc086b16fb6.png)

 Content
--------

Limit popovers to small chunks of contextual content. The content can include plain text, formatted HTML, or Angular components.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-content-simple.1975b621a1510106d296ace5238b1d7a.png)

Do use small chunks of plain text.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-content-html.9b93fd253add42b32ba5d6a5557be9e8.png)

Do use small chunks of formatted HTML.

Don't include a large amount of content, form inputs, or complex interactions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-5.007b913663855392e0ebe54752eccbe9.png)

Don't display large amounts of content in popovers.

 Layout
-------

In most cases, use the default placement for popovers to center them above the elements they reference. This minimizes the risk of obscuring content that users haven't seen and avoids obscuring the content that they will interact with next.

However, when the referenced elements are near the edge of the display, use a different placement option to obscure as little content as possible.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-layout.cd9a61e2942d8cde124346912e7f2499.png)

 Related information
--------------------

*   [Flyout](/skyux/components/flyout.md)

### Guidelines

*   [User assistance](/skyux/design/guidelines/user-assistance.md)

 Installation
-------------

NPM package

`@skyux/popovers`[View in NPM](https://www.npmjs.com/package/@skyux/popovers) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/popovers/src/lib/modules/popover/popover.module.ts#L32) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/popovers`Copy None found.

 SkyPopoverModule
-----------------

Type: Module

`import { SkyPopoverModule } from '@skyux/popovers';`

 SkyPopoverComponent
--------------------

Type: Component

Selector: `sky-popover`

### Inputs

#### `alignment: SkyPopoverAlignment`

The horizontal alignment of the popover in relation to the trigger element. The `skyPopoverAlignment` property on the popover directive takes precedence over this property when specified.

Default: `"center"`

#### `placement: SkyPopoverPlacement`

The placement of the popover in relation to the trigger element. The `skyPopoverPlacement` property on the popover directive takes precedence over this property when specified.

Default: `"above"`

#### `popoverTitle: string | undefined`

The title for the popover.

#### `popoverType: SkyPopoverType`

The type of popover.

Default: `"info"`

### Outputs

#### `popoverClosed: EventEmitter<SkyPopoverComponent>`

Fires when users close the popover.

#### `popoverOpened: EventEmitter<SkyPopoverComponent>`

Fires when users open the popover.

 SkyPopoverDirective
--------------------

Type: Directive

Selector: `[skyPopover]`

### Inputs

#### `skyPopover: SkyPopoverComponent | undefined`

Required

The popover component to display. Add this directive to the trigger element that opens the popover.

#### `skyPopoverAlignment: SkyPopoverAlignment | undefined`

The horizontal alignment of the popover in relation to the trigger element.

#### `skyPopoverMessageStream: Subject<SkyPopoverMessage>`

The RxJS `Subject` to send commands to the popover that respect the `SkyPopoverMessage` type.

#### `skyPopoverPlacement: SkyPopoverPlacement | undefined`

The placement of the popover in relation to the trigger element.

#### `skyPopoverTrigger: SkyPopoverTrigger`

Warning: **Deprecated.** To ensure usability on touch devices, trigger user-invoked popovers on `click` actions rather than `mouseenter` actions.

The user action that displays the popover.

 SkyPopoverAlignment
--------------------

Type: Type alias

Represents the horizontal alignment of the popover in relation to the trigger element.

    type SkyPopoverAlignment = "left" | "center" | "right"

 SkyPopoverPlacement
--------------------

Type: Type alias

Represents the placement of the popover in relation to the trigger element.

    type SkyPopoverPlacement = "above" | "below" | "right" | "left"

 SkyPopoverTrigger
------------------

Type: Type alias

Warning: **Deprecated.** To ensure usability on touch devices, trigger user-invoked popovers on `click` actions rather than `mouseenter` actions.

The user action that displays the popover.

    type SkyPopoverTrigger = "click" | "mouseenter"

 SkyPopoverType
---------------

Type: Type alias

The style type of the popover.

    type SkyPopoverType = "danger" | "info"

 SkyPopoverMessage
------------------

Type: Interface

Specifies messages to be sent to the popover component.

    interface SkyPopoverMessage {
      type?: SkyPopoverMessageType;
    }

### Properties

#### `type?: SkyPopoverMessageType`

The type of message to send.

 SkyPopoverMessageType
----------------------

Type: Enumeration

The type of message to send to the popover component.

    enum SkyPopoverMessageType {
      Close = 1,
      Focus = 3,
      Open = 0,
      Reposition = 2,
    }

### Properties

#### `SkyPopoverMessageType.Close`

Closes the popover.

#### `SkyPopoverMessageType.Focus`

Brings focus to the popover element.

#### `SkyPopoverMessageType.Open`

Opens the popover.

#### `SkyPopoverMessageType.Reposition`

Repositions the popover to the appropriate position. This is useful for when the popover's width and height change while it is open.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyPopoverHarness
------------------

Type: Class

`import { SkyPopoverHarness } from '@skyux/popovers/testing';`

Harness for interacting with a popover component in tests.

### Methods

#### `clickPopoverButton(): Promise<void>`

Toggles a popover open or closed.

#### Returns

`Promise<void>`

#### `getPopoverContent(): Promise<SkyPopoverContentHarness>`

Gets the popover content component.

#### Returns

`Promise<SkyPopoverContentHarness>`

#### `isOpen(): Promise<boolean>`

Whether the popover is open.

#### Returns

`Promise<boolean>`

#### `SkyPopoverHarness.with(filters: SkyPopoverHarnessFilters): HarnessPredicate<SkyPopoverHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPopoverHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyPopoverHarnessFilters`

#### Returns

`HarnessPredicate<SkyPopoverHarness>`

 SkyPopoverHarnessFilters
-------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyPopoverHarness](/skyux/components/popover?docs-active-tab=examples#class_sky-popover-harness.md) instances.

    interface SkyPopoverHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyPopoverContentHarness
-------------------------

Type: Class

`import { SkyPopoverContentHarness } from '@skyux/popovers/testing';`

Harness for interacting with a popover content component in tests.

### Methods

#### `clickOut(): Promise<void>`

Clicks out of the popover.

#### Returns

`Promise<void>`

#### `getAlignment(): Promise<string>`

Gets the alignment of the popover content.

#### Returns

`Promise<string>`

#### `getBodyText(): Promise<string>`

Gets the text of the popover content body.

#### Returns

`Promise<string>`

#### `getPlacement(): Promise<string>`

Gets the placement of the popover content.

#### Returns

`Promise<string>`

#### `getTitleText(): Promise<undefined | string>`

Gets the text of the popover content title.

#### Returns

`Promise<undefined | string>`

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

#### `SkyPopoverContentHarness.with(filters: SkyPopoverContentHarnessFilters): HarnessPredicate<SkyPopoverContentHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPopoverContentHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyPopoverContentHarnessFilters`

#### Returns

`HarnessPredicate<SkyPopoverContentHarness>`

 SkyPopoverContentHarnessFilters
--------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyComponentHarness` instances.

    interface SkyPopoverContentHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

### Popover with basic setup

Edit in StackBlitz

Open popover

Show code

Copy

    <button
      class="sky-btn sky-btn-default sky-margin-inline-sm"
      data-sky-id="popover-example"
      type="button"
      [skyPopover]="myPopover"
      [skyPopoverAlignment]="popoverAlignment"
      [skyPopoverPlacement]="popoverPlacement"
    >
      Open popover
    </button>
    
    <sky-popover #myPopover [popoverTitle]="popoverTitle">
      {{ popoverBody }}
    </sky-popover>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyPopoverAlignment, SkyPopoverPlacement } from '@skyux/popovers';
    import { SkyPopoverHarness } from '@skyux/popovers/testing';
    
    import { PopoversPopoverBasicExampleComponent } from './example.component';
    
    describe('Basic popover', () => {
      async function setupTest(options?: {
        titleText?: string;
        alignment?: SkyPopoverAlignment;
        placement?: SkyPopoverPlacement;
      }): Promise<{
        popoverHarness: SkyPopoverHarness;
        fixture: ComponentFixture<PopoversPopoverBasicExampleComponent>;
      }> {
        const fixture = TestBed.createComponent(
          PopoversPopoverBasicExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    
        if (options) {
          fixture.componentInstance.popoverAlignment = options.alignment;
          fixture.componentInstance.popoverPlacement = options.placement;
          fixture.componentInstance.popoverTitle = options.titleText;
        }
    
        fixture.detectChanges();
        await fixture.whenStable();
    
        const popoverHarness = await loader.getHarness(
          SkyPopoverHarness.with({
            dataSkyId: 'popover-example',
          }),
        );
    
        return { popoverHarness, fixture };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [PopoversPopoverBasicExampleComponent, NoopAnimationsModule],
        });
      });
    
      it('should open and close when the user interacts with the trigger', async () => {
        const { popoverHarness } = await setupTest();
    
        await expectAsync(popoverHarness.isOpen()).toBeResolvedTo(false);
    
        await popoverHarness.clickPopoverButton();
        await expectAsync(popoverHarness.isOpen()).toBeResolvedTo(true);
    
        await popoverHarness.clickPopoverButton();
        await expectAsync(popoverHarness.isOpen()).toBeResolvedTo(false);
      });
    
      it('should expose content properties when visible', async () => {
        const { popoverHarness } = await setupTest({
          titleText: 'Did you know?',
          placement: 'right',
        });
    
        await popoverHarness.clickPopoverButton();
        const contentHarness = await popoverHarness.getPopoverContent();
    
        await expectAsync(contentHarness.getTitleText()).toBeResolvedTo(
          'Did you know?',
        );
        await expectAsync(contentHarness.getBodyText()).toBeResolvedTo(
          'This is a popover.',
        );
        await expectAsync(contentHarness.getAlignment()).toBeResolvedTo('center');
        await expectAsync(contentHarness.getPlacement()).toBeResolvedTo('right');
    
        await popoverHarness.clickPopoverButton();
        // Attempting to call this method when the popover is closed will result in an error.
        await expectAsync(popoverHarness.getPopoverContent()).toBeRejectedWithError(
          'Unable to retrieve the popover content because the popover is not open.',
        );
      });
    });

Copy

    import { Component } from '@angular/core';
    import {
      SkyPopoverAlignment,
      SkyPopoverModule,
      SkyPopoverPlacement,
    } from '@skyux/popovers';
    
    /**
     * @title Popover with basic setup
     */
    @Component({
      selector: 'app-popovers-popover-basic-example',
      templateUrl: './example.component.html',
      imports: [SkyPopoverModule],
    })
    export class PopoversPopoverBasicExampleComponent {
      public popoverAlignment: SkyPopoverAlignment | undefined;
      public popoverBody = 'This is a popover.';
      public popoverPlacement: SkyPopoverPlacement | undefined;
      public popoverTitle: string | undefined = 'Did you know?';
    }
### Popover with programmatic interactions

Edit in StackBlitz

Show help content for Open popover with message stream

Show code

Copy

    <sky-help-inline
      ariaLabel="Information about Popover using message stream"
      [skyPopover]="myPopover"
      [skyPopoverMessageStream]="popoverController"
    />
    
    <button
      class="sky-btn sky-btn-default sky-margin-inline-sm"
      type="button"
      (click)="openPopover()"
    >
      Open popover with message stream
    </button>
    
    <sky-popover
      #myPopover
      (popoverClosed)="onPopoverStateChange(false)"
      (popoverOpened)="onPopoverStateChange(true)"
    >
      This is a popover.
    </sky-popover>

Copy

    import { Component } from '@angular/core';
    import { SkyHelpInlineModule } from '@skyux/help-inline';
    import {
      SkyPopoverMessage,
      SkyPopoverMessageType,
      SkyPopoverModule,
    } from '@skyux/popovers';
    
    import { Subject } from 'rxjs';
    
    /**
     * @title Popover with programmatic interactions
     */
    @Component({
      selector: 'app-popovers-popover-programmatic-example',
      templateUrl: './example.component.html',
      imports: [SkyHelpInlineModule, SkyPopoverModule],
    })
    export class PopoversPopoverProgrammaticExampleComponent {
      protected popoverController = new Subject<SkyPopoverMessage>();
    
      #popoverOpen = false;
    
      protected onPopoverStateChange(isOpen: boolean): void {
        this.#popoverOpen = isOpen;
      }
    
      protected openPopover(): void {
        if (!this.#popoverOpen) {
          this.#sendMessage(SkyPopoverMessageType.Open);
        }
      }
    
      #sendMessage(type: SkyPopoverMessageType): void {
        const message: SkyPopoverMessage = { type };
        this.popoverController.next(message);
      }
    }

# Testing

                  Skip to Main Content

 Popover
=======

Popovers display small chunks of contextual content on pages or modals. They are similar to tooltips but provide more room for plain text, HTML content, or Angular components.

 Usage
------

### Use when

Use popovers to display additional contextual content that is valuable some of the time.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-1.5042464ef0915c66afd9a61118198795.png)

Do use popovers to provide more context that might be helpful.

### Don't use when

Don't use popovers when the content is valuable most of the time. Use [persistent inline help](/skyux/design/guidelines/user-assistance#inline-help.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-2.3a2d6eea9b772d920817575b7ad4d96b.png)

Don't use popovers to display unfamiliar input requirements or important consequences.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-3.a5c676b7c4c818c4a1d6605d872dd6b0.png)

Do use persistent inline help to display requirements or call out consequences.

Don't use popovers to display inputs or other interactions that are a necessary part of a workflow.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-4.a5c30825fccd20edda68af96f64a21f0.png)

Don't use popovers as part of completing a task.

Don't use popovers when a large amount of content is necessary. Use a [flyout](/skyux/components/flyout.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-5.007b913663855392e0ebe54752eccbe9.png)

Don't use popovers for detailed record previews.

 Anatomy
--------

1

Content area

2

Highlight border

3

Element pointer

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-anatomy.6f8c9341b7b2452f007ec1c9072ae154.png)

 Options
--------

### Positioning

You can specify the position of the popover in relation to the element it references. The default position is centered above that element.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-option-position.e2770446b8d920e6f032e693ad8df20b.png)

### Trigger

To ensure usability on touch devices, trigger user-invoked popovers on `click` actions rather than `mouseenter` actions.

You can also invoke popovers programmatically. For example, you can programmatically invoke a popover when users visit a page for the first time to highlight an important interface element that they might overlook. However, don't invoke multiple popovers on a page because this reduces their effectiveness.

 Behavior and states
--------------------

### Closing

Popovers close when users click elsewhere or focus on another element.

### Responsiveness

If a popover doesn't fit in the viewport at its current position, it automatically repositions. If the popover doesn't fit at any position, it converts to a modal that overlays the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-behavior-states.c648ae54d176161c08af7fc086b16fb6.png)

 Content
--------

Limit popovers to small chunks of contextual content. The content can include plain text, formatted HTML, or Angular components.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-content-simple.1975b621a1510106d296ace5238b1d7a.png)

Do use small chunks of plain text.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-content-html.9b93fd253add42b32ba5d6a5557be9e8.png)

Do use small chunks of formatted HTML.

Don't include a large amount of content, form inputs, or complex interactions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-usage-5.007b913663855392e0ebe54752eccbe9.png)

Don't display large amounts of content in popovers.

 Layout
-------

In most cases, use the default placement for popovers to center them above the elements they reference. This minimizes the risk of obscuring content that users haven't seen and avoids obscuring the content that they will interact with next.

However, when the referenced elements are near the edge of the display, use a different placement option to obscure as little content as possible.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/popovers/img/guidelines/popover/popover-layout.cd9a61e2942d8cde124346912e7f2499.png)

 Related information
--------------------

*   [Flyout](/skyux/components/flyout.md)

### Guidelines

*   [User assistance](/skyux/design/guidelines/user-assistance.md)

 Installation
-------------

NPM package

`@skyux/popovers`[View in NPM](https://www.npmjs.com/package/@skyux/popovers) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/popovers/src/lib/modules/popover/popover.module.ts#L32) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/popovers`Copy None found.

 SkyPopoverModule
-----------------

Type: Module

`import { SkyPopoverModule } from '@skyux/popovers';`

 SkyPopoverComponent
--------------------

Type: Component

Selector: `sky-popover`

### Inputs

#### `alignment: SkyPopoverAlignment`

The horizontal alignment of the popover in relation to the trigger element. The `skyPopoverAlignment` property on the popover directive takes precedence over this property when specified.

Default: `"center"`

#### `placement: SkyPopoverPlacement`

The placement of the popover in relation to the trigger element. The `skyPopoverPlacement` property on the popover directive takes precedence over this property when specified.

Default: `"above"`

#### `popoverTitle: string | undefined`

The title for the popover.

#### `popoverType: SkyPopoverType`

The type of popover.

Default: `"info"`

### Outputs

#### `popoverClosed: EventEmitter<SkyPopoverComponent>`

Fires when users close the popover.

#### `popoverOpened: EventEmitter<SkyPopoverComponent>`

Fires when users open the popover.

 SkyPopoverDirective
--------------------

Type: Directive

Selector: `[skyPopover]`

### Inputs

#### `skyPopover: SkyPopoverComponent | undefined`

Required

The popover component to display. Add this directive to the trigger element that opens the popover.

#### `skyPopoverAlignment: SkyPopoverAlignment | undefined`

The horizontal alignment of the popover in relation to the trigger element.

#### `skyPopoverMessageStream: Subject<SkyPopoverMessage>`

The RxJS `Subject` to send commands to the popover that respect the `SkyPopoverMessage` type.

#### `skyPopoverPlacement: SkyPopoverPlacement | undefined`

The placement of the popover in relation to the trigger element.

#### `skyPopoverTrigger: SkyPopoverTrigger`

Warning: **Deprecated.** To ensure usability on touch devices, trigger user-invoked popovers on `click` actions rather than `mouseenter` actions.

The user action that displays the popover.

 SkyPopoverAlignment
--------------------

Type: Type alias

Represents the horizontal alignment of the popover in relation to the trigger element.

    type SkyPopoverAlignment = "left" | "center" | "right"

 SkyPopoverPlacement
--------------------

Type: Type alias

Represents the placement of the popover in relation to the trigger element.

    type SkyPopoverPlacement = "above" | "below" | "right" | "left"

 SkyPopoverTrigger
------------------

Type: Type alias

Warning: **Deprecated.** To ensure usability on touch devices, trigger user-invoked popovers on `click` actions rather than `mouseenter` actions.

The user action that displays the popover.

    type SkyPopoverTrigger = "click" | "mouseenter"

 SkyPopoverType
---------------

Type: Type alias

The style type of the popover.

    type SkyPopoverType = "danger" | "info"

 SkyPopoverMessage
------------------

Type: Interface

Specifies messages to be sent to the popover component.

    interface SkyPopoverMessage {
      type?: SkyPopoverMessageType;
    }

### Properties

#### `type?: SkyPopoverMessageType`

The type of message to send.

 SkyPopoverMessageType
----------------------

Type: Enumeration

The type of message to send to the popover component.

    enum SkyPopoverMessageType {
      Close = 1,
      Focus = 3,
      Open = 0,
      Reposition = 2,
    }

### Properties

#### `SkyPopoverMessageType.Close`

Closes the popover.

#### `SkyPopoverMessageType.Focus`

Brings focus to the popover element.

#### `SkyPopoverMessageType.Open`

Opens the popover.

#### `SkyPopoverMessageType.Reposition`

Repositions the popover to the appropriate position. This is useful for when the popover's width and height change while it is open.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyPopoverHarness
------------------

Type: Class

`import { SkyPopoverHarness } from '@skyux/popovers/testing';`

Harness for interacting with a popover component in tests.

### Methods

#### `clickPopoverButton(): Promise<void>`

Toggles a popover open or closed.

#### Returns

`Promise<void>`

#### `getPopoverContent(): Promise<SkyPopoverContentHarness>`

Gets the popover content component.

#### Returns

`Promise<SkyPopoverContentHarness>`

#### `isOpen(): Promise<boolean>`

Whether the popover is open.

#### Returns

`Promise<boolean>`

#### `SkyPopoverHarness.with(filters: SkyPopoverHarnessFilters): HarnessPredicate<SkyPopoverHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPopoverHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyPopoverHarnessFilters`

#### Returns

`HarnessPredicate<SkyPopoverHarness>`

 SkyPopoverHarnessFilters
-------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyPopoverHarness](/skyux/components/popover?docs-active-tab=testing#class_sky-popover-harness.md) instances.

    interface SkyPopoverHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyPopoverContentHarness
-------------------------

Type: Class

`import { SkyPopoverContentHarness } from '@skyux/popovers/testing';`

Harness for interacting with a popover content component in tests.

### Methods

#### `clickOut(): Promise<void>`

Clicks out of the popover.

#### Returns

`Promise<void>`

#### `getAlignment(): Promise<string>`

Gets the alignment of the popover content.

#### Returns

`Promise<string>`

#### `getBodyText(): Promise<string>`

Gets the text of the popover content body.

#### Returns

`Promise<string>`

#### `getPlacement(): Promise<string>`

Gets the placement of the popover content.

#### Returns

`Promise<string>`

#### `getTitleText(): Promise<undefined | string>`

Gets the text of the popover content title.

#### Returns

`Promise<undefined | string>`

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

#### `SkyPopoverContentHarness.with(filters: SkyPopoverContentHarnessFilters): HarnessPredicate<SkyPopoverContentHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyPopoverContentHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyPopoverContentHarnessFilters`

#### Returns

`HarnessPredicate<SkyPopoverContentHarness>`

 SkyPopoverContentHarnessFilters
--------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyComponentHarness` instances.

    interface SkyPopoverContentHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.