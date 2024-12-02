---
title: "Connect Data Files and Feeds"
weight: 13
---

## Set Up Region Data ##

To upload and manage region files for your Storm Center instances, use the **Regions** sub-section under **Shared Resources** in the left navigation panel of the Instance Manager Storm Center application.

Region files represent the geographic area served by a utility company, utility operating company, or other organization. Storm Center uses region files to create service territory boundaries and to verify that the polygons in a thematic file are within or intersecting the region.

To add a new region data file:

1. Click the **Add Region** button.
1. Enter a name for the region file - this is how you will identify the region file in other areas of the Instance Manager. The region name can be 1-50 alphanumeric characters and may contain whitespace, underscore, period, and hyphen characters.
1. (Optional) Enter a region code for the region. The region code is case sensitive and can be up to 4 alphanumeric characters. You can use the region code to override spatial scanning for associating delivery nodes with a region. References to the region code in data files and feeds MUST match the case shown.
1. Upload a GeoJSON region file that adheres to the [Region File Specification](/storm-center/file-specifications/region-file).
1. Click the **Submit** button.

The application will create an ID for the region data feed after you save a new region name. This ID will be part of the HTTPS URL you can use to provide updated region files as needed.

To edit, update, or delete a region file, click on the region file name in the list under the **Add Region** button.

{{% notice note %}}
You cannot delete a region file that is being used by an instance.
{{% /notice %}}

The Edit Region screen includes the region name, the region code, a region history list, a tool to manually upload a new region file, and the HTTPS URL for the region file endpoint. The region history list shows the date, time, region name, and region code for each file upload. The region history list also includes a button to download a copy of a specific region file and the user code for the user who uploaded the region file.

The **Instances Using Regions** list on the Region Management screen shows the names of the instances for the tenant account and the name of the region file connected to each instance in the format "instance name : region file name."

## Set Up Thematic Data ##

To upload and manage thematic files for your Storm Center instances, use the **Thematics** sub-section under **Shared Resources**  in the left navigation panel of the Instance Manager Storm Center application.

Thematic files represent geographic areas within a region, such as counties, ZIP codes or other postal codes, or City/Town/Village (CTV) areas. Storm Center uses thematic files to create summary reports of outage information and to visually represent the number of outages by area. Storm Center also uses thematic files to validate the locations of delivery nodes from delivery node files.

To add a new thematic data file:
1. Click the **Add Thematic** button.
1. Enter a name for the thematic file - this is how you will identify the thematic file in other areas of the Instance Manager. The thematic name can be 1-50 alphanumeric characters and may contain whitespace, underscore, period, and hyphen characters.
1. Select the area type.
    + The default options are "zip" for ZIP code, "county" for county, and "ctv" for City/Town/Village areas.
    + If you select "CUSTOM," you must provide a name for the custom area type. Each Custom area type you enter will be available in the drop-down for any additional thematic files you set up for your instance.
    + Area type values are case-sensitive and must be 15 characters or less. The values in the drop-down will match the case used for the original entry. References to area type in individual thematic files and delivery node files MUST match the case shown.
1. If applicable, provide the hierarchy for the thematic.
    + The item or items you list in the hierarchy field must match the labels for the data you provide in the thematic file. You only need to list hierarchy levels which are higher than the level of the thematic type. For example, you can list "state" as a hierarchy level above "county" for a county thematic. The area type values included in the hierarchy are case sensitive. References to hierarchy values in thematic files and delivery node files MUST match the case shown.
1. Upload a GeoJSON thematic file that adheres to the [Thematic File Specification](/storm-center/file-specifications/thematic-file).
1. Click the **Submit** button.

Repeat this process for each type of thematic you want to use for the map.

The application will create an ID for the thematic data feed after you save a new thematic name. This ID will be part of the HTTPS URL you can use to provide updated thematic files as needed.

To edit, update, or delete a thematic, click on the thematic name in the list under the **Add Thematic** button.

{{% notice note %}}
You cannot delete a thematic file that is being used by an instance.
{{% /notice %}}

The Edit Thematic screen includes the thematic name, the area type, the hierarchy, a thematic history list, a tool to manually upload a new thematic file, and the HTTPS URL for the thematic file endpoint. The thematic history list shows the date, time, thematic name, and hierarchy for each file upload. The thematic history list also includes a button to download a copy of a specific thematic file and the user code for the user who uploaded the thematic file.

