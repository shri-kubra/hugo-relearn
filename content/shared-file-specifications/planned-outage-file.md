---
title: "Planned Outage File"
weight: 9
---

## Introduction ##

This document outlines the structure of a planned outage file. Planned outage files are assumed to be complete snapshots of outage data, as opposed to incremental updates to previously sent outage data.

Planned outage files must be delivered via HTTPS POST requests to an endpoint specified by the Data Feeds application.

{{<attachments style="orange" />}}

## File Structure ##

### JSON ###

Planned outage files can be sent in JavaScript Object Notation (JSON) format as specified in {{<extlink title="Internet Engineering Task Force standard RFC7159" url="https://tools.ietf.org/html/rfc7159">}}. The .json file extension **MUST** be used to indicate file type.

#### Example 1 - A planned outage file in JSON format ####

```json
{
  "plannedOutages": [
    {
      "id": "PO-PHX01",
      "cause": "Tree Trimming",
      "comments": null,
      "start": "2017-04-05T13:27:06.974Z",
      "end": "2017-04-05T17:27:06.974Z",
      "duration": 14400,
      "updatedAt": "2017-04-05T17:27:01.000Z",
      "customersAffected": 10,
      "metadata": {
        "internalNote": "Vegetation Management",
        "affectedTransformers": 5
      },
      "affectedDeliveryNodes": [
        {
          "dnId": "PHX01"
        }
      ],
      "geometry": "MULTIPOLYGON(((-111.49 34.50,-114.91 34.50,-114.91 31.28,-111.49 31.28,-111.49 34.50)),((-113.577 34.610,-112.598 35.411,-113.576 35.411,-113.577 34.610)))"
    },
    {
      "id": "PO-PHX02",
      "cause": "Equipment Maintenance",
      "comments": "Replacing Pole",
      "start": "2017-04-05T08:13:00.000Z",
      "end": "2017-04-05T21:30:00.000Z",
      "duration": 47820,
      "updatedAt": "2017-04-05T17:27:01.000Z",
      "customersAffected": null,
      "metadata": {
        "internalNote": null,
        "affectedTransformers": 1
      },
      "affectedDeliveryNodes": [
        {
          "dnId": "PHX02"
        }
      ]
    }
  ]
}

```

### XML ###

Planned outage files can be sent in XML format as specified by the {{<extlink title="W3 XML 1.0 5th Edition recommendation" url="https://www.w3.org/TR/REC-xml/">}} adhering to the following schema:

> [planned-outages-schema.xsd](../planned-outage-file.files/planned-outages-schema.xsd)

The .xml file extension **MUST** be used to indicate file type.

#### Example 2 - A planned outage file in XML format ####

```xml
<?xml version="1.0"?>
<catalog>
  <plannedOutages>
    <plannedOutage>
      <id>PO-PHX01</id>
      <cause>Tree Trimming</cause>
      <comments></comments>
      <start>2017-04-05T13:27:06.974Z</start>
      <end>2017-04-05T17:27:06.974Z</end>
      <duration>14400</duration>
      <updatedAt>2017-04-05T17:27:01.000Z</updatedAt>
      <customersAffected>10</customersAffected>
      <metadata>
        <internalNote>Vegetation Management</internalNote>
        <affectedTransformers>5</affectedTransformers>
      </metadata>
      <affectedDeliveryNodes>
        <dnId>PHX01</dnId>
      </affectedDeliveryNodes>
      <geometry>MULTIPOLYGON(((-111.49 34.50,-114.91 34.50,-114.91 31.28,-111.49 31.28,-111.49 34.50)),((-113.577 34.610,-112.598 35.411,-113.576 35.411,-113.577 34.610)))</geometry>
    </plannedOutage>
    <plannedOutage>
      <id>PO-PHX02</id>
      <cause>Equipment Maintenance</cause>
      <comments>Replacing Pole</comments>
      <start>2017-04-05T08:13:00.000Z</start>
      <end>2017-04-05T21:30:00.000Z</end>
      <duration>47820</duration>
      <updatedAt>2017-04-05T17:27:01.000Z</updatedAt>
      <customersAffected></customersAffected>
      <metadata>
        <internalNote></internalNote>
        <affectedTransformers>1</affectedTransformers>
      </metadata>
      <affectedDeliveryNodes>
        <dnId>PHX02</dnId>
      </affectedDeliveryNodes>
    </plannedOutage>
  </plannedOutages>
</catalog>

```

