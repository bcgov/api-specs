# BC Route Planner
# Glossary of Terms
Term | Definition
----: | -----------
<a name="criteria">criteria</a> | Routing criteria to optimize. One of shortest or fastest. Default is shortest.
<a name="directions">directions</a> | Turn-by-turn directions
<a name="disclaimer">disclaimer</a> | Legal disclaimer of the Router Web Service
<a name="distance">distance</a> | Route length (in distanceUnit units)
<a name="distanceUnit">distanceUnit</a> | Unit of measure used by distance propertyerm. Allowed values are km (kilometres) and mi (miles). Default is km.
<a name="executionTime">executionTime</a> | Query execution time in milliseconds
<a name="fromPoints">fromPoints</a> | A list of origin points in geographic coordinates (lon/lat). Commas are used to separate coordinates and points as in the following list of two points: -124.972951,49.715181,-123.139464,49.704015
<a name="outputFormat">outputFormat</a> | Format of representation. Allowed values are json, html, and kml. Default is json.
<a name="outputSRS">outputSRS</a> | The EPSG code of the spatial reference system used to state the coordination location of a named feature. It is ignored if KML output is specified since KML only supports 4326 (WGS84). Allowed values are:<br>3005: BC Albers<br>4326: WGS 84 (default)<br>26907-26911: NAD83/UTM Zones 7N through 11N<br>32607-32611: WGS84/UTM Zones 7N through 11N<br>26707-26711: NAD27/UTM Zones 7N through 11N
<a name="points">points</a> | A list of any number of route points in start to end order. Points are specified as X1,Y1,...Xn,Yn where X and Y are values in the projection specified by the 'outputSRS' parameter. If no outputSRS is given, X is treated as longitude and Y is treated as latitude.<br>Here is an example:<br>-123.707942,48.778691,-123.537850,48.382005<br><br>To make a round trip, just add the start point as in:<br>-123.707942,48.778691,-123.537850,48.382005,-123.707942,48.778691
<a name="privacyStatement">privacyStatement</a> | Privacy statement associated with the Router Web Service
<a name="toPoints">toPoints</a> | A list of destination points in geographic coordinates (lon/lat). Commas are used to separate coordinates and points as in the following list of two points: -124.972951,49.715181,-123.139464,49.704015
<a name="srsCode">srsCode</a> | The EPSG code of the spatial reference system used to state the coordination location of all geometry features in HTTP response. Allowed values are:<br>3005: BC Albers<br>4326: WGS 84 (default)<br>26907-26911: NAD83/UTM Zones 7N through 11N<br>32607-32611: WGS84/UTM Zones 7N through 11N<br>26707-26711: NAD27/UTM Zones 7N through 11N
<a name="route">route</a> | route geometry (polyline)
<a name="routeDescription">routeDescription</a> | A short description of the nature of the requested route. This will be echoed in the returned route representation for use in your application. For example:<br>Fastest route from 1002 Johnson St, Victoria to 1105 Royal Ave, New Westminster
<a name="time">time</a> | Route duration (in seconds)
<a name="timeText">timeText</a> | Route duration in structured English (e.g., 1 hour and 15 minutes)
<a name="version">version</a> | Software version of the Router Web Service
