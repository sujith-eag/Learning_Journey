
#### File commands

Many of the file commands can operate on many different types of items because Linux treats them all as files. The list of file types is:
Regular files, directories, symbolic links, names pipes, domain sockets, character and block devices.

`file` command describes the type of entity passed to the command.
```bash
sujith@sujith-Latitude-7490:~$ file /home/sujith/Downloads/Print\ Resume.pdf 
/home/sujith/Downloads/Print Resume.pdf: PDF document, version 1.4, 1 page(s)

sujith@sujith-Latitude-7490:~$ file /etc/passwd
/etc/passwd: ASCII text

sujith@sujith-Latitude-7490:~$ file -i /etc/passwd
/etc/passwd: text/plain; charset=us-ascii
```

____


***Common file commands***

`pwd` 
`cd`
`ls`   `-a (all)` `-l (long listing)` `-r (reverse)` `-R (recursive)` `-s (sort by size)` 
`-1 (display in one column)`


`mv` Move or rename file(s)/ directory(ies)   
`-f (force)` `-i (interactive)` `-n (do not overwrite existing file)`

`cp` copy files (permission of copied file changes)
	`-r (recursive)`  same as `mv`
	`-b`  Create backup of every destination file
	`-I` `-s`   Create hard/symbolic link rather than physical copy
	`-L`  Follow symbolic links
	`-p`  Preserve ownership, permissions, time stamp etc
	`-u`  copy only if source is newer than the destination or destination missing
	`-v`   Verbose (output each step as it happens)


`rm` Delete files
`-f (force)` `-i (interactive)`  `-r (recursive)`

`mkdir` create a directory
`rmdir` delete a directory

`cat` concatenate files (display to window)
`-n (add line numbers)` `-T (show tabs)`

`less` display file screen by screen
`-c (clear screen first)`  `-f (open non-regular files)`

`more` display file screen by screen
`-num # (specify screen size in #rows)`    `+# (starts at row number #)`

`head`  display the first part of a file
`tail` display end of a file
`-n # (number of lines)`   `-c # (number of bytes)`

`find` locates file(s)
`........`

`cmp` compare files
`-i (ignore case)`  `-E (ignore tabs)`  `-Z (ignore trailing space)`  `-b (white space)`  `-B (blank lines)`

`cut` remove portions of each line of a file.
`-b  -c  -d  -f`  (control which portion of the file to cut)

`wc` word counter
`-c  -w  -l`  (output bytes/char, words, lines of the file)

`touch`  Updates the file's last access/modification date but also create an empty text file.
`-a  -m`  (Update the access time, modification time)


___

#### Creating a Text File Using the Nano Editor

To create a text file with the `nano` editor:

```bash {frame="none"}
nano draft.txt  
# Opens nano for editing
```

Type your content, then save using `Ctrl + O` and exit with `Ctrl + X`. 

*Note:* `nano` is a simple text editor suitable for plain text files. 
For more complex editing, consider `Emacs`, `Vim`, or graphical editors like `Gedit` or `VS Code`. On Windows, alternatives include `Notepad++` or `Notepad`.

#### [*touch*](/personal-site/docs/bash-linux/command-docs/touch)

```bash {frame="none"}
touch my_file.txt  
# Creates a blank text file
```

`touch` is mainly for modifying the last access / modification time stamp of a file.
If the file does not exist, an empty text file is created.
`-a` to  modify the last access time and date to current time
`-m` to modify last modification and time and date to current time

`-t` allows to specify new access and modification date and time.
format will be `[[CC]YY]MMDDhhmm[.ss]`


#### [wc](/personal-site/docs/bash-linux/command-docs/wc-word-count)
word count outputs the count of characters (bytes), words (whitespace between characters) , and lines (`\n`) in a text file.
`-c` `-m` limits count to characters
`-l` line count
`-w` word count
They can be combined.
`-L` prints the length of the longest line.

To get the word count for all `.pdb` files in the current directory:

```bash {frame="none"}
$ wc *.pdb
```
Returns the word count of all `.pdb` files individually and also total.


- `wc -l`  # Shows only the number of lines per file.
- `wc -m`  # Shows the number of characters only.
- `wc -w`  # Shows the number of words only.

If `wc -l` is run without specifying a filename, it waits for input from the command prompt. You can exit this mode using `Ctrl + C`.


