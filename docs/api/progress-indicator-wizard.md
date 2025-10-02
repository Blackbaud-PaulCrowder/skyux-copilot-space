---
component: 'progress-indicator-wizard'
type: 'api-documentation'
description: 'API documentation for the progress-indicator-wizard component including components, interfaces, and types.'
---

# Progress Indicator Wizard API Documentation

## Components and Directives

#### SkyProgressIndicatorComponent

**Selector:** `sky-progress-indicator`

**Package:** `@skyux/progress-indicator`

**Inputs:**

- `displayMode`: `SkyProgressIndicatorDisplayModeType` - The orientation of the progress indicator, which can be vertical or horizontal.
For [passive progress indicators](https://developer.blackbaud.com/skyux/components/progress-indicator-passive)
and [waterfall progress indicators](https://developer.blackbaud.com/skyux/components/progress-indicator-waterfall),
use the vertical display mode. For [modal wizards](https://developer.blackbaud.com/skyux/components/progress-indicator-wizard),
use the horizontal display mode. (default: "vertical")
- `isPassive`: `boolean | undefined` - Whether the progress indicator is passive. Passive progress indicators inform users of
progress that concerns them but that they are not responsible for, and they must use the vertical display mode. (default: false)
- `messageStream`: `Subject<SkyProgressIndicatorMessage | SkyProgressIndicatorMessageType> | undefined` - The observable of `SkyProgressIndicatorMessage` that determines the status to
display for items in the progress indicator. The message stream is a queue of
commanding messages to change the state of the progress indicator based on the message type.
- `startingIndex`: `number` - The index for the item to make active when the progress indicator
loads. All steps that precede the active item are marked as complete, and all steps
that follow the active item are marked as incomplete.

**Outputs:**

- `progressChanges`: `EventEmitter<SkyProgressIndicatorChange>` - Fires when the progress indicator changes the status of an item.

#### ProgressIndicatorWizardBasicExampleComponent

**Selector:** `app-progress-indicator-wizard-basic-example`

**Package:** `@skyux/code-examples`