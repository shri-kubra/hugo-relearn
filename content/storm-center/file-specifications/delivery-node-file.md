---
title: "Delivery Node File"
weight: 7
---

## Introduction ##

This document outlines the structure of a delivery node file. Delivery node files are assumed to be complete snapshots of delivery node data, as opposed to incremental updates to delivery node data. This means that every delivery node file must contain at least one valid delivery node to be processed successfully.

Storm Center uses the term "delivery node" to refer to locations with IDs in an Outage Management System. For example, these could be premises, meters, or transformers. Although it is not a requirement, KUBRA expects delivery node files to include multiple valid delivery nodes to represent all physical locations in the area indicated by the region file that could potentially be affected by outages.

Delivery node files must be delivered via HTTPS POST requests to an endpoint specified by the Data Feeds application.

{{<attachments style="orange" />}}

## Geographic Coordinate System ##

The coordinates of each delivery node must be provided in EPSG:4326, also known as WGS84. There is currently no support for providing coordinates in other geographic projection systems. For details about the EPSG:4326 coordinate system, access the {{<extlink title="specification provided by Spatial Reference" url="https://spatialreference.org/ref/epsg/wgs-84/">}}.

## Delivery Node Elements ##

A `deliveryNode` member **MUST** contain at least the following elements:

| Element | Description |
| ------- | ----------- |
| id  | A string indicating the external id in your Outage Management System (OMS).|
| latitude | A number indicating the latitude in EPSG:4326 geographic coordinate system in Decimal Degrees format. |
| longitude | A number indicating the longitude in EPSG:4326 geographic coordinate system in Decimal Degrees format. |

A `deliveryNode` member **MAY** contain the following elements:

