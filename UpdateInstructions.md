This is already moved to the new home from measureit on github

https://github.com/lalelunet/measureit/wiki

```
#
#
#
#
#old deprecated how to  for history reasons
#
#
#
#
```




Here you find update instructions if you are using a previous version from measureit. If you are new to measureit you can ignore this page. All you need you will find in the download.

## Version 115 -> Version 116 ##

Download the newest version, extract it and change into the new directory.

Update database. You can do this with the following command or if you are  using phpMyAdmin choose SQL and upload the file measureit\_system\_files/install/update\_115\_to\_116.sql

```
cat measureit_system_files/install/update_115_to_116.sql | mysql -uroot -p measure_it
```

These queries will be done in the update\_115\_to116.sql
```
UPDATE measure_system SET measure_system_setting_value = 116 WHERE measure_system_setting_name = "current_version";
ALTER TABLE measure_settings CHANGE measure_timezone_diff measure_timezone_diff FLOAT( 4 ) NOT NULL DEFAULT '0';
CREATE TABLE IF NOT EXISTS measure_notifications (
  measure_notifications_id smallint(10) NOT NULL AUTO_INCREMENT,
  measure_notifications_sensor smallint(3) NOT NULL,
  measure_notifications_name varchar(256) NOT NULL,
  measure_notifications_check_email smallint(1) NOT NULL,
  measure_notifications_check_twitter smallint(1) NOT NULL,
  measure_notifications_notification text NOT NULL,
  measure_notifications_unit varchar(1) NOT NULL,
  measure_notifications_value int(12) NOT NULL,
  measure_notifications_items int(12) NOT NULL,
  measure_notifications_criteria tinyint(1) NOT NULL,
  PRIMARY KEY (measure_notifications_id)
) ENGINE=MyISAM  DEFAULT CHARSET=latin1 AUTO_INCREMENT=1;
INSERT IGNORE INTO measure_data_now (sensor_id, watt, tmpr) VALUES (10, 0, 0), (20, 0, 0), (30, 0, 0);
```

Install python-setupools and twython that is used for tweeting

```
apt-get install python-setuptools
```

```
easy_install twython
```

This will install these libs

twython
http://pypi.python.org/simple/twython/

requests
http://pypi.python.org/simple/requests/

requests-oauthlib
http://pypi.python.org/simple/requests_oauthlib/

Replace the following files:

  * measureit\_system\_files/python/data-input.py
  * measureit\_public\_html/css/measure\_it.css
  * measureit\_public\_html/js/measureit.js
  * measureit\_public\_html/php/measureit\_funktions.php
  * measureit\_public\_html/lng/de\_DE.txt
  * measureit\_public\_html/lng/en\_EN.txt
  * measureit\_public\_html/lng/it\_IT.txt
  * measureit\_public\_html/lng/fr\_FR.txt
  * measureit\_public\_html/lng/nl\_NL.txt



## Version 114 -> Version 115 ##

Download the newest version, extract it and change into the new directory.

Update database. You can do this with the following command or if you are  using phpMyAdmin choose SQL and upload the file measureit\_system\_files/install/update\_114\_to\_115.sql

```
cat measureit_system_files/install/update_114_to_115.sql | mysql -uroot -p measure_it
```

Replace the following files:

  * measureit\_system\_files/python/data-input.py
  * measureit\_public\_html/css/measure\_it.css
  * measureit\_public\_html/js/measureit.js
  * measureit\_public\_html/php/measureit\_funktions.php
  * measureit\_public\_html/lng/de\_DE.txt
  * measureit\_public\_html/lng/en\_EN.txt
  * measureit\_public\_html/lng/it\_IT.txt
  * measureit\_public\_html/lng/fr\_FR.txt

Restart the grabber

## Version 112 -> Version 114 ##

Yes! 114 because of I forgot to insert a file in the package. 113 is the same like 114 :/

In version 114 nearly every core code file has changed and the directory structure is changed too.
Because of this we had to replace the complete code.

Don`t Panic :)

If you are not already root
```
sudo bash
```

STOP RUNNING PYTHON GRABBER! [see FAQ to learn how](https://code.google.com/p/measureit/wiki/FAQ)

This is important or the next step will fail or better... will run endless

Save the old files. Only for the case of ...  :D

In this example your installation from measureit is in the directory /var/www

```
cd /var/www/
mkdir backup-measureit-112
mv * backup-measureit-112
```

You will receive a error message like this

mv: cannot move `backup-measureit-112' to a subdirectory of itself, `backup-measureit-112/backup-measureit-112'

This is ok, Just ignore it.