Command output can be piped to `wc` to count the number of result.
```bash
$ ls -l | wc -l`
```


#### `strings`
This instruction works on files that are not necessarily text files, outputting printable characters found in the file.
```bash
sujith@sujith-Latitude-7490:~/Downloads$ strings sujith.jpeg -n 10
6*&&*6>424>LDDL_Z_||
6*&&*6>424>LDDL_Z_||
Bm&EmvX{2;
!1 0AQ@Paq
```
It outputs any sequence of four or more printable characters found between the unprintable characters.
`-n number` can over ride the length


### Directory commands

[*cd*](/personal-site/docs/bash-linux/command-docs/cd-change-directory) - Change Directory

- **`cd <name>`** changes the shell's current working directory.   
  Can only move into directories using this command.

- **`cd ~`** navigates to the home directory (e.g., `/home/sujith`).

- **`cd ..`** moves back to the parent directory (the directory containing the current one).  
- **`.`** means the current directory.

- **`cd -`** switches to the previous directory we were in.  
Repeating `cd -` toggles between the current and previous directories.

- **`cd /`** goes to the root directory.  
- **`cd ../..`** goes up two levels (parent of parent).


[*pwd*](/personal-site/docs/bash-linux/command-docs/pwd) - Print Working Directory

**`pwd`** shows the current working directory (where you are).  
Example: `/Users/sujith` indicates the user directory.
`pwd -L`

`~`  tilde character at the start of a path mean **the current users home directory**
Example: `~/data` refers to `/Users/sujith/data`, useful for absolute path typing.

(Using `pwd` to see the route of a directory and typing that absolute path to wherever we want to go)  


____


If there are different directories that we wish to visit often, we might place them onto the `directory stack`.
`dirs` displays all the directories on the directory stack.

`pushd dirname`   To add a directory on the stack
`popd` to remove from top of the stack


___

___

## Naming Conventions

- Avoid spaces; use `_` or `-` instead.
- Do not start names with `-` to prevent confusion with options/flags.
- Stick to characters: `0-9`, `a-z`, `.`, `-`, `_`. Special characters can have different meanings.
- Use single quotes `' '` for names with spaces or special characters.




#### File Movement and Copy Command

Moving(`mv`), renaming(`mv`), copying(`cp`), creating, deleting(`rm`) files and directories.

### [mv](/personal-site/docs/bash-linux/command-docs/mv-move)
Move is used to move / rename both file / directories.
`mv [options] source destination`
To rename a file, `source` is old name and `destination` is new name.
Otherwise both need to be in different directories.
If `destination` is a directory without a file name, then the file's name is not changed.

```bash
mv fo1.txt ~/temp
# moves to temp

mv fo1.txt ~/temp/fo2.txt
# moves and renames

mv *.txt /home/zapp
```
To move file into the current directory, `.` can be used as `destination`

***Renaming Files***
To rename a file or move it to a new location:

```bash {frame="none"}
mv [old] [new]  # Moves or renames a file
```

Examples:
```bash {frame="none"}
mv trial/draft.txt trial/quotes.txt  
# Renames draft.txt to quotes.txt

mv draft.txt quotes.txt
# While in Same directory rename
```

*Note:* Moving a file to a directory with the same name will silently overwrite the original. Use `mv -i` to prompt for confirmation.

To move files to a different directory:
```bash {frame="none"}
mv trial/quotes.txt .  
# Moves to the current directory

mv sucrose.dat maltase.dat ../raw  
# Moves files to the parent directory's raw folder
```


We are not allowed to rename multiple files using single `mv` command as it has only a single `destination` parameter.
`mv *.txt *.dat` will cause error because `*.dat` means multiple destination but has to be a single directory or file name.

`-i` and `-f` are interactive and force mode.
The difference happens only when the file being moved, there is another of same name.
If not interactive, destination file is overwritten.

### [cp](/personal-site/docs/bash-linux/command-docs/cp-copy)

The format is same as `mv`,    `cp [options] source destination`

```bash {frame="none"}
cp [old] [new]  # Copies a file

cp quotes.txt thesis/quotation.txt  
# Copies to a new location
```

There are three different combination that can be used:
Destination is another directory, then file name remains same after copy.
Destination is directory and a file name, then file is copied with a new name.
Destination is a filename, then file is copied into the current directory with new name.

```bash
cp fo.txt ~zap/fo1.txt
cp *.txt ~
cp ~zapp/foo.txt .
```

`-i` and `-f` use remain the same as `mv`
`-b` Creates backup of every destination file.???
`-I/-s`  Create hard / symbolic link rather than physical copy
`-u`   copy only if source is newer than the destination or destination missing
`-L` if the source is a symbolic link, the link is followed to the actual file and it is copied, not the link.
`-v` copy does not report what sis copied, so adding `-v` outputs each file movement as it takes place.
`-p` When `cp` creates a copy, it's ownership and permissions are updated to that pf the user who issued the command. `-p` preserves the original ownership, permissions and creation/ modification times.
`-r` is recursive copy to which operates on the files and subdirectories of the current directory and also applies to the content of any subdirectories of those subdirectories.

To copy a directory and all its contents, use `-r`:

```bash {frame="none"}
cp -r thesis thesis_backup  

# Copies the entire directory
```


## Operations with Multiple Files and Directories

To copy or move multiple files, list the files followed by the target directory:
If given more than one file names followed by a directory name(directory as last argument)

```bash {frame="none"}
cp file1.txt file2.txt target_directory/  
# Copy multiple files

mv file1.txt file2.txt target_directory/   
# Move multiple files
```

Using wildcards can simplify this process:

```bash {frame="none"}
cp *.txt backup/  # Copies all .txt files to backup/
```

```bash {frame="none"}
$ mkdir backup

$ cp cretures/minotaur.dat creatures/unicorn.dat backup/

$ cp minotaur.dat unicorn.dat basilisk.dat
# all three are file names, makes error, this can be handled by using wildcards.
```


## Wildcards

Wildcards represent unknown characters in commands. 

Common wildcards include:

`*` : Represents zero or more characters.
	`*.pdb` matches all files ending with `.pdb`.
    `*ethane.pdb` represents ethane and methane.
	`p*.pdb` matches files starting with `p` and has `.pdb`.
  
`?`: Represents exactly one character.
	`?ethane.pdb` matches only `methane.pdb`.

#### Using Wildcards in Commands

```bash {frame="none"}
ls *t*ane.pdb   
# Lists files with 't' and 'ane' in their names

cp *dataset* backup/datasets  
# Copies all files with 'dataset' in the name

ls *t?ne.*     # gives octane pentane
ls *t??ne.pdb  # ethane methane
ls ethane.*    #only ethane
```

Wildcards can be combined for more specific patterns:
```bash {frame="none"}
ls ???ane.pdb  

# Matches any three characters followed by 'ane.pdb'
```
When a shell sees a wildcard it expands the wildcard to create a list of matching filenames before running the preceding command.

*Note:* Be cautious; using wildcards can result in errors if not handled properly.
(e.g., `*.pdf` in a directory with `.pdb` files).


### Using wildcards for copying
```bash {frame="none"}
$ cp *dataset* backup/datasets
# copy anything having dataset as name to datasets directory inside backups

$ cp *calibration.txt backup/calibration
# copying all calibration files

$ cp 2015-11-* send_to_bob/all_november_files/
# copying just November files

$ cp *-23-dataset* send_to_bob/all_datasets_created_on_23rd/
# just 23rd files
```






#### [*rm*](/personal-site/docs/bash-linux/command-docs/rm-remove)
Remove is the delete command.
`rm [options] file(s)`
It can work on multiple files by listing, wildcards or both.

```bash {frame="none"}
rm my_file.txt  
# Deletes the specified file
```

Use `rm -i` to prompt for confirmation before deletion.
`rm` permanently deletes the files so better to use `-i`, it pauses each deletion and asks for permission.  The alias for `rm` can be `rm -i`
If too many are being deleted and a way to override the prompting messages is `-f` but this can be dangerous `rm -f *.txt`


`rm` cannot remove directories directly. To remove a directory and its contents, use the recursive `-r` option:
`-r` recursively works on the directory and the subdirectories and their files.
```bash {frame="none"}
rm -r directory_name  
# Deletes the directory and all its contents
```
To delete a complete sub hierarchy and overriding the prompts. `rm -fr *` which deletes everything in the current current directory.

- To remove files matching a pattern (e.g., all `.txt` files) with confirmation:

```bash {frame="none"}
rm -i *.txt  # Prompts for each .txt file
```

*Note:* Shell does not have a trash bin; deleted files are permanently removed.



`rmdir` is the only way to delete a directory. it has to be empty.
`rmdir -p` for recursively deleting parent as well as current directories.



## [*mkdir*](/personal-site/docs/bash-linux/command-docs/mkdir) Creating Directories

Used to make a directory, in current directory or specified path.
`-m` `--mode` we can specify the initial permissions of the directory to override the default permissions.
`-z` `--context` we can specify `SELinux` (security enhanced) context.

```bash {frame="none"}
mkdir [name]  # Make directory
```

`-p` option is used to make Multiple directories.

```bash {frame="none"}
mkdir -p [path/to/nested/directories]  
# Creates nested directories

mkdir -p ../project/data ../project/results
```
`ls -R` to list all nested sub directories within a directories.


To create multiple directories at once:
```bash {frame="none"}
mkdir north south pacific  

# Creates three separate directories
```


#### Example:
To create a directory `2016` with a sub-directory `data` that contains two directories, `processed` and `raw`:

#### Method 1: Step-by-Step Creation
```bash {frame="none"}
mkdir 2016
mkdir 2016/data
mkdir 2016/data/processed
mkdir 2016/data/raw
```

#### Method 2: Navigating and Creating
```bash {frame="none"}
mkdir 2016
cd 2016
mkdir data
cd data
mkdir processed raw
```

#### Method 3: Using `-p`
```bash {frame="none"}
mkdir -p 2016/data/{processed,raw}  

# Creates the full structure in one command
```





___
___

### Text file Viewing Commands

`cat` is one which shows only the last screen worth of data.
`less` and `more` let us step through the file, screen by screen.

#### `more`
it displays a screen's worth of content and pauses. Waits for user to press `<space>` which moves forward by one screen or `<enter>` which moves by one line.
`q` exits to command prompt. Or when end of file is reached.
`-n` is used specify the number of lines that appear in each screen
`+linenumber` to start the display at the given line number.


#### `less`
is more useful as it gives more control to step through the file.
Scrolling is possible with arrow keys. It loads in a `vi`like browser so movement can also by using `vi` commands.
Reaching the end of file will not exit, `q` will exit to command prompt.

#### `head` `tail`
[*head and tail*](/personal-site/docs/bash-linux/command-docs/head-tail)  to view only few lines of the file, not the whole file, `head` and `tail` are used.
By default both display the first ten or last ten lines of a file. 

`-c -n` both expect integer number to follow the option.
`-c` is used to specify the number of bytes (characters) to output.
`-n` specifies the number of lines to output.

for `head` we can precede the integer with a minus sign to indicate that the program should skip that number of bytes or lines.
for `tail`, precede the integer with plus to indicate the starting point within the file.

`head -n -3 file` output all but last three lines of file.
`head -c -20 file` would stop at the 21st byte of the file.
`tail -n 5 file` output last five lines of the file.
`tail -n +12 file` will display the file starting from line 12.


#### [*sort*](/personal-site/docs/bash-linux/command-docs/sort)
The `sort` command sorts lines of text files / output:
Is another file operation to sort line by line in increasing order.
`-r` to sort in decreasing order.
`-f` which causes sort to ignore cases so `a` and `A` are treated equally.
It can work on multiple files in which case the lines are mixed as if the files are combined using `cat`.

```bash {frame="none"}
$ sort lengths.txt  # Sorts alphanumerically by default
sort -n             # Sorts numerically
sort -r             # Sorts in reverse order
```

`$ sort -n lengths.txt` doesn't change the file, but sends results to screen.

To sort and redirect the results to a new file:
```bash {frame="none"}
$ sort -n lengths.txt > sorted-lengths.txt
```


____

### File Comparison Commands

#### `cmp` 
receives two files as parameter and compares them byte by byte, line by line. It stops as soon as it finds a mismatch, returning the byte and line of difference.
`cmp` can be forced to skip over a specified number of bytes for each file or stop after reaching a specified limit. If no mismatch then no output.

`cmp file1 file2 -i 100:150 -n 1024`
compares files one and two, starting at 101 of file 1 and 151 of file 2. Comparing 1024 bytes.

The default counting used with `cmp -i` (`--ignore-initial`) is a value in bytes (characters)


#### `comm`
receives two files which are expected to be sorted.
It might work even if the content is not sorted but will not give proper result.

`comm` instruction works through the two files, comparing line by line and returning each line whether content appeared in the first file, second file or both files.
Output is organized into three columns.
Column 1 has lines appearing only in the first file
Column 2 features lines common to both files.
Column 3 features lines only appearing in the second file.

Options are limited, `-1 -2 -3` which are used to output only lines unique to first file, second file and those in both.

#### `diff`
Can operate on two files, a file and a directory or two directories.
Depending on the type of parameter `diff` works differently.

For two files, compares line by line reporting every mismatch.
The output is somewhat cryptic.
`-i` can be used to make it case insensitive.
`-E` to ignore spacing (tabs)
`-Z` to ignore trailing spaces.
`-b` to ignore difference in white space
`-w` to ignore all white space
`-B` to ignore blank lines.
`-y` to make output into columns

When comparing two directories, `diff` first compares the file names to see if a file exists in one directory which does not exist in another and outputs that. To show some file exist only in one directory.
If there are files with similar names, then `diff` compares them as before.

If comparing a file and directory, it searches for the file name in the directory and compares if found.

`diff` can also compare one file to several other files using `--from-file=` or `--to-file=`


#### `uniq`
It operates on a single file, searching for consecutive duplicate lines.
Parameters can be used to remove duplicate lines.
It does not overwrite the file but the output can be can be moved to a new file.
`uniqu file.txt > filewitoutduplication.txt`

It only compares adjacent lines, it would not find duplicates lines if they do not appear consecutively.



___


### File Manipulation Commands


#### `join`
is used to join two sorted files together when the files contain a common value (field) per line.
When the two files contain a row that contains that same value, then those two lines are joined together. Lines that do not contain a matching first field are not joined.
(Joining tables using a matching keys)

`-1 NUM` and `-2 NUM` allow us to specify which fields should be used on the first and second files respectively where `NUM` is the field number desired. The default is 1.

`-i` causes `join` to ignore case if the common value includes letters.
`-e` uses `STRING` in place of an empty field 
`-a 1` or `-a 2` outputs lines from the first or second file which did not contain a match to the other file.


#### `paste`
is another way of merging files.
The contents of the files are combined line by line. First line is appended to first line of other file.
it is similar to `join` but there is no need for a common field values.


#### `split`
allows to split a file into numerous smaller files.
We specify the file to split and a `prefix` which is name used for new files.

By default `split` will place 1000 bytes in each new file.
`-b value` where value is number of bytes per file.
`-d` causes `split` to a name the new files using digits `00, 01, 02` instead of letters as the extensions to the prefix.


#### `cut`

The `cut` command is used to remove or extract specific sections of each line in a file:

Options are used to indicate which parts of a line to retain, 
based on a number of bytes (`-b first-last`),
specified characters (`-c charlist`)
a deliminator other than tab (`-d 'delimiter'`)
or field numbers (`-f list`) if the line contains individual fields.
Adding `--complement` will reverse the option so that only the cut portion is returned.

```bash {frame="none"}
$ cut -d , -f 2 animals.csv
```
- `-d ,` specifies the delimiter (in this case, a comma).
- `-f` specifies the field (column) to extract.


To get the three (fields)columns of data within a table which are delimited by tab
```bash
cut -f 3,4,6 file
```
if the delimiter was space then it has to specified using `-d ' '`

We can pipe the results of other command to reduce the output.

To remove duplicates from the output, you can pipe `cut` into `sort` and `uniq`:

```bash {frame="none"}
$ cut -d , -f 2 animals.csv | sort | uniq
```
Removing the duplicates using `uniq`
Using `uniq -c` gives the count of occurrences for each line in input.


`ls -l | cut -c 2-10`  outputs only the permissions of the files which starts from 2nd character to 10th.

```bash
sujith@sujith-Latitude-7490:~/Desktop$ ls -l | cut -c 2-10
otal 56
rw-rw-r--
rwxrwxr-x
rw-rw-r--
rwxr-xr-x
rwxr-xr-x
rwxrwxr-x
rwxrwxr-x
rwxrwxr-x
```

 To get the permissions and the file name (getting the first 2-10 chars and also the 9th field where the names are present, with delimiter being space.)
 `ls -l | cut -f 1,9 -d ' '`   won't work properly due to unevenness. 

(`awk` offers better solution that cut for selecting fields)


_____


#### Example Workflow
```bash {frame="none"}
$ cd nart-pacific-gyre
$ wc -l *.txt           # Get the word count of all .txt files
$ wc -l *.txt | sort -n | head -n 5  
# Display the first five line counts

$ wc -l *.txt | sort -n | tail -n 5  
# Display the last five line counts
```
