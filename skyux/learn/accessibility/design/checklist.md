            

 1.  [Home](/skyux/)
2.  [Learn](/skyux/learn.md)
3.  [Accessibility](/skyux/learn/accessibility.md)
4.  [Design](/skyux/learn/accessibility/design.md)
5.  [UI checklist](/skyux/learn/accessibility/design/checklist.md)

User interface accessibility checklist
======================================

We use this checklist to evaluate new SKY UX patterns and components to ensure that they are as accessible as possible. The checklist covers a subset of the WCAG 2.2 success criteria that is specific to the user interface display and behaviors. It does not cover criteria related to the code or HTML markup.

 

Does the interface include?

Then check that this is true:

1

Text (< 18pt or < 14pt if bold)

Contrast ratio of background to text is >= 4.5:1. [WCAG Criterion 1.4.3](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum)

2

Large text ( >=18 point or >= 14pt if bold)

Contrast ratio of background to text is >= 3:1. [WCAG Criterion 1.4.3](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum)

3

Links within text that are not underlined

Link color to text color contrast is >= 3:1, and links have additional visual indication when hovered and focused. [WCAG Criterion 1.4.1](https://www.w3.org/WAI/WCAG22/Understanding/use-of-color)

4

Images or non-text content such as icons

Images have text equivalents defined. For decorative images, indicate that they are presentational and should be ignored by screen readers. [WCAG Criterion 1.1.1](https://www.w3.org/WAI/WCAG22/Understanding/non-text-content)

5

Images or non-text content that invokes a function

Images have text equivalents that communicate the function. [WCAG Criterion 1.1.1](https://www.w3.org/WAI/WCAG22/Understanding/non-text-content)

6

Color that conveys information

Color is not the only means of communicating the information. [WCAG Criterion 1.4.1](https://www.w3.org/WAI/WCAG22/Understanding/use-of-color)

7

Motion or animations

Flashing does not flash more than 3 times in any 1-second period. [WCAG Criterion 2.3.1](https://www.w3.org/WAI/WCAG22/Understanding/three-flashes-or-below-threshold)

8

Motion, blinking, or scrolling that starts automatically and lasts more than 5 seconds

A mechanism exists for users to pause, stop, or hide the motion unless it is essential. [WCAG Criterion 2.2.2](https://www.w3.org/WAI/WCAG22/Understanding/pause-stop-hide)

9

Auto-updating content that starts automatically

A mechanism exists for users to pause, stop, or hide the motion unless it is essential. [WCAG Criterion 2.2.2](https://www.w3.org/WAI/WCAG22/Understanding/pause-stop-hide)

10

Forms or input elements

All input elements have text labels onscreen or specified off-screen. [WCAG Criterion 3.3.2](https://www.w3.org/WAI/WCAG22/Understanding/labels-or-instructions.html)

11

Required form inputs and required input formats such as date formats

Required elements and formats are communicated visually and textually. [WCAG Criterion 3.3.2](https://www.w3.org/WAI/WCAG22/Understanding/labels-or-instructions.html) and [WCAG Criterion 1.4.1](https://www.w3.org/WAI/WCAG22/Understanding/use-of-color)

12

Error states and messages

When users are notified of errors and given instructions on how to fix them, a method exists to navigate directly to errors from error messages. [WCAG Criterion 3.3.1](https://www.w3.org/WAI/WCAG22/Understanding/error-identification) and [3.3.3](https://www.w3.org/WAI/WCAG22/Understanding/error-suggestion)

13

Interactions that are mouse- or touch-only such as drag and drop

Keyboard operation alternatives are noted in the design proposal. [WCAG Criterion 2.1.1](https://www.w3.org/WAI/WCAG22/Understanding/keyboard)

14

Interactive elements such as links, buttons, and input elements

*   On focus, no unexpected or non-browser default behaviors are specified. [WCAG Criterion 3.2.1](https://www.w3.org/WAI/WCAG22/Understanding/on-focus)
*   On focus, additional visual indicators of the focus state are specified as necessary. [WCAG Criterion 2.4.7](https://www.w3.org/WAI/WCAG22/Understanding/focus-visible)
*   On text entry or input selection, no unexpected behavior is invoked. If unexpected behavior is necessary, a warning is communicated to users ahead of time. [WCAG Criterion 3.2.2](https://www.w3.org/WAI/WCAG22/Understanding/on-input)

15

Page titles

Titles are unique and describe the contents and/or purpose of the page.

16

Non-native HTML components such as rich Internet application widgets

Interactions are defined for keyboard use. (See WAI-ARIA Authoring Practices for [common keyboard widget patterns](https://www.w3.org/WAI/ARIA/apg/practices/keyboard-interface/#fundamentalkeyboardnavigationconventions) and [principles.)](https://www.w3.org/WAI/ARIA/apg/practices/keyboard-interface/#discernibleandpredictablekeyboardfocus) [WCAG Criterion 2.1.1](https://www.w3.org/WAI/WCAG22/Understanding/keyboard)

17

Headings

Heading levels are specified in hierarchical order (H1-H6) and are descriptive. [WCAG Criterion 1.3.1](https://www.w3.org/WAI/WCAG22/Understanding/info-and-relationships) and [WCAG Criterion 2.4.6](https://www.w3.org/WAI/WCAG22/Understanding/headings-and-labels)