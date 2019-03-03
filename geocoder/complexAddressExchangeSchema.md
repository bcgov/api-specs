# Complex Address Exchange Schema

Field Name |	Data Type |	Description |	Example | Required for Civic Address|Required for Non-civic address
----------: | -------------- | --------------------- | ------------------| ------------- | ---------
YOUR_ID |String|Unique identifier in your local address management system|X0233212| yes|yes
SITE_NAME |String|building or landmark name|Centennial Candle|yes|yes
SUPER_FULL_SITE_DESCRIPTOR|String|names of all sites in parent site hierarchy separated by double-dash|Student Union Building -- University of Victoria|No|No
UNIT_DESIGNATOR |String|Canada Post unit designator|APT|No|No
UNIT_NUMBER|String|unit number or sequence of unit number ranges separated by commas|100-119,200-219|No|No
UNIT_NUMBER_SUFFIX|String|Canada Post unit number suffix|C|No|No
CIVIC_NUMBER|Number| civic number, usually a positive integer|yes|no
CIVIC_NUMBER_SUFFIX|String|Canada Post civic number suffix|A
STREET_NAME	char(50)	Full street name including directionals, types and descriptors	yes	
LOCALITY|String|Locality|Victoria|Yes|Yes
LOCALITY_DESCRIPTOR|String|type of locality|Municipality|Yes|Yes
IS_NON_CIVIC_ADDRESS|Boolean|True if address has no assigned civic number|Yes|Yes
IS_OFFICIAL_ADDRESS|Boolean|True if address is official; False if unofficial (e.g., former address)|Yes|Yes
NARRATIVE_LOCATION|String|step by step directions to a non-civic address location||No|Yes	
SITE_POINT_DESCRIPTOR|String|centroid (e.g., parcel centroid), parcel (e.g., somewhere in parcel),rooftop,frontDoor|parcel|Yes|Yes
SITE_POSITIONAL_ACCURACY|Number|positional accuracy of N represents +/- metres|3|yes|yes
SITE_LAT|number(13,9)||yes|yes
SITE_LON|	number(13,9)||yes|yes
AP_POSITIONAL_ACCURACY|Number|access point positional accuracy in metres|3|yes|yes
AP_LAT|Number(13,9)|Only needed if access point is different than main civic address access point|No|Yes
AP_LON|Number(13,9)|Only needed if access point is different than main civic address access point|No|Yes	
EXTRA_POINT1_DESCRIPTOR|String|type of extra point 1 if needed for service access points, building panel|serviceAccess|Yes|Yes
EXTRA_POINT1_POSITIONAL_ACCURACY|Number|positional accuracy of N represents +/- N metres|3|yes|yes
EXTRA_POINT1_LAT|number(13,9)||yes|yes
EXTRA_POINT1_LON|	number(13,9)||yes|yes
