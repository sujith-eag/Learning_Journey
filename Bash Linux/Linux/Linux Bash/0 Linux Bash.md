## Linux and Bash
[The Unix Shell](https://swcarpentry.github.io/shell-novice/index.html)
[Bash](https://swcarpentry.github.io/shell-novice/)
[Book link](https://www.learnenough.com/command-line-tutorial)
[CL flash cards](https://flashcards.github.io/command_line/introduction.html)
[Command line](https://www.softcover.io/read/fc6c09de/unix_commands/ack_ag)
[GNU Coreutils](https://www.gnu.org/software/coreutils/manual/coreutils.html)

### [[1 Navigating Files & Dir]]
`clear`
`sudo apt upgrade update`  `/`  `.`  `..` 
`syntax of command, options, arguments`
`Tab completion`
`man`  `--help`
`pwd`
`relative and absolute paths`
`Combining options`
`cd`   `cd ..` `cd -`  `cd /` `cd ~`  `cd ../..` 
`ls`  `ls -F`  `ls -s` `ls -S`  `ls -l`  `ls -a`  `ls -R` 

### [[2 Working with Files & Dir]]
`touch`
`mkdir`   `mkdir -p` 
`naming conventions`
`nano`
`rm`   `rm -i`   `rm -r`
`mv`   `mv -i` 
`cp`   `cp -r`
`wild cards  * ?`

### [[3 Pipes and Filters]]
`wc`   `wc -l`   `wc -m`  `wc  -w`
`>`    `>>`
`echo`
`cat`
`less`
`sort`   `sort -n`  `sort -r`
`head`   `head -n`
`tail`    `tail -n`
`|`
`cut` `cut -d` `cut -f`
`uniq`   `uniq -c`
`pipes and filters`

### [[44 Loops]]
`for do done`
`nested loop`
`iteration`

### [[55 Shell Scripts]]
`file.sh`
`using simple text editor`
`bash`
`$1 $2 $3`   `"$1" "$2" "$3"` 
`$@`  `"$@"`
`#comments`

### [[14 grep]]
`grep`      `grep [pattern] [file]`
`grep -w " " []`
`grep -n -w -i`
`grep -n -w -v`
`grep -r `
`regular expressions`   `^ .`
[regular expression](https://librarycarpentry.org/lc-data-intro/01-regular-expressions.html)

`find .`
`find . -type d  []`
`find . -name []`
`$([command])`


[[bash-commands]]


> 3
> **Common Shell Commands**, **Executing Multiple Commands**, and **Tab Completion** sections

> 3.1 
> **Command-Line Editing**, **Redirection**, **Pipes**, **Tilde Expansion**, and **Brace Expansion**:




- **Introduction to Bash**: Mention the difference between interactive and non-interactive shells, explain why Bash is so popular.
    
- **Basic Commands**: Include how to check the manual pages (`man command`), and give an example of a commonly used command like `ls` with options (e.g., `ls -l` for long listing).
    
- **File System Navigation**: Ensure you mention relative vs absolute paths, how to navigate between directories with `cd`, and the special directories like `.` (current directory) and `..` (parent directory).
    
- **Input and Output Redirection**: Apart from basic redirection (`>`, `>>`, `<`), include examples of redirecting both stdout and stderr (`2>&1`), and explain `tee` for splitting output.
    
- **Piping**: Ensure you cover the concept of piping and chaining multiple commands together (e.g., `ps aux | grep process_name`).
    
- **Process Management**: Include handling background processes, `bg`, `fg`, `kill`, and `jobs`. Describe how to find process IDs (`ps`, `top`, `pgrep`).
    
- **Environment Variables**: Explain the difference between user and system environment variables, how to set and export variables, and how to use `env` and `printenv`.
    
- **Shell Scripting Basics**: Ensure you cover basic scripting structure, shebang (`#!/bin/bash`), and running scripts with execution permissions.
    
- **Advanced Scripting Techniques**: Explain loops (`for`, `while`), conditional statements (`if`, `case`), functions, and arrays.
    
- **Scripting Best Practices**: Discuss comments, indentation, using `set -e` to stop on errors, and modular scripts.
    
- **Troubleshooting**: Mention common errors, debugging strategies like `set -x`, and using `echo` for output.
