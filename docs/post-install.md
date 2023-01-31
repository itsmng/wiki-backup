# ITSM-NG post installation

In this documentation, you will find all the best practices to have with the ITSM-NG application.

## Security

Once installation is done, the `install` directory can be removed or protected by an `.htaccess` file.

You will also find an `.htaccess` file in `config`, `files` and in the root directory of the application. 

To activate the `.htaccess` usage, adding these lines to your Apache configuration file :

    <Directory "/var/www/html/itsm-ng">
        AllowOverride All
    </Directory>

Save and restart Apache.

## Automatic actions

When an automatic action is configured, there are two `Run mode` options :

* `ITSM-NG` (internal mode) : the scheduler activates when a user browses in ITSM-NG.
* `CLI` (external mode) : the scheduler activates when the operating system’s scheduler calls `front/cron.php`.

If you are using `CLI` mode, you need to set up a cronjob that frequently runs `front/cron.php`.

## Command line options

ITSM-NG offers several possible command line actions.

These commands can be used with `php bin/console` directly in the ITSM-NG application folder.

Below you will find the list of actions as well as their description.

| Action                                          | Description                                                                                   |
|-------------------------------------------------|-----------------------------------------------------------------------------------------------|
| `itsmng:build:compile_scss`                     | Compile SCSS files                                                                            |
| `itsmng:config:set`                             | Define application configuration value                                                        |
| `itsmng:database:check`                         | Check for schema differences between the current database and the installation file           |
| `itsmng:database:configure`                     | Define database configuration value                                                           |
| `itsmng:database:install`                       | Install database schema                                                                       |
| `itsmng:database:update`                        | Update database schema to new version                                                         |
| `itsmng:ldap:synchronize_users`                 | Synchronize users with LDAP server information                                                |
| `itsmng:maintenance:disable`                    | Disable maintenance mode                                                                      |
| `itsmng:maintenance:enable`                     | Enable maintenance mode                                                                       |
| `itsmng:migration:appliances_plugin_to_core`    | Migrate Appliances plugin data to ITSM-NG main tables                                         |
| `itsmng:migration:domains_plugin_to_core`       | Migrate Domains plugin data to ITSM-NG main tables                                            |
| `itsmng:migration:myisam_to_innodb`             | Migrate MyISAM tables to InnoDB                                                               |
| `itsmng:migration:racks_plugin_to_core`         | Migrate Racks plugin data to ITSM-NG main tables                                              |
| `itsmng:migration:timestamps`                   | Convert `datetime` fields to `timestamp` for using timezones                                  |
| `itsmng:migration:unsigned_keys`                | Migrate primary/foreign keys to unsigned integers                                             |
| `itsmng:oidc:update`                            | Each ITSM-NG user using openID connect must log in again to update their personal information |
| `itsmng:plugin:activate`                        | Activate plugin(s)                                                                            |
| `itsmng:plugin:deactivate`                      | Deactivate plugin(s)                                                                          |
| `itsmng:plugin:install`                         | Run plugin(s) installation script                                                             |
| `itsmng:rules:process_software_category_rules`  | Processing software category rules                                                            |
| `itsmng:rules:replay_dictionnary_rules`         | Replay dictionary rules on existing elements                                                  |
| `itsmng:security:change_key`                    | Change the password storage key and update the values in the database                         |
| `itsmng:system:check_requirements`              | Check system requirements                                                                     |
| `itsmng:system:clear_cache`                     | Clear application cache                                                                       |
| `itsmng:system:status`                          | Check system status                                                                           |
| `itsmng:task:unlock`                            | Unlock all automatic tasks                                                                    |
