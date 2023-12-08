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
