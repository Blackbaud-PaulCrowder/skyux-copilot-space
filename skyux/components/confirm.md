# Design

                  Skip to Main Content

 Confirm
=======

The confirm service launches simple confirmation dialogs that prompt users to confirm actions.

 Usage
------

### Use when

Use confirmation dialogs to focus user attention when actions are destructive or could be costly if performed by mistake. Prompt users to confirm an action with a single question and provide terminal actions to answer the question.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/confirm/confirm-usage-1.90c28a0beb69af121ab75415471ff5a5.png)

Do use confirmation dialogs to inform users of consequences and to prompt them to confirm potentially costly actions.

Use confirmation dialogs with a lone terminal action when users need to acknowledge important information but don't need to make a decision, such as when they need to know why they can't perform an action.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/confirm/confirm-usage-2.4323041c0e5da75f7edb16c7c82c4414.png)

Do use confirmation dialogs to prompt users to ackowledge important information.

### Don't use when

Don't use confirmation dialogs when user responses require input fields.

Don't use confirmation dialogs when the context requires significant explanation, illustration, or dynamic feedback from downstream consequences.

 Anatomy
--------

1

Modal

2

Heading

3

Actions

4

Body text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/confirm/confirm-anatomy.a52cf24c55ed8c0fe3343b0edac98e69.png)

 Options
--------

### Actions

Include up to three terminal actions to answer the question in the heading. And for confirmation dialogs that present important information without requiring a decision, include a lone action that acknowledges the information.

*   A primary button triggers the recommended or most-common action.
*   A secondary button triggers a less-common action.
*   A link button cancels the action.
*   Each button closes the dialog.

#### Primary actions that delete existing data

When a confirmation dialog's primary action deletes existing data, such as records or settings, use the `sky-btn-danger` style for a red background. Don't use this style for any other buttons, including actions that delete unsaved data and secondary actions that delete existing data.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/confirm/confirm-content-1.680e21b3d5d3c14ffc942e0f734cd449.png)

Do use the red danger style when primary buttons delete existing content.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/confirm/confirm-content-2-.8761f622658c4d9f731d0fd1eeca1983.png)

Don't use the red danger style when actions require confirmation but don't delete existing data.

### Body text

Use body text to provide context and describe potential consequences.

 Content
--------

### Heading

Limit the confirmation dialog's heading to a single sentence. In most cases, the heading poses a question that users answer when they select an action.

*   Be concise and direct. Don't use confirmation dialogs when the context requires significant explanation, illustration, or dynamic feedback from downstream consequences.
*   Avoid verbose or complicated phrasing. For example, only start questions with "Are you sure you want to" when the results of an action might be unexpected and it's important for users to think twice before they proceed. When a confirmation dialog appears after users select a delete button, a question such as "Delete this account?" is sufficient because the action is usually intentional. However, when deleting data is likely an unintended consequence of another action, such as closing a modal with unsaved data, the extra verbiage of "Are you sure you want to delete this account?" can prompt users to think twice before they confirm.

### Body text

If a confirmation message requires additional context or an explanation of potential consequences, include body text. Body text can be more than one sentence. It can help users answer the question in the heading and explain what will happen if they proceed.

### Actions

Use labels that clearly indicate what happens when users select buttons. For example, if a confirmation dialog asks users to confirm that they want to delete something, use "Delete" for the primary button.

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/modals`[View in NPM](https://www.npmjs.com/package/@skyux/modals) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/modals/src/lib/modules/confirm/confirm.service.ts#L17) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/modals`Copy None found.

 SkyConfirmService
------------------

Type: Service

Launches a dialog.

### Methods

#### `open(config: SkyConfirmConfig): SkyConfirmInstance`

Opens a dialog using the specified options.

#### Parameters

##### `config: SkyConfirmConfig`

Specifies configuration options for the dialog.

#### Returns

`SkyConfirmInstance`

 SkyConfirmConfig
-----------------

Type: Interface

    interface SkyConfirmConfig {
      body?: string;
      buttons?: SkyConfirmButtonConfig[];
      message: string;
      preserveWhiteSpace?: boolean;
      type?: SkyConfirmType;
    }

### Properties

#### `body?: string`

Secondary text to display under the primary message.

#### `buttons?: SkyConfirmButtonConfig[]`

The list of buttons to display when the `type` property is set to `SkyConfirmType.Custom`.

#### `message: string`

The message to display in bold at the top of the dialog.

#### `preserveWhiteSpace?: boolean`

Whether to preserve whitespace and new lines inside the dialog.

#### `type?: SkyConfirmType`

The preset button configuration for the dialog.

 SkyConfirmInstance
-------------------

Type: Class

### Properties

#### `closed: Observable<SkyConfirmCloseEventArgs>`

Fires when users select an action to close the dialog. This event returns a `SkyConfirmCloseEventArgs` object with information about the button that users select. It returns the `'cancel'` action when users press the <kbd>Escape</kbd> key.

### Methods

#### `close(args: SkyConfirmCloseEventArgs): void`

Closes the confirm instance.

#### Parameters

##### `args: SkyConfirmCloseEventArgs`

Specifies an object to emit to subscribers of the `closed` event of the confirm instance.

#### Returns

`void`

 SkyConfirmType
---------------

Type: Enumeration

    enum SkyConfirmType {
      Custom = 0,
      OK = 1,
      YesCancel = 2,
      YesNoCancel = 3,
    }

### Properties

#### `SkyConfirmType.Custom`

Allows you to define your own buttons using the `buttons` property of `SkyConfirmConfig`.

#### `SkyConfirmType.OK`

Displays one button with an **OK** label and an `'ok'` action.

#### `SkyConfirmType.YesCancel`

Warning: **Deprecated.** Use the `Custom` type to follow the guidance that labels should clearly indicate the actions that occur when users select buttons.

Displays two buttons with **Yes** and **Cancel** labels.

#### `SkyConfirmType.YesNoCancel`

Warning: **Deprecated.** Use the `Custom` type to follow the guidance that labels should clearly indicate the actions that occur when users select buttons.

Displays three buttons with **Yes**, **No**, and **Cancel** labels.

 SkyConfirmButtonConfig
-----------------------

Type: Interface

    interface SkyConfirmButtonConfig {
      action: string;
      autofocus?: boolean;
      styleType?: string;
      text: string;
    }

### Properties

#### `action: string`

The identifier to return when users select the button to close the dialog. This is useful to determine which button users select.

#### `autofocus?: boolean`

Warning: **Deprecated.** The confirm component automatically focuses the first interactive element of the dialog.

Whether to place focus on this button by default.

#### `styleType?: string`

The style to apply to the button. The valid options are `primary` for the button that triggers the recommended or most-common action, `default` for buttons that trigger less-common actions, `link` for a button that closes the dialog, and `danger` for a primary action that deletes existing data.

