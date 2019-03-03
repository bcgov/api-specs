# Complex Address Exchange Schema

Field Name |	Data Type |	Description | Required for Civic Address|Required for Non-civic address
----------: | -------------- | -------------- | -------------| ------
YOUR_ID |String|Unique identifier in your local address management system (eg X0233212)| yes|yes
SITE_NAME |String|building or landmark name (eg Centennial Candle)|yes|yes
SUPER_FULL_SITE_DESCRIPTOR|String|names of all sites in parent site hierarchy separated by double-dash (eg Student Union Building -- University of Victoria)|No|No
UNIT_DESIGNATOR |String|Canada Post unit designator (eg APT)|No|No
UNIT_NUMBER|String|unit number or sequence of unit number ranges separated by commas (eg 100-119,200-219)|No|No
UNIT_NUMBER_SUFFIX|String|Canada Post unit number suffix (eg C)|No|No
CIVIC_NUMBER|Number| civic number, usually a positive integer (eg 1321)|yes|no
CIVIC_NUMBER_SUFFIX|String|Canada Post civic number suffix (eg A)
STREET_NAME	char(50)	Full street name including directionals, types and descriptors	yes	
LOCALITY|String|Locality (eg Victoria)|Yes|Yes
LOCALITY_DESCRIPTOR|String|type of locality|(eg Municipality)|Yes|Yes
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
