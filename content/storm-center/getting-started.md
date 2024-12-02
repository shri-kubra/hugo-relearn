---
title: "Getting Started"
weight: 3
---

Storm Center relies on four mandatory types of data files and one optional type of data file to present outage information on an interactive map. The Instance Manager interface allows authorized users to set up data files and feeds for Storm Center instances and to manage configurable features and maps related to an organization's instances.

## Data Files ##

+ **Region files** - These files define the boundaries of an organization's service territory or region on the map. If an organization has multiple regions in its service territory, the organization can provide one region file for each region and choose to show either multiple regions on one public-facing map or one region each on multiple public-facing maps.
+ **Thematic files** - These files define the boundaries of geographical areas within a region, such as counties, postal codes, or cities, towns, and villages.
+ **Delivery node files** - These files list the locations of delivery nodes in a region and the number of customers served by each delivery node. "Delivery node" refers to a location with a unique ID in the Outage Management System or other source of outage data.
+ **Outage files** - These files list outages affecting delivery nodes in a region and provide information about each outage such as an estimated restoration time, cause, comments, and repair crew status.
+ **Planned outage files (optional, requires Planned Outages module)** - These files list outages that are planned to take place at a specific point in time and provide information about each outage such as an estimated start and end time, number of customers affected, and comments.
+ **Additional map layer files (optional, requires Additional Map Layer module)** - These files includes additional data like hazards, gas outages, flooding etc. that clients want to convey to their customers.  

See the [Storm Center File Specifications](/storm-center/file-specifications) for more information about the data files used by Storm Center.

### Data File Upload ###

Initial Region files and Thematic files must be uploaded directly using the Instance Manager interface. Updated Region files and Thematic files can be uploaded directly using the Instance Manager interface, or they can be delivered via HTTPS PUT requests.

Outage files, Delivery Node files, Planned Outage files, and Additional Map Layer files must be delivered via HTTPS POST requests.

The POST requests require Basic Authentication. This is provided as the `Authorization` header value with the string value `Basic` followed by the base64-encoded username and password of a user that has access to upload files, in the format `username:password`. Each request must have the `Content-Type` `multipart/form-data`. Each file must be attached to the corresponding request as a form field of type `file`.

KUBRA will provide the endpoints for data file delivery, as well as usernames and passwords for authentication to the endpoints, during the development phase of a Storm Center implementation project.

## Instance Manager ##

1. Navigate to the Instance Manager website.
1. Sign in using Google or other single sign-on credentials.
1. Choose a tenant. This option is only presented if you have access to more than one tenant.
1. Choose an application. This option is only presented if you have access to more than one application.

In the Storm Center application, KUBRA recommends a default setup with three instances: Sandbox, Test, and Production. The Sandbox instance can be used to develop new maps with different data feeds or configurations than the Test and Production instances. The Test instance can be used for initial setup and for testing changes before applying them to Production. The Production instance can be the only instance with maps accessible to customers or other end-users.

You can create different maps for audiences such as customers, employees, and local stakeholders in each of your instances and manage settings for each map separately. For example, you can create an "external" map available to the public that includes the types of information customers are most likely to find helpful, as well as an "internal" map with access restricted to authorized employees that includes additional information such as outage ID numbers and internal comments.

The Instance Manager Storm Center application includes tools for

+ Creating a new instance
+ Editing instance settings
+ Adding region files
+ Adding thematic files
+ Specifying a set of data sources for an instance - region, thematic, delivery node, outage data, and additional map layer data
+ Configuring resources that can be shared by multiple maps
+ Creating a map and setting map-specific configurations
+ Deploying maps and managing deployed maps
+ Managing admin features for deployed maps
+ Managing access restriction policies

The Instance Manager also includes a Data Feeds application for connecting file feeds for delivery node files, outage files, planned outage files, and additional map layer files to a Storm Center instance, and forms for creating user accounts and managing user accounts for Instance Manager.

See the [Configuration Guide](/storm-center/configuration-guide) for more information on how to use the Instance Manager to set up and manage Storm Center instances and maps.
