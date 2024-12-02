---
title: "Deregistration Manager"
weight: 3
---

## What is the Notifi Deregistration Manager? ##

The Notifi Deregistration Manager is a microservice built to identify and deregister contacts in existing and future Notifi environments according to configurable rules. KUBRA created the Deregistration Manager to allow Notifi to manage large numbers of contacts while remaining compliant with recent FCC rulings on the TCPA and other regulations for sending automated messages to customers.

## Terms and Conditions - Managing Pending Contacts ##

By default, Notifi uses a double-opt-in process for new SMS and email contacts: when a new contact is added to the Notifi system, Notifi sends a confirmation message to the customer which asks the customer to respond. The response is used to confirm that the contact is valid and has been added to the system correctly. If the customer does not respond to the confirmation message, the contact is considered “pending,” and Notifi will not send any further messages to the contact.

To clean up backlogs of pending contacts and manage additional pending contacts on an ongoing basis, KUBRA has included rules for managing pending contacts in the Deregistration Manager.

### Feature Overview ###

To clean up the contact backlog, the Deregistration Manager first scans contacts in the data warehouse over a specified period of time and identifies pending contacts. The Deregistration Manager then creates an output file with the list of pending contacts as a report which KUBRA emails to the organization for review before the next step. After KUBRA receives approval from the organization, the Deregistration Manager submits a request to Notifi to deregister the pending contacts using the appropriate Profile API. Only this one-time cleanup of the contact backlog includes a review and approval process for deregistration.

To manage pending contacts on an ongoing basis, the Deregistration Manager scans contacts in the data warehouse over a specified period of time (daily by default) and creates a list of contacts added to the data warehouse at least one day before the start of the scan time that remain pending as of the scan time. The Deregistration Manager then submits a request to Notifi to re-send the confirmation message or send a follow-up message to the pending contacts.

The Deregistration Manager considers a contact to be pending and requests a follow-up message to the contact if one or more days have passed since the contact was added to the data warehouse. For example, if a scan runs on February 8, the Deregistration Manager will consider any contacts added on or before February 7 that have not responded to Terms and Conditions to be pending.

We have listed steps to show how Notifi handles pending registrations.

**Step 1**: The pending registrant becomes eligible for a follow-up message.

**Step 2**: They receive a follow-up message in 24 hours from when they become eligible.

**Step 3**: The follow-up message will wait 2 days for a response.

**Step 4**: If more than 2 days have passed after the follow-up message was sent, the Deregistration Manager will consider that message expired.

**Step 5**: The registrant will then need to retry registering themselves.

{{% notice note %}}
The Deregistration Manager does not send follow-up messages to contacts which initiated registration via two-way SMS. Notifi treats contacts which do not accept Terms and Conditions in two-way SMS as if the user had rejected the Terms and Conditions.
{{% /notice %}}

### Configuration Options ###

To clean up a backlog of pending contacts, an organization can set an end date for the Deregistration Manager to use for the initial search. To manage pending contacts on an ongoing basis, the organization can create and select one or more message templates for re-sending a confirmation message.

| Configuration | Definition | Default Value | Options |
| ------------- | ---------- | ------------- | ------- |
| Initial Review Period | The period of time for which contacts in the Notifi system will be reviewed to determine which contacts are pending and need to be deregistered from the system. The initial review includes all contacts registered on or before an end date. | Yesterday | The end date can be any value. |
| DND Time | A window during which Notifi will NOT send follow-up messages. | 8:00 pm to 8:00 am | This can be any time, must include a start time and end time, and is one setting for the entire implementation. |
| Follow-Up Message Text | The text of the message Notifi will use for confirmation follow-ups to pending contacts. | - | Text is needed for email and/or SMS text message templates. This can be the same text as the original confirmation message. Decide whether to include “Reply N to unsubscribe” language as part of the SMS follow-up template. |

## TCPA Compliance - Managing Disconnected Phone Numbers ##

The July 2015 FCC ruling on the TCPA includes a stringent set of rules around wrong numbers or reassigned numbers. Companies are only exempt from liability under the TCPA for one call to a mobile phone number that has been reassigned. The Notifi Preference Center tracks explicit registrations and subscriptions from customers, and Notifi message templates include opt-out options, which help reduce the risk of sending multiple messages to wrong or reassigned numbers. Because the entity sending messages is responsible for either obtaining permission from the new owner or removing the phone number from its list of contacts in cases where a phone number is reassigned, we also need a way to track and deregister these phone numbers.

To track phone numbers that become disconnected or change owners and deregister those phone numbers from Notifi, KUBRA has included rules for managing disconnected phone numbers in the Deregistration Manager.

### Feature Overview ###

The Deregistration Manager performs a daily scan to identify contacts added since the time of the last scan. The Deregistration Manager then submits the list of new contacts to a monitoring service. There may be a delay of up to 24 hours between the time a contact is registered and the time the contact is added to the list of monitored contacts.

The monitoring service tracks disconnect data from cellular service providers and sends a file back to the Deregistration Manager with a list of contacts that have been disconnected. Currently, the monitoring service tracks data from AT&T, Verizon, Sprint, T-Mobile, and US Cellular. The monitoring service will attempt to expand this list of carriers as data becomes available.

The Deregistration Manager matches the list of disconnected contacts to the appropriate Notifi implementation and submits a request to the Notifi implementation for those contacts to be deregistered using the appropriate Profile API. Notifi handles deregistrations requested by the Deactivation Manager in the same way as deregistrations requested by a customer.

### Configuration Options ###

There are no configurable features for the TCPA Compliance portion of the Deregistration Manager.

## Phone Number Lookup - Distinguishing Landline and Mobile Phone Numbers ##

Organizations with phone numbers in an existing customer information system sometimes want to register those phone numbers in Notifi to receive automated alerts by IVR (voice) or SMS (text). Notifi requires a contact to be associated with a communication channel, and SMS messages can only be sent to mobile phone numbers. Organizations that do not know whether the numbers in their systems are landline or mobile need a way to determine this information before they can register contacts for SMS messages.

The Deregistration Manager includes a real-time web service option which organizations can use to determine whether provided phone numbers are landline or mobile. The real-time phone type identification service is a web service that accepts SOAP or REST requests which include phone number data. The service returns whether the phone number type is landline (L) or mobile (W for “wireless”). The organization can then use this information to call the Notifi Profile web service to register the contact for IVR messages, SMS messages, or both, as desired and applicable.

### Configuration Options ###

There are no configurable features for the real-time phone number lookup service.
