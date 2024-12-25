
Linux provides several forms of support. The most used one being man(manual) page.

## `man` Pages

`man` expects the name of the Linux command as its argument
It displays the `manual page` for that command called `man page` for short.

it is displayed within the `vi` editor without the editing option (view/search only mode).

Man page will contain section for 
Name, Synopsis, Description, Options, Configuration file, Exit code, Files, Other man pages to consult.

## Other Command line help

`rmdir --help`

also just the `help` command

using `whatis` to get brief description
```bash
sujith@sujith-Latitude-7490:~$ whatis ls pwd rm rmdir mkdir touch echo
ls (1)               - list directory contents
pwd (1)              - print name of current/working directory
rm (1)               - remove files or directories
rmdir (1)            - remove empty directories
rmdir (2)            - delete a directory
mkdir (1)            - make directories
mkdir (2)            - create a directory
touch (1)            - change file timestamps
echo (1)             - display a line of text
```

`whatis` also has options `-w` for wildcards

```bash
sujith@sujith-Latitude-7490:~$ whatis -w mkd*
mkdir (1)            - make directories
mkdir (2)            - create a directory
mkdirat (2)          - create a directory
mkdosfs (8)          - create an MS-DOS FAT filesystem
mkdtemp (3)          - create a unique temporary directory
```


## Searching in `/user/bin`
to see all the commands available


## using `apropos`
To find a command using its description.
It takes in a string as argument and searches for all the command that has it as the description.
`apropos delete`    `apropos delete directory`  these might search for specific words.

by using `" "` we can reduce to specific sentences. but might not find exact match.
`apropos "remove directory"`

Using the regular expression notation `.*` to indicate "match anything".
`apropos "remove .* directory"`
`apropos "delete .* directory"`
to match even if anything comes between these so gives a specific command.

```bash
sujith@sujith-Latitude-7490:~$ apropos "virtual memory"; apropos "delete .* directory"; apropos "virtual memory"
mremap (2)           - remap a virtual memory address
proc_sys_vm (5)      - virtual memory subsystem
proc_vmstat (5)      - virtual memory statistics
tmpfs (5)            - a virtual memory filesystem
vmstat (8)           - Report virtual memory statistics
rmdir (2)            - delete a directory
mremap (2)           - remap a virtual memory address
proc_sys_vm (5)      - virtual memory subsystem
proc_vmstat (5)      - virtual memory statistics
tmpfs (5)            - a virtual memory filesystem
vmstat (8)           - Report virtual memory statistics

sujith@sujith-Latitude-7490:~$ apropos "user account"
userdel (8)          - delete a user account and related files
usermod (8)          - modify a user account
```

