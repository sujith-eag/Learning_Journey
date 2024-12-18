

## Build options

help define how hugo must treat a given page when building the site.

Build options are stored in a reserved front matter object named `build`
```yaml
---
build:
	list: always
	render: true
	publishResources: true
---
```

### list
when to include the page within page collections.
`always  local  never`

***always*** include page in all page collections.
***local*** include in local page collection.
***never*** do not include in any page collection.


***publishResources***
applicable to page bundles, determine whetehr to publish associated page resources or not.
true is the default.


***render***
always - default, render page to disk
link - do not render, but assign `Permalink` and `RelPermalink` values
never -  never render

Any page, regardless of  its build options, will always be available by using
`.Page.GetPage`  `.Site.GetPage` method.

so a headless page can be made and then used in other pages. 

Headless section
list without publishing
publishing without listing
conditionally hide section



## Page resources

Are accessible to only from `page bundles` / folder, those directories with `index.md` or `_index.md` files at their root.
(it can be a folder of images in that bundle)

These methods can be used on a page to capture page resources.
```
Resources.ByType
Resources.Get
Resources.GetMatch
Resources.Match
```

