# Git

## Switch between branches

`git checkout <branch-name>`

## Get remote branch locally

`git checkout -b <repo-name> origin/<repo-name>`

## Create branch

* Long way:

 `git branch <branch_name>`

 `git checkout <branch_name>`

* Short way:

 `git checkout -b <branch_name>`

## Rename branch

`git branch -m <oldname> <newname>`

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

## Listing names of new files

`git diff --name-only --diff-filter=A master <branch-name>`

## Creating tag

`git tag -a <version, i.e. 1.0.0> -m '<description'`

## Pushing tag

`git push --follow-tags`

## Changing commit message

`git commit -amend`

But only if commit hasn’t been pushed to repo. Otherwise it might cause problems.

## Resetting branch

When stuff is committed but not pushed.

`git reset --hard origin/master`

## Moving commits to other branch

Scenario: you committed to a branch `master` instead of your `feature/magical-branch-name` but did not yet push. What now?

(You are on master branch.)

```
git checkout feature/<branch-name>
git merge master
git checkout master
git reset --hard origin/master
```

Stuff from `master` is now in feature branch, and `master` itself was resetted to its origin state. As nothing was pushed, nothing happened.

Instead of `master`, of course, you might use `some/other-branch`.

## Credentials

* To remember credentials by deamon:

 `git config --global credential.helper wincred`

* To clear remembering credentials:

 `git config --global --unset credential.helper`

## Removing file from tracking

* If file was committed once but we want to remove it from tracking, the following command will do:

 `git update-index --assume-unchanged <file>`

* To revert it:

 `git update-index --no-assume-unchanged path/to/file`

## Getting rid of `.idea`

If someone committed and pushed `.idea` folder to the repo, it will become problematic. This is the solution:

```
mv .idea ../.idea_backup
rm .idea # in case you forgot to close your IDE
git add .idea
git commit -m "Remove .idea from repo"
mv ../.idea_backup .idea
```

After than make sure to ignore `.idea` in your `.gitignore`.