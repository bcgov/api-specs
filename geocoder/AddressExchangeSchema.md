# Physical Address Exchange Schema

The Physical Address Exchange Schema can be used to exchange physical addresses between software systems. The schema supports the exchange of the following types of address situations:

- Addresses of buildings without units
- Addresses of buildings assigned single or multiple civic numbers
- Addresses that have no civic number (landmark or non-civic addresses)
- Addresses of buildings with multiple units
- Addresses of complexes that contain multiple buildings
- Addresses of buildings that contain sub-buildings (e.g., floors, wards, wings)

An address can have rooftop, vehicle access, and other locations. Units within buildings and buildings within complexes can have their own rooftop and vehicle access locations (e.g., townhouse units within a complex, buildings within a campus).

## Example 1 - Multiple buildings distinguished by unit number prefix

810 Esquimalt Rd, Esquimalt, BC has three buildings A,B,C. Each building has four floors with 10 units each numbered 100-110, 200-210, 300-310, and 400-410

Field | Value
-----: | ------
UNIT_DESIGNATOR| APT
UNIT_NUMBER_PREFIX|A-C
UNIT_NUMBER_RANGE|100-110,200-210,300-310,400-410
CIVIC_NUMBER|810
STREET_NAME|Esquimalt
STREET_TYPE|Rd
LOCALITY|Esquimalt
PROVINCE_CODE|BC

If this example was provided as reference data to the BC Address Geocoder, the Geocoder would derive full addresses such as:

APT A100 -- 810 Esquimalt Rd,Esquimalt,BC

APT B407 -- 810 Esquimalt Rd,Esquimalt,BC

APT C210 -- 810 Esquimalt Rd,Esquimalt,BC

## Example 2 - A complex with multiple levels of units

Vancouver International Airport, 3211 Grant McConachie Way, Richmond, BC has the following terminals and gates:
- Terminal A
  - Gate 1-35
- Terminal B
  - Gate 1-40
- Terminal C
  - Gate 1-20

The airport itself is represented as follows:

Field | Value
----:|----
SITE_NAME|Vancouver International Airport
CIVIC_NUMBER|3211
STREET_NAME|Grant McConnachie
STREET_TYPE|Way
LOCALITY|Richmond
PROVINCE_CODE|BC

The terminals are represented as follows:

Field | Value
----:|----
UNIT_DESIGNATOR|Terminal
UNIT_NUMBER|A-C
SUPER_SITE_FULL_DESCRIPTOR|Vancouver International Airport
CIVIC_NUMBER|3211
STREET_NAME|Grant McConnachie
STREET_TYPE|Way
LOCALITY|Richmond
PROVINCE_CODE|BC

The Terminal A gates are represented as follows:

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

The gates of terminals B and C are represented similarly.

If this example was provided as reference data to the BC Address Geocoder, the Geocoder would derive full addresses such as:

Vancouver International Airport -- 3211 Grant McConnachie Way,Richmond,BC
Terminal C, Vancouver International Airport -- 3211 Grant McConnachie Way,Richmond,BC
Gate 23, Terminal A, Vancouver International Airport -- 3211 Grant McConnachie Way,Richmond,BC 
Gate 7, Terminal B, Vancouver International Airport -- 3211 Grant McConnachie Way,Richmond,BC 

Each Terminal and Gate can have its own site and access locations

## Example 3 - A complex of buildings

Given the following addresses for UBC in Vancouver:

University of British Columbia -- 2329 West Mall,Vancouver,BC 
Koerner Library -- 958 Main Mall,Vancouver,BC


and assume that the Koerner library has three floors of rooms numbered 100-120,200-220, and 300-320

the university itself is represented as follows:

Field | Value
----:|----
SITE_NAME|University of British Columbia
CIVIC_NUMBER|2329
STREET_NAME|West Mall
LOCALITY|Vancouver
PROVINCE_CODE|BC

The library is represented as:

Field | Value
----:|----
SITE_NAME|Koerner Library
CIVIC_NUMBER|1958
STREET_NAME|Main Mall
LOCALITY|Vancouver
PROVINCE_CODE|BC
EXTRA_POINT1_DESCRIPTOR|emergencyAccess
EXTRA_POINT_LAT|<latitude of Koerner Library emergency access point>
EXTRA_POINT_LAT|<longitude of Koerner Library emergency access point>

