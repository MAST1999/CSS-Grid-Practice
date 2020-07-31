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
- em(not recommended)
- rem(not recommended)
- vw
- vh

You can also use `auto` for `<Values>` for automatic resizing based on the other values. And for multiple values you can repeat the values: </br>
`grid-template-columns: 2fr 1fr 1fr auto`</br>
If you have multiple columns or rows with the same sizes you can use `repeat(<number-of-repeats, size>)` instead of `<Values>`. Example:</br>
`grid-template-columns: repeat(3, 1fr)`
