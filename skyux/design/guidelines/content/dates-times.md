              

 1.  [Home](/skyux/)
2.  [Design](/skyux/design.md)
3.  [Guidelines](/skyux/design/guidelines.md)
4.  [Content](/skyux/design/guidelines/content.md)
5.  [Dates and times](/skyux/design/guidelines/content/dates-times.md)

Dates and times
===============

The content guidelines for dates and times promotes consistency across Blackbaud solutions. In most cases, SKY UX follows the [Chicago Manual of Style](https://www.chicagomanualofstyle.org/home.html), but when guidelines differ, SKY UX guidance takes precedence.

We recommend using the SKY UX [date pipe](/skyux/components/date-pipe.md) to format dates and times based on the user's locale.

Localization
------------

Use the [date pipe](/skyux/components/date-pipe.md) to localize dates and times. Display values based on the user's locale and time zone. For example, use locales to determine the correct order of the month and day, such as MM/DD/YYYY vs. DD/MM/YYYY, and whether to use 12- or 24-hour times.

If you can't localize

We always recommend localizing dates and times, but in some situations, you may may not be able to. For example, if you are following these guidelines for consistency with SKY UX applications but aren't actually using SKY UX, you can't use the date pipe to localize dates and times. If you don't have another option to localize, follow best practices to reduce ambiguity, including:

*   For dates, avoid numeric dates and spell out months.
*   For times, use "AM" or "PM" with no periods for 12-hour times and specify time zones without standard or daylight time using all-caps abbreviations with no periods.
*   For time zones, use two-letter abbreviations in the United States, and use regional abbreviations outside of the U.S. For example, use "1:30 PM CT" for U.S. Central Time and "11:30 AM AWT" for Australian Western Time.

Date formats
------------

SKY UX applications mostly use three date formats, plus fuzzy dates for when full dates are unnecessary or unavailable. Use context details, such as placement and the available space, to determine the best format for each scenario.

Use the [date pipe](/skyux/components/date-pipe.md) to localize dates based on the user's locale.

Date format

Date pipe  
value

Example in  
your locale

Usage

Short date

`shortDate`

4/25/2027

Use to conserve space and make scanning easier, especially in limited space, such as form fields, and tabular layouts, such as data lists. Use locales to determine whether to include leading zeroes with dates and months.

Long date

`longDate`

April 25, 2027

Use for display text and complete sentences. Long dates are easier to read and process in prominent text, such as page headings and description lists, and in longer content, such as persistent inline help and popovers.

Full date

`fullDate`

Sunday, April 25, 2027

Use when the day of the week is important to emphasize, such as an event's start and end date.

Fuzzy date

April 2027

Use for partial or incomplete dates when the full date is unnecessary or unavailable.

### Use when

To avoid ambiguity, use the longest date format that space allows. For example, short dates are useful when space is limited, while long dates work better in display text and complete sentences

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/content/dates-times/do-shortdate-tabular.8b0a4e047af810d60d8c992da30175be.png)

Do use short dates when space is limited, such as in grids and lists.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/content/dates-times/do-fuzzydate.0c54cb5501b2e18af2ae68d3ad68334f.png)

Do use long dates and fuzzy dates in display text, such as page headings.

### Don't use when

Don't use ordinal numbers, such as "1st," "third," or "twenty-eighth," in dates.

Time formats
------------

For specific points in time, such as when an event starts or an action takes place, separate hours and minutes with colons and no spaces. Only include seconds if that level of precision is necessary. Include leading zeroes for minutes but not hours.

Use the [date pipe](/skyux/components/date-pipe.md) to localize times. For example, localize times to use 12- or 24-hour times based on locale. If you can't localize times, use "AM" or "PM" with no periods for 12-hour times and specify time zones without standard or daylight time using all-caps abbreviations with no periods. In the United States, use two-letter abbreviations for time zones, and outside of the United States, use regional abbreviations. For example, use "1:30 PM CT" for U.S. Central Time and "11:30 AM AWT" for Australian Western Time.

Time format

Date pipe  
value

Example in  
your locale

Usage

Short time

`shortTime`

12:54 AM

Use short times in most cases. Reserve longer time formats for scenarios that require additional details, such as seconds or the time zone.

Date and time formats
---------------------

Combine dates and times when users need to know both. Use context details such as placement and the available space to determine the best format for each scenario.

Use the [date pipe](/skyux/components/date-pipe.md) to localize dates and times.

Format

Date pipe  
value

Example in  
your locale

Usage

Short date with time

`shortDate` and `shortTime`

4/25/2027 4:15 PM

Use to conserve space and make scanning easier. Don't include anything between the date and time.

Long date with time

`longDate` and `shortTime`

