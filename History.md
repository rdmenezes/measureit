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



**Version 116**

  * Fix bug that will avoid price settings.
    * https://code.google.com/p/measureit/issues/detail?id=19
    * https://code.google.com/p/measureit/issues/detail?id=27
  * Fix start page showing 0 instead of usage last hour.
    * https://code.google.com/p/measureit/issues/detail?id=29
  * Fix PVOutput api key bug in sensor settings.
    * https://code.google.com/p/measureit/issues/detail?id=32
  * Fix sensor type error in data-input.py.
    * https://code.google.com/p/measureit/issues/detail?id=33
  * Add missing default values to db.
    * https://code.google.com/p/measureit/issues/detail?id=34
  * Fix bug at sensor delte.
    * https://code.google.com/p/measureit/issues/detail?id=35
  * Fix curves in PVOutput.
    * https://code.google.com/p/measureit/issues/detail?id=36
  * Fix system detection
    * https://code.google.com/p/measureit/issues/detail?id=51
  * Add support for Fahrenheit.
    * https://code.google.com/p/measureit/issues/detail?id=40
    * https://code.google.com/p/measureit/issues/detail?id=43
  * Correct hourly / weekly consumption calculation
    * https://groups.google.com/forum/#!topic/measureit/YPNLH8NJiOI
  * Hide system and sensor settings in demo mode
  * Add notifications per twitter or email
  * Move email settings in admin menu

**Version 115**

  * Fix last hour bug on start page.
    * https://code.google.com/p/measureit/issues/detail?id=23
  * Fix 9 sensor adding bug.
    * https://code.google.com/p/measureit/issues/detail?id=25
  * Fix data spikes from not existing clamps.
    * https://code.google.com/p/measureit/issues/detail?id=26
  * Add option to send data to pvoutput.

**Version 113**

  * Add Italian and French language.
    * https://code.google.com/p/measureit/issues/detail?id=24
  * Fix January bug on costs page.
    * https://code.google.com/p/measureit/issues/detail?id=22
  * Fix bug in measureit\_functions.php.
    * https://code.google.com/p/measureit/issues/detail?id=18
  * Fix broken mysql database connections.
    * https://code.google.com/p/measureit/issues/detail?id=16
  * Add debug and logging functions to python data grabber
  * Fix security issue that enables to see database username/passwd with browser
  * Add update check to notice if a new version is available
  * Raspberry Pi ISO image with pre installed measureit in version 113

**Version 112**

  * Display usage data from all clamps.
  * Multiple prices per day. Price changes are supported.
    * https://code.google.com/p/measureit/issues/detail?id=9
  * Add Sensor ID 0 ( default sensor id from currentcost )
    * https://code.google.com/p/measureit/issues/detail?id=7
  * Fixed timezone bug
    * https://code.google.com/p/measureit/issues/detail?id=13
  * New grabbing script written in python
    * https://code.google.com/p/measureit/issues/detail?id=12
    * https://code.google.com/p/measureit/issues/detail?id=14
  * Multiple language support

**Version 111**

  * In the sensor overview there are now arrows to add additional data to the graph. Always + or - 2 hours
  * Usage graphs per day and per hour from the last 365 days
  * Set the difference in hours from the gmt time. + or - values are possible. This is a per sensor setting.
  * Admin part was not useable with chrome
  * Errormessages from php when using date/time functions
  * 404 not found excanvas.min.js
  * Update from jquery and flot

**Version 110**
  * In version 109 there is missing the install folder in the package. This version is the same like 109 but complete :)

**Version 109**

  * Added 2 new charts to display last 7 day usage per hour and last 12 months per day usage.
    * http://code.google.com/p/measureit/issues/detail?id=10
  * fixed broken file
    * http://code.google.com/p/measureit/issues/detail?id=3
  * fixed typo
    * http://code.google.com/p/measureit/issues/detail?id=11
  * fixed php error
    * http://code.google.com/p/measureit/issues/detail?id=4



**Version 108**

  * Add a python script to grab the data from the currentcost device

**Version 107**

  * Add backup function
  * database update to increase page speed
  * add google powermeter data import script
  * ie 9 fixes

**Version 106**

  * seperate the measureit java script from the index.html file into 2 new files
  * js/measureit.js
  * js/measureitadmin.js
  * fix the cost display from the start page with new created sensors
  * create new start script for ubuntu 11.4
  * store 0 watt values to make nice charts
  * some small bug fixes

**Version 105**

**NOTE: THIS VERSION IS NOT WORKING WITH UBUNTU 11.4.**

  * Fix bug with temperature function and some additional Internet Explorer issues

**Version 104**

  * Database size:
The storage measureit needs will be reduced about 40%. This is because of the temperature data was seperatet from the sensors. They are from the base station and not from the sensors itself.
  * Compatibility:
measureit now is working with Internet Explorer ( testet with v.8 )
It looks not perfect like in all other browsers but its quite ok. Maybe I found some time I will fix the rest :)
  * Page speed:
If there are more then some million database entries ( about 1,5 years of running with 2 sensors ) the start screen needs about 4 seconds to load. Now it is reduced to 20 milliseconds
  * Fixed bugs:
New added sensor position displays the costs without considered the start time and uses the data from the last sensor position too.
  * Some smaller bugs that needs not to explain in detail

**Version 103**

  * Sensor statistics added
See the power and money consumptions of all sensors sorted after sensor position and then after year - month - day

**Version 102**

  * A cleaned version.
All demo and developer files from jquery ui was removed. If you have version 101 installed you do not need to upgrade. There is just one little difference between this version and 101 that makes the fonts smaller.

**Version 101**

  * First working version