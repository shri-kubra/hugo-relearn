---
title: "Map History"
weight: 33
---

## Introduction ##

Map History is an optional module for Storm Center. Enabling this module allows an organization to keep up to five years of historical data processed by Storm Center. The Map History module also includes a Map History Viewer tool, where authorized users can select a time period from the five-year data retention window and view the selected data on an interactive map. Authorized users can also bookmark a specific date and time from the data retention window for future reference.

{{% notice note %}}
Bookmarks are deleted when they pass out of the five-year data retention window.
{{% /notice %}}

The Map History module combines data from all maps associated with the organization's instance into one map view. The data shown in the Map History Viewer is based on the data files used by the Storm Center maps and some Control Center settings, along with configurations made in the Map History app.

## Map History Viewer ##

To access the Map History Viewer:

1. Navigate to the Instance Manager website.
1. Sign in using Google or other single sign-on credentials.
1. Choose a tenant - this option is only presented if you have access to more than one tenant.
1. Choose the Map History application.
1. Choose a Storm Center instance.

### View Historical Data ###

You can use the Map History Viewer to view all data processed by Storm Center for a specific time range with full user interaction including information panels, panning, zooming, and outage summary reports.

To view historical map data:

1. Click the **Select Date and Time** button at the top of the Map History Viewer.
2. Use the calendar to select a date and time for which you want to view historical outage data.
3. Click the **Apply** button.

After you select a date and time, the top of the Map History Viewer will show a date and time range. This time range indicates the range of time for which a specific set of data was visible on the map views associated with the instance. For example, if one data set was generated on May 4, 2018 at 6:35 a.m., the next data set was generated at 6:50 a.m., and you select May 4, 2018 at 6:45 a.m., the Map History Viewer will show the time range "May 4, 2018 6:35 AM to 6:50 AM."

If you select the latest data snapshot, the time range will be the date and time when the data was generated to "Present."

To navigate from one time range to the time range before or after, you can click the arrow buttons to the right or left of the date and time range at the top of the Map History Viewer. If there is no data for the time range before or after the time range you are viewing, the arrow button or buttons will be disabled.

Consider an example map with data sets generated on May 4, 2018 at 6:35 a.m., 6:50 a.m., 7:05 a.m., and 7:20 a.m. If you select May 4, 2018 at 7:00 a.m., the Map History Viewer will show the time range "May 4, 2018 6:50 AM to 7:05 AM." If you then click the left arrow to view the previous time range, the Map History Viewer will show the time range "May 4, 2018 6:35 AM to 6:50 AM." If you then click the right arrow twice, the Map History Viewer will show the time range "May 4, 2018 7:05 AM to 7:20 AM."

#### Map History Data Display ####

The Map History Viewer shows data in information panels with generic data type labels such as "Incident ID," "Affected," and "Crew Status." If a data type does not have a value for a specific outage and time range, that data type will not appear in the information panel for that outage.

The Map History Viewer does not show configured static values for null or expired Estimated Restoration Time (ETR). Instead, the Map History Viewer shows the exact ETR value from the outage data file for the selected time range. For null ETR values, the Map History Viewer does not show the ETR field in the information panel. For areas, the ETR shown in the Map History Viewer is the latest ETR for all outages affecting the area at the start of the selected time range. If all outages affecting an area have null ETR values, the ETR field in the summary report for that area will be blank.

