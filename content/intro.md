---
title: What is Git
---

**Git** is the most popular Version Control System.  
It makes it easier to track changes to files in a project.  
You can determine exactly what changed, who changed it, and why.

## Checkpoints

**The core function of git is to save checkpoints (revisions)** and share them with other people. Everything revolves around this concept.
If you’ve ever created a checkpoint to something, you’ll be able to get back to it later as long as your .git folder is intact.

**It is mandatory for coordinating work among multiple people on a project**, and for tracking progress over time by saving those checkpoints. 

Here’s a list of the different types of checkpoint :

```
HEAD, e.g. a ref that points to the tip (latest commit) of a branch
<branch-name>, e.g. master
<commit-hash>, e.g. e093542d01d11c917c316bfaffd6c4e5633aba58 (or e093542 for short)
<tag-name>, e.g. a release version : v1.0.0
```

## Tree

You can think of your main codebase as the trunk of a tree.

Every time you add more changes (aka commits), your tree grows taller, straight up. Even if you delete code, that’s still considered a change and causes the tree to grow.

### Trunk

Git, by default, calls the trunk main or master. You can call it whatever you want; there’s nothing special about these words other than that it’s conventional.

You can travel up and down the trunk — equivalent to going forward and backward in time — by checking out specific “checkpoints” as described in [the overview](./overview).

### Branches

Most projects have a backlog of new features to add and bugs to fix. When you want to address one of these issues, one way would be to grow the tree taller and commit directly to the trunk (master). This works fine for small projects or projects where you are the only person making changes, but what if multiple people are working at the same time? It’s too easy to get in each other’s way and end up with conflicting changes.

The solution is branching. Instead of committing to the trunk, you [create your own personal branch](./branch) (e.g. my-cool-feature) and work from there. Now with each commit you are growing your branch taller instead of the trunk.

Let's say your branch started at commit T2 from "develop". While you were working on your branch (commits B1 and B2), someone else worked directly on develop (commits T3 and T4). Those commits aren’t in your branch yet; your branch is out of date but isolated and safe from possible issues.

You can see branch visualization by typing :

```bash
git log --all --decorate --oneline --graph
```

or the short version if you added [aliases from this documentation](./alias)

```bash
git l
```
