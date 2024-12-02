---
title: "Data Feed Processing Failures"
weight: 10
---

There are two types of file processing failures for delivery node, outage, and planned outage data feeds:

1. **Critical**: Fatal; processing aborts and the entire file fails.
2. **Non-critical**: Non-fatal; processing continues, but some or all of the affected entry may be discarded, the resulting outage data may be incorrect, etc.

The following are the critical and non-critical failures that can occur when processing delivery node, outage, and planned outage files.

## Delivery Node Files ##

### 1. Critical (Complete File Failure) ###

#### 1.1. Bad syntax ####

Files that do not adhere to the file format specification (JSON, JSON Lines, or XML) will result in a fatal error. The data cannot be processed and the file will fail.

Zero byte files are considered an invalid format and will not be processed.

#### 1.2. Empty `nodes` array or all nodes filtered ####

If there are no valid delivery nodes included in a file, or if all delivery nodes in a file are filtered, the file will fail and the error will be logged. Delivery nodes are filtered from a file when any of the following is true:

+ the delivery node's coordinates are outside the region
+ the delivery node's coordinates are outside one or more of the thematic areas for the thematic selected to be used for filtering delivery nodes
+ one or more of the delivery node's `areaId` values do not match any of the values for `areaId` provided in the corresponding thematic file
+ the delivery node's `regionCode` does not match any of the values for `regionCode` entered in the Instance Manager interface

#### 1.3. Internal processing error ####

Internal errors with the Storm Center platform, such as hardware limitations, hardware failures, etc. This is a fatal error and the file will fail.

#### 1.4. Missing , empty, or null `id` field ####

This is a required field. If any delivery nodes are missing the `id` field, the field is empty, or the field value is null, the file will fail.

#### 1.5. Duplicate `id` field ####

This is a required field. ID values must be unique. If duplicate delivery node IDs exist, the file will fail.

#### 1.6. Invalid `customersServed` field ####

This is an optional field. If present, for values other than non-negative integers, the file will fail.

#### 1.7. Missing, empty, or null `latitude` and/or `longitude` fields ####

Coordinates are required. If any delivery node's `latitude` and/or `longitude` value is missing, empty, or null, the file will fail and the delivery nodes with errors will be logged.

#### 1.8. Invalid `latitude` and/or `longitude` fields ####

If any delivery node's coordinates do not adhere to the {{<extlink title="WGS84/EPSG:4326 coordinate system" url="https://spatialreference.org/ref/epsg/wgs-84/">}} or the coordinates are not formatted as Decimal Degrees, the file will fail and the delivery node or delivery nodes with errors will be logged. A latitude value outside of -90 to 90 inclusive, a longitude value outside of -180 to 180 inclusive, or a value for either latitude or longitude that includes alphabetic characters is invalid. For example, latitude values of `-95`, `-90.02`, `92`, and `103` are invalid, and longitude values of `-200`, `-180.773`, `182`, and `3000` are invalid.

### 2. Non-critical (Partial File Failure) ###

#### 2.1. Coordinates outside of region or regions ####

Delivery nodes with coordinates that are outside of the defined region or regions will be discarded.

#### 2.2. Coordinates outside of thematic or thematics ####

Delivery nodes with coordinates that are outside one or more (depending on the configuration) of the thematic areas for the thematic selected to be used for filtering delivery nodes will be discarded.

#### 2.3. Invalid `areaId` for the `areaType` used to filter delivery nodes ####

Delivery nodes with a specified `areaId` for the `areaType` selected to be used for filtering delivery nodes that does not match any of the values for `areaId` provided in the corresponding thematic file will be discarded.

#### 2.4. Invalid `regionCode` ####

Delivery nodes with a specified `regionCode` that does not match any of the values for `regionCode` entered in the Instance Manager interface when uploading a region file will be discarded.

## Outage Files ##

### 1.  Critical (Complete File Failure) ###

#### 1.1. Bad syntax ####

Files that do not adhere to the file format specification (JSON or XML) will result in a fatal error. The data cannot be processed and the file will fail.

Zero byte files are considered an invalid format. At a minimum, an outage file must contain an empty `outages` array.

#### 1.2. Internal processing error ####

Internal errors with the Storm Center platform, such as hardware limitations, hardware failures, etc. This is a fatal error and the file will fail.

#### 1.3. Missing, empty, or null `id` field ####

This is a required field. If any outages have a missing `id` field or an `id` field with an empty or null value, the file will fail.

#### 1.4. Duplicate `id` field ####

This is a required field. ID values must be unique. If duplicate outage IDs exist, the file will fail.

#### 1.5. Missing or null `affectedDeliveryNodes` array ####

This is a required field. If the array of `affectedDeliveryNodes` is missing or null for one or more outages, the file will fail. An empty array is valid.

#### 1.6. Invalid `affectedDeliveryNodes` array ####

This is a required field. If any outage contains values other than an empty array or an array of `affectedDeliveryNode` elements, the file will fail.

#### 1.7. Invalid `outageConfirmed` field ####

This is an optional field. If present, for values other than `true` or `false`, the file will fail.

#### 1.8. Invalid `crewIconIndicator` field ####

