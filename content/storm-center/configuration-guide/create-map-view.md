---
title: "Create and Deploy a Map"
weight: 21
---

## Create a Map ##

The Instance Manager refers to an individual outage map as a "view." Each map view will have its own URL, and can contain different types of outage information or use different settings depending on the intended audience for the map. For example, employees may need access to more information than customers.

To create a new map view, click the **Create New View** button on the Instance Dashboard.

### General Information ###

Use the **General** section of the Create New View form to identify the map.

1. Enter a name for the map/view - this is how you will identify the map in other areas of the Instance Manager.
1. Select a default language for the map from the drop-down - options are determined by the languages selected for the instance.
1. If you want to have the map language change to match the user's browser preferences when possible, select the **Use User Locale?** checkbox.
1. Select a time zone for the map from the drop-down.
1. Select a country for the map from the drop-down - currently, options are U.S. and Canada. This setting is used to restrict address search results to avoid presenting irrelevant locations to users of the map.
1. If you want to use Google Analytics Universal (GAU) to track activity on the map, you can provide up to three GAU tracking codes. If you want to use more than one GAU account, you can enter multiple tracking codes. KUBRA has two tracking codes entered by default that cannot be changed, but does not provide individual organizations with access to these tracking codes. For more information about Storm Center analytics, see the [Google Analytics Universal page](/storm-center/analytics/google-analytics-universal).
1. If you want to use Google Analytics 4 (GA4) to track activity on the map, you can provide up to three GA4 measurement IDs. If you want to use more than one GA4 account, you can enter multiple measurement IDs. KUBRA has a two measurement IDs entered by default that cannot be changed, but does not provide individual organizations with access to this measurement ID. For more information about Storm Center analytics, see the [Google Analytics 4 page](/storm-center/analytics/google-analytics-4).
1. If you are implementing a full-screen map web page and using a CNAME record for the web page URL, enter a page title for all languages supported by the map and provide a path URL for the favicon image you want to use. A path URL is generated when you use Image Resource Manager to upload your favicon. The page title and favicon appear in the browser tab when a user opens the map web page.
1. Set an access restriction policy for the map. The options in this drop-down are created in the Access Restriction section of the instance dashboard.

#### Time Zone ####

Outage maps include times that indicate when the information on the map was last updated, when an outage started, and when an outage is estimated to be restored. To ensure these times are presented consistently, you can select either a set time zone for the map, such as Eastern or Mountain, or the "User Locale." If you select "User Locale" as the time zone for the map, Storm Center will adjust times on the map to match the locale setting from each user's web browser.

### Map Configuration ###

Use the **Map** section of the Create New View form to select settings related to the background map.

1. Select a map API to use for the background map - currently, the only option is Google Maps.
1. Provide API credentials. KUBRA's Google Maps API credentials are entered by default. If you have a different license for Google Maps that you want to use, enter that license's API credentials.
1. Select the background map types you want to allow for the map from the drop-down - options are Road, Satellite, and Hybrid (satellite with roads and landmarks labeled). The options you select will be available to users of the map as a selector in the lower right corner of the map for changing the background map.
1. Select a background map type to use when the map page loads. This is the Start Type.

#### Zoom Level Settings ####

Zoom levels are provided by the Google Maps API as integers between 0 and 21, where 0 shows the entire world and 21 shows streets and individual buildings. You can read more about how zoom levels work in the {{<extlink title="Google Maps API developer documentation" url="https://developers.google.com/maps/documentation/maps-static/dev-guide#Zoomlevels">}}. Storm Center allows you to set minimum and maximum zoom levels and to specify the starting zoom level used when the map page loads.

1. Enter a minimum zoom level for the map - this is the lowest integer zoom level that users will be able to access. Users who attempt to zoom the map out further than the minimum zoom level will be returned to a view that uses the minimum zoom level.
1. Enter a maximum zoom level for the map - this is the highest integer zoom level that users will be able to access. Users who attempt to zoom the map in closer than the maximum zoom level will be returned to a view that uses the maximum zoom level.
1. Select a starting zoom level for the map - the drop-down for this setting includes options for all integers between and including the minimum zoom level and the maximum zoom level.

{{% notice note %}}
The zoom level settings you input here should match the zoom levels for the [layer visibility configuration](/storm-center/configuration-guide/configure-layer-visibility) or configurations you will use for the map.
{{% /notice %}}

#### Latitude and Longitude Settings (Map Boundaries) ####

The **Coordinates Input** setting asks you to provide a latitude and longitude on which to center the map when the map page loads.

The **Bounding Box** setting asks you to provide latitude and longitude information for the external map boundaries. These values create an invisible box beyond which users are not allowed to navigate on the map. Users who attempt to navigate outside of this box will be returned to a view that is inside the bounding box.

