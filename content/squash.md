---
title: Squash  
---

## What is Git Squash

Squashing in Git is the process of merging several commits into one. 

## Why would I want to squash my commits

Often when we are working on a feature / bug fix / refactor etc, we may find ourselves making several interim commits over the duration of the change. Whilst we can push back to our main branch including all of these commits, this creates noise in the commit history potentially making it harder to identify the actual commit we are interested in.

## How do I Squash my commits

Git does not have a specific command to squash commits instead we make use of existing git commands.

## git merge <branch> --squash

"git merge <branch> --squash" allows us to merge one branch into another whilst condensing the commit history on the branch we are merging. It does this by creating a new commit and adding our changes to this commit, but stops before making the actual commit leaving us to add the clean commit message.

The following example assumes you have the ability to merge into develop and push this change back to the develop branch. In practice and on many projects pushing directly to any of the "main" application branches will be blocked and in these cases the merge squash feature should be used in tools like github and gitlab.
You can [read more about squashing](./teamwork/#squash-merge) using Github or Gitlab.

In the following example we have been given the task to create a "fab-feature" and so the first thing we might do is create our new branch assuming we already have pulled recent changes from the main repo.

```
git checkout -b feature/fab-feature
```

on checking the log we might see something like this

```
git log
commit 2ff6bd (HEAD -> /fab-feature)

  feature/fab-feature

commit 905F7D

  feature/great-feature

commit 0DE673 (origin/develop)
  
  intial commit

```

We would then start work on Fab-feature, at some point we will have completed the work and are ready to merge back to our main branch in this case "develop", however during the development we made several interim commits.

To keep the develop branch clean we want to get rid of the commit history and register a single commit comment which makes it clear for other people what this commit related to.

Our commit history on our fab-feature branch might look something like this.

```
git log
commit 5ef6bd (HEAD -> feature/fab-feature)

  implemented fab feature

commit c675F7D

 adding tests for fab feature

commit 98DE673
  
  working on fab feature

commit 65EF5F

  started work on fab feature

```

To squash these commits we first need to checkout the branch we want to merge into, in this case the "develop" branch

```
git checkout develop
```

to merge our changes from the feature/fab-feature branch and squash the commit history we use

```
git merge feature/fab-feature --squash
```

This should merge our feature branch back into develop and squash our commit history. 

At this stage it is important to note git has not committed this merge for us, we must do this by adding a final commit message that we want to remain in develop branch history. This message should represent the feature we have just worked on:

```
git commit -m "feature/fab-feature" 
```

at the end of this process our log would look like this:

```
git log
commit 2ff6bd (HEAD -> develop)

  feature/fab-feature

commit 905F7D

  feature/great-feature

commit 0DE673 (origin/develop)
  
  intial commit

```

Note our feature branch will still retain the git history for that branch until we delete the branch.