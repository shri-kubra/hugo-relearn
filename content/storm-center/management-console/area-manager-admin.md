---
title: "Area Manager Admin Tool"
weight: 35
---

To access the Area Manager Admin tool, click the **Area Manager** button on the Control Center Dashboard under "App Administration."

You can use the Area Manager Admin tool to determine which types of information can be overwritten in the Area Manager app, and to provide a hierarchy for thematic areas in the Area Manager app.

![Area Manager Admin tool](/images/area-manager-admin-tool.png)

## Configure Thematics ##

By default, all thematics associated with the instance allow overwritten values for estimated restoration time (ETR) and for customers affected.

To change these settings, select a thematic from the drop-down under "Select a Thematic" and then de-select the **Allow Overwritten ETR** toggle, the **Allow Overwritten Customers Affected** toggle, or both toggles for the data types you do not want to include in the Area Manager app.

If a thematic includes a hierarchy, you can select a starting and ending hierarchy to adjust the hierarchy levels included in the Area Manager app. For example, if you have a County thematic that includes a hierarchy for State, you can remove the ability to enter overwritten values at the state level by selecting "County" for both the starting hierarchy and the ending hierarchy.

{{% notice note %}}
You can only include up to two consecutive hierarchy levels in the Area Manager app. For example, if you have a thematic file that includes state, county, and city/town/village, you can include either state and county OR county and city/town/village in the Area Manager app, but not all three hierarchy levels.
{{% /notice %}}

To save your changes, click the **Submit** button in the "Select a Region and Thematic to Configure" section of the admin tool.

## Hide the Number of Outages ##

To hide the number of outages from the overview panel, summary reports, and information panels for areas in a thematic layer when overwritten values for ETR are published from the Area Manager app, click the **For Overwritten ETR** checkbox.

To hide the number of outages from the overview panel, summary reports, and information panels for areas in a thematic layer when overwritten values for Customers Affected are published from the Area Manager app, click the **For Overwritten Customers Affected** checkbox.

To save your changes, click the **Submit** button in the "Hide Number of Outages" section of the admin tool.

{{% notice tip %}}
If you want to hide one or more outage information layers from the map when overwritten values are published from the Area Manager app, you can configure those settings from the [Edit Option form](/storm-center/configuration-guide/configure-layer-visibility/#add-layer-options) in the Layer Visibility sub-section of the Shared Resources section of the Instance Dashboard.
{{% /notice %}}

## Set Up Predefined ETR Messages ##

By default, the Area Manager app includes "Pending" and "Assessing Condition" messages. To edit an existing message, click the **Edit** button to the right of the message you want to edit. To delete an existing message, click the **Delete** button to the right of the message you want to delete.

To configure predefined ETR messages for the Area Manager app, click the **Create New Predefined ETR Message** button. Enter message text for all languages supported by the instance and then click the **Submit** button.

To save your changes, click the **Submit** button in the "Predefined ETR Messages" section of the admin tool.

{{% notice note %}}
The predefined ETR messages are visible for all thematics included in the Area Manager app.
{{% /notice %}}
