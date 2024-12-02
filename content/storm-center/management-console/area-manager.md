---
title: "Area Manager App"
weight: 32
---

To access the Area Manager app, click the **Area Manager** button on the Control Center Dashboard under "Apps."

{{% notice note %}}
Access to the Area Manager app requires the optional Area Manager module. If you cannot see the Area Manager app, it may be because your organization does not have the Storm Center Area Manager module.
{{% /notice %}}

The Area Manager app screen includes a drop-down list for selecting one of the thematics associated with the instance, an option to provide an overwritten value for estimated restoration times (ETRs) for all areas in the thematic, and a table with a list of area names included in the currently selected thematic.

For example, if you have a "County" thematic, the Area Manager app will show a list of county names below the drop-down when you select the "County" thematic. The table of area names also includes columns for data from your outage data feed and for entering overwritten values to replace the values from the outage feed.

{{% notice note %}}
The Area Manager app shows all dates and times in the user's browser time zone. When times are published to a map view, they are converted to the time zone configured for the map view.
{{% /notice %}}

![Area Manager App - ZIP Codes](/images/area-manager-app-zip.png)

![Area Manager App - County/CTV](/images/area-manager-app-county-ctv.png)

## Provide a Global Overwritten ETR ##

If your Area Manager app is configured to allow overwritten values for Estimated Restoration Time, you can click on the **Overwrite All ETRs** button to provide a "global" overwritten ETR. A selector will open that allows you to choose a date and time value or to select a predefined text value for the ETR you want to show on the map. Setting an overwritten ETR in this selector will apply the overwritten ETR to all areas in the currently selected thematic.

![Global ETR Selector](/images/area-manager-app-global-etr.png)

## Enter Overwritten ETR Values by Area ##

If your Area Manager app is configured to allow overwritten values for Estimated Restoration Time, you can click on the text in the "Overwritten" column to the right of the "ETR" column for an area to enter an overwritten value. A selector will open that allows you to choose a date and time value or to select a predefined text value for the Estimated Restoration Time you want to show on the map for that area.

If the selected thematic includes an area hierarchy, you can apply an overwritten ETR value to the largest area in the hierarchy and then use the menu next to the overwritten value to apply the same value to all of the sub-areas in that hierarchy. For example, if you have a county thematic that includes a state hierarchy, you can choose to apply an overwritten ETR to at the state level and also apply the overwritten ETR to all of the counties in that state.

You can also use the menu next to an overwritten ETR value for the largest area in the hierarchy to clear overwritten values from all of the sub-areas in that hierarchy.

## Enter Overwritten Customers Affected Values by Area ##

If your Area Manager app is configured to allow overwritten values for Customers Affected, you can click on the text in the "Overwritten" column to the right of the "Affected" column for an area to enter an overwritten value. A text field will open that allows you to type in the number of Customers Affected you want to show on the map for that area.

{{% notice note %}}
You cannot enter an overwritten value for Customers Affected that is higher than the number of customers served for that area. To help you keep track of this value, the Area Manager tool includes a "Served" column which shows the number of customers served for each area in the list.
{{% /notice %}}

## Publish Overwritten Data ##

When you have finished entering all the overwritten values you want, click the **Deploy** button to save the overwritten values and show them on the map or maps for the instance.

The app will show a message whenever there are undeployed changes. This message disappears when you click the **Deploy** button.

![Area Manager - undeployed changes message and Deploy button](/images/area-manager-app-deploy-changes.png)

## Override Total Customers Affected and Total Outages fields ##

Area Manager allows you to override the Total Customers Affected and Total Outages fields with values that are more accurate than the OMS values in the outage feed.

You can input your preferred values in these fields to have complete control over outage and customer data for each region. Area Manager has built-in checks to ensure these values align with the Customers Served values.

Ensure you click **Deploy** to deploy the overridden values.

![Area Manager - Override Total Customers Affected and Total Outages fields](/images/area-manager-app-override-total-customers-affected.png)

You can also implement these overrides through API calls.


