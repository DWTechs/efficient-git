---
title: Squash  
---

## What is Git Squashing

Squashing in Git is the process of merging several commits into one. 

## Why would I want to squash my commits

Often when we are working on a feature / bug fix / refactor etc, we may find ourselves making several interim commits over the duration of the change. Whilst we can push back to our main branch including all of these commits this creates noise in the commit history potentially making it harder to identify the actual commit we are interested in.

## How do I Squash my commits

Git does not have a specific command to squash commits instead we make use of existing git commands to achieve a squash.


## rebase

Using a hypothetical example the first step to squashing our commits is to issue a git log

as in 
```bash
git log
```
this will show the commit history, we can narrow this down to the commits we have made by using the --committer followed by the persons name  e.g. 
```bash
git log --committer <username>
```
or with a date range 
```bash
git log --since 2022-04-21
```

![example output using git log](../git-log.png)

In the above example we see 5 commits which are displayed in sequential order starting with the most recent. These commits contain various work in progress steps which have no real meaning in the context of our overall project, i.e. we are only interested in the final commit which is adding the new feature. Before we commit this branch back to origin we would like to get rid of all these interim commits and present one single clean commit representing the new feature we have added. As an added bonus this makes us look like a genius developer who built the feature at the first attempt.

To do this we can issue the git rebase command 

```bash
git rebase -i <branch>
```


Where n is the number of commits from and including the current head we want include in the rebase. (current head = 1)

The -i switch says rebase using interactive mode, which gives us control over which commits to squash.

We need to tell git which branch we are rebasing to, in the example below we will rebase back to the develop branch:

```bash
git rebase -i develop
```

On issuing the command a "vi" editor will launch and show us the list of our commits with a command in front of each:

![vi editor showing git rebase](../static/rebase-i.png)

We can now choose which commits to keep (pick) and which commits to squash, **with the exception of the first commit** which we have to keep, as we need one commit to squash everything to.

We can now edit the text and choose which commits to keep aside from the first and which to squash.

![editor with selected commits](../static/rebase-selection.png)

In the example above we have chosen to squash the last four commits, and used the reword "r" command on the first commit to change the commit message to something more meaningful for our commit history, whilst retaining the actual commit.

Once we have made the selection we can save and exit the editor <:wq>.

Git will reopen the editor again this time showing the final commit message. We should check this and remove any content we do not want in our final commit, sometimes we will see the history of commit messages, these can be removed.

Save and quit the editor, git will now perform the rebase and once complete if we issue the git log command again our branch should only have the one commit:

![clean log](../static/rebase-resulting-log.png)

At this point we can now push our branch back to our branch in our case "feature/amazing-feature" and raise a pull request- to merge into develop.

```bash
git push origin -u feature/amazing-feature
```

{{< hint danger >}}
**Note:** rebasing should only be done on your local branch and never against the remote branch unless you truly understand what you are doing.
{{</hint>}}

Aside from rebasing to a branch we can also rebase to the current HEAD using

```bash
git rebase -i HEAD~<n>
```
This allows us to perform a rebase at any stage allowing us to keep our local commit tree clean, but should be used with caution as we will not be able to revert back to a previous commit if it has been squashed.
