---
title: "Additional Map Layer File"
weight: 7
---

## Introduction ##

This document outlines the data structure of a additional map layer file, which the Storm Center map uses to define the external data the clients wants to convey to their customers. Additional map layer files can be delivered via HTTPS POST request to an Additional Map Layer Datafeed endpoint specified by the Data Feed application.

{{<attachments style="orange" />}}

## File Format ##

Additional Map Layer files must comply with the following specification:

+ The files must follow standard GeoJSON format.
+ The geometry data included for an Additional Map Layer can be of type `Polygon`, `LineString`, or `Point`.
+ Each feature in the file will have only one geometry, and all the geometries for the features in the same Additional Map Layer file must be of the same type (all Polygons, all LineStrings, or all Points).
+ The number of data points in each Additional Map Layer file will be limited to 200.
+ The field `properties` for a feature in the file supports properties of the following data types:
    - Number (Integer and Float)
    - String
    - Date-Time (in ISO-8601 format)


 ### Example - The `properties` for a feature including all data types ###
 
`"properties": {
        "startTime": "2016-12-15T13:45:30",
        "crewStatus": "assigned",
        "id": "OUT456",
        "type": "X",
        "pplAff": 100,
        "numberOfHazards"`

### Failure Scenarios ###

If the Additional Map Vector Layer file does not comply with even one of the specifications described above, the file will be discarded. The job processing status will then be marked as Failed in the File Processing Jobs List available in the Deploy Manager dashboard. The reasons for the failure will be noted in the Metadata information associated with the failed job in the File Processing Jobs List.

#### Example - An additional map layer file ####

```
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "properties": {
        "startTime": "2016-12-15T13:45:30",
        "crewStatus": "assigned",
        "id": "OUT456",
        "type": "X",
        "pplAff": 100,
        "numberOfHazards": 1
      },
      "geometry": {
        "coordinates": [
          -111.92232168155347,
          33.417296979668095
        ],
        "type": "Point"
      }
    },
    {
      "type": "Feature",
      "properties": {
        "startTime": "2016-12-15T13:55:30",
        "crewStatus": "assigned",
        "id": "OUT457",
        "type": "WD",
        "pplAff": 250,
        "numberOfHazards": 3
      },
      "geometry": {
        "coordinates": [
          -111.7411580594887,
          33.37573206036812
        ],
        "type": "Point"
      }
    },
    {
      "type": "Feature",
      "properties": {
        "startTime": "2016-12-15T14:05:30",
        "crewStatus": "assigned",
        "id": "OUT458",
        "type": "PD",
        "pplAff": 14051,
        "numberOfHazards": 21
      },
      "geometry": {
        "coordinates": [
          -111.86008990298167,
          33.31103602225062
        ],
        "type": "Point"
      }
    },
    {
      "type": "Feature",
      "properties": {
        "startTime": "2016-12-15T14:15:30",
        "crewStatus": "assigned",
        "id": "OUT459",
        "type": "F0",
        "pplAff": 10,
        "numberOfHazards": 1
      },
      "geometry": {
        "coordinates": [
          -111.9983827442525,
          33.43345574523288
        ],
        "type": "Point"
      }
    },
    {
      "type": "Feature",
      "properties": {
        "startTime": "2016-12-15T14:25:30",
        "crewStatus": "assigned",
        "id": "OUT460",
        "type": "LW",
        "pplAff": 50,
        "numberOfHazards": 1
      },
      "geometry": {
        "coordinates": [
          -110.92050773256545,
          32.376188232851035
        ],
        "type": "Point"
      }
    }
  ]
}

```
