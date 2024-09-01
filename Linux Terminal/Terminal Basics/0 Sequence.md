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

### [[4 Loops]]
`for do done`
`nested loop`
`iteration`

### [[5 Shell Scripts]]
`file.sh`
`using simple text editor`
`bash`
`$1 $2 $3`   `"$1" "$2" "$3"` 
`$@`  `"$@"`
`#comments`

### [[6 Finding things]]
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
