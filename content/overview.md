---
title: Getting Started
---

## Create a repo

In a new folder on your computer type :

```bash
git init
```

This will create a hidden .git folder inside your current folder — this is the "repository" (or repo) where git stores all of its internal tracking data.
Any changes you make to any files within the original folder will now be possible to track.

The original folder is now referred to as your **working directory**, as opposed to the repository (the .git folder) that tracks your changes. You work in the working directory.

## Clone an existing repo

```bash
git clone https://github.com/xxx/xxxx.git
```

This will download a .git repository from the internet (GitHub) to your computer and extract the latest snapshot of the repo (all the files) to your working directory. By default it will all be saved in a folder with the same name as the repo.

The URL you specify here is called the **remote origin**. The place where the files were originally downloaded from.

## Status of your project

```bash
git status
```

This will print current state information of the branch, such as which files have recently been modified.

Here is the list of possible outputs for a file :   

| Name | Description |
|------|-------------|
| M | Modified |
| T | File type changed (regular file, symbolic link or submodule) |
| A | Added |
| D | Deleted |
| R | Renamed |
| C | Copied |
| U | Updated but unmerged |

You should check your status anytime you are about to do git commands.

## Create a new branch

```bash
git branch <new-branch-name>
```

You can think of this like creating a local “checkpoint” (technically called a reference) and giving it a name. It’s similar to doing File > Save as… in a text editor; the new branch that gets created is a reference to the current state of your repo. The branch name can then be used in various other commands as you’ll soon see.

*Commits are also checkpoints called a revision. The name will be a random-looking hash of numbers and letters such as e093542. This hash can then be used in various other commands just like branch names.*

When working on a project, every time you start a new feature or bug fix, you create a new branch from develop, release or master/main. Depending on the work you have to do and the moment in the sprint.

For more info about creating branches please refer to [Gitflow/branch](../branch).


## Check out a branch

Switch to an existing branch

```bash
git checkout <existing-branch-name>
git pull
```

You can think of this like “resuming” from an existing checkpoint. All your files will be reset to whatever state they were in on that particular branch.

Keep in mind that any changes in your working directory will be kept around. Preventing you to switch branche. See git stash if you’re interested in a simple way to avoid unwanted commits.

You can use the -b flag as a shortcut if you want to create the new branch while check it out all in one step. This is quite common:

```bash
git checkout -b <new-branch-name>
```

View the differences between checkpoints:

```bash
git diff <branch-name> <other-branch-name>
```

After editing some files, you can simply type git diff to view a list of the changes you’ve made. This is a good way to double-check your work before committing it.

For each group of changes, you’ll see what the file used to look like (prefixed with - and colored red), followed by what it looks like now (prefixed with + and colored green).

See further down for more advanced examples of this command.

## Stage your changes

Tell Git which files should be included in your next commit:

```bash
git add <files>
```

After editing some files, this command will mark any changes you’ve made as “staged” (or “ready to be committed”).

If you then go and make more changes, those new changes will not automatically be staged, even if you’ve changed the same files as before. This is useful for controlling exactly what you commit, but also a major source of confusion for newcomers.

If you’re ever unsure, just type git status again to see what’s going on. You’ll see “Changes to be committed:” followed by file names in green. Below that you’ll see “Changes not staged for commit:” followed by file names in red. These are not yet staged.

As a shortcut, you can use wildcards just like with any other terminal command. For example:

```bash
git add README.md app/*.txt
```

This will add the file README.md, as well as every file in the app folder that ends in .txt. 

You can also add everything that’s changed like this : 

```bash
git add --all
```

## Commit your staged changes

This will open your default command-line text editor and ask you to type in a commit message. As soon as you save and quit, your commit will be saved locally.

The commit message is important to help other people understand what was changed and why you changed it. There’s a brief guide [here](/gitflow/conventional-commit/) explaining how to write useful commit messages.

You can use the -m flag as a shortcut to write a message. For example:

```bash
git commit -m "<conventional-commit-message>"
```

## Push your branch on the server

This will upload your branch to the remote named origin (remember, that’s the URL defined initially during clone).

After a successful push, your teammates will then be able to pull your branch to view your commits (see git pull below).

```bash
git push
```

## Fetch the latest info about a repo

```bash
git fetch
```

This will download the latest info about the repo from origin (such as all the different branches stored on GitHub).

It doesn’t change any of your local files — just updates the tracking data stored in the .git folder.

## Merge in changes from somebody else

```bash
git merge <other-branch-name>
```

This will take all commits that exist on the other-branch-name branch and integrate them into your own current branch.

This uses whatever branch data is stored locally, so make sure you’ve run git pull first to download the latest info.

You can use the pull command to both fetch and merge all in one step.

For a deeper understanding of how merging works and how conflicts are resolved [see the merge docs](../merge/).
