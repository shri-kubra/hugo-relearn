---
title: "Create Summaries and Summary Reports"
weight: 16
---

Storm Center outage and AML maps can optionally show summary information for the entire service territory at the top of the overview panel. The workflow for each of them differs significantly so they have been documented separately.

To set up summary data, use the **Summaries** sub-section of the **Shared Resources** section of the Instance Dashboard.

## Outage Summaries ##

1. Click the **Create Summary** button.
1. Enter a name for the summary - this name is how you will identify the summary information in other areas of the Instance Manager; it will not show up on the map.
1. Select the **Summary Type** to define what type of map you are creating the summary for. In this case, we will choose **Outage**.
1. Select one or more region files to use for the summary information.
1. If you have multiple region files and you want to combine information into one summary, select the **Merge Multiple Regions** checkbox. If you have only one region file, this option is not applicable.
1. Select the data fields you want to include in the overview panel summary. Options are:
    + Tool Panel Title
    + %Customers With/Without Power
    + Active Outages
    + Total Customers Affected
    + Total Customers Served
1. Enter text labels for the summary data fields you selected for each language supported by the instance.
    + KUBRA recommends that labels be as short as possible. You may need to adjust the length or formatting of the labels after testing them on a map to ensure that they display and wrap well.
1. If you want to include a date/time stamp that shows the last time active outage data on the map was updated, select the **Last Updated** checkbox.
1. Enter text labels for the Last Updated time for each language supported by the instance. This text will appear before the date/time stamp.
1. If you want to mask the exact number of customers affected at or below a specific value, click the **Customer Masking** checkbox and then enter a number.
    + The value you enter for customer masking here will be combined with verbiage you enter in the **Shared Resources** section of the **Create New View** form to create a label on the map such as "Fewer than 5."
1. Select an access restriction policy. The options available in the drop-down come from the policies created in the **Access Restriction** section of the Instance Dashboard.

{{% notice note %}}
For %Customers Affected in the overview panel summary, pick between %Customers With Power or %Customers Without Power. You can also configure the precision of the metric up to two decimal places.
{{% /notice %}}

## AML Summaries ##

1. Click the **Create Summary** button.
1. Enter a name for the summary - this name is how you will identify the summary information in other areas of the Instance Manager; it will not show up on the map.
1. Select the **Summary Type** to define what type of map you are creating the summary for. In this case, we will choose **AML**.
1. Select the **Summary Source Type** from the drop-down.
1. If you want to add **Summary Data Fields**, click on the button with the name. You can create multiple summary data fields.
  1. Name the Summary element you want to create.
  1. Select the Aggregation Method. Your choices are Sum, Count, Min, and Max.
  1. Select the Data type for the Summary Data Field. Your choices are String, Number, and Datetime.
1. Enter text labels for the summary data fields you created for each language supported by the instance.
    + KUBRA recommends that labels be as short as possible. You may need to adjust the length or formatting of the labels after testing them on a map to ensure that they display and wrap well.
1. Enter the summary title for each language supported by the instance.
1. Select the precision percentage you want to allow for your summary values. You can configure integer values between 0 and 2.
1. Select an access restriction policy. The options available in the drop-down come from the policies created in the **Access Restriction** section of the Instance Dashboard.

## Outage Summary Reports ##

Storm Center outage maps can include outage summary reports that show outage information by geographical area. These reports are accessed from buttons in the overview panel.

To set up summary reports to show outage information by area, use the **Summary Reports** sub-section of the **Shared Resources** section of the Instance Dashboard.

