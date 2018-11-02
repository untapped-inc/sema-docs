# Deploying to production <small>Things are getting serious</small>

This section is a tutorial on how to deploy the system in production mode. The previous section was about running it locally and we strongly recommend that you go through the process before you start with this one because they have a lot in common.

In fact, we will not go over some details that we covered in that section, so please, [go through it](/getting-started) if you haven't done so yet.

## Prerequisites

* A linux server - preferably Ubuntu - with SSH access. We use [DigitalOcean](https://digitalocean.com).
* Install nvm: Follow [this link](https://github.com/creationix/nvm#installation) for instructions.
* Install latest LTS version of Node and npm: `nvm install --lts`
* Install Yarn: `npm i -g yarn`
* Install MySQL: Follow [this link for Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-16-04) Or find the right turorial for your version of Ubuntu.
* Install react-scripts (To be able to build the client): `yarn global add react-scripts`
* Fork the project repo through Github: Follow [this link](https://help.github.com/articles/fork-a-repo/) for instructions.
* Nginx (Reverse Proxy): `sudo apt install nginx`
* Pm2 (Robust Process Manager): `yarn global add pm2`
* Clone your new Git repo to your server: `git clone https://github.com/YOUR-USERNAME/sema-core.git` - Make sure to change ==YOUR-USERNAME== to your Github username.
* Move into your new folder: `cd sema-core`
* From this point on, we expect that you are in the root directory of the project.

## Deploying

Assuming you've installed all the necessary prerequisites *correctly*, let's get started: