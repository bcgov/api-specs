# Geocoder Faults
Name | Definition
-------: | ---------------
<a name="CIVIC_NUMBER.missing">Civic Number Missing</a> | A given address didn't contain a civic number but one was found.
<a name="CIVIC_NUMBER.notInAnyBlock">Civic Number Not In Any Block</a> | A given civic number is not in any known address range for a given street in a given locality. The street within the given locality is returned with a match precision of STREET. 
<a name="CIVIC_NUMBER_SUFFIX.notMatched">Civic Number Suffix Not Matched</a> | A given civic number suffix for a given civic number and street was not found in a given locality.
<a name="LOCALITY.isAlias">Locality Is Alias</a>	| A given civic number and street were found in an alias of the given locality but not the locality itself.
<a name="LOCALITY.missing">Locality Missing</a> | A given address didn’t contain a locality name but one was found that contains the given civic number and street.
<a name="LOCALITY.notMatched">Locality Not Matched</a> | A given locality does not contain a given civic number and street but another locality was found that does.
<a name="LOCALITY.spelledWrong">Locality Spelled Wrong</a> | A given locality was spelled wrong but was successfully corrected to match a known locality. 
<a name="POSTAL_ADDRESS_ELEMENT.notAllowed">Postal Address Element Not Allowed</a> | An element of a mailing address was detected (e.g., PO, BOX nn, SS, RR nn, a postal code. All such elements are ignored.
<a name="PROVINCE.missing">Province Missing</a> | A given address didn't contain a province code (e.g., BC)
<a name="PROVINCE.notMatched">Province Not Matched</a> |	A province code other than BC was found 
<a name="SITE_NAME.missing"> Site Name missing</a> |	A given address didn't contain a site name but one was found.
<a name="SITE_NAME.notMatched">Site Name Not Matched</a> | A given site name was not found. A match without a site name is returned.
<a name="SITE_NAME.partiallyMatched">Site Name Partially Matched</a> | Some of the words in a site name were matched. A match with a full site name is returned.
<a name="SITE_NAME.spelledWrong">Site Name Spelled Wrong</a> |	A given site name was spelled wrong but was successfully matched to a known site.
<a name="STREET.missing">Street Missing</a> | A given address didn't contain a street but one was found.
<a name="STREET_DIRECTION.missing">Street Direction Missing</a> | A given address didn’t contain a street direction for a given street name and street type in a given locality but one was found.
<a name="STREET_DIRECTION.notMatched">Street Direction Not Matched</a> | A given street direction for a given street name and street type in a given locality was not found. A match without the street direction is returned.
<a name="STREET_DIRECTION.notPrefix">Street Direction Not Prefix</a> | A given street direction was placed before street name instead of after. A match with a correctly positioned street direction is returned.
<a name="STREET_DIRECTION.notSuffix">Street Direction Not Suffix</a> | A given street direction was placed after street name instead of before. A match with a correctly positioned street direction is returned.
<a name="STREET_DIRECTION.spelledWrong">Street Direction Spelled Wrong</a> | A given street direction was spelled wrong. A match with a correctly spelled street direction is returned.
<a name="STREET_NAME.isAlias">Street Name Is Alias</a> | A given street name is an alias for the official street name. A match with the official street name is returned.
<a name="STREET_NAME.missing">Street Name Missing</a> | A given address didn't contain a street name but one was found.
<a name="STREET_NAME.notMatched">Street Name Not Matched</a> | A given streetName within a given locality was not found. The locality is returned with a match precision of LOCALITY. Other addresses in different localities that contain the given civic number and street will also be returned but with a lesser score.
<a name="STREET_NAME.spelledWrong">Street Name Spelled Wrong</a> | A given street name was spelled wrong but was successfully corrected to match a known street name with the given locality.
<a name="STREET_QUALIFIER.missing">Street Qualifier Missing</a> | A given address didn't contain a street qualifier but one was found.
<a name="STREET_QUALIFIER.notMatched">Street Qualifier Not Matched</a> | A given street qualifier was not found. A match without a street qualifier is returned.
<a name="STREET_QUALIFIER.spelledWrong">Street Qualifier Spelled Wrong</a> | A given street qualifier was spelled wrong but was successfully corrected to match a known street qualifier.
<a name="STREET_TYPE.missing">Street Type Missing</a> | A given address didn’t contain a street type for a given street name in a given locality but one was found.
<a name="STREET_TYPE.notMatched">Street Type Not Matched</a> | A given street type for a given street name in a given locality was not found. A match containing the correct street type is returned.
<a name="STREET_TYPE.notPrefix">Street Type Not Prefix</a> | A given street street was placed before street name instead of after. A match with a correctly positioned street type is returned.
<a name="STREET_TYPE.notSuffix">Street Type Not Suffix</a> | A given street type was placed after street name instead of before. A match with a correctly positioned street type is returned.
<a name="STREET_TYPE.spelledWrong">Street Type Spelled Wrong</A> | A given street type was spelled wrong but was successfully corrected to match a known street type.
<a name="UNRECOGNIZED_ELEMENT.notAllowed">Unrecognized element notAllowed</a>	| There are unnecessary or redundant words in an address. For example, the following address has a redundant streetType (e.g., Road): 33457 COTTAGE LANE ROAD ABBOTSFORD BC. The following address has an unnecessary site name (e.g., ABERDEEN SQUARE) : ABERDEEN SQUARE 101-2764 BARNET HIGHWAY COQUITLAM BC
Unit Designator Is Alias | A given unit designator is an alias of the official unit designator. A match containing the official unit designator is returned.
Unit Designator Missing | A given address didn't contain a unit designator but one was found.
Unit Designator Not Matched | A given unit designator was not found. A match containing the correct unit designator is returned.
Unit Designator Spelled Wrong | A given unit designator was spelled wrong but was successfully corrected to match a known unit designator.
Unit Number Missing | A given address didn't contain a unit number but one was found.
Unit Number Not Matched | A given unit number was not found. A match containing the correct unit number is returned.
Unit Number Suffix missing | A given address didn't contain a unit number suffix but one was found.
Unit Number Suffix Not Matched | A given unit number suffix was not found. A match containing the correct unit number suffix is returned.