#### `text: string`

The label for the button.

 SkyConfirmButtonStyleType
--------------------------

Type: Type alias

    type SkyConfirmButtonStyleType = "primary" | "default" | "link" | "danger"

 SkyConfirmCloseEventArgs
-------------------------

Type: Interface

    interface SkyConfirmCloseEventArgs {
      action: string;
    }

### Properties

#### `action: string`

The identifier for the button that users selected to close the dialog.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyConfirmHarness
------------------

Type: Class

`import { SkyConfirmHarness } from '@skyux/modals/testing';`

Harness for interacting with a confirm component in tests.

### Methods

#### `clickCustomButton(filters: SkyConfirmButtonHarnessFilters): Promise<void>`

Clicks a confirm button.

#### Parameters

##### `filters: SkyConfirmButtonHarnessFilters`

#### Returns

`Promise<void>`

#### `clickOkButton(): Promise<void>`

Clicks a confirm button.

#### Returns

`Promise<void>`

#### `getBodyText(): Promise<undefined | string>`

Gets the body of the confirm component.

#### Returns

`Promise<undefined | string>`

#### `getCustomButton(filter: SkyConfirmButtonHarnessFilters): Promise<SkyConfirmButtonHarness>`

Gets a specific confirm custom button based on the filter criteria.

#### Parameters

##### `filter: SkyConfirmButtonHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyConfirmButtonHarness>`

#### `getCustomButtons(filters?: SkyConfirmButtonHarnessFilters): Promise<SkyConfirmButtonHarness[]>`

Gets an array of confirm custom buttons based on the filter criteria. If no filter is provided, returns all confirm custom buttons.

#### Parameters

##### `filters?: SkyConfirmButtonHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyConfirmButtonHarness[]>`

#### `getMessageText(): Promise<string>`

Gets the message of the confirm component.

#### Returns

`Promise<string>`

#### `getType(): Promise<SkyConfirmType>`

Gets the type of the confirm component.

#### Returns

`Promise<SkyConfirmType>`

#### `isWhiteSpacePreserved(): Promise<boolean>`

Whether the whitespace is preserved on the confirm component.

#### Returns

`Promise<boolean>`

 SkyConfirmButtonHarness
------------------------

Type: Class

`import { SkyConfirmButtonHarness } from '@skyux/modals/testing';`

Harness for interacting with a confirm component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the confirm button.

#### Returns

`Promise<void>`

#### `getStyleType(): Promise<SkyConfirmButtonStyleType>`

Gets the button style of the confirm button.

#### Returns

`Promise<SkyConfirmButtonStyleType>`

#### `getText(): Promise<string>`

Gets the text content of the confirm button.

#### Returns

`Promise<string>`

#### `SkyConfirmButtonHarness.with(filters: SkyConfirmButtonHarnessFilters): HarnessPredicate<SkyConfirmButtonHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyConfirmButtonHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyConfirmButtonHarnessFilters`

#### Returns

`HarnessPredicate<SkyConfirmButtonHarness>`

 SkyConfirmButtonHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyConfirmButtonHarness](/skyux/components/confirm?docs-active-tab=design#class_sky-confirm-button-harness.md) instances.

    interface SkyConfirmButtonHarnessFilters {
      styleType?: string;
      text?: string | RegExp;
    }

### Properties

#### `styleType?: string`

Only find instances whose style matches the given value.

#### `text?: string | RegExp`

Only find instances whose content matches the given value.

 SkyConfirmTestingModule
------------------------

Type: Module

`import { SkyConfirmTestingModule } from '@skyux/modals/testing';`

Configures the `SkyConfirmTestingController` as the backend for the `SkyConfirmService`.

 SkyConfirmTestingController
----------------------------

Type: Class

A controller to be injected into tests, which mocks the confirm service and handles interactions with confirm dialogs.

### Methods

#### `cancel(): void`

Closes the confirm dialog with the "cancel" action.

#### Returns

`void`

#### `close(args: SkyConfirmCloseEventArgs): void`

Closes the confirm dialog with the provided action.

#### Parameters

##### `args: SkyConfirmCloseEventArgs`

#### Returns

`void`

#### `expectNone(): void`

Throws if a confirm dialog is open.

#### Returns

`void`

#### `expectOpen(config: SkyConfirmConfig): void`

Throws if the open confirm dialog does not match the provided configuration.

#### Parameters

##### `config: SkyConfirmConfig`

#### Returns

`void`

#### `ok(): void`

Closes the confirm dialog with the "ok" action.

#### Returns

`void`

# Development

                  Skip to Main Content

 Confirm
=======

The confirm service launches simple confirmation dialogs that prompt users to confirm actions.

 Usage
------

### Use when

Use confirmation dialogs to focus user attention when actions are destructive or could be costly if performed by mistake. Prompt users to confirm an action with a single question and provide terminal actions to answer the question.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/confirm/confirm-usage-1.90c28a0beb69af121ab75415471ff5a5.png)

Do use confirmation dialogs to inform users of consequences and to prompt them to confirm potentially costly actions.

Use confirmation dialogs with a lone terminal action when users need to acknowledge important information but don't need to make a decision, such as when they need to know why they can't perform an action.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/confirm/confirm-usage-2.4323041c0e5da75f7edb16c7c82c4414.png)

Do use confirmation dialogs to prompt users to ackowledge important information.

### Don't use when

Don't use confirmation dialogs when user responses require input fields.

Don't use confirmation dialogs when the context requires significant explanation, illustration, or dynamic feedback from downstream consequences.

 Anatomy
--------

1

Modal

2

Heading

3

Actions

4

Body text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/confirm/confirm-anatomy.a52cf24c55ed8c0fe3343b0edac98e69.png)

 Options
--------

### Actions

Include up to three terminal actions to answer the question in the heading. And for confirmation dialogs that present important information without requiring a decision, include a lone action that acknowledges the information.

*   A primary button triggers the recommended or most-common action.
*   A secondary button triggers a less-common action.
*   A link button cancels the action.
*   Each button closes the dialog.

#### Primary actions that delete existing data

When a confirmation dialog's primary action deletes existing data, such as records or settings, use the `sky-btn-danger` style for a red background. Don't use this style for any other buttons, including actions that delete unsaved data and secondary actions that delete existing data.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/confirm/confirm-content-1.680e21b3d5d3c14ffc942e0f734cd449.png)

Do use the red danger style when primary buttons delete existing content.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/confirm/confirm-content-2-.8761f622658c4d9f731d0fd1eeca1983.png)

Don't use the red danger style when actions require confirmation but don't delete existing data.

### Body text

Use body text to provide context and describe potential consequences.

 Content
--------

### Heading

Limit the confirmation dialog's heading to a single sentence. In most cases, the heading poses a question that users answer when they select an action.

