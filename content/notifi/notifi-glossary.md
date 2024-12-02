---
title: "Notifi Glossary of Terms"
weight: 14
---

This page provides a list of terms and definitions related to the KUBRA Notifi product.

| Term | Definition |
| ---- | ---------- |
| Account | A utility or organization account, identified by an account number supplied by the utility or other organization. There is typically one account per premises. |
| Advanced Reporting | An optional Notifi module that provides options for authorized admin users to create and share customizable charts and reports about customer activities. See the [Notifi Advanced Reporting page](/notifi/management-console/advanced-reporting) for more information. |
| Affirmation | An informative message that tells the recipient that a contact has been successfully associated with an account. No action from the recipient is required in response to the message. |
| Aggregated Message | A message that is created and sent to a contact about one event or a set of similar events that affects multiple accounts for which the contact is registered and enrolled to receive messages. |
| Aggregated Messaging | A Notifi feature where the system combines multiple messages which are part of the same batch of events if they are directed to one contact. Messages are eligible for aggregation if they have the same event data (estimated restoration time, message text, etc.) but different account information (address, account number, etc.) and if there is an aggregated message template for the event type. See the [Aggregated Messaging page](/notifi/features/aggregated-messaging) for more information. |
| Back-End Systems | Refers to the systems Notifi integrates with, such as an Outage Management System, Customer Information System, Customer Relationship Management System, or Meter Data Management System. |
| Blocklist | A list containing invalid email addresses or other contacts. Blocklists are sometimes used to reject email messages at the server level before the message is delivered to an inbox. The opposite is an Allowlist. |
| Broadcast | A type of message created using the Notifi Broadcast tool, as opposed to a Transactional Message, which is triggered by an event or a customer message. In Notifi reporting, broadcast messages are grouped with proactive messages. |
| Channel | A method of communication, such as email, text message (SMS), voice message, push notification (Android/iOS), or smart speaker. |
| Confirmation | A message that requests a reply from the recipient to confirm the association of a contact with an account. This is used to confirm that the contact owner is aware of and approves the registration. |
| Contact | Individual contact information, such as a phone number or email address, used to receive messages on one channel. Notifi counts each channel as a separate contact. For example, if one phone number is used for both text messages and voice messages, Notifi counts this as two contacts: one contact for text messages and one contact for voice messages. |
| Dashboard | A set of charts and tables available to users of the Reports tool in the Notifi Management Console. |
| Default and Supplemental Contacts | A Notifi feature that allows a broadcast file upload or an event submission to include default contacts, supplemental contacts, or both as recipients for messages. See the [Default and Supplemental Contacts page](/notifi/features/default-supplemental-contacts) for more information. |
| Default Contact | A contact that is not registered in the Notifi preferences database that is used to send messages to a recipient if there are no registered contacts for an account, or if there are no enrollments for the message type being sent. |
| Delivery Status | The current state of a message sent from the Notifi system. See the [History tool page](/notifi/management-console/history/#message-delivery-status) for information about specific delivery status values. |
| Eligibility | The state of being qualified to receive a specific message type or message category. For example, an organization can decide that only accounts with smart meters are eligible to receive demand response messages. |
| Enrollment | The association of a contact with a message category. The enrollment also includes Do Not Disturb settings for the specific contact and message category. For example, a customer can request outage messages by SMS text and set a Do Not Disturb period of 9 p.m. to 6 a.m. A contact must have an active registration to create an enrollment. |
| Event | An action occurring in a back-end system that is of interest to customers and triggers a related message. For example, an update to the estimated restoration time for an outage is an event which can trigger an outage update message, and a customer statement being finalized for the month is an event which can trigger a statement ready message. |
| Excessive Messaging | A situation that leads to a contact receiving more messages than might be ideal from a customer experience perspective. If a Notifi implementation has Excessive Messaging Protection thresholds set, this situation can result in a contact being auto-paused for a set period of time. |
| Individual Message | A standard message sent to one contact about one event related to one account, as opposed to an aggregated message. |
| Management Console | The user interface for utility or organization administrators. |
| Message | A single transmission sent or received by Notifi, such as an email, text message, voice message, or push notification. |
| Message Category (also called Program) | A set of related message templates. The templates can be either proactive messages or content for an automated two-way conversation. For proactive alerts, a category is a set of message templates which are grouped together to allow a user to request to receive them as part of a single enrollment, such as Billing messages or Outage messages. For two-way conversations, the initial keyword or message from the user and all related responses from the Notifi system are a single message category. |
| Message Group | A set of proactive and two-way Message Categories related by topic, used for analytics. For example, outage messages and two-way outage reports and status requests are one message group, and billing & payment messages and two-way bill payment authorizations and balance requests are another message group. |
| Message Template | A combination of text and variables that Notifi uses to produce a message. There are separate message templates for each message type and each communication channel. For example, an "outage detected" text message template, an "outage reported" voice message template, or an "ETR update" email message template. |
| Message Type | A classification of messages by subject. For example, bill available, ETR updated, power restored, or payment successful. |
| Messages Received | Refers to incoming messages or messages originating from a customer. In SMS, this is also known as Mobile Originated or MO. |
| Messages Sent | Refers to messages originating in Notifi. In SMS, this is also known as Mobile Terminated or MT. |
| Nickname | A short name or text label applied by a customer to an account or contact. |
| Opt-In | The start of an enrollment, when a customer asks to receive messages. |
| Opt-Out | The end of an enrollment, when a customer asks to stop receiving messages. |
| Opt-Out List | A list containing contacts that have been opted out of receiving messages from Notifi. Both the contact and the message type for the opt-out are recorded, which means that a contact can be opted out of some message types while still receiving other message types from Notifi. Notifi checks default contacts and supplemental contacts against this list before sending messages. If a contact is on the opt-out list, Notifi will not send a message to that contact. |
| Pause | A Notifi feature where the system temporarily does not send messages to a contact, either because the contact owner requested a pause or due to detected excessive messaging. A pause implemented due to excessive messaging is also called an auto pause. |
| Preferences | The set of contacts, messaging settings, and enrollments associated with an account. |
| Proactive Message | A message sent from Notifi that is triggered by an event, as opposed to a message received from a customer or a message sent in response to a customer message. |
| Push Notification | A message sent to a specific mobile app. |
| Registration | The association of a confirmed contact with a valid account. For example, a registration is created when a customer adds an email address using the Notifi preference center UI. |
| Pending registration | Pending registrations happen when a contact owner has not completed the registration process. For example, if a customer has not completed the double opt-in process for SMS by responding to a confirmation message, the SMS contact's registration will be considered pending. |
| Registration Source | The origin of a registration. Possible sources include website, initial load, text message, and mobile app. Not all Notifi implementations include all possible registration sources. |
| Supplemental Contact | A contact that is not registered in the Notifi preferences database that is used in addition to any registered contacts for the message type being sent. |
| Two-Way Messaging | SMS message conversations started by the customer using an SMS keyword (such as OUT, STAT, or BAL) or a natural language message that indicates a supported intent. The initial message from the customer and all related messages between the customer and Notifi for the same intent are considered part of a single message category. |
