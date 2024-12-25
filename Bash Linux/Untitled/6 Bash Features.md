
## history list

all entered commands are stored in a history list.
it can be called by typing `history`

`sujith@sujith-Latitude-7490:~/Desktop$ cd Desktop/; history>comm.txt;`
Created a file of commands typed, had thousand commands.

It can store max of 1000 commands and the previous ones are discarded.
The number preceding the command can be used to recall it.

`!` is read as bang, so using `!100` the command at 100 can be recalled.

___

#### Recalling instruction from history list

`!!` recalls and runs the last instruction.

`!n` Recalls and runs the `n` instruction from the list

`!str` to recall the latest instruction that uniquely starts with `str`

Using first, last and all parameters from the last instruction.
`command !^`  issue command but use first parameter / option from last instruction.
`command !$` issue command but use last parameter / option from last instruction.
`command !*` issue command but use all parameter / option from last instruction.

`ls -l !^`  `ls -l !$`  `ls !*`


#### Recalling a Previous Instructions to edit or display

`<up arrow>` or `control+p`  to retrieve last instructions in history

`<up arrow>` or `control+n`  to move forward in history

`!!:p` prints the last instruction from history
`!:2000` prints the instruction `n` from history  (not working)
`!:str` prints the last instruction that starts with `n` from history


#### Options for history command

`history -c`  clear the history list.

`history -d n`  delete `entry n` from the list, causing remaining entries to move up.

`history -r filename` to load the history list saved in `filename` and use it in place of current history list. ( worked but the previous numbers have become part of the commands, and each given new name in history)

`history -w filename` to write history list to a file.

`history -a filename`  to append the current history list to the file

`history -n filename`  
read the file, the lines that are not in the current history list, place them in current history.


______

## Variables and Environment variables

In bash variables can be defined from the command line and used later in the same shell session or from within a script.
All variables are always capitalized.

When a variable is available throughout the environment for use, not just one session or script, it is called as `environment variable` .

`env`
can be used to see all the environment variables defined (which varies along distributions)
```bash
sujith@sujith-Latitude-7490:~/Desktop$ env
SHELL=/bin/bash
SESSION_MANAGER=local/sujith-Latitude-7490:@/tmp/.ICE-unix/1537,unix/sujith-Latitude-7490:/tmp/.ICE-unix/1537
QT_ACCESSIBILITY=1
PWD=/home/sujith/Desktop
LOGNAME=sujith
HOME=/home/sujith
USERNAME=sujith
IM_CONFIG_PHASE=1
LANG=en_US.UTF-8
USER=sujith
GNOME_TERMINAL_SERVICE=:1.132
DISPLAY=:0
SHLVL=1
PATH=/home/sujith/.nvm/versions/node/v20.17.0/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin
GDMSESSION=ubuntu
DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
NVM_BIN=/home/sujith/.nvm/versions/node/v20.17.0/bin
_=/usr/bin/env
OLDPWD=/home/sujith
```

These can be viewed through `echo string` also where `string` is output.
To output the value of a variable `$` should precede the variable name.
```bash
sujith@sujith-Latitude-7490:~/Desktop$ echo $USER; echo $SHELL; echo $PWD; echo $OLDPWD;
sujith
/bin/bash
/home/sujith/Desktop
/home/sujith
```


Some Bash Environment Variables
`DESKTOP_SESSION`  Name of desktop GUI `gnome`
`HISTAG` Size of history list `1000`
`LANG` The specified language and character encoding `en_US.UTF-8`
`MAIL` Location of user's main storage
`OLDPWD` Current working directory prior to this one which is `PWD`
`PATH` List of directories to search to find executable programs
`PS1` defines the user's prompt
`SHELL` User's default shell

`PATH` is an important `env` variable. In Linux commands are implemented as programs which are distributed in various directories. Most are found in `/user/bin  /user/sbin`
```
PATH=/home/sujith/.nvm/versions/node/v20.17.0/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin
```
Without Path variable we will have to specify the location of the command before calling any command.


___

To store a value into a variable, we can use an `assignment statement`.
`VAR=VALUE` with no space between the equal sign.
We may define new or or redefine an existing one. (if known what is being done)
```bash
$ FIRST=Sujith
$ LAST=kumar
$ echo $FIRST $LAST
Sujith Kumar
```

