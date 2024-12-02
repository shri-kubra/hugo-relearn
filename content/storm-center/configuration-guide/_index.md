---
title: "Configuration Guide"
type: index
weight: 11
---

## Instance Manager Overview ##

The Instance Manager is the interface that allows you to create Storm Center instances, set up data files and feeds, and configure maps.

{{% notice note %}}
[Image Resource Manager](/shared-file-specifications/image-resource-manager) now allows users to upload icons, brand images, social media images, and any other image assets that the client requires for their logos, any social media icons, or within content blocks. These icons and image assets can also be used to customize thematic layers, planned outage layers, and additional map layers.
{{% /notice %}}

## Access the Instance Manager ##

1. Navigate to the Instance Manager website.
1. Sign in using Google or other single sign-on credentials.
1. Choose a tenant.
    + This option is only presented if you have access to more than one tenant.
1. Choose the Storm Center option from the application list.
    + This option is only presented if you have access permissions for more than one application.

In the Storm Center application, you will see sections on the left side of the screen for

+ **Instances** - Shows a list of the Storm Center instances created for your account and an option to create a new instance. Click on an instance name to access that instance's dashboard.
+ **Shared Resources** - Shows a list of the Region and Thematic files associated with your tenant account.
  + **Regions** - Allows you to add one or more region files, shows a list of region files associated with your tenant account, and shows a list of instances using specific region files.
  + **Thematics** - Allows you to add one or more thematic files and shows a list of thematic files associated with your tenant account.

## Create an Instance ##

To create a new map instance, click the **Create Instance** button at the bottom of the list of instances.

1. Enter a name for the instance.
1. If you want to prioritize data processing and monitoring for this instance over your other instances, click the **Critical Instance** checkbox.
    + Critical instances are excluded from new feature preview releases. KUBRA recommends that each tenant account have only one critical instance. The critical instance will usually be the instance used for "production" maps.
1. Select the language or languages to be used on the maps for the instance - the available options are English (American) (EN-US), French (Canadian) (fr-CA), and Spanish (Castilian) (ES-ES) or US Spanish (American) (es-US).
1. If you want to upload a configuration file for the instance, click the **Upload Config File?** checkbox and then upload a JSON file with configuration data for the instance. For example, you can use this option to copy configuration settings from one instance to another instance.
1. Click the **Submit** button.

{{% notice note %}}
When selecting Spanish as the language, you can only select either Castilian or American. Castilian Spanish: Numbers have thousands indicated with periods and decimals with commas. Time is shown in 24h notation.
American Spanish: Numbers have thousands indicated with commas and decimals with periods. Times is shown in 12h notation with AM and PM suffixes.
{{% /notice %}}

## Set Up Data Files ##

1. Set up one or more region files.
1. Set up one or more thematic files.
1. Use the Data Feeds application to set up an outage data feed.
1. Use the Data Feeds application to set up a delivery node data feed.
1. (Optional) Use the Data Feeds application to set up a planned outage data feed.
1. (Optional) Use the Data Feeds application to set up an additional map layer data feed.
1. Use the Sources section of the instance dashboard to connect data files and feeds as sources for an instance.

[More info on how to connect data files](/storm-center/configuration-guide/connect-data-files)

## Manage an Instance ##

The **Instances** section of the Storm Center application shows a list of the Storm Center instances for your account. To manage information for a specific instance, click an instance name from this list. This opens the Instance Dashboard.

The Instance Dashboard includes sections for

+ **Sources** - select data feeds and data files to connect to the instance.
+ **Shared Resources** - configure data layers, service territories, summary information, summary reports, buttons and content blocks, map designs, data labels for some null and expired values, outage data mapping, and layer visibility for maps associated with the instance.
+ **Deploy Manager** - the [Deploy Manager tools](/storm-center/deploy-manager) to deploy the instance, verify the instance, view the current deployment status of the instance, and view the deployment history for the instance including processing of outage, delivery node, and additional map layer files.
+ **Control Center** - the [Control Center](/storm-center/management-console) includes apps to create and deploy map alert banners, enter a redirect URL, change the update wording on the map, change the map between blue-sky mode and storm mode, manage custom layers areas and icons, and manage overwritten values for customers affected and/or ETR data on the map, as well as admin tools to configure custom layers and the app for managing overwritten outage data.
+ **Edit Instance** - edit the instance name, change whether the instance is a critical instance, select the available languages for the instance, or delete the instance.
+ **Access Restriction** - create and manage access restriction policies to be applied to shared resources and maps.
+ **Manage My Views** - a list of maps associated with the instance that allows you to edit, delete, create, and clone maps.

### Create Access Restriction Policies ###

In the **Access Restriction** section of the Instance Dashboard, you can create access restriction policies that you can apply to outage layers, additional map layers, summary data, outage summary reports, and maps.

