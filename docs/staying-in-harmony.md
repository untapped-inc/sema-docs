disqus: sema-docs

# Staying in Harmony <small>Let's not walk over each other</small>

This section is for those who decide to customize their version of SEMA but still want to receive particular updates from [the core repository](https://github.com/untapped-inc/sema-core/) without losing their changes in the long run.

This section assumes you already have [a version of SEMA running in development mode](/sema-docs/getting-started/) and [one running in production mode](/sema-docs/deploying-to-production/). We'll also assume you customized your POS app by changing the name, the logos and/or have even added your own features to one or more parts of the system.

It's all fun and games, until you notice, from one of our release notes, that we added a new feature that you like.

What do you do?

Your first guess would be to use `git pull upstream master`, but that's going to blow up your old changes and will annoy you with conflicts that don't even relate to the commit(s) that implement(s) the stuff(s) you like.

Here's how to selectively merge commits from our repo to yours:

1. In your development repo, make sure your repo is at its latest version: `git pull origin master`
2. Add the original repo as an upstream remote: `git remote add upstream git@github.com:untapped-inc/sema-core.git`
3. Fetch changes from the upstream remote: `git fetch upstream`
4. It will list all the branches it fetched from the remote. The changes will probably be from the `upstream/master` branch, since we already published them
5. Log the commit messages from this branch: `git log upstream/master`
6. Using the hash number of each commit, figure out which commit(s) is/are related to the feature(s) you like: `git show SHA1`
7. For each of those commits, copy the hash number of it and cherry pick it: `git cherry-pick -n SHA1`. Cherry picking a commit using the `-n` flag will set all the modified files in this commit in a staged mode. The files that have conflicts with your own code will be unstaged and will contain the conflict diffs. You have to take care of conflicts manually, using your favorite text editor. No need to even stage the changes that you make.
8. Once you're done with your modifications and testing, unstage all changes: `git reset HEAD`
9. Use `git add --patch` to pick and choose the changes that you want. Enter `y` for yes, `n` for no. Enter `?` for more options.
10. Create a commit for all the staged files: `git commit -m "Merged the IoTile integration feature from Untapped"`
11. Push your changes to your own repo and we made it!: `git push origin master`

We admit it, those are pretty intermediate to advanced git commands. Hopefully we did a good enough job explaining most steps to you. Just make sure to follow the process in order.

## Credits

This section wouldn't be made possible without [this succint answer by Tim, on StackOverflow](https://stackoverflow.com/a/1405189/927559).

Feel free to leave a comment down below or simply ping us in the <a href="https://gitter.im/sema-dev/" target="_blank">Gitter community</a>.