# Design

                  Skip to Main Content

 Flyout
======

Flyouts display large quantities of supplementary information related to a task.

 Usage
------

### Use when

Use flyouts to display large amounts of supplementary information related to user tasks. The flyout container slides out from the side of the page and lays over page content. It can contain lists, record views, graphs, or other information displays.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/flyout-skeleton.22e7ead38b4848c53e3a1a3531210cf8.png)

Do use flyouts to display large amounts of supplementary information related to user tasks.

Use flyouts to drill into analytical insights so that users can quickly glance into what makes up those insights without spawning new workflows.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/flyout-dashboard-view.af9c2ea6c5347a6f732651a6aab8486b.png)

Do use flyouts to let users drill into analytical insights.

Use flyouts to drill into child records so that users can retain the context of the parent records. Flyouts only cover part of the page, so users can refer to the page for context.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/flyout-record-view.7c3e5928c36acbbb5f428f43db58306e.png)

Do use flyouts to drill into child records.

### Don't use when

Don't use flyouts to navigate from one record to another instance of the same record type. For example, if users on a constituent record select a link to a different constituent record, navigate to the new record. Do not open it in a flyout.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-record-to-record.c3b3f69a2686ff233913219d73461b45.png)

Don't use flyouts to navigate from one record to another instance of the same record type.

Don't use flyouts to navigate from a child page to its parent page. For example, if users on a gift record select a link to return to a constituent record, navigate to a full-page view of the constituent record. Do not open it in a flyout.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-child-to-parent.31e12e0b31b8c69b74a44dede62b7588.png)

Don't use flyouts to navigate from a child page to its parent page.

Don't use flyouts when another flyout is already open. If users select a link in a flyout, close the flyout and navigate to the new link location. In other words, limit flyouts to a single drill-in. On further drilling, open a full page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-double-panel.ec114a8badbbba34e6bccb32e7f6a5f2.png)

Don't use flyouts when another flyout is already open.

Don't use flyouts on pages that don't make sense when it closes. For example, on a page to enter grades for a class of students, displaying the names of students doesn't provide value without the grade entry form, so don't use a flyout to display the grade entry form.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-need-details.d00c606f932c7571857a4f915246fc59.png)

Don't use flyouts to display essential information.

Don't use flyouts to display small amounts of additional information. Flyouts are for large amounts of supplementary information. To display smaller amounts of information, use [a popover component](/skyux/components/popover.md) or [an expandable repeater](/skyux/components/repeater.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-small-content.c51eaa2872b342fb8f9d0b3e2694ffe6.png)

Don't use flyouts for small amounts of additional information.

Don't use flyouts to display items that need a long time to load such as system-generated reports. Instead, let users continue to use the system, and use [toasts](/skyux/components/toast.md) to let them know when the content is available.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-long-load.1384bdfb7d805e18cd228c3ada554fb4.png)

Don't use flyouts for items that take a long time to load.

Don't use flyouts to link to external sites. Open external sites in new tabs. For example, when users select a constituent address, a Google map of that address opens in a new tab.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-external.2515ad21661ea3c7067bc1d625046ef9.png)

Don't use flyouts to display external content.

Don't use flyouts for tasks where users require a full-screen view of details or where they take multiple actions within the view. Navigate to a full page instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-need-full.f523b4a4b239e6ceecfd68fb229d56a1.png)

Don't use flyouts for tasks that require a full-screen view.

 Behavior and states
--------------------

### Background page remains active

The background page remains active behind a flyout. When users select a link on the background page to open another record in a list, the flyout loads the new record. When users select a link inside the flyout, the system navigates away from the current page.

When users select a non-interactive element on the background page, the flyout closes. However, when users select a non-interactive element on the background page on touch devices, the flyout does not close because users need to be able touch the background page in order to scroll.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-bg-active-1.1594c9a3747a0b8d68ae46632e36a661.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-bg-active-2.f4e230342b56ebc4332526ac69e664be.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-bg-active-3.73b3d6f8f55830a7024b8dc26c8d9b70.png)

### Independent scrolling

The flyout and its background page scroll independently. When users touch, hover, or focus on the background page, only the background content scrolls. Similarly, when users touch, hover, or focus on the flyout, only the flyout scrolls. This allows users to adjust the content in the flyout without losing context from the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-scroll-1.1594c9a3747a0b8d68ae46632e36a661.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-scroll-2.d617f36534374628900ecadf7491c542.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-scroll-3.a60818e7b8ee720e543f13648e11a4eb.png)

### Drag to resize

Users can select the flyout's left border and drag it to adjust the size. The size can range from 320px to 20px less than the full screen size. If users expand the flyout to the full screen size, it slides 20px to the right to keep a portion of the background page in view. The default size is 50 percent of the screen or 320px, whichever is larger. When users resize the panel, the system remembers their preferred size globally.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-resize-1.1594c9a3747a0b8d68ae46632e36a661.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-resize-2.c5fce5bc61761490da48ed2a7bc7b89c.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-resize-3.a204523d01307cfaf03750609e68602a.png)

### Help panel

The flyout covers the omnibar, but the help panel remains visible in the upper right corner of the screen. The help panel should recognize that the flyout is open and provide appropriate guidance based on the context.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-help-1.1594c9a3747a0b8d68ae46632e36a661.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-help-2.9ea207f70cbb25f87ce49c2604cd9a8d.png)

### Modal dialog behavior

When users perform actions in the flyout to launch modal dialogs, the modal dialogs should cover the entire page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-modal.639f26e7da41ca5c32c6d68ee718914f.png)

### Responsiveness

Do not use a flyout when a screen is smaller than 480px. At smaller resolutions, the flyout covers too much of the screen and loses much of its value. For smaller screen sizes, navigate directly to the appropriate record or list.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/flyout-mobile.a4b616d47ea5acbef340d78f9e42ca85.png)

 Options
--------

### Next and previous buttons

When a flyout opens records in a list, you can include buttons in the toolbar to open the next record or previous record. For example, if users open a flyout on a constituent record to view the first gift in a list of gifts, the next button opens the second gift in the list. When you include the next and previous buttons in the flyout toolbar, a visual indicator highlights the currently selected row on the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/opt-arrows.12698a1f532dbe6dc25ccb81097d7bcb.png)

### List toolbar

When a flyout displays a list, you can include an option in the toolbar to leave the "preview" list and create a new list for further manipulation. The create list button navigates to a new page that contains the new list.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/opt-list.0017c6a8b67744dacfa075af6a868cf4.png)

 Accessibility
--------------

Follow these guidelines to ensure that people can use flyouts with assistive technology or keyboards.

*   When a flyout opens, place focus on the first focusable item. If the flyout does not include focusable items, then place focus on the flyout container element.
    
*   While a flyout is open, limit focus to elements in the flyout. Do not move focus back to the initiating page behind the flyout. On the last focusable item, the Tab key should return focus to the first focusable item. And on the first focusable item, the Shift+Tab keys should switch focus to the last focusable item.
    
*   When a flyout closes, return focus to the element that had focus before the flyout opened. This is usually the element that opened the flyout.
    

 Related information
--------------------

### Guidelines

*   [Content containers](/skyux/design/guidelines/content-containers.md)

 Installation
-------------

NPM package

