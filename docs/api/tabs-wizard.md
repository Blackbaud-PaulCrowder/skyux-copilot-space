---
component: 'tabs-wizard'
type: 'api-documentation'
description: 'API documentation for the tabs-wizard component including components, interfaces, and types.'
---

# Tabs Wizard API Documentation

## Components and Directives

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