### Shared Resources ###

Use the **Shared Resources** section of the Create New View form to select items from the Shared Resources connected to the Storm Center instance to include on the map.

1. Select the layer visibility configuration or configurations you want to use to provide options in the map legend. Before you can see layer visibility configurations here, you must [configure layer visibility settings](/storm-center/configuration-guide/configure-layer-visibility).
1. Select the labeling you want to use for null and expired estimated restoration times (ETRs) and, if you are using the optional Planned Outages module, end times. Before you can select a labeling here, you must [create data labels](/storm-center/configuration-guide/create-data-labels).
1. Select a set of summary information to use at the top of the overview panel. Before you can select a summary here, you must [create summaries](/storm-center/configuration-guide/create-summaries/#outage-summaries).
1. Select the outage summary report or reports you want to include in the overview panel. Before you can select outage summary reports here, you must [create summary reports](/storm-center/configuration-guide/create-summaries/#outage-summary-reports).
1. Select the design to use for the map interface. Before you can select a design here, you must [create a design](/storm-center/configuration-guide/configure-map-interface).
1. Provide verbiage to use for masking the number of customers affected by outages when it is below the value you set for a layer, summary, or summary report. For example, "Fewer than." Storm Center does not add any characters between the end of the masking verbiage and the start of the masking value, so if you want the full phrase to read as "Fewer than 20," you must add a space character at the end of the masking verbiage.
1. Provide verbiage to use for masking the percentage of customers affected by outages when it is below the value you set for a layer, summary, or summary report. This field behaves the same way as the masking verbiage for number of customers affected.

{{% notice note %}}
Masking verbiage is mandatory for number of customers affected, percentage of customers affected, or both if you have selected any masking settings for those data types in other areas of the Instance Dashboard. If you have not selected any masking settings, you do not need to provide masking verbiage here.
{{% /notice %}}

### Widgets ###

Use the **Widgets** section of the Create New View form to include Custom Layers and Service Territory boundary information on the map, to select settings for the Weather radar layer if you included Weather in the map design you selected for the map, and to show the map view selector in the map legend as either a menu or a list.

1. If you want to make Custom Layers items available to users of the map, click the **Enable Custom Layers for View?** checkbox.
1. If you want to show Custom Layers items when the map loads, click the **Show View by Default on Map Load?** checkbox.
1. If you want to make weather radar available to users of the map, you must select Weather in the [map interface design for the overview panel](/storm-center/configuration-guide/configure-map-interface/#overview-panel).
1. If you want to show weather radar when the map loads, click the **Show View by Default on Map Load?** checkbox.
1. Use the slider to select a default opacity percentage for the weather radar layer, between 0 (invisible) and 100 (fully opaque).
1. Select a Service Territory indicator to use for the map. Before you can select a service territory here, you must [create a service territory](/storm-center/configuration-guide/create-service-territory).
1. If you have multiple visibility configurations connected to the map and want to show them as a list in the map legend above the map view selector menu, click the **Show Legend as List** checkbox. If you leave this checkbox unselected, the radio buttons for multiple visibility configurations will appear inside the map view selector menu.

*Example of visibility configurations shown as a list - checkbox selected*
![Visibility Configurations as List](/images/visibility-config-list.png)

*Example of visibility configurations shown as a menu - checkbox not selected*
![Visibility Configurations as Menu](/images/visibility-config-menu.png)

## Clone a Map ##

After you have created a map view, you can click the **Clone View** button to create a second map that copies all data from the original map. This can be helpful if you want to make a new map with only a few changes from an existing map's configuration.

You can only clone a map view within the same instance. After you create or clone a map, you must deploy the instance to activate the new map URL.

## Deploy a Map ##

To deploy the map or maps you have configured, use the **Deploy Manager** section of the Instance Dashboard. Click the **Deploy** sub-section of the Deploy Manager, and then click the **Deploy!** button.

The Instance Manager will provide a status message for the deployment. If the deployment is successful, the Instance Manager will provide a URL for each map associated with the instance. You can see the map URLs in the **Manage My Views** section on the instance dashboard.

{{% notice note %}}
You will not see outage data on the map until after you submit a delivery node file and an outage file using the feeds you configured for the map.
{{% /notice %}}

Each time you update the configuration, you must re-deploy the map. After the first deployment, each new deployment of the same map will use the same URL.

You can also use the [Deploy Manager section](/storm-center/deploy-manager) of the Instance Manager to verify your instance, review the current status of your deployed instance and data feeds, and see the deployment history for your instance and for the outage and delivery node files associated with the instance.
