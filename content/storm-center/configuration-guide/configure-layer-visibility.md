---
title: "Configure Layer Visibility"
weight: 20
---

## Layer Visibility ##

Layer Visibility refers to the way outage information layers are presented as choices in the Storm Center map legend.

To configure the choices to show in the Storm Center map legend, use the **Layer Visibility** sub-section of the **Shared Resources** section of the Instance Dashboard.

## Prerequisites ##

Before you can create a layer visibility configuration, you must [create outage data layers](/storm-center/configuration-guide/create-outage-layers).

## Create a New Layer Visibility Configuration ##

1. Click the **Create New Configuration** button.
1. Enter a name for the layer visibility configuration - this name is how you will identify the layer visibility configuration in other areas of the Instance Manager and in a URL parameter to control the configuration selected on map page load. This name will not show up on the map user interface.
1. If you want to show a general label for the layer visibility configuration in the map legend, enter a label. Provide separate labels for each language supported by the instance. This label will appear in the map view selector or in the map legend above the map view selector if a map uses multiple layer visibility configurations.
1. Click the **Submit** button.

Each visibility configuration can have options and sub-controls.

+ Options determine how many items will be included in the map view selector in the map legend.
+ Sub-controls allow you to include multiple layers under one option and automatically switch between the layers at a zoom level you specify.

### Add Layer Options ###

After you submit a new layer visibility configuration, the Create Option form opens automatically. To edit layer options or add layer options to an existing layer visibility configuration, click the **Edit Options** button in the Visibility Configurations list.

1. To add a new layer option to the visibility configuration, click the **Create New Option** button.
1. Enter a name for the option - this name is how you will identify the option in other areas of the Layer Visibility forms and in a URL parameter to control the option selected on map page load. It will not show up on the map user interface.
1. Enter a label for the option to be shown in the selector in the map legend - provide separate labels for each language supported by the instance.
1. Select the layer or layers you want to include for the option. If you include multiple layers here, all layers will appear at the same time when the option is selected.
  + If you want to include multiple layers with automatic switching between the layers based on zoom level, do not select a layer here and instead select the layers as sub-controls.
1. Enter a minimum and maximum zoom level for the option. These settings combine with the check zoom in and check zoom out settings as described in the examples below.
1. If you want to have the map switch from the current option to a different option when the user has this option selected and zooms out, check the **Check Zoom Out** setting.
1. If you want to have the map switch from the current option to a different option when the user has this option selected and zooms in, check the **Check Zoom In** setting.
1. If you want to disable the option when there is overwritten data for customers affected entered in the [Area Manager app](/storm-center/management-console/area-manager), check the **Disable Option when Customers Affected Override Present** setting.
1. If you want to disable the option when there is overwritten data for ETR entered in the Area Manager app, check the **Disable Option when ETR Override Present** setting.
1. To add the option to the layer visibility configuration, click the **Submit** button.
1. Repeat these steps for each option you want to add to the layer visibility configuration.

After you have created all the options you want to include in the visibility configuration, you can change the order in which the options will appear in the map view selector. The numbers in the "Order" column on the Visibility Options screen from lowest to highest will be the order from top to bottom in the map view selector.

### Add Layer Sub-Controls ###

To edit sub-controls or add sub-controls to an option, click the **Edit Sub-Controls** button in the Visibility Options list or on the Edit Option form.

1. To add a new sub-control, click the **Create New Sub-Control** button.
1. Enter a name for the sub-control - this name is how you will identify the sub-control in other areas of the Layer Visibility forms.
1. Select the layer you want to include in the sub-control.
1. Enter a minimum and maximum zoom level for the sub-control.
1. To add the sub-control to the option, click the **Submit** button.
1. Repeat these steps for each sub-control you want to add to the option.

{{% notice note %}}
The zoom level settings for the sub-controls on an option must be adjacent but not overlapping.
{{% /notice %}}

### Select Default Options per Map Mode ###

To add settings for the visibility options to be shown on page load for blue-sky mode and storm mode, return to the Visibility Configurations list and then click the **Edit** button to the right of the visibility configuration name.

1. Select which visibility option will be shown on page load for blue-sky mode.
1. Select which visibility option will be shown on page load for storm mode.

