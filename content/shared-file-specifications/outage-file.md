---
title: "Outage File"
weight: 8
---

## Introduction ##

This document outlines the structure of an outage file. Outage files are assumed to be complete snapshots of outage data, as opposed to incremental updates to previously sent outage data.

Outage files must be delivered via HTTPS POST requests to an endpoint specified by the Data Feeds application.

{{<attachments style="orange" />}}

## File Structure ##

### JSON ###

The outage file can be sent in JavaScript Object Notation (JSON) format as specified in {{<extlink title="Internet Engineering Task Force standard RFC7159" url="https://tools.ietf.org/html/rfc7159">}}. The file must contain a valid object in JSON. The .json file extension **MUST** be used to indicate file type.

#### Example 1 - An outage file in JSON format ####

```json
{
  "outages": [
    {
      "id": "O-PHX01",
      "outageConfirmed": true,
      "crewStatus": "ENROUTE",
      "crewIconIndicator": true,
      "cause": "Branch On Line",
      "comments": null,
      "etr": null,
      "etrConfidence": "LOW",
      "startedAt": "2017-04-02T17:27:06.974Z",
      "updatedAt": "2017-04-05T17:27:06.974Z",
      "affectedDeliveryNodes": [
        {
          "dnId": "PHX01",
          "confidence": "HIGH",
          "callbackContact": "16235479403",
          "reported": true
        },
        {
          "dnId": "PHX03",
          "confidence": "HIGH",
          "callbackContact": "15551234567",
          "reported": true
        }
      ]
    }
  ],
  "restorations": [
    {
      "id": "O-PHX02",
      "restorationConfidence": "HIGH",
      "restoredAt": "2017-04-05T17:27:06.974Z",
      "customersRestored": 10,
      "cause": "Branch Removed",
      "restoredDeliveryNodes": [
        {
          "dnId": "PHX02",
          "confidence": "HIGH",
          "callbackContact": "16235479403",
          "reported": true
        }
      ]
    }
  ],
  "cancellations": {
    "id": "O-SANC01",
    "metadata": {
      "comments": "Power Available",
      "internalComments": "This outage was confirmed to be invalid. Power is still available in this area.",
      "status": "Confirmed Power On"
    },
    "cancelledDeliveryNodes": [{
      "dnId": "SANC001",
      "confidence": "MEDIUM",
      "callbackContact": "",
      "reported": false
    }],
  }
}

```

### XML ###

The outage file can be sent in XML format as specified by the {{<extlink title="W3 XML 1.0 5th Edition recommendation" url="https://www.w3.org/TR/REC-xml/">}} adhering to the following schema:

> [outages-schema.xsd](../outage-file.files/outages-schema.xsd)

The .xml file extension **MUST** be used to indicate file type.

#### Example 2 - An outage file in XML format ####

```xml
<?xml version="1.0"?>
<catalog>
  <outages>
    <outage>
      <id>O-PHX01</id>
      <outageConfirmed>true</outageConfirmed>
      <crewStatus>ENROUTE</crewStatus>
      <crewIconIndicator>true</crewIconIndicator>
      <cause>Branch on Line</cause>
      <comments></comments>
      <etr></etr>
      <etrConfidence>LOW</etrConfidence>
      <startedAt>2017-04-02T17:27:06.974Z</startedAt>
      <updatedAt>2017-04-05T17:27:06.974Z</updatedAt>
      <affectedDeliveryNodes>
        <dnId>PHX01</dnId>
        <confidence>HIGH</confidence>
        <callbackContact>16235479403</callbackContact>
        <reported>true</reported>
      </affectedDeliveryNodes>
      <affectedDeliveryNodes>
        <dnId>PHX03</dnId>
        <confidence>HIGH</confidence>
        <callbackContact>15551234567</callbackContact>
        <reported>true</reported>
      </affectedDeliveryNodes>
    </outage>
  </outages>
  <restorations>
    <restoration>
      <id>O-PHX02</id>
      <restorationConfidence>HIGH</restorationConfidence>
      <restoredAt>2017-04-05T17:27:06.974Z</restoredAt>
      <customersRestored>10</customersRestored>
      <cause>Vegetation Removed</cause>
      <metadata>
        <reportedBy>IVR</reportedBy>
        <deviceType>TRANSFORMER</deviceType>
      </metadata>
      <restoredDeliveryNodes>
        <dnId>PHX02</dnId>
        <confidence>HIGH</confidence>
        <callbackContact>16235479403</callbackContact>
        <reported>true</reported>
      </restoredDeliveryNodes>
    </restoration>
  </restorations>
  <cancellations>
    <cancellation>
      <id>O-SANC01</id>
      <metadata>
        <comments>Situation Contained</comments>
        <internalComments>This outage was confirmed to be invalid. Power is still available in this area.</internalComments>
        <status>Confirmed Power On</status>
      </metadata>
      <cancelledDeliveryNodes>
        <dnId>SANC001</dnId>
        <confidence>MEDIUM</confidence>
        <callbackContact></callbackContact>
        <reported>false</reported>
      </cancelledDeliveryNodes>
    </cancellation>
  </cancellations>
</catalog>

```

