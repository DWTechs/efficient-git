---
title: What is Git
---

**Git** is the most popular Version Control System.  
It makes it easier to track changes to files in a project.  
You can determine exactly what changed, who changed it, and why.

**The core function of git is to save checkpoints (revisions)** and share them with other people. Everything revolves around this concept.
If you’ve ever created a checkpoint to something, you’ll be able to get back to it later as long as your .git folder is intact.

**So everything in git can be thought of as a checkpoint**. Here’s a list of the types of checkpoint :

```
HEAD
<branch-name>, e.g. master
<commit-hash>, e.g. e093542d01d11c917c316bfaffd6c4e5633aba58 (or e093542 for short)
<tag-name>, e.g. v1.0.0
```

**It is mandatory for coordinating work among multiple people on a project**, and for tracking progress over time by saving “checkpoints”.  


## Starting from the trunk

Git uses a lot of “tree” analogies. You can think of your main codebase as the trunk of a tree.

Every time you add more changes (aka commits), your tree grows taller, straight up. Even if you delete code, that’s still considered a change and causes the tree to grow. It’s like how the “undo” history in a text editor saves your keystrokes, including backspace.

Git, by default, calls the trunk main or master. You can call it whatever you want; there’s nothing special about these words other than that it’s conventional.

You can travel up and down the trunk — equivalent to going forward and backward in time — by checking out specific “checkpoints” as described in [the overview](./overview).

## Branching out

Most projects have a backlog of new features to add and bugs to fix. When you want to address one of these issues, one way would be to grow the tree taller and commit directly to the trunk (master). This works fine for small projects or projects where you’re the only person making changes, but what if multiple people are working at the same time? It’s too easy to get in each other’s way and end up with conflicting changes.

The solution is branching. Instead of committing to the trunk, you create your own personal branch (e.g. my-cool-feature instead of master) and work from there. Now you’re growing your branch taller instead of the trunk.

Let's say your branch started at commit T2 from "develop". While you were working on your branch (commits B1 and B2), someone else worked directly on develop (commits T3 and T4). Those commits aren’t in your branch yet; your branch is out of date.

You can also see real life branch visualizations on GitHub, or by typing :

```bash
git log --all --decorate --oneline --graph
```

