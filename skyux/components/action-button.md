# Design

                      Skip to Main Content

 Action button
=============

Action buttons create large buttons with icons, headers, and descriptions that present users with multiple, branching options to move forward with tasks

 Usage
------

### Use when

Use actions buttons when:

*   Users initiate tasks, often with a page's primary action. Tasks include 2 to 6 methods of completion, and users must choose exactly one method. If tasks have more than 6 methods of completion, use a different [selection input](/skyux/design/guidelines/form-design#selection-inputs.md) and interaction.
*   Methods of completion are system-defined, not user-defined.
*   Methods of completion mostly determine how tasks proceed, and this choice is made at or near the beginning of the task
*   The outcome of end result will be largely the same, regardless of the method

Use action buttons when they represent a decision point within a task where users must select a method of completion. Do not use them when users can skip them, avoid them, or address them later. Present action buttons in a way that isolates the choices that they represent and removes other decisions, tasks, or content. Use the details line on the buttons to provide context or explain differences between the options.

Use action buttons immediately after users initiate tasks to differentiate the methods of completion.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-use-when-1.12dfebfe661e9bfed392cdf8668f8c7e.png)

Do use action buttons immediately after users initiate tasks.

Use action buttons on pages or modals when tasks are underway and the only relevant choice for users is how to complete tasks. Do not display other inputs or choices until users select an action button. Then hide the action buttons or close the modals.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-use-when-2.e1ea6a60c31e25a2a424607f4164ee1f.png)

Do use action buttons when the only relevant choice for users is how to complete tasks.

### Don't use when

Don't use an action button by itself. Action buttons should not serve as primary calls-to-action on pages where other actions are available to users.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-dont-use-when-1.2180039e6baf95722227c4f2b85d42ac.png)

Don't use an action button by itself.

Do not use actions buttons to present different methods of completing tasks before users initiate the tasks. Action buttons should not compete against other content for user attention.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-dont-use-when-2.97b7c405ccb4c2cf947633fa5517d7ec.png)

Don't use action buttons to present different methods of completing tasks before users initiate the tasks.

Do not use action buttons when consequential choices are not made at the beginning of tasks. Instead, use a different selection input and progressive disclosure to reveal additional content as necessary. Likewise, do not use action buttons when the methods of completion in tasks differ only in minor ways such as an extra field or two. Action buttons represent consequential decisions where the methods of completion can start and end differently and can include entirely different steps and requirements.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-dont-use-when-3.39ed616eb1262a0e089e2aa51da356c2.png)

Don't use action buttons when choices are not made at the beginning of tasks.

 Behavior and states
--------------------

### Task placement

Use action buttons inside modals when tasks mostly take place within modals. For example, when tasks create records or pages that do not exist until users complete the tasks, place action buttons in modals. This is common for add processes that have multiple methods of completion and only require standard modals to create records.

*   Use the default-size modal for 2 action buttons, and use a large modal for 3 or more.

*   Center the action buttons inside the modal and wrap to another row if needed.

*   When the user selects a choice, dismiss this modal and open whatever container is appropriate for the remainder of the task.

*   If users cancel or abandon the task, do not return to the modal.

*   Always provide a "Cancel" action inside a modal with action buttons.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-behavior-1.bb3199022603f343d081c9cf64694bc1.png)

Use action buttons directly on pages or tabs that include add or configuration processes but no other tasks. Most add processes use the modal example above.

*   If necessary, include a question above the action buttons to explain the decision being made.
*   Center the question and action buttons inside the page.
*   When users select one of the action buttons, replace them with the next step of the task.
*   If users leave the page without selecting an action button, treat the record or process as "incomplete" and place any appropriate status indicators on its parent view.

*   If it is useful to include an option for users to back out of configuration processes, place an explicit "Cancel" or "Delete" action under the action buttons.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-behavior-2.6fa389f7a2bc47e56d536b0967edb410.png)

Use action buttons directly inside tabs instead of modals when users add user-defined tabs and select how populate the content.

*   A "Cancel" action under the action buttons is not necessary because users can remove user-defined tabs on the tab control.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-behavior-3.02f7e64f1012a0f3748a1af7ea886258.png)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/action-button/action-button.module.ts#L37) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyActionButtonModule
----------------------

Type: Module

`import { SkyActionButtonModule } from '@skyux/layout';`

 SkyActionButtonContainerComponent
----------------------------------

Type: Component

Selector: `sky-action-button-container`

Wraps action buttons to ensures that they have consistent height and spacing.

### Inputs

#### `alignItems: SkyActionButtonContainerAlignItemsType`

How to display the action buttons inside the action button container. Options are `"center"` or `"left"`.

Default: `"center"`

 SkyActionButtonComponent
-------------------------

Type: Component

Selector: `sky-action-button`

Creates a button to present users with an option to move forward with tasks.

### Inputs

