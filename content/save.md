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

## Save your work

You are leaving for the day. Time to backup your work in case your computer does not start tomorrow morning.

```bash
git status
git add .
git commit -m "WIP"
git push
```

## Retrieve your backup

The day after you want to retrieve the same state as ealier.
For this you have to revert your backup commit.

### Revert

```bash
reset --hard HEAD~3
git push
```

Now your backup commit is reverted in the remote and the local repositories. You can start your work as you left it.

**This will create two commits for each backup**. One for the backup and one for the revert.
So don't forget to squash your commits when your work is finished.

## Finish your work

Once your work is done. Commit as usual then create your merge request with the squash option checked.
