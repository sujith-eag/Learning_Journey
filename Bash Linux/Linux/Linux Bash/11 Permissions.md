
Permissions are a mechanism to support operating system protection.
Permissions proscribe what access rights a user has to a file or directory.

`protections` ensure that the users do not misuse system resources (CPU, memory, network)
Since user mainly interacts with files, the resources that we protect with permissions are files and directories.

Many operating systems implement file permissions through Access Control Lists (ACLs).
An ACL is attached to a specific file and consists of the list of user and groups that can access the resource. They can be lengthy depending on number of users.

Each user / group has access rights to the file.
Owner might have Read, Write, Execute access and it may vary for others.

Linux provides a shorter version of permissions, establishing access rights for three categories:
(`u`)owner,  (`g`)members of group that owns the item and then (`o`) all other users also called world..


***The Access rights:***
r (read)  File can be viewed, copied, or opened as read only
	Directory contents can be viewed by `ls`

w (write) File can be overwritten (modified)
	Files can be written in directory; File can be deleted from here.

x (execute) File can be executed (needed for programs, shell scripts)
	User can `cd` into this directory



### Altering Permissions from the Command line

#### `chmod` 
is the command to change the permission of a file.
`chmod permissions file(s)` the `file` is one or more files / directories, using space or wildcards.
`permissions` are specified using one of three different approaches.

### First:  `+ -`
specifying permissions is ti describe the changes to be applied as a combination of `u, g, o` along with `r, w, x`.
To add a permission use `+` and `-` to remove.

Currently readable and writable by `u` and `g`
and readable by `o`
`chmod g-w,o-r file.txt`
To remove writable of `g` and remove readable by `o`.
There are no spaces within the permissions.

To add execute to owners and group,
`chmode u+x,g+x file.txt`

Permissions can be changed to all by by using an `a`  instead of listing all.
To give execute permission to all
`chmod a+x file.txt`

### Second:
Second approach is to use `=` instead of `+ -`
We assign new permissions rather than changing existing ones to `u, g, o`

`chmod u=rwx,g=r,o= file.txt`
All permissions to owner, readable for group and no permissions for other(world).

Not including a category will not change the permission of that.
`chmod g=,o= file.txt` will not omitting `u=` means we are not changing anything for owner.

We can combine `=` with `+ -` to assign permission to one and remove add permission to another.

All commands doing the same thing using combinations of the two approach.
```bash
chmod u=rwx,g-w,o-r file
chmod u=rwx,g-w,o= file
chmod u+x,g=r,o-r file
chmod u+x,g-w,o= file
```

#### Third:
Is to specify the full permissions for each of `u, g, o` expressing the permissions as a 3-digit number.
This is more complicated as we need to figure out the right number.
Each digit of the 3 digit number represents the permissions for one of each group.

The digit is computed by adding `4 for r`, `2 for w` and `1 for x` access.
read + write access is 4 + 2 = 6
read + execute is 4 + 1 = 5
read + write + execute is 4 + 2 + 1 = 7

So a file needing `r,w,e` for `u` , `r,e` for `g` and nothing for `o`, then the three digit number is 750.
`chmod number file(s)`


`7 5 1` is `rwx r-x --x`
rewriting these 9 permissions to binary gives `111101001`
`111 101 001` which are the numbers we get by separating them out and,
`7 5 1` are the decimal equivalent of these binary numbers.

`----- 000    --x--x--x  111`
`r----- 400` Many more combinations

[table of 3 digit permission meaning]

___

### Changing group and owner

Root can change any items owner and/or group.
non-root user can only change owned file's group as long as we are a member of the group we are assigning the file to.

`chown` and `chgrp` are commands to change the owner and group.
`chown` can be used to change both owner and group.

```bash
chown newowner file(s)
chown newowner:newgroup file(s)

chgrp newgroup file(s)
```

```bash
chown fox/home/foxr/*.txt
chown www:www /user/local/apache/htdocs/*

chgrp citg /home/fox/citg/project-data.txt
```



___


### Altering permissions from the GUI

File Browser allows viewing file information including permissions.
Right click and select the permissions.


___

### Advanced Permissions

There are three other types of permissions to explore.
One of these is SELinux, which utilizes far more complex scheme than `ugo/rwx` mechanism.

Another deals with the user ID bit and the Group ID bit. This influences how the process will execute, it is reserved for executable files only.

Last form of permission is known as `sticky bit`.
It applies only to different and indicates that a writable directory has restrictions on the files therein.
.
.
Making a directory `777` would allow anyone to access , delete and alter the files but setting the sticky bit makes these only possible by the owner of the file, not anyone else.