If an instance has more than one map view and uses data field mapping for at least one map view, the Map History Viewer will show both the unmapped data values from the outage data feed and the mapped values. For each data type that can include mapping, the Map History Viewer shows the name of the data layer before the data value. Data layer names are created as part of the process to configure [outage data layers](/storm-center/configuration-guide/create-outage-layers/#layer-name-source-and-titles).

All alert banners that were visible on any map views associated with the instance at the start of the selected time range will be shown as a list when you click the alert banner at the bottom of the map. The list of alert banners will show the name of the map view and the time associated with each alert banner. Map view names are created as part of the process to configure [map views](/storm-center/configuration-guide/create-map-view/#general-information).

All custom layers items that were visible on map views associated with the instance at the start of the selected time range will be visible.

If an instance includes the [Area Manager Control Center app](/storm-center/management-console/area-manager) and there were overwritten values for Estimated Restoration Time (ETR) and/or Customers Affected entered in the Area Manager app for one or more areas at the start of the selected time range, the Map History Viewer will show the overwritten values in the information panels and summary reports for those areas.

### Map History Bookmarks ###

To create a bookmark:

1. Use the **Select Date and Time** tool to select the date and time you want to bookmark.
2. Click the **Bookmarks** button at the upper right of the Map History Viewer.
3. Click the **Add New Bookmark** button.
4. Enter a name for the bookmark. The date and time you are bookmarking is shown below the name field.
5. Click the **Save** button.

To view a bookmark:

1. Click the **Bookmarks** button at the upper right of the Map History Viewer.
2. Click the name of the bookmark you want to view. The date and time range for the bookmark will appear at the top of the Map History Viewer.

To edit a bookmark name:

1. Click the **Bookmarks** button at the upper right of the Map History Viewer.
2. Click the pencil icon to the right of the bookmark you want to edit.
3. Enter a new name for the bookmark.
4. To save your changes, click the checkmark icon. To discard your changes, click the X icon.

To delete a bookmark:

1. Click the **Bookmarks** button at the upper right of the Map History Viewer.
2. Click the trash can icon to the right of the bookmark you want to delete.

## Configuration ##

Configuration for the Map History module is managed from the **Settings** section of the Map History app. There are five types of configurations:

+ Thematic Ranges
+ Outage Ranges
+ Service Territory
+ Default Styling
+ Timezone Configuration

To access the Map History settings:

1. Navigate to the Instance Manager website.
1. Sign in using Google or other single sign-on credentials.
1. Choose a tenant - this option is only presented if you have access to more than one tenant.
1. Choose the Map History application.
1. Choose a Storm Center instance.
1. Choose the **Settings** option on the left side of the screen.

After you make and save changes in the Map History settings, you must reload the web page to see the changes in the Map History Viewer.

### Thematic Ranges ###

For each area type associated with the selected instance, you can configure up to five thematic ranges with start and end values for number of customers affected, a color, and an opacity percentage to be used on the Map History Viewer.

1. Select the **Thematic Ranges** option from the Layer Styles list.
2. Select an area type from the Thematics drop-down list.
3. Enter the start and end values for customers affected for the range.
4. Select a color for the thematic range from the Color drop-down list. There are six options: blue, green, yellow, red, purple, and gray.
5. Enter an opacity percentage for the thematic range shading. By default, the opacity percentage is 40%.
6. Click the **Add Another Range** button and repeat steps 3-5 for each additional range you want to include. You can include up to five ranges.
7. Repeat steps 2-6 for each area type you want to configure thematic ranges for.
8. Click the **Save** button.

{{% notice note %}}
You must leave the end value of the highest range blank (no value). On the map legend, this will create a label for the range such as ">500," where "501" is the start value for the range. Information in the data retention window for any area types that do not match the ranges you configure here will be shown using the Default Styling.
{{% /notice %}}

### Outage Ranges ###

For the outage location icons, you can configure up to five ranges with start and end values for number of customers affected and an icon to be used on the Map History Viewer. You can also configure a cluster tolerance setting.

1. Select the **Outage Ranges** option from the Layer Styles list.
2. Enter the start and end values for customers affected for the range.
3. Select an icon from the Color drop-down list. There are six options: red diamond, yellow pentagon, purple triangle, green hexagon, blue circle, and individual outage.
4. Repeat steps 2-3 for each additional range you want to include. You can include up to five ranges.
5. Select a cluster tolerance for the outage location icons. This is a value between 20 and 40. The recommended value is 35.
6. Click the **Save** button.

{{% notice note %}}
You must leave the end value of the highest range blank (no value). On the map legend, this will create a label for the range such as ">500," where "501" is the start value for the range. Information in the data retention window for any outage icons that do not fit the ranges you configure here will be shown using the Default Styling.
{{% /notice %}}

### Service Territory ###

For the service territory, you can configure the color and opacity percentage to be used on the Map History Viewer.

1. Select the **Service Territory** option from the Layer Styles list.
2. Select a color from the drop-down list. There are eight options: blue, green, lime, orange, pink, purple, red, or yellow.
3. Enter an opacity percentage for the service territory shading. KUBRA recommends that this opacity be set lower than the opacity for thematic range shading.
4. Click the **Save** button.

### Default Styling ###

You can configure default styles for any thematics or outage location icons that cannot be represented on the Map History Viewer by the other configurations you have set.

1. Select the **Default Styling** option from the Layer Styles list.
2. Select a default color for thematics from the Color drop-down list. There are six options: red, yellow, purple, green, blue, and gray.
3. Enter an opacity percentage for the thematic shading.
4. Select a default outage location icon from the Icon drop-down list. There are six options: red diamond, yellow pentagon, purple triangle, green hexagon, blue circle, and individual outage.
5. Click the **Save** button.

### Timezone Configuration ###

You can configure a time zone to be used on the Map History Viewer.

1. Select the **Timezone Configuration** option from the Layer Styles list.
2. Select a time zone from the drop-down list. There are six options: User Locale, Eastern (UTC -5), Central (UTC -6), Mountain (UTC -7), Mountain - No Daylight Saving (UTC -7), and Pacific (UTC -8).
3. Click the **Save** button.
