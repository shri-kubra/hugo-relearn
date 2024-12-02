---
title: "Storm Center File Specifications"
type: index
weight: 4
---

Storm Center uses five mandatory types of data files:

+ [**Region files**](/storm-center/file-specifications/region-file) - These files define the boundaries of an organization's service territory or region on the map. If an organization has multiple regions in its service territory, the organization can provide one region file for each region and choose whether to show multiple regions on one public-facing map or one region each on multiple public-facing maps.
+ [**Thematic files**](/storm-center/file-specifications/thematic-file) - These files define the boundaries of areas within a region, such as counties, postal codes, or cities, towns, and villages.
+ [**Delivery node files**](/storm-center/file-specifications/delivery-node-file) - These files list the locations of delivery nodes (locations with IDs in the Outage Management System or other system providing outage data) in a region and the number of customers served by each delivery node.
+ [**Outage files**](/shared-file-specifications/outage-file) - These files list outages affecting delivery nodes in a region and provide information about each outage such as an estimated restoration time, cause, comments, and repair crew status.

To set up a Storm Center instance for an organization, you must provide:

+ One or more region files, uploaded at least once and updated whenever the boundaries of the organization's region or regions change.
+ One or more thematic files, uploaded at least once and updated whenever the boundaries of any of the thematic areas change.
+ A delivery node file, uploaded periodically to keep up with changes to the number or location of the organization's delivery nodes. KUBRA requires that an organization upload an updated delivery node file no more than once per day and at least once every 90 days. One suggested schedule is provide delivery node files weekly.
+ An outage file, uploaded periodically to keep up with changes to outage information. KUBRA suggests that an organization upload an outage file every 15 minutes.

The organization using Storm Center must provide thematic files for each type of thematic, such as County, ZIP Code, or City/Town/Village (CTV).

Storm Center also supports two additional types of data file for use with the optional modules:

+ [**Planned outage files**](/shared-file-specifications/planned-outage-file) - These files list outages that have an estimated start and end time because they are planned in advance. They also provide information about each outage such as a duration, the number of customers affected, comments, and an area affected by the outage.
+ [**Additional Map Layer files**](/storm-center/file-specifications/additional-map-layer-file) - These files contain geographical features and associated data provided by clients. The features are presented on Storm Center maps with the symbology chosen by the client at the configuration phase.

For all data files, you must follow the KUBRA-provided data specifications. For example, all coordinate data must be provided according to EPSG:4326, also known as WGS84.

## Providing Data Files ##

Region files and thematic files can be provided via a direct upload to the Instance Manager interface or via HTTPS PUT request. Organizations that do not have access to the Storm Center app in Instance Manager can provide these files to KUBRA, and KUBRA will upload the files during the development phase of a Storm Center implementation project. If the organization needs to periodically update region files, thematic files, or both, KUBRA can provide the endpoints for file delivery by the appropriate user or system.

## Providing Data Feeds ##

Delivery node files, outage files, planned outage files, and additional map layer files must be delivered via HTTPS POST request. The POST requests require Basic Authentication. This is provided as the `Authorization` header value with the string value `Basic` followed by the base64-encoded username and password of a user that has access to upload files, in the format `username:password`. Each request must have the `Content-Type` `multipart/form-data`. Each file must be attached to the corresponding request as a form field of type `file`.

### (Optional) Override Spatial Scanning ###

By default, delivery nodes are placed within a thematic area and within a region based on the `latitude` and `longitude` provided for the delivery node element in the delivery node data feed. This behavior can be overridden by using references to `areaId` and to `regionCode` within the delivery node file.

To override the automatic spatial scanning for delivery nodes, you must include a unique thematic area identifier, `areaId`, in the thematic file. You must also reference the `areaId` and `areaType` in the delivery node file within the `areas` element. `areaType` is a property defined when adding the thematic in the Instance Manager user interface. For example, "county" and "zip" are area types.

If your instance includes multiple regions, you can also include a unique region identifier, `regionCode`, in the delivery node file. `regionCode` is a property defined when adding a region in the Instance Manager user interface. By default, Storm Center uses the first two alphanumeric characters of the region name entered in Instance Manager as the `regionCode` value.

If your instance includes only one region and you have some delivery nodes with coordinates outside the boundaries of that region, you can use `regionCode` to override spatial scanning and identify those delivery nodes with the region specified by the `regionCode`.

If your instance includes only one region and all of your delivery node coordinates fall within the boundaries of that region, you can omit the `regionCode` and Storm Center will identify all delivery nodes with the single region for the instance using spatial scanning.

{{% notice note %}}
Values for `regionCode` and `areaType` are case sensitive. All references to these elements in delivery node files must match the case used in region and thematic files and in the Instance Manager user interface.
{{% /notice %}}

## Assumptions ##

KUBRA makes the following assumptions about data files used for Storm Center maps.

1. Geometry boundaries in a region file do not overlap. If any of the provided geometry boundaries in a region file overlap, KUBRA will fail the entire region file.
2. The organization providing thematic files has validated all thematic areas to be within or intersecting the region defined in the region file.
3. KUBRA is not responsible for ensuring that areas provided in thematic files match the boundaries of a specific region.
4. Thematic areas share borders but do not overlap. KUBRA will provide verification of thematic areas and fail the entire thematic file if it contains overlapping thematic areas.
5. If thematic areas exist in a hierarchy (such as towns within counties), the organization providing thematic files will give KUBRA a description of this hierarchy to configure the Storm Center map appropriately.
6. Delivery nodes are validated to be within the boundary formed by the region provided in the region file. They are also validated to be within a specific thematic area polygon or multi-polygon shape provided in the thematic files. Alternatively, the delivery node file can specify a region and one or more thematic areas for each delivery node. Details for this option are included in the region file, thematic file, and delivery node file specifications.

## Failures ##

More information about [data feed file processing failures](/shared-file-specifications/failure-types).
