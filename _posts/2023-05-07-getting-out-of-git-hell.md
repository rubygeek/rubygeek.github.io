---
layout: post
title: Getting out of Git Hell
date: 2023-05-07
categories: [git]
tags: [githell, ramble]
---

The other day I found myself in the midst of A Bad Commit and the anger of other folks on the team - yeah yeah, I'll fix it. Normally if it was my own repo whee I don't care about the pristine commit history, i would script the PR and/or the branch and start over with a fresh update from master. However, that is just myself being lazy. Surely it can be fixed the right way.

## PROTIP

Before reading any blog posts or phoning in reinforcements, do this:

```
git remote -v
```

Different teams assign "origin" to different things. Some "its my master in my fork" or "its the master in the original repo" Just make sure where things are going before you start following directions. Don't ask me how I know.

## Digging

Here's how to fix a bad commit.

Work on a copy of your bad branch so you can change your mind later!

Get the sha of the last good point - lets all it `brisket`.

```
git diff --name-only `brisket`
```

Confirm those are the files that were added by accident

Armed with that knowledge lets remove files we don't want from the commit

```
git reset `brisket` [file 1] [file 2]
```

Now commit this !!!

```
git commit -m "reset files that should not be"
```

Then, do this

```
git log --oneline
```

We need to smoosh the commit so nobody can see our messup (I guess, with reflog there are no secrets but lets hope nobody is digging that hard)

```
git rebase HEAD~2
```

use `f for fixup`, discarding our stupid message about resetting files

git push origin myawesomebranch

(or whatever remote name you want) .. you may want to use force or I recently learned about `--force-with-lease` which might be good to learn to use.

I made this mostly as note to my future self when I foobar a commit but maybe it will help you.