{{% notice note %}}
You cannot change the area type of a thematic file after it is created.
{{% /notice %}}

## Set Up Outage and Delivery Node Data Feeds ##

To identify and test data feeds for outage and delivery node files, use the **Data Feeds** application.

If your instance includes the optional Planned Outages module, you can also use the Data Feeds application to set up and test a data feed for planned outage files.

### Outage Feeds ###

Outage files provide information about outages and the delivery nodes they affect. Storm Center uses outage files to create information panels for outage locations and outages by area, and to determine the location of outages by comparing data in outage files to data in delivery node files.

To manage outage data feeds, use the Outage Feeds Dashboard section of the Data Feeds application.

To set up a new outage feed:

1. Click the **Create Outage Feed** button.
1. Enter a name for the outage feed - this is how you will identify the outage feed in the Instance Manager application.
1. To save the outage feed name, click the **Submit** button.

The Data Feeds application will create an ID for the outage feed after you save a new outage feed name. This ID will be part of the HTTPS URL you use to provide outage files.

You can decide how often to provide new outage files based on how often you want to update the map views connected to the Storm Center instance. KUBRA recommends sending outage files every 15 minutes as a default.

To edit the name of an outage feed or to delete an outage feed, click the name of the feed in the **Outage Feeds** list on the Outage Feeds Dashboard. The screen that opens when you select an outage feed name also shows the HTTPS endpoint for the outage feed.

{{% notice note %}}
You cannot delete an outage feed that is being used by an instance.
{{% /notice %}}

To manually test outage data files for an outage feed, click the **Upload Outage File** button.

1. Select an outage feed name from the drop-down list.
1. Upload an outage file that adheres to the [Outage File Specification](/shared-file-specifications/outage-file).
1. Click the **Upload** button.

This manual upload will also trigger a file processing job if there are instances connected to the outage feed.

### Delivery Node Feeds ###

Delivery node files provide information about the geographic location of delivery nodes and the number of customers served by each delivery node. Storm Center uses delivery node files to determine the locations of outages and the number of customers affected by each outage by comparing data in outage files to data in delivery node files.

To manage delivery node feeds, use the Delivery Node Feeds Dashboard section of the Data Feeds application.

To set up a new delivery node feed:

1. Click the **Create Delivery Node Feed** button.
1. Enter a name for the delivery node feed - this is how you will identify the delivery node feed in the Instance Manager application.
1. To save the delivery node feed name, click the **Submit** button.

The Data Feeds application will create an ID for the delivery node feed after you save a new delivery node feed name. This ID will be part of the HTTPS URL you use to provide delivery node files.

You should provide a new delivery node file whenever information about the delivery nodes changes.

To edit the name of a delivery node feed or to delete a delivery node feed, click the name of the feed in the **Delivery Node Feeds** list on the Delivery Node Feeds Dashboard. The screen that opens when you select a delivery node feed name also lists the HTTPS endpoint for the delivery node feed.

{{% notice note %}}
You cannot delete a delivery node feed that is being used by an instance.
{{% /notice %}}

To manually test delivery node files for a delivery node feed, click the **Upload Delivery Node File** button.

1. Select a delivery node feed name from the drop-down list.
1. Upload a delivery node file that adheres to the [Delivery Node File Specification](/storm-center/file-specifications/delivery-node-file).
1. Click the **Upload** button.

This manual upload will also trigger a file processing job if there are instances connected to the delivery node feed.

### (Optional) Planned Outage Feeds ###

{{% notice note %}}
The Storm Center Planned Outages module is required to provide access to planned outage data feeds.
{{% /notice %}}

Planned outage files provide information about planned outages and the delivery nodes or geographical area they affect. Storm Center uses planned outage files to create information panels for planned outage data layers and to determine the location of planned outage icons on the map.

To manage planned outage data feeds, use the Planned Outage Feeds Dashboard section of the Data Feeds application.

To set up a new planned outage feed:

1. Click the **Create Planned Outage Feed** button.
2. Enter a name for the planned outage feed - this is how you will identify the planned outage feed in the Instance Manager application.
3. To save the planned outage feed name, click the **Submit** button.

