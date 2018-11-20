disqus: sema-docs

# Deploying to production <small>Things are getting serious</small>

This section is a tutorial on how to deploy the system in production mode. The previous section was about running it locally and we strongly recommend that you go through the process before you start with this one because they have a lot in common.

In fact, we will not go over some details that we covered in that section, so please, [go through it](/sema-docs/getting-started) if you haven't done so yet.

In production mode, the dashboard server runs on sema.untapped-inc.com and the React app is built then rendered by the server. REST calls from the app to the server are reverse proxied by Ngninx from port 80 to port 3001. We use pm2 to run the server.

### Prerequisites

Our servers are in Linux so installation methods will be for GNU/Linux:

* Install nvm: https://github.com/creationix/nvm#installation
* Install latest LTS version of Node and npm: `nvm install --lts`
* Install Yarn: `npm i -g yarn`
* Install react-scripts (To be able to build the client): `yarn global add react-scripts`
* Clone the Git repository to the server: `git clone https://github.com/untapped-inc/sema-core.git`
* Nginx (Reverse Proxy): `sudo apt install nginx`
* Pm2 (Robust Process Manager): `yarn global add pm2`

### Deploying to Production

Follow those steps to deploy this app in production mode:
 
1. Assuming you are in the root directory of this project
2. Install client dependencies: `cd report_client && yarn`
3. Build the client: `yarn build`
4. If you get a fatal error about not having enough memory, just add this - `GENERATE_SOURCEMAP=false` - to the .env file of the `report_client` directory and then run `yarn build` again: `echo 'GENERATE_SOURCEMAP=false' >> .env && yarn build`
5. Create a new `public_react` folder into the server directory: `mkdir ../report_server/public_react`
6. Copy the entire build folder from react_client/build to the report_server/public_react folder:
     `cp -rf ./build ../report_server/public_react`
7. Switch to server directory: `cd ../report_server`
8. Follow [the instructions](/sema-docs/getting-started/#configurations) to create the environment variables file needed by the project
9. Install server dependencies: `yarn`
10. Start the server with Pm2: `pm2 start bin/www --name sema-server`. Name it however you want so you can easily refer to it later
11. Get your server IP address: `curl icanhazip.com`
12. Test the server access via curl - Since we haven't configured Nginx yet, we'll test it from port 3001: `curl http://YOUR-SERVER-IP-ADDRESS:3001/untapped/health-check`. This should return {"server":"Ok","database":"Ok"}
13. Setup Ngninx using [this tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-16-04)
14. Configure Nginx by editing - *WITH SUPER USER*: `/etc/nginx/sites-available/default`:
    `sudo vim /etc/nginx/sites-available/default`
15. Within the server block, there is an existing `location /` block. Replace the contents of that block with the following configuration:

```
location / {
	proxy_pass http://localhost:3001;
	proxy_http_version 1.1;
	proxy_set_header Upgrade $http_upgrade;
	proxy_set_header Connection 'upgrade';
	proxy_set_header Host $host;
	proxy_cache_bypass $http_upgrade;
}
```
16. Make sure you didn't introduce any syntax errors: `sudo nginx -t`
17. Restart Nginx: `sudo systemctl restart nginx`
18. Test the server access without using the port: `curl http://YOUR-SERVER-IP-ADDRESS/untapped/health-check`. This should return {"server":"Ok","database":"Ok"}. You can now setup DNS zone records for your server.