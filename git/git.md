# Git

The world's most popular Version control system



## Git basics

In Windows, Install Git Bash

Then verify version
````
$ git --version
````

### Configuring Git


````
$ git config --global user.name "Your Name"
$ git config --global user.email your.mail@gmail.com
````

Verify the configuration
````
$ git config user.name
$ git config user.email
````



## Git Commands

Show local working repository status
````
$ git status
````

Create a new git repository
````
$ git init
````

## Git committing workflow

>[Working directory] => git add => [ Staging Area ] => git commit => [Repository]

Use git add to add specific files to the staging area. Separate files with spaces to add multiple at once.
````
$ git add file1 file2
````

Use "git add ." to stage all changes at once
````
$ git add .
````

To add a whole folder
````
$ git add folder/
````

Use the git commit command to actually commit changes from the staging area to local repository. We need to provide a commit message that summarizes the changes.
````
$ git commit -m "my message"
````

Retrieves information of the commits of a given repository
````
$ git log
````

show simple log for each commit
````
$ git log --abbrev-commit
````

show one line log for each commit
````
$ git log –oneline
````

### Configure Git's default editor

vim : 
````
$ git config –global core.editor "vim"
````
Escaping VIM when do git commit :
- Hit letter i to enter insert mode
- Then enter a message to commit
- Hit escape key to leave insert mode
- :wq to quit Vim then hit Enter

Visual Studio Code : 
````
$ git config –global core.editor "code --wait"
````

### Amending commits
Suppose you just made a commit and then realized you forgot to include a file. Rather than making a brand new separate commit, you can "redo" the previous commit using the –amend option

````
$ git commit -m 'some commit'
$ git add forgotten_file
$ git commit --amend
````

### .gitignore

Create a file .gitignore in the root of a repository. Inside the file we can write patterns to tell Git which files & folders to ignore:

`file1.txt` will ignore files named file1.txt

`folderName/` will ignore an entire directory

`*.log` will ignore any files with the .log extension