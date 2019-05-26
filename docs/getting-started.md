disqus: sema-docs

# Getting Started <small>Running it locally</small>

This section is a tutorial on how to get you started with setting up the platform on your system locally so you can test it.

!!! note "Windows Users"
    We only cover *nix systems like Linux and OS X **for now**. Windows users will need to figure out alternatives on their own.[^windows-users]

## The Database

Let's get started with the database.

### Prerequisites 1

From this point of this tutorial, here's what you'll need to follow along:

* Create a new root directory to contain the whole project: `mkdir sema`
* Move into the root directory: `cd sema`
* Create a new repository by forking the official database repo through Github: Follow [this link](https://help.github.com/articles/fork-a-repo/) for instructions. Link to the repo: https://github.com/untapped-inc/sema-database
* Clone your new repository to a local directory: `git clone https://github.com/YOUR-USERNAME/sema-database.git` - Make sure to change ==YOUR-USERNAME== to your Github username or the one you chose to fork the repo for
* Move into the root directory of the SEMA database: `cd sema-database`
* From this point on, we expect that you are in the root directory of the SEMA database
* Install MySQL: Follow [this link](https://dev.mysql.com/doc/refman/5.7/en/installing.html) for instructions for your system. Make sure you create an admin user, or using `root` is fine too.[^using-root]
* Install nvm: Follow [this link](https://github.com/creationix/nvm#installation) for instructions.
* Install latest LTS version of Node and npm: `nvm install --lts`
* Install Yarn: `npm i -g yarn`

### Configurations

Assuming you've successfully installed MySQL on your system and created an admin user (not **root**), let's start creating the `sema_core` database and populating the basic data for the project.

### Creating the database

Here are the steps to follow:

* Open your MySQL Workbench
* Go to File > Open SQL Script...
* Find your repository folder and choose the file database > create_schema.sql
* Go to Query > Execute (All or Selection). It will run the script and create your new database

!!! note ""
    This will create a new database named **sema_core**. If you want to rename it, either use a tool like MySQL Workbench or make sure you edit the `create_schema.sql` file from this line: `CREATE SCHEMA sema_core;` before you Execute it.

### Populating the required tables

Now that the database is created, let's populate some tables in there. Feel free to change the values to what you want, except where it's mentioned to keep them as is.

* Let's start by populating the MySQL views necessary:
    * Still in MySQL Workbench, using the same steps above, select the `customer_details_view.sql` located in the current directory and run it.
    * Then do the same for the `receipt_details_view.sql` file.
* Let's add a role
``` sql
INSERT INTO `role` (`id`,`authority`,`code`)
VALUES (1,'Admin','admin');
```
* Then the user:
``` sql
INSERT INTO `user` (`id`,`username`,`email`,`password`,`first_name`,`last_name`)
VALUES (1,'administrator','admin@untapped-inc.com','USER_PASSWORD', 'Admin','User');
```
!!! note
    Notice the ==USER_PASSWORD== placeholder for this user. Here's how to get it:

    First, install the bcrypt-cli npm package globally: `yarn global add bcrypt-cli`

    Then run the following command to get the encrypted password: `bcrypt-cli "AdminPassword" 10`

    Replace AdminPassword with the one you want and keep the last value to 10. This is the bcrypt salt round, you'll know why we use it in the [Configurations](#configurations) sub-section.
    
    Then use this encrypted password for this customer. Repeat the last step for subsequent ones.
* Let's now map the user to the role
``` sql
INSERT INTO `user_role` (`role_id`,`user_id`) VALUES (1,1);
```
* Now, time to add a country:
``` sql
INSERT INTO `country` (`id`, `name`)
VALUES (1, 'Haiti');
```
* Now, let's add a region:
``` sql
INSERT INTO `region` (`id`, `name`, `description`, `country_id`)
VALUES (1, 'Ouest', 'On the West side', 1);
```
* Next, add a kiosk/site:
``` sql
INSERT INTO `kiosk` (`id`, `name`, `region_id`)
VALUES (1, 'Bois9', 1);
```
* Now, add a few customer types:
``` sql
INSERT INTO `customer_type` (`id`, `name`)
VALUES (1, 'anonymous');
INSERT INTO `customer_type` (`id`, `name`)
VALUES (2, 'Small Store');
```
!!! note
    The `anonymous` type is required. Do not change it.
* Now for the sales channels:
``` sql
INSERT INTO `sales_channel` (`id`, `name`, `description`)
VALUES (1, 'reseller', 'Resellers');
INSERT INTO `sales_channel` (`id`, `name`, `description`)
VALUES (2, 'direct', 'Customers that walk up to the kiosk');
```
* Next, add a couple of customers:
```sql
INSERT INTO `customer_account` (`id`, `name`, `customer_type_id`, `sales_channel_id`, `kiosk_id`, `address_line1`, `gps_coordinates`, `phone_number`)
VALUES ('CUSTOMER_UUID', 'Direct Client', 2, 2, 1, '--------------------', 'gps', '---------------------');
INSERT INTO `customer_account` (`id`, `name`, `customer_type_id`, `sales_channel_id`, `kiosk_id`, `address_line1`, `phone_number`)
VALUES ('CUSTOMER_UUID', 'Chez Matilda', 1, 1, 1, '25, rue Fernand', '+50937120500');
```
!!! info
    Notice the CUSTOMER_UUID placeholder value for those customers. Here's how to get them:

    First, install the uuid npm package globally: `yarn global add uuid`

    Then simply run `uuid` to generate a uuid in your terminal: `uuid`
    
    Then use this uuid for one customer by replacing the ==CUSTOMER_UUID== placeholder with it. Repeat the last two steps for subsequent ones.
* Now it's time to add some product categories:
``` sql
INSERT INTO `product_category` (`id`, `description`, `name`)
VALUES (1, 'Water products', 'water_products');
```
* Then add a product
``` sql
INSERT INTO `product` (`id`, `name`, `sku`, `description`, `category_id`, `price_amount`, `price_currency`, `unit_per_product`, `unit_measure`, `cogs_amount`, `base64encoded_image`)
VALUES (1, '5.0L bottle', 'MD5G', '5 Liter water bottle', 1, 4000.00, 'UGX', 5, 'liters', 2000.00, 'PRODUCT_BASE64_ENCODED_IMAGE');
```
!!! note
    Notice the `PRODUCT_BASE64_ENCODED_IMAGE`. It's the image that shows up for the product. We use base64 encoded images instead of PNG files. To get your own base64 version of your product image, you can use an online tool for that. We personally like to use [this tool](https://www.base64-image.de/).

    Once you get the base64 encoded image from the tool, simply replace the ==PRODUCT_BASE64_ENCODED_IMAGE== placeholder with it.
* Finally, let's map the product to the sales channel and the kiosk
``` sql
INSERT INTO `product_mrp` (`id`, `kiosk_id`, `product_id`, `sales_channel_id`, `price_amount`, `price_currency`, `cogs_amount`)
VALUES (1, 1, 1, 1, '4000.00', 'UGX', '2000.00');
INSERT INTO `product_mrp` (`id`, `kiosk_id`, `product_id`, `sales_channel_id`, `price_amount`, `price_currency`, `cogs_amount`)
VALUES (2, 1, 1, 2, '4000.00', 'UGX', '2000.00');
```

Your database is now ready.

<!-- To learn more about the database schema, please [click here](the-database-schema.md). -->

## The REST API Server

Let's move on to the REST API.

### Prerequisites 2

From this point of this tutorial, here's what you'll need to follow along:

* Assuming you are currently in the `sema-database` directory, move back into the root directory: `cd ..`
* Create a new repository by forking the official REST API repo through Github: Follow [this link](https://help.github.com/articles/fork-a-repo/) for instructions. Link to the repo: https://github.com/untapped-inc/sema-core
* Clone your new repository to a local directory: `git clone https://github.com/YOUR-USERNAME/sema-core.git` - Make sure to change ==YOUR-USERNAME== to your Github username or the one you chose to fork the repo for
* Move into the root directory of the REST API: `cd sema-core`
* From this point on, we expect that you are in the root directory of the REST API

### Configurations

Before you can start running the server, you will need to first set the property values in the configurations file.

!!! info ""
    This configurations file is located in the root directory of the REST API as `.example-env`. It's a dot file, so if you want to see it from your terminal, you need to add the `-a` flag to your ls: `ls -a`.

First, rename this file from `.example-env` to `.env`: `cp .example-env .env`

Then move it to the parent directory (which should be `sema` if you were following along): `mv .env ../.env`

Now open this `.env` file using your favorite text editor. These properties provide the necessary details for the clients and the server to access the database and setup a few dependencies. Use the DB credentials you created while installing and setting up MySQL.

| Property Name            | Description                                            |
| ------------------------ | --------------------------------------------------     |
| DB_HOST                  | The URL to the database server location E.g. `localhost` |
| DB_USER                  | The user who has access to this database  E.g. `untapped`             |
| DB_PASSWORD              | The user password for this database E.g. `semaIsAwesome`[^db-password]                  |
| DB_SCHEMA                | The actual name of the database/schema E.g. `sema_core` |
| DB_DIALECT               | The SQL dialect used by the DB. E.g. `mysql`.          |
| DEFAULT_TABLES           | The tables that must be populated - postinstall - by sequelize-auto by default E.g. `user,role,user_role`. We recommend you keep it to the default value.      |
| JWT_SECRET               | JSON Web Token secret used to encrypt the token. E.g. `f8d74387h8undgs87`. Don't use this example, type in anything in there to make it hard to guess, this is some kind of password that will be used between the clients and the server.        |
| JWT_EXPIRATION_LENGTH    | Length of time the token is valid for. E.g. `1 day`    |
| BCRYPT_SALT_ROUNDS       | How much time is needed to calculate a single BCrypt hash - Between 8 and 12 is recommended. Used for encrypting passwords for users. Remember, changing this requires that you use the same salt rounds value when creating a new password on the `user` table. E.g. `10` |

!!! danger
    We **Strongly** recommend that you do not to push the `.env` file to your repository after adding the correct configuration property values. For security measures, we added it to the project's `.gitignore` file so that git can always ignore it. So you would need to really want to push it to be able to do so.

### Running the server

Now that your database and your configurations are all set. Let's run the server, shall we?

* Install dependencies: `yarn`
* Run the server: `yarn start`

It should start running at http://localhost:3001

Let's test that it's running fine with curl:
```
curl http://localhost:3001/sema/health-check
```
It should return something like: `{"server":"Ok","database":"Ok","version":"0.0.1.4","schema":"sema_core"}`

The version number may vary.

!!! note
    The clients are configured to access the server on port 3001.

<!-- To learn more about the REST API server, please [click here](rest-api/overview.md). -->

## The Back Office Web Client

Time to run the back office.

### Prerequisites 3

From this point of this tutorial, here's what you'll need to follow along:

* Assuming you are currently in the `sema-core` directory, move back into the root directory: `cd ..`
* Create a new repository by forking the official back office web client repo through Github: Follow [this link](https://help.github.com/articles/fork-a-repo/) for instructions. Link to the repo: https://github.com/untapped-inc/sema-back-office-web
* Clone your new repository to a local directory: `git clone https://github.com/YOUR-USERNAME/sema-back-office-web.git` - Make sure to change ==YOUR-USERNAME== to your Github username or the one you chose to fork the repo for
* Move into the root directory of the back office web client: `cd sema-back-office-web`
* Install react-scripts (To be able to run the client): `yarn global add react-scripts`
* From this point on, we expect that you are in the root directory of the back office web client

### Running the Back Office Web Client

Now it's time to run the back office client. Here are the steps to follow:

* Install dependencies: `yarn`
* Run the client: `yarn start`

It should start running at http://localhost:3000

Notice the port number: 3000

Go to the above link and test the client by logging in with the user credentials you created during the [database setup](#populating-the-required-tables).

<!-- To learn more about the back office, please [click here](back-office/overview.md). -->

## The POS Mobile Client

Finally, let's run the POS client.

### Prerequisites 4

From this point of this tutorial, here's what you'll need to follow along:

* Assuming you are currently in the `sema-back-office-web` directory, move back into the root directory: `cd ..`
* Create a new repository by forking the official POS mobile client repo through Github: Follow [this link](https://help.github.com/articles/fork-a-repo/) for instructions. Link to the repo: https://github.com/untapped-inc/sema-pos-mobile
* Clone your new repository to a local directory: `git clone https://github.com/YOUR-USERNAME/sema-pos-mobile.git` - Make sure to change ==YOUR-USERNAME== to your Github username or the one you chose to fork the repo for
* Move into the root directory of the POS mobile client: `cd sema-pos-mobile`
* From this point on, we expect that you are in the root directory of the POS mobile client

### Running the POS mobile client

* Follow the Android setup steps at [the official react native  docs](https://facebook.github.io/react-native/docs/getting-started.html#content). Make sure you select the appropriate tabs in the instructions.
    * "Building Projects with Native Code"
    * "Development OS: macOS or Windows or Linux.
    * Target OS: Android"
* Install dependencies: `yarn`
* Create and open an emulator either by using [Genymotion](https://www.genymotion.com) or the [Android Studio AVD](https://developer.android.com/studio/run/emulator)
    * Use at least a 7 inch tablet with a minimum Android version of 6.0.0
* Start the app on the emulator: `react-native run-android`

You should get the Settings page. From there, fill up the form to make the connection between the mobile client and the server:

| Settings Field          | Description                                            |
| ------------------------ | --------------------------------------------------     |
| SEMA Service URL         | The URL to the running server. Since we're on local, we just need to get the current IP address of our system using `ifconfig`. E.g.: http://192.168.1.7:3001. Notice the port number of the server at the end. |
| Site                  | The kiosk that we created during [database setup](#populating-the-required-tables). E.g.: `Bois9`             |
| Username or Email        | This is the user we just used to login to the dashboard client. E.g. `Administrator` |
| Password                | The password of the above user E.g. `diueh89ndys` |

Then choose a language and press the `Connect` button. It should connect successfully and you will be able to test the whole app.

<!-- To learn more about the POS client, please [click here](/the-pos-client). -->

## Where to go from here?

And that's it folks. You now have the whole platform running successfully on your own computer for testing and/or development purposes. Here are some useful links to go to from here:

* [Deploying to Production](deploying-to-production.md)
<!-- * [The Database Schema](the-database-schema.md) -->
<!-- * [The REST API Server](rest-api/overview.md) -->
<!-- * [The Dashboard client](back-office/overview.md) -->
<!-- * [The POS client](/the-pos-client) -->

Feel free to leave a comment down below for questions and clarifications.

[^windows-users]: No hard feelings Windows users but your system is a pain for developers
[^db-password]: Hopefully you didn't use this password while setting up MySQL. But we won't judge you if you did ;)
[^using-root]: Don't tell anyone we told you that! Seriously though, if it's on a personal computer and not a server, it's fine.