#### `permalink: SkyActionButtonPermalink | undefined`

The link for the action button.

### Outputs

#### `actionClick: EventEmitter<any>`

Fires when users select the action button.

 SkyActionButtonIconComponent
-----------------------------

Type: Component

Selector: `sky-action-button-icon`

Specifies an icon to display on the action button.

### Inputs

#### `iconName: string`

The name of the Blackbaud SVG icon to display.

 SkyActionButtonHeaderComponent
-------------------------------

Type: Component

Selector: `sky-action-button-header`

Specifies a header to display on an action button.

 SkyActionButtonDetailsComponent
--------------------------------

Type: Component

Selector: `sky-action-button-details`

Specifies a description to display on an action button.

 SkyActionButtonPermalink
-------------------------

Type: Interface

Specifies an Angular router link with the `route` property or a direct link with the `url` property. If it provides both, the action button uses the `route` property.

    interface SkyActionButtonPermalink {
      route?: { commands?: string | any[]; extras?: NavigationExtras };
      url?: string;
    }

### Properties

#### `route?: { commands?: string | any[]; extras?: NavigationExtras }`

The Angular router link for the action button. This property accepts a custom object with a `commands` property to specify router commands and an `extras` property to specify [Angular `NavigationExtras`](https://angular.io/api/router/NavigationExtras). This property passes the following properties:

*   `permalink.route?.extras?.fragment` to [`fragment`](https://angular.io/api/router/NavigationExtras#fragment)
*   `permalink.route?.extras?.queryParams` to [`queryParams`](https://angular.io/api/router/NavigationExtras#queryParams)
*   `permalink.route?.extras?.queryParamsHandling` to [`queryParamsHandling`](https://angular.io/api/router/NavigationExtras#queryParamsHandling)
*   `permalink.route?.commands` to [`routerLink`](https://angular.io/api/router/RouterLink)

#### `url?: string`

The direct link for the action button.

 SkyActionButtonContainerAlignItemsType
---------------------------------------

Type: Type alias

    type SkyActionButtonContainerAlignItemsType = "center" | "left"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyActionButtonContainerHarness
--------------------------------

Type: Class

`import { SkyActionButtonContainerHarness } from '@skyux/layout/testing';`

Harness for interacting with a action button container component in tests.

### Methods

#### `getActionButton(filter: SkyActionButtonHarnessFilters): Promise<SkyActionButtonHarness>`

Gets a specific action button based on the filter criteria.

#### Parameters

##### `filter: SkyActionButtonHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyActionButtonHarness>`

#### `getActionButtons(filters?: SkyActionButtonHarnessFilters): Promise<SkyActionButtonHarness[]>`

Gets an array of action buttons based on the filter criteria. If no filter is provided, returns all action buttons.

#### Parameters

##### `filters?: SkyActionButtonHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyActionButtonHarness[]>`

#### `getAlignment(): Promise<SkyActionButtonContainerAlignItemsType>`

Gets the alignment of the buttons inside the container.

#### Returns

`Promise<SkyActionButtonContainerAlignItemsType>`

#### `SkyActionButtonContainerHarness.with(filters: SkyActionButtonContainerHarnessFilters): HarnessPredicate<SkyActionButtonContainerHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyActionButtonContainerHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyActionButtonContainerHarnessFilters`

#### Returns

`HarnessPredicate<SkyActionButtonContainerHarness>`

 SkyActionButtonContainerHarnessFilters
---------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyActionButtonContainerHarness` instances.

    interface SkyActionButtonContainerHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyActionButtonHarness
-----------------------

Type: Class

`import { SkyActionButtonHarness } from '@skyux/layout/testing';`

Harness for interacting with a action button component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the action button.

#### Returns

`Promise<void>`

#### `getDetailsText(): Promise<null | string>`

Gets the action button details text.

#### Returns

`Promise<null | string>`

#### `getHeaderText(): Promise<null | string>`

Gets the action button header text.

#### Returns

`Promise<null | string>`

#### `getIconType(): Promise<undefined | string>`

Gets the action button icon type.

#### Returns

`Promise<undefined | string>`

#### `getLink(): Promise<undefined | string>`

Gets the action button link.

#### Returns

`Promise<undefined | string>`

#### `SkyActionButtonHarness.with(filters: SkyActionButtonHarnessFilters): HarnessPredicate<SkyActionButtonHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyActionButtonHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyActionButtonHarnessFilters`

#### Returns

`HarnessPredicate<SkyActionButtonHarness>`

 SkyActionButtonHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyActionButtonHarness` instances.

    interface SkyActionButtonHarnessFilters {
      dataSkyId?: string | RegExp;
      header?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `header?: string`

Finds action buttons whose header matches given value.

# Development

                      Skip to Main Content

 Action button
=============

Action buttons create large buttons with icons, headers, and descriptions that present users with multiple, branching options to move forward with tasks

 Usage
------

### Use when

Use actions buttons when:

*   Users initiate tasks, often with a page's primary action. Tasks include 2 to 6 methods of completion, and users must choose exactly one method. If tasks have more than 6 methods of completion, use a different [selection input](/skyux/design/guidelines/form-design#selection-inputs.md) and interaction.
*   Methods of completion are system-defined, not user-defined.
*   Methods of completion mostly determine how tasks proceed, and this choice is made at or near the beginning of the task
*   The outcome of end result will be largely the same, regardless of the method

Use action buttons when they represent a decision point within a task where users must select a method of completion. Do not use them when users can skip them, avoid them, or address them later. Present action buttons in a way that isolates the choices that they represent and removes other decisions, tasks, or content. Use the details line on the buttons to provide context or explain differences between the options.

Use action buttons immediately after users initiate tasks to differentiate the methods of completion.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-use-when-1.12dfebfe661e9bfed392cdf8668f8c7e.png)

Do use action buttons immediately after users initiate tasks.

Use action buttons on pages or modals when tasks are underway and the only relevant choice for users is how to complete tasks. Do not display other inputs or choices until users select an action button. Then hide the action buttons or close the modals.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-use-when-2.e1ea6a60c31e25a2a424607f4164ee1f.png)

Do use action buttons when the only relevant choice for users is how to complete tasks.

### Don't use when

Don't use an action button by itself. Action buttons should not serve as primary calls-to-action on pages where other actions are available to users.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-dont-use-when-1.2180039e6baf95722227c4f2b85d42ac.png)

Don't use an action button by itself.

Do not use actions buttons to present different methods of completing tasks before users initiate the tasks. Action buttons should not compete against other content for user attention.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-dont-use-when-2.97b7c405ccb4c2cf947633fa5517d7ec.png)

Don't use action buttons to present different methods of completing tasks before users initiate the tasks.

Do not use action buttons when consequential choices are not made at the beginning of tasks. Instead, use a different selection input and progressive disclosure to reveal additional content as necessary. Likewise, do not use action buttons when the methods of completion in tasks differ only in minor ways such as an extra field or two. Action buttons represent consequential decisions where the methods of completion can start and end differently and can include entirely different steps and requirements.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-dont-use-when-3.39ed616eb1262a0e089e2aa51da356c2.png)

Don't use action buttons when choices are not made at the beginning of tasks.

 Behavior and states
--------------------

### Task placement

Use action buttons inside modals when tasks mostly take place within modals. For example, when tasks create records or pages that do not exist until users complete the tasks, place action buttons in modals. This is common for add processes that have multiple methods of completion and only require standard modals to create records.

*   Use the default-size modal for 2 action buttons, and use a large modal for 3 or more.

*   Center the action buttons inside the modal and wrap to another row if needed.

*   When the user selects a choice, dismiss this modal and open whatever container is appropriate for the remainder of the task.

*   If users cancel or abandon the task, do not return to the modal.

*   Always provide a "Cancel" action inside a modal with action buttons.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-behavior-1.bb3199022603f343d081c9cf64694bc1.png)

Use action buttons directly on pages or tabs that include add or configuration processes but no other tasks. Most add processes use the modal example above.

*   If necessary, include a question above the action buttons to explain the decision being made.
*   Center the question and action buttons inside the page.
*   When users select one of the action buttons, replace them with the next step of the task.
*   If users leave the page without selecting an action button, treat the record or process as "incomplete" and place any appropriate status indicators on its parent view.

*   If it is useful to include an option for users to back out of configuration processes, place an explicit "Cancel" or "Delete" action under the action buttons.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-behavior-2.6fa389f7a2bc47e56d536b0967edb410.png)