`@skyux/flyout`[View in NPM](https://www.npmjs.com/package/@skyux/flyout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/flyout/src/lib/modules/flyout/flyout.service.ts#L36) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/flyout`Copy None found.

 SkyFlyoutService
-----------------

Type: Service

Launches flyouts and provides a common look and feel. This service dynamically generates the flyout component and appends it directly to the document's `body` element. The `SkyFlyoutInstance` class watches for and triggers flyout events.

### Methods

#### `close(args?: SkyFlyoutCloseArgs): void`

Closes the flyout. This method also removes the flyout's HTML elements from the DOM.

#### Parameters

##### `args?: SkyFlyoutCloseArgs`

Arguments used when closing the flyout.

#### Returns

`void`

#### `open(component: Type<T>, config?: SkyFlyoutConfig): SkyFlyoutInstance<T>`

Opens a flyout and displays the specified component.

#### Parameters

##### `component: Type<T>`

Specifies the component to render.

##### `config?: SkyFlyoutConfig`

Specifies the flyout configuration passed to the specified component's constructor.

#### Returns

`SkyFlyoutInstance<T>`

 SkyFlyoutConfig
----------------

Type: Interface

Specifies the configuration options to set up a flyout.

    interface SkyFlyoutConfig {
      ariaDescribedBy?: string;
      ariaLabel?: string;
      ariaLabelledBy?: string;
      ariaRole?: string;
      defaultWidth?: number;
      iteratorNextButtonDisabled?: boolean;
      iteratorPreviousButtonDisabled?: boolean;
      maxWidth?: number;
      minWidth?: number;
      permalink?: SkyFlyoutPermalink;
      primaryAction?: SkyFlyoutAction;
      providers?: any[];
      settingsKey?: string;
      showIterator?: boolean;
    }

### Properties

#### `ariaDescribedBy?: string`

The HTML element ID of the element that describes the flyout. This sets the flyout's `aria-describedby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). The description typically includes text on the flyout but not on items that users interact with, such as buttons and forms. For more information about the `aria-describedby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-describedby).

#### `ariaLabel?: string`

The ARIA label for the flyout. This sets the flyouts's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the flyout includes a visible label, use `ariaLabelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `ariaLabelledBy?: string`

The HTML element ID of the element that labels the flyout. This sets the flyout's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the flyout does not include a visible label, use `ariaLabel` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `ariaRole?: string`

Warning: **Deprecated.** Since version `5.1.0`. Consumers should use the default `dialog` role to ensure a proper accessibility implementation.

The ARIA role for the flyout [to support accessibility](/skyux/learn/accessibility.md) by indicating how the flyout functions and what it controls. For information about how an ARIA role indicates what an item represents on a web page, see the [WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles).

#### `defaultWidth?: number`

The default width of the flyout container. If you do not provide a width, the flyout defaults to half the width of its container.

#### `iteratorNextButtonDisabled?: boolean`

Disables the next iterator button in the flyout header that accesses the next record in a record set.

#### `iteratorPreviousButtonDisabled?: boolean`

Disables the previous iterator button in the flyout header that accesses the previous record in a record set.

#### `maxWidth?: number`

The maximum resize width of the flyout container.

#### `minWidth?: number`

The minimum resize width of the flyout container.

#### `permalink?: SkyFlyoutPermalink`

Displays a permalink button in the flyout header that navigates users to the URL (or application route) representative of the flyout's contents.

#### `primaryAction?: SkyFlyoutAction`

Displays a configurable button in the flyout header.

#### `providers?: any[]`

The array of custom providers to pass to the component's constructor.

#### `settingsKey?: string`

The unique key for the UI Config Service to retrieve stored settings from a database. The UI Config Service saves configuration settings for users to preserve the width of the flyout. For more information about the UI Config Service, see [the sticky settings documentation](/skyux/learn/develop/sticky-settings.md).

#### `showIterator?: boolean`

Whether to display iterator buttons in the flyout header to access the next and previous records in a record set.

 SkyFlyoutInstance
------------------

Type: Class

Represents a single displayed flyout.

### Properties

#### `closed: EventEmitter<void>`

An event that the flyout instance emits when it closes.

#### `componentInstance: T`

The instance of the component to display in the flyout.

#### `isOpen: boolean`

A `boolean` value that returns `true` if the flyout is open.

Default: `true`

#### `beforeClose: Observable<SkyFlyoutBeforeCloseHandler>`

An event that the flyout instance emits when it is about to close. If a subscription exists for this event, the flyout does not close until the subscriber calls the handler's `closeModal` method.

#### `iteratorNextButtonClick: EventEmitter<void>`

An event that the flyout instance emits when users click the next iterator button.

#### `iteratorNextButtonDisabled: boolean`

Disables the next iterator button.

Default: `false`

#### `iteratorPreviousButtonClick: EventEmitter<void>`

An event that the flyout instance emits when users click the previous iterator button.

#### `iteratorPreviousButtonDisabled: boolean`

Disables the previous iterator button.

Default: `false`

### Methods

#### `close(args?: SkyFlyoutCloseArgs): void`

Closes the flyout instance and emits its `closed` event.

#### Parameters

##### `args?: SkyFlyoutCloseArgs`

Arguments used when closing the flyout.

#### Returns

`void`

 SkyFlyoutAction
----------------

Type: Interface

    interface SkyFlyoutAction {
      callback?: () => void;
      closeAfterInvoking?: boolean;
      label?: string;
    }

### Properties

#### `callback?: () => void`

The callback function to execute when the button is clicked.

#### `closeAfterInvoking?: boolean`

Whether to close the flyout after the button is clicked.

#### `label?: string`

The button's label.

 SkyFlyoutBeforeCloseHandler
----------------------------

Type: Class

Handler for notifying the flyout when it is appropriate to close the flyout. This will be returned from the flyout instance's `beforeClose` observable.

### Properties

#### `closeFlyout: () => void`

Function which should be called to close the flyout. This should be called once any intervening actions have completed.

 SkyFlyoutCloseArgs
-------------------

Type: Interface

Arguments used when closing a flyout programmatically.

    interface SkyFlyoutCloseArgs {
      ignoreBeforeClose?: boolean;
    }

### Properties

#### `ignoreBeforeClose?: boolean`

Whether the `SkyFlyoutBeforeCloseHandler` is ignored when closing a flyout.

 SkyFlyoutPermalink
-------------------

Type: Interface

    interface SkyFlyoutPermalink {
      label?: string;
      route?: { commands: any[]; extras?: NavigationExtras };
      url?: string;
    }

### Properties

#### `label?: string`

The text label for the permalink button.

#### `route?: { commands: any[]; extras?: NavigationExtras }`

The object that represents the [Angular application route](https://angular.io/api/router/Router#navigate). The object includes two properties that are mapped to Angular's `Router.navigate(commands, extras?)` method.

#### `url?: string`

The external URL for the permalink.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyFlyoutHarness
-----------------

Type: Class

`import { SkyFlyoutHarness } from '@skyux/flyout/testing';`

Harness for interacting with a flyout component in tests.

### Methods

#### `clickNextIteratorButton(): Promise<void>`

Clicks the flyout's next iterator button.

#### Returns

`Promise<void>`

#### `clickPreviousIteratorButton(): Promise<void>`

Clicks the flyout's previous iterator button.

#### Returns

`Promise<void>`

#### `clickPrimaryActionButton(): Promise<void>`

Clicks the flyout's primary action button.

#### Returns

`Promise<void>`

#### `closeFlyout(): Promise<void>`

Clicks the flyout's close button.

#### Returns

`Promise<void>`

#### `getAriaDescribedBy(): Promise<null | string>`

Gets the flyout's aria-describedby attribute.

#### Returns

`Promise<null | string>`

#### `getAriaLabel(): Promise<null | string>`

Gets the flyout's aria-label attribute.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledBy(): Promise<null | string>`

Gets the flyout's aria-labelledby attribute.

#### Returns

`Promise<null | string>`

#### `getAriaRole(): Promise<null | string>`

Gets the flyout's ARIA role.

#### Returns

`Promise<null | string>`

#### `getFlyoutMaxWidth(): Promise<number>`

Gets the flyout's maximum width.

#### Returns

`Promise<number>`

#### `getFlyoutMinWidth(): Promise<number>`

Gets the flyout's minimum width.

#### Returns

`Promise<number>`

#### `getFlyoutWidth(): Promise<number>`

Gets the flyout's current width.

#### Returns

`Promise<number>`

#### `getPermalinkButtonLabel(): Promise<string>`

Gets the label for the flyout's permalink button.

#### Returns

`Promise<string>`

#### `getPermalinkButtonRoute(): Promise<null | string>`

Gets the route for the flyout's permalink button.

#### Returns

`Promise<null | string>`

#### `getPrimaryActionButtonLabel(): Promise<string>`

Gets the label for the flyout's primary action button.

#### Returns

`Promise<string>`

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

 Flyout
======

Flyouts display large quantities of supplementary information related to a task.

 Usage
------

### Use when

Use flyouts to display large amounts of supplementary information related to user tasks. The flyout container slides out from the side of the page and lays over page content. It can contain lists, record views, graphs, or other information displays.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/flyout-skeleton.22e7ead38b4848c53e3a1a3531210cf8.png)

Do use flyouts to display large amounts of supplementary information related to user tasks.

Use flyouts to drill into analytical insights so that users can quickly glance into what makes up those insights without spawning new workflows.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/flyout-dashboard-view.af9c2ea6c5347a6f732651a6aab8486b.png)

Do use flyouts to let users drill into analytical insights.

Use flyouts to drill into child records so that users can retain the context of the parent records. Flyouts only cover part of the page, so users can refer to the page for context.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/flyout-record-view.7c3e5928c36acbbb5f428f43db58306e.png)

Do use flyouts to drill into child records.

### Don't use when

Don't use flyouts to navigate from one record to another instance of the same record type. For example, if users on a constituent record select a link to a different constituent record, navigate to the new record. Do not open it in a flyout.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-record-to-record.c3b3f69a2686ff233913219d73461b45.png)

Don't use flyouts to navigate from one record to another instance of the same record type.

Don't use flyouts to navigate from a child page to its parent page. For example, if users on a gift record select a link to return to a constituent record, navigate to a full-page view of the constituent record. Do not open it in a flyout.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-child-to-parent.31e12e0b31b8c69b74a44dede62b7588.png)

Don't use flyouts to navigate from a child page to its parent page.

Don't use flyouts when another flyout is already open. If users select a link in a flyout, close the flyout and navigate to the new link location. In other words, limit flyouts to a single drill-in. On further drilling, open a full page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-double-panel.ec114a8badbbba34e6bccb32e7f6a5f2.png)

Don't use flyouts when another flyout is already open.

Don't use flyouts on pages that don't make sense when it closes. For example, on a page to enter grades for a class of students, displaying the names of students doesn't provide value without the grade entry form, so don't use a flyout to display the grade entry form.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-need-details.d00c606f932c7571857a4f915246fc59.png)

Don't use flyouts to display essential information.

Don't use flyouts to display small amounts of additional information. Flyouts are for large amounts of supplementary information. To display smaller amounts of information, use [a popover component](/skyux/components/popover.md) or [an expandable repeater](/skyux/components/repeater.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-small-content.c51eaa2872b342fb8f9d0b3e2694ffe6.png)

Don't use flyouts for small amounts of additional information.

Don't use flyouts to display items that need a long time to load such as system-generated reports. Instead, let users continue to use the system, and use [toasts](/skyux/components/toast.md) to let them know when the content is available.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-long-load.1384bdfb7d805e18cd228c3ada554fb4.png)

Don't use flyouts for items that take a long time to load.

Don't use flyouts to link to external sites. Open external sites in new tabs. For example, when users select a constituent address, a Google map of that address opens in a new tab.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-external.2515ad21661ea3c7067bc1d625046ef9.png)

Don't use flyouts to display external content.

Don't use flyouts for tasks where users require a full-screen view of details or where they take multiple actions within the view. Navigate to a full page instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-need-full.f523b4a4b239e6ceecfd68fb229d56a1.png)

