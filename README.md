

Description
===========

The Chef WordPress cookbook has been forked from https://github.com/brint/wordpress-cookbook.
Berksfile has been removed so that I can do a Berks init and generate a new Berksfile

Description
===========

This cookbook does not set up the WordPress blog. You will need to do this manually by going to http://hostname/wp-admin/install.php (this URL may be different if you change the attribute values).

Requirements
============

Platform
--------

* Ubuntu 12.04, 14.04
* RHEL/CentOS 5, 6
* Windows

Cookbooks
---------

* mysql
* mysql_chef_gem
* php
* apache2
* iis
* windows
* openssl (uses library to generate secure passwords)
* selinux (used to disable selinux for MySQL on RHEL-based systems)

Attributes
==========

### WordPress

* `node['wordpress']['version']` - Version of WordPress to download. Use 'latest' to download most recent version.
* `node['wordpress']['parent_dir']` - Parent directory to where WordPress will be extracted. (Windows Only)
* `node['wordpress']['dir']` - Location to place WordPress files.
* `node['wordpress']['db']['root_password']` - Root password for MySQL (added for support with community cookbook version 6+)
* `node['wordpress']['db']['instance_name']` - Name of the MySQL instance to use with MySQL (community cookbook version 6+)
* `node['wordpress']['db']['name']` - Name of the WordPress MySQL database.
* `node['wordpress']['db']['user']` - Name of the WordPress MySQL user.
* `node['wordpress']['db']['pass']` - Password of the WordPress MySQL user. By default, generated using openssl cookbook.
* `node['wordpress']['db']['prefix']` - Prefix of all MySQL tables created by WordPress.
* `node['wordpress']['db']['host']` - Host of the WordPress MySQL database.
* `node['wordpress']['db']['port']` - Port of the WordPress MySQL database.
* `node['wordpress']['db']['charset']` - [Character set](http://dev.mysql.com/doc/refman/5.7/en/charset-charsets.html) of the WordPress MySQL database tables. Defaults to 'utf8'.
* `node['wordpress']['db']['collate']` - [Collation](http://dev.mysql.com/doc/refman/5.7/en/charset-collation-effect.html) of the WordPress MySQL database tables.
* `node['wordpress']['db']['mysql_version']` - Version of MySQL to install (for supporting community cookbook version 6+)

* `node['wordpress']['allow_multisite']` - Enable [multisite](http://codex.wordpress.org/Create_A_Network) features (default: false).
* `node['wordpress']['wp_config_options']` - A hash of options to define in wp_config.php, output as key value pairs into a PHP constant e.g. `define( '<%= @key %>', <%= @value %> );`. Note: for values you will need to add single quotes around text but omit them for booleans and numbers. (default: {}).
* `node['wordpress']['config_perms']` - Permissions to set for a site's wp-config.php.
* `node['wordpress']['server_aliases']` - Aliases to use when setting up Virtual Host with Nginx or Apache
* `node['wordpress']['server_port']` - Port to use when setting up the Virtual Host with Nginx or Apache

* `node['wordpress']['install']['user']` - Install user used for WordPress file permissions and the PHP-FPM user (if applicable)
* `node['wordpress']['install']['group']` - Install group used for WordPress file permissions and the PHP-FPM group (if necessary)

* `node['wordpress']['parent_dir']` - Parent directory of where WordPress will be installed. This is used in the Windows installation to determine where the .zip will be downloaded to.
* `node['wordpress']['dir']` - Path where WordPress should be installed
* `node['wordpress']['url']` - URL to the zip or tarball installer of WordPress
* `node['wordpress']['server_name']` - Hostname used for setting up the Virtual Host configuration for your WordPress site

* `node['wordpress']['php_options']` - Additional PHP settings for the installation.

Usage
=====

Add the "wordpress" recipe to your node's run list or role, or include the recipe in another cookbook.
