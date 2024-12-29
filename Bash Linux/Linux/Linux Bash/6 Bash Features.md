

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

***Writing to a file / Capturing Output from Command***

`cat *.txt > newfile.txt`  making a new file from all the text files in directory. `newfile` if existed will be re-written.

`cat *.txt >> newfile.txt` same as above but appends if `newfile` existed.

`cat < *.txt`  or `cat *.txt`  there is not any difference as `cat` gets takes file as argument.

`cat << quit`  Accepts all input until the user enters `quit <enter>`, sending the input to `cat`
the word can be anything.

`cat << done > fruit.txt`  getting the inputs till done and then putting the input into a file.

`ls -l /home/sujith > user_entries.txt`
`ls -l /home/user >> user_entries.txt`

```bash {frame="none"}
$ wc -l *.pdb > lengths.txt
```
This command reads all `.pdb` files and writes the line counts to `lengths.txt`. If the file doesn't exist, it will be created; if it does exist, it will be overwritten, so caution is advised.

```bash {frame="none"}
$ head -n 3 animal.csv > animals-subset.csv
# Creates the file for the first 3 lines

$ tail -n 2 animals.csv >> animals-subset.csv  
# Appends the last 2 lines
```


***Pipes***

Pipes for Passing Output to Another Command.
The pipe operator `|` allows you to pass the output of one command as input to another command:

```bash {frame="none"}
$ sort -n lengths.txt | head -n 1
```
This command sorts `lengths.txt` and then retrieves the first line (smallest value).

You can chain multiple commands together:
Piping removes the need for other files to hold values.

we can pass `wc` values directly to `sort` and then send resulting output to `head`.

```bash {frame="none"}
$ wc -l *.pdb | sort -n | head -n 1  
# Gets the shortest .pdb file
```

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

____

## History list

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