---
title: "Region File"
weight: 5
---

## Introduction ##

This document outlines the data structure of a region file, which the Storm Center map uses to define the boundaries of a region. Region files can be provided via direct upload to the Instance Manager or via HTTPS PUT request to an endpoint specified by the Instance Manager application.

{{<attachments style="orange" />}}

### Assumptions ###

Geometry boundaries within a region file will not overlap. If any of the provided geometry boundaries within a region file overlap, KUBRA will fail the entire region file.

All thematic areas provided in thematic files will be validated to be within or intersecting the region.

## Geographic Coordinate System ##

The coordinates of each region must be provided in EPSG:4326, also known as WGS84. There is currently no support for providing coordinates in other geographic projection systems. For details about the EPSG:4326 coordinate system, access the {{<extlink title="specification provided by Spatial Reference" url="https://spatialreference.org/ref/epsg/wgs-84/">}}.

## File Structure ##

Region files are defined in JavaScript Object Notation (JSON) format as specified in {{<extlink title="Internet Engineering Task Force standard RFC7159" url="https://tools.ietf.org/html/rfc7159">}}. A JSON object **MUST** be at the root of the region file.

### GeoJSON Specification ###

Region files must adhere to the GeoJSON format specifications published by geojson.org at {{<extlink url="https://tools.ietf.org/html/rfc7946">}}. The file should contain a single `FeatureCollection`. In this collection of `features`, only `Polygon` and `MultiPolygon` geometry types will be consumed. Multiple features can exist in this feature collection.

Values for geometry type are case-sensitive.

{{% notice note %}}
The Storm Center region file does not use any values for the `properties` element, but this element is required as part of the GeoJSON specification.
{{% /notice %}}

#### Example 1 - A region file ####

```
{
   "type":"FeatureCollection",
   "features":[
      {
         "type":"Feature",
         "geometry":{
            "type":"MultiPolygon",
            "coordinates":[[
               [
                  [-111.49,34.50],
                  [-114.91,34.50],
                  [-114.91,31.28],
                  [-111.49,31.28],
                  [-111.49,34.50]
               ]
            ]]
         },
         "properties": {}
      }
   ]
}

```

### Alternate Format - Using Region Codes ###

If an organization has more than one region, or if an organization has one region and some delivery nodes with coordinates outside the boundaries of that region, you can include a region code for each region in the Instance Manager user interface and reference these region codes in the delivery node file. Region codes are case sensitive and can be up to four alphanumeric characters. By default, Storm Center will use the first two alphanumeric characters of the region name as the region code.

Storm Center uses region codes to override spatial scanning for identifying which delivery nodes belong to a region. If a region code is not provided for a delivery node, Storm Center will use spatial scanning to determine which region the delivery node is located in.

### Polygon ###

This section describes considerations and requirements for the `Polygon` geometry type. These considerations and requirements also apply to each individual polygon within the `MultiPolygon` geometry type.

Polygon coordinates are an array of linear ring coordinate arrays. The first linear ring must be the exterior ring of the polygon, followed by any interior linear rings.

A linear ring provided for a polygon must follow the right-hand rule with respect to the area it bounds per section 3.1.6 of the GeoJSON specification.

#### Self-Intersecting ####

Polygons with self-intersecting shapes are considered invalid. KUBRA will not be responsible for identifying these polygons and filtering them out.

#### Non-Closing ####

The polygon shape must start and stop at the same point to be considered a "closed" polygon. KUBRA will identify non-closing polygons and fail the upload process if there are non-closing polygons in the region file.

#### GIS Generalizer ####

KUBRA highly recommends that you use a generalizer tool on GIS data to simplify the edges of the polygons before you include them in a region file. Reducing the number of coordinates helps increase the outage map performance and improve the processing time of delivery node and outage files.

As a starting point for the generalization, KUBRA recommends a Douglas algorithm with a tolerance ratio of 0.0005 for data in EPSG:4326 with the “Preserve shared boundaries” option selected. The “Preserve shared boundaries” option helps avoid overlapping areas or missing space between adjacent areas. You will likely need to adjust the tolerance for the data generalization depending on the detail of your GIS data and the desired result.

### Failure Scenarios ###

KUBRA will consider the region file upload as a failure if any of the following scenarios apply:

1. The region file has zero elements of type `FeatureCollection` or has a `FeatureCollection` with an empty `Features` array.
2. The region file has one or more polygons found to be "non-closing."
3. The region file has one or more `Feature` objects missing the `geometry` element.
4. The region file has one or more `Feature` objects where the `type` element within the `geometry` element is anything other than `Polygon` or `MultiPolygon`.
