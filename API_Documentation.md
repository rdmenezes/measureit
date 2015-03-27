This is already moved to the new home from measureit on github

https://github.com/lalelunet/measureit/wiki

```
#
#
#
#
#old deprecated api  for history reasons
#
#
#
#
```

# Api Documentation #

To use the data from measureit in other applications there is a option to make requests that delivers data in JSON format. Some older options that are not ported to JSON already delivers a javascript object that is used in the graphs. They include a timestamp in JS milliseconds ( timestamp+000 ) and the data.

This documentation shows currently only the option to receive data. Currently I do not see a sense to describe the options to change / save settings.

The request URL is always http://YOUR-MEASUREIT-IP/php/measureit_functions.php

You had to send the parameter do with the wanted action. The action name is mostly practical.

Format: measureit\_functions.php?do=do\_something

The sensors with ID > 10 are the clamps. Sensor 21 is Sensor 2 Clamp 1.

To receive settings data like usernames, passwords or api keys from a sensor the demo parameter at the beginning of the measureit\_functions.php had to be false. Otherwise the values are always empty.

$demo = false;

Changeable parameters are always marked. If you change a time period parameter to a higher value you had to make sure that there is no timeout from php. In the measureit Pi images the timeout is set to 30 seconds.

## Available options ##

### Get usage data ###

  * ?do=sensor\_history\_week

Parameter:
  * &sensor=1 ( Changeable. Format numeric )
  * &timeframe=static
  * &unit=day
  * &unit\_return=timeframe
  * &unit\_value=8 ( Changeable. Format numeric )
  * &table=measure\_watt\_hourly
  * &arrange=false

Delivers hourly usage data sorted after the number of the last days defined in the unit\_value parameter

```
{"2014-02-21":{"0":{"data":"0.0045"},"1":{"data":"0.0045"},"2":{"data":"0.00449741"},"3":{"data":"0.00450303"},"4":{"data":"0.0045"},"5":{"data":"0.0045"},"6":{"data":"0.00447778"},"7":{"data":"0.0645445"},"8":{"data":"0.0723277"},"9":{"data":"0.0731574"},"10":{"data":"0.0735525"},"11":{"data":"0.0733089"},"13":{"data":"0.072459"},"14":{"data":"0.0734436"},"15":{"data":"0.0732808"},"16":{"data":"0.0726308"},"17":{"data":"0.0714459"},"18":{"data":"0.0718565"},"19":{"data":"0.0726667"},"20":{"data":"0.0383333"},"21":{"data":"0.00450207"},"22":{"data":"0.0045"},"23":{"data":"0.0045"}},"2014-02-22":[{"data":"0.00449721"},{"data":"0.0045"},{"data":"0.00450216"},{"data":"0.0045"},{"data":"0.0045"},{"data":"0.00450244"},{"data":"0.00449669"},{"data":"0.00450259"},{"data":"0.0488522"},{"data":"0.0723064"},{"data":"0.0718899"},{"data":"0.0736798"},{"data":"0.0724478"},{"data":"0.0725202"},{"data":"0.0706014"},{"data":"0.0715397"},{"data":"0.0724739"},{"data":"0.0693864"},{"data":"0.071224"},{"data":"0.0721087"},{"data":"0.0460617"},{"data":"0.00450442"},{"data":"0.0045"},{"data":"0.00449791"}],"2014-02-23":[{"data":"0.0045"},{"data":"0.0045"},{"data":"0.00450216"},{"data":"0.00449758"},{"data":"0.00450311"},{"data":"0.00449772"},{"data":"0.0045023"},{"data":"0.00449758"},{"data":"0.0509528"},{"data":"0.0738884"},{"data":"0.0744538"}]}
```



  * ?do=sensor\_history\_year

Parameter:
  * &sensor=1 ( Changeable. Format numeric )
  * &timeframe=static
  * &unit=day
  * &unit\_return=timeframe
  * &unit\_value=365 ( Changeable. Format numeric )
  * &table=measure\_watt\_daily
  * &arrange=month

Delivers daily usage data grouped by year-month independent from the unit\_return parameter that defined the number of days.

