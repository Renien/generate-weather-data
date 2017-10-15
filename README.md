<h1 align="center">
<img src="https://github.com/Renien/generate-weather-data/blob/master/doc/weather-icon.jpg" alt="weather" width="20%" height="20%">
    <br>
        Toy Data
    <br>
  <h4 align="center">Generate - Weather Data</h4>
</h1>

## Summary

This Python script allows to create a toy model of the environment (taking into account things like atmosphere, topography, geography,
oceanography, or similar) that evolves over time. These measurements at various locations (ie weather
stations), and the program emit that data, as in the following:

```
Station|GEO Location|Local Time|Conditions|Temperature|Pressure|Humidity
SYD|-33.86,151.21,39|2015-12-23T05:02:12Z|Rain|+12.5|1004.3|97
MEL|-37.83,144.98,7|2015-12-24T15:30:55Z|Snow|-5.3|998.4|55
ADL|-34.92,138.62,48|2016-01-03T12:35:37Z|Sunny|+39.4|1114.1|12
```

## Features and Limitations

The implementation generates toy data as expected,

- It generates temperature is in °C, pressure in hPa, relative humidity as a % amd the values are concatinated with '|' character in the following order '_Station|GEO Location|Local Time|Conditions|Temperature|Pressure|Humidity_'
- To Generating plausible test data random fuzz is used to check for checking boundaries
- Test data contains a reasonable number of reporting stations; 10±

Since the objective is to show the approach and technique a python script has been implemented to execute has single thread sequential job. Therefore, if we try to use bigger geo file it will take time to complete the full process and to generate the toy data. To overcome this issue we need to implement MapReduce implementation to run each process parallel in cluster.
MapReduce jobs can be implemented using one of the technology (Which will run on Hadoop Stack):

- Pig
- Scalding
- Apache Flume
- Apache Spark (Can execute in standalone mode)
- etc

## Installation

Make sure you have installed,

- Python 2.7.*
- rasterio
- affine
- pyproj
- numpy

To install the above python libs execute the following command,

```
bash install.sh
```

## Python Script Execution

Execute the following command to get functionality,

```
python generate_data.py -h
```

<p align="center">
    <img src="https://github.com/Renien/generate-weather-data/blob/master/doc/help.png" alt="help display">
</p>

Generate toy data with random station selection

```
python generate_data.py -i /<your path dir>/generate-weather-data/cea.tif -r y
```

## Directory Layout

```
.
├── cea.tif                                 --> Sample small geo map
├── gebco_08_rev_elev_D2_grey_geo.tif       --> Australia content geo map
├── generate_data.py                        --> Python script that generate weather data
├── install.sh                              --> Install python packages
└── weather_data_sample.dat                 --> Generated sample data using 'cea.tif' map file and
                                                random station selection 'y'
```

## Generated sample toy data

```
BEN|33.9435602229,-117.641409054|2012-09-27 08:04:55|Snow|-5.2|949.5|59
HOB|33.9435602245,-117.640761244|2015-11-02 14:18:00|Sunny|39.6|859.5|56
CAN|33.9435602262,-117.640113434|2009-12-07 16:31:53|Rain|21.9|1023.9|56
DAR|33.9435602278,-117.639465625|2011-06-29 08:31:23|Rain|18.2|959.3|57
SYD|33.9435602295,-117.638817815|2011-12-18 14:27:15|Sunny|13.3|1168.3|61
MEL|33.9435602312,-117.638170006|2016-12-11 18:38:29|Snow|-5.4|944.9|61
ADL|33.9435602328,-117.637522196|2011-04-21 11:37:51|Sunny|36.6|960.9|69
ALB|33.9435602345,-117.636874387|2008-06-10 20:11:15|Snow|-5.9|1008.1|65
BRB|33.9435602362,-117.636226577|2014-03-27 01:45:01|Sunny|37.1|1160.8|57
PER|33.9435602378,-117.635578768|2015-02-24 02:28:01|Sunny|36.0|1192.1|59
BEN|33.9435602395,-117.634930958|2010-06-05 01:59:31|Snow|-3.8|1080.8|61
HOB|33.9435602412,-117.634283149|2008-09-01 02:16:26|Snow|-6.5|787.9|69
CAN|33.9435602428,-117.633635339|2014-06-18 20:06:27|Snow|-3.6|941.9|60
```

Thanks [**flaticon**](https://www.flaticon.com) for free icon.