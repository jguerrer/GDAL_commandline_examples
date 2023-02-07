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


