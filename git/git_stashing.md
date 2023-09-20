# Git Stashing

Use `git stash` to save my changes without actually committing them.
Running `git stash` will take all uncommitted changes (staged and unstagged) and stash them, reverting the changes in your working copy.
````
$ git stash
$ git stash save
````

Use `git stash pop` to remove the most recently stashed changes in your stash and re-apply them to your working copy wherever I may be (i.e to re-apply them to a different branch or to the same branch that I stash them on)
````
$ git stash pop
````

You can use `git stash apply` to apply whatever is stashed away, without removing it from the stash. This can be useful if you want to apply stashed changes to multiple branches
````
$ git stash apply
````

You can add multiple stashes onto the stack of stashes. They will all be stashed in the order you added them.

````
$ git stash list
````

````
toan@CMT MINGW64 /d/github/documents/branching (branch_1)
$ git stash list
stash@{0}: WIP on branch_1: 77d231f more update
stash@{1}: WIP on master: a5b9971 add lines
````

Git assumes you want to apply the most recent stash when you run git stash apply, but you can also specify a particular stash like
````
$ git stash apply stash@{1}
````

To delete a particular stash
````
$ git stash drop <stash-id>
````

````
$ git stash drop stash@{1}
````

Delete all stash
````
$ git stash clear
````
