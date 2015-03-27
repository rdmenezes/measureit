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



Measureit runs on a Raspberry Pi without problems.

I recommend the usage from a pre configured iso image where all software is installed.

The installation from the software is NOT the same that is described in the [Linux](https://code.google.com/p/measureit/wiki/Linux) part.

The setup is lightweight, very fast and did not need much system resources so you can do additional things with your pi.

Just download and copy it on the SD-Card. All services runs with system start.

The measureit iso requires an 4 GB SD-Card but more space is always good :)

It is based on the [Raspbian “wheezy”](http://www.raspberrypi.org/downloads)

Software that was additionally installed on the original image:

php5-fpm

nginx

mysql

samba

daemontools

Except daemontools all packages are from the raspian sources.

If you are interested how the setup is done in detail you can take a look at [my copy & paste wiki](http://71421.de/wiki).
**Be warned**. It is not well documented and you should at least know how to use a text editor on the console. In this example vim ;)

php5-fpm and nginx are controlled with supervise.


The username and the password from the image is the default one from the raspian image.

User: pi
Pass: raspberry


The directories from measureit you can reach per samba share.

/web - public files

/usr/local/measureit - private files f.e. the data grabber

The username is web and the password is raspberry

You can reach the Raspberry Pi with 2 pre configured ip adresses and with the ip you get from dhcp

10.0.0.99 with the gateway 10.0.0.1

192.168.0.99 with the gateway 192.168.0.1

[Here you will find informations how to flash the image](http://elinux.org/RPi_Easy_SD_Card_Setup)

[To enlarge your image if you have a SD-Card > 4GB take a look here](http://elinux.org/RPi_Resize_Flash_Partitions)

The download is to big to hosting it on google code.

So I share it with a download service. Warning. It uses flash :(

If you know an other one where big files are no problem please let me know

Feedback welcome :)

Version 116

2014-04-18-wheezy-raspbian-measureit-116-4gb.img.zip (1.10 GB)

https://mega.co.nz/#!PVMjHYiC!sCG1c4tpUiINOUKGEg7bIfZWOVMxsGpxJO5jhVd40vM

Version 115

2013-06-23-wheezy-raspbian-measureit-115-4gb.img.zip (613.3 MB)

https://mega.co.nz/#!WJcGibRA!RWjoBw7W3iJIGBepwmBI4QyepQomeQ0PYnBsuqziZCk


Version: 114

2013-02-09-wheezy-raspbian-measureit-114-4gb-final.tgz (615.4 MB)

https://mega.co.nz/#!mA1nQJTb!FJiWmz7Z55PNqe7OdzCVh2Cug1ZTDlan4DI1pyJCcvM



older versions

Version 113

2012-12-16-wheezy-raspbian-measureit-113-4gb-complete.tgz (610.1 MB)

https://mega.co.nz/#!3ZtQhQSJ!KEi27jJ2oMwA2St9joIvUAN6O38zqqELZcTb7K-zOTI