# Staying in Harmony <small>Let's not walk over each other</small>

This section is for those who decide to customize their version of SEMA but still want to receive particular updates from [the core repository](https://github.com/untapped-inc/sema-core/) without losing their changes in the long run.

This section assumes you already have [a version of SEMA running in development mode](/sema-docs/getting-started/) and [one running in production mode](/sema-docs/deploying-to-production/).

So far, we've identified two cases for a SWE running their business with SEMA:

1. We like SEMA and we are satisfied with their features and the updates they make to the platform
2. We like SEMA and we are satisfied with their features, 

Let's go over the procedure each of those cases would go through to keep their repository in sync with the core repo.

## 1. We like SEMA and we are satisfied with their features and the updates they make to the platform

For SWEs in this category, let's see the procedure one would follow to stay in sync with the core repository:

* First read the release notes of the new version.
* Connect to your SSH server
* Get into the root directory of the project you cloned and that's 
* Check for changes that you may have made while setting up and configuring the system
    * If there are changes and you don't mind losing because you've backed them up, get rid of all changes: `git checkout -- .`


## 2. We like SEMA but we would like to make changes to the platform while still being able to cherry pick the new features we like from their repo

Nope.