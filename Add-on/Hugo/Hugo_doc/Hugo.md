
Installed ***Go*** using extraction,
installed ***hugo*** as a snap package,
***Dart sass*** was supposed to be installed but included in `hugo` snap,
***git*** is anyway there.
	So these are the basic things needed.

`hogo.toml` file in root is used to configure system wide settings.
	`hugo.yaml` can also be used, just preference as both work.
`baseURL` has to be the final link the site will be / is deployed on. 

shortcut to pass setting to `.toml`
	`echo "theme = 'anake'" >> gugo.toml `


## Basic hugo commands

`hugo --help`
`hugo new --help`
`hugo gen man` `hogo gen doc`


`hugo new site nameOfSite --format=yaml`   makes the config file `yaml`
`mkdir content/folder`  making folder in content
`mv content/file.md content/blog/`  moving files around

`hugo new file.md`  creates a markdown file in `content` with template.

`hugo new content about/index.md`
`hugo new content posts/topics/JavaScript/_index.md`
On base hugo site i could make directory and file at once



`hugo server` live render of the site.
`hugo server --disableFastRender`
`hugo server --noHTTPCache --disableFastRender`
`hugo server --disableLivReload`
`hugo server -D`

`hugo`  renders the site from files and puts it in the `public` folder.








_________________
## Folder Structure

`_index.ma` file will be read in root file, it will take precedence over `list.html`  so works as a main file. (i still don't have one properly set up )

### archetypes folder

has templates for creating new files when `hugo new file.md` is called
will have script to guess name and date
#### front mater / template
`hugo` variables to add
```
---
title:   date:   draft:   tags: 
---
```
To add cover image
```
cover:
	image: img.pic.jpeg
	alt: 'post image'
	caption: 'adding caption'	
```
Adding menu
linking to layout files as template
categories, tags
breadcrums, linkfull image

(most are theme specific) most goes into `hugo.toml` file


### content folder

all folders and md files are kept here
`hugo new posts/first.md` making file in folder inside content


### Static folder

for anything that is not a mark down file, like image, file, css goes here


### Public folder

will have the rendered site files. can be deleted and re rendered.


#### Themes folder

theme is added to this using git clone, or go module!!, fork can work
`git clone <link> themes/nameOfFolder`

adding `theme = 'nameOfFolder'` in `toml` file to link it

default of theme will have `single.html` `link.html` two files to handle single pages and list like pages

adding HTML file in layout takes precedence over `list.md`

`partial` folder has bits that are called by default like header and footer


### layout folder

comes with themes containing html file, when something has to be modified, 
that particular HTML can be copied over to `layout` folder in root to override it from theme.
The folder structure has to be similar.
prevents loss of structure when updating theme

____________



# Mark Down file
linking files using `[]()`  as regular mark down.
linking image which is in static folder `![]()` 

the link should not be `/static/image.jpeg` because while rendering, the files in `content` and `static` will be moved to `root` folder so `/image.jpeg` will work.



# Deployment

Adding `.gitmodules` file to root to add the theme as `submod` so in git the theme folder references the `git` repo of theme instead of having the file and downloads it. 
```
[submodule "themes/PaperMod"]
	path = themes/PaperMod
	url = gitLinkToTheTheme.git
```
push to git for a repo
(I didn't like the idea of a theme as a dependency so took key files, removed theme, reference and the module link,  it works still)


`netlify` as hosting space, didn't try yet.
`netlify` account
new site from git, link a repo, build command hugo


If the whole folder is set to git repo, pages has to be done by GitHub actions
`.github` folder is needed in root, within that `workflows` folder and `hugo.yml` file.
Contents are in hugo site
This gives a GitHub action.


