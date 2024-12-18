

Content folder
is the root, it cannot contain any other pages except `_index.md`
it can have images but not pages

Sections
The top level content directory `content/directories` are special are use to determine the layout.
also any content directory with `_index.md` file is also a section known as `branch bunndle`.

section templates receive one or more page `collections` in `context`
Sections will have logical ancestors and descndants and list pages.  non sections wont.

> about folder with `index.md` 

### Index pages `_index.md`

It allows to add front matter and content to `home`, `section`, `taxonomy` and `term` pages.
To make a section navigational.


## Page bundles

It is a directory that holds both content and associated resources.
Use page bundles to logically associate one or more resources with content.

'about' page / folder is page bundle with `index.md` and `image.jpg` that is the page resources needed.

Page bundles are either leaf with no descendants but can have resources or
branch (like `about`) and contains `_index.md` and resources.


leaf example `content/about/index.md`
branch example `content/posts/_index.md`

`index.html` can be used for HTML content. 


> headless bundles,  using `build options` in front mater to create an unpublished bundle that can be used in other pages.


## Content formats

`html, markdown(md), emacs org mode, AsciiDoc, Pandoc`
Content types can be mixed throughout the site but should have `front matter` with preferably `title` and `date`.

***Markdown***
Hugo natively renders `md` to `html` using `Goldmark`. It can be configured in site configuration. 
Custom markdown feature,
like `Attributes` to apply class, id to images, block elements, headings lists tables.
`extensions` to create definition, footnotes, subscripts.
`mathematics` for LaTex and Tex syntax
`render hooks` to override the conversion of `md` to html when rendering fenced code blocks, headings, images, links.

***HTML***
after the front matter, place what would be placed within `body`


## Front Matter

Used to add metadata to the content. `toml, yaml, json` serialization formats can be used.

It describes the content, augments it, establishes relationship with other content, controls published structure and determines template selection.

```toml
+++
date = 2024-02-02
draft = false
title = 'Example'
weight = 10
[params]
	author = 'Smith'
+++
```

```yaml
---
date: 2024-02-02
draft: false
title: Example
weight: 10
params:
	author = Smith
---
```

#### Fields

Most common front matte fields are `date, draft, title, weight`
Custom fields can be created under `params` key

***aliases*** an array where each alias is a relative URL to redirect browser to current location.

***build***  a map of build options

***cascade*** a map of front matter keys whose values are passed down to page's descendants.

***date*** typically a string of creation date

***description*** Is rendered within a `meta` element within the `head` of published html.

***draft***  a bool to prevent render, unless `--buildDrafts` flag to `hugo` command.

***expiryDate*** a string of expiry date. will turn to draft  on or after the date.

***headless*** a bool, applicable to leaf bundles. if true, it sets `render` and `list` build options to `never`, creating a headless bundle of `page resources`

**keywords** an array of keywords as meta data. or used as taxonomy to classify content.

***lastmod*** The date that the page was last modified.

***layout*** a string, provides a template name to target a specific template.  base name of template without the extension.

linkTitle

***menus*** string, string array or map, if set, hugo adds the page to the given menu or menus.

***params*** map of custom page parameters

***publishDate***  before the publication date, the page will not be rendered unless `--buildFuture`

***resources*** an array of maps to provide metadata for page resources.

***title*** the page title.

***url*** string that overrides the entire URL path. applicable to regular and section pages.

***weight*** int, used to order the page within a page collection.


***Taxonomies*** to classify the content by adding taxonomy terms to front matter.

Site configuration
```yaml
taxonomies:
	genre: genres
	tag: tags
```
```toml
[taxonomies]
	genre = 'genres'
	tag = 'tags'
```

adding to front matter
```yaml
---
genres:
- mystery
- romance
tags:
- red
- blue
---
```
```toml
+++
genres = ['mystery', 'romance']
tags = ['red', 'blue']
+++
```



### Resource type

page, image, content page!!


