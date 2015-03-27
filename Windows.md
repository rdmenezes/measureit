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



## Note: This instructions are for version 112. This is the latest version I have tested. There are some users out there running the newest version on windows.  Feel free to send me feedback if you try to run newer versions on windows. ##

You had to install some software to get this thing running. The URLs to the pages are from the packages I use. These sites must not be the "original pages". They come up on my search in the internet. There are certainly more sites that share these packages...


PLEASE NOTE: I WILL NEVER EVER DO ANY SUPPORT FOR YOUR WINDOWS SYSTEM PROBLEMS!
YOU CAN ASK FOR SUPPORT FROM THE POINT YOU INSTALL MEASUREIT.


#### First you need the driver from currentcost to connect to your device. ####
[http://currentcost.com/software-downloads.html](http://currentcost.com/software-downloads.html)

#### XAMMP ####
The server structure XAMPP you can get from apachefriends. Download the installer version. Available Apache and Mysql as a service.

[http://www.apachefriends.org/en/xampp-windows.html](http://www.apachefriends.org/en/xampp-windows.html)

#### Python Packages ####
The grabber script is written in python. You had to install python and the necessary modules.

FROM NOW USE THE 32 BIT VERSIONS even if you are running a Windows with 64 bit support.

#### Python 2.7.2 ####
[Python 2.7.2 Windows Installer](http://www.python.org/getit/)

#### MySQL-python ####
The database package for python to talk with your mysql server

[MySQL-python-1.2.3.win32-py2.7.exe](http://www.codegood.com/archives/129)

#### pyserial ####
The serial package to talk with your currentcost device.

IMPORTANT NOTE:
If you are on a 64bit system you had to use the version 2.4 from pyserial and you need the additional Python Win32 Extensions pywin. Otherwise it will not work. If you are not sure which windows version you are running take the 2.4 version from pyserial and install pywin. It works on both systems

**Windows 32 bit version**

[pyserial-2.5.win32.exe](http://sourceforge.net/projects/pyserial/files/pyserial/2.5/)


**Windows 64 bit version**

[pyserial-2.4.win32.exe](http://sourceforge.net/projects/pyserial/files/pyserial/2.4/)

[pywin32-216.win32-py2.7.exe](http://sourceforge.net/projects/pywin32/files/pywin32/Build216/pywin32-216.win32-py2.7.exe)



#### Finally the installation from measureit starts ####

Known issues and solutions when you are running into problems during the setup you will find on the [faq page](http://code.google.com/p/measureit/wiki/FAQ) in the wiki

From here I will answer questions if you have any problems you will not found in the [faq page](http://code.google.com/p/measureit/wiki/FAQ) .
Then create a new [Issue](http://code.google.com/p/measureit/issues/list)


#### Download the latest version from measureit ####
http://code.google.com/p/measureit/downloads/list

Create the directory C:\xampp\htdocs\measureit

Extract the downloaded measureit package and put in in the directory C:\xampp\htdocs\measureit

#### Install the database ####
Open a browser and type in the location bar ( not in the google search field .... ) "localhost".
Choose your language

You will find on the left side the point "phpMyAdmin"


Click on import on the top of the window.
Choose the following file:
C:\xampp\htdocs\measureit\install\createdb.sql

Click OK

#### Start grabbing the data ####
Now your measureit installation should be complete and if you type "localhost/measureit" in your location bar you should see the start screen from measureit

At this point it is time to start the grabbing process. Start the "cmd.exe". You can type it in the search field in your start menu. Windows will find it. Copy and paste this line into the cmd window. Now the data should be grabbed. Leave the cmd window open.

If you are more familiar with windows systems than me feel free to share you information about creating a system service that will start automatically with windows

C:\Python27\python.exe C:\xampp\htdocs\measureit\python\data-input.py

Delete the install folder and the scripts folder.

C:\xampp\htdocs\measureit\install

C:\xampp\htdocs\measureit\scripts


[AND NOW GO TO THE FAQ PAGE AND READ THE SECURITY PART. THIS IS IMPORTANT!       :)](http://code.google.com/p/measureit/wiki/FAQ)


[Here you will find informations to set up your sensors and clamps and other useful informations how to use measureit](https://code.google.com/p/measureit/wiki/Howto)