```
{"2014-01":{"05":{"data":1.6578},"06":{"data":1.62309},"07":{"data":1.57427},"08":{"data":1.55603},"09":{"data":1.56769},"10":{"data":1.64987},"11":{"data":1.61158},"12":{"data":1.4652},"13":{"data":1.50532},"14":{"data":1.53118},"15":{"data":1.50466},"16":{"data":1.43489},"17":{"data":1.41757},"18":{"data":1.3154},"19":{"data":1.33738},"20":{"data":1.2775},"21":{"data":1.28787},"22":{"data":1.06489},"23":{"data":1.1875},"24":{"data":1.13209},"25":{"data":1.03655},"26":{"data":1.00981},"27":{"data":1.05824},"28":{"data":0.770074},"29":{"data":0.922087},"30":{"data":1.09059},"31":{"data":1.23228}},"2014-02":{"01":{"data":0.965487},"02":{"data":0.954119},"03":{"data":1.03189},"04":{"data":1.06805},"05":{"data":1.15937},"06":{"data":1.0089},"07":{"data":0.961926},"08":{"data":1.00583},"09":{"data":0.975157},"10":{"data":1.00881},"11":{"data":0.995748},"12":{"data":1.11255},"13":{"data":1.09332},"14":{"data":1.04882},"15":{"data":1.01604},"16":{"data":1.04703},"17":{"data":1.03087},"18":{"data":1.00895},"19":{"data":1.02899},"20":{"data":1.05076},"21":{"data":1.09432}}}
```


  * ?do=sensor\_statistic

Parameter:
  * &sensor\_position=3 ( Changeable. Format numeric. There are many queries that delivers position settings )
  * &sensor=1 ( Changeable. Format numeric )
  * &table=measure\_watt\_hourly
  * &timeframe=position
  * &range\_from=2012-08-26 ( Changeable. Format string [YYYY-MM-DD ](.md) )
  * &order=hour\_id
  * &turn=desc ( Changeable. Format string [desc | asc ](.md)  )

Delivers usage and costs data from a defined position sort by year, month, day. The rage can be defined with the range\_from parameter.

