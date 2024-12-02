---
title: "Map Feature List"
weight: 2
---

{{% notice info %}}
This page provides information about features of Storm Center maps based on the most recently available features. KUBRA periodically releases new features for the Storm Center solution and may include a preview of the new features for non-critical instances before releasing the new features to all instances.
{{% /notice %}}

The following diagram shows the different parts of the Storm Center map interface. Storm Center maps can be configured with or without a map header.

![Storm Center map wireframe](/images/storm_center_map_wireframe.png)

## Map Header, Overview Panel, and Help Panel ##

If the map includes a map header, the header can optionally include link buttons, social media icon buttons, and a company logo with a hyperlink. On smaller screens, the link buttons and social media icon buttons are included in the overview panel.

If the map does not include a map header, configured link buttons and social media icon buttons will appear in the overview panel at all screen sizes.

The overview panel and the help panel open to the left side of the map.

### Overview Panel ###

The overview panel button opens the overview panel. This button has a configurable icon and can optionally include a text label such as "Menu."

The overview panel includes summary outage information, links to outage summary reports, and weather radar settings. The overview panel can optionally include configurable content blocks and button links.

#### Summary Outage Information Label ####

The overview panel can optionally include a text label above the summary outage information, such as "Summary," the name of the organization, or a name for the map. If the organization has multiple operating companies or Regions, the overview panel can include separate information for each region or combined information for all regions.

#### Summary Outage Information ####

The summary outage information in the overview panel can include the total number of active outages, the total number of customers affected by active outages, and the total number of customers served.

Below the summary information, the overview panel shows the date and time at which information on the map was last updated and a note about how often information on the map is updated. The last updated timestamp is based on the time when data processing is completed for the most recent file submitted to the outage data feed. Admin users can manage the update frequency note in the [Storm Center Settings app](/storm-center/management-console/settings).

{{% notice note %}}
The summary information in the overview panel is based only on active outage data, that is, data from files submitted to the Outage data feed. It does not include information from files submitted to the Planned Outage data feed.
{{% /notice %}}

The organization can optionally include a content block below the summary information and above the rest of the content in the overview panel. This content block can include text, links, and images.
{{% notice note %}}
When using images inside content blocks, please upload images using Image Resource Manager, then reference the path URL for that image in the content blocks. Specifically, use the Link section when adding images to reference the path URL.
{{% /notice %}}

#### Summary Reports ####

The Summary section of the overview panel includes links to summary reports. The summary reports show the number of customers affected by active outages per area (county, postal code, or city/town/village) and overall, as well as the latest estimated restoration time for outages in each area.

The bottom of each summary report includes the date and time at which information was last updated and a note about how often information is updated. The last updated timestamp and update frequency note at the bottom of summary reports are the same as in the top section of the overview panel.

Summary reports can optionally include a description at the top of the report that can include hyperlinks or click-to-call links for phone numbers.

Summary reports can optionally include a button to allow users to download a copy of the data in the report as a CSV file.

#### Weather (Optional) ####

The Weather section of the overview panel includes tools for viewing weather radar information on the map. Users can turn static weather radar and radar animation on or off and adjust the opacity of the weather radar layer.

#### Additional Content ####

The overview panel can also include one or more configurable link buttons or content blocks below the Summary and Weather tools. For example, the overview panel can include links to an information page about the outage restoration process or contact information for the organization providing the map.

### Help Panel ###

The help panel is optional. If included, it can show one or more configurable link buttons, one or more configurable content blocks, or any combination of buttons and content blocks. For example, the help panel can provide tips for using the map, information about other resources, and links to web pages such as a help page or a page with additional information.

## Map Legend ##

The map legend defines the color-coding used for outage icons, area polygons, and the service territory boundary. If a map uses icons to indicate the presence of a crew at an outage location, the crew symbol also appears in the map legend.

The map legend card also includes the controls for map views, custom layers, and the service territory boundary.

