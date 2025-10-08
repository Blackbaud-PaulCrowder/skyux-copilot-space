# Design

                  Skip to Main Content

 Alert
=====

Alerts highlight critical information that users absolutely must see when they visit a page.

 Usage
------

### Use when

Use alerts when information is important enough and exceptional enough that users should see it before the rest of the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-1.d4dde6712ab50d1da8adb2288fcf23b3.png)

Do use alerts when users need to view information before the rest of the page.

Use alerts when the state of a record or another capability within a user workflow requires a call to action or greatly benefits from one.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-in-context.8ef80e64e8d5f228598bcd184fc111b9.png)

Do use alerts for information that is important in the current context.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-not-in-context.61ff313ce03c892a14e825b715edf2a6.png)

Don't use alerts for information or calls to action outside the current context.

### Don't use when

Don't use alerts to convey the normal lifecycle statuses of records or pages. Use [labels](/skyux/components/label.md) or [status indicators](/skyux/components/status-indicator.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-3.bdc42b28c9af107cef15f9bf0691d805.png)

Don't use alerts to highlight statuses on records or pages.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-4.e0816af204ac2d256ca60bef587c0497.png)

Do use labels or status indicators to convey record statuses.

Don't use alerts to display messages about the success or failure of user actions. Use [toasts](/skyux/components/toast.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-5.0fe0da1cca4028ddb4f62907ad4749b4.png)

Don't use alerts to highlight the outcomes of user actions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-6.6a56925c189da7b4e956d3ce75185562.png)

Do use toasts to call out the outcomes of user actions.

 Anatomy
--------

1

Alert icon

2

Text

3

Close button  (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-anatomy.158c63abee874dd554878d5b40003f92.png)

 Options
--------

### Alert type

Use the `danger` alert for error messages or to notify users when a record or another capability within a workflow is in an unusable state.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-type-1.edbfaba1ba3baa2034c93d9f611c2202.png)

Use the `warning` alert for messages that users should know about and perhaps act on but that do not constitute error states or indicate that something is wrong.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-type-4.b0e9ef8f7fec6c6915c367543e31f8ba.png)

Use the `success` alert for messages that convey a positive or successful state.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-type-3.4e6037556c6b245753fbe9d92c3e5817.png)

Use the `info` alert for messages that provide helpful information or context but do not require user action.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-1.d4dde6712ab50d1da8adb2288fcf23b3.png)

### Description type

Use a description type with alerts to include a text equivalent for the icon and color information. This ensures that people who use assistive technologies receive equivalent information.

Status type

Description type

When to use

Example

Danger

`important-warning`

Use when the alert calls attention to information about a current status or situation that users should be aware of or that could have serious consequences.  
Includes the text "Important warning: ".

Important warning:

Your trial has expired.

`danger`

Use when the alert calls attention to information that could help users avoid potentially serious consequences if an action is taken.  
Includes the text "Danger: ".

Danger:

Your account will close without your confirmation within 24 hours.

Warning

`warning`

Use when the alert calls attention to information about a current status or situation that has potentially minor consequences.  
Includes the text "Warning: ".

Warning:

This organization is on hold and will not receive updates.

`caution`

Use when the alert calls attention to information that could help users avoid potentially minor consequences.  
Includes the text "Caution: ".

Warning:

Changes will only update this month and not subsequent months.

Success

`success`

Use when the alert calls attention to information that communicates a successful result.  
Includes the text "Success: ".

Success:

The process is running securely.

Info

`attention`

Use when the alert calls attention to neutral information that should be elevated in the information hierarchy but does not require user action or indicate a successful result.  
Includes the text "Attention: ".

Attention:

No new updates for today.

Any

`custom`

Set your own alert when none of the other alert description types are the text equivalent for what the icon and color communicate in your context.  
Includes the text "\[custom text\]: ".

### Close button

If users should be able to dismiss alerts from the page after reading, you can include the close button.

Do not make alerts dismissible when it is important for users to see the alerts every time they access a page or when underlying data triggers the alerts.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-1.d4dde6712ab50d1da8adb2288fcf23b3.png)

 Content
--------

The text inside alerts can contain hyperlinks. For accessibility reasons, these links are not styled with blue text like other links.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-2.1b4d2f22af8f1433b43e1a566c8a8fa5.png)

 Layout
-------

Always place alerts at the top of the page above the page header.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-layout-1.07cb7c4c27072c6078a9e9cf43dee221.png)