```
{"2014":{"2":{"23":{"data":0.25,"price":0.06,"weekday":"0"},"22":{"data":1.115,"price":0.28,"weekday":"6"},"21":{"data":0.498,"price":0.13,"weekday":"5"},"20":{"data":4.1,"price":1.09,"weekday":"4"},"19":{"data":4,"price":0.8,"weekday":"3"},"18":{"data":0,"price":0,"weekday":"2"},"17":{"data":0,"price":0,"weekday":"1"},"16":{"data":0,"price":0,"weekday":"0"},"15":{"data":0,"price":0,"weekday":"6"},"14":{"data":0.066,"price":0.01,"weekday":"5"},"13":{"data":0.39,"price":0.09,"weekday":"4"},"12":{"data":0.385,"price":0.09,"weekday":"3"},"11":{"data":0.421,"price":0.1,"weekday":"2"},"10":{"data":0.492,"price":0.12,"weekday":"1"},"09":{"data":0.872,"price":0.21,"weekday":"0"},"08":{"data":0.935,"price":0.24,"weekday":"6"},"07":{"data":0.539,"price":0.13,"weekday":"5"},"06":{"data":0.341,"price":0.08,"weekday":"4"},"05":{"data":0.388,"price":0.1,"weekday":"3"},"04":{"data":0.383,"price":0.09,"weekday":"2"},"03":{"data":0.479,"price":0.12,"weekday":"1"},"02":{"data":0.875,"price":0.22,"weekday":"0"},"01":{"data":1.137,"price":0.29,"weekday":"6"}},"1":{"31":{"data":0.463,"price":0.12,"weekday":"5"},"30":{"data":0,"price":0,"weekday":"4"},"29":{"data":0,"price":0,"weekday":"3"},"28":{"data":0,"price":0,"weekday":"2"},"27":{"data":0,"price":0,"weekday":"1"},"26":{"data":0,"price":0,"weekday":"0"},"25":{"data":0,"price":0,"weekday":"6"},"24":{"data":0.046,"price":0.01,"weekday":"5"},"23":{"data":0.304,"price":0.07,"weekday":"4"},"22":{"data":0.43,"price":0.1,"weekday":"3"},"21":{"data":0.942,"price":0.24,"weekday":"2"},"20":{"data":0.31,"price":0.08,"weekday":"1"},"19":{"data":0.939,"price":0.24,"weekday":"0"},"18":{"data":0.996,"price":0.25,"weekday":"6"},"17":{"data":0.229,"price":0.05,"weekday":"5"},"16":{"data":0.348,"price":0.08,"weekday":"4"},"15":{"data":0.33,"price":0.09,"weekday":"3"},"14":{"data":0.361,"price":0.09,"weekday":"2"},"13":{"data":0.431,"price":0.11,"weekday":"1"},"12":{"data":1.037,"price":0.26,"weekday":"0"},"11":{"data":0.877,"price":0.22,"weekday":"6"},"10":{"data":0.581,"price":0.14,"weekday":"5"},"09":{"data":0.463,"price":0.11,"weekday":"4"},"08":{"data":0.433,"price":0.1,"weekday":"3"},"07":{"data":0.386,"price":0.09,"weekday":"2"},"06":{"data":0.971,"price":0.25,"weekday":"1"},"05":{"data":0.961,"price":0.24,"weekday":"0"},"04":{"data":2.161,"price":0.56,"weekday":"6"},"03":{"data":0.556,"price":0.14,"weekday":"5"},"02":{"data":0.275,"price":0.07,"weekday":"4"},"01":{"data":0.875,"price":0.22,"weekday":"3"}}},"2013":{"12":{"31":{"data":0.794,"price":0.2,"weekday":"2"},"30":{"data":0.467,"price":0.12,"weekday":"1"},"29":{"data":1.251,"price":0.31,"weekday":"0"},"28":{"data":1.464,"price":0.37,"weekday":"6"},"27":{"data":1.161,"price":0.29,"weekday":"5"},"26":{"data":1.72,"price":0.43,"weekday":"4"},"25":{"data":0.85,"price":0.2,"weekday":"3"},"24":{"data":1.367,"price":0.34,"weekday":"2"},"23":{"data":1.613,"price":0.4,"weekday":"1"},"22":{"data":2.176,"price":0.54,"weekday":"0"},"21":{"data":2.069,"price":0.53,"weekday":"6"},"20":{"data":1.213,"price":0.3,"weekday":"5"},"19":{"data":1.147,"price":0.28,"weekday":"4"},"18":{"data":1.495,"price":0.38,"weekday":"3"},"17":{"data":0.832,"price":0.2,"weekday":"2"},"16":{"data":1.235,"price":0.31,"weekday":"1"},"15":{"data":2.011,"price":0.5,"weekday":"0"},"14":{"data":2.36,"price":0.59,"weekday":"6"},"13":{"data":0.582,"price":0.14,"weekday":"5"},"12":{"data":1.246,"price":0.31,"weekday":"4"},"11":{"data":1.124,"price":0.27,"weekday":"3"},"10":{"data":1.754,"price":0.43,"weekday":"2"},"09":{"data":1.377,"price":0.34,"weekday":"1"},"08":{"data":2.088,"price":0.52,"weekday":"0"},"07":{"data":1.655,"price":0.4,"weekday":"6"},"06":{"data":1.471,"price":0.35,"weekday":"5"},"05":{"data":1.147,"price":0.28,"weekday":"4"},"04":{"data":1.512,"price":0.38,"weekday":"3"},"03":{"data":1.394,"price":0.33,"weekday":"2"},"02":{"data":0.972,"price":0.24,"weekday":"1"},"01":{"data":2.027,"price":0.5,"weekday":"0"}},"11":{"30":{"data":1.596,"price":0.4,"weekday":"6"},"29":{"data":1.521,"price":0.37,"weekday":"5"},"28":{"data":1.358,"price":0.33,"weekday":"4"},"27":{"data":1.16,"price":0.28,"weekday":"3"},"26":{"data":1.745,"price":0.43,"weekday":"2"},"25":{"data":1.372,"price":0.34,"weekday":"1"},"24":{"data":2.373,"price":0.59,"weekday":"0"},"23":{"data":1.702,"price":0.43,"weekday":"6"},"22":{"data":1.32,"price":0.34,"weekday":"5"},"21":{"data":1.572,"price":0.38,"weekday":"4"},"20":{"data":1.291,"price":0.32,"weekday":"3"},"19":{"data":1.528,"price":0.37,"weekday":"2"},"18":{"data":0.94,"price":0.22,"weekday":"1"},"17":{"data":2.102,"price":0.51,"weekday":"0"},"16":{"data":2.329,"price":0.59,"weekday":"6"},"15":{"data":1.323,"price":0.32,"weekday":"5"},"14":{"data":1.716,"price":0.42,"weekday":"4"},"13":{"data":1.294,"price":0.31,"weekday":"3"},"12":{"data":0.865,"price":0.2,"weekday":"2"},"11":{"data":1.685,"price":0.4,"weekday":"1"},"10":{"data":2.306,"price":0.57,"weekday":"0"},"09":{"data":2.21,"price":0.54,"weekday":"6"},"08":{"data":2.447,"price":0.59,"weekday":"5"},"07":{"data":2.059,"price":0.49,"weekday":"4"},"06":{"data":1.689,"price":0.41,"weekday":"3"},"05":{"data":1.89,"price":0.45,"weekday":"2"},"04":{"data":2.771,"price":0.66,"weekday":"1"},"03":{"data":2.664,"price":0.67,"weekday":"0"},"02":{"data":3.383,"price":0.86,"weekday":"6"},"01":{"data":2.657,"price":0.66,"weekday":"5"}},"10":{"31":{"data":1.514,"price":0.38,"weekday":"4"},"30":{"data":1.81,"price":0.43,"weekday":"3"},"29":{"data":1.78,"price":0.44,"weekday":"2"},"28":{"data":1.351,"price":0.33,"weekday":"1"},"27":{"data":2.523,"price":0.63,"weekday":"0"},"26":{"data":2.21,"price":0.56,"weekday":"6"}}}}
```

  * ?do=sensor\_detail\_statistic