The representation above includes a special emergency access point. Regular access and front door points are not shown.

The rooms within the library are represented as:

Field | Value
----:|----
UNIT_DESIGNATOR|Room
UNIT_NUMBER|100-120,200-220,300-320
SUPER_SITE_FULL_DESCRIPTOR|Koerner Library, University of British Columbia
CIVIC_NUMBER|1958
STREET_NAME|Main mall
LOCALITY|Richmond
PROVINCE_CODE|BC

and the BC Address Geocoder would derive addresses such as:

University of British Columbia -- 2329 West Mall,Vancouver,BC 
Koerner Library -- 958 Main Mall,Vancouver,BC
Room 105, Koerner Library -- 958 Main Mall,Vancouver,BC

## Schema Definition
This schema can be used in any common text format that supports named properties including CSV,TSV,JSON, and XML

Field Name | Data Type |	Description | Required for Civic Address|Required for Non-civic address
---: | --- | --- | ---| ---
YOUR_ID |String|Unique identifier in your local address management system (eg X0233212)| yes|yes
UNIT_DESIGNATOR |String|Canada Post unit designator (eg APT)|No|No
UNIT_NUMBER_PREFIX|String|a single letter or sequence of letter ranges separated by commas (eg A-D,J,M-P)
UNIT_NUMBER|String|unit number or letter or sequence of unit number/letter ranges separated by commas (eg 100-119,200-219)|No|No
UNIT_NUMBER_SUFFIX|String|Canada Post unit number suffix (eg C)|No|No
SITE_NAME |String|building or landmark name (eg Centennial Candle)|yes|yes
SUPER_FULL_SITE_DESCRIPTOR|String|names of all sites in parent site hierarchy separated by double-dash (eg Student Union Building -- University of Victoria)|No|No
CIVIC_NUMBER|Number| civic number, usually a positive integer (eg 1321)|yes|no
CIVIC_NUMBER_SUFFIX|String|Canada Post civic number suffix (eg A)
STREET_NAME|String|Street name|Yes|No
STREET_TYPE|String|Street type|No|No
IS_STREET_TYPE_PREFIX|Boolean| True if street type appears before street name as in HWY 17
STREET_DIRECTION|String|Canada Post street direction (eg NW); Note CP does not allow prefix and suffix street type in same address|No|No
IS_STREET_DIRECTION_PREFIX|Boolean|true if street direction appears before street name as in SW Marine Dr
LOCALITY|String|Locality (eg Victoria)|Yes|Yes
LOCALITY_DESCRIPTOR|String|type of locality|(eg Municipality)|Yes|Yes
PROVINCE_CODE|String|Canada Post two-character province code|Yes|Yes
IS_NON_CIVIC_ADDRESS|Boolean|True if address has no assigned civic number|Yes|Yes
IS_OFFICIAL_ADDRESS|Boolean|True if address is official; False if unofficial (e.g., former address)|Yes|Yes
NARRATIVE_LOCATION|String|step by step directions to a non-civic address location|No|Yes	
SITE_POINT_DESCRIPTOR|String|centroid (e.g., parcel centroid), parcel (e.g., somewhere in parcel),rooftop,frontDoor (eg parcel)|Yes|Yes
SITE_POSITIONAL_ACCURACY|Number|positional accuracy of N represents +/- metres|yes|yes
SITE_LAT|number(13,9)|site latitude|yes|yes
SITE_LON|	number(13,9)|site longitude|yes|yes
AP_POSITIONAL_ACCURACY|Number|access point positional accuracy in metres|yes|yes
AP_LAT|Number(13,9)|Only needed if access point is different than main civic address access point|No|Yes
AP_LON|Number(13,9)|Only needed if access point is different than main civic address access point|No|Yes	
EXTRA_POINT1_DESCRIPTOR|String|type of extra point 1 if needed (eg serviceAccess)|Yes|Yes
EXTRA_POINT1_POSITIONAL_ACCURACY|Number|positional accuracy of N represents +/- N metres|yes|yes
EXTRA_POINT1_LAT|number(13,9)||yes|yes
EXTRA_POINT1_LON|number(13,9)||yes|yes