Avoid stacking multiple alerts because they quickly lose their impact and clutter the page. Try alternate methods to display the information, or consolidate messages into one alert.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-layout-2.38bfa0f86fefb7397689d3630696ae17.png)

Don't accumulate multiple alerts at the top of a page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-layout-3.89bcfce7c2f3c89c3d8cd41bef1bfac7.png)

Do use a single alert to consolidate multiple messages when possible and use alternate display methods such as labels.

 Related information
--------------------

### Components

*   [Label](/skyux/components/label.md)
*   [Status indicator](/skyux/components/status-indicator.md)
*   [Toast](/skyux/components/toast.md)

### Guidelines

*   [Call out information](/skyux/design/guidelines/call-out-info.md)

 Installation
-------------

NPM package

`@skyux/indicators`[View in NPM](https://www.npmjs.com/package/@skyux/indicators) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/indicators/src/lib/modules/alert/alert.module.ts#L20) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/indicators`Copy None found.

 SkyAlertModule
---------------

Type: Module

`import { SkyAlertModule } from '@skyux/indicators';`

 SkyAlertComponent
------------------

Type: Component

Selector: `sky-alert`

### Inputs

#### `alertType: SkyIndicatorIconType | undefined`

The style for the alert, which determines the icon and background color. The valid options are `danger`, `info`, `success`, and `warning`.

Default: `"warning"`

#### `closeable: boolean | undefined`

Whether to include a close button for users to dismiss the alert.

Default: `false`

#### `closed: boolean | undefined`

Whether the alert is closed.

Default: `false`

#### `customDescription: string | undefined`

The text to be read by screen readers for users who cannot see the indicator icon when `descriptionType` is `custom`.

#### `descriptionType: SkyIndicatorDescriptionType | undefined`

The predefined text to be read by screen readers for users who cannot see the alert icon. This property is optional but will be required in future versions of SKY UX.

### Outputs

#### `closedChange: EventEmitter<boolean>`

Fires when users close the alert.

 SkyIndicatorIconType
---------------------

Type: Type alias

    type SkyIndicatorIconType = "danger" | "info" | "success" | "warning"

 SkyIndicatorDescriptionType
----------------------------

Type: Type alias

    type SkyIndicatorDescriptionType = "attention" | "caution" | "completed" | "custom" | "danger" | "error" | "important-info" | "important-warning" | "none" | "success" | "warning"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyAlertHarness
----------------

Type: Class

`import { SkyAlertHarness } from '@skyux/indicators/testing';`

Harness for interacting with an alert component in tests.

### Methods

#### `close(): Promise<void>`

Closes the alert.

#### Returns

`Promise<void>`

#### `getAlertType(): Promise<undefined | SkyIndicatorIconType>`

Gets the current alert type.

#### Returns

`Promise<undefined | SkyIndicatorIconType>`

#### `getCustomDescription(): Promise<string>`

Gets the custom text used for the screen reader description of the label component icon.

#### Returns

`Promise<string>`

#### `getDescriptionType(): Promise<SkyIndicatorDescriptionType>`

Gets the `descriptionType` of the label component.

#### Returns

`Promise<SkyIndicatorDescriptionType>`

#### `getText(): Promise<string>`

Gets the current alert text.

#### Returns

`Promise<string>`

#### `isCloseable(): Promise<boolean>`

Whether the user can close the alert.

#### Returns

`Promise<boolean>`

#### `isClosed(): Promise<boolean>`

Whether the user closed the alert.

#### Returns

`Promise<boolean>`

#### `SkyAlertHarness.with(filters: SkyAlertHarnessFilters): HarnessPredicate<SkyAlertHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyAlertHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyAlertHarnessFilters`

#### Returns

`HarnessPredicate<SkyAlertHarness>`

 SkyAlertHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyAlertHarness](/skyux/components/alert?docs-active-tab=design#class_sky-alert-harness.md) instances.

    interface SkyAlertHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Development

                  Skip to Main Content

 Alert
=====

Alerts highlight critical information that users absolutely must see when they visit a page.

 Usage
------

### Use when

Use alerts when information is important enough and exceptional enough that users should see it before the rest of the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-1.d4dde6712ab50d1da8adb2288fcf23b3.png)

Do use alerts when users need to view information before the rest of the page.

Use alerts when the state of a record or another capability within a user workflow requires a call to action or greatly benefits from one.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-in-context.8ef80e64e8d5f228598bcd184fc111b9.png)

Do use alerts for information that is important in the current context.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-not-in-context.61ff313ce03c892a14e825b715edf2a6.png)

Don't use alerts for information or calls to action outside the current context.

