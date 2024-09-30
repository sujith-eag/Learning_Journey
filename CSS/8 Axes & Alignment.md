
# Axes

There is a ***Main axis*** and ***Cross axis***

> `justify-content`  works along the **main axis**  (Row for Row)
> `flex-align`  works along **cross axis**  (Column if Row)

`flex-direction` can be used to change Orientation of flex items within a flex container.

When `flex-direction` is changed, the axis is also changes and how alignment happens.

The default value is `fex-direction: row;`  arranged left to right,

> Default behavior of `flex-direction: row` which arranges things horizontally works with `flex: 1` because the `block-level` elements default to the ***full width*** of the parent block. 


When changed to `flex-direction: column;`  which puts the items top to bottom.
now `heght` will be referred instead of `width`
`flex: 1` shorthand will not works as usual,  will collapse as `flex-basis: 0` ,
this can be fixed by `flex: 1 1 auto` will default to given height and expand the div.

> In `flex-direction: column` the `block-level` elements default to the ***height of their content*** , when there is no content it collapses.


# Gap
gap adds specified space between flex items similar to adding a margin to the items.
A relatively new feature.
`gap: 8px` adds that much margin between flex items.

`gap: 10px 20px`   10 for row gap and 20 for column gap


# Margin auto
`margin-left: auto;`  takes up all the space on left and moves everything to the right
Similarly to the right

# [Cheat Sheet for flexbox](https://flexbox.malven.co/)
##### `display`  Enable flex for all children
`display: flex`
`display: inline-flex`

##### `flex-direction` Establishes the main axis
`flex-direction: row`          `flex-direction: row-reverse`
`flex-direction: column`    `flex-direction: column-reverse`

##### `flex-wrap` Wraps items if they can't all be made to fit on one line
`flex-wrap: nowrap`           `flex-wrap: wrap`               `flex-wrap: wrap-reverse`

##### `justify-content` To distribute extra space on the main axis.
`justify-content: flex-start`   `justify-content: flex-end `
`justify-content: center ` 

`justify-content: space-evenly `
`justify-content: space-between`   `justify-content: space-around `

##### `align-items` Determines how items are laid out on the *cross axis*
For column, ***cross axis*** is from left to right
For row, ***cross axis*** is from top to bottom
`align-items: flex-start`       `align-items: flex-end`             `align-items: center`
Extends and expands the height!!!    `align-items: baselie`     `align-items: stretch`

##### `align-content`
Only has an effect with more than one line of content.
`align-content:  flex-start  flex-end  centre  space-between space-around  stretch`


## for Individual Children
 `order: integer`   allows for explicitly set the order you want each child to appear in.
`order: 5;`


`align-self: flex-end`      Set alignment for the individual item along cross axis. (main axis will have other items in way) 

`flex-grow: 1` applied to all
`flex-grow: (1,2, and 3)`  for three children
`flex-shrink: 2`  making one shrink twice the other
`flex-basis: 10%`   Define the size of an element before remaining space is distributed






- This beautiful [Interactive Guide to Flexbox](https://www.joshwcomeau.com/css/interactive-guide-to-flexbox/) 
- [Typical use cases of Flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Typical_Use_Cases_of_Flexbox) is an MDN article
- The [CSS Tricks “Guide to Flexbox”](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) is a classic. 



#12sep2024 