Blue-sky mode and storm mode are the two map modes you can change between in the [Storm Center Settings app](/storm-center/management-console/settings). Selecting a different visibility option for storm mode than for blue-sky mode in this section of the Instance Manager allows you to change what users see on the map on page load if you change the map mode from "blue-sky" to "storm" in the Storm Center Settings app.

{{% notice note %}}
If a map includes more than one visibility configuration, the storm mode setting will only work for the first visibility configuration in the list.
{{% /notice %}}

## Configuration Examples ##

You can use settings for visibility configurations, visibility options, and sub-controls to create multiple ways of presenting outage layers on a map. Some examples are discussed below.

Examples 1-4 use a map with the following settings.

| Setting | Value |
| ------- | ----- |
| Minimum Zoom Level | 5 |
| Maximum Zoom Level | 18 |
| Starting Zoom Level | 10 |
| Layer 1 | An outages layer called "Location" |
| Layer 2 | A thematic layer for ZIP Code |
| Layer 3 | A thematic layer for County |

Examples 5-8 use a map that also has a planned outages layer called "Planned."

### Example 1 - One visibility option per layer with auto-switching between visibility options ###

To create a map that provides separate map view choices for each layer and automatically switches from the county layer to the ZIP code layer to the outages layer as a user zooms in, follow these guidelines.

Auto-switching between the map view choices is especially helpful for users on mobile devices, as it helps ensure that the user can always see useful information. Keeping separate visibility options for each layer allows users to select any of the choices at any zoom level.

+ Create three visibility options, one for each data layer: Location, ZIP Code, and County.
+ Use the settings from the table below.
+ Select the Location option as the default for blue-sky mode.
+ Select the County option as the default for storm mode.

Option/Sub-Control | Layer | Minimum Zoom Level | Maximum Zoom Level | Check Zoom In | Check Zoom Out
----- | ----- | ----- | ----- | ----- | -----
Location | Outages - Location | 13 | 18 | No | No
ZIP Code | Thematic - ZIP Code | 9 | 12 | Yes | No
County | Thematic - County | 5 | 8 | Yes |No

The visibility options in the configuration will match the map view choices available in the map legend.

![Configuration and Map Legend - example 1](/images/visibility-example-1.png)

The configuration will create a map that looks like this.

![Map example - three layer options](/images/separate-options-switching-dropdown.png)

The user can use the map view selector in the map legend to change between visibility options at any zoom level. Because the Location option is selected as the default for blue-sky mode, the map opens at zoom level 10 with the Location option selected. If an admin user changes the map from blue-sky mode to storm mode, the map will open at zoom level 10 with the County option selected.

If the user selects the County option, the map will show the County layer. If the user then zooms in, the map will change from the County option to the ZIP Code option when the user zooms in to any of the zoom levels in the range for the ZIP Code option. If the user continues to zoom in with the ZIP Code option selected, the map will change from the ZIP Code option to the Location option when the user zooms in to any of the zoom levels in the range for the Location option.

If the user zooms out with any of the three options selected, the map will not change from the selected option to one of the other options. In addition, the user can select a different option at any zoom level. The map view will change if the user zooms in and the new zoom level is in the range for a different option.

### Example 2 - One visibility option for outage locations layer and one visibility option for thematic layers with auto-switching between thematic sub-controls ###

To create a map that provides two map view choices, one for outages by location and one for outages by area, and that automatically switches between the county layer and the ZIP code layer when the "outages by area" choice is selected and a user zooms in or out, follow these guidelines.

+ Create two visibility options: one for the outages layer (Locations option) and one for the two thematic layers (Areas option). Do not select a layer at the option level for the Areas option.
+ Create two sub-controls for the Areas option: one for the County layer and one for the ZIP Code layer.
+ Use the settings from the table below.
+ Select the Locations option as the default for blue-sky mode.
+ Select the Areas option as the default for storm mode.

Option/Sub-Control | Layer | Minimum Zoom Level | Maximum Zoom Level | Check Zoom In | Check Zoom Out
----- | ----- | ----- | ----- | ----- | -----
Locations | Outages - Location | 13 | 18 | No | No
Areas | none | 5 | 12 | Yes | No
ZIP Code | Thematic - ZIP Code | 10 | 18 | - | -
County | Thematic - County | 5 | 9 | - | -

{{% notice note %}}
Sub-Controls are considered to have the Check Zoom In and Check Zoom Out settings selected by default.
{{% /notice %}}

