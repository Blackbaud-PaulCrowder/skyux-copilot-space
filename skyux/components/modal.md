# Design

                  Skip to Main Content

 Modal
=====

The modal component and service launch modals in a consistent way in SKY UX applications.

 Usage
------

### Use modals when

Use modals when tasks are functionally modal and users must finish them before doing anything else.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-usage1.0e224e8642a8fa0c41c003b676a33edd.png)

Do use modals when users must complete tasks before they proceed.

Use modals when displaying forms inline would lead to substantial content shifting or require users to scroll to complete the forms.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-usage2.c67fa46f712a5f337db5830372683c8f.png)

Do use modals when displaying long forms.

Use modals when users need to add records from paginated lists or infinite scroll lists.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-usage3.d6aaf7ab43a0797fd54430f333e81b8f.png)

Do use modals to add records from paginated lists or infinite scroll lists.

Use large modals when housing a large component that best utilizes the horizontal space, such as [sectioned forms](/skyux/components/sectioned-form.md) or [wizards](/skyux/components/tabs-wizard.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-usage4.db94507f627c55a790ef44efe3b65d9d.png)

Do use large modals with sectioned forms and wizards.

### Use full-screen modals when

Use full-screen modals when users usually perform self-contained tasks in a large viewport, and a full-screen modal can optimize the use of space.

Use full-screen modals when forms display feedback based on user entries or selections. For example, forms may display running totals or preview emails as they are constructed.

Use full-screen modals when forms support complex tasks for lists of objects such as filling out report cards for a class.

Use full-screen modals when tasks include subtasks that users need to complete in context.

 Anatomy
--------

1

Heading

2

Content

3

Footer

4

Buttons

5

Help inline button (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-anatomy.dcee172de54b95db0670744b5f9b5d47.png)

 Options
--------

### Help inline button

When you need to supplement a modal header with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the header to invoke contextual user assistance.

 Behavior and states
--------------------

### Unsaved data

If users close a modal before saving their changes, use `SkyModalIsDirtyDirective` to warn them about losing the unsaved data with a [confirmation dialog](/skyux/components/confirm.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/modal-close-confirm.f756192fa9878ff34249421a094c4aa3.png)

 Content
--------

### Modal title text

Modal titles use sentence-case capitalization and the following format:

<Verb> <direct object> for <indirect object>

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-with-object.2c333b6186ad2d87652c5b2643e86e0f.png)

If there is not an indirect object or the user is the implied indirect object, exclude it:

<Verb> <direct object>

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-without-object.faba5d6e76fe17417ec29341cfbdc897.png)

### Buttons in the modal action bar

Button labels should clearly indicate the actions that occur when users select buttons. For example, use **Save** as the standard label for actions where users save information to the database, but use **Submit** or another alternative if you need to indicate that an action sends data somewhere else. Make sure to use the label that is most accurate for all contexts. For example, while **Cancel** and **Close** both indicate that actions close modals, **Cancel** more clearly indicates that the actions do not save changes to modals; **Cancel** should be used in most cases.

Use a [primary button](/skyux/components/button.md) for the most important action that users take, secondary buttons for less important actions, and a link button for the **Cancel** action. Follow the [form design guidelines](/skyux/design/guidelines/form-design.md) and disable the primary action until all required inputs have valid values. If a modal has only one action, use the [confirm component](/skyux/components/confirm.md) instead.

 Related information
--------------------

### Components

*   [Buttons](/skyux/components/button.md)
*   [Confirmation dialog](/skyux/components/confirm.md)
*   [Input box](/skyux/components/input-box.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/modals`[View in NPM](https://www.npmjs.com/package/@skyux/modals) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/modals/src/lib/modules/modal/modal.module.ts#L25) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/modals`Copy None found.

 SkyModalModule
---------------

Type: Module

`import { SkyModalModule } from '@skyux/modals';`

 SkyModalComponent
------------------

Type: Component

Selector: `sky-modal`

Provides a common look-and-feel for modal content with options to display a common modal header, specify body content, and display a common modal footer and buttons.

### Inputs

#### `formErrors: SkyModalError[] | undefined`

A list of form-level errors to display to the user.

#### `headingText: string | undefined`

The text to display as the modal's heading.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to the modal header. Clicking the button invokes global help as configured by the application. This property only applies when `headingText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to the modal header. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `layout: InputSignal<"none" | "fit">`

 SkyModalHeaderComponent
------------------------

Type: Component

Selector: `sky-modal-header`

Specifies a header for the modal.

 SkyModalContentComponent
-------------------------

Type: Component

Selector: `sky-modal-content`

Specifies content to display in the modal's body.

 SkyModalFooterComponent
------------------------

Type: Component

Selector: `sky-modal-footer`

Specifies content to display in the modal's footer.

 SkyModalIsDirtyDirective
-------------------------

Type: Directive

Selector: `sky-modal[isDirty]`

Provides a way to mark a modal as "dirty" and displays a confirmation message when a user closes the modal without saving.

### Inputs

#### `isDirty: boolean`

Required

Whether the user edited an input on the modal.

Default: `false`

 SkyModalService
----------------

Type: Service

A service that launches modals.

### Methods

#### `open(component: any, config?: any[] | SkyModalConfigurationInterface): SkyModalInstance`

Opens a modal using the specified component.

#### Parameters

##### `component: any`

Determines the component to render.

##### `config?: any[] | SkyModalConfigurationInterface`

Specifies configuration options for the modal.

#### Returns

`SkyModalInstance`

 SkyModalConfigurationInterface
-------------------------------

Type: Interface

Specifies configuration options for creating a modal.

    interface SkyModalConfigurationInterface {
      ariaDescribedBy?: string;
      ariaLabelledBy?: string;
      ariaRole?: string;
      fullPage?: boolean;
      helpKey?: string;
      providers?: StaticProvider[];
      size?: string;
      tiledBody?: boolean;
      wrapperClass?: string;
    }

### Properties

#### `ariaDescribedBy?: string`

Warning: **Deprecated.** Set `headingText` on the modal component instead.

The HTML element ID of the element that describes the modal. This sets the modal's `aria-describedby` attribute to provide a text equivalent for [to support accessibility](/skyux/learn/accessibility.md). The description typically includes text on the modal but not on items that users interact with, such as buttons and forms. If you do not specify an ID, the default description is the content of the `sky-modal-content` component. For more information about the `aria-describedby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-describedby).

#### `ariaLabelledBy?: string`

Warning: **Deprecated.** Set `headingText` on the modal component instead.

The HTML element ID of the element that labels the modal. This sets the `aria-labelledby` attribute for the modal to provide a text equivalent for [to support accessibility](/skyux/learn/accessibility.md). This is typically a header element, and if you do not specify an ID, the default value is the content of the `sky-modal-header` component. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `ariaRole?: string`

The ARIA role for the modal [to support accessibility](/skyux/learn/accessibility.md) by indicating how the modal functions and what it controls. For information about how an ARIA role indicates what an item represents on a web page, see the [WAI-ARIA roles model](http://www.w3.org/WAI/PF/aria/#roles). By default, modals set the ARIA role to `dialog`.

#### `fullPage?: boolean`

Whether to display the modal full screen. This property defaults to `false`.

#### `helpKey?: string`

Warning: **Deprecated.** To display a help button in the modal header, set either the `helpKey` or `helpPopoverContent` inputs on the modal component.

The `helpKey` string. This property displays the help inline button in the modal header. When users click this button, the `helpOpened` event broadcasts the `helpKey` parameter. Blackbaud developers can use the Help Widget, which is for internal Blackbaud use only, to [display help content in a flyout panel](https://docs.blackbaud.com/bb-help-docs/components/modal-header).

#### `providers?: StaticProvider[]`

An array property of `providers`. In Angular, a provider is something that can create or deliver a service. This property can be used to pass context values from the component that launches the modal to the modal component.

#### `size?: string`

The size for the modal. The valid options are `small`, `medium`, and `large`. This property defaults to `medium`.

#### `tiledBody?: boolean`

Warning: **Deprecated.** Tiles inside modals are no longer a recommended design pattern. For complex forms, use [sectioned forms](/skyux/components/sectioned-form.md) or [other form containers](/skyux/design/guidelines/form-design.md) instead.

Whether the modal uses tiles. When set to `true`, the modal's background switches to `$sky-background-color-neutral-light` and tile headings are styled as subsection headings. This property defaults to `false`.

#### `wrapperClass?: string`

The CSS class to add to the modal, such as `ag-custom-component-popup` for using a modal as part of a cell editor in Data Entry Grid.

 SkyModalInstance
-----------------

Type: Class

### Properties

#### `componentInstance: any`

A direct reference to the provided component's class.

#### `beforeClose: Observable<SkyModalBeforeCloseHandler>`

An event that the modal instance emits when it is about to close. It emits a `SkyModalBeforeCloseHandler` object with a `closeModal` method that closes the modal. If a subscription exists for this event, the modal does not close until the subscriber calls the `closeModal` method.

#### `closed: Observable<SkyModalCloseArgs>`

An event that the modal instance emits when it closes. It emits a `SkyModalCloseArgs` object with a `data` property that includes data passed from users on close or save and a `reason` property that indicates whether the modal was saved or closed without saving. The `reason` property accepts any string value. Common examples include `"cancel"`, `"close"`, and `"save"`.

#### `helpOpened: Observable<string>`

An event that the modal instance emits when users click the help inline button. If a `helpKey` parameter was specified, the `helpOpened` event broadcasts the `helpKey`.

### Methods

#### `cancel(result?: any): void`

Closes the modal instance with `reason="cancel"`.

#### Parameters

##### `result?: any`

Specifies an object to emit to subscribers of the `closed` event of the modal instance. The `SkyModalInstance` provider can be injected into a component's constructor so that this cancel function can be called from a button in the `sky-modal-footer`.

#### Returns

`void`

#### `close(result?: any, reason?: string, ignoreBeforeClose?: boolean): void`

Closes the modal instance.

#### Parameters

##### `result?: any`

Specifies an object to emit to subscribers of the `closed` event of the modal instance. The `SkyModalInstance` provider can be injected into a component's constructor so that this `close` function can be called from a button in the `sky-modal-footer`.

##### `reason?: string`

Specifies the reason for the modal closing, with the default reason of `"close"`.

##### `ignoreBeforeClose?: boolean`

Indicates whether to ignore the modal instance's `beforeClose` event.

#### Returns

`void`

#### `openHelp(helpKey: string): void`

Triggers the `helpOpened` event that broadcasts a `helpKey` parameter to open when users click the help inline button.

#### Parameters

##### `helpKey: string`

Specifies a string to emit to subscribers of the modal instance's `helpOpened` event. Consumers can inject the `SkyModalInstance` provider into a component's constructor to call the `openHelp` function in the modal template.

#### Returns

`void`

#### `save(result?: any): void`

Closes the modal instance with `reason="save"`.

#### Parameters

##### `result?: any`

Specifies an object to emit to subscribers of the `closed` event of the modal instance. The `SkyModalInstance` provider can be injected into a component's constructor so that this `save` function can be called from a button in `the sky-modal-footer`.

#### Returns

`void`

#### `scrollContentToTop(): void`

Scrolls the modal content area to the top of its scrollable area.

#### Returns

`void`

 SkyModalCloseArgs
------------------

Type: Class

Contains an object with the data passed from users when a modal is closed and the reason that the modal was closed.

### Properties

#### `data: any`

The data passed from users when the modal is closed.

#### `reason: string | undefined`

The reason the modal was closed. Options include `"close"`, `"save"`, and `"cancel"`.

 SkyModalBeforeCloseHandler
---------------------------

Type: Class

Properties about the modal close action and a method to close the modal.

### Properties

#### `closeArgs: SkyModalCloseArgs`

The object that would be emitted by a modal's `closed` event. This object can be used to determine whether to prompt the user for confirmation, such as when the user closes a modal form after entering data.

#### `closeModal: () => void`

Function to call to close the modal. Neglecting to call this function effectively cancels the close modal action.

 SkyModalError
--------------

Type: Interface

Contains an object with properties for displaying form-level errors in the modal.

    interface SkyModalError {
      message: string;
    }

### Properties

#### `message: string`

The error message to display.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyModalHarness
----------------

Type: Class

`import { SkyModalHarness } from '@skyux/modals/testing';`

Harness for interacting with a modal component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getAriaDescribedBy(): Promise<null | string>`

Gets the aria-describedBy property of the modal.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledBy(): Promise<null | string>`

Gets the aria-labelledBy property of the modal.

#### Returns

`Promise<null | string>`

#### `getAriaRole(): Promise<null | string>`

Gets the role of the modal.

#### Returns

`Promise<null | string>`

#### `getHeadingText(): Promise<undefined | string>`

Gets the modal's heading text.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getSize(): Promise<string>`

Gets the modal size.

#### Returns

`Promise<string>`

#### `getWrapperClass(): Promise<undefined | string>`

Gets the wrapper class of the modal.

#### Returns

`Promise<undefined | string>`

#### `isDirty(): Promise<boolean>`

Whether the modal has [SkyModalIsDirtyDirective](/skyux/components/modal?docs-active-tab=design#class_sky-modal-is-dirty-directive.md).isDirty set to dirty.

#### Returns

`Promise<boolean>`

#### `isFullPage(): Promise<boolean>`

Whether the modal is full page.

#### Returns

`Promise<boolean>`

#### `SkyModalHarness.with(filters: SkyModalHarnessFilters): HarnessPredicate<SkyModalHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyModalHarness` that meets certain criteria

#### Parameters

##### `filters: SkyModalHarnessFilters`

#### Returns

`HarnessPredicate<SkyModalHarness>`

 SkyModalHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyModalHarness](/skyux/components/modal?docs-active-tab=design#class_sky-modal-harness.md) instances.

    interface SkyModalHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyModalTestingModule
----------------------

Type: Module

`import { SkyModalTestingModule } from '@skyux/modals/testing';`

Configures the `SkyModalTestingController` as the implementation for the `SkyModalService`.

 SkyModalTestingController
--------------------------

Type: Class

A controller to be injected into tests, which mocks the modal service and handles interactions with modal instances. For testing interactions with the modal component itself, use the `SkyModalHarness`.

### Methods

#### `closeTopModal(args?: SkyModalCloseArgs): void`

Closes the topmost modal with the provided arguments.

#### Parameters

##### `args?: SkyModalCloseArgs`

Arguments to pass to the modal's close event.

#### Returns

`void`

#### `expectCount(value: number): void`

Throws if the provided value does not match the number of open modals.

#### Parameters

##### `value: number`

#### Returns

`void`

#### `expectNone(): void`

Throws if modals are open.

#### Returns

`void`

#### `expectOpen(component: Type<TComponent>): void`

Throws if the given criteria does not match the topmost open modal.

#### Parameters

##### `component: Type<TComponent>`

#### Returns

`void`

# Development

                  Skip to Main Content

 Modal
=====

The modal component and service launch modals in a consistent way in SKY UX applications.

 Usage
------

### Use modals when

Use modals when tasks are functionally modal and users must finish them before doing anything else.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-usage1.0e224e8642a8fa0c41c003b676a33edd.png)

Do use modals when users must complete tasks before they proceed.

Use modals when displaying forms inline would lead to substantial content shifting or require users to scroll to complete the forms.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-usage2.c67fa46f712a5f337db5830372683c8f.png)

Do use modals when displaying long forms.

Use modals when users need to add records from paginated lists or infinite scroll lists.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-usage3.d6aaf7ab43a0797fd54430f333e81b8f.png)

Do use modals to add records from paginated lists or infinite scroll lists.

Use large modals when housing a large component that best utilizes the horizontal space, such as [sectioned forms](/skyux/components/sectioned-form.md) or [wizards](/skyux/components/tabs-wizard.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-usage4.db94507f627c55a790ef44efe3b65d9d.png)

Do use large modals with sectioned forms and wizards.

### Use full-screen modals when

Use full-screen modals when users usually perform self-contained tasks in a large viewport, and a full-screen modal can optimize the use of space.

Use full-screen modals when forms display feedback based on user entries or selections. For example, forms may display running totals or preview emails as they are constructed.

Use full-screen modals when forms support complex tasks for lists of objects such as filling out report cards for a class.

Use full-screen modals when tasks include subtasks that users need to complete in context.

 Anatomy
--------

1

Heading

2

Content

3

Footer

4

Buttons

5

Help inline button (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-anatomy.dcee172de54b95db0670744b5f9b5d47.png)

 Options
--------

### Help inline button

When you need to supplement a modal header with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the header to invoke contextual user assistance.

 Behavior and states
--------------------

### Unsaved data

If users close a modal before saving their changes, use `SkyModalIsDirtyDirective` to warn them about losing the unsaved data with a [confirmation dialog](/skyux/components/confirm.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/modal-close-confirm.f756192fa9878ff34249421a094c4aa3.png)

 Content
--------

### Modal title text

Modal titles use sentence-case capitalization and the following format:

<Verb> <direct object> for <indirect object>

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-with-object.2c333b6186ad2d87652c5b2643e86e0f.png)

