                 

 Wizard (deprecated)
===================

Wizards guide users through pre-defined steps in a particular order to represent a series of related decisions in a user's direct workflow.

Progress indicator wizard is deprecated in favor of [tabs wizard](/skyux/components/tabs-wizard.md). For more information, see the [progress indicator wizard deprecation instructions](/skyux/learn/develop/deprecation/progress-indicator-wizard.md).

 Usage
------

### Use when

Use wizards when users must perform multiple steps in a particular order. Wizards illustrate the step-wise nature of tasks and reinforce progress toward final goals as users complete steps.

Use wizards when users perform tasks repeatedly or when tasks are best presented as multiple steps but only require a single sitting.

Use wizards when tasks do not result in records or settings with page-level views.

Use wizards when interaction complexity of each step is low. For example, steps can use standard form inputs and controls.

### Don't use when

Don't use wizards when users for long or complex setup processes or when the complexity of steps varies drastically. Use [waterfall progress indicators](/skyux/components/progress-indicator-waterfall.md) instead.

Don't use wizards when tasks include more than six steps or require more time than a single sitting. Use [waterfall progress indicators](/skyux/components/progress-indicator-waterfall.md) instead.

Don't use wizards when users must be aware of sequential progress that they are not responsible for. Use [passive progress indicators](/skyux/components/progress-indicator-passive.md) instead.

 Related information
--------------------

### Components