1. Click the **Create New Summary Report** button.
1. Enter a name for the report - this name is how you will identify the summary report in other areas of the Instance Manager; it will not show up on the map.
1. Choose the report type - options are "ZIP," "County," "CTV," and any Custom thematic names, if you created custom thematics when you [set up thematic data](/storm-center/configuration-guide/connect-data-files/#set-up-thematic-data) for the instance.
    + You will only see options in this list if there is a corresponding thematic file associated with your instance.
1. Enter a label to be used for the summary report button in the overview panel. Enter a label for each language supported by the instance.
    + KUBRA recommends that these labels be 10-15 characters. You may need to adjust the length or formatting of the label or labels after testing them on a map to ensure that they display and wrap well.
1. Enter a title to be used at the top of the summary report for each language supported by the instance.
    + KUBRA recommends that this title be no more than 30 characters.
1. If you want to include a description at the top of the summary report, click the **Submit** button at the bottom of the create summary report form to save your in-progress report and then follow the instructions to [create a configurable content block](/storm-center/configuration-guide/create-buttons). After you create the content block you want to use, return to the edit summary report form under Summary Reports and select the content block name from the **Summary Report Descriptions** drop-down field.
    + KUBRA recommends that this description be no more than 368 characters and only include text and links.
    + Hyperlinks must use a complete URL including the protocol. For example, `https://example.com`.
    + You can include click-to-call links for phone numbers in the header message using the link format `tel:5555555555`. This link format uses the 10-digit phone number, including area code but excluding country code.
    + On mobile screen sizes, the report description opens at the bottom of the report when the user selects a **Report Details** button at the bottom of the report.
1. Select one or more region files to use for the areas in the report.
1. If you want to merge data from multiple regions, click the **Merge Multiple Regions** checkbox. If you have only one region file, this option is not applicable.

### Data Fields and Labels ###

1. Select the data fields you want to include in the summary report. You can select a subset of the selected fields for desktop screen sizes to be shown on mobile screen sizes. The selected data fields will become columns on the summary report. For desktop, KUBRA recommends a maximum of six summary report columns, including the mandatory name column. For mobile, KUBRA recommends a maximum of four summary report columns, including the mandatory Name column. Field options are:
    + Customers Served
    + Customers Affected
    + Percentage Customers Affected
    + ETR - Estimated Restoration Time
    + Number of Outages
1. Enter field labels to be used for the report column headers for desktop and mobile browsers and for each language supported by the instance. Labels for mobile browsers should be shorter than labels for desktop browsers so they can be read on a narrow screen.
    + KUBRA recommends a maximum of 26 characters for the desktop label and a maximum of 10 characters for the mobile label.
    + You may need to adjust the length or formatting of the labels after testing them on a map to ensure that they display and wrap well.
1. To change the order of the report columns, click the up or down arrows under "Order." The order from top to bottom in the Summary Report form will become the order from left to right on the report.

{{% notice note %}}
The Name field will always be included as a column on the summary report. If the thematic type you selected for the report includes a hierarchy, you will also have the option to include the hierarchy name as a column on the report. For example, you can include a "State" column on a County report.
{{% /notice %}}

{{% notice tip %}}
You cannot include a column on a summary report for mobile screen sizes if you do not show that column for desktop screen sizes.
{{% /notice %}}

### Report Behavior Settings ###

1. If you want to include a filter field on the report that will allow users to find a specific area on the report by entering the name of the area, click the **Filter by Area Name** checkbox.
1. If you have a report that includes a hierarchy (parent-child relationships) and want to have the report open with all child items visible when the report loads, click the **Expand Tree on Load** checkbox.
1. If you do not want to limit the areas visible on the report for mobile browsers to areas with current outages, click the **Display Areas without Outages on Mobile** checkbox to set it to "on." This checkbox is "off" by default.
1. If you do not want to limit the areas visible on the report for desktop browsers to areas with current outages, click the **Display Areas without Outages on Desktop** checkbox to set it to "on." This checkbox is "on" by default.
1. If you want to include a button on the report that allows users to export a copy of the report data in CSV format, click the **Allow summary report to be exported** checkbox to set it to "on." This checkbox is "off" by default.
1. Use the Default Sort Field drop-down to select a data field to use for sorting the report. Options are "Name" and all of the data fields you selected to be included in the report.
1. Use the Default Sort Order drop-down to select whether to sort data on the report in ascending (Asc) or descending (Desc) order based on the Default Sort Field. For example, you can choose to sort the report by area Name in ascending order (A to Z) or you can choose to sort the report by number of outages in descending order (most outages to fewest outages).
1. If you want to create a tree format report that includes information based on a hierarchy of areas, use the drop-down lists under Tree Format Hierarchy to specify the starting and ending levels for the hierarchy. For example, selecting "State" as the starting hierarchy and "County" as the ending hierarchy will create a collapsible list of counties grouped by state.

#### Summary Report Export ####

If you include an **Export Data** button on a summary report, all users of a map that includes the summary report will see the **Export Data** button.

When a user clicks the Export Data button, the CSV file will include whatever data is visible on the summary report at that time in whatever order is shown on the summary report at that time.

For example, if the user has applied an area filter and has sorted the report in ascending order by area name, only the areas included in the filtered view will be included in the CSV file, and they will be in alphabetical order by area name. The language in the CSV file will match the language currently selected on the Storm Center map.

Summary report data files show each report row as a row in the CSV file. The first row of the CSV file includes the report column headers.

For Area columns with hierarchy, the CSV file will show headers based on the data file for the area. For example, a County summary report with a tree format hierarchy where State is the starting hierarchy and County Name is the ending hierarchy will show "County-1" as the header for the state names and "County-2" as the header for the county names.

The CSV file name will include the title of the summary report and the date and time of the Last Updated field on the summary report.

### ETR Settings ###

1. If you want to show expired estimated restoration time (ETR) values on the report, click the **Mask Expired ETR** checkbox to set it to "off." This checkbox is "on" by default. You may want to set this checkbox to "off" if you are creating an internal-facing map and want to see all ETRs as reported from the source system for outage data, for example.
1. Select an ETR Grouping Condition - options are "Latest ETR Any" and "Latest ETR All."
  + "Latest ETR Any" means that the map will display the latest ETR for outages in the area if **any** of the outages has a specific, valid ETR (not null or expired). If none of the outages in the area has a specific, valid ETR, the map will display the default message specified for null or expired ETRs in the [Data Labels](/storm-center/configuration-guide/create-data-labels) sub-section of the **Shared Resources** section.
  + "Latest ETR All" means that the map will display the latest ETR for outages in the area only if **all** of the outages have a specific, valid ETR (not null or expired). If any of the outages in the area has a null or expired ETR, the map will display the default message for null or expired ETRs.

### Totals Settings ###

1. If you want to show the total number of customers affected by active outages on the report, click the **Total Customers Affected** checkbox and enter a label to be used on the map for each language supported by the instance.
1. If you want to show the total number of customers served on the report, click the **Total Customers Served** checkbox and enter a label to be used on the map for each language supported by the instance.

### Customer Masking ###

1. If you want to mask the exact number of customers affected at or below a specific value, click the **Customer Masking** checkbox and then enter a number.
1. If you want to mask the exact percentage of customers affected at or below a specific value, click the **% Customer Masking** checkbox and then enter a number.

The values you enter for customer masking here will be combined with verbiage you enter in the **Shared Resources** section of the **Create New View** form to create a statement on the map such as "Fewer than 5" or "Less than 10%."

### Access Restriction ###

Select an access restriction policy. The options available in the drop-down come from the policies created in the **Access Restriction** section of the Instance Dashboard.
