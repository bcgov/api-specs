# Geomark Glossary of Terms
Term | Definition
----: | -----------
<a name="allowOverlap">Allow Overlap</a> | If [Geometry Count](https://github.com/bcgov/api-specs/blob/master/geomark/glossary.md#geometryCount) is set to Many, this option will allow overlapping geometries if set to 'true'.
<a name="area">Area (area)</a> | Area of the placemark in hectares.
<a name="placemarkKml">Placemark KML (placemarkKml)</a> | KML text that specifies geometry or geometries of a geomark.
<a name="boundingBox">Bounding Box (boundingBox)</a> |  A comma separated list of the western, southern, eastern, and northern extent of the geomark in geographic coordinates. Western and eastern extent are displayed as decimal degrees of longitude. Northern and southern extent are displayed as decimal degrees of latitude. 
<a name="bufferCap">Buffer Cap (bufferCap)</a> | The style of buffer to use at each end of a buffered line (e.g., round, square, flat).
<a name="bufferJoin">Buffer Join (bufferJoin)</a> | The style of buffer to use for joins between the line segments for lines and polygons (e.g., round, mitre,bevel).
<a name="bufferMitreLimit">Buffer Mitre Limit (bufferMitreLimit)</a> | The number of line segments used in each quadrant to approximate the curve for round end-cap and join styles. Must be a positive number.
<a name="bufferMetres">Buffer Width (bufferMetres)</a> | The amount to buffer the geometry (in metres). Must be a positive integer (e.g., 10). If left blank, no buffer will be added to input geometries and points and lines will stay points and lines. If a buffer is specified, point and line inputs will become polygons.
<a name="bufferSegments">Buffer Segments</a> | The number of line segments used in each quadrant to approximate the curve of a buffer for round end-cap and join styles. Larger numbers will produce a smoother curve (must be greater than 0).
<a name="centroid">Centroid (centroid)</a> | The latitude and longitude of a point at or near the centre of a geomark or, if the centre is outside the polygon, some point guaranteed to be inside the polygon
<a name="creationDate">Creation Date (creationDate)</a> | The date the geomark was created.
<a name="expiryDate">Expiry Date (expiryDate)</a> | The date a geomark expires. Once expired, it will no longer be accessible. If a geomark is in use by a government application, it will never expire until it is no longer required by that application.
<a name="geomarkId">ID (geomarkId)</a> | A unique, immutable, and meaningless identifier assigned to the geomark.
<a name="geometryCount">Geometry Count (geometryCount)</a> | The number of geometries in the geomark. If you select One, the first geometry in a feature, feature collection or geometry collection will be used. If you select Many, all geometries of the selected geometry type will be used. Multiple geometries, buffered or not, can’t overlap. (1mm tolerance)
<a name="geometryType">Geometry Type (geometryType)</a> | Type of input geometry. Valids types are Point, Line, Polygon, Any. 
<a name="isRobust">Is Geometry Robust (isRobust)</a> | A geometry that has a minimum clearance of less than one millimetre is not robust. Minimum clearance is the shortest distance between any two points or between a line and a point in the geometry. A geometry that is not robust will self-intersect when loaded into a spatial data store or application. For more info, see Interchange of Spatial Data – Inhibiting Factors (PDF)
<a name="isSimple">Is Geometry Simple (isSimple)</a> | A simple geometry is closed and doesn’t self-intersect or have self-tangent points. For more info, see the Simple Feature Access - Part 2: SQL Option
<a name="isValid">A geometry is valid if it meets the validity conditions for the given geometry type. For example, a linear ring must be simple. A polygon must consist of one outer boundary and zero or more inner boundaries, all of which must be simple. All inner boundaries must be contained within the outer boundary without touching. For more info, see ST_IsValid - PostGIS
<a name="length">Length (length)</a> | Length of the geomark in kilometers.
<a name="numVertices">Vertex Count (numVertices)</a> | Number of vertices in all polygon boundaries of the geomark. A polygon without holes has a single, outer boundary, a polygon with one hole has one outer boundary and one inner boundary.
<a name="validationError">Validation Error (validationError)</a> | Detailed validation error message if geometry is not valid; blank otherwise.
minimum, longitude maximum, latitude maximum in the default output SRS, 4326 (WGS84).
<a name="centre">centre</a> | The coordinates of a centre point (x,y) used to define a bounding circle that will limit the search area. centre and maxDistance together define a search area.
<a name="changeDate">changeDate</a> | The date a site or intersection address was last changed.
<a name="geomark">geomark</a> | A point, line, or polygon of interest that can be shared in a variety of formats and map projections. Geomarks are created by the <a href="https://apps.gov.bc.ca/pub/geomark/">Geomark Service</a>.
<a name="geomarkURL">geomarkURL</a> | The URL of a polygon geomark that should be used by the geocoder as a bounding box in the /bgeo/sites/within query. Point and line geomarks will not work. When specifying this URL programmatically, it should be url-encoded without format and projection parameters.
<a name="version">version</a> | Software version of the REST Web Service
