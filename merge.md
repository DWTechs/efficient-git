---
layout: default
title: Merge
permalink: /merge/

---


# git-merge

Join two or more development histories together.

## Description

Incorporate changes from the named commits (since the time their histories diverged from the current branch) into the current branch. This command is used by git pull to incorporate changes from another repository and can be used by hand to merge changes from one branch into another.

## Pre-merge checks

Before applying outside changes, you should get your own work in good shape and committed locally, so it will not be clobbered if there are conflicts (See also git-stash). 

Git pull and git merge will stop without doing anything when local uncommitted changes overlap with files that git pull/git merge may need to update.

To avoid recording unrelated changes in the merge commit, git pull and git merge will also abort if there are any changes registered in the index relative to the HEAD commit. (Special narrow exceptions to this rule may exist depending on which merge strategy is in use, but generally, the index must match HEAD.)

If all named commits are already ancestors of HEAD, git merge will exit early with the message "Already up to date."

## True merge

the branches to be merged must be tied together by a merge commit that has both of them as its parents.

A merged version reconciling the changes from all branches to be merged is committed, and your HEAD, index, and working tree are updated to it. It is possible to have modifications in the working tree as long as they do not overlap; the update will preserve them.

When it is not obvious how to reconcile the changes, the following happens:

1. The HEAD pointer stays the same.
2. The MERGE_HEAD ref is set to point to the other branch head.
3. Paths that merged cleanly are updated both in the index file and in your working tree.
4. **For conflicting paths**, the index file records up to three versions: stage 1 stores the version from the common ancestor, stage 2 from HEAD, and stage 3 from MERGE_HEAD (you can inspect the stages with git ls-files -u). The working tree files contain the result of the "merge" program; i.e. 3-way merge results with familiar conflict markers <<< === >>>.

No other changes are made. In particular, the local modifications you had before you started merge will stay the same and the index entries for them stay as they were, i.e. matching HEAD.

**If you tried a merge which resulted in complex conflicts and want to start over, you can recover with git merge --abort.**

## How to resolve conflicts

After seeing a conflict, you can do 2 things:

Decide not to merge. The only clean-ups you need are to reset the index file to the HEAD commit. git merge --abort can be used for this.

Resolve the conflicts. Git will mark the conflicts in the working tree. Edit the files into shape and git add them to the index. Use git commit or git merge --continue to seal the deal. The latter command checks whether there is a (interrupted) merge in progress before calling git commit.

You can work through the conflict by looking at the diffs.

Git diff will show a three-way diff, highlighting changes from both the HEAD and MERGE_HEAD versions.

## How to merge

Always start by merging from the main branch to the child branch.

### Example 1

If you need to merge your working branch manually into "develop".

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

```bash
git checkout develop
git pull 
```

Git pull makes sure you are still up to date. If not repeat step 1.

```bash
git merge --no-ff <working-branch-name>
git push
```

### Example 2

Another example when merging develop into master
This type of merge should be done by a lead dev only.

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

### Step 2 : Test your updated develop branch 

If the application runs properly you can safely merge your branch into master knowing there will be no conflicts anymore

### Step 3 : Merge develop into master

```bash
git checkout master
git pull 
```

Git pull makes sure you are still up to date. If not repeat step 1.

```bash
git merge --no-ff develop
git push
```

You can also use Gitlab graphics interface to merge while keeping the same order.



