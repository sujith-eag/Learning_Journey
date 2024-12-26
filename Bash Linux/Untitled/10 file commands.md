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

`pwd` `cd`
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

#### Directory commands

`pwd`  `-L`

If there are different directories that we wish to visit often, we might place them onto the `directory stack`.
`dirs` displays all the directories on the directory stack.

`pushd dirname`   To add a directory on the stack
`popd` to remove from top of the stack


___

#### File Movement and Copy Command

Moving(`mv`), renaming(`mv`), copying(`cp`), creating, deleting(`rm`) files and directories.

### `mv`
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
We are not allowed to rename multiple files using single `mv` command as it has only a single `destination` parameter.
`mv *.txt *.dat` will cause error because `*.dat` means multiple destination but has to be a single directory or file name.

`-i` and `-f` are interactive and force mode.
The difference happens only when the file being moved, there is another of same name.
If not interactive, destination file is overwritten.

### `cp`
The format is same as `mv`
`cp [options] source destination`

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


### `rm`

Remove is the delete command.
`rm [options] file(s)`
It can work on multiple files by listing, wildcards or both.

`rm` permanently deletes the files so better to use `-i`, it pauses each deletion and asks for permission.  The alias for `rm` can be `rm -i`
If too many are being deleted and a way to override the prompting messages is `-f` but this can be dangerous `rm -f *.txt`

`-r` again works on the directory and the subdirectories and their files.
To delete a complete sub hierarchy and overriding the prompts. `rm -fr *` which deletes everything in the current current directory.

`rm` is for deleting files, there will be error to delete directories.
It deletes directories only when it is recursive delete `rm -r`

`rmdir` is the only way to delete a directory. it has to be empty.
`rmdir -p` for recursively deleting parent as well as current directories.

### `mkdir` 

Used to make a directory, in current directory or specified path.
`-m` `--mode` we can specify the initial permissions of the directory to override the default permissions.
`-z` `--context` we can specify `SELinux` (security enhanced) context.



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
To view only few lines of the file, not the whole file, `head` and `tail` are used.
By default both display the first ten or last ten lines of a file. `-c -n` both expect integer number to follow the option.
`-c` is used to specify the number of bytes (characters) to output.
`-n` specifies the number of lines to output.

for `head` we can precede the integer with a minus sign to indicate that the program should skip that number of bytes or lines.
for `tail`, precede the integer with plus to indicate the starting point within the file.

`head -n -3 file` output all but last three lines of file.
`head -c -20 file` would stop at the 21st byte of the file.
`tail -n 5 file` output last five lines of the file.
`tail -n +12 file` will display the file starting from line 12.


#### `sort`
Is another file operation to sort line by line in increasing order.
`-r` to sort in decreasing order.
`-f` which causes sort to ignore cases so `a` and `A` are treated equally.
It can work on multiple files in which case the lines are mixed as if the files are combined using `cat`.



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
is used to remove portions of each line of a file. to obtain part of a file.

Options are used to indicate which parts of a line to retain, 
based on a number of bytes (`-b first-last`),
specified characters (`-c charlist`)
a deliminator other than tab (`-d 'delimiter'`)
or field numbers (`-f list`) if the line contains individual fields.
Adding `--complement` will reverse the option so that only the cut portion is returned.

To get the three (fields)columns of data within a table which are delimited by tab
`cut -f 3,4,6 file`
if the delimiter was space then it has to specified using `-d ' '`

We can pipe the results of other command to reduce the output.

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



#### `wc`
word count outputs the count of characters (bytes), words (whitespace between characters) , and lines (`\n`) in a text file.
`-c` `-m` limits count to characters
`-l` line count
`-w` word count
They can be combined.
`-L` prints the length of the longest line.

Command output can be piped to `wc` to count the number of result.
`ls -l | wc -l`


#### `touch`

is mainly for modifying the last access / modification time stamp of a file.
If the file does not exist, an empty text file is created.
`-a` to  modify the last access time and date to current time
`-m` to modify last modification and time and date to current time

`-t` allows to specify new access and modification date and time.
format will be `[[CC]YY]MMDDhhmm[.ss]`