To create a new access restriction policy, click the **Create a Restriction Policy** button in the Access Restriction section.

1. Enter a name for the access restriction policy - this name is how you will identify the access restriction policy in other areas of the Instance Manager.
1. If you want the policy to allow anonymous access, click the **Allow Anonymous Access** checkbox. This will create a policy that allows access by anyone without authentication.
1. If you want the policy to limit access to one or more groups, select the group or groups from the **Select Group(s)** drop-down.
1. To save the policy, click the **Submit** button. To discard your changes without saving, click the **Cancel** button.

The Access Restriction page shows a list of existing access restriction policies associated with the instance, a list of groups included in each policy, and a Boolean for whether the policy allows anonymous access. Anonymous access policies do not include a list of groups.

To edit or delete an existing access restriction policy, click the policy name in the list of policies.

For more information about user management and the user permission groups, see [User Management](/storm-center/management-console/user-management).

### Configure Shared Resources for Map Views ###

To set up resources that can be shared by multiple maps, use the **Shared Resources** section of the Instance Dashboard.

1. Set up [outage data layers](/storm-center/configuration-guide/create-outage-layers). There are four types of data layers:
    + Thematic - a layer that shows outages by areas defined in a thematic file such as counties, ZIP codes, or cities/towns/villages.
    + Outages - a layer that shows active outage locations and clusters of outage locations.
    + Planned - a layer that shows planned outage locations and clusters of planned outage locations. Only available with the Planned Outages module.
    + AML - a layer that shows additional data like hazards, gas outages, flooding etc. on Storm Center maps. Only available with the Additional Map Layer module.
1. Set up a [service territory boundary](/storm-center/configuration-guide/create-service-territory) defined by one or more region files.
1. Set up [outage summaries](/storm-center/configuration-guide/create-summaries) - the data shown at the top of the overview panel.
1. Set up [outage summary reports](/storm-center/configuration-guide/create-summaries/#outage-summary-reports) - tabular representations of outage information by areas defined in a thematic file.
1. Set up [configurable buttons and content blocks](/storm-center/configuration-guide/create-buttons) to provide buttons, content blocks, or both. Buttons can appear in the map header, the overview panel, the help panel, or information panels depending on their type. Content blocks can appear in the overview panel, the help panel, information panels, or summary reports.
1. Configure [map UI design](/storm-center/configuration-guide/configure-map-interface) - the background colors, font colors, logo, and configurable buttons and content blocks used for a map.
1. Set up [data labels](/storm-center/configuration-guide/create-data-labels) for null and expired restoration time values.
1. Set up [data mapping](/storm-center/configuration-guide/create-data-labels/#outage-data-mapping) for crew status, outage cause, or metadata outage data values.
1. Configure [layer visibility](/storm-center/configuration-guide/configure-layer-visibility) - visibility configurations and options control how outage data layers are shown to users as map view choices in the map legend, including the zoom levels and labels for each map view choice.

### Create a New Map ###

To create a new map, click the **Create New View** button on the Instance Dashboard.

1. Set general configurations.
1. Set map parameters.
1. Choose resources from shared resources.
1. Select widgets settings: options are custom layers, weather radar, service territory boundary, and legend.

[More info on how to create a map](/storm-center/configuration-guide/create-map-view)

### Deploy an Instance ###

To deploy an instance, use the **Deploy Manager** section of the Instance Dashboard.

1. Select the **Deploy** section of the Deploy Manager dashboard.
1. Click the **Deploy** button.

{{% notice note %}}
You will not see outage data on the map or maps associated with the instance until after you submit a delivery node file and an outage file using the feeds configured for the instance.
{{% /notice %}}

You can also use the **Deploy Manager** section of the Instance Manager to review the current status of the instance and the deployment history for the instance and for the delivery node and outage files associated with the instance.

Each time you update the configuration, you must re-deploy the instance. The **Status** section of the instance dashboard will indicate when the instance needs to be redeployed and how many changes have been made to the instance configuration.

## Embed a Map in a Website ##

You can include a map in an existing website as a full-screen web page or as part of a web page using an iframe or using a div element. To embed a full-screen map web page in an existing website, you must provide KUBRA with a CNAME certificate for the desired page URL. To embed a map as part of an existing web page using an iframe or a div element, you must include HTML to indicate the size and position of the element containing the map. For the map to scale appropriately based on browser window size, the web page containing the iframe or div element needs to be responsive.

[More info on how to embed a map](/storm-center/configuration-guide/embed-map-view)

## Review Map History (Optional) ##

If the organization has purchased the optional Map History module, authorized users can configure the Map History Viewer and use it to review historical outage data generated by the Storm Center application.

[More info on map history](/storm-center/map-history)
