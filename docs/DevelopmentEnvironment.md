# Development environment
To setup the development environment please follow the guide below.

Check the [Server Requirement](ServerRequirements.md#Server-Requirements) section for package and tools needed.

## Environment configurations

First of all please make sure that you've prepared the environment variables by looking at `.env` within the project root folder.

If you couldn't find `.env` file in your project root folder, open **Terminal** and run the following command:

```sh
$ composer run project:prepare
```

> This command will ensure that everything is up and running for you, check `composer.json -> scripts -> project:prepare` script for more information.

## Database Migrations and Seeders

### Migrations

To migrate the table to database, make sure your `.env` is setup correctly.

Check the following variables within `.env` config:

```sh
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=homestead
DB_USERNAME=homestead
DB_PASSWORD=secret
```

Once completed, run the following **command** in your **Terminal**:

```sh
$ php artisan migrate
```

> NOTE: Check Laravel documentations for more details

### Seeders

During development we have special fake data for using during development, the database seeder will check for `APP_ENV` in `.env` file to determind whether the application should generate fake data.

> NOTE: Make sure you set the correct `APP_ENV` data before run migrations

Before seeding data to the database, make sure you migrated all tables.

To seed the data to database run the following command:

```sh
$ php artisan db:seed
```

### Refresh table and re-seed

During developmemnt, you may made some changes to the table and database. You can re-run **migration** and **seeder** with one comman:

```sh
$ php artisan migrate:fresh --seed
```
