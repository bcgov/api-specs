# BC Route Planner
# Developer Guide
This guide is aimed at developers and web masters that would like to incorporate the BC Route Planner into their applications and websites.
<br>
## Introduction
The BC Route Planner REST API lets you integrate basic routing between BC locations into your own applications. This document defines aspects of the REST API that are not covered in the [Swagger definition](https://raw.githubusercontent.com/bcgov/api-specs/master/router/router.json). You can explore the API in the [API Console](https://catalogue.data.gov.bc.ca/dataset/bc-route-planner/resource/82cd3194-0955-4d7e-b35a-78a98fda153a/view/80721e92-1a39-4300-ac76-6cfb09493d81). 
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
[points](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#points) | list of Point
[routeFound](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#routeFound) | Boolean
[distance](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#distance) | String
[time](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#time) | Integer
[timeText](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#timeText) | String

Here is a sample json response:

    {
    
        "routeDescription": "shortest distance in km and json",
        "searchTimestamp": "2016-03-30 11:18:07.752",
        "executionTime": ​1,
        "version": "1.3.0",
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
[distanceUnit](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#distanceUnit) | String
[points](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#points) | list of Point
[routeFound](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#routeFound) | Boolean
[distance](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#distance) | String
[time](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#time) | Integer
[timeText](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#timeText) | String
[route](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#route) | Polyline

Here is a sample json response:

    {
    
        "routeDescription": "shortest distance in km and json",
        "searchTimestamp": "2016-03-30 11:19:06.721",
        "executionTime": ​0,
        "version": "1.3.0",
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
[distanceUnit](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#distanceUnit) | String
[points](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#points) | list of Point
[routeFound](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#routeFound) | Boolean
[distance](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#distance) | String
[time](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#time) | Integer
[timeText](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#timeText) | String
[route](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#route) | Polyline
[directions](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#route) | list of String

Here is a sample json response:

    {
    
        "routeDescription": "shortest distance in km and json",
        "searchTimestamp": "2016-03-30 11:19:40.879",
        "executionTime": ​1,
        "version": "1.3.0",
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

    
## optimalRoute Resource
The optimalRoute resource represents the shortest or fastest route between a start point and a series of end points reordered to minimize total route distance or time. Here are some examples:

1. Shortest optimal route in km and json between the following addresses in Victoria, BC:

1200 Douglas St, 1020 View St, 851 Broughton St, 835 Fisgard St, and 707 Fort St 

https://router.api.gov.bc.ca/optimalRoute.json?criteria=shortest&points=-123.3651694%2C48.4254488%2C-123.3558749%2C48.4244505%2C-123.3605707%2C48.4232329%2C-123.3600244%2C48.4291533%2C-123.3647879%2C48.4245465&roundTrip=false&apikey=myapikey
   
2. Fastest optimal route in km and kml between same addresses as example 1

https://router.api.gov.bc.ca/optimalRoute.kml?criteria=fastest&points=-123.3651694%2C48.4254488%2C-123.3558749%2C48.4244505%2C-123.3605707%2C48.4232329%2C-123.3600244%2C48.4291533%2C-123.3647879%2C48.4245465&roundTrip=false&apikey=myapikey

### HTTP response
The optimalRoute resource will return the following representation:

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
[points](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#points) | list of Point
[routeFound](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#routeFound) | Boolean
[distance](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#distance) | String
[time](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#time) | Integer
[timeText](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#timeText) | String
[visitOrder](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#visitOrder) | list of Integer
[route](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#route) | Polyline


Here is a sample json response:

    {
	"routeDescription": "",
	"searchTimestamp": "2018-02-20 16:36:39.254",
	"executionTime": 332,
	"routingExecutionTime": 16,
	"optimizationExecutionTime": 313,
	"version": "1.4.2",
	"disclaimer": "http://www2.gov.bc.ca/gov/content/home/disclaimer",
	"privacyStatement": "http://www2.gov.bc.ca/gov/content/home/privacy",
	"copyrightNotice": "Copyright 2015 Province of British Columbia - Open Government License",
	"copyrightLicense": "http://www.data.gov.bc.ca/local/dbc/docs/license/OGL-vbc2.0.pdf",
	"srsCode": 4326,
	"criteria": "fastest",
	"distanceUnit": "km",
	"points": [
		[-123.36517, 48.42545],
		[-123.35587, 48.42445],
		[-123.36057, 48.42323],
		[-123.36002, 48.42915],
		[-123.36479, 48.42455]
	],
	"routeFound": true,
	"distance": 1.916,
	"time": 157,
	"timeText": "2 minutes 37 seconds",
	"visitOrder": [0, 3, 2, 4, 1],
	"route": [
		[-123.36517, 48.42545],
		[-123.36508, 48.42544],
		[-123.36533, 48.42465],
		[-123.36478, 48.42459],
		[-123.36478, 48.42459],
		[-123.36249, 48.42432],
		[-123.36269, 48.42352],
		[-123.36056, 48.42327],
		[-123.36056, 48.42327],
		[-123.35992, 48.42319],
		[-123.35985, 48.42352],
		[-123.35972, 48.42401],
		[-123.3569, 48.42373],
		[-123.35674, 48.42451],
		[-123.35588, 48.42442],
		[-123.35588, 48.42442],
		[-123.35674, 48.42451],
		[-123.35611, 48.42709],
		[-123.35618, 48.42732],
		[-123.35606, 48.42833],
		[-123.35599, 48.42884],
		[-123.35885, 48.42901],
		[-123.35928, 48.42914],
		[-123.36002, 48.42919]
	]
    }

The visitOrder values need a bit more explanation. The points in the request in example 2 above are given in the following order:

0. 1200 Douglas St
1. 1020 View St
2. 851 Broughton St
3. 835 Fisgard St
4. 707 Fort St

The response above is the response to the request in example 2 and contains the visitOrder 0,3,2,4,1. visitOrder represents the position in the optimal order each input point should appear in as follows:

1200 Douglas St is zeroeth point (0)<br>
1020 View St is third point (3)<br>
851 Broughton St is second point (2)<br>
835 Fisgard St is fourth point (4)<br>
707 Fort St is first point (1)

Your application can then use the visitOrder to write out the stops in the optimal order:

0. 1200 Douglas St
1. 707 Fort St
2. 851 Broughton St
3. 1020 View St
4. 835 Fisgard St


##  optimalDirections Resource
The optimalDirections resource represents the turn-by-turn directions, shortest or fastest route between given points and the length and duration of that route. Here are some examples:

1. Shortest optimal route and directions in km and json between the following addresses in Victoria, BC:

1200 Douglas St, 1020 View St, 851 Broughton St, 835 Fisgard St, and 707 Fort St 

https://router.api.gov.bc.ca/optimalDirections.json?criteria=shortest&points=-123.3651694%2C48.4254488%2C-123.3558749%2C48.4244505%2C-123.3605707%2C48.4232329%2C-123.3600244%2C48.4291533%2C-123.3647879%2C48.4245465&roundTrip=false&apikey=myapikey
   
2. Fastest optimal route and directions in km and kml between same addresses as example 1

https://router.api.gov.bc.ca/optimalDirections.kml?criteria=fastest&points=-123.3651694%2C48.4254488%2C-123.3558749%2C48.4244505%2C-123.3605707%2C48.4232329%2C-123.3600244%2C48.4291533%2C-123.3647879%2C48.4245465&roundTrip=false&apikey=myapikey

### HTTP response
The optimalDirections resource will return the following representation:

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
[points](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#points) | list of Point
[routeFound](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#routeFound) | Boolean
[distance](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#distance) | String
[time](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#time) | Integer
[timeText](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#timeText) | String
[visitOrder](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#visitOrder) | list of Integer
[route](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#route) | Polyline
[directions](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#route) | list of String

Here is a sample json response:

    {
	"routeDescription": "",
	"searchTimestamp": "2018-02-20 16:09:36.298",
	"executionTime": 325,
	"routingExecutionTime": 15,
	"optimizationExecutionTime": 304,
	"version": "1.4.2",
	"disclaimer": "http://www2.gov.bc.ca/gov/content/home/disclaimer",
	"privacyStatement": "http://www2.gov.bc.ca/gov/content/home/privacy",
	"copyrightNotice": "Copyright 2015 Province of British Columbia - Open Government License",
	"copyrightLicense": "http://www.data.gov.bc.ca/local/dbc/docs/license/OGL-vbc2.0.pdf",
	"srsCode": 4326,
	"criteria": "fastest",
	"distanceUnit": "km",
	"points": [
		[-123.36517, 48.42545],
		[-123.35587, 48.42445],
		[-123.36057, 48.42323],
		[-123.36002, 48.42915],
		[-123.36479, 48.42455]
	],
	"routeFound": true,
	"distance": 1.916,
	"time": 157,
	"timeText": "2 minutes 37 seconds",
	"visitOrder": [0, 3, 2, 4, 1],
	"route": [
		[-123.36517, 48.42545],
		[-123.36508, 48.42544],
		[-123.36533, 48.42465],
		[-123.36478, 48.42459],
		[-123.36478, 48.42459],
		[-123.36249, 48.42432],
		[-123.36269, 48.42352],
		[-123.36056, 48.42327],
		[-123.36056, 48.42327],
		[-123.35992, 48.42319],
		[-123.35985, 48.42352],
		[-123.35972, 48.42401],
		[-123.3569, 48.42373],
		[-123.35674, 48.42451],
		[-123.35588, 48.42442],
		[-123.35588, 48.42442],
		[-123.35674, 48.42451],
		[-123.35611, 48.42709],
		[-123.35618, 48.42732],
		[-123.35606, 48.42833],
		[-123.35599, 48.42884],
		[-123.35885, 48.42901],
		[-123.35928, 48.42914],
		[-123.36002, 48.42919]
	],
	"directions": [{
		"text": "Continue onto View St for 7 m (0 seconds)",
		"point": [-123.36517, 48.42545]
	}, {
		"text": "Turn right onto Douglas St for 90 m (6 seconds)",
		"point": [-123.36508, 48.42544]
	}, {
		"text": "Turn left onto Fort St for 40 m (3 seconds)",
		"point": [-123.36533, 48.42465]
	}, {
		"text": "Stopover 1",
		"point": [-123.36478, 48.42459]
	}, {
		"text": "Continue onto Fort St for 150 m (15 seconds)",
		"point": [-123.36478, 48.42459]
	}, {
		"text": "Turn right onto Blanshard St for 90 m (6 seconds)",
		"point": [-123.36249, 48.42432]
	}, {
		"text": "Turn left onto Broughton St for 150 m (14 seconds)",
		"point": [-123.36269, 48.42352]
	}, {
		"text": "Stopover 2",
		"point": [-123.36056, 48.42327]
	}, {
		"text": "Continue onto Broughton St for 50 m (4 seconds)",
		"point": [-123.36056, 48.42327]
	}, {
		"text": "Turn left onto Quadra St for 95 m (11 seconds)",
		"point": [-123.35992, 48.42319]
	}, {
		"text": "Turn right onto Fort St for 200 m (15 seconds)",
		"point": [-123.35972, 48.42401]
	}, {
		"text": "Turn left onto Vancouver St for 90 m (6 seconds)",
		"point": [-123.3569, 48.42373]
	}, {
		"text": "Turn right onto View St for 65 m (5 seconds)",
		"point": [-123.35674, 48.42451]
	}, {
		"text": "Stopover 3",
		"point": [-123.35588, 48.42442]
	}, {
		"text": "Continue onto View St for 65 m (5 seconds)",
		"point": [-123.35588, 48.42442]
	}, {
		"text": "Turn right onto Vancouver St for 500 m (39 seconds)",
		"point": [-123.35674, 48.42451]
	}, {
		"text": "Turn left onto Balmoral Rd for 200 m (15 seconds)",
		"point": [-123.35599, 48.42884]
	}, {
		"text": "Turn slight right onto Fisgard St for 90 m (6 seconds)",
		"point": [-123.35885, 48.42901]
	}, {
		"text": "Finish!",
		"point": [-123.36002, 48.42919]
	}]
    }
