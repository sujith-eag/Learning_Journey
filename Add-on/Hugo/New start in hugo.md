Set up a site, 
added nothing else,

`Page not found`

first 
`layouts` need html template files for 
page, section, home and taxonomy which follow hugo lookup rules.

> I have forgotten `hugo` command for final build
>> Try it with the personal blog to just add public in new repo


Moved `hugo.toml` to `config/_default` just for structuring

_________________
____________

[[`archetypes`]] made a new template `notes.md` and called `hugo new notes/second.md` and it got made according to `notes.md`

Each folder in content can have its own archetype like `blog` `post` `about` and its respective file will be `blog.md`.   If nothing matches, then `default.md` is used.

____________

[[`Functions`]] are used within [[`template actions`]]. 
function takes one or more arguments and returns a value.

[[`archetypes`]] receive info about ***date***, file info about ***current page***, ***content type***, ***site object***

```toml
date = '{{ .Date }}'
date = '{{ time.Now.Format "2006-01-02"}}'
# for using alternate format 'time.Now'

title = '{{ replace .File.ContentBaseName "-" " " | title }}'
```

________

`leaf bundles`  [[`page bundle`]]
Resources within a page bundle are `page resources`, accessible with [[`Resources`]] method on the [[`page object`]].
Page resources are only accessible from page bundles (dir with `index.md` or `_index.md` at their root).

______________

[[`template actions`]] are used within an archetype to populate the front matter or the body with content when file is created.
It can also be placed in body, gets evaluated every time it is rendered, in template it gets called once.

> template action in body for fresh date!!,  It worked even with " "
> it can be made into template and used!!


Templates are HTML files with [[`template actions`]] located within `layouts` directory of a project.
> [templates](https://gohugo.io/templates/)


_________

Configuration

The root contains `hugo.toml yaml json` as configuration file.
it can be moved to [[`config`]] directory.
The config file can be split by environment, root, configuration, root, language etc
[All configuration settings](https://gohugo.io/getting-started/configuration/#all-configuration-settings)

 

 [[`branch bundle`]] the page kinds are `home, section, taxonomy or term` similar template also can be made.   Its resource type is all but `page`.


home page template `layouts/index.html` along with `layouts/404.html`
templates in [[`layouts`]] folder

__________

#### links and html

Adding a pop up title to show on link ???
`[link name](http://link/path/to/target "Title On Link")`

HTML in MD works as html, Unicode characters can be written using HTML escape tag ???
so ; is the escape character.


&copy;    without ; also worked
`&copy  became © `
&trade;   this didn't work without ;
&lt  <
&gt >
&#x1F604   this is a smiley

Oh, superscript  X<sup>2</sup>  `X<sup>2</sup>`   

Making  a floating image  
`<img src=/image/logo.png  style="float: right; padding: 0 0 0 10px">`

It is not good practice to use embedded HTML in markdown content.
Hugo disables html by default, it can be enabled via the `unsafe` key in the `markup/goldmark/renderer` section if `config.toml` file.
```yaml
markup:
  goldmark:
    renderer:
      unsafe: true
```

Unicode characters are not disabled.

________________

#### table, tasks, code blocks

Github flavoured markdown(GFM) ??? are extensions to markdowns.
tables, (`|`) (`-`)

Alignment defined by putting these below as column line
right aligned `--:`  
left aligned `:--`
center aligned `:-:`
undefined `---`

Wow, obsidian auto completed this before second line, i didn't even put outer `|`
```
| Index | Product | Edges |
| ----: | :------ | ----- |
|       |         |       |
```

- [x] get update
- [ ]  no update 
- [ ]  about page
```
- [x] get update
- [ ]  no update 
- [ ] about page
```
the dash and space is needed, also space between the brackets.


In code block, code highlighting is not active by default, has to be changed in config
```
markup:
  highlighting:
    lineNos: true
```


_____________

### Enabling Emojis in hugo config
```
theme: Eclectic
enableEmoji: true
```

allows to make emoji by surrounding its name by colon `:smile:`  `:heart:`
doesnt work in obsidian but other places (https://www.unicode.org/emoji/charts/emoji-list.html)  is the list of such supported emojis.


Headers become id's, Custom Id and classes can be added using `{}` and using CSS identifiers.
`## heading {#id .className attribute="value"}`

Highlighted text by styling ???
`## This line is highlighted {style="background: yellow"}`

Definition list
  : made from lines
  : with lines

_________

Meta data using YAML
Which is a structured data with keys and values separated by :
```yaml
# is a comment

numbers, strings, bool are supported and guessed automatically

key: value

key: "string"  # "" makes string
```
Yaml is sensitive to space and indentation. A new line character defines the beginning of a new YAML key-value pair.  

```yaml
using | to make multi-line string
using > ignores all new lines and makes one line.

key1: |
	this is a multiline string
	where enter key is valid

	another new line here.


key2: >
	This is a a line
	which will be merged to single line.


Both need two blank lines to get closed.
```

Lists in YAML are declared using `-` or `[]` square brackets.
```yaml
key1:
	-a
	-b

key2: [d, e, f]
```

Dictionaries or maps or objects are key value pairs.
Order doesn't matter but indentation does
```yaml
key1:
	key11: value13
	key12:
	  - List Item 1
	  - List Item 2
	key13: 10

key14: {key14: value14}
```


In yaml strings are optional, type is guessed.
In toml every string has to be in a " "

#### Common meta data in front matter

It is like a page specific config file. The general properties of the site can be overridden.

`title`
default will be name of the file,
used in summary page

`description`
is provided to search engines and can be used in listing pages.

`keywords`
these are passed on to bots and search engines. like tags in youtube

`type`
Default is the subfolder containing the current file;
Content type for theme as each one can render differently.

`slug`
default is `<folder>/<title or filename>`
It is the final part of the url of the file in the web browser. There is also an `url` filed.
useful when going for multilanguage so prefix can change.

`aliases`
Alternate url can point to the same content, allowing us to retain our links. Used for migration from an old system to Hugo. Redirecting link.

`cascade`
lets us set a front matter property on all child pages in a folder.

`tags` 
used to supply tags with the default hugo config.

`date`
`draft`
`layouts` filed that hugo uses to render the page. (single, list)
`outputs` will it be `json` or `html`


#### Data-driven landing page using the front matter

Individual pages can be supplied for the carouse as key-value pairs.
Photo, text carousels, icon based lists, testimonials, client icons all driven by data that we can provide in page's front matter. ???

___________________

## Content management with hugo

menu items added through the front matter of index files of sections. into main or footer.
```yaml
---
menu:
	main:
		name: Blog
		identifier: blog
		weight: 110
	footer:
		name: Blog
		weight: 100
---
```

#### Page bundles

Prevents scattering of files across database, file systems. Page bundle allows making the cleanup and associations easy.
Making the contents of the web page more self contained.

leaf bundles - 
are collection of textual and non textual elements needed to independently represent the core contents of a single web page. also include page specific JS and CSS.
make a folder in the same place as the md file with same name without the extension and move the md into the file, change name to `index.md` and add all needed resources to it.
This folder can be moved to any place and it will contain everything it needs to run.

`index.md` represents a single page while `_index.md` represents a section's root which is a set of web pages.

branch bundles - 
headless bundles -


### More than tags: Taxonomies