Don't use flyouts for tasks that require a full-screen view.

 Behavior and states
--------------------

### Background page remains active

The background page remains active behind a flyout. When users select a link on the background page to open another record in a list, the flyout loads the new record. When users select a link inside the flyout, the system navigates away from the current page.

When users select a non-interactive element on the background page, the flyout closes. However, when users select a non-interactive element on the background page on touch devices, the flyout does not close because users need to be able touch the background page in order to scroll.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-bg-active-1.1594c9a3747a0b8d68ae46632e36a661.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-bg-active-2.f4e230342b56ebc4332526ac69e664be.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-bg-active-3.73b3d6f8f55830a7024b8dc26c8d9b70.png)

### Independent scrolling

The flyout and its background page scroll independently. When users touch, hover, or focus on the background page, only the background content scrolls. Similarly, when users touch, hover, or focus on the flyout, only the flyout scrolls. This allows users to adjust the content in the flyout without losing context from the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-scroll-1.1594c9a3747a0b8d68ae46632e36a661.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-scroll-2.d617f36534374628900ecadf7491c542.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-scroll-3.a60818e7b8ee720e543f13648e11a4eb.png)

### Drag to resize

Users can select the flyout's left border and drag it to adjust the size. The size can range from 320px to 20px less than the full screen size. If users expand the flyout to the full screen size, it slides 20px to the right to keep a portion of the background page in view. The default size is 50 percent of the screen or 320px, whichever is larger. When users resize the panel, the system remembers their preferred size globally.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-resize-1.1594c9a3747a0b8d68ae46632e36a661.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-resize-2.c5fce5bc61761490da48ed2a7bc7b89c.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-resize-3.a204523d01307cfaf03750609e68602a.png)

### Help panel

The flyout covers the omnibar, but the help panel remains visible in the upper right corner of the screen. The help panel should recognize that the flyout is open and provide appropriate guidance based on the context.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-help-1.1594c9a3747a0b8d68ae46632e36a661.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-help-2.9ea207f70cbb25f87ce49c2604cd9a8d.png)

### Modal dialog behavior

When users perform actions in the flyout to launch modal dialogs, the modal dialogs should cover the entire page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-modal.639f26e7da41ca5c32c6d68ee718914f.png)

### Responsiveness

Do not use a flyout when a screen is smaller than 480px. At smaller resolutions, the flyout covers too much of the screen and loses much of its value. For smaller screen sizes, navigate directly to the appropriate record or list.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/flyout-mobile.a4b616d47ea5acbef340d78f9e42ca85.png)

 Options
--------

### Next and previous buttons

When a flyout opens records in a list, you can include buttons in the toolbar to open the next record or previous record. For example, if users open a flyout on a constituent record to view the first gift in a list of gifts, the next button opens the second gift in the list. When you include the next and previous buttons in the flyout toolbar, a visual indicator highlights the currently selected row on the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/opt-arrows.12698a1f532dbe6dc25ccb81097d7bcb.png)

### List toolbar

When a flyout displays a list, you can include an option in the toolbar to leave the "preview" list and create a new list for further manipulation. The create list button navigates to a new page that contains the new list.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/opt-list.0017c6a8b67744dacfa075af6a868cf4.png)

 Accessibility
--------------

Follow these guidelines to ensure that people can use flyouts with assistive technology or keyboards.

*   When a flyout opens, place focus on the first focusable item. If the flyout does not include focusable items, then place focus on the flyout container element.
    
*   While a flyout is open, limit focus to elements in the flyout. Do not move focus back to the initiating page behind the flyout. On the last focusable item, the Tab key should return focus to the first focusable item. And on the first focusable item, the Shift+Tab keys should switch focus to the last focusable item.
    
*   When a flyout closes, return focus to the element that had focus before the flyout opened. This is usually the element that opened the flyout.
    

 Related information
--------------------

### Guidelines

*   [Content containers](/skyux/design/guidelines/content-containers.md)

 Installation
-------------

NPM package

`@skyux/flyout`[View in NPM](https://www.npmjs.com/package/@skyux/flyout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/flyout/src/lib/modules/flyout/flyout.service.ts#L36) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/flyout`Copy None found.

 SkyFlyoutService
-----------------

Type: Service

Launches flyouts and provides a common look and feel. This service dynamically generates the flyout component and appends it directly to the document's `body` element. The `SkyFlyoutInstance` class watches for and triggers flyout events.

### Methods

#### `close(args?: SkyFlyoutCloseArgs): void`

Closes the flyout. This method also removes the flyout's HTML elements from the DOM.

#### Parameters

##### `args?: SkyFlyoutCloseArgs`

Arguments used when closing the flyout.

#### Returns

`void`

#### `open(component: Type<T>, config?: SkyFlyoutConfig): SkyFlyoutInstance<T>`

Opens a flyout and displays the specified component.

#### Parameters

##### `component: Type<T>`

Specifies the component to render.

##### `config?: SkyFlyoutConfig`

Specifies the flyout configuration passed to the specified component's constructor.

#### Returns

`SkyFlyoutInstance<T>`

 SkyFlyoutConfig
----------------

Type: Interface

Specifies the configuration options to set up a flyout.

    interface SkyFlyoutConfig {
      ariaDescribedBy?: string;
      ariaLabel?: string;
      ariaLabelledBy?: string;
      ariaRole?: string;
      defaultWidth?: number;
      iteratorNextButtonDisabled?: boolean;
      iteratorPreviousButtonDisabled?: boolean;
      maxWidth?: number;
      minWidth?: number;
      permalink?: SkyFlyoutPermalink;
      primaryAction?: SkyFlyoutAction;
      providers?: any[];
      settingsKey?: string;
      showIterator?: boolean;
    }

### Properties

#### `ariaDescribedBy?: string`

The HTML element ID of the element that describes the flyout. This sets the flyout's `aria-describedby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). The description typically includes text on the flyout but not on items that users interact with, such as buttons and forms. For more information about the `aria-describedby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-describedby).

#### `ariaLabel?: string`

The ARIA label for the flyout. This sets the flyouts's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the flyout includes a visible label, use `ariaLabelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `ariaLabelledBy?: string`

The HTML element ID of the element that labels the flyout. This sets the flyout's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the flyout does not include a visible label, use `ariaLabel` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `ariaRole?: string`

Warning: **Deprecated.** Since version `5.1.0`. Consumers should use the default `dialog` role to ensure a proper accessibility implementation.

The ARIA role for the flyout [to support accessibility](/skyux/learn/accessibility.md) by indicating how the flyout functions and what it controls. For information about how an ARIA role indicates what an item represents on a web page, see the [WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles).

#### `defaultWidth?: number`

The default width of the flyout container. If you do not provide a width, the flyout defaults to half the width of its container.

#### `iteratorNextButtonDisabled?: boolean`

Disables the next iterator button in the flyout header that accesses the next record in a record set.

#### `iteratorPreviousButtonDisabled?: boolean`

Disables the previous iterator button in the flyout header that accesses the previous record in a record set.

#### `maxWidth?: number`

The maximum resize width of the flyout container.

#### `minWidth?: number`

The minimum resize width of the flyout container.

#### `permalink?: SkyFlyoutPermalink`

Displays a permalink button in the flyout header that navigates users to the URL (or application route) representative of the flyout's contents.

#### `primaryAction?: SkyFlyoutAction`

Displays a configurable button in the flyout header.

#### `providers?: any[]`

The array of custom providers to pass to the component's constructor.

#### `settingsKey?: string`

The unique key for the UI Config Service to retrieve stored settings from a database. The UI Config Service saves configuration settings for users to preserve the width of the flyout. For more information about the UI Config Service, see [the sticky settings documentation](/skyux/learn/develop/sticky-settings.md).

#### `showIterator?: boolean`

Whether to display iterator buttons in the flyout header to access the next and previous records in a record set.

 SkyFlyoutInstance
------------------

Type: Class

Represents a single displayed flyout.

### Properties

#### `closed: EventEmitter<void>`

An event that the flyout instance emits when it closes.

#### `componentInstance: T`

The instance of the component to display in the flyout.

#### `isOpen: boolean`

A `boolean` value that returns `true` if the flyout is open.

Default: `true`

#### `beforeClose: Observable<SkyFlyoutBeforeCloseHandler>`

An event that the flyout instance emits when it is about to close. If a subscription exists for this event, the flyout does not close until the subscriber calls the handler's `closeModal` method.

#### `iteratorNextButtonClick: EventEmitter<void>`

An event that the flyout instance emits when users click the next iterator button.

#### `iteratorNextButtonDisabled: boolean`

Disables the next iterator button.

Default: `false`

#### `iteratorPreviousButtonClick: EventEmitter<void>`

An event that the flyout instance emits when users click the previous iterator button.

#### `iteratorPreviousButtonDisabled: boolean`

Disables the previous iterator button.

Default: `false`

### Methods

#### `close(args?: SkyFlyoutCloseArgs): void`

Closes the flyout instance and emits its `closed` event.

#### Parameters

##### `args?: SkyFlyoutCloseArgs`

Arguments used when closing the flyout.

#### Returns

`void`

 SkyFlyoutAction
----------------

Type: Interface

    interface SkyFlyoutAction {
      callback?: () => void;
      closeAfterInvoking?: boolean;
      label?: string;
    }

### Properties

#### `callback?: () => void`

The callback function to execute when the button is clicked.

#### `closeAfterInvoking?: boolean`

Whether to close the flyout after the button is clicked.

#### `label?: string`

The button's label.

 SkyFlyoutBeforeCloseHandler
----------------------------

Type: Class

Handler for notifying the flyout when it is appropriate to close the flyout. This will be returned from the flyout instance's `beforeClose` observable.

### Properties

#### `closeFlyout: () => void`

Function which should be called to close the flyout. This should be called once any intervening actions have completed.

 SkyFlyoutCloseArgs
-------------------

Type: Interface

Arguments used when closing a flyout programmatically.

    interface SkyFlyoutCloseArgs {
      ignoreBeforeClose?: boolean;
    }

### Properties

#### `ignoreBeforeClose?: boolean`

Whether the `SkyFlyoutBeforeCloseHandler` is ignored when closing a flyout.

 SkyFlyoutPermalink
-------------------

Type: Interface

    interface SkyFlyoutPermalink {
      label?: string;
      route?: { commands: any[]; extras?: NavigationExtras };
      url?: string;
    }

### Properties

#### `label?: string`

The text label for the permalink button.

#### `route?: { commands: any[]; extras?: NavigationExtras }`

The object that represents the [Angular application route](https://angular.io/api/router/Router#navigate). The object includes two properties that are mapped to Angular's `Router.navigate(commands, extras?)` method.

#### `url?: string`

The external URL for the permalink.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyFlyoutHarness
-----------------

Type: Class

`import { SkyFlyoutHarness } from '@skyux/flyout/testing';`

Harness for interacting with a flyout component in tests.

### Methods

#### `clickNextIteratorButton(): Promise<void>`

Clicks the flyout's next iterator button.

#### Returns

`Promise<void>`

#### `clickPreviousIteratorButton(): Promise<void>`

Clicks the flyout's previous iterator button.

#### Returns

`Promise<void>`

#### `clickPrimaryActionButton(): Promise<void>`

Clicks the flyout's primary action button.

#### Returns

`Promise<void>`

#### `closeFlyout(): Promise<void>`

Clicks the flyout's close button.

#### Returns

`Promise<void>`

#### `getAriaDescribedBy(): Promise<null | string>`

Gets the flyout's aria-describedby attribute.

#### Returns

`Promise<null | string>`

#### `getAriaLabel(): Promise<null | string>`

Gets the flyout's aria-label attribute.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledBy(): Promise<null | string>`

Gets the flyout's aria-labelledby attribute.

#### Returns

`Promise<null | string>`

#### `getAriaRole(): Promise<null | string>`

Gets the flyout's ARIA role.

#### Returns

`Promise<null | string>`

#### `getFlyoutMaxWidth(): Promise<number>`

Gets the flyout's maximum width.

#### Returns

`Promise<number>`

#### `getFlyoutMinWidth(): Promise<number>`

Gets the flyout's minimum width.

#### Returns

`Promise<number>`

#### `getFlyoutWidth(): Promise<number>`

Gets the flyout's current width.

#### Returns

`Promise<number>`

#### `getPermalinkButtonLabel(): Promise<string>`

Gets the label for the flyout's permalink button.

#### Returns

`Promise<string>`

#### `getPermalinkButtonRoute(): Promise<null | string>`

Gets the route for the flyout's permalink button.

#### Returns

`Promise<null | string>`

#### `getPrimaryActionButtonLabel(): Promise<string>`

Gets the label for the flyout's primary action button.

#### Returns

`Promise<string>`

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

 Flyout
======

Flyouts display large quantities of supplementary information related to a task.Usage
------

### Use when

Use flyouts to display large amounts of supplementary information related to user tasks. The flyout container slides out from the side of the page and lays over page content. It can contain lists, record views, graphs, or other information displays.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/flyout-skeleton.22e7ead38b4848c53e3a1a3531210cf8.png)

Do use flyouts to display large amounts of supplementary information related to user tasks.

Use flyouts to drill into analytical insights so that users can quickly glance into what makes up those insights without spawning new workflows.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/flyout-dashboard-view.af9c2ea6c5347a6f732651a6aab8486b.png)