Use action buttons directly inside tabs instead of modals when users add user-defined tabs and select how populate the content.

*   A "Cancel" action under the action buttons is not necessary because users can remove user-defined tabs on the tab control.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-behavior-3.02f7e64f1012a0f3748a1af7ea886258.png)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/action-button/action-button.module.ts#L37) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyActionButtonModule
----------------------

Type: Module

`import { SkyActionButtonModule } from '@skyux/layout';`

 SkyActionButtonContainerComponent
----------------------------------

Type: Component

Selector: `sky-action-button-container`

Wraps action buttons to ensures that they have consistent height and spacing.

### Inputs

#### `alignItems: SkyActionButtonContainerAlignItemsType`

How to display the action buttons inside the action button container. Options are `"center"` or `"left"`.

Default: `"center"`

 SkyActionButtonComponent
-------------------------

Type: Component

Selector: `sky-action-button`

Creates a button to present users with an option to move forward with tasks.

### Inputs

#### `permalink: SkyActionButtonPermalink | undefined`

The link for the action button.

### Outputs

#### `actionClick: EventEmitter<any>`

Fires when users select the action button.

 SkyActionButtonIconComponent
-----------------------------

Type: Component

Selector: `sky-action-button-icon`

Specifies an icon to display on the action button.

### Inputs

