---
component: 'modal'
type: 'api-documentation'
description: 'API documentation for the modal component including components, interfaces, and types.'
---

# Modal API Documentation

## Components and Directives

#### ActionBarsSummaryActionBarModalExampleComponent

**Selector:** `app-action-bars-summary-action-bar-modal-example`

**Package:** `@skyux/code-examples`

#### ErrorsErrorModalExampleComponent

**Selector:** `app-errors-error-modal-example`

**Package:** `@skyux/code-examples`

#### LayoutTextExpandModalExampleComponent

**Selector:** `app-layout-text-expand-modal-example`

**Package:** `@skyux/code-examples`

#### ListsFilterModalExampleComponent

**Selector:** `app-lists-filter-modal-example`

**Package:** `@skyux/code-examples`

#### LookupSelectionModalAddItemExampleComponent

**Selector:** `app-lookup-selection-modal-add-item-example`

**Package:** `@skyux/code-examples`

#### LookupSelectionModalBasicExampleComponent

**Selector:** `app-lookup-selection-modal-basic-example`

**Package:** `@skyux/code-examples`

#### ModalsConfirmBasicWithControllerExampleComponent

**Selector:** `app-modals-confirm-basic-with-controller-example`

**Package:** `@skyux/code-examples`

#### ModalsConfirmBasicWithHarnessExampleComponent

**Selector:** `app-modals-confirm-basic-with-harness-example`

**Package:** `@skyux/code-examples`

#### ModalsModalBasicWithControllerExampleComponent

**Selector:** `app-modals-modal-basic-with-controller-example`

**Package:** `@skyux/code-examples`

#### ModalsModalBasicWithHarnessHelpKeyExampleComponent

**Selector:** `app-modals-modal-basic-with-harness-help-key-example`

**Package:** `@skyux/code-examples`

#### ModalsModalBasicWithHarnessExampleComponent

**Selector:** `app-modals-modal-basic-with-harness-example`

**Package:** `@skyux/code-examples`

#### ModalsModalWithErrorExampleComponent

**Selector:** `app-modals-modal-with-error-example`

**Package:** `@skyux/code-examples`

#### TabsSectionedFormModalExampleComponent

**Selector:** `app-tabs-sectioned-form-modal-example`

**Package:** `@skyux/code-examples`

#### SkyTextEditorUrlModalComponent

**Selector:** `sky-text-editor-url-modal`

**Package:** `@skyux/text-editor`

#### SkyFilterItemModalComponent

A filter bar item that opens a modal for complex filter configuration.
Use this component when your filter requires a rich UI with multiple inputs,
date pickers, or other complex controls that don't fit in an inline filter.

**Selector:** `sky-filter-item-modal`

**Package:** `@skyux/filter-bar`

**Inputs:**

- `filterId`: `InputSignal<string>` - A unique identifier for the filter item.
- `labelText`: `InputSignal<string>` - The label to display for the filter item.
- `modalComponent`: `InputSignal<Type<SkyFilterItemModal<TData>>>` - The modal component to display when the user selects the filter.
The component needs to inject a `SkyFilterItemModalInstance` object on instantiation to receive the modal instance and context from the modal service.
The return value of the modal save action needs to be a `SkyFilterBarFilterValue`.
- `modalSize`: `InputSignal<SkyFilterItemModalSizeType>` - The size of the modal to display. The valid options are `"small"`, `"medium"`, `"large"`, and `"fullScreen"`.

**Outputs:**

- `modalOpened`: `EventEmitter<SkyFilterItemModalOpenedArgs<TData>>` - Fires when the user clicks the filter item. To pass additional context data to a filter modal, consumers
must subscribe to this event and return the context using the observable property on the event args.

#### SkyModalContentComponent

Specifies content to display in the modal's body.

**Selector:** `sky-modal-content`

**Package:** `@skyux/modals`

#### SkyModalFooterComponent

Specifies content to display in the modal's footer.

**Selector:** `sky-modal-footer`

**Package:** `@skyux/modals`

#### SkyModalHeaderComponent

Specifies a header for the modal.

**Selector:** `sky-modal-header`

**Package:** `@skyux/modals`

#### SkyModalIsDirtyDirective

Provides a way to mark a modal as "dirty" and displays a confirmation
message when a user closes the modal without saving.

**Selector:** `sky-modal[isDirty]`

**Package:** `@skyux/modals`

**Inputs:**

- `isDirty`: `boolean` - Whether the user edited an input on the modal. (default: false)

#### SkyModalComponent

Provides a common look-and-feel for modal content with options to display
a common modal header, specify body content, and display a common modal footer
and buttons.

**Selector:** `sky-modal`

**Package:** `@skyux/modals`

**Inputs:**

- `headingText`: `string | undefined` - The text to display as the modal's heading.
- `helpKey`: `string | undefined` - A help key that identifies the global help content to display. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline) button is
added to the modal header. Clicking the button invokes global help as configured by the application. This property only applies when `headingText` is also specified.
- `helpPopoverContent`: `string | TemplateRef<unknown> | undefined` - The content of the help popover. When specified along with `headingText`, a [help inline](https://developer.blackbaud.com/skyux/components/help-inline)
button is added to the modal header. The help inline button displays a [popover](https://developer.blackbaud.com/skyux/components/popover)
when clicked using the specified content and optional title. This property only applies when `headingText` is also specified.
- `helpPopoverTitle`: `string | undefined` - The title of the help popover. This property only applies when `helpPopoverContent` is
also specified.
- `layout`: `InputSignal<"none" | "fit">`
- `tiledBody`: `boolean | undefined`
- `ariaDescribedBy`: `string | undefined` - Used by the confirm component to set descriptive text without using a
modal header.
- `ariaLabelledBy`: `string | undefined` - Used by the confirm component to set descriptive text without using a
modal header.
- `ariaRole`: `string | undefined` - Used by the confirm component to set a different role for the modal.
- `formErrors`: `SkyModalError[] | undefined` - A list of form-level errors to display to the user.

#### SkyModalLinkListComponent

A component that displays a list of links such as within a `<sky-page-links>` component.

**Selector:** `sky-modal-link-list`

**Package:** `@skyux/pages`

**Inputs:**

- `headingText`: `InputSignal<undefined | string>` - The text to display as the list's heading.
- `links`: `InputSignal<SkyPageModalLinksInput>` - Option to pass links as an array of `SkyPageModalLink` objects or `'loading'` to display a loading indicator.