`baseof` templates and `block`

`baseof` template in `_default/_markup` acts as the frame where all other partial parts are attached onto.
`block` is special entity in `blockof`
`{{ block "main" . }} {{ end }}`

The main can be defined in `index list single`. or any template.
`baseof` being the higher template, calls the `main` defined in whichever file it is and inputs that value within its structure.

`{{ block "footer" . }}  some default values {{ end }}`
suppose a `{{define "footer" }} Over rides default {{ end}}` is put in single, it over rides the default value in `baseof` and replaces it with what is coming from `single`. if nothing comes, it uses default value.