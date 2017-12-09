## CSS Grid

### Basics

1. Define a container with `display: grid`
1. Set column and row sizes with `grid-template: rows / columns`
1. Place child elements with `grid-area`

### Terminology

* Grid Container: Parent element, has `display: grid`
* Grid Item: Direct descendants of a grid container
* Grid Line: Dividing line (horizontal or vertical) of the grid
* Grid Track: Space between two lines (columns or rows)
* Grid Cell: Intersection of two tracks
* Grid Area: Space encompassed by 4 grid lines (any size)

### Concepts

* Valid units include `px`, `%`, `auto`, `em`/`rem`, and `fr`
    * `fr` is a fraction of unallocated space in the grid
* You can repeat declarations with `repeat(3, 1fr)`
* You can give grid-lines labels with `1 fr [optional-label another-optional-label]`
* You can specify a grid with `grid-template: rows / columns`
* You can position a grid item by specifying its starting and ending grid line with `grid-row: start / end` or `grid-column: start / end`
    * This can include negative values
    * You can use the `span` keyword to say how many rows or columns you would like it to span
    * `grid-area` combines rows and columns like this: `grid-area: row-start / column-start / row-end / column-end`
        * You can also assign it to a `grid-template-area` name
* You can order an item in the grid with the `order` keyword
* You can label grid areas with:
    ```css
    grid-template-areas:
    "header header header"
    "main main sidebar"
    ". footer footer"
    ```
    * `.` means it should be empty
    * `none` means it's undefined
* You can specify gutters with `grid-column-gap` and `grid-row-gap`, or `grid-gap: row column`
* You can specify the justification and alignment of rows and columns with `justify-items` and `align-items`. They accept `start`, `end`, `center`, and `stretch`.
    * You can override this on items with `justify-self` and `align-self`
* You can specify the justification and alignment of the entire grid with `justify-content` and `align-content` if there is excess unused space. Takes the same arguments as flexbox.

## Responsive Grids

* Use named areas to assign content to areas, and then redefine the shape of the grid using the media queries.
* You can hack `repeat` with `repeat(autofill, minmax(smallest, largest))`
