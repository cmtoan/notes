# Github

## Clone a repository
````
$ git clone <url>
````

## Git remote

To view any existing remotes for your repository
````
$ git remote
$ git remote -v (verbose, for more info)
````

## Adding a new remote
A remote is really two things : a URL and a label
````
$ git remote add <name> <url>

Ex:
$ git remote add origin https://github.com/example/repo.git
````

Origin is a conventional Git remote name, but it is not at all special. It's just a name for a URL
When we clone a Github repo, the default remote name setup for us is called origin. 
You can change it. Most people leave it.

Ex:
````
$ git remote add myfirstgithub https://github.com/example/repo.git
````

to verify
````
$ git remote -v
````

## Other commands
They are not commonly used, but there are commands to rename and delete remotes if needed
````
$ git remote rename <old> <new>
$ git remote remove <name>
````

## Pushing
We need to specify the remote we want to push up to AND the specific local branch we want to push up to that remote
````
$ git push <remote> <branch>
````

Ex:
Tells git to push up the master branch to our origin remote
````
$ git push origin master
````
push another branch
````
$ git push origin another_branch
````

We often push a local branch up to a remote branch of the same name, 
but we can push to a remote branch with a different name also
````
$ git push <remote> <local-branch>:<remote-branch>
Ex:
$ git push origin branch_1:master
````

## The -u option

The -u option allows us to set the upstream of the branch we're pushing. 
You can think of this as a link connecting our local branch to a branch on Github.

Running git push -u origin master sets the upstream of the local master branch so that it tracks the master branch on the origin repo
````
$ git push -u origin master
````

Once we've set the upstream for a branch, we can use the git push shorthand which will push our current branch to the upstream.
````
$ git push -u origin master
````

Then next time, we push
````
$ git push
````

This tells git that on my computer locally in my repo I want to push up the master branch to origin master and I want you to remember that. 
I want you to recall in the future that my master branch on my computer is connected to the master branch on origin.

## Another github workflow : clonning first

````
$ git clone https://github.com/example/repo.git
$ git remote -v
$ touch file1.txt
$ git add .
$ git commit -m "first commit"
````

check branch
````
$ git branch
$ git push origin master
````

## Rename master branch to main

In the master branch
````
$ git branch -M main
$ git branch
$ git push origin main
````

## Remote tracking branches

This is a "Remote Tracking Branch". It's a reference to the state of the master branch on the remote. 
I can't move this myself. It's like a bookmark pointing to the last known commit on the master branch on origin.

"At the time you last communicated with this remote repository, here is where x branch was pointing"

They follow this pattern <remote>/<branch>
* origin/master references the state of the master branch on the remote repo named origin.
* upstream/myBranch references the state of the myBranch branch on the remote named upstream (a common remote name)


To view the remote branches our local repository knows about
````
$ git branch -r
````

### Checking out remote checking branches
````
$ git checkout origin/master
````

## Working with remote branches
````
$ git branch
$ git branch -r
````

By default, my master branch is already tracking origin/master

````mermaid
block-beta
    columns 3
        Workspace space Remote
        A space B
        A("master") --> B("origin/master <br /> origin/branch_1")
````
checkout branch_1
````
$ git checkout origin/branch_1
````

I want my own local branch called branch_1, and I want it to be connected to origin/branch_1, 
just like my local master branch is connected to origin/master

Run git switch <remote-branch-name> to create a new local branch from the remote branch of the same name
````
$ git switch branch_1
````
makes me a local branch branch_1 AND sets it up to track the remote branch origin/branch_1

````mermaid
block-beta
    columns 3
    Workspace space Remote
    A space B
    C space D
    A("master") --> B("origin/master")
    C("branch_1") --> D("origin/branch_1")
````

````
$ git branch
````

The old way to do the same thing
````
$ git checkout --track origin/branch_1
````

## Git Fetch

````mermaid
zenuml
    title Git Workflow
    A as Workspace
    B as "Staging (index)"
    C as "Local Repository"
    D as "Remote Repository"
    A -> B : git add
    B -> C : git commit
    C -> D : git push
    D -> C : git fetch
    D -> A : git pull
````

