
# Bash


A shell is a user interface.

A shell runs an interpreter, which is a program which accepts user input and determines how to execute that input, convert it into executable statements and execute it.

The environment's role is to capture definitions and previous commands of the current session to be recalled by the user to simplify the user's interaction with the computer.

(Thompson shell 1971 -> Mashey Shell -> Bourne Shell 1977 -> C-shell 1978 -> TC-Shell 1983->  Bourne Again Shell (Bash) 1989 )

____

The shell command prompt shows, 
who we are, where we are, where we are and who we are
`sujith`   `@sujith-Latitude-7490`  `~`   `$`
`~` is the home directory of the user
`$` representing it is a normal user account  

`#` would mean root user logged in (using `sudo su`)
`root`   `@sujith-Latitude-7490`  `:home/sujith`  `#`


___

## Simple commands

`cd` `ls` `pwd`
`vi` `emacs` text editors

`who`  logged in users
`whoami` user name
`hostname` computer host name
`uname` Operating system  `uname -o` 
`echo` printing out things
`echo $SHELL`  the shell used
`arch` computer's architecture
`bash` to start a new bash session (within the current session)
`exit` to exit current bash session (if it is the outermost one, will close window)
`passwd` to create a new password

`su` 'switch user' to the specified user; if no username, switch to root.
`sudo su` to user root. `exit` ends session.


multiple commands can be typed by separating each by using `;` 
`$ uname -o; echo $SHELL; who; whoami;`
```bash
GNU/Linux
/bin/bash
sujith   seat0        2024-12-24 08:55 (login screen)
sujith   tty2         2024-12-24 08:55 (tty2)
sujith
```


___

## Commands, Options, Parameters

`command [option(s)] [parameter(s)]` is the basic format of the Linux commands.

`options` typically follow a hyphen`-` 
Same options can act differently in different commands,
some Options have similar meaning in many commands,
`-f / --force` for force and `-i / --interactive` is in `cp, mv, rm`
`-r / --recursive` perform recursive operation for `cp` `rm`
`-a` for all and `-h / --help`  are common in most commands


`parameters` are sometimes required and sometimes optional.

