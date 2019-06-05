# BC Physical Address Exchange Schema Draft v0.3

The Physical Address Exchange Schema can be used to exchange physical addresses between software systems. The schema supports the exchange of the following types of address situations:

- Addresses of buildings without units
- Addresses of buildings assigned single or multiple civic numbers
- Addresses that have no civic number (landmark or non-civic addresses)
- Addresses of buildings with multiple units
- Addresses of complexes that contain multiple buildings
- Addresses of buildings that contain sub-buildings (e.g., floors, wards, wings)

An address can have rooftop, front door, parcel, vehicle access, and other locations. Units within buildings and buildings within complexes can have their own rooftop and vehicle access locations (e.g., townhouse units within a complex, buildings within a campus).

Buildings, complexes, outdoor areas, and any other site that can be assigned an address can also have its own footprint.

## Example 1 - A house with a single civic number and no units
37 Olympia Ave, Victoria, BC

Field | Value
-----: | ------
CIVIC_NUMBER|37
STREET_NAME|Olympia
STREET_TYPE|Ave
LOCALITY|Victoria
PROVINCE_CODE|BC
SITE_POINT_DESCRIPTOR|Parcel
SITE_LAT| 
SITE_LON|
ACCESS_POINT_LAT|
ACCESS_POINT_LON|
FOOTPRINT_DESCRIPTOR|building
FOOTPRINT| (polygon)


## Example 2 - Multiple buildings distinguished by unit number prefix

810 Esquimalt Rd, Esquimalt, BC has three buildings A,B,C. Each building has four floors with 10 units each numbered 100-110, 200-210, 300-310, and 400-410

The following exchange data record will represent the above addresses:

Field | Value
-----: | ------
UNIT_DESIGNATOR| APT
UNIT_NUMBER_PREFIX|A-C
UNIT_NUMBER|100-110,200-210,300-310,400-410
CIVIC_NUMBER|810
STREET_NAME|Esquimalt
STREET_TYPE|Rd
LOCALITY|Esquimalt
PROVINCE_CODE|BC
SITE_POINT_DESCRIPTOR|Parcel
SITE_LAT| 
SITE_LON|
ACCESS_POINT_LAT|
ACCESS_POINT_LON|
FOOTPRINT_DESCRIPTOR|building
FOOTPRINT|(multiPolygon)

If this example was provided as reference data to the BC Address Geocoder, the Geocoder would derive full addresses such as:

APT A100 -- 810 Esquimalt Rd,Esquimalt,BC

APT B407 -- 810 Esquimalt Rd,Esquimalt,BC

APT C210 -- 810 Esquimalt Rd,Esquimalt,BC

## Example 3 - A complex with multiple levels of units

Vancouver International Airport, 3211 Grant McConachie Way, Richmond, BC has the following terminals and gates:
- Terminal A
  - Gate 1-35
- Terminal B
  - Gate 1-40
- Terminal C
  - Gate 1-20

The following data exchange records will represent the above addresses:

Field | Value
----:|----
SITE_NAME|Vancouver International Airport
CIVIC_NUMBER|3211
STREET_NAME|Grant McConnachie
STREET_TYPE|Way
LOCALITY|Richmond
PROVINCE_CODE|BC
SITE_POINT_DESCRIPTOR|parcel
SITE_LAT| 
SITE_LON|
ACCESS_POINT_LAT|
ACCESS_POINT_LON|
FOOTPRINT_DESCRIPTOR|complex
FOOTPRINT|(multiPolygon)

Field | Value
----:|----
UNIT_DESIGNATOR|Terminal
UNIT_NUMBER|A-C
SUPER_FULL_SITE_DESCRIPTOR|Vancouver International Airport
CIVIC_NUMBER|3211
STREET_NAME|Grant McConnachie
STREET_TYPE|Way
LOCALITY|Richmond
PROVINCE_CODE|BC
SITE_POINT_DESCRIPTOR|frontDoor
SITE_LAT| 
SITE_LON|
FOOTPRINT_DESCRIPTOR|building
FOOTPRINT|(polygon)

