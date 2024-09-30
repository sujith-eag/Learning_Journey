
# Box Model    #04sep24 

[MDN’s lesson on the box model](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model). Inline boxes !

Every single thing on a webpage is a rectangular box. These boxes can have other boxes in them and can sit alongside one another.

Margin, Border, Padding and Content is what is called box model.
` * {outline: 2px solid red}`   marking boxes

## 1 Margin
Margin is the white space around an element.
The default margin is `8px` can be set to `0` to remove it.
[CSS Tricks page on margins](https://css-tricks.com/almanac/properties/m/margin/) 

***Collapsing margins***
If `15px` is added on bottom of first element and `20px` is added on top of second element. both margins will be between first and second element and it will not become `35px` of space.
it will stay as `20px` because the largest one takes precedence.

#### Centering horizontally with margins
1. set `display: block;` to block whole line
2.  element must have a width
3.  set margin left/right: auto;    
 `margin-left: auto` moves the object to left making all space in right as margin.
 `margin-right: auto` both in conflict divides the margin space between both and gets centered.

#### Margin & Padding short hands
If Margin of Top, Right, Bottom, Left are all same, then instead of using one for each side we can just do `margin: 10px`   gets to all sides

If each values are different, then the clock method works
`margin: 10px 20px 30px 40px`   which is 
`margin: top right bottom left`

If only two values are given to `margin`, the first one is considered for `top and bottom`,   second value becomes `left and right`
`margin: 20px auto`
`margin: T&B  L&R`        this centers it horizontally 



## 2 Padding
Padding increases space b/w the border of a box and the content of the box.
Padding adds space inside the container.
Default padding inside a div will be zero
left right top bottom can be altered

The short hand works as described above for margin

## 3 Border and Border radius

`border` adds space even if it's only a pixel b/w margin and the padding.
It can be colored, made thick, change design 
the radius can be altered to make it less sharp

`border: 8px solid blue`
`border-radius: 10px`   to make it rounder

***Careful with border*** for `div` as it does not specify what to include.
border thickness, style and color all three has to be set in one `border` for it to be visible. `border: 8px solid blue`

## 4 Content
`height: 24px`   this will be just the height of the content excluding the padding in a button.
or `line-height: 24px` can be used which does the same thing.
line height is the height of one line of text



`box-sizing: content-box`   larger?
here the size of the box will be `width+paddig+border`
so if width is `300px` it is the width of the content of the box but not the box.

`box-sizing: border-box`   smaller?
the size of the box will be whatever the width we set as the width is set for the box itself, not the content.
the size of the content is changed to fit padding and border inside the specified box width.

The default is `box-sizing: content box` for all elements in HTML, so this is reset and made into border box
```css
* {
	margin: 0;
	padding: 0;
	border: 0;
	box-sizing: border-box;
* }
```





### Additional resources
1. [Learn CSS Box Model](https://www.youtube.com/watch?v=rIO5326FgPE)
2. [box-sizing: border-box](https://www.youtube.com/watch?v=HdZHcFWcAd8)
- [Scrim on the box model](https://scrimba.com/scrim/cof3d488184abe24ec6258ab4).
- [Slaying The Dragon](https://youtu.be/nSst4-WbEZk?si=HbgcEB7UyLdNbE6n)  for understanding the box model.