## Elements ##

A `plannedOutages` wrapper member is used to encapsulate the planned outage elements. These are referred to as planned outages.

A `plannedOutage` member **MUST** contain at least the following element:

| Element | Description |
| ------- | ----------- |
| id | A string indicating the external ID in your system for tracking planned outages. |

A `plannedOutage` member **MAY** contain the following elements:

| Element | Description |
| ------- | ----------- |
| start | A dateTime representing the date and time of the estimated start of the outage in {{<extlink title="ISO-8601" url="https://www.iso.org/iso-8601-date-and-time-format.html">}} format. |
| end | A dateTime representing the date and time of the estimated end of the outage (possibly also known as the estimated restoration time) in {{<extlink title="ISO-8601" url="https://www.iso.org/iso-8601-date-and-time-format.html">}} format. |
| cause | A string representing the cause of the outage, or a code which can be mapped to a specific string. |
| comments | A string representing comments for the outage. |
| duration | An integer representing the estimated duration of the outage in seconds. |
| updatedAt | A dateTime representing the date and time when the outage status was last updated in ISO-8601 format. |
| customersAffected | The number of customers affected by the planned outage. This element is required when an array of affectedDeliveryNodes is not provided. |
| affectedDeliveryNodes | An array of `affectedDeliveryNodes` members representing the affected delivery nodes or an empty array. This element is required unless a customersAffected element and a geometry element are provided. |
| geometry | A set of coordinates representing the area affected by the planned outage, in {{<extlink title="WKT" url="http://docs.opengeospatial.org/is/12-063r5/12-063r5.html">}} format. Only Point, MultiPoint, LineString, Polygon, and MultiPolygon types will be accepted. This element is required when an array of affectedDeliveryNodes is not provided. |
| metadata | An object to support custom data. This can include custom properties to be displayed with the planned outage that are not represented in the other elements of the `plannedOutage` member. Supported data types for metadata objects are string, number, percentage, datetime, and HTML markup. |

### Relationships between affectedDeliveryNodes, customersAffected, and geometry Elements ###

There are multiple options for presenting information about the area affected by a planned outage and the number of customers affected by a planned outage, depending on the set of optional elements included in the planned outages file.

| Elements Included | Source for Area Affected | Source for Customers Affected |
| ----------------- | ------------------------ | ----------------------------- |
| `affectedDeliveryNodes` | Calculation using latitude and longitude values from delivery nodes identified by `dnId` | Calculation using customers served values from delivery nodes identified by `dnId` |
| `affectedDeliveryNodes` and `geometry` | Coordinates provided in `geometry` | Calculation using customers served values from delivery nodes identified by `dnId` |
| `affectedDeliveryNodes` and `customersAffected` | Calculation using latitude and longitude values from delivery nodes identified by `dnId` | Value provided as `customersAffected` |
| `affectedDeliveryNodes`, `customersAffected`, and `geometry` | Coordinates provided in `geometry` | Value provided as `customersAffected` |
| `customersAffected` and `geometry` | Coordinates provided in `geometry` | Value provided as `customersAffected` |

### Geographic Coordinate System for Geometry Elements ###

Planned outage files support a `geometry` element in {{<extlink title="Well-known text (WKT)" url="https://en.wikipedia.org/wiki/Well-known_text">}} format. Of the geometric objects supported by WKT, planned outage files only support Point, MultiPoint, LineString, Polygon, and MultiPolygon.

