#01sep24  
HTML (HyperText Markup Language) defines the structure and content of webpages. 
We use HTML elements to create all of the paragraphs, headings, lists, images, and links that make up a typical webpage.

## Elements and tags

All elements of HTML are wrapped in opening and closing HTML tags.
`<p>`   Opening tag (angle brackets with keyword) mark the beginning  
`</p>` Closing tag shows elements end, has forward slash before key word
```html
<p>paragrah text</p>
```
[[Catalog of Tags]]

Elements are containers for content, with the tags telling what content the element contains.
Using the correct element for content is called semantic HTML.


#### Void Elements

`<meta>`   `<link>`   `<br>`  `<img>` 
Void elements are void of any content so they have a single tag.

Previously they were called self-closing tags `<br /> or  <img />`   not necessary to do this now with latest version of HTML. So now these are called invalid.


#### HTML file

A HTML file containing the homepage of the website should be `index.html` because servers will first look for that by default.


## HTML Boilerplate

All HTML documents need the same basic structure or boilerplate that needs to be in place before anything useful can be done.

### 1 Doctype
Every HTML page starts with a Doctype declaration which tells the browser what version of HTML it use to render the document.
Latest is HTML5,  and it's Doctype is `<!DOCTYPE html>`
so `<!DOCTYPE html>` should be the first line of the file

### 2 HTML element
`<html>` Root element of the document, meaning every other element will be it's descendant.
`<html lang="en">`  lang is html attribute giving additional info like language
`</html>`  closing tag

### 3 Head element
The `<head>` element is where we put important meta information to help it get rendered correctly in browser.   there should be no element that displays content.
`<head>` should be the first element under `<html>`

#### 3.1 Meta element(s)
```html
<head>
	<meta charset= "UTF-8">`  
	<meta name="viewport" content="width=device-width, initial-scale=1.0"> tag is used in HTML to control the layout on mobile browsers. 

<"UTF-8"> so different symbols get shown correctly

<meta name="viewport"> specifies that the tag is related to the viewport settings.

<content="width=device-width,  initial-scale=1.0"> 
This sets the width of the viewport to match the device's width.
and sets the initial zoom level when the page is first loaded. A scale of 1.0 means that the page will be displayed at its natural size without any zooming in or out.
```
There are other `<meta>` tag functions that can be used to define how it behaves when shared on web and so on.

#### 3.2 Title element
`<title>` is used to give the webpage a human readable title which gets displayed in the webpage's browser tab.
without `<title>` browser defaults to file name `index.html`
```HTML
<!DOCTYPE html>

<html lang="eng">
	<head> 
		<meta charset="UTF-8">
		<title>MY Webpage</title>
	</head>
</html>
```

#### 3.3 link element
`link rel="stylesheet" href="style.css">`
linking the external CSS file to the HTML 
`rel` is relation to the HTML and `href` is HTML reference


### 4 Body element
is where all the contents that will be displayed to users will go - text, images, lists, links etc.

`<body>` will also go after `<head>` but with `<html>`

```HTML
<!DOCTYPE html>

<html lang="eng">
	<head> 
		<meta charset="UTF-8">
		<title>MY Webpage</title>
	</head>
	
	<body>
		<h1>Line to be displayed</h>
	</body>
</html>
```



_______

## VScode boilerplate shortcut

If a file is `.html` type then, in the empty `index.html` file enter `!` select the first option
to get the full boilerplate code.

### To open the file

Drag and drop in address bar of browser or double click
or
in the directory having the file `google-chrome index.html`
or 
using Live Server extension of VScode.
