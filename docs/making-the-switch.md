disqus: sema-docs

# Making the switch <small>Moving your SEMA instance to the new architecture</small>

!!! warning "Temporary Section"
    This section is temporary. It will be deleted by April 1st 2019.

This section is for those who are willing to move their instance of SEMA to the new architecture introduced on March 2019.

This section assumes you already have [a version of SEMA running in development mode](getting-started.md) and [one running in production mode](deploying-to-production.md).

We'll also assume that:

* You've FORKED the main repo
* You've customized one or all components to your liking
* You've added your own features to one or more components

Let's get to it.

## 1. Development

Let's make sure our development instance is running fine first.

### The Database

The database structure file and related documents are all located at <a href="https://github.com/untapped-inc/sema-database" target="_blank">https://github.com/untapped-inc/sema-database</a>.

Simply fork that repo and go to the [Getting Started](getting-started.md#the-database) sub-section on how to use it.

### The REST API

The REST API, which is the core of SEMA, has been moved to <a href="https://github.com/untapped-inc/sema-core" target="_blank">https://github.com/untapped-inc/sema-core</a>.

Simply fork that repo and go to the [Getting Started](getting-started.md#the-rest-api-server) sub-section on how to run it.

For those who have customized this component, all you need to do after forking is to replace the content of your fork with the content of your previous `report_server` directory. The only difference in their source is the `.example-env` file, which used to be in the root directory of the old architecture. **So make sure you leave this file in there**.

### The Back Office Web Client

The back office web client is the new merge between the admin and the reports dashboards. It's now located at <a href="https://github.com/untapped-inc/sema-back-office-web" target="_blank">https://github.com/untapped-inc/sema-back-office-web</a>.

Simply fork that repo and go to the [Getting Started](getting-started.md#the-back-office-web-client) sub-section on how to run it.

For those who have customized this component, all you need to do after forking is to replace the content of your fork with the content of your previous `sema-back-office-web` directory.

### The POS Mobile Client

The POS mobile client is now located at <a href="https://github.com/untapped-inc/sema-pos-mobile" target="_blank">https://github.com/untapped-inc/sema-pos-mobile</a>. Which is actually the original repository.

Reason for this is, we intentionally never prioritized customization for the other components, so most of the SWEs that are currently using our system haven't made much changes to them.

Therefore, when it comes to the POS client, all you have to do is to follow the [Staying in Harmony](staying-in-harmony.md) tutorial and merge the changes with yours.

The only catch is, you're going to have to update the URL of the `upstream` remote. If you don't understand what this means, it's probably because you never had to add the Untapped repo as an upstream repo, so go ahead and add the new POS repo as an upstream repo:
```
git remote add upstream https://github.com/untapped-inc/sema-pos-mobile
```

If you do understand however, get into the root directory of your repo and run the following:
```
git remote -v
```
This will show you all the remotes linked to your repository. You should get something like:
```
origin	git@github.com:YOUR-USERNAME/sema-core.git (fetch)
origin	git@github.com:YOUR-USERNAME/sema-core.git (push)
upstream	git@github.com:untapped-inc/sema-core.git (fetch)
upstream	git@github.com:untapped-inc/sema-core.git (push)
```
Now, run the following to update the `upstream` remote:
```
git remote set-url upstream https://github.com/untapped-inc/sema-pos-mobile
```

Now go ahead and follow the tutorial [over there](staying-in-harmony.md). Then you can check out the [Getting Started](getting-started.md##the-pos-mobile-client) sub-section showing you how to use it.

### The Documentation

The source code of this documentation website. It has always been over at <a href="https://github.com/untapped-inc/sema-docs" target="_blank">https://github.com/untapped-inc/sema-docs</a>

Feel free to fork it if you're planning on documenting your own tools and features.

## 2. Deployment

Now that you're good locally. Let's see what needs to be done on the cloud to accommodate.

!!! warning
    There's a high chance for things to break here, so make sure you're not doing this during production at the site(s).

From the SSH server you use for production, go ahead and start the tutorial over at the [Deploying to Production](deploying-to-production.md) section. Yes, even tho there's already an instance of SEMA running on there.

Skip the The Database sub-section because you've probably done it already, just make sure you take care of all the prerequisites.

You will probably get stuck during [deployment of the REST API](deploying-to-production.md#serving-the-rest-api) because there's probably already an instance running. So go ahead and run this command:
```
pm2 ls
```
It will display a list of processes running. Using the ID of the SEMA process, stop and delete it with:
```
pm2 del PROCESS_ID
```

Now go ahead and continue with the tutorial and you should be good to go.