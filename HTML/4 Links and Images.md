## Anchor elements
An anchor element is defined by wrapping the text or another HTML element we want to be a link with an `<a>` tag.
``
```HTML
<a>About</a>
<!-- Needs href to point to where to go-->
<a href="https://www.theodinprojct.com/about">About</a>
```
### Opening links in a new tab
Default will be opening the link in the same tab `_self.
This can be changed by using the attribute `target="_blank"`

```HTML
<a href="https://www.theodinprojct.com/about" target="_blank" >About</a>
```

## `rel="noreferrer"`
To avoid the webpages knowing which pages have links pointing to them this tag is used, and also prevents the opened webpage from gaining access to the webpage it was opened from.

```HTML
<a href="https://www.theodinprojct.com/about" target="_blank" rel="noreferrer">About</a>
```


### Absolute and Relative Links
***Absolute links*** are Links to pages on other websites on the internet. A typical absolute link will be made up of: `protocol://domain/path`. An absolute link will always contain the protocol and domain of the destination.
`https://www.theodinproject.com/about`

Links to other pages within our own website are called relative links. Relative links do not include the domain name, since it is another page on the same site, it assumes the domain name will be the same as the page we created the link on.


***Relative links*** only include the file path to the other page, _relative_ to the page we are creating the link on. The second link is providing the location of file within the folder. Using `./` starts from root folder so prevents mistakes.

```HTML
<body>
  <h1>Homepage</h1>
  <a href="https://www.theodinproject.com/about">About The Odin Project</a>

  <a href="./pages/about.html">About</a>
</body>
```




# Images
`<img>`  is a void element so takes the link within the tag but doesn't need a closing tag.
`<img src="https://www.google.com/somepic.png">`

##### Path of file
Using `../` to go up a directory and finding the folder with image while using relative path. Or absolute path can be used.

#### `src` attribute
`<img src="image">` is used to assign the location of file to the tag.

#### `alt` attribute
It is the alternative text for the image which is shown when image is not found.
`<img src="image" alt="Logo of site">`

#### Image size 
Not required but specifying height and width attribute helps the image get loaded properly.
````HTML
<img src="https://www.theodinproject.com/mstile-310x310.png" alt="The Odin Project Logo" height="310" width="310">
````

#### Supported formats
`.JPG   .PNG  .GIF  .SVG`

# File Structure
Root folder which has everything
	index.html     mandatory in root file
	image folder
	css folder
	js folder

No spaces, No numbers, No capitals in names.
Keep names short and basic.
All other webpages can be in the root folder or separate.
