---
title: Squash  
---


## What is Git Squashing

Squashing in Git is the process of merging several commits into one. 

## Why would I want to squash my commits

Often when we are working on a feature / bug fix / refactor etc we may find ourselves making several interim commits over the duration of the change. Whilst we can push back to our main branch including all of these commits this creates noise in the commit history potentially making it harder to identify the actual commit we are interested in.

## How do I Squash my commits

Git does not have a specific command to squash commits instead we make use of existing git commands to achieve a squash.

There are two ways to achieve this one using rebase and the other

## rebase

Using a hypothetical example the first step to squashing our commits is to issue a git log

as in 
```bash
git log
```
this will show the commit history, we can narrow this down to the commits we have made by using the --commiteer followed by the persons name  e.g. 
```bash
git log --committer mark
```
or with a date range 
```bash
git log --since 2022-04-21
```

![example output using git log](../static/images/git-log.png)

In the above example we see 5 commits which are displayed in sequential order starting with the most recent. We would like to squash the 5 commits down to the single most recent commit to do this we use

```bash
git rebase
```