### Don't use when

Don't use alerts to convey the normal lifecycle statuses of records or pages. Use [labels](/skyux/components/label.md) or [status indicators](/skyux/components/status-indicator.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-3.bdc42b28c9af107cef15f9bf0691d805.png)

Don't use alerts to highlight statuses on records or pages.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-4.e0816af204ac2d256ca60bef587c0497.png)

Do use labels or status indicators to convey record statuses.

Don't use alerts to display messages about the success or failure of user actions. Use [toasts](/skyux/components/toast.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-5.0fe0da1cca4028ddb4f62907ad4749b4.png)

Don't use alerts to highlight the outcomes of user actions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-6.6a56925c189da7b4e956d3ce75185562.png)

Do use toasts to call out the outcomes of user actions.

 Anatomy
--------

1

Alert icon

2

Text

3

Close button  (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-anatomy.158c63abee874dd554878d5b40003f92.png)

 Options
--------

### Alert type

Use the `danger` alert for error messages or to notify users when a record or another capability within a workflow is in an unusable state.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-type-1.edbfaba1ba3baa2034c93d9f611c2202.png)

Use the `warning` alert for messages that users should know about and perhaps act on but that do not constitute error states or indicate that something is wrong.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-type-4.b0e9ef8f7fec6c6915c367543e31f8ba.png)

Use the `success` alert for messages that convey a positive or successful state.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-type-3.4e6037556c6b245753fbe9d92c3e5817.png)

Use the `info` alert for messages that provide helpful information or context but do not require user action.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-1.d4dde6712ab50d1da8adb2288fcf23b3.png)

### Description type

Use a description type with alerts to include a text equivalent for the icon and color information. This ensures that people who use assistive technologies receive equivalent information.

Status type

Description type

When to use

Example

Danger

`important-warning`

Use when the alert calls attention to information about a current status or situation that users should be aware of or that could have serious consequences.  
Includes the text "Important warning: ".

Important warning:

Your trial has expired.

`danger`

Use when the alert calls attention to information that could help users avoid potentially serious consequences if an action is taken.  
Includes the text "Danger: ".

Danger:

Your account will close without your confirmation within 24 hours.

Warning

`warning`

Use when the alert calls attention to information about a current status or situation that has potentially minor consequences.  
Includes the text "Warning: ".

Warning:

This organization is on hold and will not receive updates.

`caution`

Use when the alert calls attention to information that could help users avoid potentially minor consequences.  
Includes the text "Caution: ".

Warning:

Changes will only update this month and not subsequent months.

Success

`success`

Use when the alert calls attention to information that communicates a successful result.  
Includes the text "Success: ".

Success:

The process is running securely.

Info

`attention`

Use when the alert calls attention to neutral information that should be elevated in the information hierarchy but does not require user action or indicate a successful result.  
Includes the text "Attention: ".

Attention:

No new updates for today.

Any

`custom`

Set your own alert when none of the other alert description types are the text equivalent for what the icon and color communicate in your context.  
Includes the text "\[custom text\]: ".

### Close button

If users should be able to dismiss alerts from the page after reading, you can include the close button.

Do not make alerts dismissible when it is important for users to see the alerts every time they access a page or when underlying data triggers the alerts.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-1.d4dde6712ab50d1da8adb2288fcf23b3.png)

 Content
--------

The text inside alerts can contain hyperlinks. For accessibility reasons, these links are not styled with blue text like other links.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-2.1b4d2f22af8f1433b43e1a566c8a8fa5.png)

 Layout
-------

Always place alerts at the top of the page above the page header.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-layout-1.07cb7c4c27072c6078a9e9cf43dee221.png)

Avoid stacking multiple alerts because they quickly lose their impact and clutter the page. Try alternate methods to display the information, or consolidate messages into one alert.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-layout-2.38bfa0f86fefb7397689d3630696ae17.png)

Don't accumulate multiple alerts at the top of a page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-layout-3.89bcfce7c2f3c89c3d8cd41bef1bfac7.png)

Do use a single alert to consolidate multiple messages when possible and use alternate display methods such as labels.

 Related information
--------------------

### Components

*   [Label](/skyux/components/label.md)
*   [Status indicator](/skyux/components/status-indicator.md)
*   [Toast](/skyux/components/toast.md)

### Guidelines

*   [Call out information](/skyux/design/guidelines/call-out-info.md)

 Installation
-------------

NPM package

