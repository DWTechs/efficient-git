---

---

Join two or more development histories together.

## Description

Incorporate changes since the time their histories diverged from your branch into the main branch. This command is actually used by git pull to incorporate changes from another repository and can be used by hand to merge changes from one branch into another.

## Pre-merge checks

Before applying outside changes, you should get your own work in good shape and committed locally, so it will not be clobbered if there are conflicts (See also git-stash). 

Git pull and git merge will stop without doing anything when local uncommitted changes overlap with files that git pull/git merge may need to update.

If all named commits are already ancestors of HEAD, git merge will exit early with the message "Already up to date."


## How to resolve conflicts

After seeing a conflict, you can do 2 things:

Decide not to merge. 
**If you tried a merge which resulted in complex conflicts and want to start over, you can recover with git merge --abort.**

Resolve the conflicts. Git will mark the conflicts in the working tree. Edit the files into shape and git add them to the index. Use git commit or git merge --continue to seal the deal. The latter command checks whether there is a (interrupted) merge in progress before calling git commit.

You can work through the conflict by looking at the diffs.

Git diff will show a three-way diff, highlighting changes from both the HEAD and MERGE_HEAD versions.

You can learn more about resolving conflict in the [Teamwork page](../teamwork)

## How to merge

Always start by merging from the main branch to the child branch.


## Get your branch up to date

During the development of a feature you can spend several days working on your branch created from develop.
Everyday your colleagues will push their own work into develop, making your branch late by several commits.
It is important to keep your branch up to date by merging develop into your branch regularly.

Once your branch is ready do the following :

```bash
git checkout develop
git pull
git checkout <working-branch-name>
git merge --no-ff develop
```
Fix conflicts if needed into your IDE

```bash
git merge --continue
```

Your branch is now up to date.
If the application runs properly you can safely keep working on your branch

### merge into develop

You need to merge your working branch manually into "develop".
**You don't.**
**Only tech leads are allowed to merge directly into develop.** Please refer to "merge requests" 

{{< button relref="/tag" size="small" >}}Learn more about merge request{{< /button >}}

Tech lead will do the following : 

#### Step 1 : Start by merging develop into your working branch like this : 

```bash
git checkout develop
git pull
git checkout <working-branch-name>
git merge --no-ff develop
```
Fix conflicts if needed into your IDE

```bash
git merge --continue
git push
```

#### Step 2 : Test your updated branch 

If the application runs properly you can safely merge your branch into develop knowing there will be no conflicts anymore

#### Step 3 : Merge your branch into develop

Make sure you are still up to date. If not repeat step 1:

```bash
git checkout develop
git pull 
```

```bash
git merge --no-ff <working-branch-name>
git push
```

### merge release into master

This is the end of the sprint.
Release branch is going to be released to the client.

Again, **Only tech leads are allowed to merge into develop.** 

#### Step 1 : Start by merging master into develop like this : 

```bash
git checkout master
git pull
git checkout develop
git merge --no-ff master
```
Fix conflicts if needed into your IDE

```bash
git merge --continue
git push
```

### Step 2 : Test your updated release branch 

If the application runs properly you can safely merge release into master knowing there will be no conflicts anymore

### Step 3 : Merge release into master

```bash
git checkout master
git merge --no-ff develop
git push
```

At this point you can tag master xith the updated version number. 

{{< button relref="/tag" size="small" >}}Learn more about tagging{{< /button >}}

Repeat the process to push release into develop.

You can also use Gitlab graphics interface to merge while keeping the same order.



