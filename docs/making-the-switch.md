disqus: sema-docs

# Making the switch <small>Moving your SEMA instance to the new architecture</small>

!!! warning "Temporary Section"
    This section is temporary. It will be deleted by April 1st 2019.

This section is for those who are willing to move their instance of SEMA to the new architecture introduced on March 2019.

Unfortunately, we got rid of the main repository, so we will be losing all the previous commits. We archived the old architecture repo - it's now called `sema-core-archived` - and we strongly suggest you to do the same for yours.

!!! info ""
    We really tried our best to reduce the size of the original repository after replacing its content by those of the POS mobile client. Nothing really worked.
    
    Feel free to experience it yourself by cloning <a href="https://github.com/untapped-inc/sema-core-archived" target="_blank">this repository</a>. And that's only after we've tried to save space.

Let's get to it.

## 1. Development

Let's make sure our development instance is running fine first.

### The Database

The database structure file and related documents are all located at <a href="https://github.com/untapped-inc/sema-database" target="_blank">https://github.com/untapped-inc/sema-database</a>.

Simply fork that repo and go to the [Getting Started](getting-started.md#the-database) sub-section on how to use it.

For those who have customized this component, all you need to do after forking is to replace the content of your fork with the content of your previous `database` directory.

### The REST API

The REST API, which is the core of SEMA, has been moved to <a href="https://github.com/untapped-inc/sema-core" target="_blank">https://github.com/untapped-inc/sema-core</a>.

Now you can fork that repo and go to the [Getting Started](getting-started.md#the-rest-api-server) sub-section on how to run it.

For those who have customized this component, all you need to do after forking is to replace the content of your fork with the content of your previous `report_server` directory. The only difference in their source is the `.example-env` file, which used to be in the root directory of the old architecture. **So make sure you leave this file in there**.

### The Back Office Web Client

The back office web client is the new merge between the admin and the reports dashboards. It's now located at <a href="https://github.com/untapped-inc/sema-back-office-web" target="_blank">https://github.com/untapped-inc/sema-back-office-web</a>.

Simply fork that repo and go to the [Getting Started](getting-started.md#the-back-office-web-client) sub-section on how to run it.

For those who have customized this component, all you need to do after forking is to replace the content of your fork with the content of your previous `sema-backoffice-web` directory.

### The POS Mobile Client

The POS mobile client is now located at <a href="https://github.com/untapped-inc/sema-pos-mobile" target="_blank">https://github.com/untapped-inc/sema-pos-mobile</a>.

Simply fork that repo and go to the [Getting Started](getting-started.md#the-pos-mobile-client) sub-section on how to run it.

For those who have customized this component, all you need to do after forking is to replace the content of your fork with the content of your previous `mobile_client` directory. The only difference in their source is the `.babelrc` file. Without this new version of it, you'll get an error when trying to build the app. **So make sure you leave this file in there**.

### The Documentation

The source code of this documentation website. It has always been over at <a href="https://github.com/untapped-inc/sema-docs" target="_blank">https://github.com/untapped-inc/sema-docs</a>

Feel free to fork it if you're planning on documenting your own tools and features.

Now, all you need to do is to stage the changes, commit and push to each of the repositories. Done.

## 2. Deployment

Now that you're good locally. Let's see what needs to be done on the cloud to accommodate.

!!! warning
    There's a high chance for things to break here, so make sure you're not doing this during production at the site(s).

From the SSH server you use for production, go ahead and start the tutorial over at the [Deploying to Production](deploying-to-production.md#the-back-office-web-client) section. Yes, even tho there's already an instance of SEMA running on there. It was updated to accommodate the new structure.

Skip the The Database sub-section because you've probably done it already, just make sure you take care of all the prerequisites. The first change you'll encounter is the creation of the `sema` directory in the [prerequesites of the back office web client](deploying-to-production.md#prerequisites-3)

You are most likely to get stuck during [deployment of the REST API](deploying-to-production.md#serving-the-rest-api) because there's probably already an instance running. So go ahead and run this command:
```
pm2 ls
```
It will display a list of processes running. Using the ID of the SEMA process, stop and delete/kill it with:
```
pm2 del PROCESS_ID
```

Now go ahead and continue with the tutorial and you should be good to go.

Since the admin and the reports dashboards have been merged, if you had an admin dashboard running on your old architecture, make sure you kill its process too using the same method used above.

We hope this section was clear enough, please leave a comment below or contact us directly for any questions.