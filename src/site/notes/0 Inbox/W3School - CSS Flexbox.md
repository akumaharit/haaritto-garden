---
{"dg-publish":true,"permalink":"/0-inbox/w3-school-css-flexbox/","tags":["w3school"],"created":"2025-10-12T11:17:18.372+07:00","updated":"2025-10-12T11:33:15.818+07:00"}
---

Flexbox is a layout model for arranging items within a container in a flexible and responsive way.
CSS Flexbox is a one-dimensional layout with rows OR columns
CSS Grid is used for two-dimensional layout with rows AND columns.

Flexbox component consists of:
- Flex Container: the parent container element where the `display` property is set to `flex` or `inline-flex`
- One or more flex items (the children of the flex container) will automatically becomes flex item

You can specify container size using `height` and `width`

## Flex Container Properties
- `display` - Must be set to `flex` or `inline-flex`
- `flex-direction` - Sets the display-direction of flex items (default: `row`, `column`, `row-reverse`, `column-reverse`)
- `flex-wrap` - Specifies whether the flex items should wrap or not (default: `nowrap`, `wrap`, `wrap-reverse`)
- `flex-flow` - Shorthand property for `flex-direction` and `flex-wrap` (example: `row wrap;`)
- `justify-content` - Aligns the flex items when they do not use all available space on the main-axis (horizontally) (default: `flex-start`, `center`, `flex-end`,`space-around`,`space-between`,`space-evenly`)
- `align-items` - Aligns the flex items when they do not use all available space on the cross-axis (vertically) (default: `normal`, `flex-start`, `flex-end`, `stretch`, `baseline`, `normal`)
- `align-content` - Aligns the flex lines when there is extra space in the cross axis and flex items wrap. This is similar to `align-items` but it aligns the flex lines instead. (default `stretch`, `center`, `flex-start`, `flex-end`)

## PERFECT CENTERING
- Simply set `justify-content: center;` and `align-items: center;` and the flex items will be perfectly centered.