`@skyux/indicators`[View in NPM](https://www.npmjs.com/package/@skyux/indicators) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/indicators/src/lib/modules/alert/alert.module.ts#L20) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/indicators`Copy None found.

 SkyAlertModule
---------------

Type: Module

`import { SkyAlertModule } from '@skyux/indicators';`

 SkyAlertComponent
------------------

Type: Component

Selector: `sky-alert`

### Inputs

#### `alertType: SkyIndicatorIconType | undefined`

The style for the alert, which determines the icon and background color. The valid options are `danger`, `info`, `success`, and `warning`.

Default: `"warning"`

#### `closeable: boolean | undefined`

Whether to include a close button for users to dismiss the alert.

Default: `false`

#### `closed: boolean | undefined`

Whether the alert is closed.

Default: `false`

#### `customDescription: string | undefined`

The text to be read by screen readers for users who cannot see the indicator icon when `descriptionType` is `custom`.

#### `descriptionType: SkyIndicatorDescriptionType | undefined`

The predefined text to be read by screen readers for users who cannot see the alert icon. This property is optional but will be required in future versions of SKY UX.

### Outputs

#### `closedChange: EventEmitter<boolean>`

Fires when users close the alert.

 SkyIndicatorIconType
---------------------

Type: Type alias

    type SkyIndicatorIconType = "danger" | "info" | "success" | "warning"

 SkyIndicatorDescriptionType
----------------------------

Type: Type alias

    type SkyIndicatorDescriptionType = "attention" | "caution" | "completed" | "custom" | "danger" | "error" | "important-info" | "important-warning" | "none" | "success" | "warning"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyAlertHarness
----------------

Type: Class

`import { SkyAlertHarness } from '@skyux/indicators/testing';`

Harness for interacting with an alert component in tests.

### Methods

#### `close(): Promise<void>`

Closes the alert.

#### Returns

`Promise<void>`

#### `getAlertType(): Promise<undefined | SkyIndicatorIconType>`

Gets the current alert type.

#### Returns

`Promise<undefined | SkyIndicatorIconType>`

#### `getCustomDescription(): Promise<string>`

Gets the custom text used for the screen reader description of the label component icon.

#### Returns

`Promise<string>`

#### `getDescriptionType(): Promise<SkyIndicatorDescriptionType>`

Gets the `descriptionType` of the label component.

#### Returns

`Promise<SkyIndicatorDescriptionType>`

#### `getText(): Promise<string>`

Gets the current alert text.

#### Returns

`Promise<string>`

#### `isCloseable(): Promise<boolean>`

Whether the user can close the alert.

#### Returns

`Promise<boolean>`

#### `isClosed(): Promise<boolean>`

Whether the user closed the alert.

#### Returns

`Promise<boolean>`

#### `SkyAlertHarness.with(filters: SkyAlertHarnessFilters): HarnessPredicate<SkyAlertHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyAlertHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyAlertHarnessFilters`

#### Returns

`HarnessPredicate<SkyAlertHarness>`

 SkyAlertHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyAlertHarness](/skyux/components/alert?docs-active-tab=development#class_sky-alert-harness.md) instances.

    interface SkyAlertHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

# Examples

                    Skip to Main Content

 Alert
=====

Alerts highlight critical information that users absolutely must see when they visit a page.Usage
------

### Use when

Use alerts when information is important enough and exceptional enough that users should see it before the rest of the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-1.d4dde6712ab50d1da8adb2288fcf23b3.png)

Do use alerts when users need to view information before the rest of the page.

Use alerts when the state of a record or another capability within a user workflow requires a call to action or greatly benefits from one.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-in-context.8ef80e64e8d5f228598bcd184fc111b9.png)

Do use alerts for information that is important in the current context.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-not-in-context.61ff313ce03c892a14e825b715edf2a6.png)

Don't use alerts for information or calls to action outside the current context.

### Don't use when

Don't use alerts to convey the normal lifecycle statuses of records or pages. Use [labels](/skyux/components/label.md) or [status indicators](/skyux/components/status-indicator.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-3.bdc42b28c9af107cef15f9bf0691d805.png)

Don't use alerts to highlight statuses on records or pages.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-4.e0816af204ac2d256ca60bef587c0497.png)

Do use labels or status indicators to convey record statuses.

Don't use alerts to display messages about the success or failure of user actions. Use [toasts](/skyux/components/toast.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-5.0fe0da1cca4028ddb4f62907ad4749b4.png)

Don't use alerts to highlight the outcomes of user actions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-6.6a56925c189da7b4e956d3ce75185562.png)

Do use toasts to call out the outcomes of user actions.

 Anatomy
