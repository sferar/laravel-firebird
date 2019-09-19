laravel-firebird
================

To use this package:

Installation
------------

Install the Firebird PDO driver for PHP.

Mariuz's Blog has a very good step by step on this:
http://mapopa.blogspot.com/2009/04/php5-and-firebird-pdo-on-ubuntu-hardy.html

Install using composer:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ json
composer require rsfera/laravel-firebird
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Update the `app/config/app.php`, add the service provider:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ json
'Firebird\FirebirdServiceProvider'.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For Laravel 6.0 and later:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ php
Firebird\FirebirdServiceProvider::class,
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can remove the original DatabaseServiceProvider, as the original connection
factory has also been extended.

Declare your connection in the database config, using 'firebird' as the
connecion type. Other keys that are needed:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ php
'firebird' => [
    'driver'   => 'firebird',
    'host'     => env('DB_HOST', 'localhost'),
    'database' => env('DB_DATABASE','/storage/firebird/APPLICATION.FDB'),
    'username' => env('DB_USERNAME', 'sysdba'),
    'password' => env('DB_PASSWORD', 'masterkey'),
    'charset'  => env('DB_CHARSET', 'UTF8'),
    'role'     => 'RDB$ADMIN',
    'engine_version' => '3.0.4',
],
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

And add to your .env

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
DB_CHARSET=UTF8
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If necessary, change the UTF8 to any other charset

This package is a branch jacquestvanzuydam/laravel-firebird package and extends
its functionality. Tested on Laravel-6.0.