If there is not an indirect object or the user is the implied indirect object, exclude it:

<Verb> <direct object>

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-without-object.faba5d6e76fe17417ec29341cfbdc897.png)

### Buttons in the modal action bar

Button labels should clearly indicate the actions that occur when users select buttons. For example, use **Save** as the standard label for actions where users save information to the database, but use **Submit** or another alternative if you need to indicate that an action sends data somewhere else. Make sure to use the label that is most accurate for all contexts. For example, while **Cancel** and **Close** both indicate that actions close modals, **Cancel** more clearly indicates that the actions do not save changes to modals; **Cancel** should be used in most cases.

Use a [primary button](/skyux/components/button.md) for the most important action that users take, secondary buttons for less important actions, and a link button for the **Cancel** action. Follow the [form design guidelines](/skyux/design/guidelines/form-design.md) and disable the primary action until all required inputs have valid values. If a modal has only one action, use the [confirm component](/skyux/components/confirm.md) instead.

 Related information
--------------------

### Components

*   [Buttons](/skyux/components/button.md)
*   [Confirmation dialog](/skyux/components/confirm.md)
*   [Input box](/skyux/components/input-box.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/modals`[View in NPM](https://www.npmjs.com/package/@skyux/modals) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/modals/src/lib/modules/modal/modal.module.ts#L25) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/modals`Copy None found.

 SkyModalModule
---------------

Type: Module

`import { SkyModalModule } from '@skyux/modals';`

 SkyModalComponent
------------------

Type: Component

Selector: `sky-modal`

Provides a common look-and-feel for modal content with options to display a common modal header, specify body content, and display a common modal footer and buttons.

### Inputs

#### `formErrors: SkyModalError[] | undefined`

A list of form-level errors to display to the user.

#### `headingText: string | undefined`

The text to display as the modal's heading.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to the modal header. Clicking the button invokes global help as configured by the application. This property only applies when `headingText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to the modal header. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `layout: InputSignal<"none" | "fit">`

 SkyModalHeaderComponent
------------------------

Type: Component

Selector: `sky-modal-header`

Specifies a header for the modal.

 SkyModalContentComponent
-------------------------

Type: Component

Selector: `sky-modal-content`

Specifies content to display in the modal's body.

 SkyModalFooterComponent
------------------------

Type: Component

Selector: `sky-modal-footer`

Specifies content to display in the modal's footer.

 SkyModalIsDirtyDirective
-------------------------

Type: Directive

Selector: `sky-modal[isDirty]`

Provides a way to mark a modal as "dirty" and displays a confirmation message when a user closes the modal without saving.

### Inputs

#### `isDirty: boolean`

Required

Whether the user edited an input on the modal.

Default: `false`

 SkyModalService
----------------

Type: Service

A service that launches modals.

### Methods

#### `open(component: any, config?: any[] | SkyModalConfigurationInterface): SkyModalInstance`

Opens a modal using the specified component.

#### Parameters

##### `component: any`

Determines the component to render.

##### `config?: any[] | SkyModalConfigurationInterface`

Specifies configuration options for the modal.

#### Returns

`SkyModalInstance`

 SkyModalConfigurationInterface
-------------------------------

Type: Interface

Specifies configuration options for creating a modal.

    interface SkyModalConfigurationInterface {
      ariaDescribedBy?: string;
      ariaLabelledBy?: string;
      ariaRole?: string;
      fullPage?: boolean;
      helpKey?: string;
      providers?: StaticProvider[];
      size?: string;
      tiledBody?: boolean;
      wrapperClass?: string;
    }

### Properties

#### `ariaDescribedBy?: string`

Warning: **Deprecated.** Set `headingText` on the modal component instead.

The HTML element ID of the element that describes the modal. This sets the modal's `aria-describedby` attribute to provide a text equivalent for [to support accessibility](/skyux/learn/accessibility.md). The description typically includes text on the modal but not on items that users interact with, such as buttons and forms. If you do not specify an ID, the default description is the content of the `sky-modal-content` component. For more information about the `aria-describedby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-describedby).

#### `ariaLabelledBy?: string`

Warning: **Deprecated.** Set `headingText` on the modal component instead.

The HTML element ID of the element that labels the modal. This sets the `aria-labelledby` attribute for the modal to provide a text equivalent for [to support accessibility](/skyux/learn/accessibility.md). This is typically a header element, and if you do not specify an ID, the default value is the content of the `sky-modal-header` component. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `ariaRole?: string`

The ARIA role for the modal [to support accessibility](/skyux/learn/accessibility.md) by indicating how the modal functions and what it controls. For information about how an ARIA role indicates what an item represents on a web page, see the [WAI-ARIA roles model](http://www.w3.org/WAI/PF/aria/#roles). By default, modals set the ARIA role to `dialog`.

#### `fullPage?: boolean`

Whether to display the modal full screen. This property defaults to `false`.

#### `helpKey?: string`

Warning: **Deprecated.** To display a help button in the modal header, set either the `helpKey` or `helpPopoverContent` inputs on the modal component.

The `helpKey` string. This property displays the help inline button in the modal header. When users click this button, the `helpOpened` event broadcasts the `helpKey` parameter. Blackbaud developers can use the Help Widget, which is for internal Blackbaud use only, to [display help content in a flyout panel](https://docs.blackbaud.com/bb-help-docs/components/modal-header).

#### `providers?: StaticProvider[]`

An array property of `providers`. In Angular, a provider is something that can create or deliver a service. This property can be used to pass context values from the component that launches the modal to the modal component.

#### `size?: string`

The size for the modal. The valid options are `small`, `medium`, and `large`. This property defaults to `medium`.

#### `tiledBody?: boolean`

Warning: **Deprecated.** Tiles inside modals are no longer a recommended design pattern. For complex forms, use [sectioned forms](/skyux/components/sectioned-form.md) or [other form containers](/skyux/design/guidelines/form-design.md) instead.

Whether the modal uses tiles. When set to `true`, the modal's background switches to `$sky-background-color-neutral-light` and tile headings are styled as subsection headings. This property defaults to `false`.

#### `wrapperClass?: string`

The CSS class to add to the modal, such as `ag-custom-component-popup` for using a modal as part of a cell editor in Data Entry Grid.

 SkyModalInstance
-----------------

Type: Class

### Properties

#### `componentInstance: any`

A direct reference to the provided component's class.

#### `beforeClose: Observable<SkyModalBeforeCloseHandler>`

An event that the modal instance emits when it is about to close. It emits a `SkyModalBeforeCloseHandler` object with a `closeModal` method that closes the modal. If a subscription exists for this event, the modal does not close until the subscriber calls the `closeModal` method.

#### `closed: Observable<SkyModalCloseArgs>`

An event that the modal instance emits when it closes. It emits a `SkyModalCloseArgs` object with a `data` property that includes data passed from users on close or save and a `reason` property that indicates whether the modal was saved or closed without saving. The `reason` property accepts any string value. Common examples include `"cancel"`, `"close"`, and `"save"`.

#### `helpOpened: Observable<string>`

An event that the modal instance emits when users click the help inline button. If a `helpKey` parameter was specified, the `helpOpened` event broadcasts the `helpKey`.

### Methods

#### `cancel(result?: any): void`

Closes the modal instance with `reason="cancel"`.

#### Parameters

##### `result?: any`

Specifies an object to emit to subscribers of the `closed` event of the modal instance. The `SkyModalInstance` provider can be injected into a component's constructor so that this cancel function can be called from a button in the `sky-modal-footer`.

#### Returns

`void`

#### `close(result?: any, reason?: string, ignoreBeforeClose?: boolean): void`

Closes the modal instance.

#### Parameters

##### `result?: any`

Specifies an object to emit to subscribers of the `closed` event of the modal instance. The `SkyModalInstance` provider can be injected into a component's constructor so that this `close` function can be called from a button in the `sky-modal-footer`.

##### `reason?: string`

Specifies the reason for the modal closing, with the default reason of `"close"`.

##### `ignoreBeforeClose?: boolean`

Indicates whether to ignore the modal instance's `beforeClose` event.

#### Returns

`void`

#### `openHelp(helpKey: string): void`

Triggers the `helpOpened` event that broadcasts a `helpKey` parameter to open when users click the help inline button.

#### Parameters

##### `helpKey: string`

Specifies a string to emit to subscribers of the modal instance's `helpOpened` event. Consumers can inject the `SkyModalInstance` provider into a component's constructor to call the `openHelp` function in the modal template.

#### Returns

`void`

#### `save(result?: any): void`

Closes the modal instance with `reason="save"`.

#### Parameters

##### `result?: any`

Specifies an object to emit to subscribers of the `closed` event of the modal instance. The `SkyModalInstance` provider can be injected into a component's constructor so that this `save` function can be called from a button in `the sky-modal-footer`.

#### Returns

`void`

#### `scrollContentToTop(): void`

Scrolls the modal content area to the top of its scrollable area.

#### Returns

`void`

 SkyModalCloseArgs
------------------

Type: Class

Contains an object with the data passed from users when a modal is closed and the reason that the modal was closed.

### Properties

#### `data: any`

The data passed from users when the modal is closed.

#### `reason: string | undefined`

The reason the modal was closed. Options include `"close"`, `"save"`, and `"cancel"`.

 SkyModalBeforeCloseHandler
---------------------------

Type: Class

Properties about the modal close action and a method to close the modal.

### Properties

#### `closeArgs: SkyModalCloseArgs`

The object that would be emitted by a modal's `closed` event. This object can be used to determine whether to prompt the user for confirmation, such as when the user closes a modal form after entering data.

#### `closeModal: () => void`

Function to call to close the modal. Neglecting to call this function effectively cancels the close modal action.

 SkyModalError
--------------

Type: Interface

Contains an object with properties for displaying form-level errors in the modal.

    interface SkyModalError {
      message: string;
    }

### Properties

#### `message: string`

The error message to display.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyModalHarness
----------------

Type: Class

`import { SkyModalHarness } from '@skyux/modals/testing';`

Harness for interacting with a modal component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getAriaDescribedBy(): Promise<null | string>`

Gets the aria-describedBy property of the modal.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledBy(): Promise<null | string>`

Gets the aria-labelledBy property of the modal.

#### Returns

`Promise<null | string>`

#### `getAriaRole(): Promise<null | string>`

Gets the role of the modal.

#### Returns

`Promise<null | string>`

#### `getHeadingText(): Promise<undefined | string>`

Gets the modal's heading text.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getSize(): Promise<string>`

Gets the modal size.

#### Returns

`Promise<string>`

#### `getWrapperClass(): Promise<undefined | string>`

Gets the wrapper class of the modal.

#### Returns

`Promise<undefined | string>`

#### `isDirty(): Promise<boolean>`

Whether the modal has [SkyModalIsDirtyDirective](/skyux/components/modal?docs-active-tab=development#class_sky-modal-is-dirty-directive.md).isDirty set to dirty.

#### Returns

`Promise<boolean>`

#### `isFullPage(): Promise<boolean>`

Whether the modal is full page.

#### Returns

`Promise<boolean>`

#### `SkyModalHarness.with(filters: SkyModalHarnessFilters): HarnessPredicate<SkyModalHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyModalHarness` that meets certain criteria

#### Parameters

##### `filters: SkyModalHarnessFilters`

#### Returns

`HarnessPredicate<SkyModalHarness>`

 SkyModalHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyModalHarness](/skyux/components/modal?docs-active-tab=development#class_sky-modal-harness.md) instances.

    interface SkyModalHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyModalTestingModule
----------------------

Type: Module

`import { SkyModalTestingModule } from '@skyux/modals/testing';`

Configures the `SkyModalTestingController` as the implementation for the `SkyModalService`.

 SkyModalTestingController
--------------------------

Type: Class

A controller to be injected into tests, which mocks the modal service and handles interactions with modal instances. For testing interactions with the modal component itself, use the `SkyModalHarness`.

### Methods

#### `closeTopModal(args?: SkyModalCloseArgs): void`

Closes the topmost modal with the provided arguments.

#### Parameters

##### `args?: SkyModalCloseArgs`

Arguments to pass to the modal's close event.

#### Returns

`void`

#### `expectCount(value: number): void`

Throws if the provided value does not match the number of open modals.

#### Parameters

##### `value: number`

#### Returns

`void`

#### `expectNone(): void`

Throws if modals are open.

#### Returns

`void`

#### `expectOpen(component: Type<TComponent>): void`

Throws if the given criteria does not match the topmost open modal.

#### Parameters

##### `component: Type<TComponent>`

#### Returns

`void`

# Examples

                    Skip to Main Content

 Modal
=====

The modal component and service launch modals in a consistent way in SKY UX applications.Usage
------

### Use modals when

Use modals when tasks are functionally modal and users must finish them before doing anything else.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-usage1.0e224e8642a8fa0c41c003b676a33edd.png)

Do use modals when users must complete tasks before they proceed.

Use modals when displaying forms inline would lead to substantial content shifting or require users to scroll to complete the forms.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-usage2.c67fa46f712a5f337db5830372683c8f.png)

Do use modals when displaying long forms.

Use modals when users need to add records from paginated lists or infinite scroll lists.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-usage3.d6aaf7ab43a0797fd54430f333e81b8f.png)

Do use modals to add records from paginated lists or infinite scroll lists.

Use large modals when housing a large component that best utilizes the horizontal space, such as [sectioned forms](/skyux/components/sectioned-form.md) or [wizards](/skyux/components/tabs-wizard.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-usage4.db94507f627c55a790ef44efe3b65d9d.png)

Do use large modals with sectioned forms and wizards.

### Use full-screen modals when

Use full-screen modals when users usually perform self-contained tasks in a large viewport, and a full-screen modal can optimize the use of space.

Use full-screen modals when forms display feedback based on user entries or selections. For example, forms may display running totals or preview emails as they are constructed.

Use full-screen modals when forms support complex tasks for lists of objects such as filling out report cards for a class.

Use full-screen modals when tasks include subtasks that users need to complete in context.

 Anatomy
--------

1

Heading

2

Content

3

Footer

4

Buttons

5

Help inline button (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-anatomy.dcee172de54b95db0670744b5f9b5d47.png)

 Options
--------

### Help inline button

When you need to supplement a modal header with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the header to invoke contextual user assistance.

 Behavior and states
--------------------

### Unsaved data

If users close a modal before saving their changes, use `SkyModalIsDirtyDirective` to warn them about losing the unsaved data with a [confirmation dialog](/skyux/components/confirm.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/modal-close-confirm.f756192fa9878ff34249421a094c4aa3.png)

 Content
--------

### Modal title text

Modal titles use sentence-case capitalization and the following format:

<Verb> <direct object> for <indirect object>

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-with-object.2c333b6186ad2d87652c5b2643e86e0f.png)