--------

1

Alert icon

2

Text

3

Close button  (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-anatomy.158c63abee874dd554878d5b40003f92.png)

 Options
--------

### Alert type

Use the `danger` alert for error messages or to notify users when a record or another capability within a workflow is in an unusable state.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-type-1.edbfaba1ba3baa2034c93d9f611c2202.png)

Use the `warning` alert for messages that users should know about and perhaps act on but that do not constitute error states or indicate that something is wrong.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-type-4.b0e9ef8f7fec6c6915c367543e31f8ba.png)

Use the `success` alert for messages that convey a positive or successful state.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-type-3.4e6037556c6b245753fbe9d92c3e5817.png)

Use the `info` alert for messages that provide helpful information or context but do not require user action.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-1.d4dde6712ab50d1da8adb2288fcf23b3.png)

### Description type

Use a description type with alerts to include a text equivalent for the icon and color information. This ensures that people who use assistive technologies receive equivalent information.

Status type

Description type

When to use

Example

Danger

`important-warning`

Use when the alert calls attention to information about a current status or situation that users should be aware of or that could have serious consequences.  
Includes the text "Important warning: ".

Important warning:

Your trial has expired.

`danger`

Use when the alert calls attention to information that could help users avoid potentially serious consequences if an action is taken.  
Includes the text "Danger: ".

Danger:

Your account will close without your confirmation within 24 hours.

Warning

`warning`

Use when the alert calls attention to information about a current status or situation that has potentially minor consequences.  
Includes the text "Warning: ".

Warning:

This organization is on hold and will not receive updates.

`caution`

Use when the alert calls attention to information that could help users avoid potentially minor consequences.  
Includes the text "Caution: ".

Warning:

Changes will only update this month and not subsequent months.

Success

`success`

Use when the alert calls attention to information that communicates a successful result.  
Includes the text "Success: ".

Success:

The process is running securely.

Info

`attention`

Use when the alert calls attention to neutral information that should be elevated in the information hierarchy but does not require user action or indicate a successful result.  
Includes the text "Attention: ".

Attention:

No new updates for today.

Any

`custom`

Set your own alert when none of the other alert description types are the text equivalent for what the icon and color communicate in your context.  
Includes the text "\[custom text\]: ".

### Close button

If users should be able to dismiss alerts from the page after reading, you can include the close button.

Do not make alerts dismissible when it is important for users to see the alerts every time they access a page or when underlying data triggers the alerts.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-1.d4dde6712ab50d1da8adb2288fcf23b3.png)

 Content
--------

The text inside alerts can contain hyperlinks. For accessibility reasons, these links are not styled with blue text like other links.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-2.1b4d2f22af8f1433b43e1a566c8a8fa5.png)

 Layout
-------

Always place alerts at the top of the page above the page header.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-layout-1.07cb7c4c27072c6078a9e9cf43dee221.png)

Avoid stacking multiple alerts because they quickly lose their impact and clutter the page. Try alternate methods to display the information, or consolidate messages into one alert.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-layout-2.38bfa0f86fefb7397689d3630696ae17.png)

Don't accumulate multiple alerts at the top of a page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-layout-3.89bcfce7c2f3c89c3d8cd41bef1bfac7.png)

Do use a single alert to consolidate multiple messages when possible and use alternate display methods such as labels.

 Related information
--------------------

### Components

*   [Label](/skyux/components/label.md)
*   [Status indicator](/skyux/components/status-indicator.md)
*   [Toast](/skyux/components/toast.md)

### Guidelines

*   [Call out information](/skyux/design/guidelines/call-out-info.md)

 Installation
-------------

NPM package