*   Be concise and direct. Don't use confirmation dialogs when the context requires significant explanation, illustration, or dynamic feedback from downstream consequences.
*   Avoid verbose or complicated phrasing. For example, only start questions with "Are you sure you want to" when the results of an action might be unexpected and it's important for users to think twice before they proceed. When a confirmation dialog appears after users select a delete button, a question such as "Delete this account?" is sufficient because the action is usually intentional. However, when deleting data is likely an unintended consequence of another action, such as closing a modal with unsaved data, the extra verbiage of "Are you sure you want to delete this account?" can prompt users to think twice before they confirm.

### Body text

If a confirmation message requires additional context or an explanation of potential consequences, include body text. Body text can be more than one sentence. It can help users answer the question in the heading and explain what will happen if they proceed.

### Actions

Use labels that clearly indicate what happens when users select buttons. For example, if a confirmation dialog asks users to confirm that they want to delete something, use "Delete" for the primary button.

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/modals`[View in NPM](https://www.npmjs.com/package/@skyux/modals) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/modals/src/lib/modules/confirm/confirm.service.ts#L17) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/modals`Copy None found.

 SkyConfirmService
------------------

Type: Service

Launches a dialog.

### Methods

#### `open(config: SkyConfirmConfig): SkyConfirmInstance`

Opens a dialog using the specified options.

#### Parameters

##### `config: SkyConfirmConfig`

Specifies configuration options for the dialog.

#### Returns

`SkyConfirmInstance`

 SkyConfirmConfig
-----------------

Type: Interface

    interface SkyConfirmConfig {
      body?: string;
      buttons?: SkyConfirmButtonConfig[];
      message: string;
      preserveWhiteSpace?: boolean;
      type?: SkyConfirmType;
    }

### Properties

#### `body?: string`

Secondary text to display under the primary message.

#### `buttons?: SkyConfirmButtonConfig[]`

The list of buttons to display when the `type` property is set to `SkyConfirmType.Custom`.

#### `message: string`

The message to display in bold at the top of the dialog.

#### `preserveWhiteSpace?: boolean`

Whether to preserve whitespace and new lines inside the dialog.

#### `type?: SkyConfirmType`

The preset button configuration for the dialog.

 SkyConfirmInstance
-------------------

Type: Class

### Properties

#### `closed: Observable<SkyConfirmCloseEventArgs>`

Fires when users select an action to close the dialog. This event returns a `SkyConfirmCloseEventArgs` object with information about the button that users select. It returns the `'cancel'` action when users press the <kbd>Escape</kbd> key.

### Methods

#### `close(args: SkyConfirmCloseEventArgs): void`

Closes the confirm instance.

#### Parameters

##### `args: SkyConfirmCloseEventArgs`

Specifies an object to emit to subscribers of the `closed` event of the confirm instance.

#### Returns

`void`

 SkyConfirmType
---------------

Type: Enumeration

    enum SkyConfirmType {
      Custom = 0,
      OK = 1,
      YesCancel = 2,
      YesNoCancel = 3,
    }

### Properties

#### `SkyConfirmType.Custom`

Allows you to define your own buttons using the `buttons` property of `SkyConfirmConfig`.

#### `SkyConfirmType.OK`

Displays one button with an **OK** label and an `'ok'` action.

#### `SkyConfirmType.YesCancel`

Warning: **Deprecated.** Use the `Custom` type to follow the guidance that labels should clearly indicate the actions that occur when users select buttons.

Displays two buttons with **Yes** and **Cancel** labels.

#### `SkyConfirmType.YesNoCancel`

Warning: **Deprecated.** Use the `Custom` type to follow the guidance that labels should clearly indicate the actions that occur when users select buttons.

Displays three buttons with **Yes**, **No**, and **Cancel** labels.

 SkyConfirmButtonConfig
-----------------------

Type: Interface

    interface SkyConfirmButtonConfig {
      action: string;
      autofocus?: boolean;
      styleType?: string;
      text: string;
    }

### Properties

#### `action: string`

The identifier to return when users select the button to close the dialog. This is useful to determine which button users select.

#### `autofocus?: boolean`

Warning: **Deprecated.** The confirm component automatically focuses the first interactive element of the dialog.

Whether to place focus on this button by default.

#### `styleType?: string`

The style to apply to the button. The valid options are `primary` for the button that triggers the recommended or most-common action, `default` for buttons that trigger less-common actions, `link` for a button that closes the dialog, and `danger` for a primary action that deletes existing data.

#### `text: string`

The label for the button.

 SkyConfirmButtonStyleType
--------------------------

Type: Type alias

    type SkyConfirmButtonStyleType = "primary" | "default" | "link" | "danger"

 SkyConfirmCloseEventArgs
-------------------------

Type: Interface

    interface SkyConfirmCloseEventArgs {
      action: string;
    }

### Properties

#### `action: string`

The identifier for the button that users selected to close the dialog.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyConfirmHarness
------------------

Type: Class

`import { SkyConfirmHarness } from '@skyux/modals/testing';`

Harness for interacting with a confirm component in tests.

### Methods

#### `clickCustomButton(filters: SkyConfirmButtonHarnessFilters): Promise<void>`

Clicks a confirm button.

#### Parameters

##### `filters: SkyConfirmButtonHarnessFilters`

#### Returns

`Promise<void>`

#### `clickOkButton(): Promise<void>`

Clicks a confirm button.

#### Returns

`Promise<void>`

#### `getBodyText(): Promise<undefined | string>`

Gets the body of the confirm component.

#### Returns

`Promise<undefined | string>`

#### `getCustomButton(filter: SkyConfirmButtonHarnessFilters): Promise<SkyConfirmButtonHarness>`

Gets a specific confirm custom button based on the filter criteria.

#### Parameters

##### `filter: SkyConfirmButtonHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyConfirmButtonHarness>`

#### `getCustomButtons(filters?: SkyConfirmButtonHarnessFilters): Promise<SkyConfirmButtonHarness[]>`

Gets an array of confirm custom buttons based on the filter criteria. If no filter is provided, returns all confirm custom buttons.

#### Parameters

##### `filters?: SkyConfirmButtonHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyConfirmButtonHarness[]>`

#### `getMessageText(): Promise<string>`

Gets the message of the confirm component.

#### Returns

`Promise<string>`

#### `getType(): Promise<SkyConfirmType>`

Gets the type of the confirm component.

#### Returns

`Promise<SkyConfirmType>`

#### `isWhiteSpacePreserved(): Promise<boolean>`

Whether the whitespace is preserved on the confirm component.

#### Returns

`Promise<boolean>`

 SkyConfirmButtonHarness
------------------------

Type: Class

`import { SkyConfirmButtonHarness } from '@skyux/modals/testing';`

Harness for interacting with a confirm component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the confirm button.

#### Returns

`Promise<void>`

#### `getStyleType(): Promise<SkyConfirmButtonStyleType>`