Do use flyouts to let users drill into analytical insights.

Use flyouts to drill into child records so that users can retain the context of the parent records. Flyouts only cover part of the page, so users can refer to the page for context.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/flyout-record-view.7c3e5928c36acbbb5f428f43db58306e.png)

Do use flyouts to drill into child records.

### Don't use when

Don't use flyouts to navigate from one record to another instance of the same record type. For example, if users on a constituent record select a link to a different constituent record, navigate to the new record. Do not open it in a flyout.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-record-to-record.c3b3f69a2686ff233913219d73461b45.png)

Don't use flyouts to navigate from one record to another instance of the same record type.

Don't use flyouts to navigate from a child page to its parent page. For example, if users on a gift record select a link to return to a constituent record, navigate to a full-page view of the constituent record. Do not open it in a flyout.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-child-to-parent.31e12e0b31b8c69b74a44dede62b7588.png)

Don't use flyouts to navigate from a child page to its parent page.

Don't use flyouts when another flyout is already open. If users select a link in a flyout, close the flyout and navigate to the new link location. In other words, limit flyouts to a single drill-in. On further drilling, open a full page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-double-panel.ec114a8badbbba34e6bccb32e7f6a5f2.png)

Don't use flyouts when another flyout is already open.

Don't use flyouts on pages that don't make sense when it closes. For example, on a page to enter grades for a class of students, displaying the names of students doesn't provide value without the grade entry form, so don't use a flyout to display the grade entry form.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-need-details.d00c606f932c7571857a4f915246fc59.png)

Don't use flyouts to display essential information.

Don't use flyouts to display small amounts of additional information. Flyouts are for large amounts of supplementary information. To display smaller amounts of information, use [a popover component](/skyux/components/popover.md) or [an expandable repeater](/skyux/components/repeater.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-small-content.c51eaa2872b342fb8f9d0b3e2694ffe6.png)

Don't use flyouts for small amounts of additional information.

Don't use flyouts to display items that need a long time to load such as system-generated reports. Instead, let users continue to use the system, and use [toasts](/skyux/components/toast.md) to let them know when the content is available.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-long-load.1384bdfb7d805e18cd228c3ada554fb4.png)

Don't use flyouts for items that take a long time to load.

Don't use flyouts to link to external sites. Open external sites in new tabs. For example, when users select a constituent address, a Google map of that address opens in a new tab.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-external.2515ad21661ea3c7067bc1d625046ef9.png)

Don't use flyouts to display external content.

Don't use flyouts for tasks where users require a full-screen view of details or where they take multiple actions within the view. Navigate to a full page instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-need-full.f523b4a4b239e6ceecfd68fb229d56a1.png)

Don't use flyouts for tasks that require a full-screen view.

 Behavior and states
--------------------

### Background page remains active

The background page remains active behind a flyout. When users select a link on the background page to open another record in a list, the flyout loads the new record. When users select a link inside the flyout, the system navigates away from the current page.

When users select a non-interactive element on the background page, the flyout closes. However, when users select a non-interactive element on the background page on touch devices, the flyout does not close because users need to be able touch the background page in order to scroll.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-bg-active-1.1594c9a3747a0b8d68ae46632e36a661.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-bg-active-2.f4e230342b56ebc4332526ac69e664be.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-bg-active-3.73b3d6f8f55830a7024b8dc26c8d9b70.png)

### Independent scrolling

The flyout and its background page scroll independently. When users touch, hover, or focus on the background page, only the background content scrolls. Similarly, when users touch, hover, or focus on the flyout, only the flyout scrolls. This allows users to adjust the content in the flyout without losing context from the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-scroll-1.1594c9a3747a0b8d68ae46632e36a661.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-scroll-2.d617f36534374628900ecadf7491c542.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-scroll-3.a60818e7b8ee720e543f13648e11a4eb.png)

### Drag to resize

Users can select the flyout's left border and drag it to adjust the size. The size can range from 320px to 20px less than the full screen size. If users expand the flyout to the full screen size, it slides 20px to the right to keep a portion of the background page in view. The default size is 50 percent of the screen or 320px, whichever is larger. When users resize the panel, the system remembers their preferred size globally.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-resize-1.1594c9a3747a0b8d68ae46632e36a661.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-resize-2.c5fce5bc61761490da48ed2a7bc7b89c.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-resize-3.a204523d01307cfaf03750609e68602a.png)

### Help panel

The flyout covers the omnibar, but the help panel remains visible in the upper right corner of the screen. The help panel should recognize that the flyout is open and provide appropriate guidance based on the context.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-help-1.1594c9a3747a0b8d68ae46632e36a661.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-help-2.9ea207f70cbb25f87ce49c2604cd9a8d.png)

### Modal dialog behavior

When users perform actions in the flyout to launch modal dialogs, the modal dialogs should cover the entire page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-modal.639f26e7da41ca5c32c6d68ee718914f.png)

### Responsiveness

Do not use a flyout when a screen is smaller than 480px. At smaller resolutions, the flyout covers too much of the screen and loses much of its value. For smaller screen sizes, navigate directly to the appropriate record or list.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/flyout-mobile.a4b616d47ea5acbef340d78f9e42ca85.png)

 Options
--------

### Next and previous buttons

When a flyout opens records in a list, you can include buttons in the toolbar to open the next record or previous record. For example, if users open a flyout on a constituent record to view the first gift in a list of gifts, the next button opens the second gift in the list. When you include the next and previous buttons in the flyout toolbar, a visual indicator highlights the currently selected row on the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/opt-arrows.12698a1f532dbe6dc25ccb81097d7bcb.png)

### List toolbar

When a flyout displays a list, you can include an option in the toolbar to leave the "preview" list and create a new list for further manipulation. The create list button navigates to a new page that contains the new list.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/opt-list.0017c6a8b67744dacfa075af6a868cf4.png)

 Accessibility
--------------

Follow these guidelines to ensure that people can use flyouts with assistive technology or keyboards.

