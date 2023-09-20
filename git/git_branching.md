# Git Branching

## Branching

HEAD is simply a pointer that refers to the current "location" in your repository. It points to a particular branch reference.

Ex :
````
$ git log
commit 2ccac780399856853e774f2dfc7ce6a93f013fb1 (HEAD -> master)
````

Use `git branch` to view your existing branches.
````
$ git branch
* master
````

## Creating branches
Use `git branch <branch-name>` to make a new branch based upon the current ````HEAD````
This just creates the branch. It does not switch you to that branch (the ````HEAD```` stays the same)


````
$ git branch branch_1

$ git branch
branch_1
* master

$ git log
commit 2395afb3c206378b3224b6af9c388e3828118ad6 (HEAD -> master, branch_1)
````

## Switching branches

Use `git switch <branch-name>` to switch to a branch.

````
$ git switch branch_1
$ git log
commit 2395afb3c206378b3224b6af9c388e3828118ad6 (HEAD -> branch_1, master)
````

Historically, we used `git checkout <branch-name>` to switch branches. It does a lot more than a "git switch"


## Creating & switching

Use `git switch` with the -c flag to create a new branch and switch to it all in one go (-c as short for "create")

````
$ git switch -c <branch-name>
````

OR use `git checkout -b` (-b as short for "branch")
````
$ git checkout -b <branch-name>
````

## Deleting & renaming branches

Deleting using -d (or -D for force), you must not on the branch
````
$ git branch -d branch_3
````

Rename using -m (move/rename a branch and the corresponding reflog) or -M (shortcut for –move –force), you must on the branch
````
$ git switch branch_2
$ git branch -m new_branch_2
````


