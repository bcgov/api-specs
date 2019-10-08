# Single-Line Address Format Specification

A physical address may be represented by a single line (string) in one of the formats listed below. 

In each format, a term in square brackets is optional, a term in square brackets followed by an asterisk means the term may appear zero or more times, and a term in square brackets followed by a plus sign means the term may appear one or more times. 

A term in brace brackets may appear in none or one of the multiple places indicated. Brace brackets are used for terms that may appear before or after another term. More specifically, streetDirection and streetType may appear before or after streetName. Note also, that a given address can't have more than one streetDirection as per [Canada Post Guidelines](https://www.canadapost.ca/tools/pg/manual/PGaddress-e.asp?ecid=murl10006450#1418611)  

Civic number suffix, if present, should be placed after the civic number as follows:

1. Without a space between the civic number and the civic number suffix, if the suffix is a letter character (e.g.,"A")

2. With one space between the civic number and the civic number suffix, if the suffix is a fraction
3. A fractional suffix can be a string containing <numerator>/<denominator> as in "1/2", or it can be a single, UTF-8 fraction character. 

Unit number suffix, if present, should be place after unitNumber without a space in between.


frontGate is the double dash separator as in “--“ . 
occupantSeparator is double star as in "**"

## Format 1 – Civic address

[[unitDesignator unitNumber[unitNumberSuffix]] [siteName],]* frontGate civicNumber[civicNumberSuffix] {streetDirection} {streetType} streetName {streetType} {streetDirection} [streetQualifier], localityName, provinceCode

## Format 2 – Civic occupant address

occupantName occupantSeparator [[unitDesignator unitNumber[unitNumberSuffix]] [siteName],]* frontGate civicNumber[civicNumberSuffix] {streetDirection} {streetType} streetName {streetType} {streetDirection} [streetQualifier], localityName, provinceCode

## Format 3 – Non-civic address

[[unitDesignator unitNumber[unitNumberSuffix]] [siteName],]* frontGate [{streetDirection} {streetType} streetName {streetType} {streetDirection} [streetQualifier],] localityName, provinceCode

## Format 4 – Non-civic occupant address

occupantName occupantSeparator [[unitDesignator unitNumber[unitNumberSuffix]] [siteName],]* frontGate [{streetDirection} {streetType} streetName {streetType} {streetDirection} [streetQualifier],] localityName, provinceCode

## Format 5 – Intersection address

{streetDirection} {streetType} streetName {streetType} {streetDirection} [streetQualifier] [ and {streetDirection} {streetType} streetName {streetType} {streetDirection} [streetQualifier] ]+ , localityName, provinceCode


## Examples

### Example 1 - Civic address with street direction

420A GORGE RD E, VICTORIA, BC

which contains the following address elements:

Address Element |	Value
----: | -----------
civicNumber |	420
civicNumberSuffix |	A
streetName |	GORGE
streetType |	RD
streetDirection |	E
isStreetDirectionPrefix | false
localityName |	VICTORIA
provinceCode |	BC

### Example 2 - Civic address with prefix street direction

2233 SW MARINE DR, VANCOUVER, BC

which contains the following address elements:

Address Element |	Value
----: | -----------
civicNumber |	2233
streetName |	MARINE
streetType |	DR
streetDirection |	SW
isStreetDirectionPrefix | true
localityName |	VANCOUVER
provinceCode |	BC


### Example 3 - Civic Address on highway

5745 HWY 3, BRIDESVILLE, BC

which contains the following address elements:

Address Element |	Value
----: | -----------
civicNumber |	5745
streetName |	3
streetType |	HWY
isStreetTypePredirectional | true
localityName |	BRIDESVILLLE
provinceCode |	BC

### Example 3 - Civic Address on named highway

17270 Cariboo Hwy, Buckhorn, BC

which contains the following address elements:

Address Element |	Value
----: | -----------
civicNumber |17270
streetName |	Cariboo
streetType |	HWY
isStreetTypePredirectional | false
localityName |	Buckhorn, BC
provinceCode |	BC

### Example 5 - Civic address with unit

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

### Example 6 - Non-civic address with a street qualifier:

