# Flexbox
[Flexbox resource](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox)
Flexbox is a way to arrange items into rows or columns. 
These items will flex (i.e. grow or shrink) based on some rules that we can define.

## Flex containers and flex items
Flexbox is not just a single CSS property but a whole toolbox of properties that can be used to put things where it's needed.
Some of these properties belong on the _flex container_, while some go on the _flex items_.

A flex container is any element that has `display: flex` on it. 
A flex item is any element that lives directly inside of a flex container.

Any element can be both a flex container _and_ a flex item. 
Said another way, we can also put `display: flex` on a flex item and then use Flexbox to arrange _its_ children. Making nested flexbox.


#### Example:
Placing two buttons with `display: blocked`  in line and centered.
The main body can be `text-allign: center` but better to use Flexbox.

To use Flexbox, wrap all the buttons in a `div` wrapper.
For the wrapper, `display: flex`
This will override even if the buttons are `display: block` and make them inline

`justify-content: center` to bring them to center.

To add space between the buttons margin can be used in the buttons.
or
`justify-content: space-around`  to distribute all white space around the buttons.
`justify-content: start` to push all to left
`justify-content: end` to push all to right


## Columns in Flexbox

With `display: flex` Flexbox takes all the direct children elements under it and makes it into a separate column so all comes under a single line. 
But
Whole list will have single column, but all of it's children are not in separate column.
Anything that is not a direct children will be grouped in a single column.

So create only as many direct children as needed as the number of columns.

`display: flex` is by default is `display: block` so takes up all the space so width changes as screen size changes.
Width has to be set to center it


- Interneting Is Hard tutorial on [CSS layouts with flexbox](https://internetingishard.netlify.app/html-and-css/flexbox/index.html).
- Slaying the dragon tutorial on [Flexbox in 8 minutes](https://youtu.be/phWxA89Dy94?si=UOXlsTa0BMfQYG3q).




#12sep2024 