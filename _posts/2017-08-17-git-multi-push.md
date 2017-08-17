---
layout: post
title:  "Syncing multiple git remotes"
date:   2017-08-17 12:40:40 -0400
categories: git
---

I have a few git projects that use multiple remotes. In some cases one of the remotes contains public code while another contains all the public code plus perhaps a few private branches. If I make changes to the public code base, I want to push the changes to both the public and private remotes, but changes to the private branches should only push to the private remote. With git, you can configure a remote to have multiple push targets to accomplish the task.

My workflow was inspired by a post on how to configure [multiple push remotes](http://blog.deadlypenguin.com/blog/2016/05/02/git-push-multiple-remotes/).

We begin by create a remote that fetches from the public repo, but will eventually push to the public and private repos. Assume that the private repo was initially forked from the public repo, but may now have additional branches not found in the public repo.

```
git remote add both git@github.com/user/public-repo
```

Now we will add two push URLS

```
git remote set-url --add --push git@github.com/user/public-repo
git remote set-url --add --push git@github.com/user/private-repo
```

If you want to work on a public branch, check it out from the `both` remote

```
git checkout both/master -b master
```

A push on this branch will sync to both the public and private remotes

If you want to work on a private branch only, create a new remote that only pushes to the private repo

```
git remote add private git@github.com/user/private-repo
git checkout private/secret -b secret
```

Pushing from the secret branch will only push to the private remote.