`@skyux/indicators`[View in NPM](https://www.npmjs.com/package/@skyux/indicators) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/indicators/src/lib/modules/alert/alert.module.ts#L20) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/indicators`Copy None found.

 SkyAlertModule
---------------

Type: Module

`import { SkyAlertModule } from '@skyux/indicators';`

 SkyAlertComponent
------------------

Type: Component

Selector: `sky-alert`

### Inputs

#### `alertType: SkyIndicatorIconType | undefined`

The style for the alert, which determines the icon and background color. The valid options are `danger`, `info`, `success`, and `warning`.

Default: `"warning"`

#### `closeable: boolean | undefined`

Whether to include a close button for users to dismiss the alert.

Default: `false`

#### `closed: boolean | undefined`

Whether the alert is closed.

Default: `false`

#### `customDescription: string | undefined`

The text to be read by screen readers for users who cannot see the indicator icon when `descriptionType` is `custom`.

#### `descriptionType: SkyIndicatorDescriptionType | undefined`

The predefined text to be read by screen readers for users who cannot see the alert icon. This property is optional but will be required in future versions of SKY UX.

### Outputs

#### `closedChange: EventEmitter<boolean>`

Fires when users close the alert.

 SkyIndicatorIconType
---------------------

Type: Type alias

    type SkyIndicatorIconType = "danger" | "info" | "success" | "warning"

 SkyIndicatorDescriptionType
----------------------------

Type: Type alias

    type SkyIndicatorDescriptionType = "attention" | "caution" | "completed" | "custom" | "danger" | "error" | "important-info" | "important-warning" | "none" | "success" | "warning"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyAlertHarness
----------------

Type: Class

`import { SkyAlertHarness } from '@skyux/indicators/testing';`

Harness for interacting with an alert component in tests.

### Methods

#### `close(): Promise<void>`

Closes the alert.

#### Returns

`Promise<void>`

#### `getAlertType(): Promise<undefined | SkyIndicatorIconType>`

Gets the current alert type.

#### Returns

`Promise<undefined | SkyIndicatorIconType>`

#### `getCustomDescription(): Promise<string>`

Gets the custom text used for the screen reader description of the label component icon.

#### Returns

`Promise<string>`

#### `getDescriptionType(): Promise<SkyIndicatorDescriptionType>`

Gets the `descriptionType` of the label component.

#### Returns

`Promise<SkyIndicatorDescriptionType>`

#### `getText(): Promise<string>`

Gets the current alert text.

#### Returns

`Promise<string>`

#### `isCloseable(): Promise<boolean>`

Whether the user can close the alert.

#### Returns

`Promise<boolean>`

#### `isClosed(): Promise<boolean>`

Whether the user closed the alert.

#### Returns

`Promise<boolean>`

#### `SkyAlertHarness.with(filters: SkyAlertHarnessFilters): HarnessPredicate<SkyAlertHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyAlertHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyAlertHarnessFilters`

#### Returns

`HarnessPredicate<SkyAlertHarness>`

 SkyAlertHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyAlertHarness](/skyux/components/alert?docs-active-tab=examples#class_sky-alert-harness.md) instances.

    interface SkyAlertHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

### Alert with basic setup

Edit in StackBlitz

Important warning:

Your password expires in 9 day(s)!

Show code

Copy

    <sky-alert
      data-sky-id="alert-example"
      [alertType]="days < 8 ? 'danger' : 'warning'"
      [closeable]="days >= 8"
      [descriptionType]="days < 8 ? 'danger' : 'important-warning'"
      (closedChange)="onClosedChange($event)"
    >
      Your password expires in {{ days }} day(s)!
    </sky-alert>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { SkyAlertHarness } from '@skyux/indicators/testing';
    
    import { IndicatorsAlertBasicExampleComponent } from './example.component';
    
    describe('Basic alert', () => {
      async function setupTest(options?: { days?: number }): Promise<{
        alertHarness: SkyAlertHarness;
        fixture: ComponentFixture<IndicatorsAlertBasicExampleComponent>;
      }> {
        const fixture = TestBed.createComponent(
          IndicatorsAlertBasicExampleComponent,
        );
    
        if (options?.days !== undefined) {
          fixture.componentInstance.days = options.days;
        }
    
        const loader = TestbedHarnessEnvironment.loader(fixture);
    
        const alertHarness = await loader.getHarness(
          SkyAlertHarness.with({ dataSkyId: 'alert-example' }),
        );
    
        return { alertHarness, fixture };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [IndicatorsAlertBasicExampleComponent],
        });
      });
    
      it('should show the expected alert when the number of days is 8 or more', async () => {
        const { alertHarness, fixture } = await setupTest({ days: 8 });
        fixture.detectChanges();
    
        await expectAsync(alertHarness.getAlertType()).toBeResolvedTo('warning');
        await expectAsync(alertHarness.getText()).toBeResolvedTo(
          'Your password expires in 8 day(s)!',
        );
        await expectAsync(alertHarness.isCloseable()).toBeResolvedTo(true);
      });
    
      it('should show the expected alert when the number of days is 7 or fewer', async () => {
        const { alertHarness, fixture } = await setupTest({ days: 7 });
        fixture.detectChanges();
    
        await expectAsync(alertHarness.getAlertType()).toBeResolvedTo('danger');
        await expectAsync(alertHarness.getText()).toBeResolvedTo(
          'Your password expires in 7 day(s)!',
        );
        await expectAsync(alertHarness.isCloseable()).toBeResolvedTo(false);
      });
    });

