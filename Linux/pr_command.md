
The pr command in Linux is used to format text file for printing.

It adds header, footer, page breaks, columns and more to make output looks structured when printed.

`pr [options] [file]`


`-n`  Set number of columns for output formatting   `-pr -3 file.txt`
`-h`  Set a custom header for the output  `pr -h "My header" file.txt`
`-l` Define page length (default is 66 lines)  `pr -l 50 file.txt`
`-t` Remove header and footer form output   `pr -t file.txt`
`-d` Double-space the output  `pr -d file.txt`
`-o` Add left margin offset (indentation)    `pr -o 5 file.txt`
` | pr `  Combining with other commands for formatting output.   `ls -l | pr -3`


