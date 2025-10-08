              Skip to Main Content

 1.  [Home](/skyux/)
2.  [Design](/skyux/design.md)
3.  [Guidelines](/skyux/design/guidelines.md)
4.  [Filtering lists](/skyux/design/guidelines/filtering-lists.md)

Filtering lists
===============

Filters enable users to adjust lists to only display the items that match their specific criteria.

On this page
============

1.  [Principles](/skyux/design/guidelines/filtering-lists#principles.md)
2.  [Usage](/skyux/design/guidelines/filtering-lists#usage.md)
3.  [Contexts for filtering lists](/skyux/design/guidelines/filtering-lists#contexts-for-filtering-lists.md)
4.  [Pre-filtering full-page lists](/skyux/design/guidelines/filtering-lists#pre-filtering-full-page-lists.md)
5.  [Filter bar anatomy](/skyux/design/guidelines/filtering-lists#filter-bar-anatomy.md)
6.  [Filter bar options](/skyux/design/guidelines/filtering-lists#filter-bar-options.md)
7.  [Filter bar filter types](/skyux/design/guidelines/filtering-lists#filter-bar-filter-types.md)
8.  [Filter bar behavior and states](/skyux/design/guidelines/filtering-lists#filter-bar-behavior-and-states.md)
9.  [Filter bar content](/skyux/design/guidelines/filtering-lists#filter-bar-content.md)
10.  [Related information](/skyux/design/guidelines/filtering-lists#related-information.md)

[

Principles
----------

](/skyux/design/guidelines/filtering-lists#principles.md)

Follow these [SKY UX design principles](/skyux/design/principles.md) when you include filters with lists, and present the filtering options based on the needs of users and the specific scenarios.

**Structure content around tasks**

Include filters, set defaults, and organize filters based on user goals.

**Maintain a clean, cohesive interface**

Don't overwhelm users or clutter the user interface with too many filters. Collapse filtering options that users can discover on their own.

**Offload work from users**

Consider options, such as pre-filtered lists, to present lists that don't require filtering.

[

Usage
-----

](/skyux/design/guidelines/filtering-lists#usage.md)

Include filters with lists when users can:

*   Select individual items to take action or navigate to more information.
*   Create smaller, filtered lists to take action on multiple items or to complete related tasks.
*   Create datasets to review, export, or take action on items.

[

Contexts for filtering lists
----------------------------

](/skyux/design/guidelines/filtering-lists#contexts-for-filtering-lists.md)

### Full-page lists

When the main, or only, task on a page is to narrow a collection of items or manipulate a pre-filtered collection, use a filter bar or tabs to support the filtering tasks.

Dedicated full-page lists can appear on [list pages](/skyux/design/guidelines/page-layouts/list-page.md) or in tabs on [record pages](/skyux/design/guidelines/page-layouts/record-page.md).

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/full-page-context.9eb411599b85fa6f4db8d7bd047c56ca.png)

A full-page list with a filter bar included on a list page.

### Lists in containers

When lists appear in containers such as boxes, use simple filters, such as checkboxes and HTML select inputs, and make them persistent or expandable.

#### Persistent inline filters

When users only need one or two simple filters and containers have room to display the filter controls above the lists, use persistent inline filters. Persistent inline filters are always visible, so users can apply them directly to lists without invoking a button. They are especially useful for controls that users will use frequently or that have significant impact.

Persistent inline filters appear in a toolbar above lists and are applied immediately after users make selections.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/inline-context-select.56727e137a110fb2cb3f1d3edc39b354.png)

Users can select filter criteria in HTML select fields.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/inline-context-checkbox.c195abade33b7027835df0e22a4794c1.png)

Users can toggle filter criteria with checkboxes.

#### Expandable inline filters

When users need up to four simple filters for lists that appear within containers, such as boxes, on pages or modals, use [expandable inline filters](/skyux/components/filter.md). Filter controls are hidden by default and accessed through a **Filter** button, so they are especially useful for filters that users don't need frequently or that don't have significant impact.

If users need more filters or more complex filtering, use a dedicated list view with a [filter bar](/skyux/design/guidelines/filtering-lists#filter-bar-anatomy.md) instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/expandable-diagram.14572586e63325f731cc65d0bcf65f39.png)

Expandable filters let users expand and collapse the filters. The filter button is highlighted when filters are set.

[

Pre-filtering full-page lists
-----------------------------

](/skyux/design/guidelines/filtering-lists#pre-filtering-full-page-lists.md)

When users regularly need to access or work with collections of items, consider providing pre-filtered lists.

### Use pre-filtered lists in tabs when

*   Users need regular access to a small number of lists.
*   One list in a small group of lists needs priority or will be used most frequently.
*   A small number of lists have different tasks for users to complete.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/tab-filters-do.a85b9657b36b424fb17d4181a0055b86.png)

Do use tabs to support easy access to a few pre-filtered lists.

### Don't use pre-filtered lists in tabs when

*   Users need to access a large number of lists.
*   Users don't need to access lists regularly.
*   Pre-filtered lists already exist in the system. Use call-to-action patterns, such as notifications or needs attention items in [action hubs](/skyux/design/guidelines/page-layouts/action-hub.md), instead.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/tab-filters-dont.441ceda3f3c48f19dcf846f16d25cf0e.png)

Don't use tabs for a large set of pre-filtered lists.

### Use pre-filtered lists with a filter bar when

*   Users need to adjust preset filter values or add additional filters to refine lists.
*   Users access lists through calls to action and need to further narrow the lists before taking action.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/pre-filtered-bar.f07731a9eaf12f820440ca81321a7e81.png)

Do use pre-filtered lists to make user workflows more efficient. Users can narrow lists further as necessary.

[

Filter bar anatomy
------------------

](/skyux/design/guidelines/filtering-lists#filter-bar-anatomy.md)

### Filter bar

1

Filter bar label

2

Filter button (filter not set)

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/anatomy-filter-bar-basic.81f5f73ffed34bf9fb7d6288bccc645d.png)

### Filter bar with filter chooser

1

Filter bar label

2

Filter chooser button

3

Filter button (filter set)

4

Clear filters button

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/anatomy-filter-bar-filtered.7a1ea6882e045519c03750d6c24dfce3.png)

### Filter bar with filter operators

1

Filters dropdown button

2

Operators selector (All/Any)

3

Filter button (combination filter set)

4

Combination filter popover details

![image](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/anatomy-filter-bar-full.4dd97bc00b122d1b87fe18a3113c32bf.png)

[

Filter bar options
------------------

](/skyux/design/guidelines/filtering-lists#filter-bar-options.md)

### Filter chooser

When a list requires many filters to give users multiple ways to narrow the collection of items, include a filter choose to let users select the filters to include in the filter bar.

Within filter choosers, organize filters alphabetically.

If some filters will be used in most of the time, include them directly in the filter bar by default instead of the filter chooser.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/option-filter-chooser.791b82ee4c3464915407872ef65f3dda.png)

The filter chooser button opens a modal to select the filters to enable in the filter bar.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/option-filter-chooser-sections.5ede0519ed982c19cc8efe1f83d494cc.png)

For more than 10-12 filters, group filters into categories on a sectioned form. The number of enabled filters appears beside section headers.

### Logical operators

When users may require the ability to apply logic to filtering criteria, enable logical operators. In the filter chooser dropdown, users can select to display logical operators in the filter bar, and then they can apply operators as necessary to narrow the list.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/option-operators.1a11bff3f88a459c604cd1e0a088a62c.png)

Users enable operators through a dropdown and then apply them from the filter bar.

[

Filter bar filter types
-----------------------

](/skyux/design/guidelines/filtering-lists#filter-bar-filter-types.md)

Multiple types of selection methods are available for filtering lists. They support a large and powerful range of filter criteria creation, including a single value for a property, multiple values for a property, ranges of numbers and dates, and more complex filter groupings.

Lookup or categorical

Lookup or categorical filters support the selection of one or multiple values.

Include operators in the initial Filter by input. The pattern supports operators such as:

*   Any of these values
*   None of these values
*   No value
*   Any value

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-lookup.1a9278da381d0c49f15a48539b935409.png)

Lookup button filter values

Any of these values: One value, More than one value

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-lookup-any.27889be69557881bcaf2dde261d1502a.png)

None of these values: One value, More than one value

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-lookup-none.7837b1a2f0caba449b606e9846eae91b.png)

No value

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-lookup-no-value.ff7b280c08299aebf380887ab2f4023b.png)

Any value

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-lookup-any-value.87cf1e67e34f745832cbe97743dae792.png)

Numeric

Numeric filters allow users to narrow down numeric or currency amounts.

Include operators in the initial Filter to input. The pattern supports various operators that you should customize for your scenario:

*   Equal to
*   Does not equal
*   Greater than or equal to
*   Greater than
*   Less than or equal to
*   Less than
*   Between

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-num.dcc604a92042e9436060156379343c59.png)

Numeric button filter values

One value with operator

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-num-one.56174979ae5a8e859852d6afafc8cb12.png)

