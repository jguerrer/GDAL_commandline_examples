# GDAL_commandline_examples
GDAL examples


Masking a raster with gdalwarp  can be acomplished  in several ways.

One way is to use a file file stored  locally or remotely, which can be hand made or automated by a specific service
In case of a remote geojson, it can be masked as follows.

gdalwarp -cutline "http://localhost:8080/example_polygon.geojsonl.json" -dstalpha -of GTiff e14a29b3.bil e14a29b3_split.bil

Geoserver can also be used as a geojson source if a specific feature is known using CQL and WFS.

A custom postgis service can be created too for such purposes.

In the most simple way, just a web service which takes coordinates as parameters and transmits back a geojson file

http://localhost/getGeojson?coords="x y , x y, ...)"    --> and returns a GeoJSON


or with sql and sql.lite as a OGR data source.

gdalwarp  -cutline cut_sqldemo.sqlite -csql "select ST_GeomFromText('Polygon((478203.50386306538712233 2174402.12770100496709347, 478231.0901067839586176 2172425.1135678393766284, 480235.69048366835340858 2172434.30898241186514497, 479242.58570979902287945 2173427.41375628160312772, 480355.23087311559356749 2174374.54145728657022119, 480355.23087311559356749 2174374.54145728657022119, 478203.50386306538712233 2174402.12770100496709347))')" -dstalpha -of GTiff e14a29b3.bil e14a29b3_split_wkt.bil;



