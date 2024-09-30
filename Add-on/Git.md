## Git related   #01sep24 
[Pro Git](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)

#### Basic setup
`git --version`
`git config --global init.defaultBranch main`   to change default branch to main
`git config --global user.name "Name"`                    `git config --get user.name`
`git config --global user.email "mail@mail" `       `git config --get user.email`
`git config --global color.ui auto`

`git config --global pull.rebase false`

# Connecting git to github with SSH
### SSH key
`ls ~/.ssh/id_ed25519.pub`     To check if key already exists

`ssh-keygen -t ed25519`    To create a new SSH key
enter for default place and no passkey

`cat ~/.ssh/id_ed25519.pub`   copy the SSH key

### SSH link to GitHub
`settings   SSH and GPG keys`
`new SSH key`
`add SSH key`



# Basic git commands
`git status`    shows tracked, untracked, staged files

`git add [file name]`   to add to staging area
`git add .`   adds all available file to staging area

`git commit -m "message"`  commits all files in staging area

`git log`   the details of commits and difference b/w git and github
`q` to escape if it is too long

`git push`    or  `git push origin main`

### Through VScode
`code .` open a required directory and type to open current directory in git
other things remain the same

The commit message can be made as next entry by setting VScode as default
`git config --global core.editor "code --wait"`





# GitHub to Git 
`New repository` in github
`Code`  copy `SSH option`  not the `http`
### Repo in Git
`mkdir repos` Make a new folder
`cd repos`  move to that repo

`git clone [paste the ssh link]`     link the repo to github
`cd [the new folder]`
`git remote -v`    will show the details of git link

## Git to Github
Go to the directory, initialize it, commit it
`git init`  
`git add .` 
`git commit -m "message"`    to create repo in a folder

create an empty repository in github
dont add any readme files or licenses
once created copy the SSH key

In git 
`git remote add origin [ssh key]`
`git branch -M main`     make branch main if by chance it is in master
`git push -u origin main`     `git push origin main` also worked


# Commit messages
Have a Subject and Body

Github has 72-characters limit

## The seven rules of a great Git commit message

1. Separate subject from body with a blank line
2. Limit the subject line to 50 characters
3. Capitalize the subject line
4. Do not end the subject line with a period
5. Use the imperative mood in the subject line
6. Wrap the body at 72 characters
7. Use the body to explain _what_ and _why_ vs. how


-   
    Explore this amazing tutorial video on Conventional Commits ➔ [Full Video Link](https://www.youtube.com/watch?v=OJqUWvmf4gg). The video showcases the Conventional Commits template from the resource above. It also mentions creating releases and shows using something called “Yarn”. These two parts are out of scope for this part of the course, so don’t worry about them and instead focus on the commit template.