This is an optional field. If present, for values other than `true` or `false`, the file will fail.

#### 1.9. Invalid `etr` field ####

This is an optional field. If present, for values other than `null` or a date and time in {{<extlink title="ISO-8601 format" url="https://www.iso.org/iso-8601-date-and-time-format.html">}}, the file will fail.

#### 1.10. Invalid `etrConfidence` field ####

This is an optional field. If present, for values other than `LOW`, `MEDIUM`, or `HIGH`, the file will fail.

#### 1.11. Invalid `startedAt` field ####

This is an optional field. If present, for values other than `null` or a date and time in {{<extlink title="ISO-8601 format" url="https://www.iso.org/iso-8601-date-and-time-format.html">}}, the file will fail.

#### 1.12. Invalid `restoredAt` field ####

This is an optional field. If present, for values other than `null` or a date and time in {{<extlink title="ISO-8601 format" url="https://www.iso.org/iso-8601-date-and-time-format.html">}}, the file will fail.

#### 1.13. Invalid `updatedAt` field ####

This is an optional field. If present, for values other than `null` or a date and time in {{<extlink title="ISO-8601 format" url="https://www.iso.org/iso-8601-date-and-time-format.html">}}, the file will fail.

#### 1.14. Missing `dnId` field in `affectedDeliveryNodes` element ####

This is a required field. If not present in an `affectedDeliveryNodes` element on one or more outages, the file will fail.

#### 1.15. Invalid `confidence` field in `affectedDeliveryNodes` element ####

This is an optional field. If present, for values other than `LOW`, `MEDIUM`, or `HIGH`, the file will fail.

#### 1.16. Invalid `reported` field in `affectedDeliveryNodes` element ####

This is an optional field.  If present, for values other than `true` or `false`,  the file will fail.

### 2. Non-critical (Partial File Failure) ###

#### 2.1. `dnId` field in `affectedDeliveryNodes` element does not match any entries from the delivery node file ####

This is a required field. The number of customers served cannot be looked up for delivery node IDs that do not match an entry in the delivery node file. This will result in the wrong number of customers affected being calculated for the associated outage, thematics, reports, and/or summary.

## Planned Outage Files ##

### 1.  Critical (Complete File Failure) ###

#### 1.1. Bad syntax ####

Files that do not adhere to the file format specification (JSON or XML) will result in a fatal error. The data cannot be processed and the file will fail.

Zero byte files are considered an invalid format. At a minimum, a planned outage file must contain an empty `plannedOutages` array.

#### 1.2. Internal processing error ####

Internal errors with the Storm Center platform, such as hardware limitations, hardware failures, etc. This is a fatal error and the file will fail.

#### 1.3. Missing, empty, or null `id` field ####

This is a required field. If any outages have a missing `id` field or an `id` field with an empty or null value, the file will fail.

#### 1.4. Duplicate `id` field ####

This is a required field. ID values must be unique. If duplicate outage IDs exist, the file will fail.

#### 1.5. Invalid `start` field ####

This is an optional field. If present, for values other than `null` or a date and time in {{<extlink title="ISO-8601 format" url="https://www.iso.org/iso-8601-date-and-time-format.html">}}, the file will fail.

#### 1.6. Invalid `end` field ####

This is an optional field. If present, for values other than `null` or a date and time in {{<extlink title="ISO-8601 format" url="https://www.iso.org/iso-8601-date-and-time-format.html">}}, the file will fail.

#### 1.7. Invalid `updatedAt` field ####

This is an optional field. If present, for values other than `null` or a date and time in {{<extlink title="ISO-8601 format" url="https://www.iso.org/iso-8601-date-and-time-format.html">}}, the file will fail.

#### 1.8. Invalid `affectedDeliveryNodes` array ####

This is an optional field. If present, if any outage contains values other than an empty array or an array of `affectedDeliveryNodes` elements, the file will fail.

#### 1.9. Missing `dnId` field in `affectedDeliveryNodes` element ####

This is a required field. If not present in an `affectedDeliveryNodes` element on one or more outages, the file will fail.

#### 1.10. Missing both `geometry` and `affectedDeliveryNodes` elements ####

Either `geometry` or `affectedDeliveryNodes` is required to locate an outage on the map. If both elements are missing on one or more outages, the file will fail.

#### 1.11. Missing both `customersAffected` and `affectedDeliveryNodes` elements ####

Either `customersAffected` or `affectedDeliveryNodes` is required to determine the number of customers affected by an outage. If both elements are missing on one or more outages, the file will fail.

### 2. Non-critical (Partial File Failure) ###

#### 2.1. Value for customers affected equals 0 ####

Outages are only displayed if they have a positive integer value for customers affected. If the value for customers affected (either calculated based on the customers served values associated with the `affectedDeliveryNodes` or provided as `customersAffected`) is equal to 0, the outage will be filtered from the planned outage file and will not be displayed on the map.

#### 2.2. `dnId` field in `affectedDeliveryNodes` element does not match any entries from the delivery node file ####

This is a required field. The number of customers served cannot be looked up for delivery node IDs that do not match an entry in the delivery node file. This will result in the wrong number of customers affected being calculated for the associated outage.