Gets the button style of the confirm button.

#### Returns

`Promise<SkyConfirmButtonStyleType>`

#### `getText(): Promise<string>`

Gets the text content of the confirm button.

#### Returns

`Promise<string>`

#### `SkyConfirmButtonHarness.with(filters: SkyConfirmButtonHarnessFilters): HarnessPredicate<SkyConfirmButtonHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyConfirmButtonHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyConfirmButtonHarnessFilters`

#### Returns

`HarnessPredicate<SkyConfirmButtonHarness>`

 SkyConfirmButtonHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyConfirmButtonHarness](/skyux/components/confirm?docs-active-tab=development#class_sky-confirm-button-harness.md) instances.

    interface SkyConfirmButtonHarnessFilters {
      styleType?: string;
      text?: string | RegExp;
    }

### Properties

#### `styleType?: string`

Only find instances whose style matches the given value.

#### `text?: string | RegExp`

Only find instances whose content matches the given value.

 SkyConfirmTestingModule
------------------------

Type: Module

`import { SkyConfirmTestingModule } from '@skyux/modals/testing';`

Configures the `SkyConfirmTestingController` as the backend for the `SkyConfirmService`.

 SkyConfirmTestingController
----------------------------

Type: Class

A controller to be injected into tests, which mocks the confirm service and handles interactions with confirm dialogs.

### Methods

#### `cancel(): void`

Closes the confirm dialog with the "cancel" action.

#### Returns

`void`

#### `close(args: SkyConfirmCloseEventArgs): void`

Closes the confirm dialog with the provided action.

#### Parameters

##### `args: SkyConfirmCloseEventArgs`

#### Returns

`void`

#### `expectNone(): void`

Throws if a confirm dialog is open.

#### Returns

`void`

#### `expectOpen(config: SkyConfirmConfig): void`

Throws if the open confirm dialog does not match the provided configuration.

#### Parameters

##### `config: SkyConfirmConfig`

#### Returns

`void`

#### `ok(): void`

Closes the confirm dialog with the "ok" action.

#### Returns

`void`

# Examples

                    Skip to Main Content

 Confirm
=======

The confirm service launches simple confirmation dialogs that prompt users to confirm actions.Usage
------

### Use when

Use confirmation dialogs to focus user attention when actions are destructive or could be costly if performed by mistake. Prompt users to confirm an action with a single question and provide terminal actions to answer the question.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/confirm/confirm-usage-1.90c28a0beb69af121ab75415471ff5a5.png)

Do use confirmation dialogs to inform users of consequences and to prompt them to confirm potentially costly actions.

Use confirmation dialogs with a lone terminal action when users need to acknowledge important information but don't need to make a decision, such as when they need to know why they can't perform an action.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/confirm/confirm-usage-2.4323041c0e5da75f7edb16c7c82c4414.png)

Do use confirmation dialogs to prompt users to ackowledge important information.

### Don't use when

Don't use confirmation dialogs when user responses require input fields.

Don't use confirmation dialogs when the context requires significant explanation, illustration, or dynamic feedback from downstream consequences.

 Anatomy
--------

1

Modal

2

Heading

3

Actions

4

Body text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/confirm/confirm-anatomy.a52cf24c55ed8c0fe3343b0edac98e69.png)

 Options
--------

### Actions

Include up to three terminal actions to answer the question in the heading. And for confirmation dialogs that present important information without requiring a decision, include a lone action that acknowledges the information.

*   A primary button triggers the recommended or most-common action.
*   A secondary button triggers a less-common action.
*   A link button cancels the action.
*   Each button closes the dialog.

#### Primary actions that delete existing data

When a confirmation dialog's primary action deletes existing data, such as records or settings, use the `sky-btn-danger` style for a red background. Don't use this style for any other buttons, including actions that delete unsaved data and secondary actions that delete existing data.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/confirm/confirm-content-1.680e21b3d5d3c14ffc942e0f734cd449.png)

Do use the red danger style when primary buttons delete existing content.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/confirm/confirm-content-2-.8761f622658c4d9f731d0fd1eeca1983.png)

Don't use the red danger style when actions require confirmation but don't delete existing data.

### Body text

Use body text to provide context and describe potential consequences.

 Content
--------

### Heading

Limit the confirmation dialog's heading to a single sentence. In most cases, the heading poses a question that users answer when they select an action.

*   Be concise and direct. Don't use confirmation dialogs when the context requires significant explanation, illustration, or dynamic feedback from downstream consequences.
*   Avoid verbose or complicated phrasing. For example, only start questions with "Are you sure you want to" when the results of an action might be unexpected and it's important for users to think twice before they proceed. When a confirmation dialog appears after users select a delete button, a question such as "Delete this account?" is sufficient because the action is usually intentional. However, when deleting data is likely an unintended consequence of another action, such as closing a modal with unsaved data, the extra verbiage of "Are you sure you want to delete this account?" can prompt users to think twice before they confirm.

### Body text

If a confirmation message requires additional context or an explanation of potential consequences, include body text. Body text can be more than one sentence. It can help users answer the question in the heading and explain what will happen if they proceed.

### Actions

Use labels that clearly indicate what happens when users select buttons. For example, if a confirmation dialog asks users to confirm that they want to delete something, use "Delete" for the primary button.

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/modals`[View in NPM](https://www.npmjs.com/package/@skyux/modals) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/modals/src/lib/modules/confirm/confirm.service.ts#L17) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/modals`Copy None found.

 SkyConfirmService
------------------

Type: Service

Launches a dialog.

### Methods

#### `open(config: SkyConfirmConfig): SkyConfirmInstance`

Opens a dialog using the specified options.

#### Parameters

##### `config: SkyConfirmConfig`

Specifies configuration options for the dialog.

#### Returns

`SkyConfirmInstance`

 SkyConfirmConfig
-----------------

Type: Interface

    interface SkyConfirmConfig {
      body?: string;
      buttons?: SkyConfirmButtonConfig[];
      message: string;
      preserveWhiteSpace?: boolean;
      type?: SkyConfirmType;
    }

### Properties

#### `body?: string`

Secondary text to display under the primary message.

#### `buttons?: SkyConfirmButtonConfig[]`

The list of buttons to display when the `type` property is set to `SkyConfirmType.Custom`.

#### `message: string`

The message to display in bold at the top of the dialog.

#### `preserveWhiteSpace?: boolean`

Whether to preserve whitespace and new lines inside the dialog.

#### `type?: SkyConfirmType`

The preset button configuration for the dialog.

 SkyConfirmInstance
-------------------

Type: Class

### Properties

#### `closed: Observable<SkyConfirmCloseEventArgs>`

Fires when users select an action to close the dialog. This event returns a `SkyConfirmCloseEventArgs` object with information about the button that users select. It returns the `'cancel'` action when users press the <kbd>Escape</kbd> key.

