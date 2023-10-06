---
title: "Solving Git Pull Origin Warning"
description: "How to deal with this git warning? \"Pulling without specifying how to reconcile divergent branches is discouraged\"."
pubDate: "May 20, 2021"
heroImage: "/unsplash_yancy_min.jpeg"
---

## TL;DR

Execute any of the following:

`git config --global pull.rebase false` or `git config pull.rebase false`

`git config --global pull.rebase true` or `git config pull.rebase true`

`git config --global pull.ff only` or `git config pull.ff only`

For more references: https://git-scm.com/docs/git-pull

## Back Story

I was updating my local repository and wanted to make sure my repository is up-to-date with the `master` or `main` branch. Then got the following warnings:

```
hint: Pulling without specifying how to reconcile divergent branches is
hint: discouraged. You can squelch this message by running one of the following
hint: commands sometime before your next pull:
hint:
hint: git config pull.rebase false # merge (the default strategy)
hint: git config pull.rebase true # rebase
hint: git config pull.ff only # fast-forward only
hint:
hint: You can replace “git config” with “git config — global” to set a default
hint: preference for all repositories. You can also pass — rebase, — no-rebase,
hint: or — ff-only on the command line to override the configured default per
hint: invocation.
```

### Google is our friend (privacy not included)
So I started searching for what rebase and fast-forward means. So here it is:

#### merge (the default strategy)
`git config pull.rebase false` - This keeps the default behavior and suppresses the warning.

#### rebase
`git config pull.rebase true` - This actually commits on top of the remote branch, maintaining a single branch both locally and remotely (unlike the default behaviour where two different branches are involved — one on local and the other on remote — and, to combine the two, a merge is performed).

#### fast-forward only
`git config pull.ff only` - This only performs the pull if the local branch can be fast-forwarded. If not, it simply aborts with an error message (and does not create any commits).

## Get Involved
I'm not a fan of a paywall. However, if this helped you, consider donating for coffee... or pizza.
https://ko-fi.com/hmenojr