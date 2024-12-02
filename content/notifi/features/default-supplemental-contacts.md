---
title: "Default and Supplemental Contacts"
weight: 4
---

## Feature Information ##

Notifi provides support for default and supplemental contacts to support messaging to contacts that customers have provided to an organization, even if those contacts have not been registered in the Notifi system.

Default contacts are used to send messages in cases where an account either does not have registered contacts in the Notifi system or does not have a subscription for the message category being sent. For example, Notifi can use default contacts to send messages such as scheduled outage notifications or outage alerts for critical care customers using the main phone number or email address on file for an account whenever there is not an existing subscription for outage messages in the Notifi system.

Supplemental contacts are used to send messages in addition to sending messages to registered contacts in the Notifi system. For example, Notifi can send an overdue bill notice to the main phone number and email address on file for an account in addition to any other contacts in the Notifi system.

Notifi will still block message delivery if a default contact or supplemental contact is on the system's opt-out list. However, the organization is required to abide by the TCPA, the CAN-SPAM Act, and any local regulations related to opt-in status when passing default and supplemental contact data to Notifi.

## Business Rule Options ##

The interaction between default contacts and supplemental contacts can be configured in one of two ways:

+ **Option 1 -** Supplemental contacts are processed before default contacts. In this option, if there is a registered and subscribed contact or a supplemental contact associated with an account, the default contact for that account will not be used.
+ **Option 2 -** Default contacts before supplemental contacts. In this option, if there are no registered and subscribed contacts for an account, both the default contact and the supplemental contact will be used.
