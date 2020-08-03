# CSS Grid

## Display Grid

In order for grid to work we need to put every thing into a container (The name of the container doesn't matter). This container will contain items and sun-items will note be displayed as grid and won't be effected by grid.

You can make a container a gird by: `display: grid`

## Grid Template Columns And Rows

Simply doing a `display: grid` is not enough to make it a grid. We also need to say how many columns and rows it must have.</br>
Define Columns with :`grid-template-columns: <Values>`
Define Rows with :`grid-template-rows: <Values>`

The `<Values>` can be:

- px
- %
- fr
- em(not recommended in my own bullsh*t opinion so use it if you feel like it)
- rem(not recommended in my own bullsh*t opinion so use it if you feel like it)
- vw
- vh

You can also use `auto` for `<Values>` for automatic resizing based on the other values. And for multiple values you can repeat the values: </br>
`grid-template-columns: 2fr 1fr 1fr auto`</br>
If you have multiple columns or rows with the same sizes you can use `repeat(<number-of-repeats, size>)` instead of `<Values>`. Example:</br>
`grid-template-columns: repeat(3, 1fr)`

## Grid Template Area

Grid template area is the total space surrounded by four grid lines. A grid area may consists of many grid cells. The grid template area defines the grid template by referencing the name of the grid area which are specified with the grid area property. Repeating the name causes the content to space those cells.

Grid template area is defined with and the second line is an example:

```CSS
.grid-template-areas {
grid-template-areas: [first-row:<first-column> <second-column> ...[second-row<first-column> <second-column> ...] ...;
}
```

Example:

```CSS
.grid-template-areas {
grid-template-areas:
"nav nav nav nav"
"sidebar header header header"
"sidebar main main main"
"sidebar content content content"
"footer footer footer footer";
}
```

After that we will need to get each item in the grid and name what they are so that they can be adjusted. You can do this like demonstrated below:

```CSS
.item-1 {
  grid-area: nav;
}
.item-2 {
  grid-area: header;
}
.item-3 {
  grid-area: sidebar;
}
.item-4 {
  grid-area: main;
}
.item-5 {
  grid-area: content;
}
.item-6 {
  grid-area: footer;
}
```

## Grid Template

It is a shortened version of `grid-template-columns`, `grid-template-rows` and `grid-template-area`. The first line is the first column. After declaring the first column you can specify it's size and then name the second column and it's size then you can use `/` to specify the size of the rows.

Example:

```CSS
.grid-template {
  display: grid;
  grid-template:
  "h h q" 100px
  "m m n" 200px
  "f r r" 300px
  / auto 200px 350px;
}
```

Just like the example above the items will be order from first h (first h will be item 1) to the last f (last f will be item 9) so the first m will be item 4 and the last m will be item 6.

Take note that if you want to decide which item will go to which area you will need to name the items just like the `grid-template-area` in the previous topic.

Example:

```CSS
.item-1 {
  grid-area: f;
}
.item-2 {
  grid-area: m;
}
.item-3 {
  grid-area: h;
}
.item-4 {
  grid-area: n;
}
.item-5 {
  grid-area: q;
}
.item-6 {
  grid-area: r;
}
```

## Grid Gap

This property dictates the gap between the rows or columns. You can use it in 2 ways:

1. `row-gap` and `column-gap`
2. `gap`

As the first way suggests the `row-gap` dictates the gap between the rows and the `column-gap` is the gap between the columns.</br>
The second way however is a bit more complicated. If you only give it one value it will set it for both row and column but if you give it 2 values the first will be for rows and the second value will be for columns.

Example:

```CSS
.grid-gap {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: repeat(4, 1fr) 0.5fr;
  grid-template-areas:
    "header header header"
    "nav content sidebar"
    "nav content sidebar"
    "nav main main"
    "footer footer footer";
  /* Making a grid top */
  gap: 10px 40px;
  /* setting the gap of rows to 10px and columns to 40px */
}
```

## Justify Items

It dictates how the items in the grid should behave and fill the grid rows and columns on the horizontal axis. It has many properties but the most used ones are:

- `start`: The item is packed flush to each other toward the start edge of the alignment container in the appropriate axis.
- `end`: The item is packed flush to each other toward the end edge of the alignment container in the appropriate axis.
- `self-start`: The item is packed flush to the edge of the alignment container of the start side of the item, in the appropriate axis.
- `center`: The items are packed flush to each other toward the center of the of the alignment container.
- left: The items are packed flush to each other toward the left edge of the alignment container. If the property’s axis is not parallel with the inline axis, this value behaves like start.
- `right`: The items are packed flush to each other toward the right edge of the alignment container in the appropriate axis. If the property’s axis is not parallel with the inline axis, this value behaves like start.
- `baseline/first baseline/last baseline`: Specifies participation in first- or last-baseline alignment: aligns the alignment baseline of the box’s first or last baseline set with the corresponding baseline in the shared first or last baseline set of all the boxes in its baseline-sharing group.The fallback alignment for first baseline is start, the one for last baseline is end.
- `stretch`: If the combined size of the items is less than the size of the alignment container, any auto-sized items have their size increased equally (not proportionally), while still respecting the constraints imposed by max-height/max-width (or equivalent functionality), so that the combined size exactly fills the alignment container.
- ~~`safe`: If the size of the item overflows the alignment container, the item is instead aligned as if the alignment mode were start.~~(didn't do anything for me when I changed it to this setting)
- ~~`unsafe`: Regardless of the relative sizes of the item and alignment container, the given alignment value is honored.~~(didn't do anything for me when I changed it to this setting)
- `legacy`: Makes the value inherited by the box descendants. Note that if a descendant has a justify-self: auto value, the legacy keyword is not considered by the descend, only the left, right, or center value associated to it.

## Align Items

This is similar to the justify items but justify items positioned everything horizontally so align items position's everything vertically. The properties are also similar to the justify content:

- `start`: The item is packed flush to each other toward the start edge of the alignment container in the appropriate axis.
- `end`: The item is packed flush to each other toward the end edge of the alignment container in the appropriate axis.
- `self-start`: The item is packed flush to the edge of the alignment container of the start side of the item, in the appropriate axis.
- `center`: The items are packed flush to each other toward the center of the of the alignment container.
- left: The items are packed flush to each other toward the left edge of the alignment container. If the property’s axis is not parallel with the inline axis, this value behaves like start.
- `right`: The items are packed flush to each other toward the right edge of the alignment container in the appropriate axis. If the property’s axis is not parallel with the inline axis, this value behaves like start.
- `baseline/first baseline/last baseline`: Specifies participation in first- or last-baseline alignment: aligns the alignment baseline of the box’s first or last baseline set with the corresponding baseline in the shared first or last baseline set of all the boxes in its baseline-sharing group.The fallback alignment for first baseline is start, the one for last baseline is end.
- `stretch`: If the combined size of the items is less than the size of the alignment container, any auto-sized items have their size increased equally (not proportionally), while still respecting the constraints imposed by max-height/max-width (or equivalent functionality), so that the combined size exactly fills the alignment container.
- ~~`safe`: If the size of the item overflows the alignment container, the item is instead aligned as if the alignment mode were start.~~(didn't do anything for me when I changed it to this setting)
- ~~`unsafe`: Regardless of the relative sizes of the item and alignment container, the given alignment value is honored.~~(didn't do anything for me when I changed it to this setting)
- `legacy`: Makes the value inherited by the box descendants. Note that if a descendant has a justify-self: auto value, the legacy keyword is not considered by the descend, only the left, right, or center value associated to it.

## Justify Content

This setting positions items based on if the content don't fully use the container's space. Then it will position the content accordingly in the row axis.

- `start`: The item is packed flush to each other toward the start edge of the alignment container in the appropriate axis.
- `end`: The item is packed flush to each other toward the end edge of the alignment container in the appropriate axis.
- `self-start`: The item is packed flush to the edge of the alignment container of the start side of the item, in the appropriate axis.
- `center`: The items are packed flush to each other toward the center of the of the alignment container.
- left: The items are packed flush to each other toward the left edge of the alignment container. If the property’s axis is not parallel with the inline axis, this value behaves like start.
- `right`: The items are packed flush to each other toward the right edge of the alignment container in the appropriate axis. If the property’s axis is not parallel with the inline axis, this value behaves like start.
- `left`: The items are packed flush to each other toward the left edge of the alignment container in the appropriate axis. If the property’s axis is not parallel with the inline axis, this value behaves like start.
- `baseline/first baseline/last baseline`: Specifies participation in first- or last-baseline alignment: aligns the alignment baseline of the box’s first or last baseline set with the corresponding baseline in the shared first or last baseline set of all the boxes in its baseline-sharing group.The fallback alignment for first baseline is start, the one for last baseline is end.
- `stretch`: If the combined size of the items is less than the size of the alignment container, any auto-sized items have their size increased equally (not proportionally), while still respecting the constraints imposed by max-height/max-width (or equivalent functionality), so that the combined size exactly fills the alignment container.
- `space-between`: The items are evenly distributed within the alignment container along the main axis. The spacing between each pair of adjacent items is the same. The first item is flush with the main-start edge, and the last item is flush with the main-end edge.
- `space-evenly`: The items are evenly distributed within the alignment container along the main axis. The spacing between each pair of adjacent items, the main-start edge and the first item, and the main-end edge and the last item, are all exactly the same.
- `space-around`: The items are evenly distributed within the alignment container along the main axis. The spacing between each pair of adjacent items is the same. The empty space before the first and after the last item equals half of the space between each pair of adjacent items.
- `safe`: If the size of the item overflows the alignment container, the item is instead aligned as if the alignment mode were start.
- `unsafe`: Regardless of the relative sizes of the item and alignment container, the given alignment value is honored.

## Grid Auto Flow

The `grid-auto-flow` CSS property controls how the auto-placement algorithm works, specifying exactly how auto-placed items get flowed into the grid.

- `row`: Items are placed by filling each row in turn, adding new rows as necessary. If neither row nor column is provided, row is assumed.
- `column`: Items are placed by filling each column in turn, adding new columns as necessary.
- `dense`: "dense" packing algorithm attempts to fill in holes earlier in the grid, if smaller items come up later. This may cause items to appear out-of-order, when doing so would fill in holes left by larger items.

If it is omitted, a "sparse" algorithm is used, where the placement algorithm only ever moves "forward" in the grid when placing items, never backtracking to fill holes. This ensures that all of the auto-placed items appear "in order", even if this leaves holes that could have been filled by later items.

Note that `dense` is used after the either  `row` or `column`: `grid-auto-flow: row dense;` or `column` instead of `row` in this case.
