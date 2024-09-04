[[4 Adding CSS to HTML]] 

# Box Model    #04sep24 
Margin, Border, Padding and Content is what is called box model.

## 1 Margin
Margin is the white space around an element.
The default margin is `8px` can be set to `0` to remove it.

***Collapsing margins***
If `15px` is added on bottom of first element and `20px` is added on top of second element. both margins will be between first and second element and it will not become `35px` of space.
it will stay as `20px` because the largest one takes precedence.

#### Centering horizontally with margins
1. set `display: block;` to block whole line
2.  element must have a width
3.  set margin left/right: auto;    
 `margin-left: auto` moves the object to left making all space in right as margin.
 `margin-right: auto` both in conflict divides the margin space between both and gets centered.


## 2 Padding
padding adds space inside the container, i e between the content and the edge of the container.
Default padding inside a div will be zero
left right top bottom can be altered


## 3 Border and Border radius
`border` is the line that is between padding and margin.
it can be colored, made thick, change design 
the radius can be altered to make it less sharp

`border: 8px solid blue`
`border-radius: 10px`


## 4 Content
`height: 24px`   this will be just the height of the content excluding the padding in a button.
or `line-height: 24px` can be used which does the same thing.
line height is the height of one line of text




# Flexbox
When two buttons have to be placed in line and centered, its difficult as they will be `display: blocked`.
The main body can be `text-allign: center` but better to use Flexbox.


To use Flexbox, wrap all the buttons in a `div` wrapper.
For the wrapper, `display: flex`
This will override even if the buttons are `display: block` and make them inline

`justify-content: center` to bring them to center.
To add space between the buttons margin can be used in the buttons.


`justify-content: space-around`  to distribute all white space around the buttons.
`justify-content: start` to push all to left
`justify-content: end` to push all to right







Next   -

Prev      [[4 Adding CSS to HTML]]