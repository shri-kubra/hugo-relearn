---
title: "Thematic File"
weight: 6
---

## Introduction ##

This document outlines the data structure of a thematic file, which the Storm Center map uses to create thematic map overlays. The combination of boundary and metadata for each provided shape is called a **thematic area**. A collection of thematic areas in a thematic file is called a **thematic**.

The organization using Storm Center must provide thematic files for each type of thematic, such as County, ZIP Code, or City/Town/Village (CTV).

Thematic files can be provided via direct upload to the Instance Manager or via HTTPS PUT request to an endpoint specified by the Instance Manager application.

{{<attachments style="orange" />}}

### Assumptions ###

Delivery Nodes will be validated to be both within the calculated boundary formed by the region provided in the region file and within a specific thematic area polygon or multi-polygon shape provided in the thematic file or files chosen to filter delivery nodes.

If a region code, an area code, or both are provided for a delivery node, those values will be used instead of spatial scanning to validate the delivery node.

KUBRA will not be responsible for ensuring continuity of a thematic file against a specific region.

Thematic areas will share borders but never overlap one another. KUBRA will provide verification of overlapping thematic areas and fail the entire thematic file if this constraint is violated.

## Geographic Coordinate System ##

The coordinates of each thematic area must be provided in EPSG:4326, also known as WGS84. There is currently no support for providing coordinates in other geographic projection systems. For details about the EPSG:4326 coordinate system, access the {{<extlink title="specification provided by Spatial Reference" url="https://spatialreference.org/ref/epsg/wgs-84/">}}.

## File Structure ##

Thematic files are defined in JavaScript Object Notation (JSON) format as specified in {{<extlink title="Internet Engineering Task Force standard RFC7159" url="https://tools.ietf.org/html/rfc7159">}}. A JSON object **MUST** be at the root of the thematic file.

### GeoJSON Specification ###

Thematic files must adhere to the GeoJSON format specifications published by geojson.org at {{<extlink url="https://tools.ietf.org/html/rfc7946">}}. The file should contain a single `FeatureCollection`. In this collection of features, only `Polygon` and `MultiPolygon` geometry types will be consumed. All other features will be ignored. Each feature is required to have a `properties` element. In the `properties` element, there must be at minimum a `name` element.

Values for geometry type are case-sensitive.

#### Example 1 - A thematic file ####

```json
{
   "type":"FeatureCollection",
   "features":[
      {
         "type":"Feature",
         "properties":{
            "name":"Mohave"
         },
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
         }
      }
   ]
}

```

### Hierarchy ###

`hierarchy` is an optional element to allow nested tree structures within outage summary reports linked to the Storm Center outage map.

You can choose to define a thematic hierarchy. If you do, you will need to provide information about this hierarchy to KUBRA. If a hierarchy configuration exists for the Storm Center map, each thematic area is expected to have each of the specified hierarchy elements. These hierarchy elements do not have any ordering requirements.

Here is an example of a hierarchy configuration in which one hierarchy is specified for a thematic of type “County.”

```json
{
    "properties":{
           "name":"Westchester",
           "hierarchy":{
              "state":"New York"
           }
        }
}

```

Here is an example of a hierarchy configuration in which two hierarchies are specified for a thematic of type “CTV.” The hierarchies for each thematic area are not required to be in a specific order.

```json
{
    "properties":{
           "name":"Tigard",
           "hierarchy":{
              "state":"Oregon",
              "county":"Washington"
           }
        }
}

```

### Alternate Format - Using Area IDs and Area Type ###

If you want to override spatial scanning for identifying which delivery nodes belong to a thematic area, you can include an `areaId` within the `properties` element for each feature in the thematic file and reference these area IDs in the delivery node file.

{{% notice note %}}
The `areaId` must be unique across the thematic file. The `areaId` value can be the same as the value for the `name` field, as long as the name is unique across the thematic file.
{{% /notice %}}

You must also reference the `areaType` in the delivery node file. The `areaType` is determined when you create a new thematic in the Instance Manager interface. The `areaType` is either the value selected from the "Select Area Type" drop-down list, or the value you enter for a custom area type.

{{% notice note %}}
The `areaType` value is case-sensitive and must be all lowercase for the default values: "county," "zip," or "ctv." `areaType` values must be 15 characters or less.
{{% /notice %}}

#### Example 2 - A thematic file with area IDs ####

```json
{
    "type": "FeatureCollection",
    "features": [
        {
            "type": "Feature",
            "properties": {
                "areaId": "AREA01",
                "hierarchy": {
                    "state": "Arizona"
                },
                "name": "Mohave"
            },
            "geometry": {
                "type": "MultiPolygon",
                "coordinates": [[
                    [
                        [-111.49,34.50],
                        [-114.91,34.50],
                        [-114.91,31.28],
                        [-111.49,31.28],
                        [-111.49,34.50]
                    ]
                ]]
            }
        }
    ]
}

```

### Polygon ###

This section describes considerations and requirements for the `Polygon` geometry type. These considerations and requirements also apply to each individual polygon within the `MultiPolygon` geometry type.

Polygon coordinates are an array of linear ring coordinate arrays. The first linear ring must be the exterior ring of the polygon, followed by any interior linear rings.

A linear ring provided for a polygon must follow the right-hand rule with respect to the area it bounds per section 3.1.6 of the GeoJSON specification.

#### Self-Intersecting ####

Polygons with self-intersecting shapes are considered invalid. KUBRA will not be responsible for identifying these polygons and filtering them out.

#### Non-Closing ####

The polygon shape must start and stop at the same point to be considered a "closed" polygon. KUBRA will identify non-closing polygons and fail the upload process if there are non-closing polygons in the thematic file.

#### GIS Generalizer ####

KUBRA highly recommends that you use a generalizer tool on GIS data to simplify the edges of the polygons before you include them in a thematic file. Reducing the number of coordinates helps increase the outage map performance and improve the processing time of delivery node and outage files.

As a starting point for the generalization, KUBRA recommends a Douglas algorithm with a tolerance ratio of 0.0005 for data in EPSG:4326 with the “Preserve shared boundaries” option selected. The “Preserve shared boundaries” option helps avoid overlapping areas or missing space between adjacent areas. You will likely need to adjust the tolerance for the data generalization depending on the detail of your GIS data and the desired result.

### Failure Scenarios ###

KUBRA will consider the thematic file upload as a failure if any of the following scenarios apply:

1. The thematic file has zero elements of type `FeatureCollection` or has a `FeatureCollection` with an empty `Features` array.
2. The thematic file has one or more polygons found to be "non-closing."
3. The thematic file has one or more thematic areas found to be overlapping one another.
4. If hierarchies are configured and the thematic file has one or more Features missing one or more of the configured hierarchies.
5. The thematic file has one or more `Feature` objects missing the `properties` element or the `name` element within `properties`.
6. The thematic file has one or more `Feature` objects missing the `geometry` element.
7. The thematic file has one or more `Feature` objects where the `type` element within the `geometry` element is anything other than `Polygon` or `MultiPolygon`.
