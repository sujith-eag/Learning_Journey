`Ctrl + P` Command pallet search
`alt` Creating Multiple cursor points by holding down
`Alt + Shift` Selecting multiple sections in different areas 

Tags `#Tag`

`[[]]` Linking Notes
		Creates new file if the file doesn't exist already

`[[link | name]]` Alias Naming using a pipe `|`

`[[Obsidian#Header 1 | Alias]]` using `#` for Tagging the headers or particular section in a page

`[[Obsidian#^352532 | toHideTheNumbers]]` using `^` each small section of a page can be tagged
 
`code line`
```c
code block with language insertions
```



`[name](URL)`  for going out
`![name](URL)`  Putting an `!` to embed the link
![name](www.google.com)


[google](www.google.com "To bring up a pop up while hovering")
`[gog](www.google.com "To bring up a pop up while hovering")`



>[!info] 
>Information Block  >[!info]
>On formatting text and links
>https://help.obsidian.md/Editing+and+formatting/Basic+formatting+syntax


>[!note] : Name
Name, Something more here

^352532

==highlighting a line of text using double equals `==`


%%comments visible only in editing view%% Comments for Obsidian


Tables 
Separating text using `|`   `using --- | below it to make a table`

| Name | Column | Header |     |
| ---- | ------ | ------ | --- |
|      |        |        |     |

# Header 1
###### Header 5

*Italic*  _italic_  `*Italic*  _italic_ `
**bold**  __bold__ `**bold**  __bold__`
~~Strike through~~   `~~Strike through~~`

Quotes using `>  >>`
> Oh quote block
> 
> > Nested quote block


Lists ` + - * 1 `  these signs or numbers will work to start a list
Lists can also be nested
1. one
	1. nested one
	2. nested two
2. Two
3. Three


Checklist  `Not clear still  -[ ] `
- [ ]
- [x]

Seems subscript and superscript are not supported
H~2~O
X^2^

### Creating Footnotes    `[^1]` `[^1]:`

Using `[^1] with a line and  creating the footnote with [^1]: text`
Order of numbers can be changed and numbers will change accordingly

Foot note [^1]
Another one [^2]

[^1]: Linked to the footnote
[^2]: another link

### Inline method for Footnote   `text^[footnote]`
For a foot note^[this is the text for the footnote]

Got added automatically without having to move to the end of the page to create a footnote

Can also include Links to files
Going to other file^[[[Obsidian | this file]]]    Just that it needs Three brackets
Alias can be set like before



### Images
` ![link text](URL)`
` ![link text](URL or location   "Alt text")`






# Converting Markdown to HTML
Check out (markdownguide.org)
awesome-markdown  in gitub for resources
Markdown processors(parsers) in a markdown applications can take Markdown text and format it into HTML file which can be made into a webpage by assigning a style sheet.
Or the HTML can also be made into PDF

Ghostwriter seems like a choice, or Markdownmonster  for windows
for linux, ReText or Ghostwriter

Jekyll a popular static site generator that takes markdown and builds HTML websites.
GitHub pages provide free hosting for these pages
(other generators at Jamstack as static site generators)



Line breaks - or new lines , leave two or more spaces after a paragraph which brings` <br> ` tag within the `<p> </p>` in the HTML file 


VS Code plugins
	Markdown Extended
	Prettier- code formatter
	Markdown Shortcuts
	Markdown preview enhanced


#11sep2024