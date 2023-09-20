# Git Merging

## Merging

Use git merge command
- We merge branches, not specific commits
- We always merge to the current `HEAD` branch

Following these steps to merge:
- Switch to or checkout the branch you want to merge the changes into (the receiving branch)
- Use the `git merge` command to merge changes from a specific branch into the current branch.

Ex : to merge branch branch_1 into master
````
$ git switch master
$ git merge branch_1
````

Branches are just defined by a branch pointer : This is called a fast-forward (master simply caught up on the commits from branch_1)
````
$ git branch -v

$ git switch master
toan@CMT MINGW64 /d/github/documents/branching (master)
$ git merge branch_1

$ git commit -a -m "update file"
````

## Merge Conflicts

````
toan@CMT MINGW64 /d/github/documents/branching (master)
$ git merge branch_1
Auto-merging file1.txt
CONFLICT (content): Merge conflict in file1.txt
Automatic merge failed; fix conflicts and then commit the result.
````

Ex :
````
test 1
branch 1
<<<<<<< HEAD
new commit
once more
=======
update file
once more update
>>>>>>> branch_1
````


Resolving Conflicts:
- Open up the files with merge conflicts
- Edit the files to remove the conflicts.
- Remove the conflict markers in the document
- Add your changes and then make a commit

````
toan@CMT MINGW64 /d/github/documents/branching (master|MERGING)
$ git add file1.txt
toan@CMT MINGW64 /d/github/documents/branching (master|MERGING)
$ git commit -m "resolve conflicts"
````

## Git Diff

Without additional options, git diff lists all the changes in our working directory that are not staged for the next commit. Show the difference between the working directory and the staging area. Show unstaged
````
$ git diff
````


`git diff HEAD` lists all changes in the working tree since your last commit. Showing the difference between the `HEAD` and the working directory. Show staged and unstaged since `HEAD`
````
$ git diff HEAD
````


`git diff --staged` or `--cached` will list the changes between the staging area and our last commit. Show only the changes that are staged.
````
$ git diff --staged
````

Diff-ing specific files
````
$ git diff HEAD [filename]
$ git diff --staged [filename]
````

### Comparing branches, commits

`git diff branch1..branch2` will list the changes between the tips of branch1 and branch2

````
$ git diff branch1..branch2
$ git diff commit1..commit2
$ git diff a5b9971..77d231f
$ git diff 77d231f 725a5c3
$ git diff master..branch_1
````