Parameter:
  * &sensor=1 ( Changeable. Format numeric )

Delivers usage data from the last 12 months based on day and hour usage. The usage data is delivered in 4 parts. Usage per day. Usage per day separated per month. Usage data per hour. Usage data per hour separated by month

```
{"yeardays":[110.4652267,86.0543362,80.5594782,174.2391296,135.2990354,94.389077,106.1215017],"yearsdaysdetail":{"1":[5.79789,4.029912,3.499284,99.732626,53.440867,2.180629,2.62774],"2":[9.2160767,3.5001352,2.4076592,2.2789416,2.4217344,11.464702,10.3114117],"3":[9.37014,12.45666,10.31975,7.33524,7.76225,7.14198,7.57076],"4":[12.70313,9.27486,8.94345,11.10962,15.03423,13.84287,10.66947],"5":[16.17002,11.42657,12.02802,12.2821,10.77548,11.71777,14.905],"6":[5.29543,7.58423,9.29614,6.58046,7.4693,10.94732,10.51894],"7":[11.00304,5.48188,3.778425,5.9398,6.33366,5.773588,13.84453],"8":[7.76367,7.47194,6.0236,6.06958,8.93469,7.8876,5.72445],"9":[8.84676,7.85798,8.50048,8.11132,7.57765,5.27128,5.85137],"10":[10.36437,8.14401,6.65064,6.39881,7.29507,9.86894,12.20052],"11":[10.31784,6.591618,6.898104,5.484404,6.20471,4.940339,8.42414],"0":[3.61686,2.234541,2.213926,2.916228,2.049394,3.352059,3.47317]},"yearhours":[16.745774109,17.649504617,11.573085813,10.789971148,11.332823263,12.020548613,18.017686243,11.400559306,11.548059266,12.5678537,13.857733414,14.785908147,15.018411339,15.147457641,15.782285935,15.970571954,21.52745482,30.940625137,39.304018552,43.155454502,43.913770116,42.108039426,34.920760734,24.012143796],"monthshoursdetail":{"1":[1.16071876,4.83837523,0.69382184,0.53520254,0.53292586,0.5349257,4.50382554,0.52379141,0.59423324,0.68626138,0.69403983,0.76219479,0.82154395,0.84986051,0.87870505,0.72285649,0.80449868,0.75064701,1.07114748,1.85529982,1.97198565,2.1859871,1.68268127,1.45438476],"2":[1.291968309,0.947747637,0.729339813,0.618862708,0.635271653,0.678117953,0.789852563,0.599912966,0.573585186,0.70512605,0.838602894,0.967210727,0.955844469,0.946864051,1.177137185,1.099948064,1.25078669,1.673012567,2.572720642,3.166777002,3.266637606,3.311866656,3.081797594,2.351847006],"3":[1.77637495,1.42420401,1.26551674,1.22655344,1.3257436,1.19752268,1.02621332,0.80752639,0.94371409,0.87056915,0.90404794,0.92381616,0.91427196,0.82253711,0.89150442,1.47064848,2.40905578,3.61337367,4.74887282,4.8390196,4.74053136,4.41695827,3.6229537,2.52142915],"4":[1.6343156,1.3648966,1.3509107,1.3393989,1.3709665,1.3225331,1.7302824,1.3530103,1.3756141,1.5749245,1.5238821,1.5490759,1.5673321,1.4205875,1.2120615,1.2892072,2.128245,3.8042629,5.2940514,5.7543929,6.0216864,5.934553,4.77213,2.8055678],"5":[1.7264546,1.3800622,1.2148503,1.2143257,1.3704181,1.4081923,1.5409643,1.5031822,1.3487825,1.0783413,1.1524504,1.2560652,1.3751429,1.4482872,1.5990645,1.8440875,3.1826541,4.889286,6.6337068,7.1141604,7.3359143,6.9214961,5.2959426,3.019038],"6":[1.7381566,1.3883735,1.2512382,1.2201166,1.3166089,1.3755311,1.2647458,1.1067989,1.1020922,1.256869,1.4209631,1.1772815,1.1814254,1.2863204,1.2371935,1.6112604,2.6133223,3.4319727,4.1250485,4.1429696,4.032069,3.6613155,3.1488886,1.912877],"7":[0.8024292,0.7049985,0.728499,0.7130867,0.794619,0.7952981,1.0902849,1.15318,1.3114063,1.3983314,1.5037294,1.5618524,1.4784382,1.578759,1.4092823,1.5544581,1.5761338,2.100327,3.1866717,3.3449579,3.4012729,3.3267211,2.3065884,1.2426299],"8":[0.6331519,0.5538034,0.3856807,0.3922815,0.3974904,0.8068203,0.6118066,0.5128511,0.557653,0.6780141,0.6965381,0.6513962,0.6184548,0.5613585,0.5774347,0.706479,0.8477186,2.2307797,1.770521,1.847567,1.347992,1.175468,1.2561238,0.9041327],"9":[1.4414929,1.2676153,1.0777669,1.056889,1.1017396,1.1880651,1.3364494,1.010027,0.9505813,1.2709276,1.2909325,1.4346221,1.2972346,1.2550271,1.2179528,1.157675,1.983786,2.7821723,3.2991141,3.4600746,3.5858307,3.1443254,2.3110055,1.773926],"10":[2.2660715,2.0476031,1.5451495,1.3889728,1.310007,1.453917,1.4390103,1.4856293,1.2901999,1.2770026,1.5993505,1.9258521,2.0354362,2.3180302,2.9619308,2.1215486,2.135659,2.6677489,3.190196,3.756846,4.0572808,3.976357,3.6506088,2.9313362],"11":[1.7332843,1.45204928,1.12728032,0.9566237,1.03372098,1.1093571,1.1950659,1.1853496,1.28280476,1.25868485,1.55959025,1.84492537,2.0455848,1.94051964,1.8909729,1.6645405,1.9235164,2.271824,2.4881896,2.7975143,3.0237646,2.9803449,2.75754205,2.15635372],"0":[0.54135549,0.27977586,0.2030318,0.12765756,0.14331167,0.15026818,1.48918522,0.15930014,0.21739269,0.51280177,0.6736064,0.7316157,0.72770196,0.71930643,0.72904628,0.72786262,0.67207847,0.72521839,0.92377851,1.07587538,1.1288048,1.0726464,1.03449842,0.93862156]}}
```

  * ?do=summary\_sensor

