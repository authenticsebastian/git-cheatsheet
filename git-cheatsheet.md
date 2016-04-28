# Git

## Switch between branches

`git checkout <branch-name>`

## Get remote branch locally

`git checkout -b repo-name origin/repo-name`

## Create branch

* Long way:

 `git branch <branch_name>`
 
 `git checkout <branch_name>`
 
* Short way:

 `git checkout -b <branch_name>`

## Push new branch to remote

`git push --set-upstream origin <branch_name>`

## Remove branch

* Local:

 `git branch -d <branch-name>`

 But first checkout to some other branch. You cannot remove branch you’re on.

* Remote:

 `git push origin :<branch-name>`
 
 Looks strange, so to picture this: you’re pushing `<nothing>:<branch-name>`.
 
* Cleaning information on remote branches

 `git remote prune origin`


## Stashing

Comes handy if you want to change branch without committing current stuff.

* To stash:

 `git stash`

* To unstash:

 `git stash apply`

* To list:

 `git stash list`

## Credentials

* To remember credentials by deamon:

 `git config --global credential.helper wincred`

* To clear remembering credentials:

 `git config --global --unset credential.helper`