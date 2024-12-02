---
title: "Feature List"
type: index
weight: 2
---

## Communication Channels ##

Notifi supports SMS text messages, email messages, text-to-speech or prerecorded voice messages, and push notifications for Android and iOS mobile apps.

### Two-Way Communication ###

The latest version of Notifi uses natural language processing to identify a user's intent from the word or words the user sends to the system. This means that users can either use keywords or complete sentences to request information or complete supported tasks.

## Message Categories ##

Notifi supports a wide variety of message categories for both proactive messages (one-way) and interactive automated conversations (two-way).

### Account Messages ###

Proactive message types for account messages include

+ Contact Information Updated
+ New Contact Registration
+ Start Service Confirmation
+ Stop Service Confirmation
+ New Contact Confirmation
+ New Contact Affirmation

Two-way message topics for account messages include

+ REG or JOIN - register a new contact
+ SUB - add a message category subscription to a contact
+ NICK - add a nickname for an account
+ HELP - request a list of valid SMS keywords
+ STOP or CANCEL - unsubscribe from one or all message categories
+ PAUSE/RESUME - stop/restart proactive message delivery to the contact

### Billing and Payment Messages ###

Proactive message types for billing and payment messages include

+ Statement Available
+ Bill Due
+ Payment Processed - Success
+ Payment Processed - Failure
+ Payment Overdue
+ Disconnect Pending
+ Balance Billing Adjustment
+ Critical Peak Pricing Alert
+ Threshold Balance Alert

Two-way message topics for billing and payment messages include

+ BAL - request current account balance
+ PAY - authorize payment (using payment method on file)

### Prepaid Account Messages ###

Proactive message types for prepaid account messages include

+ Annual Program Confirmation
+ Program Enrollment Confirmation
+ Program Cancellation
+ Low Balance
+ Payment Confirmation
+ Payment Reversal
+ Disconnect Pending
+ Disconnect Completed
+ Payment Confirmation - Sufficient Amount
+ Payment Confirmation - Insufficient Amount
+ Weekly Bill-to-Date

### Outage Messages ###

Proactive message types for outage messages include

+ Outage Detected
+ Outage Updated (estimated restoration time, crew status, cause)
+ Outage Restored
+ Severe Weather Alert
+ Planned Outage Alert

Two-way message topics for outage messages include

+ OUT - report an outage (for the user's account)
+ STAT - request the status of an outage affecting the user's account

### Usage Messages ###

Proactive message types for usage messages include

+ Weekly Usage Summary
+ Threshold Usage Alert

Two-way message topics for usage messages include

+ USE - request current usage information

### Other Message Categories ###

KUBRA can configure additional message categories and templates for the Notifi system as part of an implementation project.

## Preference Center ##

The Notifi Preference Center UI is designed to integrate with a "My Account" web portal. Customers who sign in and access the Preference Center can add new contact information, remove contacts, and manage preferences and settings for existing contacts.

Users can opt in or opt out of message categories for each contact registered to an account. They can also provide a language preference for each contact and set a Do Not Disturb period for each contact.

Some message categories have additional settings, such as bill due date thresholds, cost thresholds, or usage thresholds. Users can set these thresholds by account; the same setting applies for all contacts registered to the account and enrolled to receive the message category.

## Business Rules ##

### Default and Supplemental Contacts ###

Notifi supports default contacts and supplemental contacts, which handle messaging in situations outside of the typical opt in. Default contacts are used in cases where an account does not have registered contacts in the Notifi system, or where an account does not have an enrollment for the message category being sent. Supplemental contacts are used in addition to the customer contacts registered in the Notifi system.

{{% notice note %}}
The organization using the Notifi system is required to abide by the TCPA, the CAN-SPAM Act, and any local regulations with respect to opt-in status when passing default and supplemental contacts to the Notifi system for message delivery.
{{% /notice %}}

For more information, see the [Default and Supplemental Contacts page](/notifi/features/default-supplemental-contacts) page.

### Aggregated Messaging ###

Notifi provides aggregated messaging designed to improve the customer experience by eliminating overly similar messages sent to a single contact. Message aggregation is limited to event data sent in a single batch file, or to event data sent via web service and labeled as a single data batch.

For more information, see the [Aggregated Messaging page](/notifi/features/aggregated-messaging).

### Excessive Messaging Protection ###

Notifi provides excessive messaging protection designed to improve the customer experience by providing messaging caps for messages to a customer contact. KUBRA can configure Notifi to pause delivery of further SMS or email messages for a set period of time after a specific contact receives more than a specified number of messages in a specified time window (such as more than 10 messages in one hour).

For voice messages, additional messages over the configured threshold include an option for the customer to pause delivery of further messages (for example, "press 1 to temporarily stop receiving calls from ABC Company").

For more information, see the [Excessive Messaging Protection page](/notifi/features/excessive-messaging-protection).

### ETR Change for Outage Alert ###

KUBRA can configure how large of a change in estimated restoration time is needed to send an outage update message to customers.

## Additional Cost Modules ##

### High-Capacity Voice Message Delivery ###

KUBRA provides options for increasing voice message delivery to between 15 and 30 new calls started per second depending on implementation requirements.

### Advanced Reporting ###

The [Notifi Advanced Reporting](/notifi/management-console/advanced-reporting) module includes 10 user licenses and adds support for additional features and access in the Reports admin tool. Additional features include custom report creation and report scheduling and delivery options.

KUBRA also provides additional user licenses for Advanced Reporting in sets of 10.

For more information on the difference between our Standard and Advanced Reporting options, see the [Standard and Advanced Reporting page](/notifi/features/standard-advanced-reporting).

### Mobile App SDK ###

KUBRA provides a Notifi Mobile App SDK for integrating Notifi preference management features with native mobile apps for Android and iOS. The SDK can be licensed for use with KUBRA iMobile apps or with third-party apps.

### Notifi Deregistration Manager ###

The Notifi Deregistration Manager service identifies and deregisters contacts in Notifi environments according to configurable rules. The Deregistration Manager currently includes features for managing unconfirmed contacts, managing disconnected or reassigned phone numbers, and distinguishing between landline and mobile devices by phone number.

For more information, see the [Notifi Deregistration Manager page](/notifi/features/deregistration-manager).
