`template actions` are data evaluation or control structures within a `template` delimited by "{{" and "}}"  [Go templates](https://pkg.go.dev/text/template#hdr-Actions). 

templates are executed by applying them to a data structure.

Annotations in template refer to the elements in data structure(typically field of a struct or key in a map) to derive values.

Execution of the template walks the structure and sets the cursor, represented by a period '.' called dot to the value at the current location as execution proceeds. all text outside actions are copied to output.


[[`archetypes`]] receive info about ***date***, file info about ***current page***, ***content type***, ***site object***

```toml
date = '{{ .Date }}'
date = '{{ time.Now.Format "2006-01-02"}}'
# for using alternate format 'time.Now'

title = '{{ replace .File.ContentBaseName "-" " " | title }}'
```