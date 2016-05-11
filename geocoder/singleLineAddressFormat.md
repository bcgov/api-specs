#Single-Line Address Format Specification

An address may be represented by a single line (string) in one of the formats listed below. 

In each format, a term in square brackets is optional, a term in square brackets followed by an asterisk means the term may appear zero or more times, and a term in square brackets followed by a plus sign means the term may appear one or more times. 

A term in brace brackets may appear in none or one of the multiple places indicated. Brace brackets are used for terms that may appear before or after another term. More specifically, streetDirection and streetType may appear before or after streetName but not both. Note also, that a given address can't have more than one streetDirection or streetType as per [Canada Post Guidelines]((https://www.canadapost.ca/tools/pg/manual/PGaddress-e.asp?ecid=murl10006450#1418611)  

frontGate is the double dash delimiter as in “--“ . 

##Format 1 – Civic address

{occupantName[,]}[[unitDesignator unitNumber[unitNumberSuffix]] [siteName],]* frontGate civicNumber[civicNumberSuffix] {streetDirection} {streetType} streetName {streetType} {streetDirection} [streetQualifier], localityName, provinceCode

streetDirection and streetType may appear before or after streetName but an address may have 


##Format 2 – Non-civic address

{occupantName[,]}[[unitDesignator unitNumber[unitNumberSuffix]] [siteName],]* frontGate [{streetDirection} {streetType} streetName {streetType} {streetDirection} [streetQualifier],] localityName, provinceCode


##Format 3 – Intersection address

{streetDirection} {streetType} streetName {streetType} {streetDirection} [streetQualifier] [ and {streetDirection} {streetType} streetName {streetType} {streetDirection} [streetQualifier] ]+ , localityName, provinceCode


##Examples

###Example 1 - Civic Address

420A GORGE RD E, VICTORIA, BC

which contains the following address elements:

Address Element |	Value
----: | -----------
civicNumber |	420
civicNumberSuffix |	A
streetName |	GORGE
streetType |	RD
streetDirection |	E
localityName |	VICTORIA
provinceCode |	BC


###Example 2 - Civic address with unit

UNIT 1A -- 433 CEDAR RAPIDS BLVD, PEMBERTON, BC 

which contains the following address elements:

Address Element |	Value
----: | -----------
unitDesignator |	UNIT
unitNumber |	1
unitNumberSuffix |	A
civicNumber |	433
streetName |	CEDAR RAPIDS
streetType |	BLVD
localityName |	PEMBERTON
provinceCode |	BC

###Example 3 - Non-civic address with a street qualifier:

JOHNSON ST BRIDGE, VICTORIA, BC 

which contains the following address elements:

Address Element |	Value
----: | -----------
streetName |	JOHNSON
streetType |	ST
streetQualifier |	BRIDGE
localityName |	VICTORIA
provinceCode |	BC

###Example 4 - Civic address with an occupant

UVIC Main Campus -- 3800 Finnerty Rd, Saanich, BC

###Example 5.	Civic addresses with a unit within a named complex 

PAD 2, HAPPY MOBILE HOME PARK -- 1200 NORTH PARK RD, SHAWNIGAN LAKE, BC 
ROOM 103A, CLEARIHUE BUILDING, UNIVERSITY OF VICTORIA -- 3800 FINNERTY RD, VICTORIA, BC 
ROOM 230, WEST BLOCK, ROYAL JUBILEE HOSPITAL -- 1952 BAY ST, VICTORIA, BC 

###Example 6.	Non-civic addresses with a unit within a named complex 

PAD 2, HAPPY MOBILE HOME PARK -- NIMPO LAKE, BC 
PAD 2, HAPPY MOBILE HOME PARK -- REMOTE RD, NIMPO LAKE, BC 


### Example 7.	Non-civic addresses containing a street, locality, and  province 

WILLOW DRIVE, 70 MILE HOUSE, BC 
HORSE LAKE ROAD, 100 MILE HOUSE, BC
JOHNSON ST BRIDGE, VICTORIA, BC 

###Example 8.	Non-civic addresses containing only locality and province 

PEACE RIVER REGIONAL DISTRICT, BC 
100 MILE HOUSE, BC 
PYPER LAKE, BC 

###Example 9.	Intersection addresses 

Douglas St and Johnson St, Victoria, BC
Douglas St and Gorge Rd E and Hillside Ave, Victoria, BC

 
#Alternative Address Formats
On input, the addresses and occupant/addresses resources can also handle the following alternatives to single-line address format:

1.	Unit without a frontGate:
PAD 2, 1200 NORTH PARK RD, SHAWNIGAN LAKE, BC 

2.	Unit number without a frontGate and unitDesignator (as per Canada Post):
2-1200 NORTH PARK RD, SHAWNIGAN LAKE, BC 

3.	Unit following street (as per Canada Post):
1200 NORTH PARK RD PAD 2, SHAWNIGAN LAKE, BC 
