+++
title = 'Asset File'
weight = 5
+++

## Introduction

This document outlines the structure of an asset file. Asset files are assumed to be complete snapshots of asset data, as opposed to incremental updates to asset data. IncidentWatch uses the term "asset" to refer to items for which an Organization wants to accept incident reports. For example, these could be streetlights, area lights, traffic lights, signs, water pipes, meters, poles, transformers, bus stops, buildings, or roads.

Asset files must be delivered via HTTPS POST requests to an endpoint specified by the Data Feeds application.

## Geographic Coordinate System

The coordinates of each asset must be provided in EPSG:4326, also known as WGS84. There is currently no support for providing coordinates in other geographic projection systems. For details about the EPSG:4326 coordinate system, access the {{<extlink title="specification provided by Spatial Reference" url="https://spatialreference.org/ref/epsg/wgs-84/">}}.

## Asset Elements

An `asset` member **MUST** contain at least the following elements:

| Element | Description |
| ------- | ----------- |
| id  | A unique ID string provided by the Organization that will identify the asset in the IncidentWatch system. |
| latitude | A number indicating the latitude in EPSG:4326 geographic coordinate system in Decimal Degrees format. |
| longitude | A number indicating the longitude in EPSG:4326 geographic coordinate system in Decimal Degrees format. |

An `asset` member **MAY** contain the following elements:

| Element | Description |
| ------- | ----------- |
| metadata | A configurable set of properties used to track information about an asset to be shown on the IncidentWatch map. The properties to be included in the metadata element are defined as part of an implementation project. |
| servicedBy | A string value indicating which organization services the asset. If this element is not provided, is null, or is empty, IncidentWatch will assume that the client name specified in the creation of the asset management feed is the organization that services the asset. |

{{% notice note %}}
Both the `metadata` element and all of the element properties configured for the metadata element are optional.
{{% /notice %}}

## File Structure

### JSON

The asset file can be sent in JavaScript Object Notation (JSON) format as specified in {{<extlink title="Internet Engineering Task Force standard RFC7159" url="https://tools.ietf.org/html/rfc7159">}}. The file must contain a valid object in JSON. The .json file extension **MUST** be used to indicate file type.

#### Example 1 - An asset file in JSON format

```json
{
  "assets": [
    {
      "id": "PHX01",
      "latitude": 33.468867,
      "longitude": -112.050206,
      "servicedBy": "ABC Energy",
      "metadata":
      {
        "pole_number": "P000120",
        "lamp_type": "colonial",
        "billing_info": "customer"
      }
    },
    {
      "id": "PHX02",
      "latitude": 33.48519,
      "longitude": -112.087285,
      "servicedBy": "City of DEF",
      "metadata":
      {
        "pole_number": "P000121",
        "lamp_type": "colonial",
        "billing_info": "customer"
      }
    },
    {
      "id": "PHX03",
      "latitude": 33.485190,
      "longitude": -112.087285,
      "servicedBy": "City of GHI",
      "metadata":
      {
        "pole_number": "P000122",
        "lamp_type": "colonial",
        "billing_info": "customer"
      }
    }
  ]
}

```

### JSON Lines ###

The asset file can be sent in JSON Lines format as specified on {{<extlink title="jsonlines.org" url="http://jsonlines.org/">}}. Each line is an asset object ending in a new line character. Each asset is defined in JSON. The .jsonl file extension **MUST** be used to indicate file type.

#### Example 2 - An asset file in JSON Lines format

```json
{"id": "PHX01", "latitude":33.468867, "longitude":-112.050206, "servicedBy": "ABC Energy", "metadata": {"pole_number": "P000120", "lamp_type": "colonial", "billing_info": "customer"}}
{"id": "PHX02", "latitude":33.485190, "longitude":-112.087285, "servicedBy": "City of DEF", "metadata": {"pole_number": "P000121", "lamp_type": "colonial", "billing_info": "customer"}}
{"id": "PHX03", "latitude":33.485190, "longitude":-112.087285, "servicedBy": "City of GHI", "metadata": {"pole_number": "P000122", "lamp_type": "colonial", "billing_info": "customer"}}

```

### XML

The asset file can be sent in XML format as specified by the {{<extlink title="W3 XML 1.0 5th Edition recommendation" url="https://www.w3.org/TR/REC-xml/">}} adhering to the following schema:

[asset-schema.xsd](/asset-file.files/asset-schema.xsd)

The .xml file extension **MUST** be used to indicate file type.

#### Example 3 - An asset file in XML format

```xml
<?xml version="1.0"?>
<assets>
  <asset>
    <id>PHX01</id>
    <latitude>33.468867</latitude>
    <longitude>-112.050206</longitude>
    <servicedBy>ABC Energy</servicedBy>
    <metadata>
      <pole_number>P000120</pole_number>
      <lamp_type>colonial</lamp_type>
      <billing_info>customer</billing_info>
    </metadata>
  </asset>
  <asset>
    <id>PHX02</id>
    <latitude>33.485190</latitude>
    <longitude>-112.087285</longitude>
    <servicedBy>City of DEF</servicedBy>
    <metadata>
      <pole_number>P000121</pole_number>
      <lamp_type>colonial</lamp_type>
      <billing_info>customer</billing_info>
    </metadata>
  </asset>
  <asset>
    <id>PHX03</id>
    <latitude>33.485190</latitude>
    <longitude>-112.087285</longitude>
    <servicedBy>City of GHI</servicedBy>
    <metadata>
      <pole_number>P000122</pole_number>
      <lamp_type>colonial</lamp_type>
      <billing_info>customer</billing_info>
    </metadata>
  </asset>
</assets>

```

## Failure Scenarios

KUBRA will reject the asset file upload if any of the following scenarios apply:

1. The file uses an unsupported file format.
1. The file includes invalid or improperly escaped characters.
1. The file includes misaligned records.
1. The file includes unsupported file definition changes, such as changes to the attributes included in the metadata element.

## Compression

{{<extlink title="GZip" url="https://www.gnu.org/software/gzip/">}} file compression is supported for all file types. All GZip compressed files should end with .gz, such as `assets_20180101123045.json.gz`.