| Element | Description |
| ------- | ----------- |
| customersServed  | An integer indicating the number of customers served by the delivery node. If the value supplied in the Delivery Node file is null, Storm Center will assume a value of 1.|
| areas | An array of `areaType` and `areaId` elements associated with the delivery node. These elements are specified to override spatial scanning. The value for `areaType` must match the value selected in the [Create New Thematic form](/storm-center/configuration-guide/connect-data-files/#set-up-thematic-data) in Instance Manager. `areaType` values are case-sensitive and must be 15 characters or less. The values for `areaId` must match values for `areaId` provided in the corresponding thematic file. If `areaId` is not provided in the thematic file, `name` is used instead.|
| regionCode | An identifier for the region associated with the delivery node. This element is specified to override spatial scanning when there are multiple regions within the instance. If an instance has only one region, this element can be omitted, and Storm Center will assume the value of the only region associated with the instance. The value of this element is defined when you upload a region file in the Instance Manager user interface. `regionCode` values are case sensitive and must be 4 alphanumeric characters or less. |
| articles | An array of strings. Storm Center uses the number of strings to identify the number of customers served when a `customersServed` element is not provided. |

## File Structure ##

### JSON ###

The delivery node file can be sent in JavaScript Object Notation (JSON) format as specified in {{<extlink title="Internet Engineering Task Force standard RFC7159" url="https://tools.ietf.org/html/rfc7159">}}. The file must contain a valid object in JSON. The .json file extension **MUST** be used to indicate file type.

{{% notice note %}}
If an organization has more than one million delivery node elements, or if the unzipped delivery node file size is 100MB or greater, KUBRA recommends that the organization use either JSON Lines format or XML format for the delivery node files instead of JSON format.
{{% /notice %}}

#### Example 1 - A delivery node file in JSON format ####

```json
{
  "nodes": [
    {
      "id": "PHX01",
      "latitude": 33.468867,
      "longitude": -112.050206,
      "customersServed": 2
    },
    {
      "id": "PHX02",
      "latitude": 33.48519,
      "longitude": -112.087285,
      "customersServed": 3
    }
  ]
}

```

#### Example 2 - A delivery node file in JSON format with region code, area IDs, and area types ####

```json
{
  "nodes": [
    {
      "id": "PHX01",
      "latitude": 33.468867,
      "longitude": -112.050206,
      "customersServed": 2,
      "areas": [
        { "areaId": "05", "areaType": "county" },
        { "areaId": "85006", "areaType": "zip" }
      ],
      "regionCode": "AZ"
    },
    {
      "id": "PHX02",
      "latitude": 33.48519,
      "longitude": -112.087285,
      "customersServed": 3,
      "areas": [
        { "areaId": "05", "areaType": "county" },
        { "areaId": "85006", "areaType": "zip" }
      ],
      "regionCode": "AZ"
    }
  ]
}

```

### JSON Lines ###

The delivery node file can be sent in JSON Lines format as specified on {{<extlink title="jsonlines.org" url="http://jsonlines.org/">}}. Each line is a delivery node object ending in a new line character. Each delivery node is defined in JSON. The .jsonl file extension **MUST** be used to indicate file type.

#### Example 3 - A delivery node file in JSON Lines format ####

```json
{"id": "PHX01", "latitude":33.468867, "longitude":-112.050206, "customersServed": 2}
{"id": "PHX02", "latitude":33.485190, "longitude":-112.087285, "customersServed": 3}
{"id": "PHX03", "latitude":33.485190, "longitude":-112.087285, "customersServed": 2}

```

#### Example 4 - A delivery node file in JSON Lines format with region code, area IDs, and area types ####

```json
{"id": "PHX01", "latitude":33.468867, "longitude":-112.050206, "customersServed": 2, "areas": [{"areaId":"05","areaType":"county"}, {"areaId":"85006","areaType":"zip"}], "regionCode":"AZ"}
{"id": "PHX02", "latitude":33.485190, "longitude":-112.087285, "customersServed": 3, "areas": [{"areaId":"05","areaType":"county"}, {"areaId":"85013","areaType":"zip"}], "regionCode":"AZ"}
{"id": "PHX03", "latitude":33.485190, "longitude":-112.087285, "customersServed": 2, "areas": [{"areaId":"05","areaType":"county"}], "regionCode":"AZ"}

```

### XML ###

The delivery node file can be sent in XML format as specified by the {{<extlink title="W3 XML 1.0 5th Edition recommendation" url="https://www.w3.org/TR/REC-xml/">}} adhering to the following schema:

> [dn-schema.xsd](../delivery-node-file.files/dn-schema.xsd)

The .xml file extension **MUST** be used to indicate file type.

#### Example 5 - A delivery node file in XML format ####

```xml
<?xml version="1.0"?>
<catalog>
  <dn>
    <id>PHX01</id>
    <latitude>33.468867</latitude>
    <longitude>-112.050206</longitude>
    <customersServed>2</customersServed>
  </dn>
  <dn>
    <id>PHX02</id>
    <latitude>33.485190</latitude>
    <longitude>-112.087285</longitude>
    <customersServed>3</customersServed>
  </dn>
  <dn>
    <id>PHX03</id>
    <latitude>33.485190</latitude>
    <longitude>-112.087285</longitude>
    <customersServed>2</customersServed>
  </dn>
</catalog>

```

#### Example 6 - A delivery node file in XML format with region code, area IDs, and area types ####

```xml
<?xml version="1.0"?>
<catalog>
  <dn>
    <id>PHX01</id>
    <latitude>33.468867</latitude>
    <longitude>-112.050206</longitude>
    <customersServed>2</customersServed>
    <areas>
      <areaType>county</areaType>
      <areaId>05</areaId>
    </areas>
    <areas>
      <areaType>zip</areaType>
      <areaId>85006</areaId>
    </areas>
    <regionCode>AZ</regionCode>
  </dn>
  <dn>
    <id>PHX02</id>
    <latitude>33.485190</latitude>
    <longitude>-112.087285</longitude>
    <customersServed>3</customersServed>
    <areas>
      <areaType>county</areaType>
      <areaId>05</areaId>
    </areas>
    <areas>
      <areaType>zip</areaType>
      <areaId>85013</areaId>
    </areas>
    <regionCode>AZ</regionCode>
  </dn>
  <dn>
    <id>PHX03</id>
    <latitude>33.485190</latitude>
    <longitude>-112.087285</longitude>
    <customersServed>2</customersServed>
    <areas>
      <areaType>county</areaType>
      <areaId>05</areaId>
    </areas>
    <regionCode>AZ</regionCode>
  </dn>
</catalog>

```

## Notes ##

+ Storm Center will default the value of Customers Served to “1” in the absence of a value for Customers Served.
+ Spatial scanning is used to determine a region for each delivery node if the delivery node file doesn't include a region code for the delivery node.
+ Spatial scanning is used to determine areas for each delivery node if the delivery node file doesn't include an area ID for the delivery node of the appropriate area type.
+ Each delivery node file must contain at least one valid delivery node member.

## Failure Scenarios ##

Complete and partial delivery node file processing failures are described on the [Data Feed Processing Failures page](/shared-file-specifications/failure-types/#delivery-node-files).

If a delivery node is discarded from the delivery node file, outage data associated with that delivery node will not appear on the map.

If the `areaId` for an area type not selected to filter delivery nodes is invalid, the delivery node will not be discarded from the delivery node file, but outage information related to that delivery node will not appear in the outage layer for that area type or in the summary report for that area type. For example, if a map view includes both county and ZIP code area types, delivery nodes are filtered by county, and a delivery node has an invalid ZIP code `areaId`, then outage information related to that delivery node will not appear on the "View outages by ZIP Code" map layer or in the summary report for outages by ZIP Code.

{{% notice note %}}
For information on selecting an area type to filter delivery nodes, see the [Connect Data Files and Feeds page](/storm-center/configuration-guide/connect-data-files/#connect-data-files-as-sources-for-a-map-instance) of the Configuration Guide.
{{% /notice %}}

## Compression ##

{{<extlink title="GZip" url="https://www.gnu.org/software/gzip/">}} file compression is supported for all file types. All GZip compressed files should end with .gz, such as `dn_20180101123045.json.gz`.
