---
layout: default
permalink: /tag/

---


# Tagging

Git has the ability to tag specific points in a repository’s history as being important.
It is used to mark release points (v1.0, v2.0 and so on).

## Listing Your Tags

```bash
git tag
```

This command lists the tags in alphabetical order; the order in which they are displayed has no real importance.

You can also search for tags that match a particular pattern. The Git source repo, for instance, contains more than 500 tags. If you’re interested only in looking at the 1.8.5 series, you can run this:

```bash
git tag -l "v1.8.5*"
```

## Create annotated Tags

You can use Gitlab graphics interface to create a tag.

Annotated tags are stored as full objects in the Git database. They’re checksummed; contain the tagger name, email, and date; have a tagging message; and can be signed and verified with GNU Privacy Guard (GPG). It’s generally recommended that you create annotated tags so you can have all this information; but if you want a temporary tag or for some reason don’t want to keep the other information, lightweight tags are available too.

```bash
git tag -a v1.4 -m "my version 1.4 is cool"
```

You can see the tag data along with the commit that was tagged by using the git show command:

```bash
git show v1.4
```

## Checking out

If you want to view the versions of files a tag is pointing to, you can do a git checkout of that tag, although this puts your repository in “detached HEAD” state, which has some ill side effects.

```bash
git checkout v2.0.0
```

Once a versioned package has been released, the contents of that version MUST NOT be modified. Any modifications MUST be released as a new version.
