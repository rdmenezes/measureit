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



# Usage / Setup from measureit #

Here you will find the options you can set in measureit. If you run into problems see the  [FAQ](https://code.google.com/p/measureit/wiki/FAQ)

## Setup ##

  * Add Sensor
    * Here you can add new sensors. Choose the sensor id witch is configured in your currentcost device. The default position is 0. If you have more than one sensor then the sensor id is the screen id from the cc device. [See the installation notes from currentcost](http://currentcost.com/product-envi-installation.html). You must restart the grabber script and reload the website

  * Add Clamp
    * Is there more than 1 clamp at your sensor you can add new clamps. If there is only 1 clamp at the sensor DO NOT add this clamp. It is not necessary. If you use for example 3 clamps you had to add all 3 clamps. You must restart the grabber script and reload the website. If you do not see your changes after reload try to delete the browsercache.

  * Backup / Export
    * You can use this feature if you are running measureit on a linux system. It will create a complete backup from your measureit installation. This backup includes all usage data.

  * System settings
    * If you will use global prices for all sensors then you can add your price here.
    * If the timezone setting is used all sensors will be in the same timezone.
    * If you are using PVOutput you must set here your PVOutput API key. If you are using more than 1 account you can set a key on each sensor.
    * Choose your language. ( You had to reload the windows )
    * Set your google email account here to receive info if there are problems with your installation or to receive notifications about sensor usages. If you are using the 2-step verification you had to [create an application specific password](https://support.google.com/accounts/answer/1070457?hl=en&ref_topic=1099588)
    * Set your twitter app details here to send notifications about usage to twitter. [Details](https://code.google.com/p/measureit/wiki/Twitter)



> ## Sensor settings ##

  * Positions
    * If you will measure the power consumption from different devices you can add a new position for each device. So if you decide to measure your TV add the position TV and add a new position for every new device you want to measure. Every sensor or clamp should have at least 1 position. The position name is used in the top navigation as current sensor name. If you delete a position only the position will be deleted. The usage data is not lost.

  * Settings
    * If the timezone setting from a sensor or clamp is different from the default system setting you can change it here. Every sensor even every clamp can be in his own timezone :)
    * Here you can set the currency from your country. It is just a text that is displayed in measureit where prices will shown. The default setting from new sensors and clamps are Euro
    * If you wish to hold history data for a different period of time than the default setting from 365 days you can overwrite it for every sensor or clamp. You must restart the grabber script after changing this setting.
    * Here you can set a PVOutput API key if it is different from the key in the system settings. This is useful if you own more than 1 PVOutput account.
    * Does this sensor sent usage or production data. This information is currently used to reporting data to PVOutput.
    * If you are using PVOutput you must here set the system id from your sensor.
    * Prices can be overwritten for every sensor or clamp if the sensor is using different prices than the prices in the system settings.
    * Delete sensor / clamp. You can choose to delete only the sensor or the sensor including all usage data, positions, etc
Notifications
      * Define notifications about the usage data from the sensor / clamp. You had to set either a googlemail account or your twitter app settings in the system setting to use this feature



> ## Prices ##

  * You can setup multiple prices per day. To create a price chose the date from where this price is and add the first time range and the price for it. The price is the price for 1 kwh. F.e. 0.2218 sFr/Pond/Euro/Yen. If the time range is from 06:00 AM in the morning until 10:00 PM ( 06:00 - 22:00 ) then choose 06:00 AM - 09:59 PM. After saving you can add more timeframes. If your energy provider is changing your price you can add a new price.

## Clamps and sensors ##

  * Clamps are internally the same as sensors. You can add clamps to any sensor you use. After adding clamps you can see a plus sign in front of the sensor name in the top navigation. To see the clamps from a sensor you can click on it to expand or reduce the navigation. If a sensor has only 1 clamp installed the usage data will be shown under the sensor. With multiple clamps the sensor usage you can see is the sum of all clamps. So if clamp 1 needs 200 W and clamp 2 300 W the sensor will shown 500 W as usage. Every  clamp should have a position. It will shown as clamp name in the top navigation.

## History data ##

  * The old detailed data will be delete after the time period is saved in the sensor / clamp settings. The default setting is 365 days. To deactivate it you can set it to 0.

3 Sensors where 1 sensor has 3 clamps need about 800 MB per year. These are the data that show the usage every second. The hourly, daily, monthly usage data will not deleted. This means you do not lost your consumption data or the costs. You lost the ability to see how many watt will be used on 06:53:13....  :)