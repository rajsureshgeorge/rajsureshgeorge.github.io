---
layout: post
title: Git Useful Commands
date: 2024-07-31
categories: ["Technology", "git", "Programming"]
---


# Initializing Git

git init


# Git Adding Commands


## Adding a file

git add file


## Adding Every file

git add .


## Updating Already Staged files

git add -u (or) git add `--`update


## Save Change in the entire working directory

git add -a (or) git add `--`all



# Git Branch Command



## List Branches

git branch




## Create a New Branch

git branch (branch-name)




## Switch to a Branch

git checkout (branch-name)




## Create and Switch to a new branch

git checkout -b (branch-name)




## Delete a Branch

git branch -d (branch-name)




## Force Delete a Branch

git branch -D (branch-name)




## Rename a Branch

git branch -m (new-branch-name)




## Renaming Current Branch name

git branch -m (old-branch-name) (new-branch-name)



## Track Remote Branch

git branch `--`track (new-branch) (remote-branch)



## List All Branches (Local and Remote)

git branch -a



## List Remote Branches

git branch -r




# Git Checkout Commands




## Switch to an Existing Branch

git checkout (branch-name)




## Create and Switch to a New Branch

git checkout -b (new-branch-name)




## Switch to the Previous Branch

git checkout -




## Check Out a Specific Commit

git checkout (commit-hash)




## Restore a File from a Specific Commit

git checkout (commit-hash) `--` (file-path)

> This command checks out a specific file from a specific commit.




## Discard Changes in a File

git checkout `--` (file-path)

> This command discards changes in the specified file, restoring it to the last committed state. 




## Check Out a Remote Branch

git checkout -b (new-branch-name) (remote-name)/(branch-name)

> This command creates a new local branch tracking a remote branch and switches to it.




# Git Commit Commands




## Commit with a Message

git commit -m "Your commit message"




## Commit All Changes

git commit -a -m "Your commit message"

> The -a option stages all modified and deleted files before committing, but it does not stage new untracked files.




## Amend Last Commit

git commit `--`amend -m "Updated commit message"

> The -a option stages all modified and deleted files before committing, but it does not stage new untracked files.




## Interactive Commit

git commit -p

> The -p (or `--`patch) option allows you to interactively select parts of files to commit. This is useful for breaking a large change into smaller, more meaningful commits.  




## Detailed Commit Message

git commit

> This command opens the default text editor, allowing you to write a detailed, multi-line commit message.




## Sign-Off a Commit

git commit -s -m "Your commit message"

> The -s (or `--`signoff) option adds a Signed-off-by line at the end of the commit message. This is often used in projects that require a Developer Certificate of Origin (DCO).




## Specify Author

git commit `--`author="Author Name (email@example.com)" -m "Your commit Message"




## Include Untracked Files

git commit -a -m "Your Allow Empty Commit message" -o




## Allow Empty Commit

git commit `--`allow-empty -m "Empty commit message"




## Commit with GPG Signature

git commit -S -m "Your commit message"

> The -S (or `--`gpg-sign) option signs the commit with your GPG key, providing cryptographic proof that the commit was made by you.




## Commit Using a Template

git commit `--`template=(file)




## Commit with Verbose Output

git commit `--`verbose




# Git Diff Commands




## Show Changes in Working Directory

git diff




## Show Changes Between Staged Files and Last Commit

git diff `--`cached




## Show Changes Between Working Directory and Last Commit

git diff HEAD



## Compare Two Commits

git diff (commit1) (commit2)




## Compare a Commit with Working Directory

git diff (commit)




## Compare Branches

git diff (branch1) (branch2)




## Compare a File Between Two Commits

git diff (commit1) (commit2) `--` (file-path)




## Compare Staged Changes for a Specific File

git diff `--`cached `--` (file-path)

> This command shows the differences between the staged version of a specific file and the last commit.




## Show Differences with Color

git diff `--`color




## Show Differences in Unified Format

git diff `--`unified=(num)




## Show Differences with Word Granularity

git diff `--`word-diff

> This command shows differences at the word level rather than line level.




## Show Differences with Stat Summary

git diff `--`stat

> This command provides a summary of changes, including the number of files changed, insertions, and deletions.




# Git Log Commands




## Git Log with decoration

git log `--`graph `--`oneline `--`decorate `--`all




## Git log with formatting

git log `--`graph `--`oneline `--`decorate `--`all




## Git log find by commit message

git log `--`all `--`grep="commit message"




# Git Tag Commands




## Normal Git Tagging

git tag (name)/(version)




## Pushing Git tags

git push `--`tags




## Delete Git Tag

git tag -d (name)/(version)




## Tagging with new tag name

git tag (new) (with commit hash)




## Pushing the Old Delete tag Update to Origin (local git / gitlab / github

git push origin :refs/tags/old tag name




# Git Pull Commands




## Pull Changes from the Default Remote and Branch

git pull




