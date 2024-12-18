
## Story on getting first site running

The time of update in hugo, the dependency deprecation of few lines, the difference in running things locally and running it online where dependencies get downloaded differently.
The problem of hard coded values verses getting values through variable shortcodes or something (which is like another language).

Had to get around debugging too many times altering the set structure, then going into the github issue and feature sections, understand the npm and dependency install. It was great to see the change in a package right after i raised the issue and that indirectly resolved my issue 2 days later.

The getting stuck at not knowing what to do when it is inaccessible but realizing nothing is and can be handled if people are there to help out. The path to figuring out the solution was very satisfying after the frustrations of failures.

Even though i did very basic changes but not hard coding but still making this site taught me more than other things and how different the other things are than what has to be done.

__________
> ctrl+shift+v   just gets it as is, would have saved so much time during the DSA mess.
> Also changing VS code "Copy with syntax highlighting"

Moving from obsidian to VScode is fine but reverse is formatting nightmare. with extra spaces and miss allignments.
Should avoid it all cost so build in Obsidian and launch once into VScode.
____________


> [Goldmark](https://yuin.github.io/goldmark/playground/)   [Goldmark git](https://github.com/yuin/goldmark?tab=readme-ov-file)
This project is very interesting and flexible if i can do something with it.

There is issue now with the conversion of markdown to html,
> I used <br /> where two space and enter was needed, great.
> Its again VS code that is removing that space so line break is missing. fixed
> and no need for <br />

first is next line not getting noticed so manual adding.

Then there is callout blocks getting called out from within code block.
Adding the code block meta data which was not so tough.
then image tags got called from code block..
none are a big issue as it affects demo stuff but better in deployment usage.

this has something to do with html conversion being done by gold...something, there is options to modify, need to look a it.
______________

Then there is the sidebar for navigation, which has default that displays everything, the weight for page needs careful assignment,
also its better if each section has just its navigation sidebar,, 
there is something about that, need to experiment there.

Using bread crumbs to path the file
> Pagination , Pager, Paginate

___________



Seeing these CMS netlify and many more branches of it, CloudCannon, then there is so much about Go modules which needs to be looked at.
There are commercial and opensource, with lot of libraries which i have to see how to use.

There are familar words i've been hearing like SvelteKit, astro, jekyll and not sure what exactly. 

_______

GitHub allows YAML front matter to allow navigation???

_____
copying a logo svg from using dev tools

__________



## Themes

A proper site for personal profile [hugo profile](https://github.com/gurusabarish/hugo-profile)
Moderate and good enough [Poison](https://github.com/lukeorth/poison?tab=readme-ov-file)

Fancy, complicated and documented [blowfish](https://github.com/nunocoracao/blowfish)
simple and still under construction [anubis2](https://github.com/Junyi-99/hugo-theme-anubis2)
kind of ok but not what i wanted [hugo paper](https://github.com/nanxiaobei/hugo-paper?tab=readme-ov-file)
Hmm maybe [bearcub](https://github.com/clente/hugo-bearcub)
Looks simple starter but buggy  [Hextra](https://github.com/imfing/hextra?tab=readme-ov-file)
Lot of dependencies [Hugoplate](https://github.com/zeon-studio/hugoplate)


Fully professional and feature rich and proper documentation [doks](https://github.com/thuliteio/doks)
`got stuck due to error, raised issue in github`

Modern [E25DX](https://github.com/dumindu/E25DX)  
`First try but stuck without doc and design not being obvious`

Simple and direct [Hugo blog awesome](https://github.com/hugo-sid/hugo-blog-awesome), Took the idea and basic files and ran.

https://themes.gohugo.io/


[Guy who did what i wanted to do](https://santacloud.dev/posts/creating-my-blog---a-developers-tale-of-over-engineering-using-obsidian-hugo-and-github-pages/)
