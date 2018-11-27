# SEMA Technical Documentation

This is the source code of the web page for the technical documentation of SEMA. It's hosted on Github and [it's located here](http://untapped-inc.github.io/sema-docs/).

## How to contribute

First of all, we would like to thank you very much for wanting to contribute to this documentation. We really appreciate any type of support.

The easiest way to contribute to this doc is to edit an existing page. All you have to do is to click on the pencil icon at the top right of the content of a section. See the following picture:

![Section Edit Icon][edit-icon]

Follow the instructions on Github to send a pull request.

But if you're going to add new pages and do more advanced stuffs, keep reading.

### Running it Locally - Development Mode

1. Install MkDocs: [Follow the installation instructions](https://www.mkdocs.org/#installation)
2. Fork this repo
3. Clone your forked repo: `git clone git@github.com:YOUR-GITHUB-USERNAME/sema-docs.git`
4. Get into your project directory: `cd sema-docs`
5. Run the documentation in development mode - MkDocs will run it on a local server and everytime you save a change to a file, the web page will refresh on its own: `mkdocs serve`
6. Copy and go to the `localhost:PORT-NUMBER` page from the output of the above command

### Editing and Sending a Pull Request

1. Add the original repo - from Untapped - as an upstream remote: `git remote add upstream git@github.com:untapped-inc/sema-docs.git`
2. Pull all changes from upstream, just in case: `git pull upstream master`
1. Create a new branch for your changes - change `<new-branch-name>` to anything meaningful for your changes: `git checkout -b <new-branch-name>`
2. Open the `docs` directory in your favorite text editor
3. Make changes to the appropriate files - See the [Formatting section](#formatting) below
4. Test your changes from the local dev page - See the section above
4. Stage and commit files
5. Push to your branch on your `origin` remote - `<new-branch-name>` being the branch you created earlier: `git push origin <new-branch-name>`
6. Go to your Github repo from your browser
7. You'll notice the Github notification that suggests you to make a pull request from your last branch push. If you don't, change the branch from the `Branch` dropdown and you'll definitely see it from there
8. Wait for a core team member to review and/or approve your PR.

### Formatting

It's important that your changes reflect the content formatting standard that we've set. Our core team will let you know of any missing details from your Pull Request through a `Change Request` or a simple comment. Sometimes, we might even just make the changes and push to your branch so we can complete your PR.

It's easy to follow our standards, simply go to the source of any of the current pages that have the formatting that you want. You'll see how we did it and you can simply copy and paste from it.

If you want to do some more advanced stuffs, check out what the MkDocs theme we're using has to offer: 

* [Getting Started with MkDocs and the Material Theme](https://squidfunk.github.io/mkdocs-material/getting-started/)
* [Basics of formatting](https://squidfunk.github.io/mkdocs-material/specimen/)
* [Theme customization](https://squidfunk.github.io/mkdocs-material/customization/)
* Documentation for the plugins that we're currently using:
    * [Admonition](https://squidfunk.github.io/mkdocs-material/extensions/admonition/)
    * [CodeHilite](https://squidfunk.github.io/mkdocs-material/extensions/codehilite/)
    * [Footnotes](https://squidfunk.github.io/mkdocs-material/extensions/footnotes/)
    * [PyMdown](https://squidfunk.github.io/mkdocs-material/extensions/pymdown/)

### Where are things located

* All the configurations are handled through the `mkdocs.yml`. This is also where the navigation menu is handled.
* The `docs` directory contains all the pages. They are all in Markdown. All the directories and files have self explanatory names.
* The intro page is at `docs/index.md`
* `docs/assets` contains assets like images, extra CSS and extra JS - check the `extra_css` option from the `mkdocs.yml` file.
* The `theme` directory is [a way MkDocs provides to overwrite a part of the theme you're using](https://www.mkdocs.org/user-guide/styling-your-docs/#using-the-theme-custom_dir).

[edit-icon]: section-edit-icon.png