Between two values

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-num-two.00834ba12aa1d50f641d0d6599f65ec2.png)

Boolean

For boolean filters, determine the appropriate default state based on the workflows that lists support. For example, decide whether to display all contacts in a list by default or only the active contacts that users are most likely to work with. This determines the available filter options.

### Display all items

When a list displays all items by default, users can filter the list to display only one boolean value. For example, they can filter to only display active or inactive list items.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-bool-all.0be4e38192ef008af9e7217ba6caaed8.png)

Boolean button filter values

Default (All items displayed)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-bool-all.e07d07d7949531e2323e4444206986ba.png)

Filter set

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-bool-all-set.8773c24fa6dc980fca321aca42bced3c.png)

### Display items with boolean value

When a list only displays items with a boolean value by default, users can filter to display the other boolean value. For example, they can switch from active list items to inactive items.

Use this filter when the majority of workflows for lists apply to the subset of items with a boolean value.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-bool-value.25bfdc5a633bed8d7f51f4b38c7ec01c.png)

Boolean button filter values

Default (One boolean displayed)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-bool-value-default.e07d07d7949531e2323e4444206986ba.png)

Filter set

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-bool-value-set.75c1862f7548492862fa09be8b6878f4.png)

Date

Date filters allow users to filter based on a specific date.

