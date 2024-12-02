---
title: "History"
weight: 5
---

The Notifi History tool provides a searchable history of all messages sent and received by the Notifi system.

{{% notice info %}}
The History tool retains data for up to 6 months. To review data older than 6 months, use the Reports tool.
{{% /notice %}}

## Access ##

Access to the History tool may require a second login using the same username and password you use for the Notifi Management Console.

The History tool may open in a new browser tab. You may need to close the tab and/or use the primary Notifi Management Console URL to access other Notifi management tools.

## Search for a Message or Conversation ##

You can search the conversation history by account number, phone number, email address, or message content.

{{% notice note %}}
The search feature does not support partial searches. Phone numbers must include the country code and area code with no symbols or spaces. For example: 15551234567.
{{% /notice %}}

The default search is "past 7 days." You can alternatively select "past 14 days" or "past 30 days," or you can set a specific date range.

You can also filter by channel, depending on the supported channels for your implementation:

+ Alexa
+ Email
+ Facebook
+ Google
+ IQ Chat - white-label web chat provided by KUBRA IQ
+ Push Notification - sent to an Android or iOS mobile app
+ Text Message
+ Twitter
+ Voice

By default, the History tool shows information for all environments or instances. You can select an environment/instance to view, such as Production, and the tool will remember your selection the next time you sign in. To find customer information, make sure you are looking at Production data.

## View Message Details ##

The list of messages shows contact information and a preview of the message content.

Conversations are separated into different entries in the History tool if more than 10 minutes pass between messages from the Notifi system and messages from a customer. Proactive messages always have their own entries in the History tool.

Select a message to see the contact, date sent, message content, and message status.

{{% notice note %}}
If a message in history is related to a contact that was not associated with any accounts at the time of the message, the Account field will show the message `No Associated Account`. This happens, for example, when a customer registers a new contact using two-way text messaging.
{{% /notice %}}

### Message Delivery Status ###

Notifi uses the following delivery status messages:

+ Accepted - The message was accepted by the message provider (Twilio, Twilio SendGrid, Apple Push Notification, Firebase Cloud Messaging, etc.).
+ Muted - The message was not delivered due to one of the situations described below, which will be shown under "Details" below each message:
  - Muted - An administrator muted the message category using the [Notifi Admin tool](/notifi/management-console/admin).
  - Auto Paused - [Excessive Messaging Protection](/notifi/features/excessive-messaging-protection) was triggered.
  - Paused - The contact owner requested that Notifi temporarily pause messages.
  - Obsolete - The message was deferred due to a Do Not Disturb period (either set by the customer or from an implementation-level configuration) and Notifi has a more recent message about the same event that will be sent at the end of the Do Not Disturb period. Messages marked as Obsolete will not be sent.
  - Expired - The message has been unable to be delivered within 48 hours. Messages marked as Expired will not be reattempted.
  - Bad Contact - The contact not both Enabled and Valid. Contacts may be marked invalid if previous messages have resulted in a "Permanent Failure" status.
  - Opted Out - The contact is on the Notifi opt-out list. Messages marked as Opted Out will not be sent to comply with the contact owner's wishes, telcom guidelines, and federal spam messaging regulations.
  - No Template - There may be a misconfiguration in Notifi and a valid template cannot be found for the notification's event type. Contact KUBRA support if this occurs.
  - Errors in Template - The template rendering service has errors. This may be due to either unexpected data in the event or an error in template design by KUBRA or any users with access to [Template Manager](/notifi/management-console/template-manager/). Contact KUBRA support for assistance.
  - No Studio Flow - There is a misconfiguration in the voice notification flow. Contact KUBRA support if this occurs.
  - Unexpected Failure - There was an uncaught exception within Notifi. Contact KUBRA support for assistance.
+ Permanent Failure - The message was not delivered and should not be retried. This can be caused by a spam report from the recipient, a hard bounce, or because the recipient unsubscribed.
+ Permanent Success - The message was delivered and/or opened.
+ Temporary Failure - The message was not delivered, but future messages to the contact may succeed. This can be caused by a full email inbox, for example.
+ Temporary Success - The message provider sent the message, but it has not yet been received.

In addition, the message history tool may show details sent by the message provider. For SMS text messages, there is a list of the possible values for these details in the {{<extlink title="Twilio support documentation" url="https://support.twilio.com/hc/en-us/articles/223134347-What-are-the-Possible-SMS-and-MMS-Message-Statuses-and-What-do-They-Mean-">}}. For email messages, there is a list of the possible values for these details in the {{<extlink title="SendGrid documentation" url="https://sendgrid.com/docs/ui/analytics-and-reporting/email-activity-feed/#types-of-email-activity-data">}}.

## Export Message Data or Resend a Message ##

There are two buttons: export message and resend. The **Export Message** button exports a CSV file with information about the message. The **Resend** button resends the message to the contact.

{{% notice note %}}
HTML content is rendered as "HTML text" in the message content section of the History tool.
{{% /notice %}}
