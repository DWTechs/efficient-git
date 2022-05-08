---
title: Wip
---

Here is a useful tip for listing all your current branches with their last update time.

## Edit your git config file

If it is located in your home folder and you are using nano, you can do so:

```bash
nano ~/.gitconfig
```

Otherwise, pick the editor of your choice and the right location of the file.

If you don't have this config file already, create it:

```bash
touch ~/.gitconfig
```

## Add the wip alias

Add the following lines to the config file (if you already have a [alias] section, just add the alias):

```vim
[alias]
wip= for-each-ref --sort='authordate:iso8601' --format=' %(color:green)%(authordate:relative)%09%(color:white)%(refname:short)' refs/heads
```

## Use it

All you have to do now is typing `git wip` in your terminal.

```bash
git wip
```

![gitwip](../img/gitwip.png "git wip example screenshot")
