                  

 Waterfall progress indicator
============================

Waterfall progress indicators walk users through sequential steps in lengthy or complex tasks.

 Usage
------

### Use when

Use waterfall progress indicators for long or complex setup processes with at least three steps that users typically complete only once. Waterfall indicators are ideal when events outside of the system force users to complete tasks in multiple sittings or when users must enter large amounts of data.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/progress-indicator/img/guidelines/waterfall-progress-layout.cd2ac4482f3aaa2f3e897c791e147711.png)

Do use waterfall progress indicators for complex configuration processes that users may complete in stages.

Use waterfall progress indicators when the complexity of steps varies drastically. For example, one step may require a full-screen modal for complex interactions, while another step requires a small modal for a few simple inputs. Waterfall steps can open [wizards](/skyux/components/tabs-wizard.md) if necessary.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/progress-indicator/img/guidelines/waterfall-progress-usage-2.c1e2b02f55dae37bfcb869ed91166c54.png)

Do use modals of the appropriate size for the interactions in each waterfall step.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/progress-indicator/img/guidelines/waterfall-progress-usage-3.706665f05f9332d49ca4ba42f7956f73.png)

Don't put inputs inside waterfall progress indicators.

### Don't use when

Don't use waterfall progress indicators when users monitor a sequence of events but are not responsible for completing the steps. Use [passive progress indicators](/skyux/components/progress-indicator-passive.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/progress-indicator/img/guidelines/passive-progress-usage-6.17741d2d153355397f9e3b21fe6aaf48.png)

Don't use waterfall progress indicators for steps outside of user control.

Don't use waterfall progress indicators when users perform tasks repeatedly or when tasks are best presented as multiple steps but only require a single sitting. Use [wizards](/skyux/components/tabs-wizard.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/progress-indicator/img/guidelines/waterfall-progress-usage-4.975f1967e0d9a476cded4ffc26cee4eb.png)

Don't use waterfall progress indicators for brief interactions, even when they are best divided into multiple steps.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/progress-indicator/img/guidelines/waterfall-progress-usage-5.be5f39c8ad75898ee2fdf988ca96f1bb.png)

Do use wizards for multi-step tasks that users perform repeatedly or complete in a single sitting.

Don't use waterfall progress indicators when processes include fewer than three steps or when the number or order of steps may change. If early decisions branch in different directions, arrange the workflow so that users make those decisions before the progress indicator.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/progress-indicator/img/guidelines/waterfall-progress-usage-6.3d9f16bce1415346c45c7f179ceba26c.png)

Don't present waterfall progress indicators before the extent of tasks is known.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/progress-indicator/img/guidelines/waterfall-progress-usage-7.fe42d36b6f0cf7bf55c7e01ffcc4bef1.png)

Do present decisions that determine the number and order of steps before showing waterfall progress indicators.

Don't use waterfall progress indicators to edit properties after completing configuration processes. Use [modals](/skyux/components/modal.md) instead.

If configuration properties are interrelated and require users to reexamine all or most properties, then reframe the editing task as “starting over” and restart the waterfall process.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/progress-indicator/img/guidelines/waterfall-progress-usage-8.9ae76e34ee7a0df14d6e2030294ab6ae.png)

Don't revert finished states to edit properties in waterfall progress indicators.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/progress-indicator/img/guidelines/waterfall-progress-usage-9.7f805c8f594ca907ec5ea3c466cfdcd1.png)

Do group related properties and let users edit them in isolation after they complete waterfall progress indicators.

 Anatomy
--------

1

Waterfall title

2

Step indicator

3

Step label

4

Completed step action

5

Active step action

6

Step details  (optional)

7

Help inline button  (optional)

8

Start-over action  (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/progress-indicator/img/guidelines/waterfall-anatomy.cb453c37569e35a93d66f310a916c8b3.png)

 Options
--------

### Waterfall title

We strongly recommend including a waterfall title to reflect the context of the overall task. Do not use a left-aligned page title when you include a waterfall title. The waterfall title does not change when users progress through the waterfall steps.

### Help inline button

When you need to supplement a waterfall title with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the title to invoke contextual user assistance.

### Step details

You can provide additional details about completed steps, but limit details to single pieces of information. Don't go overboard because users can reopen modals to review choices as necessary.

### Start-over action

You can include a start-over action to let users erase all saved data from the waterfall process. This returns users to the first step or to an earlier point in the workflow if decisions occurred before the waterfall progress indicator.

 Behavior & states
------------------

Waterfall progress indicators guide users through one active step at a time. When users complete a step, the progress indicator updates its step indicator and step action to the completed state and updates the next step indicator and step action to the active state. Users can review and edit completed steps, but this does not undo the completed state.

The final step summarizes the changes and requests user confirmation. You do not need to include all data that users enter in the summary, but confirmation is required. After users complete the final step, replace the waterfall progress indicator with a page that displays the finished or active state of the system.

 Content
--------

Use a waterfall title in place of an ordinary page title to provide context for the overall task. Follow the same pattern as modal titles and start the waterfall title with a verb that indicates the action that occurs when users complete the waterfall steps.

For step labels, start with a number and concisely describe the objective using the **<verb> <direct object>** format. In the label for the last step, describe the cumulative change that occurs at the end of the process.

Step action (button) labels closely follow step labels and use the same **<verb> <direct object>** format, but they do not need to be identical. For the first step action label, be generic and conversational (“Get started”), and for completed step actions, use verbs appropriate to post hoc actions (“Change”, “Edit”).

### Layout

Waterfall progress indicators are 400 pixels wide and centered inside the page. The waterfall title is the page title. Do not combine waterfall indicators with other content or actions. If waterfall indicators require extra context such as descriptions, links, or instructions, include it after the waterfall title and before the first step.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/progress-indicator/img/guidelines/waterfall-progress-layout.cd2ac4482f3aaa2f3e897c791e147711.png)

Do use waterfall progress indicators as the only content on a page while users complete them.

 Related information
--------------------

### Components

*   [Help inline button](/skyux/components/help-inline.md)
*   [Modal](/skyux/components/modal.md)
*   [Passive progress indicator](/skyux/components/progress-indicator-passive.md)
*   [Wizard (Tabs)](/skyux/components/tabs-wizard.md)

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

Used in conjunction with [SkyProgressIndicatorMessageType](/skyux/components/progress-indicator-waterfall?docs-active-tab=design#enum_sky-progress-indicator-message-type.md).GoTo to travel to a specific step by specifying an index number on the `data.activeIndex` property.

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