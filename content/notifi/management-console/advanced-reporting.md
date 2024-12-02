---
title: "Notifi Advanced Reporting"
weight: 11
---

The Notifi Advanced Reporting module expands the features offered by the [Reports tool](/notifi/management-console/reports) to allow authorized users to

+ drill down to view detailed data for reports in the standard dashboards
+ create new reports
+ add new reports to new dashboards or to existing dashboards
+ schedule report data to be delivered via email
+ export report data

{{% notice note %}}
For more training on Advanced Reporting, refer to the **Data Consumer** and **LookML Developer** sections on [Looker training](https://connect.looker.com/learning).
{{% /notice %}}

## Access ##

If your organization has access to the Advanced Reporting module, you can access Advanced Reporting features in the Reports tool of the Notifi Management Console.

If your organization does not have access to the Advanced Reporting module, you can contact your KUBRA client success manager to discuss options for adding the module to your Notifi implementation.

## Advanced Reporting Explorer ##

The Explorer feature of the Reports tool allows you to create custom reports based on the data available from the Notifi system.

There are up to five explorer options available, depending on an organization's configuration:

+ **Messaging** – includes data options related to delivery status and aspects of individual messages, such as the account number, channel, contact, category, and type.
+ **Registrations & Enrollments** – includes data options related to customer location, enrollments, accounts, contacts, and registrations.
+ **Registrations (Account Focused)** – includes data options related to customer location, accounts, and registrations.
+ **Enrollments (Account Focused)** – includes data options related to customer location, accounts, and enrollments.
+ **Enrollment Audit** – includes data options related to enrollments such as the account number, contact, date, and source of enrollment.

To select an explorer option, click on the **Select Report** drop-down and then click on one of the explorer names.

In the Explore section, data is divided into Dimensions, which are data elements from the Notifi database, and Measures, which are computations on a group of records with a common Dimension.

## Create a New Report ##

To create a new report, select one Measure and at least one Dimension. When you select multiple Dimensions, you can choose the Pivot setting for one of the Dimensions to display that Dimension horizontally on a pivot chart.

You can also add filters to restrict the data displayed in the table. To sort the data in the table, click on a column header. To sort by multiple columns, hold the **Shift** key while clicking each column header in the order by which you want to sort the data.

For example, a table that lists the number of messages sent via email and text message over the past week, separated by receipt status and channel, would use the following selections:

+ Main Dimension – Receipt Status
+ Pivot Dimension – Channel
+ Measure – Number of Messages
+ Filter – Receipt Date is in the past 7 days

To see details about the records associated with any data point in the table, click on the number in the table. For example, clicking on the number of Delivered Voice messages from the example table in the image above opens a new table (shown below with data sorted by **Message Sent Time** from newest to oldest).

You can also view the table data as a chart by clicking on the **Visualization** tab and selecting a chart type from the available options, such as Column, Scatterplot, Line, Area, or Pie. Click **Chart Settings** to adjust the number of charts displayed in a row, to change the colors used for the chart, or to show or hide the chart legend.

## Schedule a Report ##

To schedule a report to be delivered via email or to an external program, click the gear icon at the upper right corner of the Explore section and then click the **Save & Schedule...** button.

In the form that opens, enter a title for the report. You can also enter a description for the report. When you are ready to save the report, click the **Save & View Look** button.

After you save the report, a window will open with options for selecting when to send the report, how often to repeat the report delivery, how to send the report, and the file format for the scheduled report delivery.

You can schedule reports to be emailed every minute or hourly, daily, weekly, or monthly. The options for when to send the report will depend on the delivery frequency you choose. For example, if you choose to send the report weekly, you can choose the day of the week and the time of day at which to send the report. If you choose to send the report daily, you can choose to send the report every day, only on weekdays, or only on specific days, which will allow you to send a report on Monday, Wednesday, and Friday, for example.

You can send reports to an Amazon S3 bucket, to one or more email addresses, to an SFTP address, or to a webhook address.

You can send the report in different formats depending on the destination. If you choose to send the report via email, you can send it inline as an HTML table or image, or you can send it as an attachment in HTML, Text, CSV, JSON, or XSLX format.

You can choose to send a report if there are results, if there are not results, or both. You can also choose to only send a report if there are results and the results have changed since the last time the report was run.

## Add a Custom Report to a Dashboard ##

To add a report you created in the Explore section to a report dashboard, click the gear icon at the upper right corner of the Explore section and then click the **Save & Add to Dashboard...** button.

In the form that opens, enter a title for the report. You can also enter a description for the report. When you are ready to save the report, click the **Save & View Look** button.

If you have not created a dashboard before, click the **New Dashboard** button and then enter a name for the new dashboard. If you have created a dashboard before, you can select the dashboard name and then click the **Add** button to add the report to that dashboard.

## Download Data ##

To download a custom report, click the gear icon at the upper right corner of the Explore section and then click the **Download...** button.

You can download report data in TXT, Excel, CSV, JSON, HTML, Markdown, or PNG format. Download settings allow you to limit the number of rows or columns in the exported file. The maximum number of rows that can be viewed in the Reports tool is 5000 rows.

{{% notice note %}}
KUBRA recommends that you limit downloads to a maximum of one month of data at a time.
{{% /notice %}}