## Outage Elements ##

An `outages` wrapper member is used to encapsulate the outage elements. These are also referred to as unplanned outages.

An `outage` member **MUST** contain at least the following elements:

| Element | Description |
| ------- | ----------- |
| id | A string indicating the external ID in your Outage Management System (OMS). |
| affectedDeliveryNodes | An array of `affectedDeliveryNodes` members representing the affected delivery nodes or an empty array. |

An `outage` member **MAY** contain the following elements:

| Element | Description |
| ------- | ----------- |
| crewStatus | A string indicating the crew status, or a code which can be mapped to a specific string. |
| crewIconIndicator | A boolean used to determine whether the crew icon is shown for the outage location on the Storm Center map. If “True,” the crew icon will be shown. If “False,” the crew icon will not be shown. This element is used by Storm Center and is not used by Notifi. |
| etr | A dateTime representing the date and time of estimated time of restoration (ETR) in {{<extlink title="ISO-8601" url="https://www.iso.org/iso-8601-date-and-time-format.html">}} format. |
| etrConfidence | A string representing the confidence level of the ETR. The default value is LOW. This value is case sensitive and must match exactly one of the following values: `LOW`, `MEDIUM`, or `HIGH`. ETR Confidence is used by Notifi and is not used by Storm Center. |
| cause | A string representing the cause of the outage, or a code which can be mapped to a specific string. |
| comments | A string representing comments for the outage. |
| startedAt | A dateTime representing the date and time when the outage started in ISO-8601 format. |
| updatedAt | A dateTime representing the date and time when the outage status was last updated in ISO-8601 format. |
| restoredAt | A dateTime representing the date and time when the outage was restored in ISO-8601 format. This element is used by Storm Center and is not used by Notifi. |
| outageConfirmed | A boolean that indicates whether the outage has been confirmed by a customer. This element is used by Notifi and is not used by Storm Center. |
| metadata | An object to support custom data. This can include custom properties to be displayed with the outage that are not represented in the other elements of the `outage` member. Supported data types for metadata objects are string, number, percentage, datetime, and HTML markup. |

The following is an example of a `metadata` object with two properties:

```
"metadata" : {
    "affectedTransformers": "3",
    "environmentStatus": "UNSAFE"
  }

```

### Affected Delivery Node Elements ###

An `affectedDeliveryNodes` member **MUST** contain at least the following elements:

| Element | Description |
| ------- | ----------- |
| dnId | A string indicating the delivery node ID. |

An `affectedDeliveryNodes` member **MAY** contain the following elements:

| Element | Description |
| ------- | ----------- |
| confidence | A string representing the confidence level. The default value is LOW. This value is case sensitive and must match exactly one of the following values: `LOW`, `MEDIUM`, or `HIGH`. This element is used by Notifi and is not used by Storm Center. |
| callbackContact (see **Note**) | A string representing the callback contact information such as a phone number or email. This element is used by Notifi and is not used by Storm Center. |
| reported | A boolean to determine whether the outage for the affected delivery node was reported by a customer. This element is used by Notifi and is not used by Storm Center. |

{{% notice note %}}
Notifi may not have additional data about the delivery node, such as the address, available when sending outage messages to the callback contact. This fact should be considered and tested when designing message templates.
{{% /notice %}}

## Restoration Elements ##

A `restorations` wrapper member is used to encapsulate the restoration elements. These are also referred to as explicit restorations.

