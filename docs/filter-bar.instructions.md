---
component: 'filter-bar'
description: 'Design guidelines, API documentation, and usage instructions for the filter-bar component extracted from SKY UX documentation.'
---

# Filter Bar Component Guidelines

## Component Overview
The filter bar presents users with inline filter options to narrow lists. It allows for a large number of filter options. The filter bar component does not currently integrate the data manager component, but integration is coming soon.

## Usage

### ✅ Use when

Use the filter bar when the main or only task on a page is to narrow a collection of items or manipulate a pre-filtered collection. Use a filter bar or tabs to support the filtering tasks on dedicated full-page lists, such as list pages or in tabs on record pages.

**✅ Do use the filter bar with full-page lists on list pages.**

Use the filter bar with pre-filtered lists where filters are already active when:

- Users need to adjust preset filter values or add additional filters to refine lists.
- Users access lists through calls to action and need to further narrow the lists before taking action.

### ❌ Don't use when

Don't use the filter bar when:

- Users need regular access to a small number of lists.
- One list in a small group of lists needs priority or will be used most frequently.
- A small number of lists have different tasks for users to complete.

Use pre-filtered lists in tabs instead.

## Anatomy

- Toolbar divider
- Filter bar label
- Filter button (filter not set)
- Filter button (filter set)
- Clear filters button
- Filter chooser button

## Options

### Filter chooser

When a list requires many filters to give users multiple ways to narrow the collection of items, include a filter chooser to let users select the filters to include in the filter bar.

Within filter choosers, organize filters alphabetically. If some filters will be used most of the time, include them directly in the filter bar by default.

**The filter chooser button opens a modal to select the filters to enable in the filter bar.**

## Behavior and states

### Filter types

The filter bar can support multiple types of selection methods for filtering. Use the following filter types for selection and display of filters in the filter bar.

### Clear all values

When users select Clear all values, confirm their intention with a confirmation modal before removing the filter values to avoid losing their work by mistake.

### Updates to summary details

When filters or search criteria are applied to a list, update the list count and summary details to reflect the filtered list. Add "match" to the list count label to reflect the list is in a filtered state.

**✅ Do update summary details when filters or search criteria are applied to a list. To provide context, update the list count label to include 'match.'**

## Content

## Related information

### Guidelines

- Form design

## API Documentation

### Components and Directives

#### FilterBarBasicExampleComponent

**Selector:** `app-filter-bar-basic-example`

**Package:** `@skyux/code-examples`

#### SkyFilterBarComponent

The top-level filter bar component.

**Selector:** `sky-filter-bar`

**Package:** `@skyux/filter-bar`

**Inputs:**

- `appliedFilters`: `ModelSignal<undefined | SkyFilterBarFilterItem[]>` - An array of filter items containing the IDs and values of the filters that have been set.
- `selectedFilterIds`: `ModelSignal<undefined | string[]>` - An array of filter IDs that the user has selected using the built-in selection modal. Setting this input to undefined results in all filters being displayed.

#### SkyFilterBarModule

**Package:** `@skyux/filter-bar`

#### SkyFilterBarFilterItem

Represents a specific filter item and its selected value, if any.

**Package:** `@skyux/filter-bar`

#### SkyFilterBarFilterValue

Represents a value for a filter item.

**Package:** `@skyux/filter-bar`

#### SkyFilterBarHarnessFilters

A set of criteria that can be used to filter a list of `SkyFilterBarHarness` instances.

**Package:** `@skyux/filter-bar/testing`

#### SkyFilterBarHarness

Harness for interacting with a filter bar component in tests.

**Package:** `@skyux/filter-bar/testing`

### Code Examples

#### Filter bar basic example

**Selector:** `app-filter-bar-basic-example`

**TypeScript:**

```typescript
import { Component, model } from '@angular/core';
import {
  SkyFilterBarFilterItem,
  SkyFilterBarModule,
  SkyFilterItemModalOpenedArgs,
} from '@skyux/filter-bar';

import { of } from 'rxjs';

import { FilterItems } from './filter-items';
import { CommunityConnectionFilterModalComponent } from './filter-modals/community-connection-filter-modal.component';
import { CurrentGradeFilterModalComponent } from './filter-modals/current-grade-filter-modal.component';
import { EnteringGradeFilterModalComponent } from './filter-modals/entering-grade-filter-modal.component';
import { RoleFilterModalComponent } from './filter-modals/role-filter-modal.component';
import { StaffAssignedFilterModalComponent } from './filter-modals/staff-assigned-filter-modal.component';
import { FILTER_SELECTION_VALUES } from './filter-selection-values';

/**
 * @title Filter bar basic example
 */
@Component({
  selector: 'app-filter-bar-basic-example',
  imports: [SkyFilterBarModule],
  templateUrl: './example.component.html',
})
export class FilterBarBasicExampleComponent {
  protected readonly appliedFilters = model<
    SkyFilterBarFilterItem[] | undefined
  >();
  protected readonly selectedFilterIds = model<string[] | undefined>([
    'staff-assigned',
    'entering-grade',
    'current-grade',
  ]);

  protected communityConnectionModal = CommunityConnectionFilterModalComponent;
  protected currentGradeModal = CurrentGradeFilterModalComponent;
  protected enteringGradeModal = EnteringGradeFilterModalComponent;
  protected roleModal = RoleFilterModalComponent;
  protected staffAssignedModal = StaffAssignedFilterModalComponent;

  protected onModalOpened(
    args: SkyFilterItemModalOpenedArgs<FilterItems>,
  ): void {
    args.data = of({ items: FILTER_SELECTION_VALUES[args.filterId] });
  }
}

```

**Template:**

```html
<sky-filter-bar
  [(appliedFilters)]="appliedFilters"
  [(selectedFilterIds)]="selectedFilterIds"
>
  <sky-filter-item-modal
    filterId="community-connection"
    labelText="Community connection"
    modalSize="medium"
    [modalComponent]="communityConnectionModal"
    (modalOpened)="onModalOpened($event)"
  />
  <sky-filter-item-modal
    filterId="current-grade"
    labelText="Current grade"
    modalSize="medium"
    [modalComponent]="currentGradeModal"
    (modalOpened)="onModalOpened($event)"
  />
  <sky-filter-item-modal
    filterId="entering-grade"
    labelText="Entering grade"
    modalSize="medium"
    [modalComponent]="enteringGradeModal"
    (modalOpened)="onModalOpened($event)"
  />
  <sky-filter-item-modal
    filterId="role"
    labelText="Role"
    modalSize="medium"
    [modalComponent]="roleModal"
    (modalOpened)="onModalOpened($event)"
  />
  <sky-filter-item-modal
    filterId="staff-assigned"
    labelText="Staff assigned"
    modalSize="medium"
    [modalComponent]="staffAssignedModal"
    (modalOpened)="onModalOpened($event)"
  />
</sky-filter-bar>

```

## Related Information

For additional examples and complete API documentation, refer to the official SKY UX documentation.