#### `iconName: string`

The name of the Blackbaud SVG icon to display.

 SkyActionButtonHeaderComponent
-------------------------------

Type: Component

Selector: `sky-action-button-header`

Specifies a header to display on an action button.

 SkyActionButtonDetailsComponent
--------------------------------

Type: Component

Selector: `sky-action-button-details`

Specifies a description to display on an action button.

 SkyActionButtonPermalink
-------------------------

Type: Interface

Specifies an Angular router link with the `route` property or a direct link with the `url` property. If it provides both, the action button uses the `route` property.

    interface SkyActionButtonPermalink {
      route?: { commands?: string | any[]; extras?: NavigationExtras };
      url?: string;
    }

### Properties

#### `route?: { commands?: string | any[]; extras?: NavigationExtras }`

The Angular router link for the action button. This property accepts a custom object with a `commands` property to specify router commands and an `extras` property to specify [Angular `NavigationExtras`](https://angular.io/api/router/NavigationExtras). This property passes the following properties:

*   `permalink.route?.extras?.fragment` to [`fragment`](https://angular.io/api/router/NavigationExtras#fragment)
*   `permalink.route?.extras?.queryParams` to [`queryParams`](https://angular.io/api/router/NavigationExtras#queryParams)
*   `permalink.route?.extras?.queryParamsHandling` to [`queryParamsHandling`](https://angular.io/api/router/NavigationExtras#queryParamsHandling)
*   `permalink.route?.commands` to [`routerLink`](https://angular.io/api/router/RouterLink)

#### `url?: string`

The direct link for the action button.

 SkyActionButtonContainerAlignItemsType
---------------------------------------

Type: Type alias

    type SkyActionButtonContainerAlignItemsType = "center" | "left"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyActionButtonContainerHarness
--------------------------------

Type: Class

`import { SkyActionButtonContainerHarness } from '@skyux/layout/testing';`

Harness for interacting with a action button container component in tests.

### Methods

#### `getActionButton(filter: SkyActionButtonHarnessFilters): Promise<SkyActionButtonHarness>`

Gets a specific action button based on the filter criteria.

#### Parameters

##### `filter: SkyActionButtonHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyActionButtonHarness>`

#### `getActionButtons(filters?: SkyActionButtonHarnessFilters): Promise<SkyActionButtonHarness[]>`

Gets an array of action buttons based on the filter criteria. If no filter is provided, returns all action buttons.

#### Parameters

##### `filters?: SkyActionButtonHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyActionButtonHarness[]>`

#### `getAlignment(): Promise<SkyActionButtonContainerAlignItemsType>`

Gets the alignment of the buttons inside the container.

#### Returns

`Promise<SkyActionButtonContainerAlignItemsType>`

#### `SkyActionButtonContainerHarness.with(filters: SkyActionButtonContainerHarnessFilters): HarnessPredicate<SkyActionButtonContainerHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyActionButtonContainerHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyActionButtonContainerHarnessFilters`

#### Returns

`HarnessPredicate<SkyActionButtonContainerHarness>`

 SkyActionButtonContainerHarnessFilters
---------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyActionButtonContainerHarness` instances.

    interface SkyActionButtonContainerHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyActionButtonHarness
-----------------------

Type: Class

`import { SkyActionButtonHarness } from '@skyux/layout/testing';`

Harness for interacting with a action button component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the action button.

#### Returns

`Promise<void>`

#### `getDetailsText(): Promise<null | string>`

Gets the action button details text.

#### Returns

`Promise<null | string>`

#### `getHeaderText(): Promise<null | string>`

Gets the action button header text.

#### Returns

`Promise<null | string>`

#### `getIconType(): Promise<undefined | string>`

Gets the action button icon type.

#### Returns

`Promise<undefined | string>`

#### `getLink(): Promise<undefined | string>`

Gets the action button link.

#### Returns

`Promise<undefined | string>`

#### `SkyActionButtonHarness.with(filters: SkyActionButtonHarnessFilters): HarnessPredicate<SkyActionButtonHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyActionButtonHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyActionButtonHarnessFilters`

#### Returns

`HarnessPredicate<SkyActionButtonHarness>`

 SkyActionButtonHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyActionButtonHarness` instances.

    interface SkyActionButtonHarnessFilters {
      dataSkyId?: string | RegExp;
      header?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `header?: string`

Finds action buttons whose header matches given value.

# Examples

                      Skip to Main Content

 Action button
=============

Action buttons create large buttons with icons, headers, and descriptions that present users with multiple, branching options to move forward with tasks

 Usage
------

### Use when

Use actions buttons when:

*   Users initiate tasks, often with a page's primary action. Tasks include 2 to 6 methods of completion, and users must choose exactly one method. If tasks have more than 6 methods of completion, use a different [selection input](/skyux/design/guidelines/form-design#selection-inputs.md) and interaction.
*   Methods of completion are system-defined, not user-defined.
*   Methods of completion mostly determine how tasks proceed, and this choice is made at or near the beginning of the task
*   The outcome of end result will be largely the same, regardless of the method

Use action buttons when they represent a decision point within a task where users must select a method of completion. Do not use them when users can skip them, avoid them, or address them later. Present action buttons in a way that isolates the choices that they represent and removes other decisions, tasks, or content. Use the details line on the buttons to provide context or explain differences between the options.

Use action buttons immediately after users initiate tasks to differentiate the methods of completion.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-use-when-1.12dfebfe661e9bfed392cdf8668f8c7e.png)

Do use action buttons immediately after users initiate tasks.

Use action buttons on pages or modals when tasks are underway and the only relevant choice for users is how to complete tasks. Do not display other inputs or choices until users select an action button. Then hide the action buttons or close the modals.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-use-when-2.e1ea6a60c31e25a2a424607f4164ee1f.png)

Do use action buttons when the only relevant choice for users is how to complete tasks.

### Don't use when

Don't use an action button by itself. Action buttons should not serve as primary calls-to-action on pages where other actions are available to users.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-dont-use-when-1.2180039e6baf95722227c4f2b85d42ac.png)

Don't use an action button by itself.

Do not use actions buttons to present different methods of completing tasks before users initiate the tasks. Action buttons should not compete against other content for user attention.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-dont-use-when-2.97b7c405ccb4c2cf947633fa5517d7ec.png)

Don't use action buttons to present different methods of completing tasks before users initiate the tasks.

Do not use action buttons when consequential choices are not made at the beginning of tasks. Instead, use a different selection input and progressive disclosure to reveal additional content as necessary. Likewise, do not use action buttons when the methods of completion in tasks differ only in minor ways such as an extra field or two. Action buttons represent consequential decisions where the methods of completion can start and end differently and can include entirely different steps and requirements.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-dont-use-when-3.39ed616eb1262a0e089e2aa51da356c2.png)

Don't use action buttons when choices are not made at the beginning of tasks.

 Behavior and states
--------------------

### Task placement

Use action buttons inside modals when tasks mostly take place within modals. For example, when tasks create records or pages that do not exist until users complete the tasks, place action buttons in modals. This is common for add processes that have multiple methods of completion and only require standard modals to create records.

*   Use the default-size modal for 2 action buttons, and use a large modal for 3 or more.

*   Center the action buttons inside the modal and wrap to another row if needed.

*   When the user selects a choice, dismiss this modal and open whatever container is appropriate for the remainder of the task.

*   If users cancel or abandon the task, do not return to the modal.

*   Always provide a "Cancel" action inside a modal with action buttons.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-behavior-1.bb3199022603f343d081c9cf64694bc1.png)

Use action buttons directly on pages or tabs that include add or configuration processes but no other tasks. Most add processes use the modal example above.

*   If necessary, include a question above the action buttons to explain the decision being made.
*   Center the question and action buttons inside the page.
*   When users select one of the action buttons, replace them with the next step of the task.
*   If users leave the page without selecting an action button, treat the record or process as "incomplete" and place any appropriate status indicators on its parent view.

*   If it is useful to include an option for users to back out of configuration processes, place an explicit "Cancel" or "Delete" action under the action buttons.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-behavior-2.6fa389f7a2bc47e56d536b0967edb410.png)

