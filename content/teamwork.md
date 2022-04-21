---
title: Teamwork
---


## Submitting your changes

Now you have your changes on a branch, but the eventual goal is to get them back onto the trunk as part of the “official” codebase.

**Once you’ve tested your changes**, you’ll need to share them with the team. Typically you’ll do this via a pull request (PR) or a merge request (MR) — they’re the same thing, the term just depends on what software you’re using (e.g. GitHub/Bitbucket/GitLab). You’re requesting that your changes be pulled in and merged.

Most teams are happy to receive new PRs, even if the code needs a bit of work before being accepted. PRs are an important part of the open-source ecosystem.

The main thing to remember is to include a clear explanation of why you’re making the changes in order to give context.

## Discussing and revising

Once you submit your PR, someone else on the team will need to look it over and leave feedback. They can ask questions and comment on specific lines of code, or they can give more general feedback about your changes. In some cases they may push their own changes directly to your branch, but usually they’ll ask you to make the changes yourself.

If you want to make changes based on the feedback, simply add more commits to your existing branch and push it to origin again. The PR will update automatically to reflect your changes.

## Keeping up to date

If some time goes by before your PR is accepted, it might get “stale”, meaning it’s based on an older version of the trunk (like in the tree shown earlier). Your changes may have worked a week ago, but there’s no guarantee that they still work alongside other, more recent changes to the trunk.

To get up to date, you have two options:

You can “merge in” the changes using git merge master. This will apply any new changes from the trunk on top of your work.
You can “rebase on top of” the changes using git rebase master. This re-applies your work on top of any new changes on the trunk.
In either case, your own changes will still be the same — you’re effectively just moving your branch up to the top of the trunk to stay up to date with the latest code.

Different teams may prefer one method or the other; it’s safer and easier to merge.

## Dealing with conflicts

When merging or rebasing, you’ll occasionally run into conflicts. This means you changed a line of code that someone else also changed, and git doesn’t know which version to keep.

When this happens the output from git looks really nasty, with weird >>>>>>> ======= <<<<<<< symbols. Don’t worry! It looks strange, but with a bit of practice you’ll understand it.

In essence, you just need to remove those weird symbols and manually combine the code in between them.

For example, the line:

print "Hello"
Might be changed on two separate branches, leading to the conflict:

```bash
>>>>>>>
print "Hello, world"
=======
print "Hello!"
<<<<<<<
```

Which, when resolved, might become:

```bash
print "Hello, world!"
```

After manually merging the conflicting lines together — keeping both the “world” and the “!”, which had each been added separately.

## Accepting your changes

Once all of the PR comments have been addressed and any conflicts have been resolved, your branch is ready to be merged!

An administrator of the codebase can accept the PR by merging your branch into the trunk — simply by pressing a button on GitHub — thus making your changes official.