*   When a flyout opens, place focus on the first focusable item. If the flyout does not include focusable items, then place focus on the flyout container element.
    
*   While a flyout is open, limit focus to elements in the flyout. Do not move focus back to the initiating page behind the flyout. On the last focusable item, the Tab key should return focus to the first focusable item. And on the first focusable item, the Shift+Tab keys should switch focus to the last focusable item.
    
*   When a flyout closes, return focus to the element that had focus before the flyout opened. This is usually the element that opened the flyout.
    

 Related information
--------------------

### Guidelines

*   [Content containers](/skyux/design/guidelines/content-containers.md)

 Installation
-------------

NPM package

`@skyux/flyout`[View in NPM](https://www.npmjs.com/package/@skyux/flyout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/flyout/src/lib/modules/flyout/flyout.service.ts#L36) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/flyout`Copy None found.

 SkyFlyoutService
-----------------

Type: Service

Launches flyouts and provides a common look and feel. This service dynamically generates the flyout component and appends it directly to the document's `body` element. The `SkyFlyoutInstance` class watches for and triggers flyout events.

### Methods

#### `close(args?: SkyFlyoutCloseArgs): void`

Closes the flyout. This method also removes the flyout's HTML elements from the DOM.

#### Parameters

##### `args?: SkyFlyoutCloseArgs`

Arguments used when closing the flyout.

#### Returns

`void`

#### `open(component: Type<T>, config?: SkyFlyoutConfig): SkyFlyoutInstance<T>`

Opens a flyout and displays the specified component.

#### Parameters

##### `component: Type<T>`

Specifies the component to render.

##### `config?: SkyFlyoutConfig`

Specifies the flyout configuration passed to the specified component's constructor.

#### Returns

`SkyFlyoutInstance<T>`

 SkyFlyoutConfig
----------------

Type: Interface

Specifies the configuration options to set up a flyout.

    interface SkyFlyoutConfig {
      ariaDescribedBy?: string;
      ariaLabel?: string;
      ariaLabelledBy?: string;
      ariaRole?: string;
      defaultWidth?: number;
      iteratorNextButtonDisabled?: boolean;
      iteratorPreviousButtonDisabled?: boolean;
      maxWidth?: number;
      minWidth?: number;
      permalink?: SkyFlyoutPermalink;
      primaryAction?: SkyFlyoutAction;
      providers?: any[];
      settingsKey?: string;
      showIterator?: boolean;
    }

### Properties

#### `ariaDescribedBy?: string`

The HTML element ID of the element that describes the flyout. This sets the flyout's `aria-describedby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). The description typically includes text on the flyout but not on items that users interact with, such as buttons and forms. For more information about the `aria-describedby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-describedby).

#### `ariaLabel?: string`

The ARIA label for the flyout. This sets the flyouts's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the flyout includes a visible label, use `ariaLabelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `ariaLabelledBy?: string`

The HTML element ID of the element that labels the flyout. This sets the flyout's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the flyout does not include a visible label, use `ariaLabel` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `ariaRole?: string`

Warning: **Deprecated.** Since version `5.1.0`. Consumers should use the default `dialog` role to ensure a proper accessibility implementation.

The ARIA role for the flyout [to support accessibility](/skyux/learn/accessibility.md) by indicating how the flyout functions and what it controls. For information about how an ARIA role indicates what an item represents on a web page, see the [WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles).

#### `defaultWidth?: number`

The default width of the flyout container. If you do not provide a width, the flyout defaults to half the width of its container.

#### `iteratorNextButtonDisabled?: boolean`

Disables the next iterator button in the flyout header that accesses the next record in a record set.

#### `iteratorPreviousButtonDisabled?: boolean`

Disables the previous iterator button in the flyout header that accesses the previous record in a record set.

#### `maxWidth?: number`

The maximum resize width of the flyout container.

#### `minWidth?: number`

The minimum resize width of the flyout container.

#### `permalink?: SkyFlyoutPermalink`

Displays a permalink button in the flyout header that navigates users to the URL (or application route) representative of the flyout's contents.

#### `primaryAction?: SkyFlyoutAction`

Displays a configurable button in the flyout header.

#### `providers?: any[]`

The array of custom providers to pass to the component's constructor.

#### `settingsKey?: string`

The unique key for the UI Config Service to retrieve stored settings from a database. The UI Config Service saves configuration settings for users to preserve the width of the flyout. For more information about the UI Config Service, see [the sticky settings documentation](/skyux/learn/develop/sticky-settings.md).

#### `showIterator?: boolean`

Whether to display iterator buttons in the flyout header to access the next and previous records in a record set.

 SkyFlyoutInstance
------------------

Type: Class

Represents a single displayed flyout.

### Properties

#### `closed: EventEmitter<void>`

An event that the flyout instance emits when it closes.

#### `componentInstance: T`

The instance of the component to display in the flyout.

#### `isOpen: boolean`

A `boolean` value that returns `true` if the flyout is open.

Default: `true`

#### `beforeClose: Observable<SkyFlyoutBeforeCloseHandler>`

An event that the flyout instance emits when it is about to close. If a subscription exists for this event, the flyout does not close until the subscriber calls the handler's `closeModal` method.

#### `iteratorNextButtonClick: EventEmitter<void>`

An event that the flyout instance emits when users click the next iterator button.

#### `iteratorNextButtonDisabled: boolean`

Disables the next iterator button.

Default: `false`

#### `iteratorPreviousButtonClick: EventEmitter<void>`

An event that the flyout instance emits when users click the previous iterator button.

#### `iteratorPreviousButtonDisabled: boolean`

Disables the previous iterator button.

Default: `false`

### Methods

#### `close(args?: SkyFlyoutCloseArgs): void`

Closes the flyout instance and emits its `closed` event.

#### Parameters

##### `args?: SkyFlyoutCloseArgs`

Arguments used when closing the flyout.

#### Returns

`void`

 SkyFlyoutAction
----------------

Type: Interface

    interface SkyFlyoutAction {
      callback?: () => void;
      closeAfterInvoking?: boolean;
      label?: string;
    }

### Properties

#### `callback?: () => void`

The callback function to execute when the button is clicked.

#### `closeAfterInvoking?: boolean`

Whether to close the flyout after the button is clicked.

#### `label?: string`

The button's label.

 SkyFlyoutBeforeCloseHandler
----------------------------

Type: Class

Handler for notifying the flyout when it is appropriate to close the flyout. This will be returned from the flyout instance's `beforeClose` observable.

### Properties

#### `closeFlyout: () => void`

Function which should be called to close the flyout. This should be called once any intervening actions have completed.

 SkyFlyoutCloseArgs
-------------------

Type: Interface

Arguments used when closing a flyout programmatically.

    interface SkyFlyoutCloseArgs {
      ignoreBeforeClose?: boolean;
    }

### Properties

#### `ignoreBeforeClose?: boolean`

Whether the `SkyFlyoutBeforeCloseHandler` is ignored when closing a flyout.

 SkyFlyoutPermalink
-------------------

Type: Interface

    interface SkyFlyoutPermalink {
      label?: string;
      route?: { commands: any[]; extras?: NavigationExtras };
      url?: string;
    }

### Properties

#### `label?: string`

The text label for the permalink button.

#### `route?: { commands: any[]; extras?: NavigationExtras }`

The object that represents the [Angular application route](https://angular.io/api/router/Router#navigate). The object includes two properties that are mapped to Angular's `Router.navigate(commands, extras?)` method.

#### `url?: string`

The external URL for the permalink.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyFlyoutHarness
-----------------

Type: Class

`import { SkyFlyoutHarness } from '@skyux/flyout/testing';`

Harness for interacting with a flyout component in tests.

### Methods

#### `clickNextIteratorButton(): Promise<void>`

Clicks the flyout's next iterator button.

#### Returns

`Promise<void>`

#### `clickPreviousIteratorButton(): Promise<void>`

Clicks the flyout's previous iterator button.

#### Returns

`Promise<void>`

#### `clickPrimaryActionButton(): Promise<void>`

Clicks the flyout's primary action button.

#### Returns

`Promise<void>`

#### `closeFlyout(): Promise<void>`

Clicks the flyout's close button.

#### Returns

`Promise<void>`

#### `getAriaDescribedBy(): Promise<null | string>`

Gets the flyout's aria-describedby attribute.

#### Returns

`Promise<null | string>`

#### `getAriaLabel(): Promise<null | string>`

Gets the flyout's aria-label attribute.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledBy(): Promise<null | string>`

Gets the flyout's aria-labelledby attribute.

#### Returns

`Promise<null | string>`

#### `getAriaRole(): Promise<null | string>`

Gets the flyout's ARIA role.

#### Returns

`Promise<null | string>`

#### `getFlyoutMaxWidth(): Promise<number>`

Gets the flyout's maximum width.

#### Returns

`Promise<number>`

#### `getFlyoutMinWidth(): Promise<number>`

Gets the flyout's minimum width.

#### Returns

`Promise<number>`

#### `getFlyoutWidth(): Promise<number>`

Gets the flyout's current width.

#### Returns

`Promise<number>`

#### `getPermalinkButtonLabel(): Promise<string>`

Gets the label for the flyout's permalink button.

#### Returns

`Promise<string>`

#### `getPermalinkButtonRoute(): Promise<null | string>`

Gets the route for the flyout's permalink button.

#### Returns

`Promise<null | string>`

#### `getPrimaryActionButtonLabel(): Promise<string>`

Gets the label for the flyout's primary action button.

#### Returns

`Promise<string>`

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

### Flyout with basic setup

Edit in StackBlitz

Open flyout Open flyout with custom width Close flyout programmatically

Show code

Copy

    <button
      class="sky-btn sky-btn-default sky-margin-inline-sm"
      type="button"
      (click)="openSimpleFlyout()"
    >
      Open flyout
    </button>
    
    <button
      class="sky-btn sky-btn-default sky-margin-inline-sm"
      type="button"
      (click)="openFlyoutWithCustomWidth()"
    >
      Open flyout with custom width
    </button>
    
    <button
      class="sky-btn sky-btn-default"
      type="button"
      (click)="closeAndRemoveFlyout()"
    >
      Close flyout programmatically
    </button>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyFlyoutHarness } from '@skyux/flyout/testing';
    
    import { FlyoutBasicExampleComponent } from './example.component';
    
    describe('Basic flyout example', () => {
      async function setupTest(): Promise<{
        flyoutHarness: SkyFlyoutHarness;
        fixture: ComponentFixture<FlyoutBasicExampleComponent>;
      }> {
        await TestBed.configureTestingModule({
          imports: [FlyoutBasicExampleComponent, NoopAnimationsModule],
        }).compileComponents();
    
        const fixture = TestBed.createComponent(FlyoutBasicExampleComponent);
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    
        fixture.componentInstance.openFlyoutWithCustomWidth();
    
        const flyoutHarness: SkyFlyoutHarness =
          await loader.getHarness(SkyFlyoutHarness);
    
        return { flyoutHarness, fixture };
      }
    
      it('should set up the flyout', async () => {
        const { flyoutHarness } = await setupTest();
    
        await expectAsync(flyoutHarness.getAriaLabelledBy()).toBeResolvedTo(
          'flyout-title',
        );
        await expectAsync(flyoutHarness.getAriaRole()).toBeResolvedTo('dialog');
        await expectAsync(flyoutHarness.getFlyoutWidth()).toBeResolvedTo(350);
        await expectAsync(flyoutHarness.getFlyoutMinWidth()).toBeResolvedTo(200);
        await expectAsync(flyoutHarness.getFlyoutMaxWidth()).toBeResolvedTo(500);
    
        await flyoutHarness.closeFlyout();
      });
    });
Copy

    import { Component } from '@angular/core';
    
    @Component({
      standalone: true,
      selector: 'app-flyout',
      template: `
        <div class="sky-padding-even-xl">
          <h2>Sample flyout</h2>
          <p>
            Flyouts can display large quantities of supplementary information
            related to a task, including:
          </p>
          <ul>
            <li>lists</li>
            <li>records</li>
            <li>analytics</li>
          </ul>
        </div>
      `,
    })
    export class FlyoutComponent {}

Copy

    import { Component, inject } from '@angular/core';
    import { SkyFlyoutInstance, SkyFlyoutService } from '@skyux/flyout';
    
    import { FlyoutComponent } from './flyout.component';
    
    /**
     * @title Flyout with basic setup
     */
    @Component({
      standalone: true,
      selector: 'app-flyout-basic-example',
      templateUrl: './example.component.html',
    })
    export class FlyoutBasicExampleComponent {
      #flyout: SkyFlyoutInstance<FlyoutComponent> | undefined;
    
      readonly #flyoutSvc = inject(SkyFlyoutService);
    
      protected closeAndRemoveFlyout(): void {
        if (this.#flyout?.isOpen) {
          this.#flyoutSvc.close();
        }
    
        this.#flyout = undefined;
      }
    
      public openFlyoutWithCustomWidth(): void {
        this.#flyout = this.#flyoutSvc.open(FlyoutComponent, {
          ariaLabelledBy: 'flyout-title',
          ariaRole: 'dialog',
          defaultWidth: 350,
          maxWidth: 500,
          minWidth: 200,
        });
    
        this.#flyout.closed.subscribe(() => {
          this.#flyout = undefined;
        });
      }
    
      protected openSimpleFlyout(): void {
        this.#flyout = this.#flyoutSvc.open(FlyoutComponent, {
          ariaLabelledBy: 'flyout-title',
          ariaRole: 'dialog',
        });
    
        this.#flyout.closed.subscribe(() => {
          this.#flyout = undefined;
        });
      }
    }
