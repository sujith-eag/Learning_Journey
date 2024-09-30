
# Flexibility

Making the Flex items responsive and changing their shape according the flex container they are in.

## Components of flexibility
### `flex-grow` 
A flex container distributes its free space to its items to fill the container.
Takes a single number as its value which is the "growth factor"
`flex: 1 1 0%` makes all the div grow the same amount.
if `flex: 2 1 0%` is used in any of the other div, it will grow 2 times the size of the other.

### `flex-shrink`
Sets the "shrink factor" of a flex item. Shrinks the items to prevent overflow.
This gets applied only if the size of all flex items are larger than their parent container.

`flex-shrink: 1` is the default value, which means all items will shrink evenly. A higher number can be  selected for an item to make it shrink at higher rate.
>Ex: Suppose width of 3 div is set to 100 each and the parent div isn't 300, then all div will shrink evenly to fit

If any specific item should not shrink below its defined size, then `flex-shrink: 0` can be used. It will grow beyond this size but will not shrink below it.

>[!note]
>  When `flex-grow` and `flex-shrink` is specified, the flex boxes wont respect the given values of width. They shrink and expand to fill the box.
>  
>  When `flex-grow` `flex-shrink` are 0, they will be completely inflexible.

### `flex-basis`
It forms a generic flex size which acts like width or height depending on primary axis.
It sets the `hypothetical size` of an element in primary axis.

This sets the base size of the flex items, so any shrinking and growing starts from that baseline.

`flex-basis: 0%`  is the default in the shorthand value.
with basis set to 0, items would ignore the item's width and everything would shrink evenly.

`flex-basis: auto` Using `auto` tells the item to check for a width declaration. 
If any one element has to shrink differently, better to set that one to `flex-basis: auto`

> Default for `flex-basis` is `auto`   but in shorthand `flex: 1` it will be 0%


# The `flex` shorthand
Shorthand properties are CSS properties that lets you set the values of multiple other CSS properties simultaneously.

`flex` declaration is a shorthand for 3 properties that can be set on a `flex item`.


## Basic Values of `flex` 

### `flex: auto`
`flex: 1 1 auto`
is shorthand that means `flex-grow: 1, flex-shrink: 1, flex-basis: auto`
Sizes the item based on width and height properties but make it fully flexible so they absorb any free space and shrink to fit.

### `flex: <positive-number>`
`flex: 1`   is equal to  `flex-grow: 1, flex-shrink: 1, flex-basis: 0`
that is `flex: 1 1 0`
Makes it receive the free space proportionately.

### `flex: initial`
`flex: 0 1 auto`     
size will be based on height and width (since basis is auto). but makes it inflexible when there is free space but prevents overflow and shrinks.

### `flex: none`
`flex: 0 0 auto`  
Fully inflexible and size is set by height and width.




> So in practice, 
> `flex-grow: 1` is used to make sure all grow evenly
> 
>`flex-shrink: 0` to keep certain div's from shrinking beyond certain size.
>
> Setting One div to `flex: 1` and not using `flex` for others will make the one expand and contract while the other will stay inflexible.  


### Resource links

[General Shorthand Properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties)
[Shorthand flex documentation](https://www.w3.org/TR/css-flexbox-1/#flex-common)
[Flex documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/flex)

CSS Channel [Demo Video on Flexbox](https://www.youtube.com/watch?v=u044iM9xsWU&t=1s) 


#12sep2024 