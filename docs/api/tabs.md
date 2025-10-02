---
component: 'tabs'
type: 'api-documentation'
description: 'API documentation for the tabs component including components, interfaces, and types.'
---

# Tabs API Documentation

## Components and Directives

#### PagesPageListPageTabsLayoutExampleComponent

**Selector:** `app-pages-page-list-page-tabs-layout-example`

**Package:** `@skyux/code-examples`

#### PagesPageRecordPageTabsLayoutExampleComponent

**Selector:** `app-pages-page-record-page-tabs-layout-example`

**Package:** `@skyux/code-examples`

#### TabsSectionedFormModalExampleComponent

**Selector:** `app-tabs-sectioned-form-modal-example`

**Package:** `@skyux/code-examples`

#### TabsDynamicAddCloseExampleComponent

**Selector:** `app-tabs-dynamic-add-close-example`

**Package:** `@skyux/code-examples`

#### TabsDynamicExampleComponent

**Selector:** `app-tabs-dynamic-example`

**Package:** `@skyux/code-examples`

#### TabsStaticAddCloseExampleComponent

**Selector:** `app-tabs-static-add-close-example`

**Package:** `@skyux/code-examples`

#### TabsStaticExampleComponent

**Selector:** `app-tabs-static-example`

**Package:** `@skyux/code-examples`

#### TabsVerticalTabsBasicExampleComponent

**Selector:** `app-tabs-vertical-tabs-basic-example`

**Package:** `@skyux/code-examples`

#### TabsVerticalTabsGroupedExampleComponent

**Selector:** `app-tabs-vertical-tabs-grouped-example`

**Package:** `@skyux/code-examples`

#### TabsVerticalTabsMixedExampleComponent

**Selector:** `app-tabs-vertical-tabs-mixed-example`

**Package:** `@skyux/code-examples`

#### TabsWizardBasicExampleComponent

**Selector:** `app-tabs-wizard-basic-example`

**Package:** `@skyux/code-examples`

#### SkyTabComponent

**Selector:** `sky-tab`

**Package:** `@skyux/tabs`

**Inputs:**

