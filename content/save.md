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

## Step 1 : Save your work

You are leaving for the day. Time to backup your work in case your computer does not start tomorrow morning.
This commands only work if it is the first time you are saving yout work on this branch. If it is not the case please jump to step three.


```bash
git status
git add .
git commit -m "WIP"
git push
```

## Step 2 : Retrieve your backup

The day after you want to retrieve the same state as ealier.
For this you have to revert your backup commit.

### Reset

If your computer died during the night and is not starting up anymore, you can pull your save from another computer and work as nothing happened.

But hopefully most of the time you will not have any issue during the night. So the next morning you just want to get back to the state you were the day before. to reset your commit on your local branch do the following : 

```bash
git reset --soft HEAD~1
```

Now your backup commit is reset in your local repository. You can start your work as you left it.
Keep in mind the remote did not reset so your local repository is late by one commit.

## Step 3 : Save your work again after a previous backup 

This commands only work if it is not the first time you are saving your work on this branch and you retrieved your backup using step 2.

```bash
git status
git add .
git commit -m "WIP"
```

At this point "git push" cannot work because the remote is ahead of the local repository by 1 commit. Which the backup commit you did yesterday.


<<<<<<< HEAD
=======

>>>>>>> 5b441e22288a136804138ab6e0caa921fa10e76c

**This will create two commits for each backup**. One for the backup and one for the revert.
So don't forget to squash your commits when your work is finished.

## Finish your work

Once your work is done. Commit as usual then create your merge request with the squash option checked.
