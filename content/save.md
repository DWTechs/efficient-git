---
title: Save
---

Git is not meant to be used as a backup device.

But let's be pragmatic here as not every company has a proper way of backuping developers work every day.

As said before the core function of Git is to save checkpoints. And it has all the tools to recover from it very easily.
Meaning that, if used properly, Git is a poweful backup application for developers and can save you from losing several days of work.

## Overview

This backup routine should be done every evening when you leave work.
And every morning when you start your day in order to recover your work as you left it the day before. 


## Step 1: Save your work

You are leaving for the day. Time to backup your work in case your computer does not start tomorrow morning.
This commands only work if it is the first time you are saving your work on this branch. If it is not the case please jump to step three.

```bash
git status
git add .
git commit -m "WIP"
git push
```

## Step 2: Retrieve your backup

The day after you want to retrieve the same state as ealier.
For this you have to reset your backup commit.

If your computer died during the night and is not starting up anymore, you can pull your save to another computer and work as nothing happened.

But hopefully, most of the time, you will not have any issue during the night, the next morning you just need to reset your commit on your local branch:

```bash
git reset --soft HEAD~1
```

Now your backup commit is reset in the local repository. You can start your work as you left it.
Keep in mind the remote did not reset so your local repository is late by one commit.


## Step 3: Save your work again after a previous backup

This is the end of the second day working on this feature.
You want to backup again before leaving for the day : 

```bash
git status
git add .
git commit -m "WIP"
git push --force
```
test

At this point "git push" cannot work because the remote is ahead of the local repository by 1 commit. Which is the backup commit you did yesterday.

<!-- **This will create two commits for each backup**. One for the backup and one for the revert.
So don't forget to squash your commits when your work is finished. -->

## Finish your work

Once this feature is done. Commit as usual then create your merge request with the squash option checked.
