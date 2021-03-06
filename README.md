Tidbit v2.0
===========
Tidbit is random data generator for SugarCRM versions 5.5 and later.  By optimizing
the communications with the database, large amounts of data can be inserted
into the system for testing without manual intervention.

Requirements
------------
PHP 5.3+ (could work for older versions, but no guaranty)
SugarCRM Already installed

Installation
------------
To install Tidbit, unpack the Tidbit-v###.tar.bz2 file, and place the Tidbit/
directory within your SugarCRM installation (Tidbit Directory need to be created inside SugarCRM Installation folder).

The only requirement of Tidbit is that you have an installed and properly
configured copy of SugarCRM in the directory above it.

Example:

1. SSH into vagrant stack you are using via command line.
    ```
    $ vagrant ssh
    ```

2. Navigate to Sugar directory. 
    ```
    $ cd /
    $ cd var/www/html/ (sugar instance).
    ```
    
3. Download zip file from repo (master.zip) into the sugar instance. e.g. /SugarEnt-Full-7.6.0.0/.
    ```
    $ wget (url to zip file)
    ```
    
4. Unzip file (master.zip). Directory created by zip file is called Tidbit-master.
    ```
    $ unzip master.zip
    ```
    
5. Change Directory to /Tidbit e.g., mv /Tidbit-master /Tidbit.
    ```
    $ mv /Tidbit-master /Tidbit
    ```
    
6. Navigate to /Tidbit and follow instructions under usage, below, from within /Tidbit directory.
    ```
    $ cd /Tidbit
    ```

Usage
-----
**NOTE** **Usage of Tidbit could affect on your _data_ in DB**
Please make sure you have a backup, before running data Generation commands

Tidbit uses a command line interface.  To run it from the Tidbit directory:

    $ php -f install_cli.php

Various options are available to control the number of entries generated.
To view them:

    $ php -f install_cli.php -- -h

Example usages:

    * Clean out existing seed data when generating new data set:
      $ php -f install_cli.php -- -c

    * Insert 500 users:
      $ php -f install_cli.php -- -u 500

    * Obliterate all data when generating new records with 300 users:
      $php -f install_cli.php -- -o -u 400
      
    * Create data using a load factor of 10, automatically detecting modules
      and automatically adding relationships.
      $php -f install_cli.php -- -l 10 -o --allmodules --allrelationships
      
    * Generate TeamBasedACL action restrictions for chosen level (check level options in install_config.php)
      $php -f install_cli.php -- -o --tba -tba_level full
      
    * Controlling INSERT_BATCH_SIZE (MySQL Support only for now)
      $php -f install_cli.php -- -o --insert_batch_size 1000
