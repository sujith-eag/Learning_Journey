HTML (HyperText Markup Language) defines the structure and content of webpages. 
We use HTML elements to create all of the paragraphs, headings, lists, images, and links that make up a typical webpage.

## Elements and tags

All elements of HTML are wrapped in opening and closing HTML tags.
`<p>`   Opening tag (angle brackets with keyword) mark the beginning  
`</p>` Closing tag shows elements end, has forward slash before key word
`<p>paragrah text</p>`
[[Catalog of Tags]]

Elements are containers for content, with the tags telling what content the element contains.
Using the correct element for content is called semantic HTML.

#### Void Elements
`<br> or  <img>` Void elements are void of any content so they have a single tag.

Previously they were called self-closing tags `<br /> or  <img />`   not necessary to do this now with latest version of HTML. So now these are called invalid.

#### HTML file
`html-boilerplate` folder
`index.html` file
A HTML file containing the homepage of the website should be `index.html` because servers will first look for that by default.

## HTML Boilerplate
All HTML documents need the same basic structure or boilerplate that needs to be in place before anything useful can be done.

#### Doctype
Every HTML page starts with a Doctype declaration which tells the browser what version of HTML it use to render the document.
Latest is HTML5,  and it's Doctype is `<!DOCTYPE html>`
so `<!DOCTYPE html>` should be the first line of the file
#### HTML element
`<html>` Root element of the document, meaning every other element will be it's descendant.
`<html lang="en">`  lang is html attribute giving additional info like language
`</html>`  closing tag
#### Head element
The `<head>` element is where we put important meta information to help it get rendered correctly in browser.   there should be no element that displays content.
`<head>` should be the first element under `<html>`
#### Meta element
it should contain the charset encoding of the webpage in `<head>`
`<meta charset= "utf-8">`  so different symbols get shown correctly
#### Title element
`<title>` is used to give the webpage a human readable title which gets displayed in the webpage's browser tab.
without `<title>` browser defaults to file name `index.html`

There are more things that go into head

```
<!DOCTYPE html>

<html lang="eng">
	<head> 
		<meta charset="UTF-8">
		<title>MY Webpage</title>
	</head>
</html>
```



### Body element
is where all the contents that will be displayed to users will go - text, images, lists, links etc.

`<body>` will also go after `<head>` but with `<html>`

```
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


### VScode boilerplate shortcut
If a file is `.html` type then, in the empty `index.html` file enter `!` select the first option
to get the full boilerplate code.

### To open the file
Drag and drop in address bar of browser
or double click
or
in the directory having the file `google-chrome index.html`


[First webpage](https://www.youtube.com/watch?v=V8UAEoOvqFg&t=93s)