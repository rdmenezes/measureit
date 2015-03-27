The FAQ is already moved to the new home from measureit on github

[Go to the FAQ](https://github.com/lalelunet/measureit/wiki/Help---FAQ)

```
#
#
#
#
#old deprecated faq for history reasons
#
#
#
#
```


If there are any questions about using or installing measureit feel free to ask  them :)
Just create a new [issue](http://code.google.com/p/measureit/issues/list).

You will find also contact on TWITTER:

[@measureitsoft](http://twitter.com/#!/measureitsoft)

All commands had to be done as user root. On the Raspberry PI you can change to root with

```
sudo bash
```

### FAQ ###

**Does my system support the USB cable?**

Plug in the cable and run the following command in your konsole:
```
lsusb
```
You should see a entry like this:
Bus 002 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port

Then your USB cable should be supported from your system

On windows systems please read the information from the currentcost website



**Does my system receive data from my currentcost device?
Something is not working. Why not?**

Measureit writes infos into a logfile. There you can see error messages or debug informations.

```
tail -f /tmp/measureit.log
```

To get detailed informations you can start the grabber manually.

To run the grabber manually you had to stop the currently running measureit process first. On the PI image you can do this with
```
svc -d /service/measureit
```

To start it after debugging do a
```
svc -u /service/measureit
```

This will write some debugging information in the measure.log
```
/usr/bin/python /usr/local/measureit/python/data-input.py test
```

To create a log file from the XML Output from your Current Cost device you can do the following.

This will write the original XML into the file /tmp/mylogfile.txt
```
/usr/bin/python /usr/local/measureit/python/data-input.py test > /tmp/mylogfile.txt
```

You should now see the xml data stream and in the log are detailed informations.
Press ctrl+c to get back control of the konsole

On windows systems you can use the "C2 Terminal" software from currentcost.

To get more debugging informations in the log file you can start the grabber with "debug".

```
/usr/bin/python /usr/local/measureit/python/data-input.py debug
```

If you want to see very detailed informations you can start it with "debug v".

This will create very very very much informations in the log.

**How can I read the measureit.log?**

You have several options to do this.

> If you want to read the log in real time you can open a second console to your instalation and do a

```
tail -f /tmp/measureit.log
```

To show the log you can do a

```
cat /tmp/measureit.log
```

Or if the log is too long you can read it in parts. Every time you press space you get the next part

```
cat /tmp/measureit.log | more
```

**I receive no data although the system supports the USB cable**

You can try to load the USB driver again. Do this with the following command.

```
sudo modprobe -r pl2303
sudo modprobe pl2303
```

The baud rate from the the USB interface should be 57600. Set this with the following command. Yes 2 times ;)
```
sudo stty -F /dev/ttyUSB0 57600
sudo stty -F /dev/ttyUSB0 57600
```


**I receive the XML data but nothing was displayed on the website**

Control that your appliance id is the same like the sensor id in measureit. You will find the appliance id in the right bottom corner ( Envi ). See the instructions from the currentcost website how to pair a device. [Here you will find the installation from the envi](http://currentcost.com/product-envi-installation.html)

In the xml data you will find the device id from your transmitter and how it is paired with your currentcost device. There you find something like this:

`<msg><src>CCdsb>00385</dsb><timemsg><src>CC128-v0.12</srtime>06:52:19</time><tmpr>20.3</tmpr><sensor>1</sensor><id>01674</id><type>1</type><ch1><watts>00236</watts></ch1></msg>`

`<sensor>1</sensor>`


In this example make sure that your sensor has id 1. The start screen from the envi is sensor 0.


**I install a system into a virtual machine software. I do not found the /dev/ttyUSB0 device**

I do not have any experience with virtual systems. However... If the device is a serial port in your linux guest you will find it under /dev/ttyS0, /dev/ttyS1, /dev/ttyS2 ,....

On Windows systems it is the com3 device.

I take a look in google and found a very good instruction page how to get the device into virtual machine. Thanks to the author!  :)
[http://techtooltip.wordpress.com/2008/09/12/using-host-serial-port-from-guest-in-virtual-box/](http://techtooltip.wordpress.com/2008/09/12/using-host-serial-port-from-guest-in-virtual-box/)

**I get a white screen after installing**

If you get a white page with no information after installing or update there is mostly an error in your config.

Try the following steps:

  * You can call the follwing URL to get a clear error message: ```
http://YOUR-CURRENT_URL/php/measureit_functions.php?do=navigation_main```
See also:
https://groups.google.com/forum/#!searchin/measureit/ubuntu/measureit/N6TySMsQ1ws

  * I do a programming error so your second step should be [to take a look here](https://code.google.com/p/measureit/issues/list)

  * Detailed debug informations you can get if you start the grabber manually with the debug parameter "debug v". Informations how to do this you will find above in "Does my system receive data from my currentcost device?". You need the latest grabber version to do this:
https://measureit.googlecode.com/svn/trunk/measureit_system_files/python/data-input.py

  * If there is no solution please create a new [issue](http://code.google.com/p/measureit/issues/list)

**Security**

I believe that the most of you will use measureit with a public dyndns domain. There is no problem with this idea but note that everyone who knows this domain or find it with a search engine can add sensor or sensor positions or if this is a evil person can **delete all your data**!

To make shure that this is not happend open the file php/measureit\_functions.php with a text editor and replace the following line at the beginning of the script:

replace

`$demo = false;`

with

`$demo = true;`


After changing this line it is not possible to do the following actions:

see/download/create/delete backups, add/delete sensors, add/delete sensor positions


Change the mysql password!

The setup from measureit set a default password with the value "measureitpasswd". If you decide to make measureit available in the internet you **MUST** change it. Replace the XXXXXXXXXXXXXX with your new password. If you use windows and the xammp server you can change the password from the mysql user in phpMyAdmin. You will find it in the user rights settings.

```
mysql -uroot -p
use mysql;
update user set Password = password('XXXXXXXXXXXXXX') where User = 'measureit';
flush privileges;
```

Then edit /usr/local/measureit/measureit.cfg.php and change the password
```
$database_passwd                 = "measureitpasswd";
$database_passwd                = "XXXXXXXXXXXXXX";
```

You had to restart the grabber

**Does measureit supports multiple clambs per sensor?**

Since version 112 you will have clamp support.
**Thanks to Ivo from Switzerland**. He is the gui who sponsored the clamps for developing.

**How can I stop the python grabber?**

On windows machines it should be enough to close the cmd window or shut down the service if measureit runs as a service. On unix / linux machines you must kill the process.

Find the ProcessID
```
ps auxf | grep data-input
```

You will get something like this

root      3959  2.5  2.0  48988  9176 ?        Sl   Feb11  91:56 /usr/bin/python /usr/local/measureit/python/data-input.py

In this case The PID is 3959

```
kill -9 3959
```

If you are running measureit under supervise shut down the process with
```
svc -d /service/measureit
```

To start it again
```
svc -u /service/measureit
```

**Does measureit supports IAMS (Individial Appliance Monitor)?**

Yes. IAMs are the same like a sensor. Pair your IAM with your Envi and add a sensor in the admin menu from measureit. Then restart the grabber.


**Measureit does not work with Internet Explorer version X**

The Internet Explorer is a bug and not a browser. I do not waste any private lifetime to get things working with IE. Measureit works with Safari, Firefox, Chrome and Opera.

**There is a tracking code inside. Do you observe me?**

Yes. I know everything about you. The name from your cat is xxx...

NO! Fun aside. The tracking counts the users from measureit. And I am proud that I can say that the tracking told me that currently there are about 300 user that use measureit and about 30 people use it daily. (2013.06.15). Nothing more! To know that people like and use my software is a good reason to go ahead with the work.

If you do no like that I count your usage from measureit you can remove the analytics code from the measureit\_public\_html/index.html. Just delete the the the  script part that begins on line 24

**Measureit does not upload data to PVOutput**

To find out why no data will be uploaded to PVOutput you can start the grabber manually with the debug parameter.

You should see informations about the sensor and systems setting found by measureit in /tmp/measureit.log. This will look like this:

```
2014-05-24 09:05:31,318 INFO Try to get sensor settings from sensor_settings_get
2014-05-24 09:05:31,344 INFO Sensor 0 Check if there are any PVOutput settings for this sensor
2014-05-24 09:05:31,350 INFO Sensor 0 has a PVOutput ID
2014-05-24 09:05:31,355 INFO XXXXX
2014-05-24 09:05:31,361 INFO Sensor 0 Now checking if there is a PVOutput API key
2014-05-24 09:05:31,366 INFO Sensor 0 has no PVOutput API. Next check if there is a global API key
2014-05-24 09:05:31,375 INFO Found PVOutput API key in the system settings.
2014-05-24 09:05:31,380 DEBUG XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
2014-05-24 09:05:31,400 INFO Using PVOutput for this sensor
```

Measureit uploads data every 5 minutes to PVOutput. If everything is fine you will see something like this:

```
2014-05-24 09:10:13,842 INFO Try to update PVOutput from sensor : 0 Output: OK 200: Added Status
2014-05-24 09:10:13,850 DEBUG http://pvoutput.org/service/r2/addstatus.jsp?key=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX&sid=XXXXX&d=20140524&t=11%3A10&v2=92&v5=27.9
```

If not you will see the error message that returns from PVOutput.


**HTTPError: HTTP Error 400: Bad Request**

If you can see this error in the measure it.log there is something wrong with the settings in PVOutput in your system. Mostly you send more watts that are possible with your system settings in PVOutput.

Then copy the URL under this error and paste it in your browser. There you can get a detailed error.

[Detailed infos about the error you can found here in the part "Error Messages"](http://pvoutput.org/help.html)

**After adding a sensor / clamp there is "null" displayed as clamp name**

The sensor / clamp name is displaying the latest position from the sensor. If you do not add a position in the sensor / clamp settings it will display "null"

**How to install phpMyAdmin to make the SQL stuff easier?**

Do not try to get it running with apt-get. The measureit image is designed to be fast with no overhead installed. If you do it with apt-get a lot of useless software is installed too and sometimes you can get problem with missing dependents.

You can just download it and move the extracted folder into /web/measureit and then you can use it.

http://measureit/phpMyAdmin

WARNING! If your measureit installation is reachable to the internet RENAME the folder to something like:

/web/measureit/you\_can\_not\_guess\_how\_my\_name\_is

This is because of there are many automated bots outside there that are scanning for folder names like "phpMyAdmin" or "pma" to broke into your system with known security issues

**Can I use webmin on your image**

Yes you can but you should not!

This means not that the measureit image is not compatible with it. This is because of it will doing things in the background you possible not understand and you was not the first user of measureit that click on a update button and then the image is crashed and not longer working.

It is a cool software that helps to learn how things are working that nothing you want to use on a production system :)

**Is there a API to use the usage data in other applications?**

Yes. Take a look here:
https://code.google.com/p/measureit/wiki/API_Documentation