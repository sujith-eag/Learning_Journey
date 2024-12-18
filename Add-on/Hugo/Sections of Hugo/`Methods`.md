(previously variables)
are not accessible inside content, only inside `template` 
`{{ .Title }}` many more defaults.

Custom variable in front matter, and accessing it using variables inside template.
`myVar: "myValue"`   in front matter
`{{ .Params.myVar }}`  accessing that variable.

Creating custom varible inside template
`{{ $myVarName := "aString" }}`   assigning
`{{ $myVarName }}` accessing
`<h1>{{ $myVarName }}</h1>`    making it a header

params  parameters