If there is not an indirect object or the user is the implied indirect object, exclude it:

<Verb> <direct object>

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-without-object.faba5d6e76fe17417ec29341cfbdc897.png)

### Buttons in the modal action bar

Button labels should clearly indicate the actions that occur when users select buttons. For example, use **Save** as the standard label for actions where users save information to the database, but use **Submit** or another alternative if you need to indicate that an action sends data somewhere else. Make sure to use the label that is most accurate for all contexts. For example, while **Cancel** and **Close** both indicate that actions close modals, **Cancel** more clearly indicates that the actions do not save changes to modals; **Cancel** should be used in most cases.

Use a [primary button](/skyux/components/button.md) for the most important action that users take, secondary buttons for less important actions, and a link button for the **Cancel** action. Follow the [form design guidelines](/skyux/design/guidelines/form-design.md) and disable the primary action until all required inputs have valid values. If a modal has only one action, use the [confirm component](/skyux/components/confirm.md) instead.

 Related information
--------------------

### Components

*   [Buttons](/skyux/components/button.md)
*   [Confirmation dialog](/skyux/components/confirm.md)
*   [Input box](/skyux/components/input-box.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/modals`[View in NPM](https://www.npmjs.com/package/@skyux/modals) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/modals/src/lib/modules/modal/modal.module.ts#L25) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/modals`Copy None found.

 SkyModalModule
---------------

Type: Module

`import { SkyModalModule } from '@skyux/modals';`

 SkyModalComponent
------------------

Type: Component

Selector: `sky-modal`

Provides a common look-and-feel for modal content with options to display a common modal header, specify body content, and display a common modal footer and buttons.

### Inputs

#### `formErrors: SkyModalError[] | undefined`

A list of form-level errors to display to the user.

#### `headingText: string | undefined`

The text to display as the modal's heading.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to the modal header. Clicking the button invokes global help as configured by the application. This property only applies when `headingText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to the modal header. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `layout: InputSignal<"none" | "fit">`

 SkyModalHeaderComponent
------------------------

Type: Component

Selector: `sky-modal-header`

Specifies a header for the modal.

 SkyModalContentComponent
-------------------------

Type: Component

Selector: `sky-modal-content`

Specifies content to display in the modal's body.

 SkyModalFooterComponent
------------------------

Type: Component

Selector: `sky-modal-footer`

Specifies content to display in the modal's footer.

 SkyModalIsDirtyDirective
-------------------------

Type: Directive

Selector: `sky-modal[isDirty]`

Provides a way to mark a modal as "dirty" and displays a confirmation message when a user closes the modal without saving.

### Inputs

#### `isDirty: boolean`

Required

Whether the user edited an input on the modal.

Default: `false`

 SkyModalService
----------------

Type: Service

A service that launches modals.

### Methods

#### `open(component: any, config?: any[] | SkyModalConfigurationInterface): SkyModalInstance`

Opens a modal using the specified component.

#### Parameters

##### `component: any`

Determines the component to render.

##### `config?: any[] | SkyModalConfigurationInterface`

Specifies configuration options for the modal.

#### Returns

`SkyModalInstance`

 SkyModalConfigurationInterface
-------------------------------

Type: Interface

Specifies configuration options for creating a modal.

    interface SkyModalConfigurationInterface {
      ariaDescribedBy?: string;
      ariaLabelledBy?: string;
      ariaRole?: string;
      fullPage?: boolean;
      helpKey?: string;
      providers?: StaticProvider[];
      size?: string;
      tiledBody?: boolean;
      wrapperClass?: string;
    }

### Properties

#### `ariaDescribedBy?: string`

Warning: **Deprecated.** Set `headingText` on the modal component instead.

The HTML element ID of the element that describes the modal. This sets the modal's `aria-describedby` attribute to provide a text equivalent for [to support accessibility](/skyux/learn/accessibility.md). The description typically includes text on the modal but not on items that users interact with, such as buttons and forms. If you do not specify an ID, the default description is the content of the `sky-modal-content` component. For more information about the `aria-describedby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-describedby).

#### `ariaLabelledBy?: string`

Warning: **Deprecated.** Set `headingText` on the modal component instead.

The HTML element ID of the element that labels the modal. This sets the `aria-labelledby` attribute for the modal to provide a text equivalent for [to support accessibility](/skyux/learn/accessibility.md). This is typically a header element, and if you do not specify an ID, the default value is the content of the `sky-modal-header` component. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `ariaRole?: string`

The ARIA role for the modal [to support accessibility](/skyux/learn/accessibility.md) by indicating how the modal functions and what it controls. For information about how an ARIA role indicates what an item represents on a web page, see the [WAI-ARIA roles model](http://www.w3.org/WAI/PF/aria/#roles). By default, modals set the ARIA role to `dialog`.

#### `fullPage?: boolean`

Whether to display the modal full screen. This property defaults to `false`.

#### `helpKey?: string`

Warning: **Deprecated.** To display a help button in the modal header, set either the `helpKey` or `helpPopoverContent` inputs on the modal component.

The `helpKey` string. This property displays the help inline button in the modal header. When users click this button, the `helpOpened` event broadcasts the `helpKey` parameter. Blackbaud developers can use the Help Widget, which is for internal Blackbaud use only, to [display help content in a flyout panel](https://docs.blackbaud.com/bb-help-docs/components/modal-header).

#### `providers?: StaticProvider[]`

An array property of `providers`. In Angular, a provider is something that can create or deliver a service. This property can be used to pass context values from the component that launches the modal to the modal component.

#### `size?: string`

The size for the modal. The valid options are `small`, `medium`, and `large`. This property defaults to `medium`.

#### `tiledBody?: boolean`

Warning: **Deprecated.** Tiles inside modals are no longer a recommended design pattern. For complex forms, use [sectioned forms](/skyux/components/sectioned-form.md) or [other form containers](/skyux/design/guidelines/form-design.md) instead.

Whether the modal uses tiles. When set to `true`, the modal's background switches to `$sky-background-color-neutral-light` and tile headings are styled as subsection headings. This property defaults to `false`.

#### `wrapperClass?: string`

The CSS class to add to the modal, such as `ag-custom-component-popup` for using a modal as part of a cell editor in Data Entry Grid.

 SkyModalInstance
-----------------

Type: Class

### Properties

#### `componentInstance: any`

A direct reference to the provided component's class.

#### `beforeClose: Observable<SkyModalBeforeCloseHandler>`

An event that the modal instance emits when it is about to close. It emits a `SkyModalBeforeCloseHandler` object with a `closeModal` method that closes the modal. If a subscription exists for this event, the modal does not close until the subscriber calls the `closeModal` method.

#### `closed: Observable<SkyModalCloseArgs>`

An event that the modal instance emits when it closes. It emits a `SkyModalCloseArgs` object with a `data` property that includes data passed from users on close or save and a `reason` property that indicates whether the modal was saved or closed without saving. The `reason` property accepts any string value. Common examples include `"cancel"`, `"close"`, and `"save"`.

#### `helpOpened: Observable<string>`

An event that the modal instance emits when users click the help inline button. If a `helpKey` parameter was specified, the `helpOpened` event broadcasts the `helpKey`.

### Methods

#### `cancel(result?: any): void`

Closes the modal instance with `reason="cancel"`.

#### Parameters

##### `result?: any`

Specifies an object to emit to subscribers of the `closed` event of the modal instance. The `SkyModalInstance` provider can be injected into a component's constructor so that this cancel function can be called from a button in the `sky-modal-footer`.

#### Returns

`void`

#### `close(result?: any, reason?: string, ignoreBeforeClose?: boolean): void`

Closes the modal instance.

#### Parameters

##### `result?: any`

Specifies an object to emit to subscribers of the `closed` event of the modal instance. The `SkyModalInstance` provider can be injected into a component's constructor so that this `close` function can be called from a button in the `sky-modal-footer`.

##### `reason?: string`

Specifies the reason for the modal closing, with the default reason of `"close"`.

##### `ignoreBeforeClose?: boolean`

Indicates whether to ignore the modal instance's `beforeClose` event.

#### Returns

`void`

#### `openHelp(helpKey: string): void`

Triggers the `helpOpened` event that broadcasts a `helpKey` parameter to open when users click the help inline button.

#### Parameters

##### `helpKey: string`

Specifies a string to emit to subscribers of the modal instance's `helpOpened` event. Consumers can inject the `SkyModalInstance` provider into a component's constructor to call the `openHelp` function in the modal template.

#### Returns

`void`

#### `save(result?: any): void`

Closes the modal instance with `reason="save"`.

#### Parameters

##### `result?: any`

Specifies an object to emit to subscribers of the `closed` event of the modal instance. The `SkyModalInstance` provider can be injected into a component's constructor so that this `save` function can be called from a button in `the sky-modal-footer`.

#### Returns

`void`

#### `scrollContentToTop(): void`

Scrolls the modal content area to the top of its scrollable area.

#### Returns

`void`

 SkyModalCloseArgs
------------------

Type: Class

Contains an object with the data passed from users when a modal is closed and the reason that the modal was closed.

### Properties

#### `data: any`

The data passed from users when the modal is closed.

#### `reason: string | undefined`

The reason the modal was closed. Options include `"close"`, `"save"`, and `"cancel"`.

 SkyModalBeforeCloseHandler
---------------------------

Type: Class

Properties about the modal close action and a method to close the modal.

### Properties

#### `closeArgs: SkyModalCloseArgs`

The object that would be emitted by a modal's `closed` event. This object can be used to determine whether to prompt the user for confirmation, such as when the user closes a modal form after entering data.

#### `closeModal: () => void`

Function to call to close the modal. Neglecting to call this function effectively cancels the close modal action.

 SkyModalError
--------------

Type: Interface

Contains an object with properties for displaying form-level errors in the modal.

    interface SkyModalError {
      message: string;
    }

### Properties

#### `message: string`

The error message to display.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyModalHarness
----------------

Type: Class

`import { SkyModalHarness } from '@skyux/modals/testing';`

Harness for interacting with a modal component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getAriaDescribedBy(): Promise<null | string>`

Gets the aria-describedBy property of the modal.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledBy(): Promise<null | string>`

Gets the aria-labelledBy property of the modal.

#### Returns

`Promise<null | string>`

#### `getAriaRole(): Promise<null | string>`

Gets the role of the modal.

#### Returns

`Promise<null | string>`

#### `getHeadingText(): Promise<undefined | string>`

Gets the modal's heading text.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getSize(): Promise<string>`

Gets the modal size.

#### Returns

`Promise<string>`

#### `getWrapperClass(): Promise<undefined | string>`

Gets the wrapper class of the modal.

#### Returns

`Promise<undefined | string>`

#### `isDirty(): Promise<boolean>`

Whether the modal has [SkyModalIsDirtyDirective](/skyux/components/modal?docs-active-tab=examples#class_sky-modal-is-dirty-directive.md).isDirty set to dirty.

#### Returns

`Promise<boolean>`

#### `isFullPage(): Promise<boolean>`

Whether the modal is full page.

#### Returns

`Promise<boolean>`

#### `SkyModalHarness.with(filters: SkyModalHarnessFilters): HarnessPredicate<SkyModalHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyModalHarness` that meets certain criteria

#### Parameters

##### `filters: SkyModalHarnessFilters`

#### Returns

`HarnessPredicate<SkyModalHarness>`

 SkyModalHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyModalHarness](/skyux/components/modal?docs-active-tab=examples#class_sky-modal-harness.md) instances.

    interface SkyModalHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyModalTestingModule
----------------------

Type: Module

`import { SkyModalTestingModule } from '@skyux/modals/testing';`

Configures the `SkyModalTestingController` as the implementation for the `SkyModalService`.

 SkyModalTestingController
--------------------------

Type: Class

A controller to be injected into tests, which mocks the modal service and handles interactions with modal instances. For testing interactions with the modal component itself, use the `SkyModalHarness`.

### Methods

#### `closeTopModal(args?: SkyModalCloseArgs): void`

Closes the topmost modal with the provided arguments.

#### Parameters

##### `args?: SkyModalCloseArgs`

Arguments to pass to the modal's close event.

#### Returns

`void`

#### `expectCount(value: number): void`

Throws if the provided value does not match the number of open modals.

#### Parameters

##### `value: number`

#### Returns

`void`

#### `expectNone(): void`

Throws if modals are open.

#### Returns

`void`

#### `expectOpen(component: Type<TComponent>): void`

Throws if the given criteria does not match the topmost open modal.

#### Parameters

##### `component: Type<TComponent>`

#### Returns

`void`

### Modal with basic setup, tested with controller

Edit in StackBlitz

Open modal

Show code

Copy

    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import {
      SkyModalTestingController,
      SkyModalTestingModule,
    } from '@skyux/modals/testing';
    
    import { ModalsModalBasicWithControllerExampleComponent } from './example.component';
    import { ModalComponent } from './modal.component';
    
    describe('Modal example using testing controller', () => {
      function setupTest(): {
        fixture: ComponentFixture<ModalsModalBasicWithControllerExampleComponent>;
        modalController: SkyModalTestingController;
      } {
        const fixture = TestBed.createComponent(
          ModalsModalBasicWithControllerExampleComponent,
        );
        const modalController = TestBed.inject(SkyModalTestingController);
    
        return { fixture, modalController };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [
            SkyModalTestingModule,
            ModalsModalBasicWithControllerExampleComponent,
          ],
        });
      });
    
      it('should expect a modal to be open, close it, and expect none', () => {
        const { fixture, modalController } = setupTest();
    
        fixture.componentInstance.openModal();
        fixture.detectChanges();
    
        modalController.expectCount(1);
        modalController.expectOpen(ModalComponent);
        modalController.closeTopModal({
          data: {},
          reason: 'save',
        });
        modalController.expectNone();
      });
    });
Copy

    import { Injectable } from '@angular/core';
    import {
      SkyHelpOpenArgs,
      SkyHelpService,
      SkyHelpUpdateArgs,
    } from '@skyux/core';
    
    /**
     * This is a mock implementation of the help service. In a production scenario,
     * the `SkyHelpService` would be provided at the application root.
     * @see: https://developer.blackbaud.com/skyux/learn/develop/global-help
     */
    @Injectable({ providedIn: 'root' })
    export class MyHelpService extends SkyHelpService {
      public override openHelp(args?: SkyHelpOpenArgs): void {
        if (args) {
          console.error(`Open help panel to key: ${args.helpKey}`);
        }
      }
    
      public override updateHelp(args: SkyHelpUpdateArgs): void {
        if ('helpKey' in args) {
          console.error(`help key update: ${args.helpKey}`);
        }
    
        if ('pageDefaultHelpKey' in args) {
          console.error(`page default help key update: ${args.pageDefaultHelpKey}`);
        }
      }
    }
Copy

    import { Injectable } from '@angular/core';
    
    @Injectable()
    export class ModalContext {
      public data:
        | {
            value1: string;
          }
        | undefined;
    }
Copy

    import { Component, inject } from '@angular/core';
    import {
      FormBuilder,
      FormControl,
      FormGroup,
      FormsModule,
      ReactiveFormsModule,
    } from '@angular/forms';
    import { SkyInputBoxModule } from '@skyux/forms';
    import { SkyModalInstance, SkyModalModule } from '@skyux/modals';
    
    import { ModalContext } from './modal-context';
    
    @Component({
      imports: [
        FormsModule,
        ReactiveFormsModule,
        SkyInputBoxModule,
        SkyModalModule,
      ],
      template: `
        <form [formGroup]="exampleForm" (submit)="saveForm()">
          <sky-modal headingText="Modal title" helpKey="help.html">
            <sky-modal-content>
              <sky-input-box>
                <input formControlName="value1" type="text" />
              </sky-input-box>
            </sky-modal-content>
            <sky-modal-footer>
              <button class="sky-btn sky-btn-primary" type="submit">Save</button>
              <button
                class="sky-btn sky-btn-link"
                type="button"
                (click)="cancelForm()"
              >
                Cancel
              </button>
            </sky-modal-footer>
          </sky-modal>
        </form>
      `,
    })
    export class ModalComponent {
      protected exampleForm: FormGroup<{
        value1: FormControl<string | null | undefined>;
      }>;
    
      readonly #context = inject(ModalContext);
      readonly #instance = inject(SkyModalInstance);
    
      constructor() {
        this.exampleForm = inject(FormBuilder).group({
          value1: new FormControl(this.#context.data?.value1),
        });
      }
    
      protected cancelForm(): void {
        this.#instance.cancel();
      }
    
      protected saveForm(): void {
        this.#instance.save({});
      }
    }

Copy

    import { Component, OnDestroy, inject } from '@angular/core';
    import { SkyHelpService } from '@skyux/core';
    import {
      SkyModalError,
      SkyModalInstance,
      SkyModalService,
    } from '@skyux/modals';
    
    import { MyHelpService } from './help.service';
    import { ModalContext } from './modal-context';
    import { ModalComponent } from './modal.component';
    
    /**
     * @title Modal with basic setup, tested with controller
     */
    @Component({
      selector: 'app-modals-modal-basic-with-controller-example',
      standalone: true,
      template: `<button
        class="sky-btn sky-btn-default"
        type="button"
        (click)="openModal()"
      >
        Open modal
      </button>`,
    })
    export class ModalsModalBasicWithControllerExampleComponent
      implements OnDestroy
    {
      public hasErrors = false;
    
      protected errors: SkyModalError[] = [];
    
      readonly #instances: SkyModalInstance[] = [];
      readonly #modalSvc = inject(SkyModalService);
    
      public ngOnDestroy(): void {
        this.#instances.forEach((i) => {
          i.close();
        });
      }
    
      public openModal(): void {
        const instance = this.#modalSvc.open(ModalComponent, {
          providers: [
            {
              provide: ModalContext,
              useValue: { value1: 'Hello!' },
            },
            // NOTE: The help service is normally provided at the application root, but
            // it is added here purely for demonstration purposes.
            // See: https://developer.blackbaud.com/skyux/learn/develop/global-help
            {
              provide: SkyHelpService,
              useExisting: MyHelpService,
            },
          ],
        });
    
        instance.beforeClose.subscribe((handler) => {
          if (this.hasErrors && handler.closeArgs.reason !== 'cancel') {
            this.errors = [
              {
                message: 'Something bad happened.',
              },
            ];
          } else {
            handler.closeModal();
          }
        });
    
        this.#instances.push(instance);
      }
    }
