## Install on a already running Linux ##

The data cable driver you need is available since kernel version 2.6.30

**If you have already a running Linux test if your kernel support the data cable:**

If you have a older kernel then you had to upgrade to a newer version.
The kernel you use you can find out with:

`uname -a`

You will need:

a webserver ( apache, lighttpd, nginx, etc )
mysql database server ( version > 5 )
php5

All further informations you will found below


Known issues and solutions when you are running into problems during the setup you will find on the [faq page](http://code.google.com/p/measureit/wiki/FAQ) in the wiki

## Starting with a new system: ##

Debian Lenny / Squeeze does not work with the data cable so I use a [Ubuntu Desktop Version](http://www.ubuntu.com/) that is easy to install.
After downloading and install you have a ready to use linux system.
Open "Konsole". You will find it under applications.

If you get the data cable working on a debian system feel free to tell me how :)

On a Raspberry Pi both data cables are working. The old black one and the new white with the led are tested.

Copy and paste every from the following lines into the konsole and press enter. During the installation you will asked for a password for the database user root. Remember this password!
You can copy and paste each code block complete but do not forget to press enter to execute the last command from the block  ;)

If you are not root
```
sudo bash
```


install software. This can take several minutes on a Rasperry Pi  :)

NOTE: Some user report problems with the xbmc Image on the Raspberry PI because of there is running already a apache web server and php is installed already. So do not install the apache2 server again.

```
apt-get update
apt-get install php5-cgi php5-cli apache2 mysql-server libapache2-mod-php5 php5-mysql python-setuptools
```

There are several ways to run the grabber. I prefer the usage from supervise/daemontools ([supervise home](http://cr.yp.to/daemontools.html)). It is a control daemon that will start the grabber on boot, control the grabber and restart the grabber if it is not running.

In the download there are some user generated start / stop scripts. I did not test them. Maybe there is one that is matching your setup. You will find them in measureit\_system\_files/install

You can also start it manual on system start. Since version 113 the grabber is very stable and does not crash.

command to start manually
```
/usr/bin/python /usr/local/measureit/python/data-input.py &
```

install supervise/daemontools
```
mkdir -p /package
chmod 1755 /package
cd /package
wget http://cr.yp.to/daemontools/daemontools-0.76.tar.gz
tar xvzf daemontools-0.76.tar.gz
cd admin/daemontools-0.76/src
```

```
perl -pi -le 's/extern int errno;/#include <errno.h>/' *.[hc]
```

```
cd ..
package/install
mkdir /etc/servers
```

```
easy_install twython
```

Now all required software is installed.

Next we download and setup Measureit. You will asked for the user password you entered during the setup from Ubuntu. Replace the XXX with the current version. [The newest you will find in the downloads](https://code.google.com/p/measureit/wiki/Download)

```
cd /usr/local/src
wget https://mega.co.nz/#!6QUgHJIA!cuMLTMEcWe_-EOGoTXhygDLqQFxNfH4Q8ZSjFp-t3X0
tar -xvf measureit-XXX.tar
cd measureit-XXX/measureit_system_files/
```

setup the database. You will asked for the database root password you hopefully remember :)

```
cat install/createdb.sql | mysql -uroot -p
```

copy the supervise run script

```
cd install 
cp -R measureit /etc/servers/measureit
chmod +x /etc/servers/measureit/run
cd ..
```

remove the install directory

```
rm -R ./install
```

remove the scripts directory if you are not plan to use one of them. If you plan to use one of the scripts do not forget to delete this directory after using.

```
rm -R ./scripts
```

First we had to create a new directory for the system files. This are files that are private and should not available in the internet. In this example the web server needs the user permission www-data. If your web server needs an other user change www-data to your settings.

```
mkdir /usr/local/measureit/
cp -R * /usr/local/measureit
chown -R www-data:www-data /usr/local/measureit/
```

copy the Measureit code to the webserver directory and give the webserver the rights to read and write the directory

```
cd ../measureit_public_html
cp -fr ./* /var/www
chown -R www-data:www-data /var/www
chmod -R 775 /var/www
```

The grabber script is written in python. It is working on windows and on linux. Python and the necessary modules should be installed on the most linux operating systems. On Ubuntu I need to install the mysql module.

On a Raspberry Pi you had to install the serial and the mysql module

```
apt-get install python-mysqldb python-serial
```

If you get error messages from python about missing modules you had to install these. Modules used by measureit are:
```
serial
re
MySQLdb
datetime
warnings
time
threading
sys
platform
simplemail
urllib2
traceback
os
subprocess
```

start grabbing the data

```
cd /service
ln -s ../etc/servers/measureit
```

You are done!
Open your Browser an type in localhost. You can see the start page. Go to the tab Setup and change the data from the sensor or add additional sensors. Have a lot of fun :)

[AND NOW GO TO THE FAQ PAGE AND READ THE SECURITY PART. THIS IS IMPORTANT!       :)](http://code.google.com/p/measureit/wiki/FAQ)

[Here you will find informations to set up your sensors and clamps and other useful informations how to use measureit](https://code.google.com/p/measureit/wiki/Howto)