Parameter:
  * &sensor=2 ( Changeable. Format numeric )
  * &timeframe=select ( Changeable. Format string [select | range ](.md) )
  * &unit=DAY
  * &unit\_return=timeframe
  * &table=measure\_watt\_hourly ( Changeable. Format string [measure\_watt\_daily | measure\_watt\_hourly | measure\_tmpr\_hourly ](.md) )
  * &select=2014-2-21 ( Changeable. Format string [YYYY-MM-DD | time ](.md) )
  * &range\_from=false ( Changeable. Format string [YYYY-MM-DD\_0 | false ](.md) )
  * &range\_to=false ( Changeable. Format string [YYYY-MM-DD\_0 | false ](.md) )

Delivers a JS object  with the usage from the selected day in hours defined by the select parameter.

```
[[1392858000000, 15.9],[1392861600000, 15.9],[1392865200000, 15.7],[1392868800000, 15.7],[1392872400000, 15.7],[1392876000000, 15.8],[1392879600000, 15.8],[1392883200000, 15.7],[1392886800000, 15.9],[1392890400000, 15.9],[1392894000000, 16],[1392897600000, 16.1],[1392901200000, 16.2],[1392904800000, 16.6],[1392908400000, 17.3],[1392912000000, 18.2],[1392915600000, 17.5],[1392919200000, 17.1],[1392922800000, 16.9],[1392926400000, 17],[1392930000000, 16.9],[1392933600000, 16.8],[1392937200000, 15.8]]
```

  * ?do=summary\_sensor

