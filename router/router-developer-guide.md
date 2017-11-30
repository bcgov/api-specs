# BC Route Planner
# Developer Guide
This guide is aimed at developers and web masters that would like to incorporate the BC Route Planner into their applications and websites.
<br>
## Introduction
The BC Route Planner REST API lets you integrate basic routing between BC locations into your own applications. This document defines aspects of the REST API that are not covered in the [Swagger definition](https://raw.githubusercontent.com/bcgov/api-specs/master/router/router.json). You can explore the API in the [API Console](http://apps.gov.bc.ca/pub/api-explorer/?url=https://raw.githubusercontent.com/bcgov/api-specs/master/router/router.json). 
<br>

Your application can store router results or display them on any web map.

## API Key
Use of the BC Route Planner REST API is currently restricted to government. If you are working on a government application that needs routing, please email [DataBC](mailto:Data@gov.bc.ca) for an API key. Be sure to include the name of the project and the business area responsible.


## Distance Resource
The distance resource represents the length and duration of the shortest or fastest route between given points. Here are some examples:

1. Length of shortest route in km and json between Duncan and Metchosin<br>https://router.api.gov.bc.ca/distance.json?routeDescription=shortest%20distance%20in%20km%20and%20json&points=-123.707942%2C48.778691%2C-123.537850%2C48.382005&outputSRS=4326&criteria=shortest&distanceUnits=km&apikey=myapikey<br>
   
2. Length of shortest route in km and kml between Duncan and Metchosin<br>https://router.api.gov.bc.ca/distance.kml?routeDescription=shortest%20distance%20in%20km%20and%20kml&points=-123.707942%2C48.778691%2C-123.537850%2C48.382005&outputSRS=4326&criteria=shortest&distanceUnits=km&apikey=myapikey<br>

3. Length of fastest route in miles and html between Duncan and Metchosin<br>https://router.api.gov.bc.ca/distance.html?routeDescription=fastest%20distance%20in%20km%20and%20html&points=-123.707942%2C48.778691%2C-123.537850%2C48.382005&outputSRS=4326&criteria=shortest&distanceUnit=mi&apikey=myapikey<br>

### HTTP Response

The distance resource will return the following representation:

Attribute Name |	Type
---------------------: | --- |
[routeDescription](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#routeDescription) | String
[searchTimestamp](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#searchTimestamp) | Datetime
[executionTime](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#executionTime) | Real
[version](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#version) | String 
[disclaimer](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#disclaimer) | String
[privacyStatement](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#privacyStatement) | String
[srsCode](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#srsCode) | Integer
[criteria](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#criteria) | String
[distanceUnit](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#distanceUnit) | String
[routeFound](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#routeFound) | String
[points](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#points) | list of Point
[distance](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#distance) | String
[distanceUnit](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#distanceUnit) | String
[time](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#time) | Integer
[timeText](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#timeText) | String

Here is a sample json response:

    {
    
        "routeDescription": "shortest distance in km and json",
        "searchTimestamp": "2016-03-30 11:18:07.752",
        "executionTime": ​1,
        "version": "1.1.1",
        "disclaimer": "http://www2.gov.bc.ca/gov/content/home/disclaimer",
        "privacyStatement": "http://www2.gov.bc.ca/gov/content/home/privacy",
        "copyrightNotice": "Copyright 2016 Province of British Columbia - Access only",
        "copyrightLicense": "http://www2.gov.bc.ca/gov/content/home/copyright",
        "srsCode": ​4326,
        "criteria": "shortest",
        "distanceUnit":"km",
        "points": 
    
    [
    
    [
    
        ​-123.1485847,
        ​55.3933927
    
    ],
    
            [
                ​-123.1515025,
                ​55.3913904
            ]
        ],
        "routeFound:true"
        "distance": ​1.17,
        "time": ​95,
        "timeText": "1 minutes 35 seconds"
    
    }


## Route Resource
The route resource represents the shortest or fastest route between given points and the length and duration of that route. Here are some examples:

1. Shortest route in km and json between Duncan and Metchosin<br>https://router.api.gov.bc.ca/route.json?routeDescription=shortest%20route%20in%20km%20and%20json&points=-123.707942%2C48.778691%2C-123.537850%2C48.382005&outputSRS=4326&criteria=shortest&distanceUnits=km&apikey=myapikey<br>
   
2. Shortest route in km and kml between Duncan and Metchosin<br>https://router.api.gov.bc.ca/route.kml?routeDescription=shortest%20route%20in%20km%20and%20kml&points=-123.707942%2C48.778691%2C-123.537850%2C48.382005&outputSRS=4326&criteria=shortest&distanceUnits=km&apikey=myapikey<br>

3. Fastest route in miles and html between Duncan and Metchosin<br>https://router.api.gov.bc.ca/route.html?routeDescription=fastest%20route%20in%20km%20and%20html&points=-123.707942%2C48.778691%2C-123.537850%2C48.382005&outputSRS=4326&criteria=shortest&distanceUnit=mi&apikey=myapikey<br>

### HTTP response
The route resource will return the following representation:

Attribute Name |	Type
---------------------: | --- |
[routeDescription](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#routeDescription) | String
[searchTimestamp](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#searchTimestamp) | Datetime
[executionTime](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#executionTime) | Real
[version](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#version) | String 
[disclaimer](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#disclaimer) | String
[privacyStatement](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#privacyStatement) | String
[srsCode](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#srsCode) | Integer
[criteria](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#criteria) | String
[points](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#points) | list of Point
[distance](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#distance) | String
[distanceUnit](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#distanceUnit) | String
[time](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#time) | Integer
[timeText](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#timeText) | String
[route](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#route) | Polyline

Here is a sample json response:
{
    
        "routeDescription": "shortest distance in km and json",
        "searchTimestamp": "2016-03-30 11:19:06.721",
        "executionTime": ​0,
        "version": "1.1.1",
        "disclaimer": "http://www2.gov.bc.ca/gov/content/home/disclaimer",
        "privacyStatement": "http://www2.gov.bc.ca/gov/content/home/privacy",
        "copyrightNotice": "Copyright 2016 Province of British Columbia - Access only",
        "copyrightLicense": "http://www2.gov.bc.ca/gov/content/home/copyright",
        "srsCode": ​4326,
        "criteria": "shortest",
        "distanceUnit":"km",
        "points": 
    
    [
    
    [
    
        ​-123.1485847,
        ​55.3933927
    
    ],
    
        [
            ​-123.1515025,
            ​55.3913904
        ]
    
    ],
    "routeFound:true",
    "distance": ​1.17,
    "time": ​95,
    "timeText": "1 minutes 35 seconds",
    "route": 
    [
    
    [
    
        ​-123.14858470195041,
        ​55.39339267997931
    
    ],
    [
    
        ​-123.14840793196278,
        ​55.39338712528468
    
    ],
    [
    
        ​-123.14761109235013,
        ​55.39341636881418
    
    ],
    [
    
        ​-123.14668144613537,
        ​55.393617534494794
    
    ],
    [
    
        ​-123.14503449525762,
        ​55.39417521046494
    
    ],
    [
    
        ​-123.14390833997521,
        ​55.39236304295874
    
    ],
    [
    
        ​-123.14305692485847,
        ​55.39099288115634
    
    ],
    [
    
        ​-123.1446450161482,
        ​55.39068293699658
    
    ],
    [
    
        ​-123.14784075650216,
        ​55.390523867097286
    
    ],
    
            [
                ​-123.15160701279896,
                ​55.3907106829186
            ]
        ]
    
    }



##  Directions Resource
The directions resource represents the turn-by-turn directions, shortest or fastest route between given points and the length and duration of that route. Here are some examples:

1. Directions and shortest route in km and json between Duncan and Metchosin<br>https://router.api.gov.bc.ca/directions.json?routeDescription=directions%20Cand%20Cshortest%20route%20in%20km%20and%20json&points=-123.707942%2C48.778691%2C-123.537850%2C48.382005&outputSRS=4326&criteria=shortest&distanceUnits=km&apikey=myapikey<br>
   
2. Directions and shortest route in km and kml between Duncan and Metchosin<br>https://router.api.gov.bc.ca/directions.kml?routeDescription=directions%20Cand%20Cshortest%20route%20in%20km%20and%20kml&points=-123.707942%2C48.778691%2C-123.537850%2C48.382005&outputSRS=4326&criteria=shortest&distanceUnits=km&apikey=myapikey<br>

3. Directions and fastest route in miles and html between Duncan and Metchosin<br>https://router.api.gov.bc.ca/route.html?routeDescription=directions%20Cand%20Cfastest%20route%20in%20km%20and%20html&points=-123.707942%2C48.778691%2C-123.537850%2C48.382005&outputSRS=4326&criteria=shortest&distanceUnit=mi&apikey=myapikey<br>

### HTTP response
The directions resource will return the following representation:

Attribute Name |	Type
---------------------: | --- |
[routeDescription](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#routeDescription) | String
[searchTimestamp](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#searchTimestamp) | Datetime
[executionTime](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#executionTime) | Real
[version](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#version) | String 
[disclaimer](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#disclaimer) | String
[privacyStatement](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#privacyStatement) | String
[srsCode](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#srsCode) | Integer
[criteria](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#criteria) | String
[points](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#points) | list of Point
[distance](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#distance) | String
[distanceUnit](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#distanceUnit) | String
[time](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#time) | Integer
[timeText](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#timeText) | String
[route](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#route) | Polyline
[directions](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#route) | list of String

Here is a sample json response:

    {
    
        "routeDescription": "shortest distance in km and json",
        "searchTimestamp": "2016-03-30 11:19:40.879",
        "executionTime": ​1,
        "version": "1.1.1",
        "disclaimer": "http://www2.gov.bc.ca/gov/content/home/disclaimer",
        "privacyStatement": "http://www2.gov.bc.ca/gov/content/home/privacy",
        "copyrightNotice": "Copyright 2016 Province of British Columbia - Access only",
        "copyrightLicense": "http://www2.gov.bc.ca/gov/content/home/copyright",
        "srsCode": ​4326,
        "criteria": "shortest",
        "distanceUnit":"km",
        "points": 
    
    [
    
    [
    
        ​-123.1485847,
        ​55.3933927
    
    ],
    
        [
            ​-123.1515025,
            ​55.3913904
        ]
    
    ],
    "routeFound:true",
    "distance": ​1.17,
    "time": ​95,
    "timeText": "1 minutes 35 seconds",
    "route": 
    [
    
    [
    
        ​-123.14858470195041,
        ​55.39339267997931
    
    ],
    [
    
        ​-123.14840793196278,
        ​55.39338712528468
    
    ],
    [
    
        ​-123.14761109235013,
        ​55.39341636881418
    
    ],
    [
    
        ​-123.14668144613537,
        ​55.393617534494794
    
    ],
    [
    
        ​-123.14503449525762,
        ​55.39417521046494
    
    ],
    [
    
        ​-123.14390833997521,
        ​55.39236304295874
    
    ],
    [
    
        ​-123.14305692485847,
        ​55.39099288115634
    
    ],
    [
    
        ​-123.1446450161482,
        ​55.39068293699658
    
    ],
    [
    
        ​-123.14784075650216,
        ​55.390523867097286
    
    ],
    
        [
            ​-123.15160701279896,
            ​55.3907106829186
        ]
    
    ],
    "directions": 
    
        [
            "Continue onto Columbia Dr for 250 m",
            "Turn right onto Hwy 39 for 400 m",
            "Turn right onto Alberta Dr for 550 m",
            "Finish!"
        ]
    
    }
