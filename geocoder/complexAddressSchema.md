Field Name |	Data Type	Description	Required for CAP	Required for NCAP
DATABC_ID	number(8,0)	ID used by DataBC; this will be retained internally as the geocoder YourID	yes	yes
SITE_NAME	char(240)			yes
UNIT_DESIGNATOR	char(10)			N/A
UNIT_NUMBER_OR_RANGE	char(50)	See ticket #250, e.g. 100-119,200-219		N/A
UNIT_NUMBER_SUFFIX	char(3)			N/A
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
