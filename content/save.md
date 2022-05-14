---
title: Save
---

Git is not meant to be used as a backup device.

But let's be pragmatic here as not every company has a proper way of backuping developers work every day.

As said before the core function of Git is to save checkpoints. Thus it has all the tools to recover from it very easily.
Meaning that, if used properly, Git is a poweful backup application for developers and can save you from losing several days of work in case of problem.

## Overview

This backup routine should be done every evening when you leave work.
And every morning when you start your day in order to recover your work as you left it the day before. 

Note that you only need to do this if your current work if sufficiently started since the last commit and the current state is not mature enough for a proper intermediary conventional commit.
**If you can commit properly just do it and push.**

## Step 1: Save your work

You are leaving for the day and started to work on a new branch today. Your job is not finished yet, you want to continue tomorrow. It is then time to backup your work in case your computer does not start tomorrow morning.
This commands only work if it is the first time you are saving your work on this branch. If it is not the case please jump to step 3.

```bash
git status
git add .
git commit -m "WIP"
git push
```

Your work is safe.


## Step 2: Retrieve your backup

The day after you want to retrieve the same state as ealier.
For this you have to reset your backup commit.

If your computer died during the night and is not starting up anymore, you can pull your save to another computer and work as nothing happened.

But hopefully, most of the time, you will not have any issue during the night. The next morning you then need to reset your commit on your local branch:

```bash
git reset HEAD~1
```

Now your backup commit is reset in the local repository. You can keep working on your branch as you left it.
**Keep in mind the remote did not reset so your local repository is late by one commit.**


## Step 3: Save your work again after a previous backup

This is the end of the second day working on this feature.
You want to backup again before leaving for the day.

As usual you want to pull your remote branch to make sure you are up to date.
But As said earlier your local branch has diverged in step 2.
You need to stash your work first in order to pull the remote.


```bash
git stash
git pull 
git stash apply
```


"git stash apply" may generate conflicts as your local branch diverged from remote in step 2. Fix them by "using the current" state as this is the work you have made lately. then continue with the usual commands.

```bash
git status
git add .
git commit -m "WIP"
git push 
```

<**This will create a commit for each backup**. So don't forget to squash your commits when your work is finished.

## Step 4: Finish your work

Once this feature is done. Commit is following step 3 and create your merge request with the squash option checked.
