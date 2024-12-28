
Mechanisms to search through Linux file space for particular files or directories that match some criteria.

### File Browser
Has a search bar, typing the string of what we are searching for.
It also has a drop down menu to select date, type of item. Last modified.
If full text is used, the search examines the search string against both filename and contents found within the file, works for text files only.


### `find` command

The `find` command is used to locate files and directories based on specific criteria. Complicated yet powerful.

`find directory options` 
where directory is the starting place where the search should begin.

***Basic Usage***
To find and list all files and directories under the current directory:
```bash {frame="none"}
$ find .
```

***Filtering by Type***
- **Directories (`-type d`)**: Lists only directories.
```bash {frame="none"}
$ find . -type d
```
- **Files (`-type f`)**: Lists only files.
```bash {frame="none"}
$ find . -type f
```


***Finding by name***
Simplest form of find is to find a file whose name matches the given string.We can use wildcards also.
`-name` option followed by the `"string"`.

```bash {frame="none"}
$ find . -name *.txt
# this finds files by only in current directory because,
```
the `*` got expanded before execution of command so what actually got executed was,
```bash {frame="none"}
$ find . -name numbers.txt
```
So only that got listed.    
Putting it in quotes will solve this issue.
```bash {frame="none"}
$ find . -name "*.txt"
```
now `find` will get all `.txt` files in all directories.

**Note**: Enclose the pattern in quotes to prevent shell expansion of `*`. Otherwise, it will only search for files named literally `*.txt`.

```bash
find /etc -name "*.conf"
```
 to locate files ending in `.conf` in the `/etc` directory.

`-iname` is a case sensitive version of the same search.

the above command is similar to the `ls /etc/*.conf` but `ls` will not search all the sub-directories. `-R` recursive search can be added to make it similar.
(But did not work recursively)


### Using Command Substitution
You can combine commands using `$()` to insert the output of one command into another. For example, to count lines in all `.txt` files:
```bash {frame="none"}
$ wc -l $(find . -name "*.txt")
```
`$([command])` inserts a command's output in place.     
So the shell first executes what is inside the ( ) and does rest later.

### Example
To count lines in all `.dat` files and sort the results numerically:
```bash {frame="none"}
$ wc -l $(find . -name "*.dat") | sort -n
```
This command finds all `.dat` files, counts their lines, and sorts the results.



____

There are three categories of options
1. search criteria: which `-name` and `-iname` are part
2. options are kind of Linux instructions that alter `find`'s behavior.
3. actions: which control what should happen when it has located an item.


***The search criteria options***
Most but not all search expression require a parameter.
`n` indicates an integer (time, size or `UID/GID`)
`file` indicates filename.
`test` indicates a set of permissions
`type` represents file type or file system type.
`name` is user or group name
`pattern` is regular expression.


#### Time based options
#### `-amin [+-]n`
`find -amin [+-]n` Find all files accessed >, < or =n minutes ago.
(using `-5` finds all files modified within the last 5 minutes )
(`+5` searches for everything before 5 minutes,)
#### `-cmin [+-]n`
`find -cmin [+-]n` Find all files with a status change >, < or =n minutes ago.
`find -cmin 60`
#### `-mmin [+-]n`
Find all files last modified > < =n minutes ago. `-mmin -100`


#### `-atime [+-]n`
Find all files accessed >, < or =n days ago
#### `-ctime [+-]n`
`find -ctime [+-]n` Find all files with a status change >, < or =n days ago.
#### `-mtime [+-]n`
Find all files last modified > < =n days ago. `-mtime 1`  (Useful)


