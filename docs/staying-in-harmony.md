disqus: sema-docs

# Staying in harmony <small>Let's not walk over each other</small>

This section is for those who decide to customize their version of SEMA but still want to receive particular updates from [the main repository](https://github.com/untapped-inc/sema-core/) without losing their changes in the long run.

This section assumes you already have [a version of SEMA running in development mode](/sema-docs/getting-started/) and [one running in production mode](/sema-docs/deploying-to-production/tutorial).
We'll also assume that:

* You've FORKED the main repo
* You've Customized your POS app by changing the name, the logos, etc...
* You've added your own features to one or more parts of the system

It's all fun and games, until you notice, from one of our release notes, that we added a new feature that you like.

What do you do now?

Your first guess would be to use `git pull upstream master`, but that's going to blow up your old changes and will annoy you with conflicts that don't even relate to the commit(s) that implement(s) the stuff(s) you like.

Keep reading if you want to selectively merge modifications/updates from our repo to yours.

## Fetch from upstream remote

While this isn't an absolutely necessary step, you'll want to make sure you keep your fork up to date by tracking the original "upstream" repo that you forked. To do this, you'll need to add a remote:

```
git remote add upstream https://github.com/untapped-inc/sema-core.git
```

Verify the new remote named 'upstream'

```
git remote -v
```

Whenever you want to update your fork with the latest upstream changes, you'll need to first fetch the upstream repo's branches and latest commits to bring them into your repository:

```
git fetch -v upstream
```

`-v` makes sure it outputs the fetched branches (verbose).

## Checkout your master branch and merge upstream

Now, checkout your own master branch and squash and merge the upstream repo's master branch. We're merging the master branch here because this is the branch that Untapped releases latest features on. You could have used another one for your own purposes:

```
git checkout master
```

```
git merge --squash upstream/master
```

If there are no unique commits on the local master branch, git will simply perform a fast-forward.

However, if you have been making changes on master - or already merged another branch, you may have to deal with conflicts.<br>When doing so, either through a graphical user interface or the command line, make sure to pick the right modification source for the conflict: `Ours`/`HEAD` - the local changes, `Theirs`/`Incoming Changes` - the incoming changes. 

Then you can stage the changes and make a single commit to complete the merge:

```
git add .
```

```
git commit -m "Merge changes from Untapped"
```

Now, your local master branch is up-to-date with everything modified upstream while retaining your own changes.

Feel free to leave a comment down below or simply ping us in the <a href="https://gitter.im/sema-dev/" target="_blank">Gitter community</a>.