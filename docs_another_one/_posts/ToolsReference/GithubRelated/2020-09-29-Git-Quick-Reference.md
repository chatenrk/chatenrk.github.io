---
layout: post
title: Git Quick Reference
categories: [Tools Reference, Git Reference]
tags: [github,git,cheatsheet]
background: '/img/bg-github.jpg'
---

- [Creating Snapshots](#creating-snapshots)
  - [Initializing a repository](#initializing-a-repository)
  - [Staging files](#staging-files)
  - [Viewing the status](#viewing-the-status)
  - [Committing the staged files](#committing-the-staged-files)
  - [Removing files](#removing-files)
  - [Viewing the staged/unstaged changes](#viewing-the-stagedunstaged-changes)
  - [Viewing the history](#viewing-the-history)
  - [Unstaging files (undoing git add)](#unstaging-files-undoing-git-add)
  - [Discarding local changes](#discarding-local-changes)
- [Browsing History](#browsing-history)
  - [Viewing the history](#viewing-the-history-1)
  - [Filtering the history](#filtering-the-history)
  - [Creating an alias](#creating-an-alias)
- [Branching & Merging](#branching--merging)
  - [Managing branches](#managing-branches)
  - [Stashing](#stashing)
  - [Merging](#merging)
- [Collaboration](#collaboration)
  - [Syncing with remotes](#syncing-with-remotes)
  - [Managing remotes](#managing-remotes)
- [Rewriting History](#rewriting-history)
  - [Undoing commits](#undoing-commits)
  - [Reverting commits](#reverting-commits)

# Creating Snapshots
## Initializing a repository
```sh
git init
```

## Staging files
```sh
git add file1.js # Stages a single file
git add file1.js file2.js # Stages multiple files
git add *.js # Stages with a pattern
git add . # Stages the current directory and all its content
```

## Viewing the status
```sh
git status # Full status
git status -s # Short status
```

## Committing the staged files
```sh
git commit -m “Message” # Commits with a one-line message
git commit # Opens the default editor to type a long message
```

## Removing files
```sh
git rm file1.js # Removes from working directory and staging area
git rm --cached file1.js # Removes from staging area only
```

## Viewing the staged/unstaged changes
```sh
git diff # Shows unstaged changes
git diff --staged # Shows staged changes
git diff --cached # Same as the above
```

## Viewing the history
```sh
git log # Full history
git log --oneline # Summary
git log --reverse # Lists the commits from the oldest to the newest
```

## Unstaging files (undoing git add)
```sh
git restore --staged file.js # Copies the last version of file.js from repo to index
```

## Discarding local changes
```sh
git restore file.js # Copies file.js from index to working directory
git restore file1.js file2.js # Restores multiple files in working directory
git restore . # Discards all local changes (except untracked files)
git clean -fd # Removes all untracked files
```

# Browsing History
## Viewing the history
```sh
git log --stat # Shows the list of modified files
git log --patch # Shows the actual changes (patches)
```
## Filtering the history
```sh
git log -3 # Shows the last 3 entries
git log --author=“Mosh”
git log --before=“2020-08-17”
git log --after=“one week ago”
git log --grep=“GUI” # Commits with “GUI” in their message
git log -S“GUI” # Commits with “GUI” in their patches
git log hash1..hash2 # Range of commits
git log file.txt # Commits that touched file.txt
```

## Creating an alias
`git config --global alias.lg “log --oneline"`

# Branching & Merging
## Managing branches
```sh
git branch bugfix # Creates a new branch called bugfix
git checkout bugfix # Switches to the bugfix branch
git switch bugfix # Same as the above
git switch -C bugfix # Creates and switches
git branch -d bugfix # Deletes the bugfix branch
```

## Stashing
```sh
git stash push -m “New tax rules” # Creates a new stash
git stash list # Lists all the stashes
git stash show stash@{1} # Shows the given stash
git stash show 1 # shortcut for stash@{1}
git stash apply 1 # Applies the given stash to the working dir
git stash drop 1 # Deletes the given stash
git stash clear # Deletes all the stashes
```

## Merging
```sh
git merge bugfix # Merges the bugfix branch into the current branch
git merge --no-ff bugfix # Creates a merge commit even if FF is possible
git merge --squash bugfix # Performs a squash merge
git merge --abort # Aborts the merge
```

# Collaboration
## Syncing with remotes
```sh
git fetch origin master # Fetches master from origin
git fetch origin # Fetches all objects from origin
git fetch # Shortcut for “git fetch origin”
git pull # Fetch + merge
git push origin master # Pushes master to origin
git push # Shortcut for “git push origin master”
```

## Managing remotes
```sh
git remote # Shows remote repos
git remote add upstream url # Adds a new remote called upstream
git remote rm upstream # Remotes upstream
```

# Rewriting History
## Undoing commits
```sh
git reset --soft HEAD^ # Removes the last commit, keeps changed staged
git reset --mixed HEAD^ # Unstages the changes as well
git reset --hard HEAD^ # Discards local changes
```
## Reverting commits
```sh
git revert 72856ea # Reverts the given commit
git revert HEAD~3.. # Reverts the last three commits
git revert --no-commit HEAD~3..
```