### Modal with basic setup, tested with harness

Edit in StackBlitz

Open modal example

Show code

Copy

    import { ModalDemoData } from './data';
    
    export class ModalDemoContext {
      constructor(public data: ModalDemoData) {}
    }
Copy

    import { Injectable } from '@angular/core';
    
    import { Observable, of } from 'rxjs';
    import { delay } from 'rxjs/operators';
    
    import { ModalDemoData } from './data';
    
    @Injectable({
      providedIn: 'root',
    })
    export class ModalDemoDataService {
      #data: ModalDemoData = {
        value1: 'Hello world',
      };
    
      public load(): Observable<ModalDemoData> {
        // Simulate a network request to get data.
        return of(this.#data).pipe(delay(1000));
      }
    
      public save(data: ModalDemoData): Observable<ModalDemoData> {
        this.#data = data;
    
        // Simulate a network request to save data.
        return of(this.#data).pipe(delay(1000));
      }
    }
Copy

    export interface ModalDemoData {
      value1?: string | null;
    }
Copy

    <button
      class="sky-btn sky-btn-default"
      type="button"
      (click)="onOpenModalClick()"
    >
      Open modal example
    </button>
    @if (exampleValue) {
      <div>The user entered {{ exampleValue }}</div>
    }
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyWaitService } from '@skyux/indicators';
    import { SkyModalHarness } from '@skyux/modals/testing';
    
    import { Observable, of } from 'rxjs';
    
    import { ModalDemoDataService } from './data.service';
    import { ModalsModalBasicWithHarnessExampleComponent } from './example.component';
    
    class mockWaitSvc {
      public blockingWrap(data: unknown): Observable<unknown> {
        return of(data);
      }
    }
    
    describe('Basic modal', () => {
      async function setupTest(): Promise<{
        modalHarness: SkyModalHarness;
        fixture: ComponentFixture<ModalsModalBasicWithHarnessExampleComponent>;
      }> {
        const fixture = TestBed.createComponent(
          ModalsModalBasicWithHarnessExampleComponent,
        );
        fixture.componentInstance.onOpenModalClick();
        fixture.detectChanges();
    
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
        const modalHarness = await loader.getHarness(
          SkyModalHarness.with({
            dataSkyId: 'modal-example',
          }),
        );
    
        return { modalHarness, fixture };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [
            ModalsModalBasicWithHarnessExampleComponent,
            NoopAnimationsModule,
          ],
          providers: [
            {
              provide: SkyWaitService,
              useClass: mockWaitSvc,
            },
            ModalDemoDataService,
          ],
        });
      });
    
      it('should open the correct modal', async () => {
        const { modalHarness, fixture } = await setupTest();
    
        fixture.detectChanges();
    
        await expectAsync(modalHarness.getAriaRole()).toBeResolvedTo('dialog');
        await expectAsync(modalHarness.getSize()).toBeResolvedTo('medium');
        await expectAsync(modalHarness.isFullPage()).toBeResolvedTo(false);
        await expectAsync(modalHarness.getHeadingText()).toBeResolvedTo(
          'Modal title',
        );
    
        await modalHarness.clickHelpInline();
    
        await expectAsync(modalHarness.getHelpPopoverContent()).toBeResolvedTo(
          'Use the help inline component to invoke contextual user assistance.',
        );
      });
    });
