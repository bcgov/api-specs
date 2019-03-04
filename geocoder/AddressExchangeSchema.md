# Physical Address Exchange Schema

The Physical Address Exchange Schema can be used to exchange physical addresses between software systems. The schema supports the exchange of the following types of address situations:

- Addresses of buildings without units
- Addresses of buildings assigned single or multiple civic numbers
- Addresses that have no civic number (landmark or non-civic addresses)
- Addresses of buildings with multiple units
- Addresses of complexes that contain multiple buildings
- Addresses of buildings that contain sub-buildings (e.g., floors, wards, wings)

An address can have rooftop, vehicle access, and other locations. Units within buildings and buildings within complexes can have their own rooftop and vehicle access locations (e.g., townhouse units within a complex, buildings within a campus).

Vancouver International Airport
    - Terminal A
         - Gate 1-35
    - Terminal B
         - Gate 1-40
    - Terminal C
         - Gate 1-20



Field Name |	Data Type |	Description | Required for Civic Address|Required for Non-civic address
---: | --- | --- | ---| ---
YOUR_ID |String|Unique identifier in your local address management system (eg X0233212)| yes|yes
SITE_NAME |String|building or landmark name (eg Centennial Candle)|yes|yes
SUPER_FULL_SITE_DESCRIPTOR|String|names of all sites in parent site hierarchy separated by double-dash (eg Student Union Building -- University of Victoria)|No|No
UNIT_DESIGNATOR |String|Canada Post unit designator (eg APT)|No|No
UNIT_NUMBER|String|unit number or sequence of unit number ranges separated by commas (eg 100-119,200-219)|No|No
UNIT_NUMBER_SUFFIX|String|Canada Post unit number suffix (eg C)|No|No
CIVIC_NUMBER|Number| civic number, usually a positive integer (eg 1321)|yes|no
CIVIC_NUMBER_SUFFIX|String|Canada Post civic number suffix (eg A)
STREET_NAME|String|Street name|Yes|No
STREET_TYPE|String|Street type|No|No
IS_STREET_TYPE_PREFIX|Boolean| True if street type appears before street name as in HWY 17
STREET_DIRECTION|String|Canada Post street direction (eg NW); Note CP does not allow prefix and suffix street type in same address|No|No
IS_STREET_DIRECTION_PREFIX|Boolean|true if street direction appears before street name as in SW Marine Dr
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