#### `-newer file`
Find all files modified more recently than file.
#### `-anewer file`  
Find all files accessed more recently than file. (Didn't work as expected)
#### `-cnewer file` 
Find all files with a status change more recently than file.
`-cnewer abc.txt`


#### Type or kind based options
#### `-empty`
Find all empty files and directories. (very useful)
#### `-executable` `-readable` `-writable`
Find all files that are readable, writable and executable.
#### `-perm test`
Find files whose permission matches `test` (`test` is a set of permissions)
`-perm 755`
#### `-fstype type`
Find all files on a file system of the `type`    `-fstype nfs`  
(did not work for `pdf`, might mean something else)


#### `-regex pattern`
Find all fines whose name matches the regular expression in pattern.
`-regex [abc]+\.txt`
#### `-size [+-]n`
Find all files whose size is > < = n.
n can be followed by b (512-byte blocks), c (byte), w (2-word bytes), 
k (kilobytes), M (megabytes) and G (Gigabytes)
`-size +1024c`  `-size +1k`
`-size 1000c` means exactly 1000 bytes in size.
`-size -1000c` means less than 1000 bytes in size.
#### `-type type`
Find all files of type where `type` is one of b (block), c (character), `d` (directory),
p (pipe), f (regular file), `l`(symbolic link), s (socket)


`-uid n` `-gid n`  Find all files owned by user ID n or group ID n.
`-user name`  `-group name` 


____

`[+-]n` for time and size, if the number is by itself then it tries to find an exact match.
If the integer is preceded by `+` then `find` looks for matches where the property is greater than the integer.
`-n` looks for property values less than n.

____

#### and or not

Search criteria can be combined using `-and` `-a` to represent ANDed criteria.
`-or` `-o` represents ORed conditions.
If there are multiple conditions, find assumes it is ANDed together by default.

Trying to find a file of size between 100 and 200 bytes in user's home directory (`~`)
All do the same thing
```bash
find ~ -size +100c -size -200c
find ~ -size +100c -a -200c
find ~ -size +100c -and -size -200c
```

```bash
find ~ -uid 1000 -o -gid 1000
```

Negating a condition where we want to find all files where the condition is `not true` using `-not  !`
```bash
find /dev ! -type c
find /dev -not -type c
```
All files that are not character type.

Without parenthesis, not is applied first, followed by and, then or.

.
.
.
.
.
.
.
`-daystart`
`-amin` `atime`
`-mindepth` `-maxdepth`
`-mount`
`-P` for not following symbolic links
`-L` to force to follow symbolic link
`-H`

`-D` for debugging options followed by (`all`, `exec`, `help`, `opt`, `rates`, `search`, `stat`, `tree`)
`-warn` `-nowarn`




### `find` Actions

`-delete`
Delete all files that match
`find ~ -empty -delete`   delete all empty files.

`-exec command \;`
Execute `command` on all files found.
`find ~ -type f -exec wc -l {} \;`
Execute `wc` on each file of type f(regular file)

`-ok command \;`
Same as `exec` except that `find` pauses before executing the command on each matching file to ask for permission.
`find / -perm 777 -ok`
	    `chmod 755 {} \;`
Ask permission and change permission to `755`

`-ls` `-print`
Output found items using the command `ls -dils` or by full file name respectively.
`find ~ -name *core* -print`

`-printf format`
Same as `print` except we provide formatting specifiers to output such info.
`find ~ -size +10000c -printf %b`
Outputs size on disk block of all files greater than 10,000 bytes.

`-prune`
If a found item is a directory, do not descend into it
`find ~ -perm 755 -prune`

`-quit`
If a match is found, exit immediately.
`find ~ -name *core* -quit`





### Other means of locating files

`which name`
to find an executable file `name` which is present in `PATH` variable directories.

`whereis` 
is similar as it outputs programs location. but not reliant on the `PATH`
```bash
sujith@sujith-Latitude-7490:~$ whereis man
man: /usr/bin/man /usr/local/man /usr/share/man /usr/share/man/man1/man.1.gz /usr/share/man/man7/man.7.gz
```

`locate`
Is a search program which accesses a database storing file locations.
Before using it , data base must be updated and created using `updatedb`.