### Map Views ###

Users can switch between map views using radio buttons or a selector on the map legend card. Map view choices include Location, County, ZIP or Postal Code, and City/Town/Village (CTV). If a map includes planned outage data, Planned Outages can appear as a map view choice. When a user changes the map view, the legend icons also change to match the selected map view.

### Custom Layers ###

The Custom Layers feature includes icons, shaded polygons, or both which are managed by admin users in the Control Center. Custom layers icons and areas can represent items such as flood zones, blocked roads, shelters, ice distribution trucks, or offices. Users of the map can turn the custom layers items on or off from the map legend card, and they can interact with custom layers items on the map to open an information panel with a name and a note. When custom layers items are visible on the map, the legend includes definitions for the custom layers icons and areas.

## Map Display Options ##

The map display options are a collection of buttons at the upper left corner of the map, to the right of the overview panel or help panel when that panel is open.

The available buttons from top to bottom are:

+ Search
+ Show My Location (requires the user to allow location services)
+ Map Overview
+ Select Language (if enabled, this allows users to change the map UI between the languages supported by the map)

Visible map display options buttons for desktop and mobile browsers can be configured in the Instance Manager.

{{% notice note %}}
Translations for most map elements are managed in the Instance Manager. Storm Center supports English, French, and Spanish.
{{% /notice %}}

### Search Button and Bookmarks Tool ###

The search button opens a modal with a search box and a bookmarks tool for saving locations. The search box allows users to enter an address, city name, or ZIP code to navigate to a specific location on the map. The bookmarks tool allows users to name and save a location after they search for a location. Users must have local storage enabled on their web browsers to save locations as bookmarks.

Map View supports a maximum of six bookmarks.

## Alert Banner ##

The alert banner is an optional feature managed by admin users in the Control Center. When an alert banner is active, it appears at the top or bottom of the map with a title message. Users can interact with the banner to open a message card. The alert banner message can include lists, images, links, tables, and videos. The alert banner message can be set to open automatically on page load to make important messages more visible to users.

## Map Controls ##

### Zoom In and Zoom Out ###

Storm Center supports zoom using a mouse wheel and pinch-to-zoom. The map also provides zoom in and zoom out buttons in the lower right corner of the map to support users who prefer manual selection or keyboard controls.

The zoom in and zoom out buttons are hidden by default when Storm Center detects a touch device such as a smartphone or a laptop touchpad that supports pinch-to-zoom. Visibility of the zoom buttons can be configured in the Instance Manager.

### Background Map ###

The background map is provided using the Google Maps API and includes up to three options: road, satellite, and hybrid. Users can change between the supported background map types using the controls in the lower right corner of the map.

## Outage Locations and Clusters ##

In "View by Locations," the map shows outage information using icons to represent individual outage locations and cluster icons to represent groups of outage locations that are close together.

Outage location icons can be color-coded based on the number of customers affected by the outage, divided into one or more configurable ranges: for example, 1-10 customers, 11-50 customers, 51-250 customers, and more than 250 customers. Outage location icons use shapes as well as colors to distinguish between customers-affected ranges. An organization can alternatively choose to use one outage location icon color for all individual outage locations.

Outage location icons can optionally include an additional icon that indicates when a repair crew is on site working to repair the outage.

Outage cluster icons can optionally indicate how many outage locations are included in the cluster.

### Information Panels ###

When users interact with an outage location icon, an information panel opens from the right side of the map (for desktop browsers) or the bottom of the map (for mobile browsers).

Information panels for outage location icons can include any combination of the following data:

+ Estimated restoration time (ERT)
+ Number of customers affected
+ Start time of the outage
+ Incident ID
+ Cause of outage
+ Crew status
+ Comments
+ Metadata - additional configurable information types described in the [outage file specification](/shared-file-specifications/outage-file)

Information panels for outage cluster icons can include any combination of the following data:

