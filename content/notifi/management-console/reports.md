---
title: "Reports"
weight: 10
---

The Notifi Reports tool allows you to view statistical information about the performance of the Notifi system.

Dashboard configuration, ad hoc report creation, and scheduled report delivery are provided by the optional Advanced Reporting module. These features are described on the [Notifi Advanced Reporting page](/notifi/management-console/advanced-reporting).

## Standard Report Dashboards ##

There are up to seven standard dashboards available, depending on an organization's configuration:

+ **Registrations** – shows information about registrations over time, from different sources, by channel, by area, and by operating company (if applicable), as well as the number of pending registrations.
+ **Enrollment Audit** – shows information about the number of customer contacts opted in or opted out of messages by date and by message category.
+ **Enrollments** – shows information about the total number of customer contacts enrolled by channel, message category, and month as a running total.
+ **Messaging** – shows information about the number and type of messages sent and received by Notifi over time, by channel, by message category, and by delivery status.
+ **Account-Based Registrations** – shows information about the number of customer accounts with contacts registered to receive messages, trends in the number and type of contacts registered to an account, and trends in the number and type of contacts enrolled by message category.
+ **Billing** - shows information about the number and type of messages sent and received by Notifi, focused on messages counted for billing purposes. This dashboard includes a date filter that shows messages sent in the previous full month by default. This dashboard also includes an environment filter that shows messages from the test environment, the production environment, or both.
+ **Outage Summary** - shows information about outage messages including the number of outage notifications for each outage message template and the number of outage reporting (OUT) and outage status (STAT) conversations started and completed. For outage reporting, a completed conversation is labeled "reported out," and for outage status, a completed conversation is labeled either "valid response" for information provided about an existing outage or "report outage" for a response asking the customer if they want to report an outage.
+ **Broadcast Summary** - shows information about recent broadcasts grouped by broadcast name such as total messages sent, messages by channel, and processing time. The Broadcast Summary also includes a delivery summary breakdown.

## Report Dashboards for the Notifi Deregistration Manager ##

There are four additional dashboards related to the features provided by the [Notifi Deregistration Manager](/notifi/features/deregistration-manager/):

+ **Deregistrations** - shows information about contacts deregistered by the Notifi Deregistration Manager by day and by module (Terms & Conditions or TCPA).
+ **TCPA** - shows information about contacts being monitored for changes in ownership to comply with a TCPA ruling requiring companies to not send automated messages to contacts whose owners have not opted in.
+ **T&C Follow-Ups** - shows information about follow-up messages sent to contacts who have not responded to accept Terms and Conditions for messaging, as well as how many contacts have completed registration in response to a follow-up message.
+ **Phone Lookups** - shows information about the number of phone lookups completed and how many numbers are landline vs. mobile.

## View Reports ##

To select a dashboard, click the **Select Report** drop-down and then select one of the dashboard names.

{{% notice tip %}}
If you see a 401 error in the Reports tool, this means that your session has timed out. Sign out and sign back in to keep viewing reports.
{{% /notice %}}

### Filters ###

Each dashboard includes a **Filters** section. The filters allow you to sort the data in the dashboard by date, channel, location (county or city), Operating Company, or other information.

#### Date Filter ####

Some of the charts in each dashboard show information over a specific period of time. A date filter note in the **Filters** section at the top of the dashboard indicates the time period used for these charts.

For example, the note “Date Filter is in the past 30 days” indicates that the charts show information for the past 30 days, unless a specific chart indicates otherwise.

To select a different date range:

1. Click on the **Filters** section of the dashboard to view filter data.
2. In the Date Filter row, either change the number in the text box or adjust the drop-down values and the text box values to the desired date range. For example, you can view information that "is in the past 30 days," "is in range" from one specific date until before another specific date, or "is any time."
3. Click the **Run** button to refresh the report data.

#### Channel Filter ####

By default, charts show combined data for all supported communication channels. The Registrations, Enrollment Audit, Enrollments, Messaging, Billing, and Outage Summary dashboards include a channel filter.

To view data for a single channel:

1. Click on the **Filters** section of the dashboard.
2. In the Channel row, change the first drop-down value from "is any value" to "is."
3. Select the desired channel from the second drop-down list.
4. Click the **Run** button to refresh the report data.

#### Location Filters ####

The Registrations, Enrollments, Messaging, and Account-Based Registrations dashboards include filters by city and county. Use these filters to view data for a single city or county or for a group of cities or counties.

To view data for a single location:

1. Click on the **Filters** section of the dashboard.
2. In the City, County, or Zip Code row, enter the name of the location, after the drop-down field "is equal to."
3. Click the **Run** button to refresh the report data.

To view data for a group of locations:

1. Click on the **Filters** section of the dashboard.
2. In the City, County, or Zip Code row, enter the name of the location, after the drop-down field "is equal to."
3. Click the plus symbol to the right of the filter row to add another location name row.
4. Repeat steps 1-3 for each additional location you want to include.
5. Click the **Run** button to refresh the report data.