Use action buttons directly inside tabs instead of modals when users add user-defined tabs and select how populate the content.

*   A "Cancel" action under the action buttons is not necessary because users can remove user-defined tabs on the tab control.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-behavior-3.02f7e64f1012a0f3748a1af7ea886258.png)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/action-button/action-button.module.ts#L37) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyActionButtonModule
----------------------

Type: Module

`import { SkyActionButtonModule } from '@skyux/layout';`

 SkyActionButtonContainerComponent
----------------------------------

Type: Component

Selector: `sky-action-button-container`

Wraps action buttons to ensures that they have consistent height and spacing.

### Inputs

#### `alignItems: SkyActionButtonContainerAlignItemsType`

How to display the action buttons inside the action button container. Options are `"center"` or `"left"`.

Default: `"center"`

 SkyActionButtonComponent
-------------------------

Type: Component

Selector: `sky-action-button`

Creates a button to present users with an option to move forward with tasks.

### Inputs

#### `permalink: SkyActionButtonPermalink | undefined`

The link for the action button.

### Outputs

#### `actionClick: EventEmitter<any>`

Fires when users select the action button.

 SkyActionButtonIconComponent
-----------------------------

Type: Component

Selector: `sky-action-button-icon`

Specifies an icon to display on the action button.

### Inputs

