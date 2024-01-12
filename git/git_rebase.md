# Git rebase

### Command to rebase
````
$  git fetch
$  git rebase -i origin/main
````

### For some reason, to abort rebase
````
$  git rebase –abort
````

### To fix rebase
````
$  git rebase -i origin/main
````

In vim
````
:%s/pick/fixup/g
````
First ligne still be 'pick'

verify status
````
$  git status
````


### Solve conflits
````
$  git rebase --continue
$  git status
$  git rebase --continue
````

### Verify if good push it
````
$  git log
$  git push -f
````

### key words

````
p, pick = use commit

r, reword = use commit, but edit the commit message

e, edit = use commit, but stop for amending

s, squash = use commit, but meld into previous commit

f, fixup = like "squash", but discard this commit's log message

x, exec = run command (the rest of the line) using shell

d, drop = remove commit
````