### Methods

#### `close(args: SkyConfirmCloseEventArgs): void`

Closes the confirm instance.

#### Parameters

##### `args: SkyConfirmCloseEventArgs`

Specifies an object to emit to subscribers of the `closed` event of the confirm instance.

#### Returns

`void`

 SkyConfirmType
---------------

Type: Enumeration

    enum SkyConfirmType {
      Custom = 0,
      OK = 1,
      YesCancel = 2,
      YesNoCancel = 3,
    }

### Properties

#### `SkyConfirmType.Custom`

Allows you to define your own buttons using the `buttons` property of `SkyConfirmConfig`.

#### `SkyConfirmType.OK`

Displays one button with an **OK** label and an `'ok'` action.

#### `SkyConfirmType.YesCancel`

Warning: **Deprecated.** Use the `Custom` type to follow the guidance that labels should clearly indicate the actions that occur when users select buttons.

Displays two buttons with **Yes** and **Cancel** labels.

#### `SkyConfirmType.YesNoCancel`

Warning: **Deprecated.** Use the `Custom` type to follow the guidance that labels should clearly indicate the actions that occur when users select buttons.

Displays three buttons with **Yes**, **No**, and **Cancel** labels.

 SkyConfirmButtonConfig
-----------------------

Type: Interface

    interface SkyConfirmButtonConfig {
      action: string;
      autofocus?: boolean;
      styleType?: string;
      text: string;
    }

### Properties

#### `action: string`

The identifier to return when users select the button to close the dialog. This is useful to determine which button users select.

#### `autofocus?: boolean`

Warning: **Deprecated.** The confirm component automatically focuses the first interactive element of the dialog.

Whether to place focus on this button by default.

#### `styleType?: string`

The style to apply to the button. The valid options are `primary` for the button that triggers the recommended or most-common action, `default` for buttons that trigger less-common actions, `link` for a button that closes the dialog, and `danger` for a primary action that deletes existing data.

#### `text: string`

The label for the button.

 SkyConfirmButtonStyleType
--------------------------

Type: Type alias

    type SkyConfirmButtonStyleType = "primary" | "default" | "link" | "danger"

 SkyConfirmCloseEventArgs
-------------------------

Type: Interface

    interface SkyConfirmCloseEventArgs {
      action: string;
    }

### Properties

#### `action: string`

The identifier for the button that users selected to close the dialog.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyConfirmHarness
------------------

Type: Class

`import { SkyConfirmHarness } from '@skyux/modals/testing';`

Harness for interacting with a confirm component in tests.

### Methods

#### `clickCustomButton(filters: SkyConfirmButtonHarnessFilters): Promise<void>`

Clicks a confirm button.

#### Parameters

##### `filters: SkyConfirmButtonHarnessFilters`

#### Returns

`Promise<void>`

#### `clickOkButton(): Promise<void>`

Clicks a confirm button.

#### Returns

`Promise<void>`

#### `getBodyText(): Promise<undefined | string>`

Gets the body of the confirm component.

#### Returns

`Promise<undefined | string>`

#### `getCustomButton(filter: SkyConfirmButtonHarnessFilters): Promise<SkyConfirmButtonHarness>`

Gets a specific confirm custom button based on the filter criteria.

#### Parameters

##### `filter: SkyConfirmButtonHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyConfirmButtonHarness>`

#### `getCustomButtons(filters?: SkyConfirmButtonHarnessFilters): Promise<SkyConfirmButtonHarness[]>`

Gets an array of confirm custom buttons based on the filter criteria. If no filter is provided, returns all confirm custom buttons.

#### Parameters

##### `filters?: SkyConfirmButtonHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyConfirmButtonHarness[]>`

#### `getMessageText(): Promise<string>`

Gets the message of the confirm component.

#### Returns

`Promise<string>`

#### `getType(): Promise<SkyConfirmType>`

Gets the type of the confirm component.

#### Returns

`Promise<SkyConfirmType>`

#### `isWhiteSpacePreserved(): Promise<boolean>`

Whether the whitespace is preserved on the confirm component.

#### Returns

`Promise<boolean>`

 SkyConfirmButtonHarness
------------------------

Type: Class

`import { SkyConfirmButtonHarness } from '@skyux/modals/testing';`

Harness for interacting with a confirm component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the confirm button.

#### Returns

`Promise<void>`

#### `getStyleType(): Promise<SkyConfirmButtonStyleType>`

Gets the button style of the confirm button.

#### Returns

`Promise<SkyConfirmButtonStyleType>`

#### `getText(): Promise<string>`

Gets the text content of the confirm button.

#### Returns

`Promise<string>`

#### `SkyConfirmButtonHarness.with(filters: SkyConfirmButtonHarnessFilters): HarnessPredicate<SkyConfirmButtonHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyConfirmButtonHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyConfirmButtonHarnessFilters`

#### Returns

`HarnessPredicate<SkyConfirmButtonHarness>`

 SkyConfirmButtonHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyConfirmButtonHarness](/skyux/components/confirm?docs-active-tab=examples#class_sky-confirm-button-harness.md) instances.

    interface SkyConfirmButtonHarnessFilters {
      styleType?: string;
      text?: string | RegExp;
    }

### Properties

#### `styleType?: string`

Only find instances whose style matches the given value.

#### `text?: string | RegExp`

Only find instances whose content matches the given value.

 SkyConfirmTestingModule
------------------------

Type: Module

`import { SkyConfirmTestingModule } from '@skyux/modals/testing';`

Configures the `SkyConfirmTestingController` as the backend for the `SkyConfirmService`.

 SkyConfirmTestingController
----------------------------

Type: Class

A controller to be injected into tests, which mocks the confirm service and handles interactions with confirm dialogs.

### Methods

#### `cancel(): void`

Closes the confirm dialog with the "cancel" action.

#### Returns

`void`

#### `close(args: SkyConfirmCloseEventArgs): void`

Closes the confirm dialog with the provided action.

#### Parameters

##### `args: SkyConfirmCloseEventArgs`

#### Returns

`void`

#### `expectNone(): void`

Throws if a confirm dialog is open.

#### Returns

`void`

#### `expectOpen(config: SkyConfirmConfig): void`

Throws if the open confirm dialog does not match the provided configuration.

#### Parameters

##### `config: SkyConfirmConfig`

#### Returns

`void`

#### `ok(): void`

Closes the confirm dialog with the "ok" action.

#### Returns

`void`

### Confirm, tested with controller

Edit in StackBlitz

Open confirm

Show code

Copy

    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import {
      SkyConfirmTestingController,
      SkyConfirmTestingModule,
    } from '@skyux/modals/testing';
    
    import { ModalsConfirmBasicWithControllerExampleComponent } from './example.component';
    
    describe('Testing with SkyConfirmTestingController', () => {
      function setupTest(): {
        confirmController: SkyConfirmTestingController;
        fixture: ComponentFixture<ModalsConfirmBasicWithControllerExampleComponent>;
      } {
        const confirmController = TestBed.inject(SkyConfirmTestingController);
        const fixture = TestBed.createComponent(
          ModalsConfirmBasicWithControllerExampleComponent,
        );
    
        return { confirmController, fixture };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [
            SkyConfirmTestingModule,
            ModalsConfirmBasicWithControllerExampleComponent,
          ],
        });
      });
    
      it('should click "OK" on a confirmation dialog', () => {
        const { confirmController, fixture } = setupTest();
    
        fixture.componentInstance.launchConfirm();
        fixture.detectChanges();
    
        confirmController.expectOpen({
          message: 'Are you sure?',
        });
    
        confirmController.ok();
        confirmController.expectNone();
    
        expect(fixture.componentInstance.selectedAction).toEqual('ok');
      });
    
      it('should cancel the confirmation dialog', () => {
        const { confirmController, fixture } = setupTest();
    
        fixture.componentInstance.launchConfirm();
        fixture.detectChanges();
    
        confirmController.expectOpen({
          message: 'Are you sure?',
        });
    
        confirmController.cancel();
        confirmController.expectNone();
    
        expect(fixture.componentInstance.selectedAction).toEqual('cancel');
      });
    });