### Flyouts with customized headers

Edit in StackBlitz

Open flyout with a URL permalink Open flyout with an Angular routing permalink Open flyout with iterators Open flyout with primary action

Show code

Copy

    <button
      class="sky-btn sky-btn-default sky-margin-inline-sm"
      type="button"
      (click)="openFlyoutWithUrlPermalink()"
    >
      Open flyout with a URL permalink
    </button>
    
    <button
      class="sky-btn sky-btn-default sky-margin-inline-sm"
      type="button"
      (click)="openFlyoutWithRoutePermalink()"
    >
      Open flyout with an Angular routing permalink
    </button>
    
    <button
      class="sky-btn sky-btn-default sky-margin-inline-sm"
      type="button"
      (click)="openFlyoutWithIterators()"
    >
      Open flyout with iterators
    </button>
    
    <button
      class="sky-btn sky-btn-default sky-margin-inline-sm"
      type="button"
      (click)="openFlyoutWithPrimaryAction()"
    >
      Open flyout with primary action
    </button>
Copy

    import { TestbedHarnessEnvironment } from '@angular/cdk/testing/testbed';
    import { ComponentFixture, TestBed } from '@angular/core/testing';
    import { NoopAnimationsModule } from '@angular/platform-browser/animations';
    import { SkyFlyoutHarness } from '@skyux/flyout/testing';
    
    import { FlyoutCustomHeadersExampleComponent } from './example.component';
    
    describe('Custom headers flyout example', () => {
      async function setupTest(option?: string): Promise<{
        flyoutHarness: SkyFlyoutHarness;
        fixture: ComponentFixture<FlyoutCustomHeadersExampleComponent>;
      }> {
        await TestBed.configureTestingModule({
          imports: [FlyoutCustomHeadersExampleComponent, NoopAnimationsModule],
        }).compileComponents();
    
        const fixture = TestBed.createComponent(
          FlyoutCustomHeadersExampleComponent,
        );
        const loader = TestbedHarnessEnvironment.documentRootLoader(fixture);
    
        switch (option) {
          case 'url':
            fixture.componentInstance.openFlyoutWithUrlPermalink();
            break;
          case 'action':
            fixture.componentInstance.openFlyoutWithPrimaryAction();
            break;
          default:
            fixture.componentInstance.openFlyoutWithIterators();
            break;
        }
    
        const flyoutHarness: SkyFlyoutHarness =
          await loader.getHarness(SkyFlyoutHarness);
    
        return { flyoutHarness, fixture };
      }
    
      it('should set up the flyout with iterators', async () => {
        const { flyoutHarness, fixture } = await setupTest();
    
        await expectAsync(flyoutHarness.getAriaLabelledBy()).toBeResolvedTo(
          'flyout-title',
        );
        await expectAsync(flyoutHarness.getAriaRole()).toBeResolvedTo('dialog');
    
        expect(fixture.componentInstance.recordNumber).toBe(0);
        await flyoutHarness.clickNextIteratorButton();
        expect(fixture.componentInstance.recordNumber).toBe(1);
        await flyoutHarness.clickPreviousIteratorButton();
        expect(fixture.componentInstance.recordNumber).toBe(0);
        // previous button is disabled
        await expectAsync(
          flyoutHarness.clickPreviousIteratorButton(),
        ).toBeRejectedWithError(
          'Could not click the previous iterator because it is disabled.',
        );
      });
    
      it('should set up the flyout with permalink', async () => {
        const { flyoutHarness } = await setupTest('url');
    
        await expectAsync(flyoutHarness.getPermalinkButtonLabel()).toBeResolvedTo(
          'Visit blackbaud.com',
        );
        await expectAsync(flyoutHarness.getPermalinkButtonRoute()).toBeResolvedTo(
          'http://www.blackbaud.com',
        );
      });
    
      it('should set up the flyout with primary action', async () => {
        const { flyoutHarness, fixture } = await setupTest('action');
    
        await expectAsync(
          flyoutHarness.getPrimaryActionButtonLabel(),
        ).toBeResolvedTo('Save');
    
        const actionSpy = spyOn(fixture.componentInstance, 'primaryActionCallback');
        await flyoutHarness.clickPrimaryActionButton();
        expect(actionSpy).toHaveBeenCalledTimes(1);
      });
    });
Copy

    import { Component } from '@angular/core';
    
    @Component({
      standalone: true,
      selector: 'app-flyout',
      template: `
        <div class="sky-padding-even-xl">
          <h2>Sample flyout</h2>
          <p>
            Flyouts can display large quantities of supplementary information
            related to a task, including:
          </p>
          <ul>
            <li>lists</li>
            <li>records</li>
            <li>analytics</li>
          </ul>
        </div>
      `,
    })
    export class FlyoutComponent {}

