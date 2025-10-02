---
component: 'action-hub'
type: 'api-documentation'
description: 'API documentation for the action-hub component including components, interfaces, and types.'
---

# Action Hub API Documentation

## Components and Directives

#### PagesActionHubExampleComponent

**Selector:** `app-pages-action-hub-example`

**Package:** `@skyux/code-examples`

#### SkyActionHubButtonsComponent

Displays buttons after the page title.

**Selector:** `sky-action-hub-buttons`

**Package:** `@skyux/pages`

#### SkyActionHubContentComponent

Displays additional content after the action items.

**Selector:** `sky-action-hub-content`

**Package:** `@skyux/pages`

#### SkyActionHubComponent

Creates an action hub to direct user attention to important
actions and provide quick access to common tasks.

**Selector:** `sky-action-hub`

**Package:** `@skyux/pages`

**Inputs:**

- `parentLink`: `SkyPageLink | undefined` - Links back to a parent page.
- `recentLinks`: `SkyRecentLinksInput` - The list of recently accessed links, or `"loading"` to display a wait indicator. (default: [])
- `relatedLinks`: `SkyPageLinksInput` - The list of related links, or `"loading"` to display a wait indicator. (default: [])
- `settingsLinks`: `SkyPageModalLinksInput` - The list of settings with modal parameters, or `"loading"` to display a wait indicator. (default: [])
- `title`: `string` - The page title. (default: "")
- `needsAttention`: `SkyActionHubNeedsAttentionInput | undefined` - The list of actions that users must perform based on business requirements or best practices, or `"loading"` to display a wait indicator.