## Pull Changes from a Specific Remote and Branch

git pull (remote) (branch)




## Rebase Instead of Merge

git pull `--`rebase

> This command fetches changes from the remote and rebases your local commits on top of the fetched changes instead of merging them. This can help keep a linear history.




## Pull with Verbose Output

git pull `--`verbose




## Pull with Squash

git pull `--`squash

> This option prepares the changes from the remote branch for a single commit rather than merging them directly. You need to manually commit the squashed changes.




## Pull with Specific Merge Strategy

git pull -s (strategy)

> This command specifies a merge strategy for integrating the fetched changes.




# Git Push Commands




## Push Changes to the Default Remote Branch

git push




## Push Changes to a Specific Remote and Branch

git push (remote) (branch)




## Push All Local Branches

git push `--`all




## Push Tags

git push `--`tags




## Push with Force

git push `--`force




## Push with Lease

git push `--`force-with-lease

> This command forces the push but only if your local branch is up-to-date with the remote branch. It helps prevent overwriting changes that others might have pushed.




## Push with a Specific Ref

git push (remote) (local-branch):(remote-branch)




## Push to Set Upstream Tracking

git push `--`set-upstream (remote) (branch)

> This command sets the specified remote branch as the upstream branch for the current local branch. It is useful for tracking branches and simplifying future push and pull commands.




## Push with Verbose Output

git push `--`verbose




# Git Merge Commands




## Merge Another Branch into Current Branch

git merge (branch-name)

> This command merges the specified branch into the current branch.




## Merge with a Specific Commit

git merge (commit-hash)

> This command merges the changes from a specific commit into the current branch. This is less common but can be used for selective integration.




## Merge with No Fast-Forward

git merge `--`no-ff (branch-name)

> This command performs a merge without fast-forwarding, creating a merge commit even if the merge could be fast-forwarded. This is useful for keeping a record of the merge in the history.




## Merge with Squash

git merge `--`squash (branch-name)

> This command combines all the changes from the specified branch into a single commit. It does not create a merge commit but instead prepares the changes for a new commit.




## Merge with Strategy

git merge -s (strategy) (branch-name)

> This command specifies a merge strategy. Common strategies include recursive (default), ours, theirs, resolve, and octopus.




## Abort a Merge

git merge `--`abort

> If a merge conflict occurs and you decide not to continue with the merge, this command aborts the merge process and restores the working directory to the state before the merge.




# Git Rebase Commands




## Rebase the Current Branch onto Another Branch

git rebase (branch)

> This command rebases the current branch onto the specified branch.




## Rebase Interactively

git rebase -i (base-commit)

> This command starts an interactive rebase from a specified base commit.




## Continue a Rebase After Conflicts

git rebase `--`continue

> After resolving conflicts during a rebase, use this command to continue the rebase process.




## Skip a Commit During Rebase

git rebase `--`skip

> This command skips the current commit that caused conflicts and continues with the rebase.




## Abort a Rebase

git rebase `--`abort

> This command aborts the rebase process and returns your branch to its previous state before the rebase started.




## Rebase with Autosquash

git rebase `--`autosquash

> This command automatically squashes commits marked with fixup! or squash! in the interactive rebase session.




## Rebase with a Specific Strategy

git rebase -s (strategy)

> This command specifies a merge strategy for rebasing. Strategies include recursive, ours, theirs.




## Rebase with No-FF

git rebase `--`no-ff

> This command forces a rebase without fast-forwarding, creating a new commit even if the rebase could be fast-forwarded.




# Git Status Commands




## Show Current Status

git status




## Show Status with Verbose Output

git status `--`verbose




## Show Status with Short Format

git status `--`short




## Show Status with Porcelain Format

git status `--`porcelain

> Provides a machine-readable output, which is useful for scripts. It outputs a status that’s easy to parse programmatically.




## Show Status for a Specific Path

git status (path)




# Git Stash Commands




## Stash Changes

git stash

> This command stashes all the uncommitted changes in your working directory and the index (staged changes). By default, it stashes both modified and staged files.




## Stash with a Message

git stash save "message"

> This command stashes changes with an optional message describing the stash.




## List Stashes

git stash list

> This command lists all stashes in your repository. Each stash is referenced by an index (e.g., stash@{0}).



## Apply Stash

git stash apply [(stash)]

> This command applies the most recent stash or a specific stash to your working directory without removing it from the stash list




## Pop Stash

git stash pop [(stash)]

> This command applies the most recent stash or a specific stash and then removes it from the stash list.




## Drop a Stash

git stash drop [(stash)]

> This command removes a specific stash from the stash list.




## Clear All Stashes

git stash clear

> This command removes all stashes from the stash list




## Stash Only Unstaged Changes

git stash push -k

> This command stashes only the changes in your working directory, leaving staged changes as they are.




## Stash Only Staged Changes

git stash push -p

> This command stashes only the staged changes, leaving the working directory as is.
