### Utility class
A class for a single CSS property.

Define a class that has only one property and put it for any element in the HTML file.
Normal way was, name a class, set a property later.
Here, it's like first define a class in CSS and then move it to HTML wherever it is needed. or to the main parent.
`.italic { font-style: itlic}`
This also allows for easily removing certain properties as it is just one line.

Select any line and `Ctrl + D` which selects all instance of it, then can be edited at once.


## Inheritance
Inheritance refers to certain CSS properties that, when applied to an element, are inherited by that element’s descendants, even if we don’t explicitly write a rule for those descendants. Typography-based properties (`color`, `font-size`, `font-family`, etc.) are usually inherited, while most other properties aren’t.
##### DRYer code : do not repeat yourself
Knowing which property will be inherited, putting that in the parent tag and it will be inherited by all parents. 
Anything that is unique to a specific tag can be put there.

There are 41 properties which are inheritable, check the list
`colour` `font related` `text-allign`  are main ones.



# Font
Web safe fonts (10 fonts)

In applying font, it applies a font stack, where if first isn't available, it moves to next one. 




Making a circle from a sqare,   "border radius: 100%"