#### `iconName: string`

The name of the Blackbaud SVG icon to display.

 SkyActionButtonHeaderComponent
-------------------------------

Type: Component

Selector: `sky-action-button-header`

Specifies a header to display on an action button.

 SkyActionButtonDetailsComponent
--------------------------------

Type: Component

Selector: `sky-action-button-details`

Specifies a description to display on an action button.

 SkyActionButtonPermalink
-------------------------

Type: Interface

Specifies an Angular router link with the `route` property or a direct link with the `url` property. If it provides both, the action button uses the `route` property.

    interface SkyActionButtonPermalink {
      route?: { commands?: string | any[]; extras?: NavigationExtras };
      url?: string;
    }

### Properties

#### `route?: { commands?: string | any[]; extras?: NavigationExtras }`

The Angular router link for the action button. This property accepts a custom object with a `commands` property to specify router commands and an `extras` property to specify [Angular `NavigationExtras`](https://angular.io/api/router/NavigationExtras). This property passes the following properties:

*   `permalink.route?.extras?.fragment` to [`fragment`](https://angular.io/api/router/NavigationExtras#fragment)
*   `permalink.route?.extras?.queryParams` to [`queryParams`](https://angular.io/api/router/NavigationExtras#queryParams)
*   `permalink.route?.extras?.queryParamsHandling` to [`queryParamsHandling`](https://angular.io/api/router/NavigationExtras#queryParamsHandling)
*   `permalink.route?.commands` to [`routerLink`](https://angular.io/api/router/RouterLink)

#### `url?: string`

The direct link for the action button.

 SkyActionButtonContainerAlignItemsType
---------------------------------------

Type: Type alias

    type SkyActionButtonContainerAlignItemsType = "center" | "left"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyActionButtonContainerHarness
--------------------------------

Type: Class

`import { SkyActionButtonContainerHarness } from '@skyux/layout/testing';`

Harness for interacting with a action button container component in tests.

### Methods

#### `getActionButton(filter: SkyActionButtonHarnessFilters): Promise<SkyActionButtonHarness>`

Gets a specific action button based on the filter criteria.

#### Parameters

##### `filter: SkyActionButtonHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyActionButtonHarness>`

#### `getActionButtons(filters?: SkyActionButtonHarnessFilters): Promise<SkyActionButtonHarness[]>`

Gets an array of action buttons based on the filter criteria. If no filter is provided, returns all action buttons.

#### Parameters

##### `filters?: SkyActionButtonHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyActionButtonHarness[]>`

#### `getAlignment(): Promise<SkyActionButtonContainerAlignItemsType>`

Gets the alignment of the buttons inside the container.

#### Returns

`Promise<SkyActionButtonContainerAlignItemsType>`

#### `SkyActionButtonContainerHarness.with(filters: SkyActionButtonContainerHarnessFilters): HarnessPredicate<SkyActionButtonContainerHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyActionButtonContainerHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyActionButtonContainerHarnessFilters`

#### Returns

`HarnessPredicate<SkyActionButtonContainerHarness>`

 SkyActionButtonContainerHarnessFilters
---------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyActionButtonContainerHarness` instances.

    interface SkyActionButtonContainerHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyActionButtonHarness
-----------------------

Type: Class

`import { SkyActionButtonHarness } from '@skyux/layout/testing';`

Harness for interacting with a action button component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the action button.

#### Returns

`Promise<void>`

#### `getDetailsText(): Promise<null | string>`

Gets the action button details text.

#### Returns

`Promise<null | string>`

#### `getHeaderText(): Promise<null | string>`

Gets the action button header text.

#### Returns

`Promise<null | string>`

#### `getIconType(): Promise<undefined | string>`

Gets the action button icon type.

#### Returns

`Promise<undefined | string>`

#### `getLink(): Promise<undefined | string>`

Gets the action button link.

#### Returns

`Promise<undefined | string>`

#### `SkyActionButtonHarness.with(filters: SkyActionButtonHarnessFilters): HarnessPredicate<SkyActionButtonHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyActionButtonHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyActionButtonHarnessFilters`

#### Returns

`HarnessPredicate<SkyActionButtonHarness>`

 SkyActionButtonHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyActionButtonHarness` instances.

    interface SkyActionButtonHarnessFilters {
      dataSkyId?: string | RegExp;
      header?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `header?: string`

Finds action buttons whose header matches given value.

# Testing

                      Skip to Main Content

 Action button
=============

Action buttons create large buttons with icons, headers, and descriptions that present users with multiple, branching options to move forward with tasks

 Usage
------

### Use when

Use actions buttons when:

*   Users initiate tasks, often with a page's primary action. Tasks include 2 to 6 methods of completion, and users must choose exactly one method. If tasks have more than 6 methods of completion, use a different [selection input](/skyux/design/guidelines/form-design#selection-inputs.md) and interaction.
*   Methods of completion are system-defined, not user-defined.
*   Methods of completion mostly determine how tasks proceed, and this choice is made at or near the beginning of the task
*   The outcome of end result will be largely the same, regardless of the method

Use action buttons when they represent a decision point within a task where users must select a method of completion. Do not use them when users can skip them, avoid them, or address them later. Present action buttons in a way that isolates the choices that they represent and removes other decisions, tasks, or content. Use the details line on the buttons to provide context or explain differences between the options.

Use action buttons immediately after users initiate tasks to differentiate the methods of completion.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-use-when-1.12dfebfe661e9bfed392cdf8668f8c7e.png)

Do use action buttons immediately after users initiate tasks.

Use action buttons on pages or modals when tasks are underway and the only relevant choice for users is how to complete tasks. Do not display other inputs or choices until users select an action button. Then hide the action buttons or close the modals.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-use-when-2.e1ea6a60c31e25a2a424607f4164ee1f.png)

Do use action buttons when the only relevant choice for users is how to complete tasks.

### Don't use when

Don't use an action button by itself. Action buttons should not serve as primary calls-to-action on pages where other actions are available to users.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-dont-use-when-1.2180039e6baf95722227c4f2b85d42ac.png)

Don't use an action button by itself.

Do not use actions buttons to present different methods of completing tasks before users initiate the tasks. Action buttons should not compete against other content for user attention.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-dont-use-when-2.97b7c405ccb4c2cf947633fa5517d7ec.png)

Don't use action buttons to present different methods of completing tasks before users initiate the tasks.

Do not use action buttons when consequential choices are not made at the beginning of tasks. Instead, use a different selection input and progressive disclosure to reveal additional content as necessary. Likewise, do not use action buttons when the methods of completion in tasks differ only in minor ways such as an extra field or two. Action buttons represent consequential decisions where the methods of completion can start and end differently and can include entirely different steps and requirements.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-dont-use-when-3.39ed616eb1262a0e089e2aa51da356c2.png)

Don't use action buttons when choices are not made at the beginning of tasks.

 Behavior and states
--------------------

### Task placement

Use action buttons inside modals when tasks mostly take place within modals. For example, when tasks create records or pages that do not exist until users complete the tasks, place action buttons in modals. This is common for add processes that have multiple methods of completion and only require standard modals to create records.

*   Use the default-size modal for 2 action buttons, and use a large modal for 3 or more.

*   Center the action buttons inside the modal and wrap to another row if needed.

*   When the user selects a choice, dismiss this modal and open whatever container is appropriate for the remainder of the task.

*   If users cancel or abandon the task, do not return to the modal.

*   Always provide a "Cancel" action inside a modal with action buttons.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-behavior-1.bb3199022603f343d081c9cf64694bc1.png)

Use action buttons directly on pages or tabs that include add or configuration processes but no other tasks. Most add processes use the modal example above.

*   If necessary, include a question above the action buttons to explain the decision being made.
*   Center the question and action buttons inside the page.
*   When users select one of the action buttons, replace them with the next step of the task.
*   If users leave the page without selecting an action button, treat the record or process as "incomplete" and place any appropriate status indicators on its parent view.

*   If it is useful to include an option for users to back out of configuration processes, place an explicit "Cancel" or "Delete" action under the action buttons.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-behavior-2.6fa389f7a2bc47e56d536b0967edb410.png)