Copy

    import { Component, inject } from '@angular/core';
    import { SkyConfirmService } from '@skyux/modals';
    
    /**
     * @title Confirm, tested with controller
     */
    @Component({
      selector: 'app-modals-confirm-basic-with-controller-example',
      standalone: true,
      template: `<button
        aria-haspopup="dialog"
        class="sky-btn sky-btn-default"
        type="button"
        (click)="launchConfirm()"
      >
        Open confirm
      </button>`,
    })
    export class ModalsConfirmBasicWithControllerExampleComponent {
      public selectedAction: string | undefined;
    
      readonly #confirmSvc = inject(SkyConfirmService);
    
      public launchConfirm(): void {
        const dialog = this.#confirmSvc.open({
          message: 'Are you sure?',
        });
    
        dialog.closed.subscribe((args) => {
          this.selectedAction = args.action;
        });
      }
    }
### Confirm, tested with harness

Edit in StackBlitz

OK confirm Confirm with two actions Confirm with three actions Confirm with delete button

Show code

Copy

    <button
      aria-haspopup="dialog"
      class="sky-btn sky-btn-default sky-margin-inline-sm ok-confirm-btn"
      type="button"
      (click)="openOKConfirm()"
    >
      OK confirm
    </button>
    
    <button
      aria-haspopup="dialog"
      class="sky-btn sky-btn-default sky-margin-inline-sm two-action-confirm-btn"
      type="button"
      (click)="openTwoActionConfirm()"
    >
      Confirm with two actions
    </button>
    
    <button
      aria-haspopup="dialog"
      class="sky-btn sky-btn-default sky-margin-inline-sm"
      type="button"
      (click)="openThreeActionConfirm()"
    >
      Confirm with three actions
    </button>
    
    <button
      aria-haspopup="dialog"
      class="sky-btn sky-btn-default sky-margin-inline-sm"
      type="button"
      (click)="openDeleteConfirm()"
    >
      Confirm with delete button
    </button>
    
    @if (selectedAction) {
      @if (selectedText) {
        <p class="displayed-text">
          You selected the "{{ selectedText }}" button, which has an action of "{{
            selectedAction
          }}."
        </p>
      } @else {
        <p class="displayed-text">
          You selected the "{{ selectedAction }}" action.
        </p>
      }
    }
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { SkyConfirmHarness } from '@skyux/modals/testing';
    
    import { ModalsConfirmBasicWithHarnessExampleComponent } from './example.component';
    
    describe('Testing with SkyConfirmHarness', () => {
      async function setupTest(confirmBtnClass: string): Promise<{
        confirmHarness: SkyConfirmHarness;
        fixture: ComponentFixture<ModalsConfirmBasicWithHarnessExampleComponent>;
      }> {
        const fixture = TestBed.createComponent(
          ModalsConfirmBasicWithHarnessExampleComponent,
        );
        const el = fixture.nativeElement as HTMLElement;
        const openBtn = el.querySelector<HTMLButtonElement>(confirmBtnClass);
    
        openBtn?.click();
    
        const rootLoader = TestbedHarnessEnvironment.documentRootLoader(fixture);
        const confirmHarness = await rootLoader.getHarness(SkyConfirmHarness);
    
        return { confirmHarness, fixture };
      }
    
      function expectDisplayedText(
        fixture: ComponentFixture<ModalsConfirmBasicWithHarnessExampleComponent>,
        expectedText: string,
      ): void {
        expect(
          (fixture.nativeElement as HTMLElement).querySelector<HTMLElement>(
            '.displayed-text',
          )?.innerText,
        ).toEqual(expectedText);
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [ModalsConfirmBasicWithHarnessExampleComponent],
        });
      });
    
      it('should show the correct text when OK is clicked on an OK confirm', async () => {
        const { confirmHarness, fixture } = await setupTest('.ok-confirm-btn');
    
        await confirmHarness.clickOkButton();
    
        expectDisplayedText(fixture, 'You selected the "ok" action.');
    
        await expectAsync(confirmHarness.getMessageText()).toBeResolvedTo(
          'Cannot delete invoice because it has vendor, credit memo, or purchase order activity.',
        );
      });
    
      it('should show the correct text when "Finalize" is clicked on a custom confirm', async () => {
        const { confirmHarness, fixture } = await setupTest(
          '.two-action-confirm-btn',
        );
    
        await confirmHarness.clickCustomButton({ text: 'Finalize' });
    
        expectDisplayedText(
          fixture,
          'You selected the "Finalize" button, which has an action of "save."',
        );
    
        await expectAsync(confirmHarness.getMessageText()).toBeResolvedTo(
          'Finalize report cards?',
        );
    
        await expectAsync(confirmHarness.getBodyText()).toBeResolvedTo(
          'Grades cannot be changed once the report cards are finalized.',
        );
      });
    });

