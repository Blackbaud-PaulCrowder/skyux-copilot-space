# Design

                  Skip to Main Content

 Error
=====

The error component displays a SKY UX-themed error message.

 Usage
------

### Use when

Use error messages to communicate system statuses to users when the system encounters unexpected errors.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-1.57e72d1dfb5d65d471a62856c41aa88f.png)

Do use error messages when system errors occur.

Use error messages when the content inside modals fails to load.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-8.87634b5baa62cd8637e9606d2479eac9.png)

Do use error messages when system errors occur when opening modals.

### Don't use when

Don't use error messages to display information about background processes. Use [toasts](/skyux/components/toast.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-2.7d3fe9f62b8697b41827bcaa24379d7e.png)

Don't use error messages for background processes.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-7.340ee0d39e6d311d34ff5d7e9b19c3b7.png)

Do use toasts to inform users about background processes.

Don't use error messages when statuses on specific content require user attention but when no system errors occurred. To notify users of broken statuses on workflows or records, use [alerts](/skyux/components/alert.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-3.f9c12df24e5721a8ac8a7c1b9d9270b2.png)

Don't use error messages to highlight content that users must address when no errors occurred.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-4.d8fd8d5183c874e0c07944fe6b1a58dc.png)

Do use alerts to call attention to issues that require user interaction.

Don't use security error messages when users lack permission to view portions of pages or modals such as tiles on record pages. Hide the content from view instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-5.ced7a6f664144577cd006590b60c3b92.png)

Don't use security error messages in portions of pages or modals. Hide the restricted content instead.

 Anatomy
--------

1

Title

2

Image (optional)

3

Description (optional)

4

Action (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-anatomy.1328aa284f223ca0b9b9d6466a315d8f.png)

 Options
--------

### Error type

Use the broken error type in situations when underlying content doesn't load or when issues such as 500 errors reach the server.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-option-broken.e6c8e4daae448da5583bc79cec8cfd9d.png)

Use the under construction error type when pages are under maintenance or experience known outages.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-option-construction.2a5473ae978c2d324876584357af89b8.png)

Use the not found error type when pages fail to load because of 404 errors.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-option-notfound.a2880635383441067e601977c7913505.png)

Use the security error type when users don't have access to view content.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-option-security.19e3c113d809559d3d0cb40bdabb4924.png)

### Image

Include images when error messages are the only content on pages. Tiles have limited space and may not be important to users' immediate tasks, so exclude images in tiles and only display the title and description.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-6.9d0be3995cae0325cdf88d5ce9a0cd6b.png)

Exclude images and actions when error messages only affect portions of the content on pages and users can still complete other tasks.

### Description

Use descriptions to recommend solutions for users to resolve errors and to explain why the errors occurred.

### Action

Include actions when error messages are the only content on pages. When users can complete other tasks without addressing errors, provide suggestions to correct errors in the description, but exclude attention-drawing actions.

 Content
--------

### Style and tone

Make error messages short and succinct, and use a conversational tone. Keep the title brief, and when possible, use a description to offer a solution and to explain why the error or warning is occurring.

Errors can frustrate users and sometimes indicate serious problems, so be thoughtful and helpful with the wording. Avoid humor, limit the use of "please" and "sorry," and avoid negative constructions such as "you can't" and "you don't" that could be received as criticism.

 Layout
-------

The error component, including its title and description text, is always centered within its container.

 Related Information
--------------------

### Components

*   [Alert](/skyux/components/alert.md)
*   [Toast](/skyux/components/toast.md)

### Guidelines

*   [Error handling](/skyux/design/guidelines/error-handling.md)
*   [Form design](/skyux/design/guidelines/form-design.md)
*   [User assistance](/skyux/design/guidelines/user-assistance.md)

 Installation
-------------

NPM package