Parameter:
  * &sensor=2 ( Changeable. Format numeric )
  * &timeframe=select ( Changeable. Format string [select | range ](.md) )
  * &unit=DAY
  * &unit\_return=timeframe
  * &table=measure\_watt\_daily ( Changeable. Format string [measure\_watt\_daily | measure\_watt\_hourly | measure\_tmpr\_hourly ](.md) )
  * &select=time ( Changeable. Format string [YYYY-MM-DD | time ](.md) )
  * &range\_from=false ( Changeable. Format string [YYYY-MM-DD\_0 | false ](.md) )
  * &range\_to=2014-01-31\_0 ( Changeable. Format string [YYYY-MM-DD\_0 | false ](.md) )

Delivers a JS object  with the usage from the selected range in days defined by the range\_from and the range\_to parameter.

```
[[1388534400000, 1.57358],[1388620800000, 1.61554],[1388707200000, 1.65527],[1388793600000, 1.61476],[1388880000000, 1.6578],[1388966400000, 1.62309],[1389052800000, 1.57427],[1389139200000, 1.55603],[1389225600000, 1.56769],[1389312000000, 1.64987],[1389398400000, 1.61158],[1389484800000, 1.4652],[1389571200000, 1.50532],[1389657600000, 1.53118],[1389744000000, 1.50466],[1389830400000, 1.43489],[1389916800000, 1.41757],[1390003200000, 1.3154],[1390089600000, 1.33738],[1390176000000, 1.2775],[1390262400000, 1.28787],[1390348800000, 1.06489],[1390435200000, 1.1875],[1390521600000, 1.13209],[1390608000000, 1.03655],[1390694400000, 1.00981],[1390780800000, 1.05824],[1390867200000, 0.770074],[1390953600000, 0.922087],[1391040000000, 1.09059],[1391126400000, 1.23228]]
```

  * ?do=summary\_sensor

