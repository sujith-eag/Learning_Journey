
Permissions are a mechanism to support operating system protection.
Permissions proscribe what access rights a user has to a file or directory.

`protections` ensure that the users do not misuse system resources (CPU, memory, network)
Since user mainly interacts with files, the resources that we protect with permissions are files and directories.

Many operating systems implement file permissions through Access Control Lists (ACLs).
An ACL is attached to a specific file and consists of the list of user and groups that can access the resource. They can be lengthy depending on number of users.

Each user / group has access rights to the file.
Owner might have Read, Write, Execute access and it may vary for others.

Linux provides a shorter version of permissions, establishing access rights for three categories:
(`u`)owner,  (`g`)members of group that owns the item and then (`o`) all other users.


***The Access rights:***
r (read)  File can be viewed, copied, or opened as read only
	Directory contents can be viewed by `ls`

w (write) File can be overwritten (modified)
	Files can be written in directory; File can be deleted from here.

x (execute) File can be executed (needed for programs, shell scripts)
	User can `cd` into this directory



### Altering Permissions from the Command line

`chmod` is the command to change the permission of a file.

`chmod permissions file(s)` where permissions are specified using one of three different approaches.