---
title: "Excessive Messaging Protection"
weight: 6
---

## Feature Information ##

Notifi provides excessive messaging protection to improve the customer experience by providing messaging caps in situations where too many messages are being sent to a customer.

If a customer contact (such as a phone number or email address) has been receiving a large number of messages, Notifi can be set to pause delivery of any further SMS or email messages for a set period of time to limit the total number of messages sent to a single contact. By default, Notifi considers more than 10 messages in 1 hour to be a large number of messages and stops delivery of further messages to the contact for 2 hours.

### Email and SMS Text Message Behavior ###

For email and SMS text messages, after the threshold is passed, Notifi sends a message to the contact indicating that the contact has been paused. SMS users can reply RESUME to continue receiving messages. Email users can click a link in the pause notification to continue receiving messages.

### Voice Message Behavior ###

For voice messages, after the threshold is passed, each additional voice message includes an option for the customer to pause delivery of further messages (for example, “press 3 to temporarily stop receiving calls from ABC Company”).

### Broadcast Message Behavior ###

For messages sent using the Notifi Broadcast tool, there is a configuration that stops additional messages to a specific contact after 1 message from a broadcast batch. All auto-pauses created for the broadcast batch are removed when the batch is completed.

### History and Reports Behavior ###

Messages that would have been sent to a contact during the pause period are not queued or re-delivered, but they are marked in the History tool and the Reports tool with a delivery status of “Auto Paused.”

## Configuration Options ##

To set up excessive messaging protection, an organization using Notifi must establish a list of message types to be considered for excessive messaging. This list can be either inclusive (listing messages to be considered) or exclusive (listing messages not to be considered). For example, outage messages can be configured so that they are excluded from excessive messaging protection.

If a message type is excluded from excessive messaging protection, messages of that type will not be counted toward the Excessive Messaging Threshold. However, when the Excessive Messaging Threshold is reached, all messages to the contact will be paused.

If a customer requests a pause for a contact, all proactive messages will be paused for the User Pause Duration or until the customer requests to resume receiving messages (whichever is sooner), regardless of any other excessive messaging configurations.

The following variables must be defined:

+ Excessive Messaging Duration - the period of time to be reviewed to determine if the number of messages sent to a contact is excessive.
  - Default Value - 1 hour
  - Options - any number of hours between 1 hour and 24 hours
+ Excessive Messaging Threshold - the number of messages a contact must receive within the Excessive Messaging Duration to be considered to be receiving excessive messages. All messages with message types that are configured to be considered for excessive messaging are counted when determining whether a contact has received excessive messages. After the Excessive Messaging Threshold is reached, Notifi will take action according to the contact channel. The same action will be applied to all messages, including messages with message types that are not counted toward the Excessive Messaging Threshold.
  - Default Value - 10 messages
  - Options - there is not currently a limitation on this value (it can be any number of messages)
+ System Pause Duration - the amount of time after the system generates a pause for excessive messaging that the pause expires (automatically resuming messaging).
  - Default Value - 2 hours
  - Options - there is not currently a limitation on this value - it can be a number of hours, or a set time such as “Next Day at 6:00 a.m.” However, this setting must be equal to or longer than the Excessive Messaging Duration. For example, if the Excessive Messaging Duration is set to 1 hour, the System Pause Duration must be at least 1 hour. As another example, if the System Pause Duration is set to “Next Day at 8:00 a.m.,” the Excessive Messaging Duration must not be more than 8 hours.
+ User Pause Duration - the amount of time after a user submits a PAUSE command that the pause expires (automatically resuming messaging).
  - Default Value - 24 hours
  - Options - there is not currently a limitation on this value (can be a number of hours or a set time, for example, the following day at 6:00 a.m.)

### Things to Consider to Configure Excessive Messaging Protection ###

The values for Excessive Messaging Duration, Excessive Messaging Threshold, and System Pause Duration need to be decided together, as they are used in combination to determine when and for how long to pause message delivery to a contact.

For example, you could choose to set the Excessive Messaging Duration to 3 hours, the Excessive Messaging Threshold to 10 messages, and the System Pause Duration to 4 hours. These choices would cause the Notifi system to pause message delivery to any contact that has received at least 10 messages in the past 3 hours, and then resume sending messages after the contact has been paused for 4 hours.

Setting a lower Excessive Messaging Duration, a lower Excessive Messaging Threshold, or both will cause more contacts to be paused more frequently, and setting a longer System Pause Duration will cause more messages to be held from delivery to contacts that are paused. The business decision to be made is based on the value of reducing message frequency versus the value of information in those messages.

User Pause Duration sets an upper limit on the duration of a pause requested by a customer. This feature is available to prevent a situation where a customer who texts the command PAUSE to temporarily stop receiving messages forgets to text the command RESUME to resume receiving messages. The business decision to be made is based on the desired time for a contact to be paused or kept from receiving alerts.