*   [Modal](/skyux/components/modal.md)
*   [Passive progress indicator](/skyux/components/progress-indicator-passive.md)
*   [Waterfall progress indicator](/skyux/components/progress-indicator-waterfall.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/progress-indicator`[View in NPM](https://www.npmjs.com/package/@skyux/progress-indicator) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/progress-indicator/src/lib/modules/progress-indicator/progress-indicator.module.ts#L48) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/progress-indicator`Copy None found.

 SkyProgressIndicatorModule
---------------------------

Type: Module

`import { SkyProgressIndicatorModule } from '@skyux/progress-indicator';`

 SkyProgressIndicatorComponent
------------------------------

Type: Component

Selector: `sky-progress-indicator`

### Inputs

#### `displayMode: SkyProgressIndicatorDisplayModeType`

Warning: **Deprecated.** The property was designed to create wizards by setting `displayMode="horizontal"` on progress indicators in modals, but this wizard implementation was replaced by the [wizard component that uses tabs](/skyux/components/tabs-wizard.md).

The orientation of the progress indicator, which can be vertical or horizontal. For [passive progress indicators](/skyux/components/progress-indicator-passive.md) and [waterfall progress indicators](/skyux/components/progress-indicator-waterfall.md), use the vertical display mode. For [modal wizards](/skyux/components/progress-indicator-wizard.md), use the horizontal display mode.

Default: `"vertical"`

#### `isPassive: boolean | undefined`

Whether the progress indicator is passive. Passive progress indicators inform users of progress that concerns them but that they are not responsible for, and they must use the vertical display mode.

Default: `false`

#### `messageStream: Subject<SkyProgressIndicatorMessage | SkyProgressIndicatorMessageType> | undefined`

The observable of `SkyProgressIndicatorMessage` that determines the status to display for items in the progress indicator. The message stream is a queue of commanding messages to change the state of the progress indicator based on the message type.

#### `startingIndex: number`

The index for the item to make active when the progress indicator loads. All steps that precede the active item are marked as complete, and all steps that follow the active item are marked as incomplete.

### Outputs

#### `progressChanges: EventEmitter<SkyProgressIndicatorChange>`

Fires when the progress indicator changes the status of an item.

 SkyProgressIndicatorTitleComponent
-----------------------------------

Type: Component

Selector: `sky-progress-indicator-title`

Specifies a header to display above the progress indicator.

 SkyProgressIndicatorItemComponent
----------------------------------

Type: Component

Selector: `sky-progress-indicator-item`

Specifies a step to include in the progress indicator. Each step requires a label, and you can also specify step details within the `sky-progress-indicator-item` element.

### Inputs

#### `title: string | undefined`

Required

The step label for the step in the progress indicator.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `title`, a [help inline](/skyux/components/help-inline.md) button is placed beside the progress indicator item label. Clicking the button invokes global help as configured by the application. This property only applies when `title` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `title`, a [help inline](/skyux/components/help-inline.md) button is added to the progress indicator item label. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `title` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

 SkyProgressIndicatorNavButtonComponent
---------------------------------------

Type: Component

Selector: `sky-progress-indicator-nav-button`

Displays a button to navigate the steps in modal wizards. We recommend against using it in passive progress indicators and waterfall progress indicators.

### Inputs

#### `progressIndicator: SkyProgressIndicatorComponent | undefined`

Required

The progress indicator component to associate with the nav button.

#### `buttonText: string | undefined`

The label to display on the nav button.

Default: `"Next"`

#### `buttonType: SkyProgressIndicatorNavButtonType`

The type of nav button to include.

Default: `"next"`

#### `disabled: boolean | undefined`

Whether to disable the nav button.

Default: `false`

### Outputs

#### `actionClick: EventEmitter<SkyProgressIndicatorActionClickArgs>`

Fires when users select the nav button and emits a `SkyProgressIndicatorActionClickArgs` object that is passed into the callback function to allow consumers to decide whether the button’s action should complete successfully.

 SkyProgressIndicatorResetButtonComponent
-----------------------------------------

Type: Component

Selector: `sky-progress-indicator-reset-button`

Displays a button to mark all items in the progress indicator as incomplete and set the first item as the active item. The steps after the active item remain incomplete until users reach them in their sequential order.

### Inputs

#### `progressIndicator: SkyProgressIndicatorComponent | undefined`

Required

The progress indicator component to associate with the reset button.

#### `disabled: boolean | undefined`

Whether to disable the reset button.

Default: `false`

### Outputs

#### `resetClick: EventEmitter<void>`

Fires when users select the reset button that marks all items as incomplete and sets the first item as the active item.

 SkyProgressIndicatorActionClickArgs
------------------------------------

Type: Interface

The arguments passed to the `actionClick` event handler.

    interface SkyProgressIndicatorActionClickArgs {
      event: MouseEvent;
      progressHandler: SkyProgressIndicatorActionClickProgressHandler;
    }

### Properties

#### `event: MouseEvent`

The mouse event from the user click.

#### `progressHandler: SkyProgressIndicatorActionClickProgressHandler`

The progress handler object that allows consumers to trigger step advancement manually.

 SkyProgressIndicatorActionClickProgressHandler
-----------------------------------------------

Type: Class

Allows the consumer to decide whether the button's action should be completed successfully. The handler is provided with all nav button types.

### Properties

#### `advance: () => void`

Advances the progress indicator to the next step.

 SkyProgressIndicatorChange
---------------------------

Type: Interface

    interface SkyProgressIndicatorChange {
      activeIndex?: number;
      isComplete?: boolean;
      itemStatuses?: SkyProgressIndicatorItemStatus[];
    }

### Properties

#### `activeIndex?: number`

The active item.

#### `isComplete?: boolean`

Whether the progress indicator is complete.

#### `itemStatuses?: SkyProgressIndicatorItemStatus[]`

The array with the status of each item.

 SkyProgressIndicatorDisplayModeType
------------------------------------

Type: Type alias

    type SkyProgressIndicatorDisplayModeType = 0 | 1 | "vertical" | "horizontal"

 SkyProgressIndicatorItemStatus
-------------------------------

Type: Enumeration

    enum SkyProgressIndicatorItemStatus {
      Active = 0,
      Complete = 1,
      Incomplete = 2,
      Pending = 3,
    }

### Properties

#### `SkyProgressIndicatorItemStatus.Active`

The item is active.

#### `SkyProgressIndicatorItemStatus.Complete`

The item is complete.

#### `SkyProgressIndicatorItemStatus.Incomplete`

The item is incomplete.

#### `SkyProgressIndicatorItemStatus.Pending`

The item is pending.

 SkyProgressIndicatorNavButtonType
----------------------------------

Type: Type alias

The nav button type.

    type SkyProgressIndicatorNavButtonType = "finish" | "next" | "previous" | "reset"

 SkyProgressIndicatorMessage
----------------------------

Type: Interface

    interface SkyProgressIndicatorMessage {
      data?: { activeIndex?: number; [key: string]: any };
      type: SkyProgressIndicatorMessageType;
    }

### Properties

#### `data?: { activeIndex?: number; [key: string]: any }`

Used in conjunction with [SkyProgressIndicatorMessageType](/skyux/components/progress-indicator-wizard?docs-active-tab=design#enum_sky-progress-indicator-message-type.md).GoTo to travel to a specific step by specifying an index number on the `data.activeIndex` property.

#### `type: SkyProgressIndicatorMessageType`

The type of state change for the progress indicator.

 SkyProgressIndicatorMessageType
--------------------------------

Type: Enumeration

    enum SkyProgressIndicatorMessageType {
      Finish = 3,
      GoTo = 4,
      Progress = 0,
      Regress = 1,
      Reset = 2,
    }

### Properties

#### `SkyProgressIndicatorMessageType.Finish`

Progress is complete. This marks all items as complete and sets the last item as the active item.

#### `SkyProgressIndicatorMessageType.GoTo`

Moves progress to the item indicated by the `data.activeIndex` property.

#### `SkyProgressIndicatorMessageType.Progress`

The current step is complete. This completes the active item and moves to the next item.

#### `SkyProgressIndicatorMessageType.Regress`

Returns progress to the previous step. This moves from the active item to the item that precedes it.

#### `SkyProgressIndicatorMessageType.Reset`

Progress is incomplete. This marks all items as incomplete and sets the first item as the active item.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyProgressIndicatorHarness
----------------------------

Type: Class

`import { SkyProgressIndicatorHarness } from '@skyux/progress-indicator/testing';`

Harness for interacting with a progress indicator component in tests.

### Methods

#### `clickResetButton(): Promise<void>`

Clicks the reset button.

#### Returns

`Promise<void>`

#### `getItem(filter: SkyProgressIndicatorItemFilters): Promise<SkyProgressIndicatorItemHarness>`

Gets a specific progress indicator item based on the filter criteria.

#### Parameters

##### `filter: SkyProgressIndicatorItemFilters`

The filter criteria.

#### Returns

`Promise<SkyProgressIndicatorItemHarness>`

#### `getItems(filters?: SkyProgressIndicatorItemFilters): Promise<SkyProgressIndicatorItemHarness[]>`

Gets an array of progress indicator items based on the filter criteria. If no filter is provided, returns all progress indicator items.

#### Parameters

##### `filters?: SkyProgressIndicatorItemFilters`

The optional filter criteria.

#### Returns

`Promise<SkyProgressIndicatorItemHarness[]>`

#### `getTitle(): Promise<string>`

Gets the progress indicator title.

#### Returns

`Promise<string>`

#### `isPassive(): Promise<boolean>`

Whether the progress indicator is passive.

#### Returns

`Promise<boolean>`

#### `SkyProgressIndicatorHarness.with(filters: SkyProgressIndicatorFilters): HarnessPredicate<SkyProgressIndicatorHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyProgressIndicatorHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyProgressIndicatorFilters`

#### Returns

`HarnessPredicate<SkyProgressIndicatorHarness>`

 SkyProgressIndicatorFilters
----------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyProgressIndicatorHarness` instances.

    interface SkyProgressIndicatorFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyProgressIndicatorItemHarness
--------------------------------

Type: Class

`import { SkyProgressIndicatorItemHarness } from '@skyux/progress-indicator/testing';`

Harness for interacting with a progress indicator item component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help inline popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help inline popover title.

#### Returns

`Promise<undefined | string>`

#### `getTitle(): Promise<string>`

Gets the progress indicator item's title text.

#### Returns

`Promise<string>`

#### `isCompleted(): Promise<boolean>`

Whether the indicator item step is completed.

#### Returns

`Promise<boolean>`

#### `SkyProgressIndicatorItemHarness.with(filters: SkyProgressIndicatorItemFilters): HarnessPredicate<SkyProgressIndicatorItemHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyProgressIndicatorItemHarness` that meets certain criteria

#### Parameters

##### `filters: SkyProgressIndicatorItemFilters`

#### Returns

`HarnessPredicate<SkyProgressIndicatorItemHarness>`

 SkyProgressIndicatorItemFilters
--------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyProgressIndicatorItemHarness` instances.

    interface SkyProgressIndicatorItemFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.