Copy

    import { Component, inject } from '@angular/core';
    import {
      SkyConfirmButtonConfig,
      SkyConfirmInstance,
      SkyConfirmService,
      SkyConfirmType,
    } from '@skyux/modals';
    
    /**
     * @title Confirm, tested with harness
     */
    @Component({
      selector: 'app-modals-confirm-basic-with-harness-example',
      standalone: true,
      templateUrl: './example.component.html',
    })
    export class ModalsConfirmBasicWithHarnessExampleComponent {
      protected selectedAction: string | undefined;
      protected selectedText: string | undefined;
    
      readonly #confirmSvc = inject(SkyConfirmService);
    
      protected openOKConfirm(): void {
        const dialog: SkyConfirmInstance = this.#confirmSvc.open({
          message:
            'Cannot delete invoice because it has vendor, credit memo, or purchase order activity.',
        });
    
        dialog.closed.subscribe((result) => {
          this.selectedText = undefined;
          this.selectedAction = result.action;
        });
      }
    
      protected openTwoActionConfirm(): void {
        const buttons: SkyConfirmButtonConfig[] = [
          { text: 'Finalize', action: 'save', styleType: 'primary' },
          { text: 'Cancel', action: 'cancel', styleType: 'link' },
        ];
    
        const dialog: SkyConfirmInstance = this.#confirmSvc.open({
          message: 'Finalize report cards?',
          body: 'Grades cannot be changed once the report cards are finalized.',
          type: SkyConfirmType.Custom,
          buttons,
        });
    
        dialog.closed.subscribe((result) => {
          this.selectedAction = result.action;
    
          for (const button of buttons) {
            if (button.action === result.action) {
              this.selectedText = button.text;
              break;
            }
          }
        });
      }
    
      protected openThreeActionConfirm(): void {
        const buttons: SkyConfirmButtonConfig[] = [
          { text: 'Save', action: 'save', styleType: 'primary' },
          { text: 'Delete', action: 'delete' },
          { text: 'Keep working', action: 'cancel', styleType: 'link' },
        ];
    
        const dialog = this.#confirmSvc.open({
          message: 'Save your changes before leaving?',
          type: SkyConfirmType.Custom,
          buttons,
        });
    
        dialog.closed.subscribe((result) => {
          this.selectedAction = result.action;
    
          for (const button of buttons) {
            if (button.action === result.action) {
              this.selectedText = button.text;
              break;
            }
          }
        });
      }
    
      protected openDeleteConfirm(): void {
        const buttons: SkyConfirmButtonConfig[] = [
          { text: 'Delete', action: 'delete', styleType: 'danger' },
          { text: 'Cancel', action: 'cancel', styleType: 'link' },
        ];
    
        const dialog = this.#confirmSvc.open({
          message: 'Delete this account?',
          body: 'Deleting this account may affect processes that are currently running.',
          type: SkyConfirmType.Custom,
          buttons,
        });
    
        dialog.closed.subscribe((result) => {
          this.selectedAction = result.action;
    
          for (const button of buttons) {
            if (button.action === result.action) {
              this.selectedText = button.text;
              break;
            }
          }
        });
      }
    }

# Testing

                  Skip to Main Content

 Confirm
=======

The confirm service launches simple confirmation dialogs that prompt users to confirm actions.

 Usage
------

### Use when

Use confirmation dialogs to focus user attention when actions are destructive or could be costly if performed by mistake. Prompt users to confirm an action with a single question and provide terminal actions to answer the question.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/confirm/confirm-usage-1.90c28a0beb69af121ab75415471ff5a5.png)

Do use confirmation dialogs to inform users of consequences and to prompt them to confirm potentially costly actions.

Use confirmation dialogs with a lone terminal action when users need to acknowledge important information but don't need to make a decision, such as when they need to know why they can't perform an action.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/confirm/confirm-usage-2.4323041c0e5da75f7edb16c7c82c4414.png)

Do use confirmation dialogs to prompt users to ackowledge important information.

### Don't use when

Don't use confirmation dialogs when user responses require input fields.

Don't use confirmation dialogs when the context requires significant explanation, illustration, or dynamic feedback from downstream consequences.

 Anatomy
--------

1

Modal

2

Heading

3

Actions

4

Body text (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/confirm/confirm-anatomy.a52cf24c55ed8c0fe3343b0edac98e69.png)

 Options
--------

### Actions

Include up to three terminal actions to answer the question in the heading. And for confirmation dialogs that present important information without requiring a decision, include a lone action that acknowledges the information.

*   A primary button triggers the recommended or most-common action.
*   A secondary button triggers a less-common action.
*   A link button cancels the action.
*   Each button closes the dialog.

#### Primary actions that delete existing data

When a confirmation dialog's primary action deletes existing data, such as records or settings, use the `sky-btn-danger` style for a red background. Don't use this style for any other buttons, including actions that delete unsaved data and secondary actions that delete existing data.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/confirm/confirm-content-1.680e21b3d5d3c14ffc942e0f734cd449.png)

Do use the red danger style when primary buttons delete existing content.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/confirm/confirm-content-2-.8761f622658c4d9f731d0fd1eeca1983.png)

Don't use the red danger style when actions require confirmation but don't delete existing data.

### Body text

Use body text to provide context and describe potential consequences.

 Content
--------

### Heading

Limit the confirmation dialog's heading to a single sentence. In most cases, the heading poses a question that users answer when they select an action.

*   Be concise and direct. Don't use confirmation dialogs when the context requires significant explanation, illustration, or dynamic feedback from downstream consequences.
*   Avoid verbose or complicated phrasing. For example, only start questions with "Are you sure you want to" when the results of an action might be unexpected and it's important for users to think twice before they proceed. When a confirmation dialog appears after users select a delete button, a question such as "Delete this account?" is sufficient because the action is usually intentional. However, when deleting data is likely an unintended consequence of another action, such as closing a modal with unsaved data, the extra verbiage of "Are you sure you want to delete this account?" can prompt users to think twice before they confirm.

### Body text

If a confirmation message requires additional context or an explanation of potential consequences, include body text. Body text can be more than one sentence. It can help users answer the question in the heading and explain what will happen if they proceed.

### Actions

Use labels that clearly indicate what happens when users select buttons. For example, if a confirmation dialog asks users to confirm that they want to delete something, use "Delete" for the primary button.

 Related information
--------------------

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/modals`[View in NPM](https://www.npmjs.com/package/@skyux/modals) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/modals/src/lib/modules/confirm/confirm.service.ts#L17) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/modals`Copy None found.

 SkyConfirmService
------------------

Type: Service

Launches a dialog.

### Methods

#### `open(config: SkyConfirmConfig): SkyConfirmInstance`

Opens a dialog using the specified options.

#### Parameters

##### `config: SkyConfirmConfig`

Specifies configuration options for the dialog.

#### Returns

`SkyConfirmInstance`

 SkyConfirmConfig
-----------------

Type: Interface

    interface SkyConfirmConfig {
      body?: string;
      buttons?: SkyConfirmButtonConfig[];
      message: string;
      preserveWhiteSpace?: boolean;
      type?: SkyConfirmType;
    }

### Properties

#### `body?: string`

Secondary text to display under the primary message.

#### `buttons?: SkyConfirmButtonConfig[]`

The list of buttons to display when the `type` property is set to `SkyConfirmType.Custom`.

#### `message: string`

The message to display in bold at the top of the dialog.

#### `preserveWhiteSpace?: boolean`

Whether to preserve whitespace and new lines inside the dialog.