Use action buttons directly inside tabs instead of modals when users add user-defined tabs and select how populate the content.

*   A "Cancel" action under the action buttons is not necessary because users can remove user-defined tabs on the tab control.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/layout/img/guidelines/action-button/action-button-behavior-3.02f7e64f1012a0f3748a1af7ea886258.png)

 Installation
-------------

NPM package

`@skyux/layout`[View in NPM](https://www.npmjs.com/package/@skyux/layout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/layout/src/lib/modules/action-button/action-button.module.ts#L37) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/layout`Copy None found.

 SkyActionButtonModule
----------------------

Type: Module

`import { SkyActionButtonModule } from '@skyux/layout';`

 SkyActionButtonContainerComponent
----------------------------------

Type: Component

Selector: `sky-action-button-container`

Wraps action buttons to ensures that they have consistent height and spacing.

### Inputs

#### `alignItems: SkyActionButtonContainerAlignItemsType`

How to display the action buttons inside the action button container. Options are `"center"` or `"left"`.

Default: `"center"`

 SkyActionButtonComponent
-------------------------

Type: Component

Selector: `sky-action-button`

Creates a button to present users with an option to move forward with tasks.

### Inputs

#### `permalink: SkyActionButtonPermalink | undefined`

The link for the action button.

### Outputs

#### `actionClick: EventEmitter<any>`

Fires when users select the action button.

 SkyActionButtonIconComponent
-----------------------------

Type: Component

Selector: `sky-action-button-icon`

Specifies an icon to display on the action button.

### Inputs

#### `iconName: string`

The name of the Blackbaud SVG icon to display.

 SkyActionButtonHeaderComponent
-------------------------------

Type: Component

Selector: `sky-action-button-header`

Specifies a header to display on an action button.

 SkyActionButtonDetailsComponent
--------------------------------

Type: Component

Selector: `sky-action-button-details`

Specifies a description to display on an action button.

 SkyActionButtonPermalink
-------------------------

Type: Interface

Specifies an Angular router link with the `route` property or a direct link with the `url` property. If it provides both, the action button uses the `route` property.

    interface SkyActionButtonPermalink {
      route?: { commands?: string | any[]; extras?: NavigationExtras };
      url?: string;
    }

### Properties

#### `route?: { commands?: string | any[]; extras?: NavigationExtras }`

The Angular router link for the action button. This property accepts a custom object with a `commands` property to specify router commands and an `extras` property to specify [Angular `NavigationExtras`](https://angular.io/api/router/NavigationExtras). This property passes the following properties:

*   `permalink.route?.extras?.fragment` to [`fragment`](https://angular.io/api/router/NavigationExtras#fragment)
*   `permalink.route?.extras?.queryParams` to [`queryParams`](https://angular.io/api/router/NavigationExtras#queryParams)
*   `permalink.route?.extras?.queryParamsHandling` to [`queryParamsHandling`](https://angular.io/api/router/NavigationExtras#queryParamsHandling)
*   `permalink.route?.commands` to [`routerLink`](https://angular.io/api/router/RouterLink)

#### `url?: string`

The direct link for the action button.

 SkyActionButtonContainerAlignItemsType
---------------------------------------

Type: Type alias

    type SkyActionButtonContainerAlignItemsType = "center" | "left"

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyActionButtonContainerHarness
--------------------------------

Type: Class

`import { SkyActionButtonContainerHarness } from '@skyux/layout/testing';`

Harness for interacting with a action button container component in tests.

### Methods

#### `getActionButton(filter: SkyActionButtonHarnessFilters): Promise<SkyActionButtonHarness>`

Gets a specific action button based on the filter criteria.

#### Parameters

##### `filter: SkyActionButtonHarnessFilters`

The filter criteria.

#### Returns

`Promise<SkyActionButtonHarness>`

#### `getActionButtons(filters?: SkyActionButtonHarnessFilters): Promise<SkyActionButtonHarness[]>`

Gets an array of action buttons based on the filter criteria. If no filter is provided, returns all action buttons.

#### Parameters

##### `filters?: SkyActionButtonHarnessFilters`

The optional filter criteria.

#### Returns

`Promise<SkyActionButtonHarness[]>`

#### `getAlignment(): Promise<SkyActionButtonContainerAlignItemsType>`

Gets the alignment of the buttons inside the container.

#### Returns

`Promise<SkyActionButtonContainerAlignItemsType>`

#### `SkyActionButtonContainerHarness.with(filters: SkyActionButtonContainerHarnessFilters): HarnessPredicate<SkyActionButtonContainerHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyActionButtonContainerHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyActionButtonContainerHarnessFilters`

#### Returns

`HarnessPredicate<SkyActionButtonContainerHarness>`

 SkyActionButtonContainerHarnessFilters
---------------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyActionButtonContainerHarness` instances.

    interface SkyActionButtonContainerHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyActionButtonHarness
-----------------------

Type: Class

`import { SkyActionButtonHarness } from '@skyux/layout/testing';`

Harness for interacting with a action button component in tests.

### Methods

#### `click(): Promise<void>`

Clicks the action button.

#### Returns

`Promise<void>`

#### `getDetailsText(): Promise<null | string>`

Gets the action button details text.

#### Returns

`Promise<null | string>`

#### `getHeaderText(): Promise<null | string>`

Gets the action button header text.

#### Returns

`Promise<null | string>`

#### `getIconType(): Promise<undefined | string>`

Gets the action button icon type.

#### Returns

`Promise<undefined | string>`

#### `getLink(): Promise<undefined | string>`

Gets the action button link.

#### Returns

`Promise<undefined | string>`

#### `SkyActionButtonHarness.with(filters: SkyActionButtonHarnessFilters): HarnessPredicate<SkyActionButtonHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyActionButtonHarness` that meets certain criteria.

#### Parameters

##### `filters: SkyActionButtonHarnessFilters`

#### Returns

`HarnessPredicate<SkyActionButtonHarness>`

 SkyActionButtonHarnessFilters
------------------------------

Type: Interface

A set of criteria that can be used to filter a list of `SkyActionButtonHarness` instances.

    interface SkyActionButtonHarnessFilters {
      dataSkyId?: string | RegExp;
      header?: string;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

#### `header?: string`

Finds action buttons whose header matches given value.