+ Number of outages
+ Earliest start time for outages in the cluster
+ Latest estimated restoration time (ERT) for outages in the cluster
+ Number of customers affected

Information panels for outage cluster icons can expand at closer zoom levels, which shows information for the individual outage locations included in the cluster instead of aggregated information for all outages in the cluster.

## Planned Outage Locations and Clusters (Optional) ##

If a map includes information about planned outages, the planned outage view shows information using icons to represent individual planned outage locations and cluster icons to represent groups of planned outage locations that are close together.

Planned outage location icons can be color-coded based on the number of customers affected by the outage, divided into one or more configurable ranges: for example, 1-10 customers, 11-50 customers, 51-250 customers, and more than 250 customers. Planned outage location icons use shapes as well as colors to distinguish between customers-affected ranges. An organization can alternatively choose to use one planned outage location icon color for all individual planned outage locations.

If a planned outage view is configured to use one range for all planned outages, the map legend can show a label such as “Planned Outage” instead of a number range for number of customers affected.

Planned outage cluster icons can optionally indicate how many planned outage locations are included in the cluster.

### Information Panels ###

When users interact with a planned outage location icon, an information panel opens from the right side of the map (for desktop browsers) or the bottom of the map (for mobile browsers).

Information panels for planned outage location icons can include any combination of the following data:

+ Estimated start time of the outage
+ Estimated end time of the outage
+ Estimated duration of the outage
+ Number of customers affected
+ Incident ID
+ Cause of outage
+ Comments
+ Metadata - additional configurable information types described in the [planned outage file specification](/storm-center/file-specifications/planned-outage-file)

Information panels for planned outage cluster icons can include any combination of the following data:

+ Number of outages
+ Earliest start time for planned outages in the cluster
+ Latest estimated end time for planned outages in the cluster
+ Number of customers affected

Information panels for planned outage cluster icons can expand at closer zoom levels, which shows information for the individual planned outage locations included in the cluster instead of aggregated information for all planned outages in the cluster.

## Outages by Area ##

In "View by County," "View by ZIP," and "View by CTV," the map shows outage information using colored shading to represent areas with outages. The shading can be color-coded based on the number or percentage of customers affected by outages in the area, divided into one or more configurable ranges. An organization can alternatively choose to use one color for shading all areas affected by outages.

In the data specifications, a group of areas of the same type is called a "thematic." For example, the data that defines the shape of counties to be shown on a Storm Center map would be included in a thematic file.

### Information Panels ###

When users interact with a shaded area, an information panel opens from the right side of the map (for desktop browsers) or the bottom of the map (for mobile browsers).

Information panels for shaded areas can include any combination of the following data:

+ Number of outages
+ Number of customers affected
+ Number of customers served
+ % of customers affected
+ Earliest start time for outages in the area
+ Latest estimated restoration time (ERT) for outages in the area

## Information Panel Link Buttons ##

Information panels can also include one or more buttons at the bottom of the panel. In addition to the **Magnify/Zoom** button, which is mandatory, one or more link buttons can be configured in the Instance Manager with a label and link target.

Separate buttons can be configured for the information panels attached to outage locations, outage location clusters, and each type of area.

## Information Panel Configurable Content ##

Information panels can include a configurable content block at the bottom of the panel. Separate content can be configured for the information panels attached to outage locations, outage location clusters, and each type of area.

## Additional Map Layers (optional) ##

The Additional Map Layer module allows clients to display additional data like hazards, gas outages, flooding etc. on their public or internal Outage Maps, such as safety concerns, planned work, and reliability indexes. Clients collect and deliver the information in a GeoJSON file via the Additional Map Layer datafeed, and Storm Center presents the features on their maps with the client's chosen symbology. The layer can be displayed on one or more Storm Center maps, and map users can view detailed information about a feature by selecting it. The summary overview in the Overview Panel displays the total feature count.