Using `' '` single quotes make the bash interpreter to use the items literally and not apply the `$` to retrieve the value from the variables.
```bash
$ FULL_NAME='$FIRST $LAST'
$ echo $FULL_NAME
$ $FIRST $LAST
```
If there is any blank space in the Value being assigned, then value has to be in `" "`
```bash
$ FULL_NAME="$FIRST $LAST"
$ echo $FULL_NAME
Sujith Kumar
```

> If a command like `pwd` is stored in a variable and called, bash will execute it.


the escape character `\` is used to tell the bash interpreter to treat whatever comes after `\` literally and not to interpret it. `\$$AMOUNT`, the first `$` is escaped.

`$$` has its own meaning which is getting the process ID of the running bash interpreter.


Other escape characters 
`\\`  outputs a `\`,  escaping the escape character
`\b` backspace
`\n` Newline
`\t` tab
`\!  \$  \&  \;  \'  \"`  escaping all the usual symbols used.


_____

## Aliases

alias is used to define an instruction in a shortened form.
Similar to defining a variable, this is also defined using an assignment of a name to a value, but in this case the value is a Linux command.
We an execute the command by by issuing the alias.

To define an alias, after the word `alias` type the assignment statement.
`alias name=command`  the name is the alias.
The name is not as restrictive as for variables, any character can be used.
for the value, if the command contains space, then `" "` has to be used. 
again ` ' '` will make the command to be taken literally, but not executed.

```bash
alias ..="cd .."
alias ~="cd ~"
alias lss=less
alias sl=ls
alias rm='rm -i'
```
`rm` is given in single quotes to input the interactive version.

We can view the pre defined alias by typing `alias` itself
```bash
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -alF'
alias ls='ls --color=auto'
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'
```

Alias can be removed by using `unalias ll` to remove it


___



## Command-Line Editing


Bash interpreter accepts some special keystrokes which perform some function like move, copy, paste.
keystrokes are combinations of control key, escape key or some other key on the board.
These are based on the `emacs` text editor.



when using `control` key it has to be held down and the other key has to be pressed.
with `escape` key it is pressed, released and the other key is pressed.

`ctrl + p` `ctrl + n` were to move up and down in history list. ( up an down arrow) 
`ctrl + a`  `ctrl + e`  moves cursor to beginning of line and to the end of line.

`ctrl + d` or `delete` which deletes the character the cursor is on currently.
`backspace` deleted the character before the cursor.
`ctrl + w` (deletes one word) removes all characters from cursor towards beginning of line, till white space)
`ctrl + k`  kill (delete) everything from the cursor to the end of the line.
`ctrl + u` delete everything from the command line (removes all)

`ctrl + y`  yank all deleted characters (just last one )



`esc + u`  uppercase the word from where the cursor is to blank space 
`esc + l`  lower case the word from where the cursor is to blank space 
`esc + c` capitalize the word ( only first letter)

`ctrl + l`  to clear the screen except the command line



___

## Redirection

`cat` is concatenation command to join files or display content of files.

Writing to a file
`cat *.txt > newfile.txt`  making a new file from all the text files in directory. `newfile` if existed will be re-written.

`cat *.txt >> newfile.txt` same as above but appends if `newfile` existed.

`cat < *.txt`  or `cat *.txt`  there is not any difference as `cat` gets takes file as argument.

`cat << quit`  Accepts all input until the user enters `quit <enter>`, sending the input to `cat`
the word can be anything.

`cat << done > fruit.txt`  getting the inputs till done and then putting the input into a file.

`ls -l /home/sujith > user_entries.txt`
`ls -l /home/user >> user_entries.txt`


***Pipes***
`cat *.txt | sort` takes all `.txt` files and pipes the output to `sort`. So sorts all the contents rather than outputting the file.

`cat *.txt | sort > newfile.txt`  takes input, sorts it, puts it into a file.



**Using tilde**
`~` is replaced by with our home directory. This is known as `tilde expansion`
so it is used in commands to eliminate typing `/home/username/`
`cd ~` takes us to user home directory

`*` is a wildcard that replaces everything found and there are more.
it is termed as `filename` expansion.
`ls -l *.txt`    the `.*txt` is replaced by all the files before execution.

***brace expansion***
We can group the files or sub-directories which share the same path in common and list the files and sub-directories in curly braces `{ }`.
`/directory/{item1,item2}` this expands to
`/directory/item1  /directory/item2`


`ls -l /home/{one,two/{.,stuff},underwood,overwood/{.,lyrics,music}}`
Here the `.` are used to include the current directories also.