`@skyux/errors`[View in NPM](https://www.npmjs.com/package/@skyux/errors) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/errors/src/lib/modules/error/error.module.ts#L29) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/errors`Copy None found.

 SkyErrorModule
---------------

Type: Module

`import { SkyErrorModule } from '@skyux/errors';`

 SkyErrorComponent
------------------

Type: Component

Selector: `sky-error`

Displays a SKY UX-themed error message.

### Inputs

#### `errorType: SkyErrorType | undefined`

The set of pre-defined values for the image, title, and description.

#### `showImage: boolean | undefined`

Whether to display the error image.

Default: `true`

 SkyErrorImageComponent
-----------------------

Type: Component

Selector: `sky-error-image`

Specifies an image to display with the error message.

 SkyErrorTitleComponent
-----------------------

Type: Component

Selector: `sky-error-title`

Specifies a title to display with the error message.

### Inputs

#### `replaceDefaultTitle: boolean | undefined`

Whether to replace the default title. If `false`, the content from this component is added after the default title.

Default: `false`

 SkyErrorDescriptionComponent
-----------------------------

Type: Component

Selector: `sky-error-description`

Specifies a description to provide additional details about the error.

### Inputs

#### `replaceDefaultDescription: boolean | undefined`

Whether to replace the default description. If `false`, the content from this component is added after the default description.

Default: `false`

 SkyErrorActionComponent
------------------------

Type: Component

Selector: `sky-error-action`

Specifies an interactive element to include with the error message. For example, you can include a button to reload the page or to refresh data.

 SkyErrorType
-------------

Type: Type alias

The type of error to display.

    type SkyErrorType = "broken" | "construction" | "notfound" | "security"

 SkyErrorModalService
---------------------

Type: Service

Warning: **Deprecated.** We recommend using a standard modal with an error component instead.

Opens a modal to display a SKY UX-themed error message.

### Methods

#### `open(config: ErrorModalConfig): void`

Warning: **Deprecated.** We recommend using a standard modal with an error component instead.

Text for the the error message, including title, description, and action label.

#### Parameters

##### `config: ErrorModalConfig`

#### Returns

`void`

 ErrorModalConfig
-----------------

Type: Class

Warning: **Deprecated.** We recommend using a standard modal with an error component instead.

### Properties

#### `errorCloseText: string | undefined`

The label for the action button that closes the modal error message.

#### `errorDescription: string | undefined`

The description to provide additional details in the modal error message.

#### `errorTitle: string | undefined`

The title to display in the modal error message.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyErrorHarness
----------------

Type: Class

`import { SkyErrorHarness } from '@skyux/errors/testing';`

Harness for interacting with an error component in tests.

### Methods

#### `clickActionButton(): Promise<void>`

Clicks the action button in the error action.

#### Returns

`Promise<void>`

#### `getActionButtonText(): Promise<string>`

Gets the text of the action button in the error action.

#### Returns

`Promise<string>`

#### `getDescription(): Promise<string>`

Gets the description of the error.

#### Returns

`Promise<string>`

#### `getErrorAction(): Promise<SkyErrorActionHarness>`

Gets an error action harness.

#### Returns

`Promise<SkyErrorActionHarness>`

#### `getErrorImage(): Promise<SkyErrorImageHarness>`

Gets an error image harness.

#### Returns

`Promise<SkyErrorImageHarness>`

#### `getErrorType(): Promise<undefined | SkyErrorType>`

Gets the error type.

#### Returns

`Promise<undefined | SkyErrorType>`

#### `getTitle(): Promise<string>`

Gets the title of the error.

#### Returns

`Promise<string>`

#### `hasImage(): Promise<boolean>`

Whether the error displays an image.

#### Returns

`Promise<boolean>`

#### `SkyErrorHarness.with(filters: SkyErrorHarnessFilters): HarnessPredicate<SkyErrorHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyErrorHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyErrorHarnessFilters`

#### Returns

`HarnessPredicate<SkyErrorHarness>`

 SkyErrorHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyErrorHarness` instances.

    interface SkyErrorHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyErrorActionHarness
----------------------

Type: Class

`import { SkyErrorActionHarness } from '@skyux/errors/testing';`

Harness for interacting with an error action component in tests.

### Methods

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

 SkyErrorImageHarness
---------------------

Type: Class

`import { SkyErrorImageHarness } from '@skyux/errors/testing';`

Harness for interacting with an error image component in tests.

### Methods

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

# Development

                  Skip to Main Content

 Error
=====

The error component displays a SKY UX-themed error message.

 Usage
------

### Use when

Use error messages to communicate system statuses to users when the system encounters unexpected errors.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-1.57e72d1dfb5d65d471a62856c41aa88f.png)

Do use error messages when system errors occur.

Use error messages when the content inside modals fails to load.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-8.87634b5baa62cd8637e9606d2479eac9.png)

Do use error messages when system errors occur when opening modals.

### Don't use when

Don't use error messages to display information about background processes. Use [toasts](/skyux/components/toast.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-2.7d3fe9f62b8697b41827bcaa24379d7e.png)

Don't use error messages for background processes.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-7.340ee0d39e6d311d34ff5d7e9b19c3b7.png)

Do use toasts to inform users about background processes.

Don't use error messages when statuses on specific content require user attention but when no system errors occurred. To notify users of broken statuses on workflows or records, use [alerts](/skyux/components/alert.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-3.f9c12df24e5721a8ac8a7c1b9d9270b2.png)

Don't use error messages to highlight content that users must address when no errors occurred.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-4.d8fd8d5183c874e0c07944fe6b1a58dc.png)

Do use alerts to call attention to issues that require user interaction.

Don't use security error messages when users lack permission to view portions of pages or modals such as tiles on record pages. Hide the content from view instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-5.ced7a6f664144577cd006590b60c3b92.png)

Don't use security error messages in portions of pages or modals. Hide the restricted content instead.

 Anatomy
--------

1

Title

2

Image (optional)

3

Description (optional)

4

Action (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-anatomy.1328aa284f223ca0b9b9d6466a315d8f.png)

 Options
--------

### Error type

Use the broken error type in situations when underlying content doesn't load or when issues such as 500 errors reach the server.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-option-broken.e6c8e4daae448da5583bc79cec8cfd9d.png)

Use the under construction error type when pages are under maintenance or experience known outages.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-option-construction.2a5473ae978c2d324876584357af89b8.png)

Use the not found error type when pages fail to load because of 404 errors.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-option-notfound.a2880635383441067e601977c7913505.png)

Use the security error type when users don't have access to view content.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-option-security.19e3c113d809559d3d0cb40bdabb4924.png)

### Image

Include images when error messages are the only content on pages. Tiles have limited space and may not be important to users' immediate tasks, so exclude images in tiles and only display the title and description.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-6.9d0be3995cae0325cdf88d5ce9a0cd6b.png)

Exclude images and actions when error messages only affect portions of the content on pages and users can still complete other tasks.

### Description

Use descriptions to recommend solutions for users to resolve errors and to explain why the errors occurred.

### Action

Include actions when error messages are the only content on pages. When users can complete other tasks without addressing errors, provide suggestions to correct errors in the description, but exclude attention-drawing actions.

 Content
--------

### Style and tone

Make error messages short and succinct, and use a conversational tone. Keep the title brief, and when possible, use a description to offer a solution and to explain why the error or warning is occurring.

Errors can frustrate users and sometimes indicate serious problems, so be thoughtful and helpful with the wording. Avoid humor, limit the use of "please" and "sorry," and avoid negative constructions such as "you can't" and "you don't" that could be received as criticism.

 Layout
-------

The error component, including its title and description text, is always centered within its container.

 Related Information
--------------------

### Components

*   [Alert](/skyux/components/alert.md)
*   [Toast](/skyux/components/toast.md)

### Guidelines

*   [Error handling](/skyux/design/guidelines/error-handling.md)
*   [Form design](/skyux/design/guidelines/form-design.md)
*   [User assistance](/skyux/design/guidelines/user-assistance.md)

 Installation
-------------

NPM package

`@skyux/errors`[View in NPM](https://www.npmjs.com/package/@skyux/errors) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/errors/src/lib/modules/error/error.module.ts#L29) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/errors`Copy None found.

 SkyErrorModule
---------------

Type: Module

`import { SkyErrorModule } from '@skyux/errors';`

 SkyErrorComponent
------------------

Type: Component

Selector: `sky-error`

Displays a SKY UX-themed error message.

### Inputs

#### `errorType: SkyErrorType | undefined`

The set of pre-defined values for the image, title, and description.

#### `showImage: boolean | undefined`

Whether to display the error image.

Default: `true`

 SkyErrorImageComponent
-----------------------

Type: Component

Selector: `sky-error-image`

Specifies an image to display with the error message.

 SkyErrorTitleComponent
-----------------------

Type: Component

Selector: `sky-error-title`

Specifies a title to display with the error message.

### Inputs

#### `replaceDefaultTitle: boolean | undefined`

Whether to replace the default title. If `false`, the content from this component is added after the default title.

Default: `false`

 SkyErrorDescriptionComponent
-----------------------------

Type: Component

Selector: `sky-error-description`

Specifies a description to provide additional details about the error.

### Inputs

#### `replaceDefaultDescription: boolean | undefined`

Whether to replace the default description. If `false`, the content from this component is added after the default description.

Default: `false`

 SkyErrorActionComponent
------------------------

Type: Component

Selector: `sky-error-action`

Specifies an interactive element to include with the error message. For example, you can include a button to reload the page or to refresh data.

 SkyErrorType
-------------

Type: Type alias

The type of error to display.

    type SkyErrorType = "broken" | "construction" | "notfound" | "security"

 SkyErrorModalService
---------------------

Type: Service

Warning: **Deprecated.** We recommend using a standard modal with an error component instead.

Opens a modal to display a SKY UX-themed error message.

### Methods

#### `open(config: ErrorModalConfig): void`

Warning: **Deprecated.** We recommend using a standard modal with an error component instead.

Text for the the error message, including title, description, and action label.

#### Parameters

##### `config: ErrorModalConfig`

#### Returns

`void`

 ErrorModalConfig
-----------------

Type: Class

Warning: **Deprecated.** We recommend using a standard modal with an error component instead.

### Properties

#### `errorCloseText: string | undefined`

The label for the action button that closes the modal error message.

#### `errorDescription: string | undefined`

The description to provide additional details in the modal error message.

#### `errorTitle: string | undefined`

The title to display in the modal error message.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyErrorHarness
----------------

Type: Class

`import { SkyErrorHarness } from '@skyux/errors/testing';`

Harness for interacting with an error component in tests.

### Methods

#### `clickActionButton(): Promise<void>`

Clicks the action button in the error action.

#### Returns

`Promise<void>`

#### `getActionButtonText(): Promise<string>`

Gets the text of the action button in the error action.

#### Returns

`Promise<string>`

#### `getDescription(): Promise<string>`

Gets the description of the error.

#### Returns

`Promise<string>`

#### `getErrorAction(): Promise<SkyErrorActionHarness>`

Gets an error action harness.

#### Returns

`Promise<SkyErrorActionHarness>`

#### `getErrorImage(): Promise<SkyErrorImageHarness>`

Gets an error image harness.

#### Returns

`Promise<SkyErrorImageHarness>`

#### `getErrorType(): Promise<undefined | SkyErrorType>`

Gets the error type.

#### Returns

`Promise<undefined | SkyErrorType>`

#### `getTitle(): Promise<string>`

Gets the title of the error.

#### Returns

`Promise<string>`

#### `hasImage(): Promise<boolean>`

Whether the error displays an image.

#### Returns

`Promise<boolean>`

#### `SkyErrorHarness.with(filters: SkyErrorHarnessFilters): HarnessPredicate<SkyErrorHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyErrorHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyErrorHarnessFilters`

#### Returns

`HarnessPredicate<SkyErrorHarness>`

 SkyErrorHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyErrorHarness` instances.

    interface SkyErrorHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyErrorActionHarness
----------------------

Type: Class

`import { SkyErrorActionHarness } from '@skyux/errors/testing';`

Harness for interacting with an error action component in tests.

### Methods

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

 SkyErrorImageHarness
---------------------

Type: Class

`import { SkyErrorImageHarness } from '@skyux/errors/testing';`

Harness for interacting with an error image component in tests.

### Methods

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

# Examples

                    Skip to Main Content

 Error
=====

The error component displays a SKY UX-themed error message.Usage
------

### Use when

Use error messages to communicate system statuses to users when the system encounters unexpected errors.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-1.57e72d1dfb5d65d471a62856c41aa88f.png)

Do use error messages when system errors occur.

Use error messages when the content inside modals fails to load.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-8.87634b5baa62cd8637e9606d2479eac9.png)

Do use error messages when system errors occur when opening modals.

### Don't use when

Don't use error messages to display information about background processes. Use [toasts](/skyux/components/toast.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-2.7d3fe9f62b8697b41827bcaa24379d7e.png)

Don't use error messages for background processes.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-7.340ee0d39e6d311d34ff5d7e9b19c3b7.png)

Do use toasts to inform users about background processes.

Don't use error messages when statuses on specific content require user attention but when no system errors occurred. To notify users of broken statuses on workflows or records, use [alerts](/skyux/components/alert.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-3.f9c12df24e5721a8ac8a7c1b9d9270b2.png)

Don't use error messages to highlight content that users must address when no errors occurred.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-4.d8fd8d5183c874e0c07944fe6b1a58dc.png)

Do use alerts to call attention to issues that require user interaction.

Don't use security error messages when users lack permission to view portions of pages or modals such as tiles on record pages. Hide the content from view instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-5.ced7a6f664144577cd006590b60c3b92.png)

Don't use security error messages in portions of pages or modals. Hide the restricted content instead.

 Anatomy
--------

1

Title

2

Image (optional)

3

Description (optional)

4

Action (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-anatomy.1328aa284f223ca0b9b9d6466a315d8f.png)

 Options
--------

### Error type

Use the broken error type in situations when underlying content doesn't load or when issues such as 500 errors reach the server.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-option-broken.e6c8e4daae448da5583bc79cec8cfd9d.png)

Use the under construction error type when pages are under maintenance or experience known outages.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-option-construction.2a5473ae978c2d324876584357af89b8.png)

Use the not found error type when pages fail to load because of 404 errors.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-option-notfound.a2880635383441067e601977c7913505.png)

Use the security error type when users don't have access to view content.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-option-security.19e3c113d809559d3d0cb40bdabb4924.png)

### Image

Include images when error messages are the only content on pages. Tiles have limited space and may not be important to users' immediate tasks, so exclude images in tiles and only display the title and description.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-6.9d0be3995cae0325cdf88d5ce9a0cd6b.png)

Exclude images and actions when error messages only affect portions of the content on pages and users can still complete other tasks.

### Description

Use descriptions to recommend solutions for users to resolve errors and to explain why the errors occurred.

### Action

Include actions when error messages are the only content on pages. When users can complete other tasks without addressing errors, provide suggestions to correct errors in the description, but exclude attention-drawing actions.

 Content
--------

### Style and tone

Make error messages short and succinct, and use a conversational tone. Keep the title brief, and when possible, use a description to offer a solution and to explain why the error or warning is occurring.

Errors can frustrate users and sometimes indicate serious problems, so be thoughtful and helpful with the wording. Avoid humor, limit the use of "please" and "sorry," and avoid negative constructions such as "you can't" and "you don't" that could be received as criticism.

 Layout
-------

The error component, including its title and description text, is always centered within its container.

 Related Information
--------------------

### Components

*   [Alert](/skyux/components/alert.md)
*   [Toast](/skyux/components/toast.md)

### Guidelines

*   [Error handling](/skyux/design/guidelines/error-handling.md)
*   [Form design](/skyux/design/guidelines/form-design.md)
*   [User assistance](/skyux/design/guidelines/user-assistance.md)

 Installation
-------------

NPM package

`@skyux/errors`[View in NPM](https://www.npmjs.com/package/@skyux/errors) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/errors/src/lib/modules/error/error.module.ts#L29) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/errors`Copy None found.

 SkyErrorModule
---------------

Type: Module

`import { SkyErrorModule } from '@skyux/errors';`

 SkyErrorComponent
------------------

Type: Component

Selector: `sky-error`

Displays a SKY UX-themed error message.

### Inputs

#### `errorType: SkyErrorType | undefined`

The set of pre-defined values for the image, title, and description.

#### `showImage: boolean | undefined`

Whether to display the error image.

Default: `true`

 SkyErrorImageComponent
-----------------------

Type: Component

Selector: `sky-error-image`

Specifies an image to display with the error message.

 SkyErrorTitleComponent
-----------------------

Type: Component

Selector: `sky-error-title`

Specifies a title to display with the error message.

### Inputs

#### `replaceDefaultTitle: boolean | undefined`

Whether to replace the default title. If `false`, the content from this component is added after the default title.

Default: `false`

 SkyErrorDescriptionComponent
-----------------------------

Type: Component

Selector: `sky-error-description`

Specifies a description to provide additional details about the error.

### Inputs

#### `replaceDefaultDescription: boolean | undefined`

Whether to replace the default description. If `false`, the content from this component is added after the default description.

Default: `false`

 SkyErrorActionComponent
------------------------

Type: Component

Selector: `sky-error-action`

Specifies an interactive element to include with the error message. For example, you can include a button to reload the page or to refresh data.

 SkyErrorType
-------------

Type: Type alias

The type of error to display.

    type SkyErrorType = "broken" | "construction" | "notfound" | "security"

 SkyErrorModalService
---------------------

Type: Service

Warning: **Deprecated.** We recommend using a standard modal with an error component instead.

Opens a modal to display a SKY UX-themed error message.

### Methods

#### `open(config: ErrorModalConfig): void`

Warning: **Deprecated.** We recommend using a standard modal with an error component instead.

Text for the the error message, including title, description, and action label.

#### Parameters

##### `config: ErrorModalConfig`

#### Returns

`void`

 ErrorModalConfig
-----------------

Type: Class

Warning: **Deprecated.** We recommend using a standard modal with an error component instead.

### Properties

#### `errorCloseText: string | undefined`

The label for the action button that closes the modal error message.

#### `errorDescription: string | undefined`

The description to provide additional details in the modal error message.

#### `errorTitle: string | undefined`

The title to display in the modal error message.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyErrorHarness
----------------

Type: Class

`import { SkyErrorHarness } from '@skyux/errors/testing';`

Harness for interacting with an error component in tests.

### Methods

#### `clickActionButton(): Promise<void>`

Clicks the action button in the error action.

#### Returns

`Promise<void>`

#### `getActionButtonText(): Promise<string>`

Gets the text of the action button in the error action.

#### Returns

`Promise<string>`

#### `getDescription(): Promise<string>`

Gets the description of the error.

#### Returns

`Promise<string>`

#### `getErrorAction(): Promise<SkyErrorActionHarness>`

Gets an error action harness.

#### Returns

`Promise<SkyErrorActionHarness>`

#### `getErrorImage(): Promise<SkyErrorImageHarness>`

Gets an error image harness.

#### Returns

`Promise<SkyErrorImageHarness>`

#### `getErrorType(): Promise<undefined | SkyErrorType>`

Gets the error type.

#### Returns

`Promise<undefined | SkyErrorType>`

#### `getTitle(): Promise<string>`

Gets the title of the error.

#### Returns

`Promise<string>`

#### `hasImage(): Promise<boolean>`

Whether the error displays an image.

#### Returns

`Promise<boolean>`

#### `SkyErrorHarness.with(filters: SkyErrorHarnessFilters): HarnessPredicate<SkyErrorHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyErrorHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyErrorHarnessFilters`

#### Returns

`HarnessPredicate<SkyErrorHarness>`

 SkyErrorHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyErrorHarness` instances.

    interface SkyErrorHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyErrorActionHarness
----------------------

Type: Class

`import { SkyErrorActionHarness } from '@skyux/errors/testing';`

Harness for interacting with an error action component in tests.

### Methods

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

 SkyErrorImageHarness
---------------------

Type: Class

`import { SkyErrorImageHarness } from '@skyux/errors/testing';`

Harness for interacting with an error image component in tests.

### Methods

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

### Embed error within the page markup

Edit in StackBlitz

That's odd...

Something went wrong. Try again or come back later.

Try again

Nothing to see here.

Pardon us, but this page is missing or has moved.

Go back

Work in progress.

We appreciate your patience while we make improvements.

Go back

Heads up! You're in a restricted area.

Ask your administrator for access.

Go back

![](data:image/png;base64,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)

Custom error with a custom image.

Custom description.

Custom action

Custom error with a default image.

Custom description.

Custom action

Show code

Copy

    <sky-error errorType="broken">
      <sky-error-action>
        <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
          Try again
        </button>
      </sky-error-action>
    </sky-error>
    
    <sky-error errorType="notfound">
      <sky-error-action>
        <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
          Go back
        </button>
      </sky-error-action>
    </sky-error>
    
    <sky-error errorType="construction">
      <sky-error-action>
        <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
          Go back
        </button>
      </sky-error-action>
    </sky-error>
    
    <sky-error errorType="security">
      <sky-error-action>
        <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
          Go back
        </button>
      </sky-error-action>
    </sky-error>
    
    <sky-error>
      <sky-error-image>
        <img
          alt=""
          role="presentation"
          src="data:image/png;base64,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"
        />
      </sky-error-image>
      <sky-error-title> Custom error with a custom image. </sky-error-title>
      <sky-error-description> Custom description. </sky-error-description>
      <sky-error-action>
        <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
          Custom action
        </button>
      </sky-error-action>
    </sky-error>
    
    <sky-error errorType="broken">
      <sky-error-title [replaceDefaultTitle]="true">
        Custom error with a default image.
      </sky-error-title>
      <sky-error-description [replaceDefaultDescription]="true">
        Custom description.
      </sky-error-description>
      <sky-error-action>
        <button class="sky-btn sky-btn-link" type="button" (click)="customAction()">
          Custom action
        </button>
      </sky-error-action>
    </sky-error>

Copy

    import { Component } from '@angular/core';
    import { SkyErrorModule } from '@skyux/errors';
    
    /**
     * @title Embed error within the page markup
     */
    @Component({
      selector: 'app-errors-error-embedded-example',
      templateUrl: './example.component.html',
      imports: [SkyErrorModule],
    })
    export class ErrorsErrorEmbeddedExampleComponent {
      protected customAction(): void {
        alert('action clicked!');
      }
    }
### Show an error inside a modal

Edit in StackBlitz

Open error modal

Show code

Copy

    <button
      class="sky-btn sky-btn-default"
      type="button"
      (click)="openErrorModal()"
    >
      Open error modal
    </button>

Copy

    import { Component, inject } from '@angular/core';
    import { SkyErrorModalService } from '@skyux/errors';
    
    /**
     * @title Show an error inside a modal
     */
    @Component({
      standalone: true,
      selector: 'app-errors-error-modal-example',
      templateUrl: './example.component.html',
    })
    export class ErrorsErrorModalExampleComponent {
      readonly #errorSvc = inject(SkyErrorModalService);
    
      public openErrorModal(): void {
        this.#errorSvc.open({
          errorTitle: 'Something went wrong.',
          errorDescription: 'Close the modal, and come back later.',
          errorCloseText: 'Close',
        });
      }
    }

# Testing

                  Skip to Main Content

 Error
=====

The error component displays a SKY UX-themed error message.

 Usage
------

### Use when

Use error messages to communicate system statuses to users when the system encounters unexpected errors.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-1.57e72d1dfb5d65d471a62856c41aa88f.png)

Do use error messages when system errors occur.

Use error messages when the content inside modals fails to load.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-8.87634b5baa62cd8637e9606d2479eac9.png)

Do use error messages when system errors occur when opening modals.

### Don't use when

Don't use error messages to display information about background processes. Use [toasts](/skyux/components/toast.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-2.7d3fe9f62b8697b41827bcaa24379d7e.png)

Don't use error messages for background processes.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-7.340ee0d39e6d311d34ff5d7e9b19c3b7.png)

Do use toasts to inform users about background processes.

Don't use error messages when statuses on specific content require user attention but when no system errors occurred. To notify users of broken statuses on workflows or records, use [alerts](/skyux/components/alert.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-3.f9c12df24e5721a8ac8a7c1b9d9270b2.png)

Don't use error messages to highlight content that users must address when no errors occurred.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-4.d8fd8d5183c874e0c07944fe6b1a58dc.png)

Do use alerts to call attention to issues that require user interaction.

Don't use security error messages when users lack permission to view portions of pages or modals such as tiles on record pages. Hide the content from view instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-5.ced7a6f664144577cd006590b60c3b92.png)

Don't use security error messages in portions of pages or modals. Hide the restricted content instead.

 Anatomy
--------

1

Title

2

Image (optional)

3

Description (optional)

4

Action (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-anatomy.1328aa284f223ca0b9b9d6466a315d8f.png)

 Options
--------

### Error type

Use the broken error type in situations when underlying content doesn't load or when issues such as 500 errors reach the server.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-option-broken.e6c8e4daae448da5583bc79cec8cfd9d.png)

Use the under construction error type when pages are under maintenance or experience known outages.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-option-construction.2a5473ae978c2d324876584357af89b8.png)

Use the not found error type when pages fail to load because of 404 errors.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-option-notfound.a2880635383441067e601977c7913505.png)

Use the security error type when users don't have access to view content.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-option-security.19e3c113d809559d3d0cb40bdabb4924.png)

### Image

Include images when error messages are the only content on pages. Tiles have limited space and may not be important to users' immediate tasks, so exclude images in tiles and only display the title and description.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/errors/img/guidelines/error/error-usage-6.9d0be3995cae0325cdf88d5ce9a0cd6b.png)

Exclude images and actions when error messages only affect portions of the content on pages and users can still complete other tasks.

### Description

Use descriptions to recommend solutions for users to resolve errors and to explain why the errors occurred.

### Action

Include actions when error messages are the only content on pages. When users can complete other tasks without addressing errors, provide suggestions to correct errors in the description, but exclude attention-drawing actions.

 Content
--------

### Style and tone

Make error messages short and succinct, and use a conversational tone. Keep the title brief, and when possible, use a description to offer a solution and to explain why the error or warning is occurring.

Errors can frustrate users and sometimes indicate serious problems, so be thoughtful and helpful with the wording. Avoid humor, limit the use of "please" and "sorry," and avoid negative constructions such as "you can't" and "you don't" that could be received as criticism.

 Layout
-------

The error component, including its title and description text, is always centered within its container.

 Related Information
--------------------

### Components

*   [Alert](/skyux/components/alert.md)
*   [Toast](/skyux/components/toast.md)

### Guidelines

*   [Error handling](/skyux/design/guidelines/error-handling.md)
*   [Form design](/skyux/design/guidelines/form-design.md)
*   [User assistance](/skyux/design/guidelines/user-assistance.md)

 Installation
-------------

NPM package

`@skyux/errors`[View in NPM](https://www.npmjs.com/package/@skyux/errors) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/errors/src/lib/modules/error/error.module.ts#L29) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/errors`Copy None found.

 SkyErrorModule
---------------

Type: Module

`import { SkyErrorModule } from '@skyux/errors';`

 SkyErrorComponent
------------------

Type: Component

Selector: `sky-error`

Displays a SKY UX-themed error message.

### Inputs

#### `errorType: SkyErrorType | undefined`

The set of pre-defined values for the image, title, and description.

#### `showImage: boolean | undefined`

Whether to display the error image.

Default: `true`

 SkyErrorImageComponent
-----------------------

Type: Component

Selector: `sky-error-image`

Specifies an image to display with the error message.

 SkyErrorTitleComponent
-----------------------

Type: Component

Selector: `sky-error-title`

Specifies a title to display with the error message.

### Inputs

#### `replaceDefaultTitle: boolean | undefined`

Whether to replace the default title. If `false`, the content from this component is added after the default title.

Default: `false`

 SkyErrorDescriptionComponent
-----------------------------

Type: Component

Selector: `sky-error-description`

Specifies a description to provide additional details about the error.

### Inputs

#### `replaceDefaultDescription: boolean | undefined`

Whether to replace the default description. If `false`, the content from this component is added after the default description.

Default: `false`

 SkyErrorActionComponent
------------------------

Type: Component

Selector: `sky-error-action`

Specifies an interactive element to include with the error message. For example, you can include a button to reload the page or to refresh data.

 SkyErrorType
-------------

Type: Type alias

The type of error to display.

    type SkyErrorType = "broken" | "construction" | "notfound" | "security"

 SkyErrorModalService
---------------------

Type: Service

Warning: **Deprecated.** We recommend using a standard modal with an error component instead.

Opens a modal to display a SKY UX-themed error message.

### Methods

#### `open(config: ErrorModalConfig): void`

Warning: **Deprecated.** We recommend using a standard modal with an error component instead.

Text for the the error message, including title, description, and action label.

#### Parameters

##### `config: ErrorModalConfig`

#### Returns

`void`

 ErrorModalConfig
-----------------

Type: Class

Warning: **Deprecated.** We recommend using a standard modal with an error component instead.

### Properties

#### `errorCloseText: string | undefined`

The label for the action button that closes the modal error message.

#### `errorDescription: string | undefined`

The description to provide additional details in the modal error message.

#### `errorTitle: string | undefined`

The title to display in the modal error message.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyErrorHarness
----------------

Type: Class

`import { SkyErrorHarness } from '@skyux/errors/testing';`

Harness for interacting with an error component in tests.

### Methods

#### `clickActionButton(): Promise<void>`

Clicks the action button in the error action.

#### Returns

`Promise<void>`

#### `getActionButtonText(): Promise<string>`

Gets the text of the action button in the error action.

#### Returns

`Promise<string>`

#### `getDescription(): Promise<string>`

Gets the description of the error.

#### Returns

`Promise<string>`

#### `getErrorAction(): Promise<SkyErrorActionHarness>`

Gets an error action harness.

#### Returns

`Promise<SkyErrorActionHarness>`

#### `getErrorImage(): Promise<SkyErrorImageHarness>`

Gets an error image harness.

#### Returns

`Promise<SkyErrorImageHarness>`

#### `getErrorType(): Promise<undefined | SkyErrorType>`

Gets the error type.

#### Returns

`Promise<undefined | SkyErrorType>`

#### `getTitle(): Promise<string>`

Gets the title of the error.

#### Returns

`Promise<string>`

#### `hasImage(): Promise<boolean>`

Whether the error displays an image.

#### Returns

`Promise<boolean>`

#### `SkyErrorHarness.with(filters: SkyErrorHarnessFilters): HarnessPredicate<SkyErrorHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyErrorHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyErrorHarnessFilters`

#### Returns

`HarnessPredicate<SkyErrorHarness>`

 SkyErrorHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyErrorHarness` instances.

    interface SkyErrorHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyErrorActionHarness
----------------------

Type: Class

`import { SkyErrorActionHarness } from '@skyux/errors/testing';`

Harness for interacting with an error action component in tests.

### Methods

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

 SkyErrorImageHarness
---------------------

Type: Class

`import { SkyErrorImageHarness } from '@skyux/errors/testing';`

Harness for interacting with an error image component in tests.

### Methods

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