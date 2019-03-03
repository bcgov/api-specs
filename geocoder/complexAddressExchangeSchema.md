# Complex Address Exchange Schema

Field Name |	Data Type |	Description |	Example | Required for CAP |	Required for NCAP
----------: | -------------- | --------------------- | ------------------| ------------- | ---------
YOUR_ID |String|Unique identifier in your local address management system|X0233212| yes|yes
SITE_NAME |String|building or landmark name|Centennial Candle|yes|yes
SUPER_FULL_SITE_DESCRIPTOR|String|names of all sites in parent site hierarchy|Student Union Building -- University of Victoria|No|No
UNIT_DESIGNATOR |String|Canada Post unit designator|APT|No|No
UNIT_NUMBER|String| unit number or sequence of unit number ranges separated by commas|100-119,200-219|No|No
UNIT_NUMBER_SUFFIX| Canada Post unit number suffix|C|No|No
CIVIC_NUMBER	number(6,0)		yes	N/A
CIVIC_NUMBER_SUFFIX	char(3)			N/A
STREET_NAME	char(50)	Full street name including directionals, types and descriptors	yes	
LOCALITY	char(50)		yes	yes
LOCATION_DESCRIPTOR	char(20)	parcelPoint, frontDoor, etc	yes	yes
SITE_POSITIONAL_ACCURACY	char(6)	low, medium or high	yes	yes
SITE_LATITUDE	number(13,9)		yes	yes
SITE_LONGITUDE	number(13,9)		yes	yes
AP_POSITIONAL_ACCURACY	char(6)	only used for custom AP locations (low, medium or high)		
AP_LATITUDE	number(13,9)	only used for custom AP locations		
AP_LONGITUDE	number(13,9)	only used for custom AP locations		
AP_TYPE	char(4)	CAP or NCAP	yes	yes
IS_PRIMARY_IND	char(1)	Y or N	yes	yes
NARRATIVE_LOCATION	char(240)			
PSEUDO_SITE	char(1)	Y or N [a pseudo site will only be used for generating address ranges from CAPs]	yes	yes [set to N]
superFullSiteDescriptor	char(240)	See ticket #146, e.g. Patient Care Centre--Royal Miracle Hospital		
SOURCE_NOTES	char(240)	DataBC custom comments		