Fetching allows us to download changes from a remote repository, 
BUT those changes will not be automatically integrated into our working files.

It lets you see what others have been working on, 
without having to merge those changes into your local repo.

Think of it as "please go and get the latest information from Github, but don't screw up my working directory."

The git fetch <remote> command fetches branches and history from a specific remote repository. It only updates remote tracking branches.

````
$ git fetch <remote>
````

If not specified, <remote> defaults to origin
````
"git fetch origin" would fetch all changes from the origin remote repository
````

We can also fetch a specific branch from a remote :
````
$ git fetch <remote> <branch>
````
Ex: retrieve the latest information from the master branch on the origin remote repository
````
$ git fetch origin master
````

To see those changes on remote
````
$ git fetch origin master
$ git checkout origin/master
````

My master branch in local is untouched.

## Git pull

Git pull is another command we can use to retrieve changes from a remote repository. 
Unlike fetch, pull actually updates our HEAD branch with whatever changes are retrieved from the remote.
````
git pull = git fetch + git merge
````
(git fetch : update the remote tracking branch with the latest changes from the remote repository;
git merge : update my current branch with whatever changes are on the remote tracking branch)

syntaxe
````
$ git pull <remote> <branch>
````

Just like with git merge, it matters WHERE we run this command from. 
Whatever branch we run it from is where the changes will be merged into.

Fetch the latest information from the origin's master branch and merge those changes into our current branch.
````
$ git pull origin master
````

If we run git pull without specifying a particular remote or branch to pull from, git assumes the following :
* remote will default to origin
* branch will default to whatever tracking connection is configured for your current branch

## Merging in feature branches
Pull request

delete branch after merge
````
$ git branch -D branch_1
$ git branch
````

## Merge with conflict

* Step 1 : bring the changes and test
````
$ git fetch origin
$ git checkout -b branch_1 origin/branch_1
$ git merge main
````

* Step 2 : merge the changes and update on Github
````
$ git checkout main
$ git merge --no-ff branch_1
$ git push origin main
(--no-ff  : not fast forward)
````

Or

* Step 1 :
````
$ git fetch origin
$ git switch branch_1
$ git merge main
````

fix conflicts
````
($ git add file.txt
$ git commit -m "message")
````

* Step 2 :
````
$ git switch main
$ git merge branch_1
$ git push origin main
````

## Forking

Github (and similar tools) allow us to create personal copies of other peoples' repositories. 
We call those copies a "fork" of the original.

When we fork a repo, we're basically asking Github "Make me my own copy of this repo please"

As with pull requests, forking is not a Git feature. The ability to fork is implemented by Github.

Create a fork from the official project :
* checkout the fork (origin) into local
* In my local machine, I add a remote pointing to the original project repo (not the fork). 
This remote can be named anything, but you'll often see "upstream" or "original" used. 
So I can update any changes in the original.

We have two remotes, one to my fork (origin), one to the original (upstream).
Make changes and commit to my fork.

Next I can make a pull request from my fork on Github to the original project repository.

All I need to do is pull from upstream (the original repo) to get the latest changes in my local repo.

The whole point of this workflow is to allow people who don't have direct access,  
direct permission to push or to change anything in a project repository. 
They can still collaborate, they can still make pull requests by forking and 
then pushing the changes to their fork and opening a PR.

````mermaid
flowchart
    subgraph Github
        A(My Fork)
        B(The Official Project Repository)
        A -- Pull Request --> B
    end
    subgraph My Local Machine
        C(Local Repository)
        C -- Push --> A
        B -- Pull --> C
    end
````

1. Create a project fork-and-clone for user 1 in github and make some commits
2. Fork this project fork-and-clone for user 2

clone this project of user 2 in local
````
$ git clone <url_2>
````
verify this point to the project fork-and-clone of user 2
````
$ git log
$ git remote -v
````

add a second remote that point to the user 1's project
````
$ git remote add upstream <url_1>
````

verify that now we have two remotes
````
$ git remote -v
verify status
$ git status
````

In this local, check if there are some updates from original and retrieve this
````
$ git pull upstream main
$ git log
````

do some commits in user 2's branch
````
$ git add readme.md
$ git commit -m "do some commits"
````

