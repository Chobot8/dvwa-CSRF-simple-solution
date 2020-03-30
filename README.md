# dvwa CSRF example

The aim of this project is to show how the CSRF vulnerability is exploited and to create a simple solution. It is using the DVWA web application as a backbone for the project. Everything that is changed has a copy of the **ORIGINAL** files.

## WARNING!

Damn Vulnerable Web Application is damn vulnerable! **Do not upload it to your hosting provider's public html folder or any Internet facing servers**, as they will be compromised. It is recommended using a virtual machine (such as [VirtualBox](https://www.virtualbox.org/) or [VMware](https://www.vmware.com/)), which is set to NAT networking mode. Inside a guest machine, you can download and install [XAMPP](https://www.apachefriends.org/en/xampp.html) for the web server and database.

## License

This file is part of Damn Vulnerable Web Application (DVWA).

Damn Vulnerable Web Application (DVWA) is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

Damn Vulnerable Web Application (DVWA) is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with Damn Vulnerable Web Application (DVWA).  If not, see http://www.gnu.org/licenses/.

- - -

## Installation

**Please make sure your config/config.inc.php file exists. Only having a config.inc.php.dist will not be sufficient and you'll have to edit it to suit your environment and rename it to config.inc.php. [Windows may hide the trailing extension.](https://support.microsoft.com/en-in/help/865219/how-to-show-or-hide-file-name-extensions-in-windows-explorer)**

### Installation Videos

- [How to setup DVWA (Damn Vulnerable Web Application) on Ubuntu](https://www.youtube.com/watch?v=5BG6iq_AUvM) [21:01 minutes]
- [Installing Damn Vulnerable Web Application (DVWA) on Windows 10](https://www.youtube.com/watch?v=cak2lQvBRAo) [12:39 minutes]

### Windows + XAMPP

The easiest way to install DVWA is to download and install [XAMPP](https://www.apachefriends.org/en/xampp.html) if you do not already have a web server setup.

XAMPP is a very easy to install Apache Distribution for Linux, Solaris, Windows and Mac OS X. The package includes the Apache web server, MySQL, PHP, Perl, a FTP server and phpMyAdmin.

XAMPP can be downloaded from:
https://www.apachefriends.org/en/xampp.html

Simply unzip dvwa.zip, place the unzipped files in your public html folder, then point your browser to: http://127.0.0.1/dvwa/setup.php

### Linux Packages

If you are using a Debian based Linux distribution, you will need to install the following packages _(or their equivalent)_:

`apt-get -y install apache2 mysql-server php php-mysqli php-gd libapache2-mod-php`

### Database Setup

To set up the database, simply click on the `Setup DVWA` button in the main menu, then click on the `Create / Reset Database` button. This will create / reset the database for you with some data in.

If you receive an error while trying to create your database, make sure your database credentials are correct within `./config/config.inc.php`. *This differs from config.inc.php.dist, which is an example file.*

The variables are set to the following by default:

```php
$_DVWA[ 'db_user' ] = 'root';
$_DVWA[ 'db_password' ] = 'p@ssw0rd';
$_DVWA[ 'db_database' ] = 'dvwa';
```

Note, if you are using MariaDB rather than MySQL (MariaDB is default in Kali), then you can't use the database root user, you must create a new database user. To do this, connect to the database as the root user then use the following commands:

```mysql
mysql> create database dvwa;
Query OK, 1 row affected (0.00 sec)

mysql> grant all on dvwa.* to dvwa@localhost identified by 'SuperSecretPassword99';
Query OK, 0 rows affected, 1 warning (0.01 sec)

mysql> flush privileges;
Query OK, 0 rows affected (0.00 sec)
```

You will then need to update the config file, the new entries will look like this:

```php
$_DVWA[ 'db_user' ] = 'dvwa';
$_DVWA[ 'db_password' ] = 'SuperSecretPassword99';
$_DVWA[ 'db_database' ] = 'dvwa';
```


### Default Credentials

**Default username = `admin`**

**Default password = `password`**

_...can easily be brute forced ;)_

Login URL: http://127.0.0.1/dvwa/login.php


## Links

Homepage: http://www.dvwa.co.uk/

Project Home: https://github.com/ethicalhack3r/DVWA

*Created by the DVWA team*
