disqus: sema-docs

# Getting Started <small>Running it locally</small>

This section is a tutorial on how to get you started with setting up the platform on your system locally so you can test it.

!!! note ""
    We cover only *nix systems like Linux and OS X. Windows users will need to figure out alternatives on their own.[^windows-users]

## Prerequisites

* Download MySQL Workbench: Get it [there](https://dev.mysql.com/downloads/workbench/).
* Install nvm: Follow [this link](https://github.com/creationix/nvm#installation) for instructions.
* Install latest LTS version of Node and npm: `nvm install --lts`
* Install Yarn: `npm i -g yarn`
* Install react-scripts (To be able to run the client): `yarn global add react-scripts`
* Install MySQL: Follow [this link](https://dev.mysql.com/doc/refman/5.7/en/installing.html) for instructions for your system. Make sure you create an admin user, or using `root` is fine too.[^using-root]
* Fork the project repo through Github: Follow [this link](https://help.github.com/articles/fork-a-repo/) for instructions.
* Clone your new Git repo to a local folder: `git clone https://github.com/YOUR-USERNAME/sema-core.git` - Make sure to change ==YOUR-USERNAME== to your Github username.
* Move into your new folder: `cd sema-core`
* From this point on, we expect that you are in the root directory of the project.

## Setting up the Database

Assuming you successfully installed MySQL on your system and created an admin user, let's start creating the `sema_core` database and populating some sample data for the project.

### Creating the database

Here are the steps to follow:

* Open your MySQL Workbench
* Go to File > Open SQL Script...
* Find your repository folder and choose the file database > create_schema.sql
* In the editor, add these two lines at the top of the file:
``` sql
CREATE SCHEMA sema_core
USE sema_core;
```
Feel free to name the database however you want. For the rest of this tutorial, we will use `sema_core`, so make sure you remember to change it to yours.

* Go to Query > Execute (All or Selection). It will run the script and create your new database

### Populating the required tables

Now that the database is created, let's populate some tables in there. Feel free to change the values to what you want, except where it's mentioned to keep them as is.

* Let's start by populating the MySQL views necessary:
    * Still in MySQL Workbench, using the same steps above, select the `customer_details_view.sql` located in the `database` folder and run it.
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
!!! note
    Those two sales channels are required for now. Do not change them, except for the descriptions.
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
    
    Then use this uuid for one customer by replacing the ==CUSTOMER_UUID== placeholder with it. Repeat the last step for subsequent ones.
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
    As of now, you must have at least one product with a `unit_measure` value of `liters`.

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

## Configurations

Before you can start running the clients and the server, you will need to first set the property values in the configuration file.

!!! info ""
    This configuration file is located in the root folder as `.example-env`. It's a dot file, so if you want to see it from your terminal, you need to add the `-a` flag to your ls: `ls -a`.

First, rename this file from `.example-env` to `.env`: `cp .example-env .env`

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
| BCRYPT_SALT_ROUNDS       | How much time is needed to calculate a single BCrypt hash - Between 8 and 12 is recommended. Used for encrypting passwords for users. E.g. `10` |

!!! danger
    We **Strongly** recommend you not to push the `.env` file to your repository after adding the correct configuration property values. For security measures, we added it to the project's `.gitignore` file so that git can always ignore it. So you would need to really want to push it to be able to do so.

## Running the server

[^windows-users]: No hard feelings Windows users but your system is a pain for developers
[^db-password]: Hopefully you didn't use this password while installing MySQL. But we won't judge you if you did ;)
[^using-root]: Don't tell anyone we told you that! Seriously though, if it's on a personal computer and not a server, it's fine.