The visibility options in the configuration will match the map view choices available in the map legend.

![Configuration and Map Legend - example 2](/images/visibility-example-2.png)

The configuration will create a map that looks like this.

![Map example - two options](/images/two-options-dropdown.png)

The user can use the map view selector in the map legend to change between visibility options at any zoom level. Because the Locations option is selected as the default for blue-sky mode, the map opens at zoom level 10 with the Locations option selected. If an admin user changes the map from blue-sky mode to storm mode, the map will open at zoom level 10 with the Areas option selected.

If the user selects the Areas option, the map will show either the County layer or the ZIP Code layer depending on the current zoom level. If the user zooms in with the Outages by Area choice selected, the map will change from the County layer to the ZIP Code layer when the user zooms in to any of the zoom levels in the range for the ZIP Code sub-control. If the user continues to zoom in, the map will change from the ZIP Code layer to the Location option when the user zooms in to any of the zoom levels in the range for the Location option.

If the user zooms out with the Outages by Area choice selected, the map will change from the ZIP Code layer to the County layer when the user zooms out to any of the zoom levels in the range for the County sub-control.

### Example 3 - One visibility option per layer with no auto-switching between layers ###

To create a map that provides separate map view choices for each layer and does not automatically switch between layers when a user zooms in or out, follow these guidelines.

+ Create three visibility options, one for each data layer.
+ Use the settings from the table below.
+ Select the Location option as the default for blue-sky mode.
+ Select the County option as the default for storm mode.

Option/Sub-Control | Layer | Minimum Zoom Level | Maximum Zoom Level | Check Zoom In | Check Zoom Out
----- | ----- | ----- | ----- | ----- | -----
Location | Outages - Location | 5 | 18 | No | No
ZIP Code | Thematic - ZIP Code | 5 | 18 | No | No
County | Thematic - County | 5 | 18 | No |No

The visibility options in the configuration will match the map view choices available in the map legend.

![Configuration and Map Legend - example 3](/images/visibility-example-3.png)

The configuration will create a map that looks like this.

![Map example - three options](/images/separate-options-dropdown.png)

The user can use the map view selector in the map legend to change between visibility options, and each visibility option is visible at all zoom levels supported by the map.

### Example 4 - One visibility option for all layers with auto-switching between sub-controls ###

To create a map that does not include map view choices in the map legend and automatically switches between the layers when a user zooms in or out, follow these guidelines.

+ Create one visibility option with no layers selected at the option level.
+ Create three sub-controls, one for each layer.
+ Use the settings from the table below.
+ Select the visibility option as the default for both blue-sky mode and storm mode. This means that changing the map mode in the [Storm Center Settings app](/storm-center/management-console/settings) will not change the map UI.

Option/Sub-Control | Layer | Minimum Zoom Level | Maximum Zoom Level | Check Zoom In | Check Zoom Out
----- | ----- | ----- | ----- | ----- | -----
Outages | none | 5 | 18 | Yes | Yes
Location | Outages - Location | 14 | 18 | - | -
ZIP Code | Thematic - ZIP Code | 11 | 13 | - | -
County | Thematic - County | 5 | 10 | - | -

The combination of the sub-control zoom level ranges should be the same as the overall zoom level range for the map, and the ranges of the sub-controls should be adjacent but not overlapping.

Because there is only one visibility option in the configuration and because layers are only connected at the sub-control level, there will not be any map view choices in the map legend.

The configuration will create a map that looks like this.

![Map example - one option - ZIP codes](/images/no-dropdown.png)

![Map example - one option - outage locations](/images/no-dropdown-locations.png)

The user does not have a choice to change between the layers in the map legend. The County sub-control is visible at the minimum zoom level supported by the map, and this view changes to the ZIP Code sub-control when the user zooms in to any of the zoom levels in the range for the ZIP Code sub-control, and then to the Location sub-control when the user zooms in to any of the zoom levels in the range for the Location sub-control.

### Example 5 - One visibility configuration for active outage layers and one visibility configuration for planned outages in list format ###

To create a map that shows a list of radio buttons for active outages and planned outages always visible on the map legend and includes a map view selector to view active outages by location or by area when the active outages choice is selected, follow these guidelines.