JOHNSON ST BRIDGE, VICTORIA, BC 

which contains the following address elements:

Address Element |	Value
----: | -----------
streetName |	JOHNSON
streetType |	ST
streetQualifier |	BRIDGE
localityName |	VICTORIA
provinceCode |	BC

### Example 7 - Civic occupant address

UVIC Main Campus ** 3800 Finnerty Rd, Saanich, BC

which contains the following occupant address elements:

Address Element |	Value
----: | -----------
occupantName|UVIC Main Campus
civicNumber |3800
streetName |	Finnerty
streetType |	Rd
localityName |	Saanich
provinceCode |	BC

### Example 8.	Civic addresses with a unit within a named complex 

PAD 433, SHAWNIGAN LAKE MOBILE HOME PARK -- 2785 Wallbank Rd., Shawnigan Lake, BC  

which contains the following address elements:

Address Element |	Value
----: | -----------
unitDesignator |	Pad
unitNumber |	433
siteName|SHAWNIGAN LAKE MOBILE HOME PARK
civicNumber |	2785
streetName |	WallBank
streetType |	Rd
localityName |	Shawnigan Lake
provinceCode |	BC

ROOM 103A, CLEARIHUE BUILDING, UNIVERSITY OF VICTORIA -- 3800 Finnerty Rd, Saanich, BC

which contains the following address elements:

unitDesignator |	Room
unitNumber |	103A
siteName|CLEARHUE BUILDING
fullSiteDescriptor|CLEARIHUE BUILDING, UNIVERSITY OF VICTORIA
civicNumber |	3800
streetName |	Finnerty
streetType |	Rd
localityName |	Saanich
provinceCode |	BC

ROOM 230, WEST BLOCK, ROYAL JUBILEE HOSPITAL -- 1952 BAY ST, VICTORIA, BC   

which contains the following address elements:

unitDesignator |	Room
unitNumber |	230
siteName|WEST BLOCK
fullSiteDescriptor|WEST BLOCK, ROYAL JUBILEE HOSPITAL
civicNumber |	1952
streetName |	Bay
streetType |	St
localityName |	Victoria
provinceCode |	BC


### Example 9.	Non-civic address with a unit within a named complex 

PAD 2, HAPPY MOBILE HOME PARK -- REMOTE RD, NIMPO LAKE, BC   

which contains the following address elements:

unitDesignator |	Pad
unitNumber |	2
siteName| Happy Mobile Home Park
streetName|Remote
streetType|Rd
localityName |	Nimpo Lake
provinceCode |	BC

### Example 10.	Non-civic occupant address with a unit within a named complex 
 
Paws N Suds ** PAD 2, HAPPY MOBILE HOME PARK -- REMOTE RD, NIMPO LAKE, BC 

which contains the following occupant address elements:

occupantName|Paws N Suds
unitDesignator |Pad
unitNumber |2
siteName| appy Mobile Home Park
streetName|Remote
streetType|Rd
localityName |Nimpo Lake
provinceCode |BC

### Example 11.	Non-civic addresses containing a street, locality, and  province 

WILLOW DRIVE, 70 MILE HOUSE, BC   
HORSE LAKE ROAD, 100 MILE HOUSE, BC  
JOHNSON ST BRIDGE, VICTORIA, BC   

### Example 12.	Non-civic addresses containing only locality and province 

PEACE RIVER REGIONAL DISTRICT, BC   
100 MILE HOUSE, BC   
PYPER LAKE, BC 

### Example 13.	Intersection addresses 

Douglas St and Johnson St, Victoria, BC  
Douglas St and Gorge Rd E and Hillside Ave, Victoria, BC

 
# Alternative Address Formats
On input, the addresses and occupant/addresses resources can also handle the following alternatives to single-line address format:

1.	Unit without a frontGate:
Pad 433, 2785 Wallbank Rd., Shawnigan Lake, BC

2.	Unit number without a frontGate and unitDesignator (as per Canada Post):
433-2785 Wallbank Rd., Shawnigan Lake, BC

3.	Unit following street (as per Canada Post):
2785 Wallbank Rd. Pad 433, Shawnigan Lake, BC
