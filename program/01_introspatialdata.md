[Overview](./00_overview.md) |
[Introduction to spatial data](./01_introspatialdata.md) |
[Using spatial data](./02_usingspatialdata.md) |
[Closeout](./05_closeout.md)

# Introduction to spatial data

| *75 min* |
| --------- |

## Preparations for exercies
To ensure you are able to work through this morning, please make sure you have the package `cartopy` installed in the environment.

We're going to explore geocoding using [LocationIQ's API](https://locationiq.com). If you've never used an API before this might be a fun introduction to how most servers talk to each other on the web.

Before you get going you will need to have a LocationIQ API key - something that authenticates you as 'not a bot' to LocationIQ's servers. You can get one by heading over here and signing up for an account: https://www.locationiq.com/

Then you'll need to create an access token to let Python access the API. You can do this here: https://my.locationiq.com/dashboard#account

## Fundamental concepts for spatial analysis

| *5 min*  |
| --------- |

1. Space
2. Location
3. Distance

See this website on Introduction to [Spatial Thinking](https://learn.canvas.net/courses/464/pages/unit-1-dot-4-spatial-thinking) for more on these fundamental concepts.
### Space

There are different types of space, for example: 
1.	Absolute space: mathematical space – everything is given an (x, y, z) tuple and positions are unambiguous. Example: Geographic space, geological map of WA.
2.	Relative space: topological space - used to represent connectivity between features of the world. Precise measurement not as important. Example: Railway map for the metro.
3.	Cognitive space: reflects people’s beliefs, experiences and perceptions about places. You might know how to get to your office quite well, but not other offices in the rest of the building. Emphasizes space via relevance to you. Example – a mud map to get your tradies to site.

### Location

1. Absolute: an unambiguous descriptor of location, expressed as a coordinate. Can’t be confused with any other location. Example:  Latitude and longitude.
2. Relative: Site (physical attributes of location) and situation (location relative to other places). Example: Perth is located far from other cities, near raw materials etc. Or 191 St Georges Terrace
3.	Cognitive: Compiled from personal knowledge, experiences, and impressions. Example: traditional knowledge of waterholes as a resource, then a stock route, then a 4WD track. Same physical location but different perception.
4.	Nominal: *Where were you when…?* Linking space and time. Example: Where were you when you heard about 9/11?

### Distance

1.	Absolute: a physical unit of measure Example: kilometers between two assets
2.	Relative: Generally calculated using time, effort or cost (will differ from absolute – what happens when you go over a mountain range?). Example: voting maps sized by number of seats vs area.
3.	Cognitive: Individual perception of distance. Example: driving in NZ vs driving in Australia

## Geospatial Data types

| *10 min*  |
| --------- |

Geospatial data are a representations of reality, typically in a geographic space, defined as an object that may or may not have attributes. Geospatial data types can be defined as 2-dimensional or 3-dimensional.

### Object
Determined by whether we are describing a discrete (e.g. river, lake, outcrop) or continuous (e.g. temperature, elevation) spatial phenomena.

1.	Raster data: Regularly defined geographic space, often used for representing continuous phenomena. Example: orthophotos, remote sensing
2.	Vector data: Defined as point, line, or polygon. Often used for representing discrete phenomena. Example: River locations
3.	Point clouds: Vector space representation of a 3D surface or object. Example: lidar data

[ArcGIS Blog on using point cloud data](https://www.esri.com/arcgis-blog/products/3d-gis/3d-gis/point-cloud-smart-mapping-in-3d-with-scene-viewer/)

### Attributes

Anything that we want to describe about the object. For example:

1. Raster attribute: elevation, temperature
2. Vector attribute: Name of river, pH measurement, date of pH measurement
3. Point cloud attribue: Color of feature at point location

### Data storage format

1.	Raster: There are numerous formats, and often specialty data will have unique formats. A common and protable format is GeoTiff. All formats are more or less an "image" (i.e. array of values) with some metadata showing the grid parameters (start, stop, step, and an affine transformation to warp to projection)

2.	Vector: GeoJSON, Shapefile (record by record geometries, according to some schema). 

## Spatial reference frame

| *10 min*  |
| --------- |

A static reference surface for identifying locations on the earth. The actual location values (latitude, longitude) will vary depending on the reference frame. For this reason, *it is important to make sure all spatial data have the appropriate spatial reference information in the metadata.*

Spatial reference frames are specified by the datum and projection.

### Datums
A datum identifies how locations are specified on earth's surface.

A spheroid (or ellipsoid) is an approximation for the earth's surface. There are different spheroids that are more accurate for specific parts of the world. The actual surface of the earth is irregular (i.e. it is not a perfect sphere).

The datum builds upon the reference spheroid and incorporates more localized elevation variations. There are global and local datums.

Global datums can be used to represent world-wide data. The most commonly used is the World Geodetic System of 1984 (WGS84).

Local datums incorporate more local variations that global datums, and are fixed to the area of interest. They should only be used to locate data within the region specified by the datum.

For the Australian continent, a new datum has recently been released called GDA2020. This datum will replace the GDA94 datum that had been the standard.

[A National Geographic article about why Australia is updating the standard datum to GDA2020](https://www.nationalgeographic.com/news/2016/09/australia-moves-gps-coordinates-adjusted-continental-drift/)

### Projections

A projection specifies how to represent the features from a spheroidal surface on a flat plane. Types of projection techniques include:
- azimuthal
- cylindrical
- conical

Projections may cause distortions in how the data is reprented. Consider different projections depending on the use of the final product use. Things to consider are:
- size preserving
- shape preserving
- distance between features preserving
- direction between features preserving

## Exercise: Intro to spatial data

| *50 min*  |
| --------- |

Open [am1_intro_to_spatial_data.ipynb.ipynb](../notebooks/am1_intro_to_spatial_data.ipynb) and go through the notebook.