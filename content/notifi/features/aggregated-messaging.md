---
title: "Aggregated Messaging"
weight: 5
---

## Feature Information ##

Notifi provides aggregated messaging to improve the customer experience by eliminating multiple similar messages sent to a single contact as part of the same event.

For example, if a landlord is registered to receive outage notifications for all 50 units in an apartment building, and there is a power outage affecting the entire building, Notifi will detect that there is one contact associated with all 50 premise locations, and send one message to the contact.

Message template options for aggregated messages are configurable - for example, the message can include a list of all the affected addresses, a list of the affected addresses up to a certain number followed by the note “and more,” or a message variable that provides the number of affected addresses (for example, “50 locations”).

For the latest version of Notifi, the Broadcast tool does not aggregate messages. Instead, KUBRA uses a special configuration of the [Excessive Messaging Protection feature](/notifi/features/excessive-messaging-protection) to prevent multiple copies of a broadcast message from going to a single contact.

## Configuration Options ##

Message aggregation is limited either to event data sent in a single batch file, or to event data sent via web service that is labeled as a single batch.

Each organization using Notifi can choose to use message aggregation either for all message types, or only for specified message types. For example, an organization can choose to use aggregation for outage and billing messages but not for energy usage messages. For each message type to be implemented, the organization must decide whether or not the message type will be eligible for aggregation.

For each message type that is chosen to be eligible for aggregation, the organization must make some decisions related to the message template designs for both individual messages and aggregated messages. Designs must be considered for each supported communication channel and each supported language. For example, if outage alerts will be eligible for aggregation and the implementation supports email and SMS text messages, the organization must review and approve designs for an individual email message, an aggregated email message, an individual text message, and an aggregated text message.

Options for aggregated message templates include

+ listing all affected accounts
+ including language such as “Account XYZ and more”
+ including language such as “affecting X accounts”

In addition, the following variable must be defined:

+ Aggregated Messaging Candidacy Threshold - the number of accounts a contact must be associated with in the Notifi system for Notifi to attempt to aggregate eligible messages to that contact. Messages are aggregated only if they are part of a single data batch and have a message type that is configured to use message aggregation.
  - Default Value - 3 accounts
  - Options - there is not currently a limitation on this value (it can be any number of accounts)
