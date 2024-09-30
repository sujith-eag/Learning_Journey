## CSS Colors

Colors in CSS can be specified by the following methods:
- Predefined/Cross-browser color names
- With the `currentcolor` keyword
- Hexadecimal colors
- Hexadecimal colors with transparency
- RGB colors
- RGBA colors
- HSL colors
- HSLA colors


## Predefined/Cross-browser Color Names

[140 color names](https://www.w3schools.com/colors/colors_names.asp) are predefined in the HTML and CSS color specification.
For example: `blue`, `red`, `coral`, `brown`, etc:
```css
#p1 {background-color: blue;}  
#p2 {background-color: red;}  
#p3 {background-color: coral;}  
#p4 {background-color: brown;}
```


## The currentcolor Keyword

The `currentcolor` keyword refers to the value of the color property of an element.

The border color of the following `<div>` element will be blue, because the text color of the `<div> `element is blue:

```css
#myDIV {  color: blue; /* Blue text color */  
  border: 10px solid currentcolor; /* Blue border color */}
```

## Hexadecimal Colors

A hexadecimal color is specified with: `#RRGGBB`, where the RR (red), GG (green) and BB (blue) hexadecimal integers specify the components of the color. All values must be between 00 and FF.

For example, the `#0000ff` value is rendered as blue, because the blue component is set to its highest value (ff) and the others are set to 00.

```css
#p1 {background-color: #ff0000;}   /* red */  
#p2 {background-color: #00ff00;}   /* green */  
#p3 {background-color: #0000ff;}   /* blue */
```

## Hexadecimal Colors With Transparency

A hexadecimal color is specified with: `#RRGGBB`. To add transparency, add two additional digits between 00 and FF.

```css
#p1a {background-color: #ff000080;}   /* red transparency */  
#p2a {background-color: #00ff0080;}   /* green transparency */  
#p3a {background-color: #0000ff80;}   /* blue transparency */
```


## RGB Colors

An RGB color value is specified with the `rgb()` function, which has the following syntax:
`rgb(red, green, blue)`

Each parameter (red, green, and blue) defines the intensity of the color and can be an integer between 0 and 255 or a percentage value (from 0% to 100%).
```css
#p1 {background-color: rgb(255, 0, 0);}   /* red */  
#p2 {background-color: rgb(0, 255, 0);}   /* green */  
#p3 {background-color: rgb(0, 0, 255);}   /* blue */
```


## RGBA Colors

RGBA color values are an extension of RGB color values with an alpha channel - which specifies the opacity of the object.

An RGBA color is specified with the `rgba()`
function:
`rgba(red, green, blue, alpha)`

The alpha parameter is a number between 0.0 (fully transparent) and 1.0 (fully opaque).
```css
#p1 {background-color: rgba(255, 0, 0, 0.3);}   /* red with opacity */  
#p2 {background-color: rgba(0, 255, 0, 0.3);}   /* green with opacity */  
#p3 {background-color: rgba(0, 0, 255, 0.3);}   /* blue with opacity */
```


## HSL Colors

HSL stands for hue, saturation, and lightness - and represents a cylindrical-coordinate representation of colors.

An HSL color value is specified with the `hsl()` function, which has the following syntax:
`hsl(hue, saturation, lightness)`

Hue is a degree on the color wheel (from 0 to 360) - 0 (or 360) is red, 120 is green, 240 is blue. Saturation is a percentage value; 0% means a shade of gray and 100% is the full color. Lightness is also a percentage; 0% is black, 100% is white.

```css
#p1 {background-color: hsl(120, 100%, 50%);}   /* green */  
#p2 {background-color: hsl(120, 100%, 75%);}   /* light green */  
#p3 {background-color: hsl(120, 100%, 25%);}   /* dark green */  
#p4 {background-color: hsl(120, 60%, 70%);}    /* pastel green */
```


## HSLA Colors

HSLA color values are an extension of HSL color values with an alpha channel - which specifies the opacity of the object.

An HSLA color value is specified with the `hsla()` function:
`hsla(hue, saturation, lightness, alpha)`

The alpha parameter is a number between 0.0 (fully transparent) and 1.0 (fully opaque).

```css
#p1 {background-color: hsla(120, 100%, 50%, 0.3);}   /* green with opacity */  
#p2 {background-color: hsla(120, 100%, 75%, 0.3);}   /* light green with opacity */  
#p3 {background-color: hsla(120, 100%, 25%, 0.3);}   /* dark green with opacity */  
#p4 {background-color: hsla(120, 60%, 70%, 0.3);}    /* pastel green with opacity */
```