Copy

    <form [formGroup]="exampleForm" (submit)="saveForm()">
      <sky-modal
        data-sky-id="modal-example"
        headingText="Modal title"
        helpPopoverContent="Use the help inline component to invoke contextual user assistance."
        [isDirty]="exampleForm.dirty"
      >
        <sky-modal-content>
          <sky-input-box labelText="An input inside a modal">
            <input formControlName="value1" type="text" />
          </sky-input-box>
        </sky-modal-content>
        <sky-modal-footer>
          <button class="sky-btn sky-btn-primary" type="submit">Save</button>
          <button class="sky-btn sky-btn-link" type="button" (click)="cancelForm()">
            Cancel
          </button>
        </sky-modal-footer>
      </sky-modal>
    </form>
Copy

    import { Component, inject } from '@angular/core';
    import { FormControl, FormGroup, ReactiveFormsModule } from '@angular/forms';
    import { SkyInputBoxModule } from '@skyux/forms';
    import { SkyWaitService } from '@skyux/indicators';
    import { SkyModalInstance, SkyModalModule } from '@skyux/modals';
    
    import { ModalDemoContext } from './context';
    import { ModalDemoDataService } from './data.service';
    
    @Component({
      selector: 'app-modal',
      templateUrl: './modal.component.html',
      imports: [ReactiveFormsModule, SkyInputBoxModule, SkyModalModule],
    })
    export class ModalComponent {
      protected exampleForm: FormGroup<{
        value1: FormControl<string | null | undefined>;
      }>;
    
      readonly #context = inject(ModalDemoContext);
      readonly #dataSvc = inject(ModalDemoDataService);
      readonly #instance = inject(SkyModalInstance);
      readonly #waitSvc = inject(SkyWaitService);
    
      constructor() {
        this.exampleForm = new FormGroup({
          value1: new FormControl(this.#context.data.value1),
        });
      }
    
      protected saveForm(): void {
        // Use the data service to save the data.
    
        this.#waitSvc
          .blockingWrap(this.#dataSvc.save(this.exampleForm.value))
          .subscribe((data) => {
            // Notify the modal instance that data was saved and return the saved data.
            this.#instance.save(data);
          });
      }
    
      protected cancelForm(): void {
        this.#instance.cancel();
      }
    }

Copy

    import { Component, OnDestroy, inject } from '@angular/core';
    import { SkyWaitService } from '@skyux/indicators';
    import { SkyModalConfigurationInterface, SkyModalService } from '@skyux/modals';
    
    import { Subject } from 'rxjs';
    import { takeUntil } from 'rxjs/operators';
    
    import { ModalDemoContext } from './context';
    import { ModalDemoData } from './data';
    import { ModalDemoDataService } from './data.service';
    import { ModalComponent } from './modal.component';
    
    /**
     * @title Modal with basic setup, tested with harness
     */
    @Component({
      standalone: true,
      selector: 'app-modals-modal-basic-with-harness-example',
      templateUrl: './example.component.html',
    })
    export class ModalsModalBasicWithHarnessExampleComponent implements OnDestroy {
      protected modalSize = 'medium';
      protected exampleValue: string | null | undefined;
    
      #ngUnsubscribe = new Subject<void>();
    
      readonly #dataSvc = inject(ModalDemoDataService);
      readonly #modalSvc = inject(SkyModalService);
      readonly #waitSvc = inject(SkyWaitService);
    
      public ngOnDestroy(): void {
        this.#ngUnsubscribe.next();
        this.#ngUnsubscribe.complete();
      }
    
      public onOpenModalClick(): void {
        // Display a blocking wait while data is loaded from the data service.
        this.#waitSvc
          .blockingWrap(this.#dataSvc.load())
          .pipe(takeUntil(this.#ngUnsubscribe))
          .subscribe((data) => {
            const options: SkyModalConfigurationInterface = {
              providers: [
                {
                  provide: ModalDemoContext,
                  useValue: new ModalDemoContext(data),
                },
              ],
              size: this.modalSize,
            };
    
            // Show the modal after data is loaded.
            const instance = this.#modalSvc.open(ModalComponent, options);
    
            instance.closed.subscribe((result) => {
              if (result.reason === 'save') {
                // Display the updated value.
                this.exampleValue = (result.data as ModalDemoData).value1;
              }
            });
          });
      }
    }
### Modal with a help key

Edit in StackBlitz

Open modal example

Show code

Copy

    import { ModalDemoData } from './data';
    
    export class ModalDemoContext {
      constructor(public data: ModalDemoData) {}
    }
Copy

    import { Injectable } from '@angular/core';
    
    import { Observable, of } from 'rxjs';
    import { delay } from 'rxjs/operators';
    
    import { ModalDemoData } from './data';
    
    @Injectable({
      providedIn: 'root',
    })
    export class ModalDemoDataService {
      #data: ModalDemoData = {
        value1: 'Hello world',
      };
    
      public load(): Observable<ModalDemoData> {
        // Simulate a network request to get data.
        return of(this.#data).pipe(delay(1000));
      }
    
      public save(data: ModalDemoData): Observable<ModalDemoData> {
        this.#data = data;
    
        // Simulate a network request to save data.
        return of(this.#data).pipe(delay(1000));
      }
    }
Copy

    export interface ModalDemoData {
      value1?: string | null;
    }
Copy

    <button
      class="sky-btn sky-btn-default"
      type="button"
      (click)="onOpenModalClick()"
    >
      Open modal example
    </button>
    @if (exampleValue) {
      <div>The user entered {{ exampleValue }}</div>
    }
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import {
      SkyHelpTestingController,
      SkyHelpTestingModule,
    } from '@skyux/core/testing';
    import { SkyWaitService } from '@skyux/indicators';
    import { SkyModalHarness } from '@skyux/modals/testing';
    
    import { Observable, of } from 'rxjs';
    
    import { ModalDemoDataService } from './data.service';
    import { ModalsModalBasicWithHarnessHelpKeyExampleComponent } from './example.component';
    
    class mockWaitSvc {
      public blockingWrap(data: unknown): Observable<unknown> {
        return of(data);
      }
    }
    
    describe('Basic modal', () => {
      async function setupTest(): Promise<{
        modalHarness: SkyModalHarness;
        fixture: ComponentFixture<ModalsModalBasicWithHarnessHelpKeyExampleComponent>;
        helpController: SkyHelpTestingController;
      }> {
        const fixture = TestBed.createComponent(
          ModalsModalBasicWithHarnessHelpKeyExampleComponent,
        );
        fixture.componentInstance.onOpenModalClick();
        fixture.detectChanges();
    
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
        const modalHarness = await loader.getHarness(
          SkyModalHarness.with({
            dataSkyId: 'modal-example',
          }),
        );
        const helpController = TestBed.inject(SkyHelpTestingController);
    
        return { modalHarness, fixture, helpController };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [
            ModalsModalBasicWithHarnessHelpKeyExampleComponent,
            NoopAnimationsModule,
            SkyHelpTestingModule,
          ],
          providers: [
            {
              provide: SkyWaitService,
              useClass: mockWaitSvc,
            },
            ModalDemoDataService,
          ],
        });
      });
    
      it('should have the correct help key', async () => {
        const { modalHarness, helpController } = await setupTest();
    
        await modalHarness.clickHelpInline();
    
        helpController.expectCurrentHelpKey('modal-help');
      });
    });
Copy

    <form [formGroup]="exampleForm" (submit)="saveForm()">
      <sky-modal
        data-sky-id="modal-example"
        headingText="Modal title"
        helpKey="modal-help"
        [isDirty]="exampleForm.dirty"
      >
        <sky-modal-content>
          <sky-input-box labelText="An input inside a modal">
            <input formControlName="value1" type="text" />
          </sky-input-box>
        </sky-modal-content>
        <sky-modal-footer>
          <button class="sky-btn sky-btn-primary" type="submit">Save</button>
          <button class="sky-btn sky-btn-link" type="button" (click)="cancelForm()">
            Cancel
          </button>
        </sky-modal-footer>
      </sky-modal>
    </form>
Copy

    import { Component, inject } from '@angular/core';
    import { FormControl, FormGroup, ReactiveFormsModule } from '@angular/forms';
    import { SkyInputBoxModule } from '@skyux/forms';
    import { SkyWaitService } from '@skyux/indicators';
    import { SkyModalInstance, SkyModalModule } from '@skyux/modals';
    
    import { ModalDemoContext } from './context';
    import { ModalDemoDataService } from './data.service';
    
    @Component({
      selector: 'app-modal',
      templateUrl: './modal.component.html',
      imports: [ReactiveFormsModule, SkyInputBoxModule, SkyModalModule],
    })
    export class ModalComponent {
      protected exampleForm: FormGroup<{
        value1: FormControl<string | null | undefined>;
      }>;
    
      readonly #context = inject(ModalDemoContext);
      readonly #dataSvc = inject(ModalDemoDataService);
      readonly #instance = inject(SkyModalInstance);
      readonly #waitSvc = inject(SkyWaitService);
    
      constructor() {
        this.exampleForm = new FormGroup({
          value1: new FormControl(this.#context.data.value1),
        });
      }
    
      protected saveForm(): void {
        // Use the data service to save the data.
    
        this.#waitSvc
          .blockingWrap(this.#dataSvc.save(this.exampleForm.value))
          .subscribe((data) => {
            // Notify the modal instance that data was saved and return the saved data.
            this.#instance.save(data);
          });
      }
    
      protected cancelForm(): void {
        this.#instance.cancel();
      }
    }

Copy

    import { Component, OnDestroy, inject } from '@angular/core';
    import { SkyWaitService } from '@skyux/indicators';
    import { SkyModalConfigurationInterface, SkyModalService } from '@skyux/modals';
    
    import { Subject } from 'rxjs';
    import { takeUntil } from 'rxjs/operators';
    
    import { ModalDemoContext } from './context';
    import { ModalDemoData } from './data';
    import { ModalDemoDataService } from './data.service';
    import { ModalComponent } from './modal.component';
    
    /**
     * @title Modal with a help key
     */
    @Component({
      standalone: true,
      selector: 'app-modals-modal-basic-with-harness-help-key-example',
      templateUrl: './example.component.html',
    })
    export class ModalsModalBasicWithHarnessHelpKeyExampleComponent
      implements OnDestroy
    {
      protected modalSize = 'medium';
      protected exampleValue: string | null | undefined;
    
      #ngUnsubscribe = new Subject<void>();
    
      readonly #dataSvc = inject(ModalDemoDataService);
      readonly #modalSvc = inject(SkyModalService);
      readonly #waitSvc = inject(SkyWaitService);
    
      public ngOnDestroy(): void {
        this.#ngUnsubscribe.next();
        this.#ngUnsubscribe.complete();
      }
    
      public onOpenModalClick(): void {
        // Display a blocking wait while data is loaded from the data service.
        this.#waitSvc
          .blockingWrap(this.#dataSvc.load())
          .pipe(takeUntil(this.#ngUnsubscribe))
          .subscribe((data) => {
            const options: SkyModalConfigurationInterface = {
              providers: [
                {
                  provide: ModalDemoContext,
                  useValue: new ModalDemoContext(data),
                },
              ],
              size: this.modalSize,
            };
    
            // Show the modal after data is loaded.
            const instance = this.#modalSvc.open(ModalComponent, options);
    
            instance.closed.subscribe((result) => {
              if (result.reason === 'save') {
                // Display the updated value.
                this.exampleValue = (result.data as ModalDemoData).value1;
              }
            });
          });
      }
    }
### Modal with form errors

Edit in StackBlitz

Open modal example

Show code

Copy

    import { ModalDemoData } from './data';
    
    export class ModalDemoContext {
      constructor(public data: ModalDemoData) {}
    }
Copy

    import { Injectable } from '@angular/core';
    
    import { Observable, of } from 'rxjs';
    import { delay } from 'rxjs/operators';
    
    import { ModalDemoData } from './data';
    
    @Injectable({
      providedIn: 'root',
    })
    export class ModalDemoDataService {
      #data: ModalDemoData = {
        value1: 'Hello world',
      };
    
      public load(): Observable<ModalDemoData> {
        // Simulate a network request to get data.
        return of(this.#data).pipe(delay(1000));
      }
    
      public save(data: ModalDemoData, error = false): Observable<ModalDemoData> {
        if (!error) {
          this.#data = data;
        }
    
        // Simulate a network request to save data.
        return of(this.#data).pipe(delay(1000));
      }
    }
Copy

    export interface ModalDemoData {
      value1?: string | null;
    }
Copy

    <button
      class="sky-btn sky-btn-default"
      type="button"
      (click)="onOpenModalClick()"
    >
      Open modal example
    </button>
    @if (exampleValue) {
      <div>The user entered {{ exampleValue }}</div>
    }
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { SkyWaitService } from '@skyux/indicators';
    import { SkyModalHarness } from '@skyux/modals/testing';
    
    import { Observable, of } from 'rxjs';
    
    import { ModalDemoDataService } from './data.service';
    import { ModalsModalWithErrorExampleComponent } from './example.component';
    
    class mockWaitSvc {
      public blockingWrap(data: unknown): Observable<unknown> {
        return of(data);
      }
    }
    
    describe('Basic modal', () => {
      async function setupTest(): Promise<{
        modalHarness: SkyModalHarness;
        fixture: ComponentFixture<ModalsModalWithErrorExampleComponent>;
      }> {
        const fixture = TestBed.createComponent(
          ModalsModalWithErrorExampleComponent,
        );
        fixture.componentInstance.onOpenModalClick();
        fixture.detectChanges();
    
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
        const modalHarness = await loader.getHarness(
          SkyModalHarness.with({
            dataSkyId: 'modal-example',
          }),
        );
    
        return { modalHarness, fixture };
      }
    
      beforeEach(() => {
        TestBed.configureTestingModule({
          imports: [ModalsModalWithErrorExampleComponent],
          providers: [
            {
              provide: SkyWaitService,
              useClass: mockWaitSvc,
            },
            ModalDemoDataService,
          ],
        });
      });
    
      it('should open the correct modal', async () => {
        const { modalHarness, fixture } = await setupTest();
    
        fixture.detectChanges();
    
        await expectAsync(modalHarness.getAriaRole()).toBeResolvedTo('dialog');
        await expectAsync(modalHarness.getSize()).toBeResolvedTo('medium');
        await expectAsync(modalHarness.isFullPage()).toBeResolvedTo(false);
      });
    });
Copy

    <form [formGroup]="exampleForm" (submit)="saveForm()">
      <sky-modal
        data-sky-id="modal-example"
        headingText="Modal title"
        [isDirty]="exampleForm.dirty"
        [formErrors]="errors"
      >
        <sky-modal-content>
          <sky-input-box labelText="An input inside a modal">
            <input formControlName="value1" type="text" />
          </sky-input-box>
        </sky-modal-content>
        <sky-modal-footer>
          <button class="sky-btn sky-btn-primary" type="submit">Save</button>
          <button
            class="sky-btn sky-btn-link"
            type="button"
            (click)="saveFormWithFormError()"
          >
            Save form with an error
          </button>
          <button class="sky-btn sky-btn-link" type="button" (click)="cancelForm()">
            Cancel
          </button>
        </sky-modal-footer>
      </sky-modal>
    </form>
Copy

    import { Component, inject } from '@angular/core';
    import { FormControl, FormGroup, ReactiveFormsModule } from '@angular/forms';
    import { SkyInputBoxModule } from '@skyux/forms';
    import { SkyWaitService } from '@skyux/indicators';
    import { SkyModalError, SkyModalInstance, SkyModalModule } from '@skyux/modals';
    
    import { ModalDemoContext } from './context';
    import { ModalDemoDataService } from './data.service';
    
    @Component({
      selector: 'app-modal',
      templateUrl: './modal.component.html',
      imports: [ReactiveFormsModule, SkyInputBoxModule, SkyModalModule],
    })
    export class ModalComponent {
      protected exampleForm: FormGroup<{
        value1: FormControl<string | null | undefined>;
      }>;
    
      readonly #context = inject(ModalDemoContext);
      readonly #dataSvc = inject(ModalDemoDataService);
      readonly #instance = inject(SkyModalInstance);
      readonly #waitSvc = inject(SkyWaitService);
    
      public errors: SkyModalError[] = [];
    
      constructor() {
        this.exampleForm = new FormGroup({
          value1: new FormControl(this.#context.data.value1),
        });
      }
    
      protected saveForm(): void {
        // Use the data service to save the data.
    
        this.#waitSvc
          .blockingWrap(this.#dataSvc.save(this.exampleForm.value))
          .subscribe((data) => {
            // Notify the modal instance that data was saved and return the saved data.
            this.#instance.save(data);
          });
      }
    
      protected saveFormWithFormError(): void {
        // Use the data service to save the data.
    
        this.#waitSvc
          .blockingWrap(this.#dataSvc.save(this.exampleForm.value, true))
          .subscribe(() => {
            this.errors = [{ message: 'There was an error saving the form.' }];
          });
      }
    
      protected cancelForm(): void {
        this.#instance.cancel();
      }
    }

Copy

    import { Component, OnDestroy, inject } from '@angular/core';
    import { SkyWaitService } from '@skyux/indicators';
    import { SkyModalConfigurationInterface, SkyModalService } from '@skyux/modals';
    
    import { Subject } from 'rxjs';
    import { takeUntil } from 'rxjs/operators';
    
    import { ModalDemoContext } from './context';
    import { ModalDemoData } from './data';
    import { ModalDemoDataService } from './data.service';
    import { ModalComponent } from './modal.component';
    
    /**
     * @title Modal with form errors
     */
    @Component({
      standalone: true,
      selector: 'app-modals-modal-with-error-example',
      templateUrl: './example.component.html',
    })
    export class ModalsModalWithErrorExampleComponent implements OnDestroy {
      protected modalSize = 'medium';
      protected exampleValue: string | null | undefined;
    
      #ngUnsubscribe = new Subject<void>();
    
      readonly #dataSvc = inject(ModalDemoDataService);
      readonly #modalSvc = inject(SkyModalService);
      readonly #waitSvc = inject(SkyWaitService);
    
      public ngOnDestroy(): void {
        this.#ngUnsubscribe.next();
        this.#ngUnsubscribe.complete();
      }
    
      public onOpenModalClick(): void {
        // Display a blocking wait while data is loaded from the data service.
        this.#waitSvc
          .blockingWrap(this.#dataSvc.load())
          .pipe(takeUntil(this.#ngUnsubscribe))
          .subscribe((data) => {
            const options: SkyModalConfigurationInterface = {
              providers: [
                {
                  provide: ModalDemoContext,
                  useValue: new ModalDemoContext(data),
                },
              ],
              size: this.modalSize,
            };
    
            // Show the modal after data is loaded.
            const instance = this.#modalSvc.open(ModalComponent, options);
    
            instance.closed.subscribe((result) => {
              if (result.reason === 'save') {
                // Display the updated value.
                this.exampleValue = (result.data as ModalDemoData).value1;
              }
            });
          });
      }
    }

# Testing

                  Skip to Main Content

 Modal
=====

The modal component and service launch modals in a consistent way in SKY UX applications.

 Usage
------

### Use modals when

Use modals when tasks are functionally modal and users must finish them before doing anything else.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-usage1.0e224e8642a8fa0c41c003b676a33edd.png)

Do use modals when users must complete tasks before they proceed.

Use modals when displaying forms inline would lead to substantial content shifting or require users to scroll to complete the forms.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-usage2.c67fa46f712a5f337db5830372683c8f.png)

Do use modals when displaying long forms.

Use modals when users need to add records from paginated lists or infinite scroll lists.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-usage3.d6aaf7ab43a0797fd54430f333e81b8f.png)

Do use modals to add records from paginated lists or infinite scroll lists.

Use large modals when housing a large component that best utilizes the horizontal space, such as [sectioned forms](/skyux/components/sectioned-form.md) or [wizards](/skyux/components/tabs-wizard.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-usage4.db94507f627c55a790ef44efe3b65d9d.png)

Do use large modals with sectioned forms and wizards.

### Use full-screen modals when

Use full-screen modals when users usually perform self-contained tasks in a large viewport, and a full-screen modal can optimize the use of space.

Use full-screen modals when forms display feedback based on user entries or selections. For example, forms may display running totals or preview emails as they are constructed.

Use full-screen modals when forms support complex tasks for lists of objects such as filling out report cards for a class.

Use full-screen modals when tasks include subtasks that users need to complete in context.

 Anatomy
--------

1

Heading

2

Content

3

Footer

4

Buttons

5

Help inline button (optional)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-anatomy.dcee172de54b95db0670744b5f9b5d47.png)

 Options
--------

### Help inline button

When you need to supplement a modal header with additional information but don't require persistent inline help, you can place a [help inline button](/skyux/components/help-inline.md) beside the header to invoke contextual user assistance.

 Behavior and states
--------------------

### Unsaved data

If users close a modal before saving their changes, use `SkyModalIsDirtyDirective` to warn them about losing the unsaved data with a [confirmation dialog](/skyux/components/confirm.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/formdesign/modal-close-confirm.f756192fa9878ff34249421a094c4aa3.png)

 Content
--------

### Modal title text

Modal titles use sentence-case capitalization and the following format:

<Verb> <direct object> for <indirect object>

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-with-object.2c333b6186ad2d87652c5b2643e86e0f.png)

If there is not an indirect object or the user is the implied indirect object, exclude it:

<Verb> <direct object>

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/modal/modal-without-object.faba5d6e76fe17417ec29341cfbdc897.png)

### Buttons in the modal action bar

Button labels should clearly indicate the actions that occur when users select buttons. For example, use **Save** as the standard label for actions where users save information to the database, but use **Submit** or another alternative if you need to indicate that an action sends data somewhere else. Make sure to use the label that is most accurate for all contexts. For example, while **Cancel** and **Close** both indicate that actions close modals, **Cancel** more clearly indicates that the actions do not save changes to modals; **Cancel** should be used in most cases.

Use a [primary button](/skyux/components/button.md) for the most important action that users take, secondary buttons for less important actions, and a link button for the **Cancel** action. Follow the [form design guidelines](/skyux/design/guidelines/form-design.md) and disable the primary action until all required inputs have valid values. If a modal has only one action, use the [confirm component](/skyux/components/confirm.md) instead.

 Related information
--------------------

### Components

*   [Buttons](/skyux/components/button.md)
*   [Confirmation dialog](/skyux/components/confirm.md)
*   [Input box](/skyux/components/input-box.md)

### Guidelines

*   [Form design](/skyux/design/guidelines/form-design.md)

 Installation
-------------

NPM package

`@skyux/modals`[View in NPM](https://www.npmjs.com/package/@skyux/modals) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/modals/src/lib/modules/modal/modal.module.ts#L25) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/modals`Copy None found.

 SkyModalModule
---------------

Type: Module

`import { SkyModalModule } from '@skyux/modals';`

 SkyModalComponent
------------------

Type: Component

Selector: `sky-modal`

Provides a common look-and-feel for modal content with options to display a common modal header, specify body content, and display a common modal footer and buttons.

### Inputs

#### `formErrors: SkyModalError[] | undefined`

A list of form-level errors to display to the user.

#### `headingText: string | undefined`

The text to display as the modal's heading.

#### `helpKey: string | undefined`

A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to the modal header. Clicking the button invokes global help as configured by the application. This property only applies when `headingText` is also specified.

#### `helpPopoverContent: string | TemplateRef<unknown> | undefined`

The content of the help popover. When specified along with `headingText`, a [help inline](/skyux/components/help-inline.md) button is added to the modal header. The help inline button displays a [popover](/skyux/components/popover.md) when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.

#### `helpPopoverTitle: string | undefined`

The title of the help popover. This property only applies when `helpPopoverContent` is also specified.

#### `layout: InputSignal<"none" | "fit">`

 SkyModalHeaderComponent
------------------------

Type: Component

Selector: `sky-modal-header`

Specifies a header for the modal.

 SkyModalContentComponent
-------------------------

Type: Component

Selector: `sky-modal-content`

Specifies content to display in the modal's body.

 SkyModalFooterComponent
------------------------

Type: Component

Selector: `sky-modal-footer`

Specifies content to display in the modal's footer.

 SkyModalIsDirtyDirective
-------------------------

Type: Directive

Selector: `sky-modal[isDirty]`

Provides a way to mark a modal as "dirty" and displays a confirmation message when a user closes the modal without saving.

### Inputs

#### `isDirty: boolean`

Required

Whether the user edited an input on the modal.

Default: `false`

 SkyModalService
----------------

Type: Service

A service that launches modals.

### Methods

#### `open(component: any, config?: any[] | SkyModalConfigurationInterface): SkyModalInstance`

Opens a modal using the specified component.

#### Parameters

##### `component: any`

Determines the component to render.

##### `config?: any[] | SkyModalConfigurationInterface`

Specifies configuration options for the modal.

#### Returns

`SkyModalInstance`

 SkyModalConfigurationInterface
-------------------------------

Type: Interface

Specifies configuration options for creating a modal.

    interface SkyModalConfigurationInterface {
      ariaDescribedBy?: string;
      ariaLabelledBy?: string;
      ariaRole?: string;
      fullPage?: boolean;
      helpKey?: string;
      providers?: StaticProvider[];
      size?: string;
      tiledBody?: boolean;
      wrapperClass?: string;
    }

### Properties

#### `ariaDescribedBy?: string`

Warning: **Deprecated.** Set `headingText` on the modal component instead.

The HTML element ID of the element that describes the modal. This sets the modal's `aria-describedby` attribute to provide a text equivalent for [to support accessibility](/skyux/learn/accessibility.md). The description typically includes text on the modal but not on items that users interact with, such as buttons and forms. If you do not specify an ID, the default description is the content of the `sky-modal-content` component. For more information about the `aria-describedby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-describedby).

#### `ariaLabelledBy?: string`

Warning: **Deprecated.** Set `headingText` on the modal component instead.

The HTML element ID of the element that labels the modal. This sets the `aria-labelledby` attribute for the modal to provide a text equivalent for [to support accessibility](/skyux/learn/accessibility.md). This is typically a header element, and if you do not specify an ID, the default value is the content of the `sky-modal-header` component. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `ariaRole?: string`

The ARIA role for the modal [to support accessibility](/skyux/learn/accessibility.md) by indicating how the modal functions and what it controls. For information about how an ARIA role indicates what an item represents on a web page, see the [WAI-ARIA roles model](http://www.w3.org/WAI/PF/aria/#roles). By default, modals set the ARIA role to `dialog`.

#### `fullPage?: boolean`

Whether to display the modal full screen. This property defaults to `false`.

#### `helpKey?: string`

Warning: **Deprecated.** To display a help button in the modal header, set either the `helpKey` or `helpPopoverContent` inputs on the modal component.

The `helpKey` string. This property displays the help inline button in the modal header. When users click this button, the `helpOpened` event broadcasts the `helpKey` parameter. Blackbaud developers can use the Help Widget, which is for internal Blackbaud use only, to [display help content in a flyout panel](https://docs.blackbaud.com/bb-help-docs/components/modal-header).

#### `providers?: StaticProvider[]`

An array property of `providers`. In Angular, a provider is something that can create or deliver a service. This property can be used to pass context values from the component that launches the modal to the modal component.

#### `size?: string`

The size for the modal. The valid options are `small`, `medium`, and `large`. This property defaults to `medium`.

#### `tiledBody?: boolean`

Warning: **Deprecated.** Tiles inside modals are no longer a recommended design pattern. For complex forms, use [sectioned forms](/skyux/components/sectioned-form.md) or [other form containers](/skyux/design/guidelines/form-design.md) instead.

Whether the modal uses tiles. When set to `true`, the modal's background switches to `$sky-background-color-neutral-light` and tile headings are styled as subsection headings. This property defaults to `false`.

#### `wrapperClass?: string`

The CSS class to add to the modal, such as `ag-custom-component-popup` for using a modal as part of a cell editor in Data Entry Grid.

 SkyModalInstance
-----------------

Type: Class

### Properties

#### `componentInstance: any`

A direct reference to the provided component's class.

#### `beforeClose: Observable<SkyModalBeforeCloseHandler>`

An event that the modal instance emits when it is about to close. It emits a `SkyModalBeforeCloseHandler` object with a `closeModal` method that closes the modal. If a subscription exists for this event, the modal does not close until the subscriber calls the `closeModal` method.

#### `closed: Observable<SkyModalCloseArgs>`

An event that the modal instance emits when it closes. It emits a `SkyModalCloseArgs` object with a `data` property that includes data passed from users on close or save and a `reason` property that indicates whether the modal was saved or closed without saving. The `reason` property accepts any string value. Common examples include `"cancel"`, `"close"`, and `"save"`.

#### `helpOpened: Observable<string>`

An event that the modal instance emits when users click the help inline button. If a `helpKey` parameter was specified, the `helpOpened` event broadcasts the `helpKey`.

### Methods

#### `cancel(result?: any): void`

Closes the modal instance with `reason="cancel"`.

#### Parameters

##### `result?: any`

Specifies an object to emit to subscribers of the `closed` event of the modal instance. The `SkyModalInstance` provider can be injected into a component's constructor so that this cancel function can be called from a button in the `sky-modal-footer`.

#### Returns

`void`

#### `close(result?: any, reason?: string, ignoreBeforeClose?: boolean): void`

Closes the modal instance.

#### Parameters

##### `result?: any`

Specifies an object to emit to subscribers of the `closed` event of the modal instance. The `SkyModalInstance` provider can be injected into a component's constructor so that this `close` function can be called from a button in the `sky-modal-footer`.

##### `reason?: string`

Specifies the reason for the modal closing, with the default reason of `"close"`.

##### `ignoreBeforeClose?: boolean`

Indicates whether to ignore the modal instance's `beforeClose` event.

#### Returns

`void`

#### `openHelp(helpKey: string): void`

Triggers the `helpOpened` event that broadcasts a `helpKey` parameter to open when users click the help inline button.

#### Parameters

##### `helpKey: string`

Specifies a string to emit to subscribers of the modal instance's `helpOpened` event. Consumers can inject the `SkyModalInstance` provider into a component's constructor to call the `openHelp` function in the modal template.

#### Returns

`void`

#### `save(result?: any): void`

Closes the modal instance with `reason="save"`.

#### Parameters

##### `result?: any`

Specifies an object to emit to subscribers of the `closed` event of the modal instance. The `SkyModalInstance` provider can be injected into a component's constructor so that this `save` function can be called from a button in `the sky-modal-footer`.

#### Returns

`void`

#### `scrollContentToTop(): void`

Scrolls the modal content area to the top of its scrollable area.

#### Returns

`void`

 SkyModalCloseArgs
------------------

Type: Class

Contains an object with the data passed from users when a modal is closed and the reason that the modal was closed.

### Properties

#### `data: any`

The data passed from users when the modal is closed.

#### `reason: string | undefined`

The reason the modal was closed. Options include `"close"`, `"save"`, and `"cancel"`.

 SkyModalBeforeCloseHandler
---------------------------

Type: Class

Properties about the modal close action and a method to close the modal.

### Properties

#### `closeArgs: SkyModalCloseArgs`

The object that would be emitted by a modal's `closed` event. This object can be used to determine whether to prompt the user for confirmation, such as when the user closes a modal form after entering data.

#### `closeModal: () => void`

Function to call to close the modal. Neglecting to call this function effectively cancels the close modal action.

 SkyModalError
--------------

Type: Interface

Contains an object with properties for displaying form-level errors in the modal.

    interface SkyModalError {
      message: string;
    }

### Properties

#### `message: string`

The error message to display.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyModalHarness
----------------

Type: Class

`import { SkyModalHarness } from '@skyux/modals/testing';`

Harness for interacting with a modal component in tests.

### Methods

#### `clickHelpInline(): Promise<void>`

Clicks the help inline button.

#### Returns

`Promise<void>`

#### `getAriaDescribedBy(): Promise<null | string>`

Gets the aria-describedBy property of the modal.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledBy(): Promise<null | string>`

Gets the aria-labelledBy property of the modal.

#### Returns

`Promise<null | string>`

#### `getAriaRole(): Promise<null | string>`

Gets the role of the modal.

#### Returns

`Promise<null | string>`

#### `getHeadingText(): Promise<undefined | string>`

Gets the modal's heading text.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverContent(): Promise<undefined | string>`

Gets the help popover content.

#### Returns

`Promise<undefined | string>`

#### `getHelpPopoverTitle(): Promise<undefined | string>`

Gets the help popover title.

#### Returns

`Promise<undefined | string>`

#### `getSize(): Promise<string>`

Gets the modal size.

#### Returns

`Promise<string>`

#### `getWrapperClass(): Promise<undefined | string>`

Gets the wrapper class of the modal.

#### Returns

`Promise<undefined | string>`

#### `isDirty(): Promise<boolean>`

Whether the modal has [SkyModalIsDirtyDirective](/skyux/components/modal?docs-active-tab=testing#class_sky-modal-is-dirty-directive.md).isDirty set to dirty.

#### Returns

`Promise<boolean>`

#### `isFullPage(): Promise<boolean>`

Whether the modal is full page.

#### Returns

`Promise<boolean>`

#### `SkyModalHarness.with(filters: SkyModalHarnessFilters): HarnessPredicate<SkyModalHarness>`

Gets a `HarnessPredicate` that can be used to search for a `SkyModalHarness` that meets certain criteria

#### Parameters

##### `filters: SkyModalHarnessFilters`

#### Returns

`HarnessPredicate<SkyModalHarness>`

 SkyModalHarnessFilters
-----------------------

Type: Interface

A set of criteria that can be used to filter a list of [SkyModalHarness](/skyux/components/modal?docs-active-tab=testing#class_sky-modal-harness.md) instances.

    interface SkyModalHarnessFilters {
      dataSkyId?: string | RegExp;
    }

### Properties

#### `dataSkyId?: string | RegExp`

Only find instances whose `data-sky-id` attribute matches the given value.

 SkyModalTestingModule
----------------------

Type: Module

`import { SkyModalTestingModule } from '@skyux/modals/testing';`

Configures the `SkyModalTestingController` as the implementation for the `SkyModalService`.

 SkyModalTestingController
--------------------------

Type: Class

A controller to be injected into tests, which mocks the modal service and handles interactions with modal instances. For testing interactions with the modal component itself, use the `SkyModalHarness`.

### Methods

#### `closeTopModal(args?: SkyModalCloseArgs): void`

Closes the topmost modal with the provided arguments.

#### Parameters

##### `args?: SkyModalCloseArgs`

Arguments to pass to the modal's close event.

#### Returns

`void`

#### `expectCount(value: number): void`

Throws if the provided value does not match the number of open modals.

#### Parameters

##### `value: number`

#### Returns

`void`

#### `expectNone(): void`

Throws if modals are open.

#### Returns

`void`

#### `expectOpen(component: Type<TComponent>): void`

Throws if the given criteria does not match the topmost open modal.

#### Parameters

##### `component: Type<TComponent>`

#### Returns

`void`