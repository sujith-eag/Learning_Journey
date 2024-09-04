[[2 Multiple Selectors]]

## Declaration      #02sep24 
 
- **Declaration** is  property : value
- **Property** which is an identifier, that is a human-readable _name_, that defines the feature.
- **Value** which describe how the feature must be handled by the engine. 

Declarations are grouped in ***declaration blocks*** or CSS blocks which is delimited by `{  }`. 
Separate declarations must be separated by a `;` inside the block.
```CSS
div.bold-text {
				font-weight: 700;
				text-align: center;
				}
    selector    property     value

{
	A CSS block
}
```
Blocks can be nested sometimes but braces must be matched.

# Properties
Each property has a set of valid values, defined by a formal grammar, as well as a semantic meaning, implemented by the browser engine.

#### Color and background-color
The `color` property sets an element’s text color, 
while `background-color` sets the background color of an element.
Almost. Both of these properties can accept one of several kinds of values.

A common one is a keyword, such as an actual color name like `red` or the `transparent` keyword. They also accept HEX, RGB, and HSL values.
[[CSS Color values]]

```css
p {
	  /* hex example: */
	  color: #1100ff;
	}

p {
	  /* rgb example: */
	  color: rgb(100, 0, 127);
	}

p {
	  /* hsl example: */
	  color: hsl(15, 82%, 56%);
	}
```


## Typography basics and text-align

#### Font Family
`font-family` can be a single value or a comma-separated list of values that determine what font an element uses. 
Each font will fall into one of two categories, either a “font family name” like `"Times New Roman"` (we use quotes due to the whitespace between words) 
or a “generic family name” like `serif` (generic family names never use quotes).

If a browser cannot find or does not support the first font in a list, it will use the next one, then the next one and so on until it finds a supported and valid font. This is why it’s best practice to include a list of values for this property, starting with the font you want to be used most and ending with a generic font family as a fallback, e.g. `font-family: "Times New Roman", serif;`

### Font size
`font-size` set the size of the font. 
Value to this property should not contain any whitespace,
`font-size: 22px` has no space between “22” and “px”.

### Font weight
`font-weight` affects the boldness of text, assuming the font supports the specified weight. 
This value can be a keyword, `font-weight: bold`, 
or a number between 1 and 1000, e.g. `font-weight: 700` (the equivalent of `bold`). 
Usually, the numeric values will be in increments of 100 up to 900, though this will depend on the font.

### Text align
`text-align` will align text horizontally within an element. 
Common keywords can be value for this property. `text-align: center`.


## Image height and width
By default, an `<img>` element’s `height` and `width` values will be the same as the actual image file’s height and width. 

Images aren’t the only elements that we can adjust the height and width on.
To adjust the size of the image without causing it to lose its proportions, you would use a value of “auto” for the `height` property and adjust the `width` value:

```css
img {
	  height: auto;
	  width: 500px;
	}
```

These properties work in conjunction with the height and width attributes in the HTML. It’s best to include both of these properties and the HTML attributes for image elements, even if you don’t plan on adjusting the values from the image file’s original ones. 

When these values aren’t included, if an image takes longer to load than the rest of the page contents, it won’t take up any space on the page at first but will suddenly cause a drastic shift of the other page contents once it does load in. 
Explicitly stating a `height` and `width` prevents this from happening, as space will be “reserved” on the page and appear blank until the image loads.


## Inline and Block display

`display: inline` Makes the elements form a line, one after the other.
`displa: block`  makes each item block out the whole line so next item goes to the next line(stacked on each other)
```CSS
img {
		display: Block;
}
button {
		display: inline;
}
```





Next    [[4 Adding CSS to HTML]]


Prev   [[2 Multiple Selectors]]                