push to user 2's origin
````
$ git push origin main
````

Make a pull request to the original github
````
main/user_2:fork-and-clone -> main/user_1:fork-and-clone
````

## Rebase

There are two main ways to use the git rebase command :
* as an alternative to merging
* as a cleanup tool

### Comparing Merge and Rebase
With the merge : the feature branch has a bunch of merge commits. 
If the master branch is very active, my feature branch's history is muddied.

If I'm merging pretty frequently just to get those changes from master whatever my coworkers are doing, 
if that is a very active project, that could be a lot of merging onto each feature branch. 
And my coworkers all have to do that too. And if everyone else has merged changes into master, 
they need to get those changes onto their feature branches. 
So everyone's feature branches might be riddled with a bunch of merge commits and then when they merge those back into master, 
there's just a bunch of useless merge commits as part of the history.

### Rebasing can help us with this
We can instead rebase the feature branch onto the master branch. 
This moves the entire feature branch so that it BEGINS at the top of the master branch. 
All the work is still there, but **we have re-written history (and this is why it's sometimes problematic)**. 
We are rewriting history, we're creating new commits, 
or we have git create new commits for us based upon the original feature branch commits.

Instead of using a merge commit, rebasing rewrites history by creating new commits for each of the original feature branch commits.
````
$ git switch feature
$ git rebase master
````

### Example Merge
````
$ git init
$ touch readme.md
$ git commit -am "add readme"
````

switch to a feature branch
````
$ git switch -c feat
$ touch feature.txt
$ git add feature.txt
$ git commit -m "add file"
````

get back to master branch
````
$ git switch master
````

do some updates
````
$ git commit -am "add something"
````

#### do merge
````
$ git switch feat
````
merge master to feature branch
````
$ git merge master
````

continue on feature, do some changes then commit it
````
$ git commit -am "more commits"
````

go back to master
````
$ git switch master
````

do some changes and commit it
````
$ git commit -am "add some changes in master"
````

#### do merge feature into master
````
$ git switch feat
$ git merge master
````

### Example rebase
on feature branch
````
$ git rebase master
$ git branch
$ git log –oneline
````

make some changes on master branch
````
$ git switch master
$ git commit -am "add something"
````

check difference
````
$ git diff feat..master
````

go to feature
````
$ git switch feat
````

rebase the feature branch onto the master branch
````
$ git rebase master
````

### When not to Rebase

Never rebase commits that have been shared with others. 
If you have already pushed commits up to Github... DO NOT rebase them unless you are positive no one on the team is using those commits

You do not want to rewrite any git history that other people already have. 
It's a pain to reconcile the alternate histories.

### Rebase conflict

resolve conflicts then do the command
````
$ git add file.txt
$ git status
$ git rebase --continue
````

### Interactive rebase

Rewriting history.

Sometimes we want to rewrite, delete, rename or even reorder commits (before sharing them). 
We can do this using git rebase.

Running git rebase with the -i option will enter the interactive mode, which allows us to edit commits, add files, drop commits, etc. 
Note that we need to specify how far back we want to rewrite commits

also, notice that we are not rebasing onto another branch. 
Instead we are rebasing a series of commits onto the HEAD they currently are based on.

Ex: we go back four commits
````
$ git rebase -i HEAD~4
````

Ex:
````
$ git clone <url>
$ git log --oneline
$ git switch -c my-feat
````

go back to 9 commits
````
$ git rebase -i HEAD~9
````

In our text editor, we'll see a list of commits alongside a list of commands that we can choose from. 
Here are a couple of the more commonly used commands:
* pick – use the commit
* reword – use the commit, but edit the commit message
* edit – use commit, but stop for amending
* fixup – use commit contents but meld it into previous commit and discard the commit message
* drop – remove commit

Ex:
````mermaid
block-beta
    columns 1
        A space B
        A("pick 1ff9e42 add notes
pick 414ff9c ignore
pick d24cdfb update
") --> B("drop 1ff9e42 add notes
pick 414ff9c ignore
reword d24cdfb update")
````

do some changes (reword), save it, then verify
````
$ git status
$ git log --oneline
````

