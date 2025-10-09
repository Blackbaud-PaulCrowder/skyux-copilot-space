                  

 Status indicator
================

Status indicators highlight important status information that users need to address.

 Usage
------

### Use when

Use status indicators when users must address or be aware of important information while completing tasks.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/status-indicator/status-indicator-usage-1.eafbc9953a9194deeb63c64620a3af89.png)

Do use status indicators to highlight important information.

Use status indicators to call out important status information for items in a list or specific properties on a record.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/status-indicator/status-indicator-usage-2.497c426c43cffbcbc963475790c60602.png)

Do use status indicators to draw attention to items in a list that require action.

Use status indicators to highlight validation errors on input fields.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/status-indicator/status-indicator-usage-3.74cad9083da3668a4e5459ecc80e2f17.png)

Do use status indicators for validation error messages.

### Don't use when

Don't use status indicators to highlight statuses in the page summary. Use [labels](/skyux/components/label.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/status-indicator/status-indicator-usage-4a.dc095d03affae4a41f39738435684a8d.png)

Don't use status indicators for statuses in the page summary.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/status-indicator/status-indicator-usage-4b.4eb3d8f547e95e039fef695961e9468e.png)

Do use labels for statuses in the page summary.

Don't use status indicators when no user action is necessary and status information is not important enough to highlight. Use plain text instead to avoid the overuse of status indicators.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/status-indicator/status-indicator-usage-5.3cecd3dbd29c942c293c59fb3d5dd991.png)

Don't use status indicators when statuses do not convey critical information.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/status-indicator/status-indicator-usage-6.95cfc953393471238756e1395e782a84.png)

Do use statuses indicators to emphasize only important statuses.

 Anatomy
--------

1

Icon

2

Text label

3

Help inline button (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/status-indicator/status-indicator-anatomy.31d131f9374779a095b277594a2d2abd.png)

 Options
--------

### Status type

Danger: Danger

The danger indicator represents statuses that require immediate attention.  
Use this type for items such as failed processes, overdue items, and inputs with invalid values.

Warning: Warning

The warning indicator represents statuses or decisions with significant consequences.  
Use this type for items such as approaching expirations and changes with far-reaching or irreversible consequences.

Success: Success

The success indicator represents statuses of positive completion.  
Use this type for items such as successfully finished processes, completed tasks, and records that meet workflow requirements.

Attention: Info

The info indicator represents statuses or content with high interest but neutral meaning.  
Use this type for items such as high-level classifications on records and highlighted fields.

### Description type

Use a description type with status indicators to include a text equivalent for the icon and color information. This ensures that people who use assistive technologies receive equivalent information.

Status type

Description type

When to use

Example

Danger

`error`

Use when the indicator calls attention to an error.  
Includes "Error: " text.

Error: First name is required.

`important-warning`

Use when the indicator calls attention to information about a current status or situation that users should be aware of or that could have serious consequences.  
Includes "Important warning: " text.

Important warning: Overdue

`danger`

Use when the indicator calls attention to information that could help users avoid potentially serious consequences if an action is taken.  
Includes "Danger: " text.

Danger: You cannot undo this action.

Warning

`warning`

Use when the indicator calls attention to information about a current status or situation that has potentially minor consequences.  
Includes "Warning: " text.

Warning: Unpaid

`caution`

Use when the indicator calls attention to information that could help users avoid potentially minor consequences.  
Includes "Caution: " text.

Caution: The start time has already occurred.

Success

`success`

Use when the indicator calls attention to a successful result or positive state.  
Includes "Success: " text.

Success: All forms are submitted.

Info

`attention`

Use when the indicator calls attention to information that should be elevated in the information hierarchy of the page but is not positive or negative.  
Includes "Attention: " text.

Attention: Pending

Any

`none`

Use when the icon and color only call attention to the text associated with the indicator and the text carries all of the meaning in that context.

In progress

Any

`custom`

Set your own status indicator when none of the other description types are the text equivalent for what the icon and color communicate in your context.  
Includes the text "\[Custom text\]: ".

### Help inline button

When you need to supplement a status indicator label with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the label to invoke contextual user assistance.

 Related information
--------------------

### Components

*   [Alert](/skyux/components/alert.md)
*   [Help inline button](/skyux/components/help-inline.md)
*   [Label](/skyux/components/label.md)
*   [Toast](/skyux/components/toast.md)

### Guidelines

*   [Call out information](/skyux/design/guidelines/call-out-info.md)

 Installation
-------------

NPM package

`@skyux/indicators`[View in NPM](https://www.npmjs.com/package/@skyux/indicators) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/indicators/src/lib/modules/status-indicator/status-indicator.module.ts#L25) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/indicators`Copy None found.

 SkyStatusIndicatorModule
-------------------------

Type: Module

`import { SkyStatusIndicatorModule } from '@skyux/indicators';`

 SkyStatusIndicatorComponent
----------------------------

Type: Component

Selector: `sky-status-indicator`

Displays status text with an icon matching the specified indicator type. To display a help button beside the label, include a help button element, such as `sky-help-inline`, in the `sky-status-indicator` element and a `sky-control-help` CSS class on that help button element.

### Inputs

#### `descriptionType: SkyIndicatorDescriptionType | undefined`

Required

The predefined text to be read by screen readers for users who cannot see the indicator icon.

#### `customDescription: string | undefined`

The text to be read by screen readers for users who cannot see the indicator icon when `descriptionType` is `custom`.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified, a [help inline](/skyux/components/help-inline.md) button is placed beside the status indicator label. Clicking the button invokes global help as configured by the application.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified, a [help inline](/skyux/components/help-inline.md) button is added to the status indicator. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `indicatorType: SkyIndicatorIconType`

The style for the status indicator, which determines the icon.

Default: `"warning"`

 SkyIndicatorDescriptionType
----------------------------

Type: Type alias

    type SkyIndicatorDescriptionType = "attention" | "caution" | "completed" | "custom" | "danger" | "error" | "important-info" | "important-warning" | "none" | "success" | "warning"

 SkyIndicatorIconType
---------------------

Type: Type alias

    type SkyIndicatorIconType = "danger" | "info" | "success" | "warning"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyStatusIndicatorHarness
--------------------------

Type: Class

`import { SkyStatusIndicatorHarness } from '@skyux/indicators/testing';`

Harness for interacting with a status indicator component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getCustomDescription(): Promise<string>`

Gets the custom text used for the screen reader description of the status indicator component icon.

#### Returns

`Promise<string>`

#### `getDescriptionType(): Promise<SkyIndicatorDescriptionType>`

Gets the `descriptionType` of the status indicator component.

#### Returns

`Promise<SkyIndicatorDescriptionType>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help inline popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help inline popover title.

#### Returns

`Promise<undefined | string>`

#### `getIndicatorType(): Promise<undefined | SkyIndicatorIconType>`

Gets the current status indicator type.

#### Returns

`Promise<undefined | SkyIndicatorIconType>`

#### `getText(): Promise<string>`

Gets the current status indicator text.

#### Returns

`Promise<string>`

#### `SkyStatusIndicatorHarness.with(filters: SkyStatusIndicatorHarnessFilters): HarnessPredicate<SkyStatusIndicatorHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyStatusIndicatorHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyStatusIndicatorHarnessFilters`

#### Returns

`HarnessPredicate<SkyStatusIndicatorHarness>`

 SkyStatusIndicatorHarnessFilters
---------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyStatusIndicatorHarness](/skyux/components/status-indicator?docs-active-tab=design#class_sky-status-indicator-harness.md) instances.

    interface SkyStatusIndicatorHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.