#### `type?: SkyConfirmType`

The preset button configuration for the dialog.

 SkyConfirmInstance
-------------------

Type: Class

### Properties

#### `closed: Observable<SkyConfirmCloseEventArgs>`

Fires when users select an action to close the dialog. This event returns a `SkyConfirmCloseEventArgs` object with information about the button that users select. It returns the `'cancel'` action when users press the <kbd>Escape</kbd> key.

### Methods

#### `close(args: SkyConfirmCloseEventArgs): void`

Closes the confirm instance.

#### Parameters

##### `args: SkyConfirmCloseEventArgs`

Specifies an object to emit to subscribers of the `closed` event of the confirm instance.

#### Returns

`void`

 SkyConfirmType
---------------

Type: Enumeration

    enum SkyConfirmType {
      Custom = 0,
      OK = 1,
      YesCancel = 2,
      YesNoCancel = 3,
    }

### Properties

#### `SkyConfirmType.Custom`

Allows you to define your own buttons using the `buttons` property of `SkyConfirmConfig`.

#### `SkyConfirmType.OK`

Displays one button with an **OK** label and an `'ok'` action.

#### `SkyConfirmType.YesCancel`

Warning: **Deprecated.** Use the `Custom` type to follow the guidance that labels should clearly indicate the actions that occur when users select buttons.

Displays two buttons with **Yes** and **Cancel** labels.

#### `SkyConfirmType.YesNoCancel`

Warning: **Deprecated.** Use the `Custom` type to follow the guidance that labels should clearly indicate the actions that occur when users select buttons.

Displays three buttons with **Yes**, **No**, and **Cancel** labels.

 SkyConfirmButtonConfig
-----------------------

Type: Interface

    interface SkyConfirmButtonConfig {
      action: string;
      autofocus?: boolean;
      styleType?: string;
      text: string;
    }

### Properties

#### `action: string`

The identifier to return when users select the button to close the dialog. This is useful to determine which button users select.

#### `autofocus?: boolean`

Warning: **Deprecated.** The confirm component automatically focuses the first interactive element of the dialog.

Whether to place focus on this button by default.

#### `styleType?: string`

The style to apply to the button. The valid options are `primary` for the button that triggers the recommended or most-common action, `default` for buttons that trigger less-common actions, `link` for a button that closes the dialog, and `danger` for a primary action that deletes existing data.

#### `text: string`

The label for the button.

 SkyConfirmButtonStyleType
--------------------------

Type: Type alias

    type SkyConfirmButtonStyleType = "primary" | "default" | "link" | "danger"

 SkyConfirmCloseEventArgs
-------------------------

Type: Interface

    interface SkyConfirmCloseEventArgs {
      action: string;
    }

### Properties

#### `action: string`

The identifier for the button that users selected to close the dialog.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyConfirmHarness
------------------

Type: Class

`import { SkyConfirmHarness } from '@skyux/modals/testing';`

Harness for interacting with a confirm component in tests.

### Methods

#### `clickCustomButton(filters: SkyConfirmButtonHarnessFilters): Promise<void>`

Clicks a confirm button.

#### Parameters

##### `filters: SkyConfirmButtonHarnessFilters`

#### Returns

`Promise<void>`

#### `clickOkButton(): Promise<void>`

Clicks a confirm button.

#### Returns

`Promise<void>`

#### `getBodyText(): Promise<undefined | string>`

Gets the body of the confirm component.

#### Returns

`Promise<undefined | string>`

#### `getCustomButton(filter: SkyConfirmButtonHarnessFilters): Promise<SkyConfirmButtonHarness>`

Gets a specific confirm custom button based on the filter criteria.

#### Parameters

##### `filter: SkyConfirmButtonHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyConfirmButtonHarness>`

#### `getCustomButtons(filters?: SkyConfirmButtonHarnessFilters): Promise<SkyConfirmButtonHarness[]>`

Gets an array of confirm custom buttons based on the filter criteria. If no filter is provided, returns all confirm custom buttons.

#### Parameters

##### `filters?: SkyConfirmButtonHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyConfirmButtonHarness[]>`

#### `getMessageText(): Promise<string>`

Gets the message of the confirm component.

#### Returns

`Promise<string>`

#### `getType(): Promise<SkyConfirmType>`

Gets the type of the confirm component.

#### Returns

`Promise<SkyConfirmType>`

#### `isWhiteSpacePreserved(): Promise<boolean>`

Whether the whitespace is preserved on the confirm component.

#### Returns

`Promise<boolean>`

 SkyConfirmButtonHarness
------------------------

Type: Class

`import { SkyConfirmButtonHarness } from '@skyux/modals/testing';`

Harness for interacting with a confirm component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the confirm button.

#### Returns

`Promise<void>`

#### `getStyleType(): Promise<SkyConfirmButtonStyleType>`

Gets the button style of the confirm button.

#### Returns

`Promise<SkyConfirmButtonStyleType>`

#### `getText(): Promise<string>`

Gets the text content of the confirm button.

#### Returns

`Promise<string>`

#### `SkyConfirmButtonHarness.with(filters: SkyConfirmButtonHarnessFilters): HarnessPredicate<SkyConfirmButtonHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyConfirmButtonHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyConfirmButtonHarnessFilters`

#### Returns

`HarnessPredicate<SkyConfirmButtonHarness>`

 SkyConfirmButtonHarnessFilters
-------------------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyConfirmButtonHarness](/skyux/components/confirm?docs-active-tab=testing#class_sky-confirm-button-harness.md) instances.

    interface SkyConfirmButtonHarnessFilters {
      styleType?: string;
      text?: string | RegExp;
    }

### Properties

#### `styleType?: string`

Only find instances whose style matches the given value.

#### `text?: string | RegExp`

Only find instances whose content matches the given value.

 SkyConfirmTestingModule
------------------------

Type: Module

`import { SkyConfirmTestingModule } from '@skyux/modals/testing';`

Configures the `SkyConfirmTestingController` as the backend for the `SkyConfirmService`.

 SkyConfirmTestingController
----------------------------

Type: Class

A controller to be injected into tests, which mocks the confirm service and handles interactions with confirm dialogs.

### Methods

#### `cancel(): void`

Closes the confirm dialog with the "cancel" action.

#### Returns

`void`

#### `close(args: SkyConfirmCloseEventArgs): void`

Closes the confirm dialog with the provided action.

#### Parameters

##### `args: SkyConfirmCloseEventArgs`

#### Returns

`void`

#### `expectNone(): void`

Throws if a confirm dialog is open.

#### Returns

`void`

#### `expectOpen(config: SkyConfirmConfig): void`

Throws if the open confirm dialog does not match the provided configuration.

#### Parameters

##### `config: SkyConfirmConfig`

#### Returns

`void`

#### `ok(): void`

Closes the confirm dialog with the "ok" action.

#### Returns

`void`