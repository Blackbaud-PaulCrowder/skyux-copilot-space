---
component: 'button'
type: 'api-documentation'
description: 'API documentation for the button component including components, interfaces, and types.'
---

# Button API Documentation

## Components and Directives

#### SkyProgressIndicatorNavButtonComponent

Displays a button to navigate the steps in modal wizards. We recommend against using it in
passive progress indicators and waterfall progress indicators.

**Selector:** `sky-progress-indicator-nav-button`

**Package:** `@skyux/progress-indicator`

**Inputs:**

- `buttonText`: `string | undefined` - The label to display on the nav button. (default: "Next")
- `buttonType`: `SkyProgressIndicatorNavButtonType` - The type of nav button to include. (default: "next")
- `disabled`: `boolean | undefined` - Whether to disable the nav button. (default: false)
- `progressIndicator`: `SkyProgressIndicatorComponent | undefined` - The progress indicator component to associate with the nav button.

**Outputs:**

- `actionClick`: `EventEmitter<SkyProgressIndicatorActionClickArgs>` - Fires when users select the nav button and emits a `SkyProgressIndicatorActionClickArgs`
object that is passed into the callback function to allow consumers to decide whether
the button’s action should complete successfully.

#### SkyProgressIndicatorResetButtonComponent

Displays a button to mark all items in the progress indicator as incomplete and set the
first item as the active item. The steps after the active item remain incomplete until
users reach them in their sequential order.

**Selector:** `sky-progress-indicator-reset-button`

**Package:** `@skyux/progress-indicator`

**Inputs:**

- `progressIndicator`: `SkyProgressIndicatorComponent | undefined` - The progress indicator component to associate with the reset button.
- `disabled`: `boolean | undefined` - Whether to disable the reset button. (default: false)

**Outputs:**

- `resetClick`: `EventEmitter<void>` - Fires when users select the reset button that marks all items as incomplete and sets the
first item as the active item.

#### IconIconButtonExampleComponent

**Selector:** `app-icon-icon-button-example`

**Package:** `@skyux/code-examples`

#### InlineFormCustomButtonsExampleComponent

**Selector:** `app-inline-form-custom-buttons-example`

**Package:** `@skyux/code-examples`

#### LayoutActionButtonBasicExampleComponent

**Selector:** `app-layout-action-button-basic-example`

**Package:** `@skyux/code-examples`

#### LayoutActionButtonPermalinkExampleComponent

**Selector:** `app-layout-action-button-permalink-example`

**Package:** `@skyux/code-examples`

#### SkyListFilterButtonComponent

Contains a filter button for the list toolbar. Place a
[`sky-filter-button`](https://developer.blackbaud.com/skyux/components/filter)
component inside this component to open a modal with filtering options.
To apply filter options, use the
[list component's](https://developer.blackbaud.com/skyux/components/list/overview#list-properties)
`appliedFilters` property.

**Selector:** `sky-list-filter-button`

**Package:** `@skyux/list-builder`

#### SkyDocsClipboardButtonDirective

**Selector:** `[skyDocsClipboardButton]`

**Package:** `@skyux/docs-tools`

**Inputs:**

- `clipboardTarget`: `InputSignal<HTMLElement>`
- `copySuccessMessage`: `InputSignal<string>`

#### SkyDropdownButtonComponent

Specifies the button for the dropdown menu.

**Selector:** `sky-dropdown-button`

**Package:** `@skyux/popovers`

#### SkyActionButtonContainerComponent

Wraps action buttons to ensures that they have consistent height and spacing.

**Selector:** `sky-action-button-container`

**Package:** `@skyux/layout`

**Inputs:**

- `alignItems`: `SkyActionButtonContainerAlignItemsType` - How to display the action buttons inside the action button container.
Options are `"center"` or `"left"`. (default: "center")

#### SkyActionButtonDetailsComponent

Specifies a description to display on an action button.

**Selector:** `sky-action-button-details`

**Package:** `@skyux/layout`

#### SkyActionButtonHeaderComponent

Specifies a header to display on an action button.

**Selector:** `sky-action-button-header`

**Package:** `@skyux/layout`

#### SkyActionButtonIconComponent

Specifies an icon to display on the action button.

**Selector:** `sky-action-button-icon`

**Package:** `@skyux/layout`

**Inputs:**

- `iconName`: `string` - The name of the Blackbaud SVG icon to display.

#### SkyActionButtonComponent

Creates a button to present users with an option to move forward with tasks.

**Selector:** `sky-action-button`

**Package:** `@skyux/layout`

**Inputs:**

- `permalink`: `SkyActionButtonPermalink | undefined` - The link for the action button.

**Outputs:**

- `actionClick`: `EventEmitter<any>` - Fires when users select the action button.

#### SkyFilterButtonComponent

**Selector:** `sky-filter-button`

**Package:** `@skyux/lists`

**Inputs:**

- `active`: `boolean | undefined` - Whether to highlight the filter button to indicate that filters were applied.
We recommend setting this property to `true` when no indication of filtering is visible
to users. For example, set it to `true` if you do not display the filter summary. (default: false)
- `ariaControls`: `string | undefined` - The ID to identify the element that contains
the filtering options that the filter button exposes.
To support [accessibility rules for disclosures](https://www.w3.org/TR/wai-aria-practices-1.1/#disclosure),
this property is necessary to set the `aria-controls` attribute when using inline filters.
For more information about the `aria-controls` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-controls).
- `ariaExpanded`: `boolean | undefined` - Whether the filtering options are exposed.
To support [accessibility rules for disclosures](https://www.w3.org/TR/wai-aria-practices-1.1/#disclosure),
this property is necessary to set the `aria-expanded` attribute when using inline filters.
For more information about the `aria-expanded` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-expanded). (default: false)
- `ariaLabel`: `string | undefined` - The ARIA label for the filter button. This sets the
filter button's `aria-label` attribute to provide a text equivalent for screen readers
[to support accessibility](https://developer.blackbaud.com/skyux/learn/accessibility).
Use a context-sensitive label, such as "Filter constituents." Context is especially important when multiple filter buttons are in close proximity.
In toolbars, filter buttons use the `listDescriptor` to provide context, and the ARIA label defaults to "Filter <listDescriptor>."
For more information about the `aria-label` attribute, see the [WAI-ARIA definition](https://www.w3.org/TR/wai-aria/#aria-label).
- `disabled`: `boolean | undefined` - Whether to disable the filter button. (default: false)
- `showButtonText`: `boolean | undefined` - Whether to display a "Filter" label beside the icon on the filter button. (default: false)
- `filterButtonId`: `string` - The ID for the filter button.

**Outputs:**

- `filterButtonClick`: `EventEmitter<void>` - Fires when the filter button is selected.

#### SkyActionHubButtonsComponent

Displays buttons after the page title.

**Selector:** `sky-action-hub-buttons`

**Package:** `@skyux/pages`

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