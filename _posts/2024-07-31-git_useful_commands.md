---
layout: post
title: Git Useful Commands
date: 2024-07-31
categories: ["Technology", "git", "Programming"]
---

# Table of Contents

1.  [Initializing Git](#org70b1225)
2.  [Git Adding Commands](#org8390a23)
    1.  [Adding a file](#org44e8520)
    2.  [Adding Every file](#org189441f)
    3.  [Updating Already Staged files](#orge2c87a0)
    4.  [Save Change in the entire working directory](#org8465e65)
3.  [Git Branch Command](#org41c9f69)
    1.  [List Branches](#org65029e3)
    2.  [Create a New Branch](#org160456b)
    3.  [Switch to a Branch](#org2cecdaa)
    4.  [Create and Switch to a new branch](#org538a5b1)
    5.  [Delete a Branch](#org3913f81)
    6.  [Force Delete a Branch](#org4f3d49c)
    7.  [Rename a Branch](#orgd25c328)
    8.  [Renaming Current Branch name](#orged6e585)
    9.  [Track Remote Branch](#orgf555149)
    10. [List All Branches (Local and Remote)](#orga7a9a61)
    11. [List Remote Branches](#org0cb2501)
4.  [Git Checkout Commands](#org46e9e99)
    1.  [Switch to an Existing Branch](#org67ba876)
    2.  [Create and Switch to a New Branch](#orgf3e452e)
    3.  [Switch to the Previous Branch](#orgeff1b82)
    4.  [Check Out a Specific Commit](#org909ad53)
    5.  [Restore a File from a Specific Commit](#org5138bef)
    6.  [Discard Changes in a File](#orge3d4d43)
    7.  [Check Out a Remote Branch](#org74fe276)
5.  [Git Commit Commands](#orgb90e494)
    1.  [Commit with a Message](#orgfa859c0)
    2.  [Commit All Changes](#org7c64531)
    3.  [Amend Last Commit](#org3f88a75)
    4.  [Interactive Commit](#orgf5f0f76)
    5.  [Detailed Commit Message](#org76d8d65)
    6.  [Sign-Off a Commit](#org10d3e4b)
    7.  [Specify Author](#org5516cbf)
    8.  [Include Untracked Files](#org0b41350)
    9.  [Allow Empty Commit](#org7d88769)
    10. [Commit with GPG Signature](#orgfe74236)
    11. [Commit Using a Template](#org28881c2)
    12. [Commit with Verbose Output](#orgdca5847)
6.  [Git Diff Commands](#orgfd7f2b5)
    1.  [Show Changes in Working Directory](#orgfe26c3a)
    2.  [Show Changes Between Staged Files and Last Commit](#orgfec4df0)
    3.  [Show Changes Between Working Directory and Last Commit](#orgca95cca)
    4.  [Compare Two Commits](#orgfca5e65)
    5.  [Compare a Commit with Working Directory](#org160fd3a)
    6.  [Compare Branches](#org032c4ea)
    7.  [Compare a File Between Two Commits](#org8a5f737)
    8.  [Compare Staged Changes for a Specific File](#org550ff20)
    9.  [Show Differences with Color](#org5743a60)
    10. [Show Differences in Unified Format](#orgedfd788)
    11. [Show Differences with Word Granularity](#org97e6a33)
    12. [Show Differences with Stat Summary](#orgf5a7eda)
7.  [Git Log Commands](#org745367f)
    1.  [Git Log with decoration](#org7601d1a)
    2.  [Git log with formatting](#org16eef07)
    3.  [Git log find by commit message](#org07f5b7d)
8.  [Git Tag Commands](#org6078316)
    1.  [Normal Git Tagging](#org9f8365b)
    2.  [Pushing Git tags](#org1ea9985)
    3.  [Delete Git Tag](#orgcd08fa7)
    4.  [Tagging with new tag name](#org59415b7)
    5.  [Pushing the Old Delete tag Update to Origin (local git / gitlab / github](#orgc5f034b)
9.  [Git Pull Commands](#orgd7b6fd7)
    1.  [Pull Changes from the Default Remote and Branch](#org5726569)
    2.  [Pull Changes from a Specific Remote and Branch](#org3188419)
    3.  [Rebase Instead of Merge](#org4839e1e)
    4.  [Pull with Verbose Output](#orgf9e8362)
    5.  [Pull with Squash](#orgf5a0e04)
    6.  [Pull with Specific Merge Strategy](#org1b99a64)
10. [Git Push Commands](#org0db9a2c)
    1.  [Push Changes to the Default Remote Branch](#org27e10ef)
    2.  [Push Changes to a Specific Remote and Branch](#orgc81a80f)
    3.  [Push All Local Branches](#org8669712)
    4.  [Push Tags](#org8f578f9)
    5.  [Push with Force](#org8977ad0)
    6.  [Push with Lease](#org8111154)
    7.  [Push with a Specific Ref](#org3a1e661)
    8.  [Push to Set Upstream Tracking](#orgb1147ce)
    9.  [Push with Verbose Output](#org3719cba)
11. [Git Merge Commands](#org301c9ee)
    1.  [Merge Another Branch into Current Branch](#org83454fd)
    2.  [Merge with a Specific Commit](#org9c8aabb)
    3.  [Merge with No Fast-Forward](#org38458e2)
    4.  [Merge with Squash](#org8cbc8dc)
    5.  [Merge with Strategy](#orgadcce97)
    6.  [Abort a Merge](#org75f3ee0)
12. [Git Rebase Commands](#org09ce845)
    1.  [Rebase the Current Branch onto Another Branch](#org465f3a7)
    2.  [Rebase Interactively](#org0502c1d)
    3.  [Continue a Rebase After Conflicts](#org09df405)
    4.  [Skip a Commit During Rebase](#org0398e70)
    5.  [Abort a Rebase](#org3ca2e0f)
    6.  [Rebase with Autosquash](#org7cecde1)
    7.  [Rebase with a Specific Strategy](#org17dcb0b)
    8.  [Rebase with No-FF](#orgf8e1c3c)
13. [Git Status Commands](#orgb431e07)
    1.  [Show Current Status](#orgf09672d)
    2.  [Show Status with Verbose Output](#org070244a)
    3.  [Show Status with Short Format](#org651ab96)
    4.  [Show Status with Porcelain Format](#orge9be64b)
    5.  [Show Status for a Specific Path](#org56873e3)
14. [Git Stash Commands](#org2fcc6b2)
    1.  [Stash Changes](#org08bb203)
    2.  [Stash with a Message](#org53b7edb)
    3.  [List Stashes](#org669d18b)
    4.  [Apply Stash](#org8b39fc5)
    5.  [Pop Stash](#orga117a3e)
    6.  [Drop a Stash](#orgdbb7b0a)
    7.  [Clear All Stashes](#org515f3b6)
    8.  [Stash Only Unstaged Changes](#orgfc9f0be)
    9.  [Stash Only Staged Changes](#orgb9a3d00)



<a id="org70b1225"></a>

# Initializing Git

git init


<a id="org8390a23"></a>

# Git Adding Commands


<a id="org44e8520"></a>

## Adding a file

git add file


<a id="org189441f"></a>

## Adding Every file

git add .


<a id="orge2c87a0"></a>

## Updating Already Staged files

git add -u (or) git add `--`update


<a id="org8465e65"></a>

## Save Change in the entire working directory

git add -a (or) git add `--`all


<a id="org41c9f69"></a>

# Git Branch Command


<a id="org65029e3"></a>

## List Branches

git branch


<a id="org160456b"></a>

## Create a New Branch

git branch (branch-name)


<a id="org2cecdaa"></a>

## Switch to a Branch

git checkout (branch-name)


<a id="org538a5b1"></a>

## Create and Switch to a new branch

git checkout -b (branch-name)


<a id="org3913f81"></a>

## Delete a Branch

git branch -d (branch-name)


<a id="org4f3d49c"></a>

## Force Delete a Branch

git branch -D (branch-name)


<a id="orgd25c328"></a>

## Rename a Branch

git branch -m (new-branch-name)


<a id="orged6e585"></a>

## Renaming Current Branch name

git branch -m (old-branch-name) (new-branch-name)


<a id="orgf555149"></a>

## Track Remote Branch

git branch `--`track (new-branch) (remote-branch)


<a id="orga7a9a61"></a>

## List All Branches (Local and Remote)

git branch -a


<a id="org0cb2501"></a>

## List Remote Branches

git branch -r


<a id="org46e9e99"></a>

# Git Checkout Commands


<a id="org67ba876"></a>

## Switch to an Existing Branch

git checkout (branch-name)


<a id="orgf3e452e"></a>

## Create and Switch to a New Branch

git checkout -b (new-branch-name)


<a id="orgeff1b82"></a>

## Switch to the Previous Branch

git checkout -


<a id="org909ad53"></a>

## Check Out a Specific Commit

git checkout (commit-hash)


<a id="org5138bef"></a>

## Restore a File from a Specific Commit

git checkout (commit-hash) `--` (file-path)

> This command checks out a specific file from a specific commit.


<a id="orge3d4d43"></a>

## Discard Changes in a File

git checkout `--` (file-path)

> This command discards changes in the specified file, restoring it to the last committed state. 


<a id="org74fe276"></a>

## Check Out a Remote Branch

git checkout -b (new-branch-name) (remote-name)/(branch-name)

> This command creates a new local branch tracking a remote branch and switches to it.


<a id="orgb90e494"></a>

# Git Commit Commands


<a id="orgfa859c0"></a>

## Commit with a Message

git commit -m "Your commit message"


<a id="org7c64531"></a>

## Commit All Changes

git commit -a -m "Your commit message"

> The -a option stages all modified and deleted files before committing, but it does not stage new untracked files.


<a id="org3f88a75"></a>

## Amend Last Commit

git commit `--`amend -m "Updated commit message"

> The -a option stages all modified and deleted files before committing, but it does not stage new untracked files.


<a id="orgf5f0f76"></a>

## Interactive Commit

git commit -p

> The -p (or `--`patch) option allows you to interactively select parts of files to commit. This is useful for breaking a large change into smaller, more meaningful commits.  


<a id="org76d8d65"></a>

## Detailed Commit Message

git commit

> This command opens the default text editor, allowing you to write a detailed, multi-line commit message.


<a id="org10d3e4b"></a>

## Sign-Off a Commit

git commit -s -m "Your commit message"

> The -s (or `--`signoff) option adds a Signed-off-by line at the end of the commit message. This is often used in projects that require a Developer Certificate of Origin (DCO).


<a id="org5516cbf"></a>

## Specify Author

git commit `--`author="Author Name (email@example.com)" -m "Your commit Message"


<a id="org0b41350"></a>

## Include Untracked Files

git commit -a -m "Your Allow Empty Commit message" -o


<a id="org7d88769"></a>

## Allow Empty Commit

git commit `--`allow-empty -m "Empty commit message"


<a id="orgfe74236"></a>

## Commit with GPG Signature

git commit -S -m "Your commit message"

> The -S (or `--`gpg-sign) option signs the commit with your GPG key, providing cryptographic proof that the commit was made by you.


<a id="org28881c2"></a>

## Commit Using a Template

git commit `--`template=(file)


<a id="orgdca5847"></a>

## Commit with Verbose Output

git commit `--`verbose


<a id="orgfd7f2b5"></a>

# Git Diff Commands


<a id="orgfe26c3a"></a>

## Show Changes in Working Directory

git diff


<a id="orgfec4df0"></a>

## Show Changes Between Staged Files and Last Commit

git diff `--`cached


<a id="orgca95cca"></a>

## Show Changes Between Working Directory and Last Commit

git diff HEAD


<a id="orgfca5e65"></a>

## Compare Two Commits

git diff (commit1) (commit2)


<a id="org160fd3a"></a>

## Compare a Commit with Working Directory

git diff (commit)


<a id="org032c4ea"></a>

## Compare Branches

git diff (branch1) (branch2)


<a id="org8a5f737"></a>

## Compare a File Between Two Commits

git diff (commit1) (commit2) `--` (file-path)


<a id="org550ff20"></a>

## Compare Staged Changes for a Specific File

git diff `--`cached `--` (file-path)

> This command shows the differences between the staged version of a specific file and the last commit.


<a id="org5743a60"></a>

## Show Differences with Color

git diff `--`color


<a id="orgedfd788"></a>

## Show Differences in Unified Format

git diff `--`unified=(num)


<a id="org97e6a33"></a>

## Show Differences with Word Granularity

git diff `--`word-diff

> This command shows differences at the word level rather than line level.


<a id="orgf5a7eda"></a>

## Show Differences with Stat Summary

git diff `--`stat

> This command provides a summary of changes, including the number of files changed, insertions, and deletions.


<a id="org745367f"></a>

# Git Log Commands


<a id="org7601d1a"></a>

## Git Log with decoration

git log `--`graph `--`oneline `--`decorate `--`all


<a id="org16eef07"></a>

## Git log with formatting

git log `--`graph `--`oneline `--`decorate `--`all


<a id="org07f5b7d"></a>

## Git log find by commit message

git log `--`all `--`grep="commit message"


<a id="org6078316"></a>

# Git Tag Commands


<a id="org9f8365b"></a>

## Normal Git Tagging

git tag (name)/(version)


<a id="org1ea9985"></a>

## Pushing Git tags

git push `--`tags


<a id="orgcd08fa7"></a>

## Delete Git Tag

git tag -d (name)/(version)


<a id="org59415b7"></a>

## Tagging with new tag name

git tag (new) (with commit hash)


<a id="orgc5f034b"></a>

## Pushing the Old Delete tag Update to Origin (local git / gitlab / github

git push origin :refs/tags/old tag name


<a id="orgd7b6fd7"></a>

# Git Pull Commands


<a id="org5726569"></a>

## Pull Changes from the Default Remote and Branch

git pull


<a id="org3188419"></a>

## Pull Changes from a Specific Remote and Branch

git pull (remote) (branch)


<a id="org4839e1e"></a>

## Rebase Instead of Merge

git pull `--`rebase

> This command fetches changes from the remote and rebases your local commits on top of the fetched changes instead of merging them. This can help keep a linear history.


<a id="orgf9e8362"></a>

## Pull with Verbose Output

git pull `--`verbose


<a id="orgf5a0e04"></a>

## Pull with Squash

git pull `--`squash

> This option prepares the changes from the remote branch for a single commit rather than merging them directly. You need to manually commit the squashed changes.


<a id="org1b99a64"></a>

## Pull with Specific Merge Strategy

git pull -s (strategy)

> This command specifies a merge strategy for integrating the fetched changes.


<a id="org0db9a2c"></a>

# Git Push Commands


<a id="org27e10ef"></a>

## Push Changes to the Default Remote Branch

git push


<a id="orgc81a80f"></a>

## Push Changes to a Specific Remote and Branch

git push (remote) (branch)


<a id="org8669712"></a>

## Push All Local Branches

git push `--`all


<a id="org8f578f9"></a>

## Push Tags

git push `--`tags


<a id="org8977ad0"></a>

## Push with Force

git push `--`force


<a id="org8111154"></a>

## Push with Lease

git push `--`force-with-lease

> This command forces the push but only if your local branch is up-to-date with the remote branch. It helps prevent overwriting changes that others might have pushed.


<a id="org3a1e661"></a>

## Push with a Specific Ref

git push (remote) (local-branch):(remote-branch)


<a id="orgb1147ce"></a>

## Push to Set Upstream Tracking

git push `--`set-upstream (remote) (branch)

> This command sets the specified remote branch as the upstream branch for the current local branch. It is useful for tracking branches and simplifying future push and pull commands.


<a id="org3719cba"></a>

## Push with Verbose Output

git push `--`verbose


<a id="org301c9ee"></a>

# Git Merge Commands


<a id="org83454fd"></a>

## Merge Another Branch into Current Branch

git merge (branch-name)

> This command merges the specified branch into the current branch.


<a id="org9c8aabb"></a>

## Merge with a Specific Commit

git merge (commit-hash)

> This command merges the changes from a specific commit into the current branch. This is less common but can be used for selective integration.


<a id="org38458e2"></a>

## Merge with No Fast-Forward

git merge `--`no-ff (branch-name)

> This command performs a merge without fast-forwarding, creating a merge commit even if the merge could be fast-forwarded. This is useful for keeping a record of the merge in the history.


<a id="org8cbc8dc"></a>

## Merge with Squash

git merge `--`squash (branch-name)

> This command combines all the changes from the specified branch into a single commit. It does not create a merge commit but instead prepares the changes for a new commit.


<a id="orgadcce97"></a>

## Merge with Strategy

git merge -s (strategy) (branch-name)

> This command specifies a merge strategy. Common strategies include recursive (default), ours, theirs, resolve, and octopus.


<a id="org75f3ee0"></a>

## Abort a Merge

git merge `--`abort

> If a merge conflict occurs and you decide not to continue with the merge, this command aborts the merge process and restores the working directory to the state before the merge.


<a id="org09ce845"></a>

# Git Rebase Commands


<a id="org465f3a7"></a>

## Rebase the Current Branch onto Another Branch

git rebase (branch)

> This command rebases the current branch onto the specified branch.


<a id="org0502c1d"></a>

## Rebase Interactively

git rebase -i (base-commit)

> This command starts an interactive rebase from a specified base commit.


<a id="org09df405"></a>

## Continue a Rebase After Conflicts

git rebase `--`continue

> After resolving conflicts during a rebase, use this command to continue the rebase process.


<a id="org0398e70"></a>

## Skip a Commit During Rebase

git rebase `--`skip

> This command skips the current commit that caused conflicts and continues with the rebase.


<a id="org3ca2e0f"></a>

## Abort a Rebase

git rebase `--`abort

> This command aborts the rebase process and returns your branch to its previous state before the rebase started.


<a id="org7cecde1"></a>

## Rebase with Autosquash

git rebase `--`autosquash

> This command automatically squashes commits marked with fixup! or squash! in the interactive rebase session.


<a id="org17dcb0b"></a>

## Rebase with a Specific Strategy

git rebase -s (strategy)

> This command specifies a merge strategy for rebasing. Strategies include recursive, ours, theirs.


<a id="orgf8e1c3c"></a>

## Rebase with No-FF

git rebase `--`no-ff

> This command forces a rebase without fast-forwarding, creating a new commit even if the rebase could be fast-forwarded.


<a id="orgb431e07"></a>

# Git Status Commands


<a id="orgf09672d"></a>

## Show Current Status

git status


<a id="org070244a"></a>

## Show Status with Verbose Output

git status `--`verbose


<a id="org651ab96"></a>

## Show Status with Short Format

git status `--`short


<a id="orge9be64b"></a>

## Show Status with Porcelain Format

git status `--`porcelain

> Provides a machine-readable output, which is useful for scripts. It outputs a status that’s easy to parse programmatically.


<a id="org56873e3"></a>

## Show Status for a Specific Path

git status (path)


<a id="org2fcc6b2"></a>

# Git Stash Commands


<a id="org08bb203"></a>

## Stash Changes

git stash

> This command stashes all the uncommitted changes in your working directory and the index (staged changes). By default, it stashes both modified and staged files.


<a id="org53b7edb"></a>

## Stash with a Message

git stash save "message"

> This command stashes changes with an optional message describing the stash.


<a id="org669d18b"></a>

## List Stashes

git stash list

> This command lists all stashes in your repository. Each stash is referenced by an index (e.g., stash@{0}).

<a id="org8b39fc5"></a>

## Apply Stash

git stash apply [(stash)]

> This command applies the most recent stash or a specific stash to your working directory without removing it from the stash list


<a id="orga117a3e"></a>

## Pop Stash

git stash pop [(stash)]

> This command applies the most recent stash or a specific stash and then removes it from the stash list.


<a id="orgdbb7b0a"></a>

## Drop a Stash

git stash drop [(stash)]

> This command removes a specific stash from the stash list.


<a id="org515f3b6"></a>

## Clear All Stashes

git stash clear

> This command removes all stashes from the stash list


<a id="orgfc9f0be"></a>

## Stash Only Unstaged Changes

git stash push -k

> This command stashes only the changes in your working directory, leaving staged changes as they are.


<a id="orgb9a3d00"></a>

## Stash Only Staged Changes

git stash push -p

> This command stashes only the staged changes, leaving the working directory as is.