Coordinate pairs must be presented with the longitude followed by the latitude. The coordinate points of each geometry element must be provided in EPSG:4326, also known as WGS84. There is currently no support for providing coordinates in other geographic projection systems. For details about the EPSG:4326 coordinate system, access the {{<extlink title="specification provided by Spatial Reference" url="https://spatialreference.org/ref/epsg/wgs-84/">}}.

The Open Geospatial Consortium standard for WKT requires a polygon to be topologically closed. If the exterior linear ring of a polygon is defined in a counter clockwise direction, it will be seen from the "top." Any interior linear rings should be defined in the opposite direction as the exterior ring, in this case, clockwise.

#### Example Point ####

```
POINT(-108.72070312499997 34.99400375757577)
```

#### Example MultiPoint ####

```
MULTIPOINT((-108.72070312499997 34.99400375757577),(-108.71744155883789 34.99203495489647))
```

#### Example LineString ####

```
LINESTRING(-108.71967315673827 34.995128766415135,-108.71641159057616 34.991753693504876,-108.72053146362303 34.989081662082214,-108.7152099609375 34.98865975441066,-108.71091842651366 34.98739401834899)
```

#### Example Polygon without Hole ####

```
POLYGON((-108.72070312499997 34.99400375757577,-100.01953124999997 46.58906908309183,-90.79101562499996 34.92197103616377,-108.72070312499997 34.99400375757577))
```

#### Example Polygon with Hole ####

```
POLYGON((-108.72070312499997 34.99400375757577,-100.01953124999997 46.58906908309183,-90.79101562499996 34.92197103616377,-108.72070312499997 34.99400375757577),(-100.10742187499997 41.47566020027821,-102.91992187499996 37.61423141542416,-96.85546874999996 37.54457732085582,-100.10742187499997 41.47566020027821))
```

#### Example MultiPolygon without Hole ####

```
MULTIPOLYGON(((-108.72070312499997 34.99400375757577,-100.01953124999997 46.58906908309183,-90.79101562499996 34.92197103616377,-108.72070312499997 34.99400375757577)),((-85.16601562499999 34.84987503195417,-80.771484375 28.497660832963476,-76.904296875 34.92197103616377,-85.16601562499999 34.84987503195417)))
```

#### Example MultiPolygon with Hole ####

```
MULTIPOLYGON(((-108.72070312499997 34.99400375757577,-100.01953124999997 46.58906908309183,-90.79101562499996 34.92197103616377,-108.72070312499997 34.99400375757577),(-100.10742187499997 41.47566020027821,-102.91992187499996 37.61423141542416,-96.85546874999996 37.54457732085582,-100.10742187499997 41.47566020027821)),((-85.16601562499999 34.84987503195417,-80.771484375 28.497660832963476,-76.904296875 34.92197103616377,-85.16601562499999 34.84987503195417)))
```

### Affected Delivery Node Elements ###

An `affectedDeliveryNodes` member **MUST** contain at least the following element:

| Element | Description |
| ------- | ----------- |
| dnId | A string indicating the delivery node ID. |

An `affectedDeliveryNodes` member **MAY** contain the following elements:

| Element | Description |
| ------- | ----------- |
| confidence | A string representing the confidence level. The default value is LOW. This value is case sensitive and must match exactly one of the following values: `LOW`, `MEDIUM`, or `HIGH`. |
| callbackContact | A string representing the callback contact information such as a phone number or email. |
| reported | A boolean to determine whether the outage for the affected delivery node was reported by a customer. |

## Failure Scenarios ##

Complete and partial planned outage file processing failures are described on the [Data Feed Processing Failures page](/shared-file-specifications/failure-types/#planned-outage-files).

If an outage is discarded from the planned outage file, outage data associated with that outage will not appear on the map.

## Compression ##

{{<extlink title="GZip" url="https://www.gnu.org/software/gzip/">}} file compression is supported for all file types. All GZip compressed files should end with .gz, such as `plannedOutages_20180101123045.json.gz`.
