partial templates
is another folder under layouts that has parts that can be added into other templates. `footer, head, header, main, private, sidebar` these will have their own separate files which have some functions.
Accessed using `{{ partial "header" . }}`
if within a folder `{{ partial "footer/footer" .`
`.` works as the scope that gives access to all the methods inside the partial