Location filters are only available if county and/or city data is provided to Notifi.

#### Operating Company Filter ####

By default, charts show combined data for all operating companies. The Registrations, Enrollments, Messaging, and Account-Based Registrations dashboards include an operating company filter. Use the Operating Company filter to view data for a single operating company or for a group of operating companies.

To view data for a single operating company:

1. Click on the **Filters** section of the dashboard.
2. In the Operating Company row, enter the name of the operating company, after the drop-down field "is equal to."
3. Click the **Run** button to refresh the report data.

To view data for a group of operating companies:

1. Click on the **Filters** section of the dashboard.
2. In the Operating Company row, enter the name of the operating company, after the drop-down field "is equal to."
3. Click the plus symbol to the right of the filter row to add another operating company name row.
4. Repeat steps 1-3 for each additional operating company you want to include.
5. Click the **Run** button to refresh the report data.

The operating company filter is only available if operating company data is provided to Notifi.

## Download Report Data ##

To download data for a report:

1. Hold the mouse cursor over the report.
2. Click the icon of three dots in a vertical line
3. Click the **Download Data...** option.

You can download report data in TXT, Excel (2007 or later), CSV, JSON, HTML, Markdown, or PNG format.

To download an entire dashboard, click the gear icon in the upper right corner of the dashboard. You can either download the dashboard as a PDF file or as a set of CSV files.

## Dashboard Descriptions ##

### Registrations Dashboard ###

You can use the Registrations dashboard to answer questions such as

+ How have registrations grown over time?
+ Where do most registered customers live?
+ Which channel or channels are customers using the most?
+ How are customers registering for alerts?

### Enrollment Audit Dashboard ###

You can use the Enrollment Audit dashboard to answer questions such as

+ How does the rate of opt-ins compare to the rate of opt-outs?
+ Which categories were the most popular in the past month?
+ How is the relative popularity of categories changing over time?

### Enrollments Dashboard ###

You can use the Enrollments dashboard to answer questions such as

+ How many customer contacts are enrolled to receive outage alerts?
+ How has the number of enrollments grown over time?
+ Are there differences in the channels customers choose for different message categories?

### Messaging Dashboard ###

You can use the Messaging dashboard to answer questions such as

+ How many messages were processed by the system last month?
+ How many messages were processed by the system in the last calendar year?
+ Which message category is the most popular?
+ What is the success rate for message delivery?

### Account-Based Registrations Dashboard ###

You can use the Account-Based Registrations dashboard to answer questions such as

+ What is the most popular combination of contact channels to register?
+ How many customer accounts are registered for messages?
+ What is the most popular number of contacts to register?
+ How many email contacts are enrolled in usage alerts?

### Billing Dashboard ###

You can use the Billing dashboard to answer questions such as

+ How many billable messages were sent last month?
+ How many of the messages sent last month were text messages?
+ How many of the messages sent last month were Outage Update messages?
+ How many of the messages sent last month were related to two-way text messaging conversations?

{{% notice tip %}}
To view data for a specific month, enter the month in YYYY-MM format. For example, if you want to view data for June 2020, the date filter should read `Sent Date matches (advanced) 2020-06.`
{{% /notice %}}

Billing for two-way text messaging conversations is tracked per session, while billing for proactive messages is tracked per message.

### Outage Summary Dashboard ###

You can use the Outages dashboard to answer questions such as

+ How many outage notifications have been sent in the past week?
+ How many two-way text messaging conversations asking for outage status were started?
+ How many two-way text messaging conversations asking for outage status resulted in an outage report?
+ How many two-way text messaging conversations about outage reports were completed successfully?

### Deregistrations Dashboard ###

You can use the Deregistrations dashboard to answer questions such as

+ How many contacts have been deregistered by the Notifi Deregistration Manager in the past month?
+ How many SMS contacts have been deregistered due to a change of ownership?
+ What percentage of deregistrations by the Notifi Deregistration Manager are due to a lack of response to Terms & Conditions?

### TCPA Dashboard ###

You can use the TCPA dashboard to answer questions such as

+ How many contacts were added to TCPA monitoring in the past month?
+ How long have contacts being monitored by the Notifi Deregistration Manager been in service?

### Terms & Conditions Follow-Ups Dashboard ###

You can use the Terms & Conditions Follow-Ups dashboard to answer questions such as

+ How many follow-up messages were sent in the past month to customers who did not complete contact registration?
+ How many follow-up messages resulted in completed registrations?
+ Which channel has the most completed registrations due to follow-up messages?

### Phone Lookups Dashboard ###

You can use the Phone Lookups dashboard to answer questions such as

+ How many phone lookups have been completed in the past month?
+ How many phone lookups have been completed per day for the past week?
+ How many of the phone numbers we have looked up are wireless numbers?