Include operators in the initial Filter to input. This pattern supports various operators that you should customize for your scenario.

*   After
*   Before
*   Specific range
*   Yesterday
*   Today
*   Tomorrow
*   Last week
*   This week
*   Next week
*   Last month
*   This month
*   Next month
*   Last quarter
*   This quarter
*   Next quarter
*   Last calendar year
*   This calendar year
*   Next calendar year
*   Last fiscal year
*   This fiscal year
*   Next fiscal year
*   Last N days
*   Next N days
*   Any value
*   No value

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-date.7f7378c82bafbcdb382ef9cf6833772c.png)

Date button filter values

One value with operator

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-date-one.71cf68e602ef48b18cd428e76c60f2aa.png)

Between two values

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-date-two.b31bd21669ab738fdbd5f10f05ad2aa7.png)

Fuzzy dates

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-date-fuzzy.3dfac838e827e668a0ebe339db4d3688.png)

Month-day

Month-day filters allow users to set a filter based on dates without specifying a year.

Include operators in the initial Filter to input similar to a date filter.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-month-day.727c3f5289daccbf47ff2deb38a90935.png)

Month-day button filter values

One value with operator

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-month-one.64fe292aa0f18d737ceb1f060e33a181.png)

Between two values

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-month-two.092f567788ce8766e36fe1675455d5e9.png)

Text

Text filters allow users to filter based on a string of text.

Include operators in the initial Filter to input. This pattern supports various operators that you should customize for your scenario.

*   Equal to
*   Does not equal
*   Blank
*   Not blank
*   Starts with
*   Does not start with
*   Any of these values
*   None of these values

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-text.3d91e960b61c0845ecb1741effcf513a.png)

Text button filter values

Operators

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-text-ops.894a2dd01512ae669aa8020fb9bc2236.png)

Blank or Not blank

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-text-blank.5ea1e0424335281fd3e7859f2141acee.png)

Any of these values: One value, More than one value

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-text-any.d025bc6a3124283b4e5a14644f645303.png)

None of these values: One value, More than one value

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-text-none.bab1c93366afaff5a77805e0126c400f.png)

Combination filters

Combination filters allow users to filter using multiple criteria at the same time. They include multiple individual filters for list item properties and can use various filter types, such as text or lookup. For more than seven filters, use headings to group the filters.

States

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-combo.eb87c27a3dd08a08b959c887a5cf693d.png)

Starting to create a filter with a combination of education criteria to narrow people in a list.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-combo-set.313c0cbd073d450e219bf06c0b70569f.png)

Multiple individual filters are set for the combination filter.