Field | Value
----:|----
UNIT_DESIGNATOR|Gate
UNIT_NUMBER|1-35
SUPER_FULL_SITE_DESCRIPTOR|Terminal A -- Vancouver International Airport
CIVIC_NUMBER|3211
STREET_NAME|Grant McConnachie
STREET_TYPE|Way
LOCALITY|Richmond
PROVINCE_CODE|BC
SITE_POINT_DESCRIPTOR|frontDoor
SITE_LAT| 
SITE_LON|

The gates of terminals B and C are represented similarly.

If this example was provided as reference data to the BC Address Geocoder, the Geocoder would derive full addresses such as:

Vancouver International Airport -- 3211 Grant McConnachie Way,Richmond,BC

Terminal C, Vancouver International Airport -- 3211 Grant McConnachie Way,Richmond,BC

Gate 23, Terminal A, Vancouver International Airport -- 3211 Grant McConnachie Way,Richmond,BC 

Gate 7, Terminal B, Vancouver International Airport -- 3211 Grant McConnachie Way,Richmond,BC 

Each Terminal and Gate can have its own site and access locations

## Example 4 - A complex of buildings

Given the following addresses for UVIC:

Rooms 100-110 in the Clearihue Building, University of Victoria -- 3800 Finnerty Rd, Saanich BC

Michele Pujol Room, Student Union Building, University of Victoria -- 38800 Finnerty Rd, Saanich, BC

The following exchange data records will represent the above addresses:


Field | Value
----:|----
SITE_NAME|University of Victoria
CIVIC_NUMBER|3800
STREET_NAME|Finnerty
STREET_TYPE|Rd
LOCALITY|Victoria
PROVINCE_CODE|BC
SITE_POINT_DESCRIPTOR|Parcel
SITE_LAT| 
SITE_LON|
ACCESS_POINT_LAT|
ACCESS_POINT_LON|
FOOTPRINT_DESCRIPTOR|complex
FOOTPRINT|(multiPolygon)

Field | Value
----:|----
SITE_NAME|Student Union Building
SUPER_FULL_SITE_DESCRIPTOR|University of Victoria
CIVIC_NUMBER|3800
STREET_NAME|Finnerty
STREET_TYPE|Rd
LOCALITY|Saanich
PROVINCE_CODE|BC
SITE_POINT_DESCRIPTOR|frontDoor
SITE_LAT| 
SITE_LON|
ACCESS_POINT_LAT|
ACCESS_POINT_LON|
FOOTPRINT_DESCRIPTOR|building
FOOTPRINT|(polygon)

Field | Value
----:|----
SITE_NAME|Clearihue Building
SUPER_FULL_SITE_DESCRIPTOR|University of Victoria
CIVIC_NUMBER|3800
STREET_NAME|Finnerty
STREET_TYPE|Rd
LOCALITY|Saanich
PROVINCE_CODE|BC
SITE_POINT_DESCRIPTOR|frontDoor
SITE_LAT| 
SITE_LON|
ACCESS_POINT_LAT|
ACCESS_POINT_LON|
FOOTPRINT_DESCRIPTOR|building
FOOTPRINT|(polygon)

Field | Value
----:|----
SITE_NAME|Michele Pujol Room
SUPER_FULL_SITE_DESCRIPTOR|Student Union Building -- University of Victoria
CIVIC_NUMBER|3800
STREET_NAME|Finnerty
STREET_TYPE|Rd
LOCALITY|Saanich
PROVINCE_CODE|BC
SITE_POINT_DESCRIPTOR|frontDoor
SITE_LAT| 
SITE_LON|
ACCESS_POINT_LAT|
ACCESS_POINT_LON|
FOOTPRINT_DESCRIPTOR|indoorArea
FOOTPRINT|(polygon)

Field | Value
----:|----
UNIT_DESIGNATOR|Room
UNIT_NUMBER|100-110
SUPER_FULL_SITE_DESCRIPTOR|Clearhue Building -- University of Victoria
CIVIC_NUMBER|3800
STREET_NAME|Finnerty
STREET_TYPE|Rd
LOCALITY|Saanich
PROVINCE_CODE|BC