+ Create one visibility configuration called Active-Outages with one visibility option for the location layer and one visibility option with sub-controls for the county and ZIP code layers.
+ Use the settings from the table below for this Active Outages visibility configuration.
+ Select the Locations visibility option as the default for blue-sky mode and the Areas visibility option as the default for storm mode.

Option/Sub-Control | Layer | Minimum Zoom Level | Maximum Zoom Level | Check Zoom In | Check Zoom Out
----- | ----- | ----- | ----- | ----- | -----
Locations | Outages - Location | 13 | 18 | No | No
Areas | none | 5 | 12 | Yes | No
ZIP Code | Thematic - ZIP Code | 10 | 18 | - | -
County | Thematic - County | 5 | 9 | - | -

+ Create a second visibility configuration with one visibility option for the planned outages layer.
+ Use the settings from the table below for this Planned Outages visibility configuration.
+ Select the Planned Outages visibility option as the default for both blue-sky and storm mode for the planned outage visibility configuration.

Option/Sub-Control | Layer | Minimum Zoom Level | Maximum Zoom Level | Check Zoom In | Check Zoom Out
----- | ----- | ----- | ----- | ----- | -----
Planned Outages | Planned | 5 | 18 | No | No

+ Select both the Active-Outages visibility configuration and the Planned-Outages visibility configuration under Shared Resources in the [Create Map View form](/storm-center/configuration-guide/create-map-view/#shared-resources). The order in which you select the visibility configurations is the order in which they will appear in the map legend.
+ Select the "Show Legend as List" option under Widgets in the [Create Map View form](/storm-center/configuration-guide/create-map-view/#widgets).

The visibility configurations in the map view configuration will match the radio button map view choices available in the map legend, and the visibility options in the active outages configuration will match the drop-down map view choices available in the map legend.

![Configuration and Map Legend - example 5](/images/visibility-example-5.png)

The configuration will create a map that looks like this.

![Map example - two visibilities - list format](/images/two-visibilities-list-format.png)

The user can use the radio buttons above the map view selector in the map legend to choose to view either Active Outages or Planned Outages.

If the user selects the Active Outages radio button, the user can use the map view selector to change between Locations and Areas at any zoom level. While the Areas choice is selected, the map will change from showing Counties to showing ZIP Codes if the user zooms in to a zoom level in the range for the ZIP Codes sub-control.

If the user selects the Planned Outages radio button, the map will show cluster icons and individual outage icons for planned outages at all zoom levels.

If an admin user puts the map into Storm Mode using the [Settings app](/storm-center/management-console/settings), the selector under Active Outages will show Areas on page load instead of Locations. The Storm Mode setting will not have any effect on the Planned Outages map view choice.

### Example 6 - One visibility configuration for planned outages and one visibility configuration for active outage layers in menu format ###

To create a map that shows a map view selector at the top of the map legend that includes radio buttons for planned outages and active outages and choices to view active outages by location or by area when the active outages radio button is selected, follow these guidelines.

+ Create one visibility configuration with one visibility option for the planned outages layer.
+ Use the settings from the table below for this Planned Outages visibility configuration.
+ Select the planned outages visibility option as the default for both blue-sky and storm mode for the planned outage visibility configuration.

Option/Sub-Control | Layer | Minimum Zoom Level | Maximum Zoom Level | Check Zoom In | Check Zoom Out
----- | ----- | ----- | ----- | ----- | -----
Planned Outages | Planned | 5 | 18 | No | No

+ Create a second visibility configuration called Active-Outages with one visibility option for the location layer and one visibility option with sub-controls for the county and ZIP code layers.
+ Use the settings from the table below for this Active Outages visibility configuration.
+ Select the Locations visibility option as the default for blue-sky mode and the Areas visibility option as the default for storm mode.

Option/Sub-Control | Layer | Minimum Zoom Level | Maximum Zoom Level | Check Zoom In | Check Zoom Out
----- | ----- | ----- | ----- | ----- | -----
Locations | Outages - Location | 13 | 18 | No | No
Areas | none | 5 | 12 | Yes | No
ZIP Code | Thematic - ZIP Code | 10 | 18 | - | -
County | Thematic - County | 5 | 9 | - | -

+ Select both the Planned-Outages visibility configuration and the Active-Outages visibility configuration under Shared Resources in the [Create Map View form](/storm-center/configuration-guide/create-map-view/#shared-resources).
+ Leave the "Show Legend as List" option unselected under Widgets in the [Create Map View form](/storm-center/configuration-guide/create-map-view/#widgets).

The visibility configurations in the map view configuration will match the radio button map view choices available in the map view selector, and the visibility options in the active outages configuration will match the drop-down list map view choices available in the map view selector.

![Configuration and Map Legend - example 6](/images/visibility-example-6.png)

The configuration will create a map that looks like this.

![Map example - two visibilities - menu format](/images/two-visibilities-menu-format.png)

The user can open the map view selector at the top of the map legend to see two radio buttons, one for Planned Outages and one for Active Outages. While the Active Outages radio button is selected, the user can also use a list of choices to change between viewing active outages by location and viewing active outages by area. The user can change between Locations and Areas at any zoom level. While the Areas option is selected, the map will change from showing Counties to showing ZIP Codes if the user zooms in to a zoom level in the range for the ZIP Codes sub-control.

If the user selects the Planned Outages radio button, the map will show cluster icons and individual outage icons for planned outages at all zoom levels.

If an admin user puts the map into Storm Mode using the [Settings app](/storm-center/management-console/settings), the Storm Mode setting will not have any effect because the Planned Outages configuration appears first and does not have multiple visibility options.

### Example 7 - Separate visibility options for active outages and planned outages ###

To create a map that shows separate map view choices for active outages and planned outages as a list in the map view selector in the map legend, follow these guidelines. This is similar to the setup in example 3, except with active outages and planned outages layers instead of multiple active outages layers.

+ Create one visibility option for Active Outages with an Outages layer, and one visibility option for Planned Outages with a Planned layer.
+ Use the settings from the table below.
+ Select the Planned Outages visibility option as the default for blue-sky mode.
+ Select the Active Outages visibility option as the default for storm mode.

Option/Sub-Control | Layer | Minimum Zoom Level | Maximum Zoom Level | Check Zoom In | Check Zoom Out
----- | ----- | ----- | ----- | ----- | -----
Active Outages | Outages - Locations | 5 | 18 | No | No
Planned Outages | Planned | 5 | 18 | No | No

The visibility options in the configuration will match the map view choices available in the map legend.

![Configuration and Map Legend - example 7](/images/visibility-example-7.png)

The configuration will create a map that looks like this.

![Map example - active and planned outages options](/images/active-planned-dropdown.png)

The user can open the map view selector at the top of the map legend to change between viewing active outages and viewing planned outages. For this example, the outage icons and cluster icons are visible at all zoom levels.

If an admin user puts the map into Storm Mode using the [Settings app](/storm-center/management-console/settings), the map view selector will show Active Outages on page load instead of Planned Outages.

### Example 8 - Separate visibility configurations for active outage locations and planned outage locations ###

To create a map that shows separate map view choices for active outages and planned outages as radio buttons on the map legend, follow these guidelines.

+ Create one visibility configuration for Active Outages with one visibility option for the Outages - Locations layer.
+ Use the settings from the table below.
+ Select the Active Outages visibility option as the default for both blue-sky mode and storm mode.

Option/Sub-Control | Layer | Minimum Zoom Level | Maximum Zoom Level | Check Zoom In | Check Zoom Out
----- | ----- | ----- | ----- | ----- | -----
Active Outages | Outages - Locations | 5 | 18 | No | No

+ Create a second visibility configuration for Planned Outages with one visibility option for the Planned Outages layer.
+ Use the settings from the table below.
+ Select the Planned Outages visibility option as the default for both blue-sky mode and storm mode.

Option/Sub-Control | Layer | Minimum Zoom Level | Maximum Zoom Level | Check Zoom In | Check Zoom Out
----- | ----- | ----- | ----- | ----- | -----
Planned Outages | Planned | 5 | 18 | No | No

The visibility configurations in the map view configuration will match the radio button map view choices available in the map legend.

![Configuration and Map Legend - example 8](/images/visibility-example-8.png)

The configuration will create a map that looks like this.

![Map example - active and planned outages radio buttons](/images/active-planned-radios.png)

The user can select a radio button on the map legend to change between viewing active outages and viewing planned outages. For this example, the outage icons and cluster icons are visible at all zoom levels.

Because there is only one visibility option for each visibility configuration, the Storm Mode setting in the [Settings app](/storm-center/management-console/settings) will have no effect on the map.