Grouped filters

Grouped filters allow users to create groups of multiple criteria so that they can then filter lists to include "Any of" or "All of" the items in those groups. Groups can include filters with different filter types.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-multi-combo.6276811e6af8fe7e973dd4fe30f04217.png)

Starting to create an initial filter group of education criteria to narrow people in a list.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-multi-combo-set.495f783176918052880646b3512387bb.png)

Two groups are created to filter items meeting the criteria in either group.

Combination button filter values

One value set

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-multi-combo-one.9b45bd2c1dd83d55261d47cdd853e682.png)

More than one value set

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-multi-combo-more.24dc10cbdf9e12b3058ca59965106a4a.png)

[

Filter bar behavior and states
------------------------------

](/skyux/design/guidelines/filtering-lists#filter-bar-behavior-and-states.md)

### Clearing filters

When users select **Clear all values**, [confirm](/skyux/components/confirm.md) their intention before removing the filter values to avoid losing their work by mistake.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/clearing-filters.89fc5ebcfc1f3a20bb14005cc221ae51.png)

### Filter details display

For combination filters that aggregate filters in a filter button but don't display the filter values, use a [popover](/skyux/components/popover.md) to progressively disclose the values on focus and hover. This keeps users in context and avoids extra effort to obtain the information.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/popover-filter-details.a694f539888348df9fa077a7cba564a9.png)

### Filter bar and button states

Filter bar states

Filters not set

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/state-not-set.fb1559dd611dcab36a4ae1a8ef9764c3.png)

Filter set

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/state-filter-set.7f3f48af5154866cc14b1b50a212caa5.png)

More filters available with filter chooser button

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/state-chooser.35a3dac4d940c7d160ed8f715af19dab.png)

More filters and operators available

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/state-more.874538092d565bffd68c59b3f4bb0b74.png)

Operator shown (options displayed)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/state-operators-set.3861c6087d82cba59772d16d89ed9df9.png)

Button state

Filter not set

Filter set

Base

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-base.86f0acf6d647262085a62e05d71afe13.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-on-base.d92fae9a39b4b348329c354f7d0e169e.png)

Hover

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-hover.eb15c93a33ca884eace5784f246da90f.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-on-hover.d92fae9a39b4b348329c354f7d0e169e.png)

Focus

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-focus.28ef05da4fc368510c765744ae170590.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-on-focus.25624e2a32205a7699ac6de67a0b77aa.png)

Click

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-click.746e311990210bd7e55b08230a728930.png)

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filter-button-on-click.98bd834880ddf3ecc06d0395bb9b3168.png)

### Filter bar responsive behaviors

Larger than extra small (XS) breakpoint

More filters available

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/responsive-chooser-wrap.c7f93647f304d9f316593987ee00ee2e.png)

Operator shown

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/responsive-operators-wrap.965612cfcec2a17ca96a4342e4ac86b3.png)

Smaller than extra small (XS) breakpoint

More filters available

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/responsive-chooser-xs.35315b58c54b896d1942bdf1677891a1.png)

Operators set

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/responsive-operators-xs.b9789218dedf34153cd1cf0f85777c43.png)

### Updates to summary details

When filters or search criteria are applied to a list, update the list count and summary details to reflect the filtered list. Add “match” to the list count label to reflect the list is in a filtered state.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/filteringrecords/filtered-list-count.769d0cd8c574c061bb42292676159f41.png)

Do update summary details when filters or search criteria are applied to a list. To provide context, update the list count label to include 'match.'

[

Filter bar content
------------------

](/skyux/design/guidelines/filtering-lists#filter-bar-content.md)

Use colons after filter property names when filters are set.

When displaying filters in the filter bar by default, organize them in descending order of importance based the tasks that users will perform. Place the most important or most frequently used first filters first.

[

Related information
-------------------

](/skyux/design/guidelines/filtering-lists#related-information.md)

### Guidelines

*   [Data grid](/skyux/components/data-grid.md)
*   [Dropdown](/skyux/components/dropdown.md)
*   [Filter](/skyux/components/filter.md)
*   [Inline form](/skyux/components/inline-form.md)
*   [Popover](/skyux/components/popover.md)
*   [Sectioned form](/skyux/components/sectioned-form.md)

### Guidelines

*   [Page design](/skyux/design/guidelines/page-layouts.md)