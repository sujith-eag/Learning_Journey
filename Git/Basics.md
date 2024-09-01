Creating a repository on Github
Getting files to and from Github
Taking snapshot of code

### Beginning
`git --version`
`git config --global init.defaultBranch main`   to change default branch to main
`git config --global user.name "Name"`                    `git config --get user.name`
`git config --global user.email "mail@mail" `       `git config --get user.email`
`git config --global color.ui auto`

`git config --global pull.rebase false`

### SSH key
`ls ~/.ssh/id_ed25519.pub`     To check if key already exists

`ssh-keygen -t ed25519`    To create a new SSH key
enter for default place and no passkey

`cat ~/.ssh/id_ed25519.pub`   copy the SSH key

### SSH link to GitHub
`settings   SSH and GPG keys`
`new SSH key`
`add SSH key`

### Repository in GitHub
`new repository`
`Code`  copy `SSH option`  not the `http`

### Repo in Git
`mkdir repos` Make a new folder
`cd repos`

`git clone [paste the ssh link]`
`cd [the new folder]`

`git remote -v`    will show the details of git link



## Basic git commands
`git status`    shows tracked, untracked, staged files

`git add [file name]`   to add to staging area
`git add .`   adds all available file to staging area

`git commit -m "message"`  commits all files in staging area

`git log`   the details of commits and difference b/w git and github
`q` to escape if it is too long

`git push`    or  `git push origin main`


### Through VSCode
open a required directory and type `code .`   to open current directory in git
other things remain the same

The commit message can be made as next entry by setting VScode as default
`git config --global core.editor "code --wait"`