## Schema Definition
This schema can be used in any common text format that supports named properties including CSV,TSV,JSON, and XML

Field Name | Data Type |	Description | Required for Civic Address|Required for Non-civic address
---: | --- | --- | ---| ---
YOUR_ID |String|Unique identifier in your local address management system (e.g., X0233212)| No|No
UNIT_DESIGNATOR |String|Canada Post unit designator (e.g., APT)|No|No
UNIT_NUMBER_PREFIX|String|a single letter or sequence of letter ranges separated by commas (e.g., A-D,J,M-P)|No|No
UNIT_NUMBER|String|unit number or letter or sequence of unit number/letter ranges separated by commas (e.g., 100-119,200-219)|No|No
UNIT_NUMBER_SUFFIX|String|Canada Post unit number suffix (e.g., C)|No|No
SITE_NAME |String|building or landmark name (e.g., Centennial Candle)|yes|yes
SUPER_FULL_SITE_DESCRIPTOR|String|names of all units and sites in parent site hierarchy separated by double-dash (e.g., Student Union Building -- University of Victoria)|No|No
CIVIC_NUMBER|Number| civic number, usually a positive integer (e.g., 1321)|Yes|No
CIVIC_NUMBER_SUFFIX|String|Canada Post civic number suffix (e.g., A)|No|No
STREET_NAME|String|Street name|Yes|No
STREET_TYPE|String|Street type|No|No
IS_STREET_TYPE_PREFIX|Boolean| True if street type appears before street name as in HWY 17|No|No
STREET_DIRECTION|String|Canada Post street direction (e.g., NW); Note CP does not allow prefix and suffix street type in same address|No|No
IS_STREET_DIRECTION_PREFIX|Boolean|true if street direction appears before street name as in SW Marine Dr|No|No
LOCALITY|String|Locality (e.g., Victoria)|Yes|Yes
LOCALITY_DESCRIPTOR|String|type of locality|(e.g., Municipality)|Yes|Yes
PROVINCE_CODE|String|Canada Post two-character province code|Yes|Yes
IS_NON_CIVIC_ADDRESS|Boolean|True if address has no assigned civic number|Yes|Yes
IS_OFFICIAL_ADDRESS|Boolean|True if address is official; False if unofficial (e.g., former address)|Yes|Yes
NARRATIVE_LOCATION|String|step by step directions to a non-civic address location|No|Yes	
SITE_POINT_DESCRIPTOR|String|one of parcel,rooftop,frontDoor,internalDoor,entrance,frontGate|Yes|Yes
SITE_LAT|Number|site latitude|Yes|Yes
SITE_LON|Number)|site longitude|Yes|Yes
SITE_TAGS|String| Comma-separated list of descriptive tags (e.g. stadium)|No|No
ACCESS_POINT_LAT|Number|Only needed if access point is different than site point or super site point|No|Yes
ACCESS_POINT_LON|Number|Only needed if access point is different than site point or super site point|No|Yes
FOOTPRINT_DESCRIPTOR|String| one of building,complex,parcel,outdoorArea,indoorArea,secureOutdoorArea (e.g., inner courtyard, football field associated with a stadium)
FOOTPRINT|OGC WKT|geometry of site footprint in OGC Well-Known Text format. Can use other geometry standards in other formats (e.g., GML GeoJson)|No|No
EXTRA_POINT1_DESCRIPTOR|String|one of serviceAccess,emergencyAccess,internalDoor,frontDoor,parcel,rooftop|No|No
EXTRA_POINT1_LAT|Number||No|No
EXTRA_POINT1_LON|Number||No|No
EXTRA_POINT2_DESCRIPTOR|String|one of serviceAccess,emergencyAccess,internalDoor,frontDoor,parcel,rooftop|No|No
EXTRA_POINT2_LAT|Number||No|No
EXTRA_POINT2_LON|Number||No|No
EXTRA_POINT3_DESCRIPTOR|String|one of serviceAccess,emergencyAccess,internalDoor,frontDoor,parcel,rooftop|No|No
EXTRA_POINT3_LAT|Number||No|No
EXTRA_POINT3_LON|Number||No|No