Copy

    import { Component, inject } from '@angular/core';
    import { SkyFlyoutInstance, SkyFlyoutService } from '@skyux/flyout';
    
    import { FlyoutComponent } from './flyout.component';
    
    /**
     * @title Flyouts with customized headers
     */
    @Component({
      standalone: true,
      selector: 'app-flyout-custom-headers-example',
      templateUrl: './example.component.html',
    })
    export class FlyoutCustomHeadersExampleComponent {
      public recordNumber = 0;
      public primaryActionCallback(): void {
        alert('Primary action clicked!');
      }
    
      #flyout: SkyFlyoutInstance<FlyoutComponent> | undefined;
    
      readonly #flyoutSvc = inject(SkyFlyoutService);
    
      public openFlyoutWithIterators(): void {
        this.#flyout = this.#flyoutSvc.open(FlyoutComponent, {
          ariaLabelledBy: 'flyout-title',
          ariaRole: 'dialog',
          showIterator: true,
          iteratorNextButtonDisabled: this.#nextButtonDisabled(),
          iteratorPreviousButtonDisabled: this.#previousButtonDisabled(),
        });
    
        this.#flyout.iteratorNextButtonClick.subscribe(() => {
          alert('Next iterator button clicked!');
          this.recordNumber += 1;
          this.#flyout!.iteratorNextButtonDisabled = this.#nextButtonDisabled();
          this.#flyout!.iteratorPreviousButtonDisabled =
            this.#previousButtonDisabled();
        });
    
        this.#flyout.iteratorPreviousButtonClick.subscribe(() => {
          alert('Previous iterator button clicked!');
          this.recordNumber -= 1;
          this.#flyout!.iteratorNextButtonDisabled = this.#nextButtonDisabled();
          this.#flyout!.iteratorPreviousButtonDisabled =
            this.#previousButtonDisabled();
        });
    
        this.#flyout.closed.subscribe(() => {
          this.#flyout = undefined;
        });
      }
    
      public openFlyoutWithPrimaryAction(): void {
        this.#flyout = this.#flyoutSvc.open(FlyoutComponent, {
          ariaLabelledBy: 'flyout-title',
          ariaRole: 'dialog',
          primaryAction: {
            label: 'Save',
            callback: () => {
              this.primaryActionCallback();
            },
          },
        });
      }
    
      public openFlyoutWithRoutePermalink(): void {
        this.#flyout = this.#flyoutSvc.open(FlyoutComponent, {
          ariaLabelledBy: 'flyout-title',
          ariaRole: 'dialog',
          permalink: {
            label: 'Go to Components page',
            route: {
              commands: ['/components'],
              extras: {
                fragment: 'helloWorld',
                queryParams: {
                  foo: 'bar',
                },
              },
            },
          },
        });
    
        this.#flyout.closed.subscribe(() => {
          this.#flyout = undefined;
        });
      }
    
      public openFlyoutWithUrlPermalink(): void {
        this.#flyout = this.#flyoutSvc.open(FlyoutComponent, {
          ariaLabelledBy: 'flyout-title',
          ariaRole: 'dialog',
          permalink: {
            label: `Visit blackbaud.com`,
            url: 'http://www.blackbaud.com',
          },
        });
    
        this.#flyout.closed.subscribe(() => {
          this.#flyout = undefined;
        });
      }
    
      #nextButtonDisabled(): boolean {
        return this.recordNumber >= 3;
      }
    
      #previousButtonDisabled(): boolean {
        return this.recordNumber <= 0;
      }
    }

# Testing

                  Skip to Main Content

 Flyout
======

Flyouts display large quantities of supplementary information related to a task.

 Usage
------

### Use when

Use flyouts to display large amounts of supplementary information related to user tasks. The flyout container slides out from the side of the page and lays over page content. It can contain lists, record views, graphs, or other information displays.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/flyout-skeleton.22e7ead38b4848c53e3a1a3531210cf8.png)

Do use flyouts to display large amounts of supplementary information related to user tasks.

Use flyouts to drill into analytical insights so that users can quickly glance into what makes up those insights without spawning new workflows.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/flyout-dashboard-view.af9c2ea6c5347a6f732651a6aab8486b.png)

Do use flyouts to let users drill into analytical insights.

Use flyouts to drill into child records so that users can retain the context of the parent records. Flyouts only cover part of the page, so users can refer to the page for context.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/flyout-record-view.7c3e5928c36acbbb5f428f43db58306e.png)

Do use flyouts to drill into child records.

### Don't use when

Don't use flyouts to navigate from one record to another instance of the same record type. For example, if users on a constituent record select a link to a different constituent record, navigate to the new record. Do not open it in a flyout.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-record-to-record.c3b3f69a2686ff233913219d73461b45.png)

Don't use flyouts to navigate from one record to another instance of the same record type.

Don't use flyouts to navigate from a child page to its parent page. For example, if users on a gift record select a link to return to a constituent record, navigate to a full-page view of the constituent record. Do not open it in a flyout.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-child-to-parent.31e12e0b31b8c69b74a44dede62b7588.png)

Don't use flyouts to navigate from a child page to its parent page.

Don't use flyouts when another flyout is already open. If users select a link in a flyout, close the flyout and navigate to the new link location. In other words, limit flyouts to a single drill-in. On further drilling, open a full page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-double-panel.ec114a8badbbba34e6bccb32e7f6a5f2.png)

Don't use flyouts when another flyout is already open.

Don't use flyouts on pages that don't make sense when it closes. For example, on a page to enter grades for a class of students, displaying the names of students doesn't provide value without the grade entry form, so don't use a flyout to display the grade entry form.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-need-details.d00c606f932c7571857a4f915246fc59.png)

Don't use flyouts to display essential information.

Don't use flyouts to display small amounts of additional information. Flyouts are for large amounts of supplementary information. To display smaller amounts of information, use [a popover component](/skyux/components/popover.md) or [an expandable repeater](/skyux/components/repeater.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-small-content.c51eaa2872b342fb8f9d0b3e2694ffe6.png)

Don't use flyouts for small amounts of additional information.

Don't use flyouts to display items that need a long time to load such as system-generated reports. Instead, let users continue to use the system, and use [toasts](/skyux/components/toast.md) to let them know when the content is available.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-long-load.1384bdfb7d805e18cd228c3ada554fb4.png)

Don't use flyouts for items that take a long time to load.

Don't use flyouts to link to external sites. Open external sites in new tabs. For example, when users select a constituent address, a Google map of that address opens in a new tab.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-external.2515ad21661ea3c7067bc1d625046ef9.png)

Don't use flyouts to display external content.

Don't use flyouts for tasks where users require a full-screen view of details or where they take multiple actions within the view. Navigate to a full page instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/not-need-full.f523b4a4b239e6ceecfd68fb229d56a1.png)

Don't use flyouts for tasks that require a full-screen view.

 Behavior and states
--------------------

### Background page remains active

The background page remains active behind a flyout. When users select a link on the background page to open another record in a list, the flyout loads the new record. When users select a link inside the flyout, the system navigates away from the current page.

When users select a non-interactive element on the background page, the flyout closes. However, when users select a non-interactive element on the background page on touch devices, the flyout does not close because users need to be able touch the background page in order to scroll.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-bg-active-1.1594c9a3747a0b8d68ae46632e36a661.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-bg-active-2.f4e230342b56ebc4332526ac69e664be.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-bg-active-3.73b3d6f8f55830a7024b8dc26c8d9b70.png)

### Independent scrolling

The flyout and its background page scroll independently. When users touch, hover, or focus on the background page, only the background content scrolls. Similarly, when users touch, hover, or focus on the flyout, only the flyout scrolls. This allows users to adjust the content in the flyout without losing context from the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-scroll-1.1594c9a3747a0b8d68ae46632e36a661.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-scroll-2.d617f36534374628900ecadf7491c542.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-scroll-3.a60818e7b8ee720e543f13648e11a4eb.png)

### Drag to resize

Users can select the flyout's left border and drag it to adjust the size. The size can range from 320px to 20px less than the full screen size. If users expand the flyout to the full screen size, it slides 20px to the right to keep a portion of the background page in view. The default size is 50 percent of the screen or 320px, whichever is larger. When users resize the panel, the system remembers their preferred size globally.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-resize-1.1594c9a3747a0b8d68ae46632e36a661.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-resize-2.c5fce5bc61761490da48ed2a7bc7b89c.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-resize-3.a204523d01307cfaf03750609e68602a.png)

### Help panel

The flyout covers the omnibar, but the help panel remains visible in the upper right corner of the screen. The help panel should recognize that the flyout is open and provide appropriate guidance based on the context.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-help-1.1594c9a3747a0b8d68ae46632e36a661.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-help-2.9ea207f70cbb25f87ce49c2604cd9a8d.png)

### Modal dialog behavior

When users perform actions in the flyout to launch modal dialogs, the modal dialogs should cover the entire page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/ixn-modal.639f26e7da41ca5c32c6d68ee718914f.png)

### Responsiveness

Do not use a flyout when a screen is smaller than 480px. At smaller resolutions, the flyout covers too much of the screen and loses much of its value. For smaller screen sizes, navigate directly to the appropriate record or list.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/flyout-mobile.a4b616d47ea5acbef340d78f9e42ca85.png)

 Options
--------

### Next and previous buttons

When a flyout opens records in a list, you can include buttons in the toolbar to open the next record or previous record. For example, if users open a flyout on a constituent record to view the first gift in a list of gifts, the next button opens the second gift in the list. When you include the next and previous buttons in the flyout toolbar, a visual indicator highlights the currently selected row on the page.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/opt-arrows.12698a1f532dbe6dc25ccb81097d7bcb.png)

### List toolbar

When a flyout displays a list, you can include an option in the toolbar to leave the "preview" list and create a new list for further manipulation. The create list button navigates to a new page that contains the new list.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/flyout/img/guidelines/flyout/opt-list.0017c6a8b67744dacfa075af6a868cf4.png)

 Accessibility
--------------

Follow these guidelines to ensure that people can use flyouts with assistive technology or keyboards.

*   When a flyout opens, place focus on the first focusable item. If the flyout does not include focusable items, then place focus on the flyout container element.
    
*   While a flyout is open, limit focus to elements in the flyout. Do not move focus back to the initiating page behind the flyout. On the last focusable item, the Tab key should return focus to the first focusable item. And on the first focusable item, the Shift+Tab keys should switch focus to the last focusable item.
    
*   When a flyout closes, return focus to the element that had focus before the flyout opened. This is usually the element that opened the flyout.
    

 Related information