Copy

    import { ChangeDetectionStrategy, Component, Input } from '@angular/core';
    import { SkyAlertModule } from '@skyux/indicators';
    
    /**
     * @title Alert with basic setup
     */
    @Component({
      selector: 'app-indicators-alert-basic-example',
      templateUrl: './example.component.html',
      changeDetection: ChangeDetectionStrategy.OnPush,
      imports: [SkyAlertModule],
    })
    export class IndicatorsAlertBasicExampleComponent {
      @Input()
      public days = 9;
    
      protected onClosedChange(event: boolean): void {
        alert(`Alert closed with: ${event}`);
      }
    }

# Testing

                  Skip to Main Content

 Alert
=====

Alerts highlight critical information that users absolutely must see when they visit a page.

 Usage
------

### Use when

Use alerts when information is important enough and exceptional enough that users should see it before the rest of the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-1.d4dde6712ab50d1da8adb2288fcf23b3.png)

Do use alerts when users need to view information before the rest of the page.

Use alerts when the state of a record or another capability within a user workflow requires a call to action or greatly benefits from one.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-in-context.8ef80e64e8d5f228598bcd184fc111b9.png)

Do use alerts for information that is important in the current context.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-not-in-context.61ff313ce03c892a14e825b715edf2a6.png)

Don't use alerts for information or calls to action outside the current context.

### Don't use when

Don't use alerts to convey the normal lifecycle statuses of records or pages. Use [labels](/skyux/components/label.md) or [status indicators](/skyux/components/status-indicator.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-3.bdc42b28c9af107cef15f9bf0691d805.png)

Don't use alerts to highlight statuses on records or pages.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-4.e0816af204ac2d256ca60bef587c0497.png)

Do use labels or status indicators to convey record statuses.

Don't use alerts to display messages about the success or failure of user actions. Use [toasts](/skyux/components/toast.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-5.0fe0da1cca4028ddb4f62907ad4749b4.png)

Don't use alerts to highlight the outcomes of user actions.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-6.6a56925c189da7b4e956d3ce75185562.png)

Do use toasts to call out the outcomes of user actions.

 Anatomy
--------

1

Alert icon

2

Text

3

Close button  (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-anatomy.158c63abee874dd554878d5b40003f92.png)

 Options
--------

### Alert type

Use the `danger` alert for error messages or to notify users when a record or another capability within a workflow is in an unusable state.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-type-1.edbfaba1ba3baa2034c93d9f611c2202.png)

Use the `warning` alert for messages that users should know about and perhaps act on but that do not constitute error states or indicate that something is wrong.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-type-4.b0e9ef8f7fec6c6915c367543e31f8ba.png)

Use the `success` alert for messages that convey a positive or successful state.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-type-3.4e6037556c6b245753fbe9d92c3e5817.png)

Use the `info` alert for messages that provide helpful information or context but do not require user action.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-1.d4dde6712ab50d1da8adb2288fcf23b3.png)

### Description type

Use a description type with alerts to include a text equivalent for the icon and color information. This ensures that people who use assistive technologies receive equivalent information.

Status type

Description type

When to use

Example

Danger

`important-warning`

Use when the alert calls attention to information about a current status or situation that users should be aware of or that could have serious consequences.  
Includes the text "Important warning: ".

Important warning:

Your trial has expired.

`danger`

Use when the alert calls attention to information that could help users avoid potentially serious consequences if an action is taken.  
Includes the text "Danger: ".

Danger:

Your account will close without your confirmation within 24 hours.

Warning

`warning`

Use when the alert calls attention to information about a current status or situation that has potentially minor consequences.  
Includes the text "Warning: ".

Warning:

This organization is on hold and will not receive updates.

`caution`

Use when the alert calls attention to information that could help users avoid potentially minor consequences.  
Includes the text "Caution: ".

Warning:

Changes will only update this month and not subsequent months.

Success

`success`

Use when the alert calls attention to information that communicates a successful result.  
Includes the text "Success: ".

Success:

The process is running securely.

Info

`attention`

Use when the alert calls attention to neutral information that should be elevated in the information hierarchy but does not require user action or indicate a successful result.  
Includes the text "Attention: ".

Attention:

No new updates for today.

Any

`custom`

Set your own alert when none of the other alert description types are the text equivalent for what the icon and color communicate in your context.  
Includes the text "\[custom text\]: ".

### Close button