Now execute the code from the [linux setup page](https://code.google.com/p/measureit/wiki/Linux) from the install supervise/daemontools point.

The only different between the update and a fresh install is the database.

DO NOT execute the database install. Do the following points instead.

Execute the update script for the mysql database from the install folder from version 114:

```
cat install/update_112_113.sql | mysql -uroot -p
```

Or if you are using phpMyAdmin choose SQL and upload the update\_112\_113.sql file

Then go ahead with the install instructions

## Version 111 -> Version 112 ##

Between the last version there are so many differences that it is the easiest way to update is to replace the complete files with the new version and edit the database files again.

Execute the update script for the mysql database from the install folder from version 112:

```
sudo cat install/update_111_to_112.sql | mysql -uroot -p
```

Or if you are using phpMyAdmin choose SQL and upload the update\_111\_to\_112.sql file

The grabber script is written in python. It is working on windows and on linux. The php grabber script is not longer supported from now on. Python and the necessary modules should be installed on the most linux operating systems. On Ubuntu I need to install the mysql module.

```
sudo apt-get install python-mysqldb
```

If you use the windows installation from this site all modules are already installed.



Replace you init file: /etc/init.d/measureit

Edit the database connecting files to fit to your settings:

  * php/class.db.php
  * python/data-input.py


## Version 110 -> Version 111 ##

To update replace the following files
  * index.html
  * js/flot (complete directory)
  * js/measureit.js
  * php/measureit\_functions.php
  * css/measure\_it.css
  * js/jquery-1.4.2.min.js with js/jquery-1.7.1.min.js

remove the following files
  * js/measureit-admin.js

add the following files
  * img (directory)

Run the following queries on the konsole:
```
echo "ALTER TABLE `measure_settings` ADD `measure_timezone_diff` SMALLINT( 4 ) NOT NULL DEFAULT '0';" | mysql -uroot -p
```

Or if you are using phpMyAdmin choose the measure\_it database and run this SQL
```
ALTER TABLE `measure_settings` ADD `measure_timezone_diff` SMALLINT( 4 ) NOT NULL DEFAULT '0';
```


## Version 109 -> Version 110 ##

To update replace the following files
  * index.html
  * js/measureit.js
  * php/measureit\_functions.php
  * js/measureit-admin.js
  * js/jquery-ui-1.8.1/js/jquery-ui-1.8.16.custom.min.js
  * css/measure\_it.css

## Version 108 -> Version 109 ##

Between version 107 and 108 there is no difference. New is a data grabbing script written in python because of php uses 100% cpu on windows systems. If you want to use measureit on a windows system just following the installation instructions in the wiki.

Update: It seems that the file jquery-ui-1.8.1.custom.min.js was broken from packaging. If you want to use measureit-108 replace it with this version:
http://code.google.com/p/measureit/source/browse/trunk/js/jquery-ui-1.8.1/js/jquery-ui-1.8.1.custom.min.js

## Version 107-> Version 108 ##


To Update from version 106 you had to replace the following files:
  * php/measureit\_functions.php
  * php/class.db.php
  * js/measureit\_admin.js
  * index.html ( only neccesary if you are using Internet Explorer > 8 )

  * Run the following queries on the konsole to enable backup rights to the database client:
```
echo "GRANT SELECT , INSERT , UPDATE , DELETE, LOCK TABLES ON * . * TO 'measureit'@'localhost' IDENTIFIED BY 'measureitpasswd';" | mysql -uroot -p

echo "FLUSH PRIVILEGES;" | mysql -uroot -p
```

  * To speed up measureit run: ( recommented for every version of measureit )
```
echo "ALTER TABLE measure_it.measure_watt ADD INDEX time_sensor ( time , sensor );" | mysql -uroot -p
```

If you want to import your google powermeter data add the directory "scripts" in the same directory where are the other directories ( php/js/install/css )

## Version 106-> Version 107 ##

To update from version 105 you just had to replace the files in your webserver directory.

NOTE: If you are running a ubuntu 10.4 DO NOT change the init script. The init script from 11.4 DOES NOT work with earlier versions.


## Version 105-> Version 106 ##

To update from version 104 you just had to replace this files

  * php/measureit\_functions.php
  * index.html ( only neccesary if you are using Internet Explorer )


**Version 104-> Version 105**


If you are using already measureit it is recommendet to follow this instructions step by step or you can destroy your database :)

1. Stop the running process from the data-input.php
This can be done by following command on the konsole:
```
sudo killall -9 cat
```

Then you had to upgrade your database. You will be asked for the root password of the mysql database server you hopefully remember. Copy and paste the following commands to the konsole:
Note for advanced users: If you DO NOT use the install instructions from measureit and have your own setup please make sure that mysql IS NOT connected through a socket file. Otherwise you destroy your mysql binary. Then you had to add a " -S/path/to/mysql.sock" at the end of every command

```
echo "CREATE TABLE measure_data_now (sensor_id tinyint(2) NOT NULL, watt smallint(5) NOT NULL, tmpr float NOT NULL, PRIMARY KEY (sensor_id) ) ENGINE=MyISAM DEFAULT CHARSET=latin1;
" | mysql -uroot -p -Dmeasure_it

echo "INSERT INTO measure_data_now (sensor_id, watt, tmpr) VALUES (1, 0, 0), (2, 0, 0), (3, 0, 0), (4, 0, 0), (5, 0, 0), (6, 0, 0), (7, 0, 0), (8, 0, 0), (9, 0, 0);
" | mysql -uroot -p -Dmeasure_it
```

If you are using MORE THAN 1 SENSOR we had to clean the datebase before we go to the next step. This is very important otherwise you crash your database:
```
echo "DELETE FROM measure_tmpr_hourly WHERE sensor > 1; DELETE FROM measure_tmpr WHERE sensor > 1;" | mysql -uroot -p -Dmeasure_it
```

The last step indipended you are using more than one sensor or just one:
```
echo "ALTER TABLE measure_it.measure_tmpr_hourly DROP INDEX data , ADD UNIQUE data ( hour , time );" | mysql -uroot -p -Dmeasure_it

echo "ALTER TABLE measure_tmpr_hourly DROP sensor;" | mysql -uroot -p -Dmeasure_it

echo "ALTER TABLE measure_tmpr DROP sensor;" | mysql -uroot -p -Dmeasure_it
```

Replace the following files with them from version 104:
  * php/measureit\_functions.php
  * php/data-input.php
  * index.html
  * measure\_it.css - only if you are using Internet Explorer :D

Thats all. Now start the data-input.php process new:
```
sudo /etc/init.d/measureit start
```

## Version 103-> Version 104 ##


To update from Version 102
Stop the running data-import process

Replace the following 3 files:
  * /css/measure\_it.css
  * /php/measureit\_functions.php
  * index.html

Start the data-import.php and have fun :)