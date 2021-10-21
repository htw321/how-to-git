# Your local TEST environment
If you just want to try things out, create a local test repository and start messing about - you can't break anything there.
## Help
    git
    git <command> -h
    git <command> --help

## Test repository
    mkdir test; cd test;
### git init   
Create a new GIT repository

    git init

### git add
Moves changes into a staging area. This allows you to prepare a set of changes you want to commit

    touch README.md
    git add README.md

### git commit

    git commit -m "My Great Test setup"

`git commit -a` would commit all changes without a need for staging

First commit is done, now let's change the file and look at the changes:
### git diff
Show the changes to the files

    echo "hello Cambridge" >> README.md
    git diff 

`git diff --staged` only compares the staged files
`git diff HEAD` compare to HEAD

### git status
print the current file status and staged set

    git status
`git status -s` for a short version of the status

To commit the changed file, you have to add it to the commit list

    git add README.md
    git status
    git commit -m "I've added some text"

### git log
View commit history

    git log

`git log -3` to show the last three commits
```git log --since=yesterday``` for commits since yesterday.
xxx

### git mv
Move / rename a file

    echo "Milk in a glas" > drink-me
    git add drink-me
    git commit -m "thirsty?"
    git mv drink-me empty-glass
    git commit -m "Empty"

### git rm
Remove the file from being tracked by git, but only removes the file from your current working directory when you commit the change.

    git rm empty-glass
    git commit -m "Put the glass in the dishwasher"

### git reset
Remove a file from the staging area

    echo "Forgot to butter the bread" >> README.md
    echo "Put the jam on" >> my-breakfast.txt
    git add README.md my-breakfast.txt
    git status
    git reset README.md
    git status
    git commit -m "Only put the jam in"

:exclamation: BUT can also rollback changes

    git log -2
    git reset --soft HEAD~
    git log -2

`git reset --soft` preserves the changes on your local filesystem
:exclamation: `git reset --hard` all local changes are lost

### git revert
Creates a new commit with the status of all files before the last commit (full history tracking available).
Continue with the previous status

    git status -s
    git commit -m "Only put the jam in"
    git revert --no-edit HEAD
    git log -2

    
