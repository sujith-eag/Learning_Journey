
#### File commands

Many of the file commands can operate on many different types of items because Linux treats them all as files. The list of file types is:
Regular files, directories, symbolic links, names pipes, domain sockets, character and block devices.


##### `file` 
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

`head` display the first part of a file
`tail` display end of a file
`-n # (number of lines)`   `-c # (number of bytes)`

`find` locates file(s)

`cmp` compare files
`-i (ignore case)`  `-E (ignore tabs)`  `-Z (ignore trailing space)`  `-b (white space)`  `-B (blank lines)`

`cut` remove portions of each line of a file.
`-b  -c  -d  -f`  (control which portion of the file to cut)

`wc` word counter
`-c  -w  -l`  (output bytes/char, words, lines of the file)

`touch`  Updates the file's last access/modification date but also create an empty text file.
`-a  -m`  (Update the access time, modification time)


____

### Directory commands


[*pwd*](/personal-site/docs/bash-linux/command-docs/pwd) - Print Working Directory

**`pwd`** shows the current working directory (where you are).  
Example: `/Users/sujith` indicates the user directory.
`pwd -L`

`~`  tilde character at the start of a path mean **the current users home directory**
Example: `~/data` refers to `/Users/sujith/data`, useful for absolute path typing.

(Using `pwd` to see the route of a directory and typing that absolute path to wherever we want to go)  


________

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