- `disabled`: `boolean | undefined` - Whether to disable the tab. (default: false)
- `tabHeaderCount`: `string | undefined` - Displays a counter beside the tab header.
This input only applies when the tabset's `tabStyle` is `"tabs"`.
- `active`: `boolean` - Whether the tab is active when the tabset loads. After initialization, the `active`
property on the tabset component should be used to set the active tab. (default: false)
- `layout`: `SkyTabLayoutType` - The tab layout that applies spacing to the tab container element. Use the layout
that corresponds with the top-level component type used within the tab, or use `fit` to
constrain the tab contents to the available viewport.
Use `none` for custom content that does not adhere to predefined spacing or constraints. (default: "none")
- `permalinkValue`: `string | undefined` - The custom query parameter value for the tab.
This works in conjunction with the tabset's `permalinkId` to distinguish
the tab's unique state in the URL by generating a query parameter that is
written as `?<queryParam>-active-tab=<sanitized-tab-heading`.
By default, the query parameter's value is parsed automatically from the tab's heading text.
This input only applies when the tabset's `tabStyle` is `"tabs"`.
- `tabHeading`: `string | undefined` - The tab header.
When using tabs as the main navigation on a page,
use [the Angular `Title` service](https://angular.io/docs/ts/latest/cookbook/set-document-title.html)
and [the SKY UX `title` configuration property](https://developer.blackbaud.com/skyux/learn/reference/configuration#app)
to reflect the tab header in the page title.
- `tabIndexValue`: `SkyTabIndex | undefined` - The unique identifier for the tab.
If not defined, the identifier is set to the position of the tab on load, starting with `0`.

**Outputs:**

- `close`: `EventEmitter<void>` - Fires when users click the button to close the tab.
The close button is added to the tab when you specify a listener for this event.
This event only applies when the tabset's `tabStyle` is `"tabs"`.

#### SkyTabsetNavButtonComponent

Creates a button to navigate between tabs in a tabset when `tabStyle` is `"wizard"`.

**Selector:** `sky-tabset-nav-button`

**Package:** `@skyux/tabs`

**Inputs:**

- `buttonText`: `string` - The label to display on the nav button. The following are the defaults for each `buttonType`:
`next` = "Next", `previous` = "Previous", `finish` = "Finish"
- `buttonType`: `SkyTabsetNavButtonType | undefined` - The type of nav button to include.
- `disabled`: `boolean | undefined` - Whether to disable the nav button.
Defaults to the disabled state of the next tab for `next`, the existence of a previous tab for `previous`,
and false for `finish`.
- `tabset`: `SkyTabsetComponent | undefined` - The tabset wizard component to associate with the nav button.

#### SkyTabsetComponent

**Selector:** `sky-tabset`

**Package:** `@skyux/tabs`

**Inputs:**

- `ariaLabel`: `string | undefined` - The ARIA label for the tabset. This sets the tabset's `aria-label` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the tabset includes a visible label, use `ariaLabelledBy` instead.
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `ariaLabelledBy`: `string | undefined` - The HTML element ID of the element that labels
the tabset. This sets the tabset's `aria-labelledby` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the tabset does not include a visible label, use `ariaLabel` instead.
For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).
- `active`: `SkyTabIndex | undefined` - Activates a tab by its `tabIndex` property.
- `permalinkId`: `string` - Distinguishes a tabset's unique state in the URL by generating a query parameter
that is written as `?<queryParam>-active-tab=<sanitized-tab-heading>`.
The query parameter's value is parsed automatically from the selected tab's heading text,
but you can supply a custom query parameter value for each tab with its `permalinkValue`.
This input only applies when `tabStyle` is `"tabs"`
- `tabStyle`: `SkyTabsetStyle` - The behavior for a series of tabs. (default: "tabs")

**Outputs:**

- `activeChange`: `EventEmitter<SkyTabIndex>` - Fires when the active tab changes. This event emits the index of the active tab.
- `newTab`: `EventEmitter<void>` - Fires when users click the button to add a new tab.
The new tab button is added to the tab area when you specify a listener for this event.
This event only applies when `tabStyle` is `"tabs"`.
- `openTab`: `EventEmitter<void>` - Fires when users click the button to open a tab.
The open tab button is added to the tab area when you specify a listener for this event.
This event only applies when `tabStyle` is `"tabs"`.
- `tabIndexesChange`: `EventEmitter<SkyTabsetTabIndexesChange>` - Fires when any tab's `tabIndex` value changes.
This event only applies when `tabStyle` is `"tabs"`.

#### SkyVerticalTabsetGroupComponent

**Selector:** `sky-vertical-tabset-group`

**Package:** `@skyux/tabs`

**Inputs:**

- `groupHeading`: `string | undefined` - The header for the collapsible group of tabs.
- `disabled`: `boolean | undefined` - Whether to disable the ability to expand and collapse the group. (default: false)
- `open`: `boolean | undefined` - Whether the collapsible group is expanded. (default: false)

#### SkyVerticalTabsetComponent

**Selector:** `sky-vertical-tabset`

**Package:** `@skyux/tabs`

**Inputs:**

- `ariaLabel`: `string | undefined` - The ARIA label for the tabset. This sets the tabset's `aria-label` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the tabset includes a visible label, use `ariaLabelledBy` instead.
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `ariaLabelledBy`: `string | undefined` - The HTML element ID of the element that labels
the tabset. This sets the tabset's `aria-labelledby` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
If the tabset does not include a visible label, use `ariaLabel` instead.
For more information about the `aria-labelledby` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-labelledby).
- `maintainTabContent`: `boolean | undefined` - Whether the vertical tabset loads tab content during initialization so that it
displays content without moving around elements in the content container. (default: false)
- `showTabsText`: `string | undefined` - The text to display on the show tabs button on mobile devices.
- `ariaRole`: `string` - The ARIA role for the vertical tabset
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility)
by indicating how the tabset functions and what it controls. For information about how
an ARIA role indicates what an item represents on a web page, see the
[WAI-ARIA roles model](https://www.w3.org/WAI/PF/aria/#roles). (default: "tablist")

**Outputs:**

- `activeChange`: `EventEmitter<number>` - Fires when the active tab changes. Emits the index of the active tab. The
index is based on the tab's position when it loads.