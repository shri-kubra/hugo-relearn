+++
title = 'IncidentWatch File Specifications'
type = ''
weight = 4
+++

IncidentWatch uses data feeds for asset data. [**Asset files**](/incidentwatch/file-specifications/asset-file) define the locations and properties of the assets to be displayed on the IncidentWatch map.

KUBRA recommends providing asset files at least once per week and no more than once per day.

## Providing Data Feeds

Asset files must be delivered via HTTPS POST request. The POST requests require Basic Authentication. This is provided as the `Authentication` header value with the string value `Basic` followed by the base64-encoded username and password of a user that has access to upload files, in the format `username:password`.

Additional information about the endpoints for asset files is provided on the pages for the file type.

## Assumptions

KUBRA makes the following assumptions about data files used for IncidentWatch.

1. The latitude and longitude coordinates provided in the asset file represent asset locations.
1. All records included in an asset file represent asset data.
1. The asset properties to be included in the metadata element are defined as part of an implementation project and will not be changed without notification to and agreement from KUBRA.
1. Any data issues will be resolved by the Organization - KUBRA will not modify asset files.
