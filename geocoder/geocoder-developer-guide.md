---
title: BC Address Geocoder Developer Guide
description: Locate and standardize your addresses with the BC Address Geocoder.
---

# BC Address Geocoder Developer Guide
This guide is aimed at developers and web masters that would like to incorporate the Physical Address Geocoder into their applications and websites.
<br>

## Table of Contents

[Introduction](#intro)<br>
[API Changes](#apichanges)<br>
[Resource Overview](#resources)<br>
[Cross-Origin Resource Sharing](#cors)<br>
[addresses Resource](#addresses)<br>
[occupants\/addresses Resource](#occupantsaddresses)<br>
[occupants\/nearest Resource](#occupantsnearest)<br>
[Resource Representations](#resourcerepresentations)<br>
[About Query Representation](#aboutqueryrepresentation)<br>
[Site Address Representation](#siteaddressrepresentation)<br> 
[Occupant Address Representation](#occupantaddressrepresentation)<br>
[Intersection Address Representation](#intersectionaddressrepresentation)<br>
[About faults](#aboutfaults)<br>
[Implementing address autocompletion in your application](#implementingautocomplete)<br>


<a name=intro></a>
## Introduction
The BC Physical Address Online Geocoder REST API lets you integrate real-time standardization, validation, and geocoding of physical addresses into your own applications. This document defines aspects of the REST API that are not covered in the [OpenAPI definition](https://catalogue.data.gov.bc.ca/dataset/physical-address-geocoding-web-service/resource/40d6411e-ab98-4df9-a24e-67f81c45f6fa/view/1d3c42fc-53dc-4aab-ae3b-f4d056cb00e0).
<br>


<a name=apichanges></a>
## API Changes in v4.1
There are no breaking API changes in this release. There is one non-breaking API change:

- There is a new fault property called **value** that contains the string that caused the address match fault. This is useful when figuring out why a given address didn't geocode well. For details, see [About faults](#aboutFaults).

## API Changes in v4.0.0
There are no API changes in this release.


## API Changes in v3.4.1
There are two breaking API changes but they only affect the occupants/addresses resource.<br>
1. In occupants/addresses, if no occupant separator ("**") is found in addressString, addressString is assumed to be an occupant name, not a civic address. In previous versions, if no frontGate ("--") was found, addressString was assumed to be a civic address.

2. In occupants/addresses, fullAddress now includes an occupant separator "**" as in "Sir Jame Douglas Elementary ** 401 Moss St, Victoria, BC"
 

## API Changes in v3.3.1
There is one breaking API change:<br>
The following anonymous online geocoder URLs are deprecated, no longer supported and may be shut down in the future:

https://apps.gov.bc.ca/pub/geocoder<br><br>
http://apps.gov.bc.ca/pub/geocoder<br><br>

<br><br>
<a name=resources></a>
## Resource Overview
The Online Geocoder offers resources for validating and geocoding an address (including public and related business occupants); finding a given site, intersection, and occupant; and finding sites, intersections, and occupants near a point or within an area. 
The current baseUrl for the online geocoder is:<br>

https://geocoder.api.gov.bc.ca/

This URL allows both public and gated access. Gated access requires an apikey. To get a sandbox apikey with a maximum rate of 1000 requests per minute, visit the [geocoder api console](https://catalogue.data.gov.bc.ca/dataset/bc-address-geocoder-web-service/resource/40d6411e-ab98-4df9-a24e-67f81c45f6fa/view/1d3c42fc-53dc-4aab-ae3b-f4d056cb00e0). You can get an unrestricted apikey for use in government applications by contacting the [DataBC Help Desk](https://forms.gov.bc.ca/databc-contact-us/)

<br><br>
<a name=cors></a>
## Cross-Origin Resource Sharing (CORS)
CORS is enabled for any domain if you include an apikey with each request.

<br><br>
<a name=addresses></a>
## Addresses Resource
The addresses resource represents all addresses in the geocoder. A request on this resource to find a query address will return one or more matching addresses that are standardized and geocoded (i.e., given a point location on the earth). 

A query address can be specified in two different ways:

1.	A single address string containing all elements of an address as in:<br>
https://geocoder.api.gov.bc.ca/addresses.geojson?addressString=525%20superior%20st,%20victoria,%20bc<br><br> 
2.	Individual address elements as in:<br>
https://geocoder.api.gov.bc.ca/addresses.geojson?civicNumber=525&streetName=superior&streetType=st&localityName=victoria&provinceCode=BC

Here are some more example geocoder requests:

1.	Geocode 456 Gorge Rd E, Victoria, BC<br> 
https://geocoder.api.gov.bc.ca/addresses.xhtml?addressString=456%20Gorge%20Rd%20e%20victoria%20bc<br><br>
2.	Geocode 7-955 13th Ave, Valemount, BC<br>
https://geocoder.api.gov.bc.ca/addresses.xhtml?addressString=7-955%2013th%20ave,%20Valemount,bc<br><br> 
3.	Geocode the intersection at Johnson and Government<br>
https://geocoder.api.gov.bc.ca/addresses.xhtml?addressString=johnson%20and%20government<br><br> 
4.	Geocode 5671 Malibu Terrace, Nanaimo, BC and return results in GEOJSON and BC Albers projection<br>
https://geocoder.api.gov.bc.ca/addresses.geojson?outputSRS=3005&addressString=5671%20malibu%20terrace%20nanaimo%20bc<br><br>
5.	Geocode 5670 Malibu Terrace, Nanaimo and return the location along the road centreline for using in routing<br>
https://geocoder.api.gov.bc.ca/addresses.kml?locationDescriptor=routingPoint&addressString=5670%20malibu%20terrace%20nanaimo%20bc<br><br>
6.	Geocode 5670 Malibu Terrace, Nanaimo and return accessPoint set back four metres from the curb towards the inside of the property. Note that only accessPoints can be set back<br>
https://geocoder.api.gov.bc.ca/addresses.kml?locationDescriptor=accessPoint&setBack=4&addressString=5670%20malibu%20terrace%20nanaimo%20bc<br><br>  
7.	Geocode 5671 Malibu Terrace, Nanaimo, BC without interpolation. In other words, if the geocoder doesn’t have a site with a civic number of 5671, it will fail instead of looking for an address range that contains 5671<br>
https://geocoder.api.gov.bc.ca/addresses.xhtml?interpolation=none&addressString=5671%20malibu%20terrace%20nanaimo%20bc<br><br>
8.	Geocode 200 Gorge Rd W, Saanich, BC and limit results to Victoria. It will return 200 Gorge Rd E, Victoria, BC since Gorge Rd E is in Victoria<br>
https://geocoder.api.gov.bc.ca/addresses.xhtml?localities=victoria&addressString=200%20gorge%20rd%20w%20saanich%20bc<br><br> 
9.	Geocode 1434 Graham St, Kelowna, BC and limit results to ten matches within the greater Kelowna area<br>
https://geocoder.api.gov.bc.ca/addresses.xhtml?&bbox=-119.8965522070019%2C49.70546831817266%2C-119.2157397287486%2C50.06954472056336&addressString=1434%20Graham%20St%2C%20Kelowna%2C%20BC&maxResults=10<br><br>
10.	Geocode 1434 Graham St, Kelowna, BC and limit results to ten street-level matches<br>
https://geocoder.api.gov.bc.ca/addresses.xhtml?&addressString=1434%20Graham%20St%2C%20Kelowna%2C%20BC%20&matchPrecision=street&maxResults=10<br><br> 
11. Geocode 13450 104 ave, Surrey, BC<br>
https://geocoder.api.gov.bc.ca/addresses.xhtml?addressString=13450%20104%20ave%20surrey%20bc<br><br>
12. Reverse geocode the longitude/latitude location returned by example 11. This should return 13450 104 ave, Surrey, BC. Note that reverse geocoding a point means finding the nearest known address to that point which is why the resource is called sites/nearest.<br>
https://geocoder.api.gov.bc.ca/sites/nearest.xhtml?point=-122.8491387,49.1914645<br><br>
13.	Extrapolate the known location of 12 Bushby St from a parcelPoint to get an accessPoint<br> 
https://geocoder.api.gov.bc.ca/addresses.xhtml?setBack=0&minScore=1&maxResults=1&maxDistance=0&interpolation=adaptive&echo=true&outputSRS=4326&addressString=12%20bushby%20st%20victoria%20bc&locationDescriptor=any&extrapolate=true&parcelPoint=-123.349174,2048.407134<br><br> 
14. Geocode a Surrey address and limit address search to Surrey<br>
https://geocoder.api.gov.bc.ca/addresses.xhtml?localities=surrey&addressString=13450%20104%20ave%20surrey%20bc<br><br>
15. Geocode a Surrey address and limit address search to Richmond. This will return a fullAddress of BC which means no match.<br>
https://geocoder.api.gov.bc.ca/addresses.xhtml?localities=richmond&addressString=13450%20104%20ave%20surrey%20bc<br><br>
16. Geocode a Surrey address and limit address search to Surrey and Richmond.<br>
https://geocoder.api.gov.bc.ca/addresses.xhtml?localities=richmond,surrey&addressString=13450%20104%20ave%20surrey%20bc<br><br>

<a name=occupantsaddresses></a>
## occupants/addresses resource
The occupants/addresses resource represents all occupant addresses in the geocoder. A request on this resource to find a query address will return one or more matching occupants and their addresses.

17. Find up to 10 schools named Sir James Douglas Elementary<br>
https://geocoder.api.gov.bc.ca/occupants/addresses.json?addressString=Sir%20James%20Douglas%20Elementary&maxResults=10

18. Find a school named Sir James Douglas Elementary in Victoria<br>
https://geocoder.api.gov.bc.ca/occupants/addresses.json?addressString=Sir%20James%20Douglas%20Elementary%20%2A%2A%20Victoria

<br><br>
## occupants/nearest resource
The occupants/nearest resource represents the nearest site to a given point location

19.	Find the nearest courthouse to a given point<br>
https://geocoder.api.gov.bc.ca/occupants/nearest.geojson?point=-123.7064038,48.8498537&tags=courts

<br><br>
<a name=resourcerepresentations></a>
### Resource representations in HTTP Responses
The addresses resource will return a document in the requested format and spatial reference system.  Documents in formats that support a header record (e.g., XHTML, KML, GEOJSON, GEOJSONP, GML) will contain a single About Query representation describing the query and its execution, and one or more site address or intersection address representations. Documents in formats that don’t support a header record (e.g., CSV, SHPZ), will contain one or more site/intersection address representations.

<a name=aboutqueryrepresentation></a>
#### About Query Representation
Attribute Name |	Type
---------------------: | --- |
[searchTimestamp](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#searchTimestamp) | Datetime
[executionTime](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#executionTime) | Real
[version](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#version) | String 
[minScore](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#minScore)  | Integer 
[maxResults](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#maxResults) | Integer 
[echo](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#echo)  | Boolean
[interpolation](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#interpolation)  |	String 
[outputSRS](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#outputSRS) | Integer
[setBack](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#setBack) |Real 

<br><br>
<a name=siteaddressrepresentation></a> 
#### Site Address Representation
Attribute Name |	Type
---------------------: | ---
[fullAddress](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#fullAddress) |	String
[score](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#score) |	integer
[matchPrecision](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#matchPrecision) |	String
[precisionPoints](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#mprecisionPoints) | integer
[faults](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#faults) | String
[siteName](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#siteName) | String
[unitDesignator](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#unitDesignator) | String
[unitNumber](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#unitNumber) | String
[unitNumberSuffix](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#unitNumberSuffix) | String
[civicNumber](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#civicNumber) | String
[civicNumberSuffix](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#civicNumberSuffix) | String
[streetName](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#streetName) | String
[streetType](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#streetType) | String
[isStreetTypePrefix](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#isStreetTypePrefix) | Boolean
[streetDirection](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#streetDirection) | String
[isStreetDirectionPrefix](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#isStreetDirectionPrefix) | Boolean
[streetQualifier](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#streetQualifier) | String
[localityName](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#localityName) | String
[localityType](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#localityType) | String
[electoralArea](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#electoralArea) | String
[provinceCode](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#provinceCode) |	String
[locationPositionalAccuracy](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#locationPositionalAccuracy) |	String
[locationDescriptor](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#locationDescriptor) |	String
[siteID](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#siteID) |	string
[blockID](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#blockID) |	String
[fullSiteDescriptor](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#fullSiteDescriptor) |	String
[accessNotes](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#accessNotes) |	String
[siteStatus](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#siteStatus) |	String
[siteRetireDate](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#siteRetireDate) |	Date
[changeDate](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#changeDate) |	string
[isOfficial](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#isOfficial) |	string

<br><br>
<a name=intersectionaddressrepresentation></a>
#### Intersection Address Representation
Attribute Name |	Type
---------------------: | ---
[fullAddress](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#fullAddress) |	String
[intersectionName](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#intersectionName) |	String
[localityName](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#localityName) |	String
[provinceCode](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#provinceCode]) |	String
[score](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#score) |	Integer
[matchPrecision](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#matchPrecision) |	String
[precisionPoints](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#precisionPoints) |	Integer
[provinceCode](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#provinceCode) |	String
[matchPrecision](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#matchPrecision) |	String
[precisionPoints](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#precisionPoints) |	Integer
[faults](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#faults) |	String
[intersectionID](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#intersectionID) |	String
[degree](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#degree) |	String

<br><br>
<a name=occupantaddressrepresentation></a>
## Occupant/addresses Resource
The occupants/addresses resource is similar to the addresses resource. Its response will include an About Query representation plus one site representation and occupant representation for each address matched.

<br><br>
#### Occupant Representation
Attribute Name |	Type
---------------------: | ---
[occupantName](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#occupantName) |	string
[occupantID](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#occupantID) |	string
[occupantAliasAddress](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#occupantAliasAddress) |	string
[occupantDescription](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#occupantDescription) |	string
[contactEmail](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#contactEmail) |	string
[contactPhone](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#contactPhone) |	string
[contactFax](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#contactFax) |	string
[websiteUrl](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#websiteUrl) |	string
[imageUrl](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#imageUrl) |	string
[keywords](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#keywords) |	string
[businessCategoryClass](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#businessCategoryClass) |	string
[businessCategoryDescription](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#businessCategoryDescription) |	string
[naicsCode](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#naicsCode) |	string
[dateOccupantUpdated](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#dateOccupantUpdated) |	string
[dateOccupantAdded](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#dateOccupantAdded) |	string
[custodianId](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#custodianId) |	string
[sourceDataId](https://github.com/bcgov/api-specs/blob/master/geocoder/glossary.md#sourceDataId) |	string

<br><br>
<a name=aboutfaults></a>
## About faults
The *faults* property in a resource response is a list of one or more address match faults. Each fault has the following properties:

|Property name|Description|Example
|--|--|--|
|value|string that caused the fault (new in v4.1)|7380
|element|name of address element at fault|CIVIC_NUMBER
|fault|fault descriptor|notInAnyBlock
|penalty|number of points to reduce score by|1

<br><br>
<a name=implementingautocomplete></a>
## Implementing address autocompletion in your application
Using the autoComplete boolean request parameter is the key to successful implementation of address autocompletion in your application. Let's assume your application input form has an address text box and a search icon. 

A user starts entering the characters of an address. After three or so characters, the application should issue a get request on the addresses resource with autoComplete set to True every time a user enters an additional character. This tells the geocoder that addressString contains a partial address and to find the best N address prefix matches for display in a pick list below the address text box.

If the user clicks on the search icon or presses the Enter key, the application should issue a get request on the addresses resource with autocomplete set to False. This tells the geocoder to use addressString as entered when trying to find the best N matches.

If you are using jQuery in your javascript app, check out our javascript code for autocompletion [here](https://github.com/bcgov/ols-devkit/tree/gh-pages/widget). To see the code in action, visit [here](https://bcgov.github.io/ols-devkit/examples/address_autocomplete.html)