--------------------

### Guidelines

*   [Content containers](/skyux/design/guidelines/content-containers.md)

 Installation
-------------

NPM package

`@skyux/flyout`[View in NPM](https://www.npmjs.com/package/@skyux/flyout) | [View in GitHub](https://github.com/blackbaud/skyux/blob/main
/libs/components/flyout/src/lib/modules/flyout/flyout.service.ts#L36) None found.

Install with NPMShow help content for

`npm install --save-exact @skyux/flyout`Copy None found.

 SkyFlyoutService
-----------------

Type: Service

Launches flyouts and provides a common look and feel. This service dynamically generates the flyout component and appends it directly to the document's `body` element. The `SkyFlyoutInstance` class watches for and triggers flyout events.

### Methods

#### `close(args?: SkyFlyoutCloseArgs): void`

Closes the flyout. This method also removes the flyout's HTML elements from the DOM.

#### Parameters

##### `args?: SkyFlyoutCloseArgs`

Arguments used when closing the flyout.

#### Returns

`void`

#### `open(component: Type<T>, config?: SkyFlyoutConfig): SkyFlyoutInstance<T>`

Opens a flyout and displays the specified component.

#### Parameters

##### `component: Type<T>`

Specifies the component to render.

##### `config?: SkyFlyoutConfig`

Specifies the flyout configuration passed to the specified component's constructor.

#### Returns

`SkyFlyoutInstance<T>`

 SkyFlyoutConfig
----------------

Type: Interface

Specifies the configuration options to set up a flyout.

    interface SkyFlyoutConfig {
      ariaDescribedBy?: string;
      ariaLabel?: string;
      ariaLabelledBy?: string;
      ariaRole?: string;
      defaultWidth?: number;
      iteratorNextButtonDisabled?: boolean;
      iteratorPreviousButtonDisabled?: boolean;
      maxWidth?: number;
      minWidth?: number;
      permalink?: SkyFlyoutPermalink;
      primaryAction?: SkyFlyoutAction;
      providers?: any[];
      settingsKey?: string;
      showIterator?: boolean;
    }

### Properties

#### `ariaDescribedBy?: string`

The HTML element ID of the element that describes the flyout. This sets the flyout's `aria-describedby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). The description typically includes text on the flyout but not on items that users interact with, such as buttons and forms. For more information about the `aria-describedby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-describedby).

#### `ariaLabel?: string`

The ARIA label for the flyout. This sets the flyouts's `aria-label` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the flyout includes a visible label, use `ariaLabelledBy` instead. For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).

#### `ariaLabelledBy?: string`

The HTML element ID of the element that labels the flyout. This sets the flyout's `aria-labelledby` attribute to provide a text equivalent for screen readers [to support accessibility](/skyux/learn/accessibility.md). If the flyout does not include a visible label, use `ariaLabel` instead. For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).

#### `ariaRole?: string`

Warning: **Deprecated.** Since version `5.1.0`. Consumers should use the default `dialog` role to ensure a proper accessibility implementation.

The ARIA role for the flyout [to support accessibility](/skyux/learn/accessibility.md) by indicating how the flyout functions and what it controls. For information about how an ARIA role indicates what an item represents on a web page, see the [WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles).

#### `defaultWidth?: number`

The default width of the flyout container. If you do not provide a width, the flyout defaults to half the width of its container.

#### `iteratorNextButtonDisabled?: boolean`

Disables the next iterator button in the flyout header that accesses the next record in a record set.

#### `iteratorPreviousButtonDisabled?: boolean`

Disables the previous iterator button in the flyout header that accesses the previous record in a record set.

#### `maxWidth?: number`

The maximum resize width of the flyout container.

#### `minWidth?: number`

The minimum resize width of the flyout container.

#### `permalink?: SkyFlyoutPermalink`

Displays a permalink button in the flyout header that navigates users to the URL (or application route) representative of the flyout's contents.

#### `primaryAction?: SkyFlyoutAction`

Displays a configurable button in the flyout header.

#### `providers?: any[]`

The array of custom providers to pass to the component's constructor.

#### `settingsKey?: string`

The unique key for the UI Config Service to retrieve stored settings from a database. The UI Config Service saves configuration settings for users to preserve the width of the flyout. For more information about the UI Config Service, see [the sticky settings documentation](/skyux/learn/develop/sticky-settings.md).

#### `showIterator?: boolean`

Whether to display iterator buttons in the flyout header to access the next and previous records in a record set.

 SkyFlyoutInstance
------------------

Type: Class

Represents a single displayed flyout.

### Properties

#### `closed: EventEmitter<void>`

An event that the flyout instance emits when it closes.

#### `componentInstance: T`

The instance of the component to display in the flyout.

#### `isOpen: boolean`

A `boolean` value that returns `true` if the flyout is open.

Default: `true`

#### `beforeClose: Observable<SkyFlyoutBeforeCloseHandler>`

An event that the flyout instance emits when it is about to close. If a subscription exists for this event, the flyout does not close until the subscriber calls the handler's `closeModal` method.

#### `iteratorNextButtonClick: EventEmitter<void>`

An event that the flyout instance emits when users click the next iterator button.

#### `iteratorNextButtonDisabled: boolean`

Disables the next iterator button.

Default: `false`

#### `iteratorPreviousButtonClick: EventEmitter<void>`

An event that the flyout instance emits when users click the previous iterator button.

#### `iteratorPreviousButtonDisabled: boolean`

Disables the previous iterator button.

Default: `false`

### Methods

#### `close(args?: SkyFlyoutCloseArgs): void`

Closes the flyout instance and emits its `closed` event.

#### Parameters

##### `args?: SkyFlyoutCloseArgs`

Arguments used when closing the flyout.

#### Returns

`void`

 SkyFlyoutAction
----------------

Type: Interface

    interface SkyFlyoutAction {
      callback?: () => void;
      closeAfterInvoking?: boolean;
      label?: string;
    }

### Properties

#### `callback?: () => void`

The callback function to execute when the button is clicked.

#### `closeAfterInvoking?: boolean`

Whether to close the flyout after the button is clicked.

#### `label?: string`

The button's label.

 SkyFlyoutBeforeCloseHandler
----------------------------

Type: Class

Handler for notifying the flyout when it is appropriate to close the flyout. This will be returned from the flyout instance's `beforeClose` observable.

### Properties

#### `closeFlyout: () => void`

Function which should be called to close the flyout. This should be called once any intervening actions have completed.

 SkyFlyoutCloseArgs
-------------------

Type: Interface

Arguments used when closing a flyout programmatically.

    interface SkyFlyoutCloseArgs {
      ignoreBeforeClose?: boolean;
    }

### Properties

#### `ignoreBeforeClose?: boolean`

Whether the `SkyFlyoutBeforeCloseHandler` is ignored when closing a flyout.

 SkyFlyoutPermalink
-------------------

Type: Interface

    interface SkyFlyoutPermalink {
      label?: string;
      route?: { commands: any[]; extras?: NavigationExtras };
      url?: string;
    }

### Properties

#### `label?: string`

The text label for the permalink button.

#### `route?: { commands: any[]; extras?: NavigationExtras }`

The object that represents the [Angular application route](https://angular.io/api/router/Router#navigate). The object includes two properties that are mapped to Angular's `Router.navigate(commands, extras?)` method.

#### `url?: string`

The external URL for the permalink.

SKY UX test harnesses are built upon Angular CDK component harnesses. For more information see the [Angular CDK component harness documentation](https://material.angular.io/cdk/test-harnesses/overview).

 SkyFlyoutHarness
-----------------

Type: Class

`import { SkyFlyoutHarness } from '@skyux/flyout/testing';`

Harness for interacting with a flyout component in tests.

### Methods

#### `clickNextIteratorButton(): Promise<void>`

Clicks the flyout's next iterator button.

#### Returns

`Promise<void>`

#### `clickPreviousIteratorButton(): Promise<void>`

Clicks the flyout's previous iterator button.

#### Returns

`Promise<void>`

#### `clickPrimaryActionButton(): Promise<void>`

Clicks the flyout's primary action button.

#### Returns

`Promise<void>`

#### `closeFlyout(): Promise<void>`

Clicks the flyout's close button.

#### Returns

`Promise<void>`

#### `getAriaDescribedBy(): Promise<null | string>`

Gets the flyout's aria-describedby attribute.

#### Returns

`Promise<null | string>`

#### `getAriaLabel(): Promise<null | string>`

Gets the flyout's aria-label attribute.

#### Returns

`Promise<null | string>`

#### `getAriaLabelledBy(): Promise<null | string>`

Gets the flyout's aria-labelledby attribute.

#### Returns

`Promise<null | string>`

#### `getAriaRole(): Promise<null | string>`

Gets the flyout's ARIA role.

#### Returns

`Promise<null | string>`

#### `getFlyoutMaxWidth(): Promise<number>`

Gets the flyout's maximum width.

#### Returns

`Promise<number>`

#### `getFlyoutMinWidth(): Promise<number>`

Gets the flyout's minimum width.

#### Returns

`Promise<number>`

#### `getFlyoutWidth(): Promise<number>`

Gets the flyout's current width.

#### Returns

`Promise<number>`

#### `getPermalinkButtonLabel(): Promise<string>`

Gets the label for the flyout's permalink button.

#### Returns

`Promise<string>`

#### `getPermalinkButtonRoute(): Promise<null | string>`

Gets the route for the flyout's permalink button.

#### Returns

`Promise<null | string>`

#### `getPrimaryActionButtonLabel(): Promise<string>`

Gets the label for the flyout's primary action button.

#### Returns

`Promise<string>`

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