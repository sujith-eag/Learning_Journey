A shell contains an environment which consists of all the entities defined during this session.
Ending a session(`exit`) or starting a new session within a session (`bash`) makes the entities no longer defined.
we can move back to previous sessions from inner sessions (`subshell` or `nested shell).

A `subshell` allows to enter a new session to handle something without introducing anything to the previous session.

A item defined in a shell can be made to persist in the subshell by using `export`
`export` followed by one or more variables to be exported. (value altered in subshell does not affect the value in the outer shell)
`export -f` can be used to export functions
`export -p` displays all exported items (there are many predefined ones)
`export -n` is used to remove the export property of variable



___

There are four script files of note,
two for users and two for system admins.
`/etc/profile` `/etc/bashrc`  these are for the system admins to modify
`~/.bash_profile`  `~/.bashrc` these in the home directory are for user to modify.

The two profile files execute for both interactive and non interactive sessions.
Non interactive session is one where a shell is needed to run a script but there is no user interaction.

When we login to Linux and open a window, we are running an interactive shell.
then both the `profile` and `bashrc` scripts will execute.

`etc/profile` is the first to execute and it first defines a function called `pathmunge`.
This function is responsible for constructing the PATH variable.
Then it also defines other variables like `USER, LOGNAME, MAIL, EUID, UID` and `HOSTNAME, HISTCONTROL, HISTSIZE` environment variables are defined.
All defined variables are exported.
A `umask` instruction is executed.

`etc/bashrc` file sets up further environment variables and also adds to the PATH.
As a system administrator, we should place system-wide functions and aliases in this file.

Now `~/.bash_profile` executes.
this file by default has only one executable instruction, an if-statement to test whether the user has a `.bashrc` file in the user's home directory, and if so runs it.

users are free to edit their own `.bashrc` file, adding their own instruction to it.

`~/.bashrc` file tests to see if `etc/bashrc` exists and if so executes it (even though it has already been executed by `etc/profile`)
It concludes by adding local `bin` directories `$HOME/.local/bin` and `$HOME/bin` to the PATH variable.
At the bottom of `~/.bashrc` file is a comment whereby we can add our own aliases and functions.

___

Another file to note is `~/.bash_logout`.
This file is invoked when a bash session closes.
User might define code here to run before any session ends to clean up the user's environment (to delete empty files).

changing a file will not cause the changes until a new session starts, so `SOURCE` command can be used to run the script.
`SOURCE ~/.bashrc`


____

`vi` or newer `vim` (`vi` improved), is the default text editor found in Linux.

___

Compiler
Interpreter
platform independent `byte code` which can be quickly interpreted.

___


