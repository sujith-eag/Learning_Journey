(`home.searchingindex.json` ???)

`layouts/_default` folder having the main `single.md` `list.md`, [[`baseof.md`]] and `term  terms  version`  also `section.sitemap.xml`

There is also `layouts/_default/_markup` which has `render.--` files

section templates, 
each specific folder in content can be given its own template by making a folder with same name in layouts, `layouts/blog/single.html`
they can have their own `list single` templates.

[[`partials`]], partial templates
is another folder under layouts that has parts that can be added into other templates.


[[`shortcodes`]], shortcode template
These are essentially `partial templates` but instead of being used inside of templates inside layout folder for `HTML` files, it is used inside content folder with the `markdown` files to insert some specific code. 


[[`Methods`]] are not accessible inside content, only inside `template` 


[[`Functions`]] Prebuilt code to be used in templates. 
`{{ funcName param1 param2 }} {{ end }} `

