---
title: "Create Service Territory"
weight: 15
---

Storm Center outage maps can optionally show a visual indicator of the geographical area served by a utility, either as an outline or as a shaded area.

To create a visual indicator of a service territory or service area, use the **Service Territories** sub-section of the **Shared Resources** section of the Instance Dashboard.

1. Click the **Create Service Territory** button.
1. Enter a name for the service territory boundary - this name is how you will identify the service territory in other areas of the Instance Manager; it will not show up on the map.
1. Select one or more region files to use for the service territory data.
    + If you want to combine the shapes of multiple regions to create one service territory boundary on an outage map, click the **Merge Multiple Regions?** checkbox.
1. Select a color to use for indicating the service territory - options are Green, Blue, Lime, Orange, Pink, Purple, Red, and Yellow.
1. Enter a percentage for the fill opacity. If you want the service territory to appear as an outline, enter `0` for the fill opacity.
1. If you want to provide a toggle on the map legend to allow map users to turn the service territory indicator on and off, click the **Include Toggle for Service Territory** checkbox.
1. If you provide a toggle for the service territory and you want the service territory indicator to be visible when the map page first loads, click the **Set Toggle to "On" on Map Page Load** checkbox.
1. Enter labels to be used on the map for the service territory indicator for each language supported by the instance.
    + KUBRA recommends a maximum of 20 characters for this label. You may need to adjust the length or formatting of the label after testing it on a map to ensure that it displays well without wrapping to a second line.
1. Click the **Save** button.

To edit settings for an existing service territory, click on the service territory name in the list of Service Territories.
