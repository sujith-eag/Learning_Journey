



### [*ls*](/personal-site/docs/bash-linux/command-docs/ls-list) - Listing Files and Directories

**`ls`** lists files and directories in the current directory.  

```bash {frame="none"}
ls ~/Desktop/trial
# Using absolute path

ls /Users/sujith/Desktop/trial
# Another way using absolute path

ls -F Desktop
# List contents of Desktop directory
```

```bash
sujith@sujith-Latitude-7490:~$ ls ./ Desktop/ Documents/ Downloads/
./:
Desktop    Downloads  Music     Public  snap       Videos
Documents  grep.txt   Pictures  repos   Templates

Desktop/:
 courses  'MCA Sem1 Text Books'   obsidian-vaults   Opage   pylab   websites

Documents/:

Downloads/:
 hugoinaction-chapter-02-resources
'Option WorkSheet.pdf'
 pcc-master
'Print Resume.pdf'
 sujith.jpeg
```


(`;` didn't work as intended because all are options, not separate statements)
```bash
sujith@sujith-Latitude-7490:~$ ls .; Desktop/; Documents/; Downloads/;
Desktop    Downloads  Music     Public  snap       Videos
Documents  grep.txt   Pictures  repos   Templates
bash: Desktop/: Is a directory
bash: Documents/: Is a directory
bash: Downloads/: Is a directory
```
`ls -l; ls-a; ls -la;` is separate statements linked.


### Long listing

`ls -l` used for long listing the details of files and directories.
`ls -l file.txt` for details of that file
The file types and permissions are combined together to form 10 characters.
`drwxr-xr-x` 
`-r-xr-xr-x`
the first `d` represents a directory and `-` are files.

```bash
sujith@sujith-Latitude-7490:~/Desktop$ ls -l
total 24
drwxrwxr-x 4 sujith sujith 4096 Sep  3 15:29  courses
drwxr-xr-x 2 sujith sujith 4096 Dec 22 16:11 'MCA Sem1 Text Books'
drwxr-xr-x 4 sujith sujith 4096 Dec 18 19:56  obsidian-vaults
drwxrwxr-x 7 sujith sujith 4096 Oct  6 15:21  Opage
drwxrwxr-x 6 sujith sujith 4096 Dec 24 10:09  pylab
drwxrwxr-x 8 sujith sujith 4096 Oct 26 09:04  websites
-rw-rw-r--  1 sujith sujith   68146 Dec 24 12:43  sujith.jpeg
-rw-rw-r--  1 sujith sujith 2957628 Oct 30 13:52 'Option WorkSheet.pdf'
```

The file types and permissions are combined together to form 10 characters.
`drwxr-xr-x`    `-r-xr-xr-x`  the first `d` represents a directory and `-` are files.

The contents of Long Listing
`File-Type` `Permissions` `Hard links` `User, Group` `size` `Last` `Name`

***File type*** : can be true files, directories, symbolic links, devices and other items `-` `d` 
`l` for symbolic link

***Permissions*** : called *mode*, file's access permissions.
`rw- r-- ---`  owner has read write access, group members have read access, others have no access.
( `.` at end of permissions to indicate the `SELinux` content)

***Hard links*** : Number of hard links that point at this item. Often `1` for files and `2` for directories but can be larger.

***User, Group*** : The user who owns the file and the group that file belongs to. (for most users the group is the user's private group)  `sujith sujith`

***Size*** : Size of objects in bytes. `0` is for empty.

***Last*** : Modification date/time (creation date/time if not modified)

***Name*** : Name of the item.   for a symbolic link, the name is followed by `->` 


Options can be combined in any order:
```bash {frame="none"}
ls -Fal   # combined options
ls -la
ls -al
```


## Other useful options of `ls`

`-a` hidden files and shows `.` current directory and `..` parent directory are also indicated.
`-A` same as `-a` but without the `.` `..`
`-g` same as `-l` but the owner is not shown
`-G` Group owner is hidden (along with `-l`)
`-h` human readable size of long list (along with `-l`)
`-i` `inode` numbers of the files are included
`-r` reverse alphabetical order of file listing
`-R` Recursive listing (listing all contents of all sub directories)
`-s` size shown in blocks instead of bytes (along with `-l`)
`-S` Sort files by size (used with `-l`)
`-t` time based sorting (along with `-l`)
`-X` Extension based sorting  (along with `-l`)
`-1` 1 file per line (not to use columns)
`-C` Columns listing of entries to fir more in a page.




