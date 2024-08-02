# Git use case

## Checkout

We can use git checkout <commit-hash> to view a previous commit. We just need the first 7 digits of a commit hash.
````
$ git checkout 2395afb
````

HEAD usually refers to a branch NOT a specific commit.

````
$ git checkout HEAD~1
$ git checkout HEAD~2
````

go back to what I was
````
$ git switch -
````

## Discarding changes

Suppose you've made some changes to a file but don't want to keep them. To revert the file back to whatever it looked like when you last committed, you can use :
````
$ git checkout HEAD <file>
````

Another Option does the same thing
````
$ git checkout -- <file>
````

to discard any changes in that file, reverting back to the HEAD
````
$ git checkout HEAD file1.txt
$ git checkout -- file1.txt
````

## Restore

git restore is a brand new Git command that helps with undoing operations.
````
$ git restore <file-name>
````

Restore the contents of file to its state from the commit prior to HEAD
````
$ git restore --source HEAD~1 file1.txt
````

### Unstaging files with Restore

If you have accidentally added a file to your staging area with git add and you don't wish to include it in the next commit, 
you can use git restore to remove it from staging
````
$ git restore --staged <file-name>
$ git restore --staged file2.txt
````

## Undoing commits with Git reset
This will reset the repo back to a specific commit. The commits are gone. 
The changes still there in local. We can use to deplace these changes to another branch.

````
$ git reset <commit-hash>
$ git reset e96f283
````

If you want to undo both the commits and the actual changes in your files, 
you can use the --hard option.
````
$ git reset --hard <commit>
$ git reset --hard e96f283
````

## Reverting commit

git revert is similar to git reset in that they both "undo" changes :
* git reset actually moves the branch pointer backwards, eliminating commits.
* git revert instead creates a brande new commit which reverses/undos the changes from a commit.

````
$ git revert <commit-hash>
$ git commit -a -m "bad commit"
````

## Show current branch name

````
$ git rev-parse --abbrev-ref HEAD
$ git branch --show-current
````

## Reset a local branch to the point where the remote is

````
$ git fetch origin
$ git reset --hard origin/<branchname>
````
git fetch origin downloads the latest from remote without trying to merge or rebase anything.

Ex:
````
$ git branch --show-current
$ git fetch origin
$ git reset --hard origin/fix/test
````