{{% notice note %}}
Restoration elements are not required as part of an outage file. Currently, the Notifi solution uses restoration data to provide automated messages to customers, but Storm Center does not use restoration data.
{{% /notice %}}

A `restoration` member **MUST** contain at least the following elements:

| Element | Description |
| ------- | ----------- |
| id | A string indicating the external ID in your Outage Management System (OMS). |
| restoredDeliveryNodes | An array of `restoredDeliveryNodes` members representing the restored delivery nodes. |

A `restoration` member **MAY** contain the following elements:

| Element | Description |
| ------- | ----------- |
| restoredAt | A dateTime representing the date and time when the outage was restored in ISO-8601 format. |
| restorationConfidence | A string representing the confidence level of the restoration. The default value is LOW. This value is case sensitive and must match exactly one of the following values: `LOW`, `MEDIUM`, or `HIGH`. |
| customersRestored | The number of customers restored. |
| cause | A string representing the cause of the restoration, or a code which can be mapped to a specific string. |
| comments | A string representing comments for the outage. |
| metadata | An object to support custom data. This can include custom properties to be displayed with the outage that are not represented in the other elements of the `outage` member. Supported data types for metadata objects are string, number, percentage, datetime, and HTML markup. |

### Restored Delivery Node Elements ###

A `restoredDeliveryNodes` member **MUST** contain at least the following elements:

| Element | Description |
| ------- | ----------- |
| dnId | A string indicating the delivery node ID. |

A `restoredDeliveryNodes` member **MAY** contain the following elements:

| Element | Description |
| ------- | ----------- |
| confidence | A string representing the confidence level. The default value is LOW. This value is case sensitive and must match exactly one of the following values: `LOW`, `MEDIUM`, or `HIGH`. |
| callbackContact | A string representing the callback contact information such as a phone number or email. |
| reported | A boolean to determine whether the outage for the affected delivery node was reported by a customer. |

## Cancellation Elements ##

A `cancellations` wrapper member is used to encapsulate the cancellation elements.

{{% notice note %}}
Cancellation elements are used by Notifi to differentiate cancelled outages from restorations to determine the correct message to send to affected customers. Storm Center does not use cancellation data.
{{% /notice %}}

A `cancellation` member **MUST** contain at least the following elements:

| Element | Description |
| ------- | ----------- |
| id | A string indicating the external ID in your Outage Management System (OMS). |
| cancelledDeliveryNodes | An array of `cancelledDeliveryNodes` members representing the delivery nodes affected by the cancelled outage. |

A `cancellation` member **MAY** contain the following elements:

| Element | Description |
| ------- | ----------- |
| metadata | An object to support custom data. This can include custom properties to be displayed with the outage that are not represented in the other elements of the `outage` member. Supported data types for metadata objects are string, number, percentage, datetime, and HTML markup. |

### Cancelled Delivery Node Elements ###

A `cancelledDeliveryNodes` member **MUST** contain at least the following elements:

| Element | Description |
| ------- | ----------- |
| dnId | A string indicating the delivery node ID. |

A `cancelledDeliveryNodes` member **MAY** contain the following elements:

| Element | Description |
| ------- | ----------- |
| confidence | A string representing the confidence level. The default value is LOW. This value is case sensitive and must match exactly one of the following values: `LOW`, `MEDIUM`, or `HIGH`. |
| callbackContact | A string representing the callback contact information such as a phone number or email. |
| reported | A boolean to determine whether the outage for the affected delivery node was reported by a customer. |

## Delivery Node Associated with Multiple Outages ##

If a delivery node ID is included in an outage file as an affected delivery node for more than one outage, the outage file will be processed without errors. The number of customers affected for individual outage location icon information panels will include all affected delivery nodes. The number of customers affected for cluster icon information panels, outage summary reports, and the outage summary information in the overview panel will include only distinct (non-duplicate) delivery nodes.

## Failure Scenarios ##

Complete and partial outage file processing failures are described on the [Data Feed Processing Failures page](/shared-file-specifications/failure-types/#outage-files).

## Compression ##

{{<extlink title="GZip" url="https://www.gnu.org/software/gzip/">}} file compression is supported for all file types. All GZip compressed files should end with .gz, such as `outages_20180101123045.json.gz`.
