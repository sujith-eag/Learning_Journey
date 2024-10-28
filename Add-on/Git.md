#01sep24 
## Git related   
[Pro Git](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)

#### Basic setup
```c
git --version

// to change default branch to main
git config --global init.defaultBranch main

git config --global user.name  // "Name"                    
git config --get user.name
git config --global user.email // "mail@mail"       
git config --get user.email
git config --global color.ui auto

git config --global pull.rebase false
```

## Connecting git to github with SSH

### SSH key
```c
ls ~/.ssh/id_ed25519.pub      // To check if key already exists

ssh-keygen -t ed25519    // To create a new SSH key
// enter for default place and no passkey

cat ~/.ssh/id_ed25519.pub   // copy the SSH key
```
### SSH link to GitHub
`settings   SSH and GPG keys`
`new SSH key`
`add SSH key`


## Basic git commands

```c
git status    // shows tracked, untracked, staged files

git add [file name]   // to add to staging area
git add .   // adds all available file to staging area

git commit -m "message"  // commits all files in staging area

git log   // the details of commits and difference b/w git and github
q  // to escape if it is too long

git push
git push origin main
```

### Through VScode
`code .` open a required directory and type to open current directory in git
other things remain the same

The commit message can be made as next entry by setting VScode as default
`git config --global core.editor "code --wait"`




## GitHub to Git 
```c
`New repository` in github
`Code`  copy `SSH option`  not the `http`
```
#### Repo in Git
```c
mkdir repos  //Make a new folder
cd repos   // move to that repo

git clone [paste the ssh link]     // link the repo to github
cd [the new folder]
git remote -v      // will show the details of git link
```

# Git to GitHub
```c
// Go to the directory, initialize it, commit it
git init  
git add .
git commit -m "message"   // to create repo in a folder
```
create an empty repository in github
dont add any readme files or licenses
once created copy the SSH key

#### In git 
```c
git remote add origin [ssh key]
git branch -M main     // make branch main if by chance it is in master
git push -u origin main     // git push origin main` also worked
```


# Commit messages
Have a Subject and Body, GitHub has 72-characters limit

## The seven rules of a great Git commit message

1. Separate subject from body with a blank line
2. Limit the subject line to 50 characters
3. Capitalize the subject line
4. Do not end the subject line with a period
5. Use the imperative mood in the subject line
6. Wrap the body at 72 characters
7. Use the body to explain _what_ and _why_ vs. how


-   
    Tutorial video on Conventional Commits ➔ [Video Link](https://www.youtube.com/watch?v=OJqUWvmf4gg).
    The video showcases the Conventional Commits template from the resource above. It also mentions creating releases and shows using something called “Yarn”. 
___


# Branches

`git branch` can be used to see all the current branches

The branch that was created when the first commit was made is called the main branch.
Other branches can be made to work on a certain feature as a feature branch.

```c
git branch

git branch <branch_name>
// New branch can be made using the command

git checkout <branch_name>
// Changing into a new branch is done using

// using -b flag to create a new branch and changing into it
git checkout -b <branch_name>

// Changing back to main branch from any branch
git checkout main
```
``

# Merge

When wanting to merge the feature branch into the main branch
```c
// Move to the branch to merge with

git merge <branch_name>
// takes the changes commited in <branch_name> and adds them to the branch that we are currently on.
```

### Merge Conflict

When same lines in a file have been changed by two different branches, there will be merge conflict.

### Deleting a branch
```c
git branch -d <branch_name>
// when branch is already merged with main

git branch -D <branch_name>
// when it hasn't been merged
```


Pushing a new branch to git hub
```c
git checkout -b rps
git push origin rps  // not the main branch

git push -u origin <branch>
// It automatically links local branch you push with remote one.

```

## Changing to old commit
```c
git log --oneline

get the id of commit 

git reset --hard 9digitId   // deleted current progress

git checkout -b old-state id  // 

git revert  // to make revert commits

```