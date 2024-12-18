Each folder in content can have its own archetype like `blog` `post` `about` and its respective file will be `blog.md`.   If nothing matches, then `default.md` is used.

`archetypes` receive info about ***date***, file info about ***current page***, ***content type***, ***site object***

```toml
date = '{{ .Date }}'
date = '{{ time.Now.Format "2006-01-02"}}'
# for using alternate format 'time.Now'

title = '{{ replace .File.ContentBaseName "-" " " | title }}'
```