If users should be able to dismiss alerts from the page after reading, you can include the close button.

Do not make alerts dismissible when it is important for users to see the alerts every time they access a page or when underlying data triggers the alerts.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-1.d4dde6712ab50d1da8adb2288fcf23b3.png)

 Content
--------

The text inside alerts can contain hyperlinks. For accessibility reasons, these links are not styled with blue text like other links.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-usage-2.1b4d2f22af8f1433b43e1a566c8a8fa5.png)

 Layout
-------

Always place alerts at the top of the page above the page header.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-layout-1.07cb7c4c27072c6078a9e9cf43dee221.png)

Avoid stacking multiple alerts because they quickly lose their impact and clutter the page. Try alternate methods to display the information, or consolidate messages into one alert.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-layout-2.38bfa0f86fefb7397689d3630696ae17.png)

Don't accumulate multiple alerts at the top of a page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/alert/alert-layout-3.89bcfce7c2f3c89c3d8cd41bef1bfac7.png)

Do use a single alert to consolidate multiple messages when possible and use alternate display methods such as labels.

 Related information
--------------------

### Components

*   [Label](/skyux/components/label.md)
*   [Status indicator](/skyux/components/status-indicator.md)
*   [Toast](/skyux/components/toast.md)

### Guidelines

*   [Call out information](/skyux/design/guidelines/call-out-info.md)

 Installation
-------------

NPM package

`@skyux/indicators`[View in NPM](https://www.npmjs.com/package/@skyux/indicators) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/indicators/src/lib/modules/alert/alert.module.ts#L20) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/indicators`Copy None found.

 SkyAlertModule
---------------

Type: Module

`import { SkyAlertModule } from '@skyux/indicators';`

 SkyAlertComponent
------------------

Type: Component

Selector: `sky-alert`

### Inputs

#### `alertType: SkyIndicatorIconType | undefined`

The style for the alert, which determines the icon and background color. The valid options are `danger`, `info`, `success`, and `warning`.

Default: `"warning"`

#### `closeable: boolean | undefined`

Whether to include a close button for users to dismiss the alert.

Default: `false`

#### `closed: boolean | undefined`

Whether the alert is closed.

Default: `false`

#### `customDescription: string | undefined`

The text to be read by screen readers for users who cannot see the indicator icon when `descriptionType` is `custom`.

#### `descriptionType: SkyIndicatorDescriptionType | undefined`

The predefined text to be read by screen readers for users who cannot see the alert icon. This property is optional but will be required in future versions of SKY UX.

### Outputs

#### `closedChange: EventEmitter<boolean>`

Fires when users close the alert.

 SkyIndicatorIconType
---------------------

Type: Type alias

    type SkyIndicatorIconType = "danger" | "info" | "success" | "warning"

 SkyIndicatorDescriptionType
----------------------------

Type: Type alias

    type SkyIndicatorDescriptionType = "attention" | "caution" | "completed" | "custom" | "danger" | "error" | "important-info" | "important-warning" | "none" | "success" | "warning"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyAlertHarness
----------------

Type: Class

`import { SkyAlertHarness } from '@skyux/indicators/testing';`

Harness for interacting with an alert component in tests.

### Methods

#### `close(): Promise<void>`

Closes the alert.

#### Returns

`Promise<void>`

#### `getAlertType(): Promise<undefined | SkyIndicatorIconType>`

Gets the current alert type.

#### Returns

`Promise<undefined | SkyIndicatorIconType>`

#### `getCustomDescription(): Promise<string>`

Gets the custom text used for the screen reader description of the label component icon.

#### Returns

`Promise<string>`

#### `getDescriptionType(): Promise<SkyIndicatorDescriptionType>`

Gets the `descriptionType` of the label component.

#### Returns

`Promise<SkyIndicatorDescriptionType>`

#### `getText(): Promise<string>`

Gets the current alert text.

#### Returns

`Promise<string>`

#### `isCloseable(): Promise<boolean>`

Whether the user can close the alert.

#### Returns

`Promise<boolean>`

#### `isClosed(): Promise<boolean>`

Whether the user closed the alert.

#### Returns

`Promise<boolean>`

#### `SkyAlertHarness.with(filters: SkyAlertHarnessFilters): HarnessPredicate<SkyAlertHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyAlertHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyAlertHarnessFilters`

#### Returns

`HarnessPredicate<SkyAlertHarness>`

 SkyAlertHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyAlertHarness](/skyux/components/alert?docs-active-tab=testing#class_sky-alert-harness.md) instances.

    interface SkyAlertHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.