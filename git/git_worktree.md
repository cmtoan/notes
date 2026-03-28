# Git Worktree

Worktrees are a feature that allows developers to create additional working trees within the same Git repository. 
This feature aims at making it easier to work on two branches simultaneously.

Using a second working tree can be useful to, e.g., run long-running tests on the current version, 
while working on the next version branch, or to make an urgent fix without switching out of the current branch.

Working trees are linked to the main repository and all know about each other. So, it is not allowed to check out 
the same branch in two different working trees, to prevent the two working trees from going out of sync.

## Worktree Command

````
$ git worktree add ../worktree-1 new-feature
$ git worktree add ../worktree-hotfix -b hotfix
$ git worktree add ../worktree-hotfix hotfix
$ git worktree add -b worktree-test ../worktree-1 main
````

This will create a new directory at the specified location, e.g. ../worktree-hotfix, a new branch from origin/master, 
and will check it out in that directory.
````
$ git worktree add -b hotfix ../worktree-hotfix origin/master
````

````
$ git worktree list
$ git worktree remove ../worktree-1

$ rm -rf worktree-hotfix
$ git worktree prune
````

## Triangular workflows

A typical git branch setup
````mermaid
---
Title: A typical git branch setup
---
flowchart 
    A(Local ref: <br> branch)-->|"push"| B(Source ref: <br> origin/branch)
    B --> |"pull/merge"| A
````

### Refs

A ref is a reference to a repository and branch. It has two parts: the remote, usually a name like origin or upstream, 
and the branch. If the remote is the local repository, it is blank. 
So, in the example above, origin/branch in the purple box is a remote ref, referring to a branch named branch on 
the repository name origin, while branch in the green box is a local ref, referring to a branch named branch on
the local machine.

While working with GitHub, the remote ref is usually the repository you are hosting on GitHub. In the diagram above, 
you can consider the purple box GitHub and the green box your local machine.

### Pushing and pulling

The headRef is sending the changes (pushing them) and the baseRef is receiving the changes (pulling them).

````mermaid
---
Title: Disambiguating headRef and baseRef for push/pull operations
---
flowchart LR
    A(headRef)-->|"push/pull"| B(baseRef)
````

When dealing with a branch
* we call pullRef the branch from which we perform a pull (this is the pull’s headRef)
* we call pushRef the branch to which we perform a push (this is the push’s baseRef)

### Pull Requests

On GitHub, a pull request is a proposal to integrate changes from one ref to another.

### Triangular workflow

In a centralized workflow, any given branch is pushing and pulling from a remote ref with the same branch name.

A triangular workflow pushes to and pulls from different refs.

Triangular workflows are commonly used to coordinate a team of contributors. The basic ideas is that 
contributors have their own forks and, when ready to share their work, they create a pull request that 
will eventually be merged into the main repository.

````mermaid
---
Title: a triangular workflow
---
flowchart 
    A(Local Machine <br> ref: branch)-->|"push"| B(GitHub <br> ref: origin/branch)
    B --> |"Pull request"| C(Github <br> ref: upstream/branch)
    C --> |"pull"| A
````

### Git commands for triangular workflows

First, fork the project, for example, from https://github.com/upstream_repo/example .

After clone your forked repository to your local machine.
Then set up a remote ref to the upstream repository.
````
$ git clone https://github.com/my_repo/example.git
$ git remote add upstream https://github.com/upstream_repo/example
````

We have the following configuration:

.git/config
````
[remote "origin"]
	url = https://github.com/my_repo/example.git
	fetch = +refs/heads/*:refs/remotes/origin/*
[remote "upstream"]
	url = https://github.com/upstream_repo/example
	fetch = +refs/heads/*:refs/remotes/upstream/*
[branch "main"]
	remote = origin
	merge = refs/heads/main
````

Verify configuration and configure your editor
````
$ git remote -v
$ git config --global core.editor "vim"
````

re-sync your local main branch with upstream
````
$ git fetch upstream
$ git checkout main
# update local main
$ git pull --ff-only upstream main
# push to my fork
$ git push origin main
````

create feature branche from my updated main
````
$ git checkout -b feature/my-new-branch
````

re-sync my feature branch with upstream
````
$ git fetch upstream
$ git rebase upstream/main
````

### The @{push} revision syntax

The @{push} notation denotes the current value of the remote-tracking (pushRef) branch that the current branch would be pushed to.

| Command                            | Description                                                                                              |
|------------------------------------|----------------------------------------------------------------------------------------------------------|
| git rev-parse --abbrev-ref HEAD    | The actuel local branche                                                                                 |
| git rev-parse --abbrev-ref @{push} | The target branche to push to (pushRef), the one Git will update if you run `git push` with no arguments |
| git rev-parse --abbrev-ref @{u}    | The upstream branche (pullRef)                                                                           |   

Example:
````
[branch "feat/test"]
    remote = origin
    merge = refs/heads/main        # pullRef
    push = refs/heads/dev          # pushRef
````

## Ref

https://github.blog/open-source/git/how-the-github-cli-can-now-enable-triangular-workflows/