The Data Feeds application will create an ID for the planned outage data feed after you save a new planned outage feed name. This ID will be part of the HTTPS URL you use to provide planned outage files.

You can decide how often to provide new planned outage files based on how often you want to update the map views connected to the Storm Center instance that include planned outage data. You should provide a new planned outage file whenever information about a planned outage changes.

To edit the name of a planned outage feed or to delete a planned outage feed, click the name of the feed in the **Planned Outage Feeds** list on the Planned Outage Feeds Dashboard. The screen that opens when you select a planned outage feed name also lists the HTTPS endpoint for the planned outage feed.

{{% notice note %}}
You cannot delete a planned outage feed that is being used by an instance.
{{% /notice %}}

To manually test planned outage files for a planned outage feed, click the **Upload Planned Outage File** button.

1. Select a planned outage feed name from the drop-down list.
2. Upload a planned outage file that adheres to the [Planned Outage File Specification](/storm-center/file-specifications/planned-outage-file).
3. Click the **Upload** button.

This manual upload will also trigger a file processing job if there are instances connected to the planned outage feed.

### (Optional) Additional Map Layer Feeds ###

{{% notice note %}}
The Storm Center Additional Map Layer module is required to provide access to Additional Map Layer data feeds.
{{% /notice %}}

Additional Map Layer (AML) files provide non-outage data that clients might want to display on the map. Storm Center also uses AML files to create information panels for Additional Map layers.

To manage AML data feeds, use the Additional Map Layer Feeds Dashboard section of the Data Feeds application.

To set up a new Additional Map Layer feed:

1. Click the **Create Additional Map Layer Feed** button.
2. Enter a name for the Additional Map Layer feed - this is how you will identify the AML feed in the Instance Manager application.
3. To save the Additional Map Layer feed name, click the **Submit** button.

The Data Feeds application will create an ID for the AML data feed after you save a new AML feed name. This ID will be part of the HTTPS URL you use to provide AML files.

You can decide how often to provide new AML files based on how often you want to update the map views connected to the Storm Center instance that include AML data. You should provide a new AML file whenever information you want customers to know about changes.

To edit the name of an AML feed or to delete an AML feed, click the name of the feed in the **Additional Map Layer Feeds** list on the Additional Map Layer Feeds Dashboard. The screen that opens when you select an AML feed name also lists the HTTPS endpoint for the AML feed.

{{% notice note %}}
You cannot delete an Additional Map Layer feed that is being used by an instance.
{{% /notice %}}

To manually test AML files for an AML feed, click the **Upload Additional Map Layer File** button.

1. Select an Additional Map Layer feed name from the drop-down list.
2. Upload an AML file that adheres to the [Additional Map Layer File Specification](/storm-center/file-specifications/additional-map-layer-file).
3. Click the **Upload** button.

This manual upload will also trigger a file processing job if there are instances connected to the Additional Map Layer feed.

## Connect Data Files as Sources for a Map Instance ##

To manage the data files connected to a Storm Center instance, click on the name of the instance in the **Instances** section of the Instance Manager Storm Center application and then use the **Sources** section of the Instance Dashboard.

1. Select a delivery node feed.
2. Select an outage feed.
3. (Optional) Select a planned outage feed.
4. (Optional) Select an Additional Map Layer feed.
4. Select a region file.
5. Select a thematic file.
6. You must choose at least one thematic to filter delivery nodes. This allows the Storm Center map to verify that delivery node locations from the delivery node feed are within the boundaries of the region and a thematic area from the thematic file. To filter delivery nodes using the data from the selected thematic, click the **Filter Delivery Nodes** checkbox.
7. To add the selected thematic, click the **Add Thematic** button.
8. Repeat steps 5-7 for each thematic you want to include for the selected region.
9. To add the selected region and thematics to the instance, click the **Add Region + Selected Thematics** button.
10. Repeat steps 4-9 for each region you want to include.
11. Click the **Submit** button to save the data file configuration.

{{% notice note %}}
If you need to change the region feed connected to your instance, or if you need to add a new thematic file or change the thematic files connected to your instance, you must remove and re-add both the region file and all thematic files.
{{% /notice %}}