Parameter:
  * &sensor=2 ( Changeable. Format numeric )
  * &timeframe=select ( Changeable. Format string [select | range ](.md) )
  * &unit=DAY
  * &unit\_return=timeframe
  * &table=measure\_tmpr\_hourly ( Changeable. Format string [measure\_watt\_daily | measure\_watt\_hourly | measure\_tmpr\_hourly ](.md) )
  * &select=2014-2-21 ( Changeable. Format string [YYYY-MM-DD | time ](.md) )
  * &range\_from=false ( Changeable. Format string [YYYY-MM-DD\_0 | false ](.md) )
  * &range\_to=false ( Changeable. Format string [YYYY-MM-DD\_0 | false ](.md) )

Delivers a JS object  with the temperature data from the selected day in hours defined by the select parameter.

```
[[1392940800000, 16.7],[1392944400000, 16.7],[1392948000000, 16.5],[1392951600000, 16.6],[1392955200000, 16.5],[1392958800000, 16.5],[1392962400000, 16.4],[1392966000000, 16.4],[1392969600000, 16.6],[1392973200000, 16.4],[1392976800000, 16.6],[1392980400000, 16.6],[1392984000000, 16.8],[1392987600000, 16.8],[1392991200000, 16.7],[1392994800000, 17.3],[1392998400000, 17.1],[1393002000000, 16.9],[1393005600000, 16.8],[1393009200000, 16.8],[1393012800000, 16.8],[1393016400000, 16.8],[1393020000000, 16.6],[1393023600000, 16.6]]
```


### Get settings data ###

  * ?do=global\_settings\_get

Delivers the global system settings for all sensors

```
{"system_settings_tmpr":"c","language_use":"en_EN","current_version":"116","system_settings_system":"envi","system_settings_email_pass":"XXXXXXXXXX","system_settings_email_address":"XXXXXXXXXX","system_settings_twitter_oauth_token_secret":"XXXXXXXXXX","system_settings_twitter_oauth_token":"XXXXXXXXXX","system_settings_twitter_app_secret":"XXXXXXXXXX","system_settings_twitter_app_key":"XXXXXXXXXX","system_settings_pvoutput_api":"XXXXXXXXXX","system_settings_demo":0}
```

  * ?do=summary\_start

Delivers sensor data like id, description, current usage, usage from predefined time ranges.

```
{"0":{"sensor":{"x":"","sensor_id":"0","sensor_title":"Sensor 0","sensor_clamp":"0","position_id":"2","position_time":"2012-08-26 21:37:50","position_description":"Aquarium","position_sensor":"0","measure_history":"365","measure_currency":"Euro","measure_sensor":"0","measure_range":"","measure_timeframe":"0","measure_timezone":"GMT0","measure_timezone_diff":"2","measure_type":"1","measure_pvoutput_id":"123456","measure_pvoutput_api":"XXXXXXXXXX","measure_twitter_ app_key":"","measure_twitter_ app_secret":"","measure_twitter_ oauth_token":"","measure_twitter_ oauth_token_secret":"","positions":{"1":{"position":"1","time":"2012-08-26 18:45:17","description":"start position"},"2":{"position":"2","time":"2012-08-26 21:37:50","description":"Aquarium"}}},"tmpr":"16.7","watt":"87","daily":"1.136 Kwh<br \/>0","hourly":"0.09 Kwh<br \/>0","weekly":"8.076 Kwh<br \/>0.01","monthly":"32.873 Kwh<br \/>0.06"}}
```

  * ?do=sensor\_prices\_get

Parameter:
  * &sensor=2 ( Changeable. Format numeric )

Delivers the defined prices with defined price ranges from the chosen sensor

```
{"2013-11-18":[{"costs_id":"9","costs_sensor":"0","costs_from":"0","costs_to":"23","costs_price":"0.0018"}]}
```

  * ?do=sensor\_notifications\_get

Parameter:
  * &sensor=2 ( Changeable. Format numeric )

Delivers the existing notifications from the selected sensor.

```
{"12":{"measure_notifications_name":"notification title","measure_notifications_unit":"m","measure_notifications_check_email":"1","measure_notifications_check_twitter":"1","measure_notifications_notification":"notification text","measure_notifications_items":"3","measure_notifications_criteria":"2","measure_notifications_value":"1111"}}
```