April 25, 2027 at 4:15 PM

Use for display text and complete sentences. Separate the date and time with "at." (If you need to lead with the time, separate with "on" instead.)

Full date with time

`fullDate` and `shortTime`

Sunday, April 25, 2027 at 4:15 PM

Use when the day of the week is important to emphasize. Separate the date and time with "at." (If you need to lead with the time, separate with "on" instead.)

Date and time ranges
--------------------

Date and time ranges combine start dates and times with their end dates and times.

*   In display text, use en dashes ("–") with no spaces before or after to separate start dates or times from end dates or times. If an editing tool doesn't provide a first-class option for en dashes, use the HTML escape character `&ndash;`.
*   In longer text and complete sentences, use connecting words, such as "from ... to" or "between ... and" instead of en dashes.
*   In date ranges that include years, include years with both start and end dates even if they are the same. This ensures clarity when date formats are adjusted based on locale.
*   In time ranges for 12-hour times, include "AM" or "PM" with both start and end times even if they are the same. This ensures clarity when time formats are adjusted based on locale.

Use the [date pipe](/skyux/components/date-pipe.md) to localize dates and times.

**Do**

**Don't**

4/25/2027–5/9/2027

4/25–5/9/2027

4/25/2027 to 5/9/2027

June 7, 2026–July 18, 2026

June 7–July 18, 2026

June 7, 2026 - July 18, 2026

Registration is open from June 7, 2026, to July 18, 2026.

Registration is open from June 7, 2026–July 18, 2026.

4:30 PM–6:00 PM

4:30–6:00 PM

4:30 PM - 6:00 PM

Abbreviations
-------------

In display text, don't abbreviate months or days of the week unless context makes the meaning clear. When necessary, abbreviate to the first three letters of the month or day with no period. For example, if a chart uses months as the x-axis, you can use three-letter abbreviations for consistent spacing across screen sizes because the sequence provides the necessary context to avoid confusion even if the text is translated to a language where some months start with the same three letters.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/content/dates-times/do-abbr-charts.d4b6cded474f31b3bd09443590bcebc8.png)

Do abbreviate months or days in areas such as charts where space is limited and context makes the meaning clear.

**Do**

**Don't**

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/content/dates-times/do-abbr-full-date-review.5b8c3dc849a6d36c4fa0f450b43930b0.png)

Do spell out months and days in display text to avoid ambiguity.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/content/dates-times/dont-abbr-review.75614b16f75bfaa5af527b71c2b811d0.png)

Don't abbreviate in display text because this can cause localization issues.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/content/dates-times/do-abbr-full-date-heading.3060f3f9e224c5938d6f48875f47d819.png)

Do spell out months and days in headings.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/content/dates-times/dont-abbr-heading.80b0ae1ecbf1aaabe3e16918369c8552.png)

Don't abbreviate in headings.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/content/dates-times/do-abbr-full-date-label.92004c3215ee6d435f0f0ee78d1d23d2.png)

Do spell out months and days in labels.

![undefined](https://sky.blackbaudcdn.net/skyuxapps/skyux/assets/img/guidelines/content/dates-times/dont-abbr-label.20ed2b6dd7a349e898680a3edf7de0dc.png)

Don't abbreviate in labels.

Relative dates and times
------------------------

Relative dates and times provide a sense of urgency. Whereas exact dates, such as April 25, 2027, and exact times, such as 12:54 AM, indicate specific points in time, relative dates and times help users to quickly understand the recency of an event relative to the current date or time. For example, relative dates and times help indicate how recently data was last updated.

Keep in mind that relative dates and times lose their effectiveness after about a day for times and about a week for dates, and they need to be converted to exact dates and times.

*   For relative times, switch to relative dates and/or exact times after 24 hours.
*   For relative dates, switch to exact dates after 7 days.

### In the past

Description

Example

In the past few seconds

"just now"

In the past minute

"1 minute ago"

In the past 59 minutes

"x minutes ago"

1 to 24 hours ago

"x hours ago"

1 day ago (by date, not hours)

"yesterday"

1 day ago with exact time (by date, not hours)

"yesterday at 9:45 AM"

2 to 7 days ago

"x days ago"

7 days ago

"1 week ago""

More than 7 days ago

exact date

### In the future

Description

Example

In the next few seconds

"now"

In the next minute

"in 1 minute"

In the next 59 minutes

"in x minutes"

In 1 to 24 hours

"in x hours"

in 1 day (by date, not hours)

"tomorrow"

in 1 day with exact time (by date, not hours)

"tomorrow at 9:45 AM"

In 2 to 7 days

"In x days"

In 7 days

"In 1 week""

In more than 7 days

exact date