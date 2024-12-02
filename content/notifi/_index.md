---
title: "Notifi"
url: notifi
type: index
weight: 1
---

## What is Notifi? ##

Notifi is KUBRA's automated alerts and preference management platform. Notifi uses business data from back-end systems to deliver messages to customers on a variety of communication channels according to customer preferences. Notifi also allows customers to request information and complete transactions such as outage reports and payment authorizations using automated SMS text conversations.

To put it another way, Notifi collects information about customers' communication preferences and then "listens in" on business activities to update customers when something happens which is of interest to them. Notifi can also retrieve information from other systems to answer customer questions or collect information from a customer to send to other systems to help a customer complete an account-related task.

The Notifi product uses a combination of single-tenant and multi-tenant architecture supported by Amazon Web Services (AWS). Although data is kept in shared data centers by AWS, KUBRA data is logically separated on virtualized hardware using AWS account management tools. Multi-tenant pieces of the Notifi architecture logically separate data using unique identifiers for each client. Access to all data managed by KUBRA is restricted using both the client identifier and permissions in user tokens. Our authentication vendor provides cryptographically signed user tokens to each user when the user signs in.

## Benefits of Notifi ##

| Benefits |  |
------ | -----------
Multiple alert types | Supports messages about bills, payments, account status, service requests, outages, and more
Multiple contact channels | Includes SMS text, email, voice, and app push notification
Single source of communication preferences | The Notifi Preference Center UI gives customers an easy way to add and manage contact information and alert preferences on desktop and mobile web browsers and in mobile apps for Android and iOS
Bilingual support | Customers can select English or Spanish preference for each contact (phone number, email address, or phone ID)
Robust administration tools | Notifi Management Console includes tools for sending ad hoc messages, temporarily pausing message delivery by type or channel, and reviewing system activity
Durable and scalable infrastructure | Amazon Web Services resources adjust to support user traffic while taking advantage of economies of scale

## Admin Tools ##

Notifi includes a management console UI with tools available to an organization's admin users. This management console provides a tool for [managing admin user accounts](/notifi/management-console/user-management). In addition, the Notifi product includes the following admin tools:

+ [Preferences](/notifi/management-console/preferences) — allows users to look up a customer account number and view a version of the Preference Center interface with the current contact and preference information for that account (users can also make changes to contact or preference information)
+ [History](/notifi/management-console/history) — shows a history of all messages sent and received by the Notifi system, searchable by Account, Contact, Alert Type, Delivery Method, or Delivery Status
+ [Broadcast](/notifi/management-console/broadcast) — allows users to create ad hoc email, voice, and/or SMS text messages and send them to all customers or to a selected user group (the Broadcast tool has the same available channels as the supported channels configured for the rest of the Notifi system)
+ [Template Manager](/notifi/management-console/template-manager/) — allows users to view and edit message templates for proactive messages and submit edits for review and promotion from development to test or from test to production
+ [Admin](/notifi/management-console/admin) — allows users to temporarily “mute” all messages or messages with a selected message type
+ [Reports](/notifi/management-console/reports) — shows graphs, charts, and tables with summary and timeline data of communications to customers
  + [Advanced Reporting](/notifi/management-console/advanced-reporting) — an optional addition to the Reports tool that allows users to view additional data, create custom reports, and schedule reports for delivery by email
+ [Enrollments](/notifi/management-console/enrollments) — allows users to look up a customer account number and see a list of all changes to enrollments for contacts registered to that account
