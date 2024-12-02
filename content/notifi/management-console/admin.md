---
title: "Admin"
weight: 9
---

The Notifi Admin tool allows you to manage some configurable features of the Notifi system related to outbound message delivery.

Your implementation may not include all of the settings described here, depending on the implementation's configuration.

## Optional Settings ##

### Real-Time Outage Status ###

Notifi supports two methods for retrieving outage status information: a web service call to the Outage Management System (OMS) or a check of the latest file in the Notifi Outage Hub.

When the real-time outage status toggle is set to **ON**, Notifi will make web service calls to the utility's OMS to retrieve outage status information.

When the real-time outage status toggle is set to **OFF**, Notifi will check the latest file in the Notifi Outage Hub to retrieve outage status information.

The real-time outage status toggle is set to **ON** by default. If you want to reduce the number of web service calls to the OMS (and reduce the overall load on the system), you can turn the real-time outage status toggle to **OFF**.

### Full Proactive Messaging ###

Notifi supports two methods for delivering outage status update messages: full proactive messaging and partial proactive messaging.

When the full proactive messaging toggle is set to **ON**, Notifi will send outage updates to all contacts of affected accounts enrolled to receive outage messages.

When the full proactive messaging toggle is set to **OFF**, Notifi will send outage updates to contacts of affected accounts enrolled to receive outage messages only when a customer associated with the account has reported an outage at their location. This is also known as partial proactive messaging.

### Conversation in Maintenance Mode ###

If a Notifi implementation includes both two-way SMS text messaging and web chat, the conversation in maintenance mode toggle will affect both channels.

When the conversation in maintenance mode toggle is set to **ON**, Notifi will respond to messages sent by customers to the Notifi system with the maintenance message template (a message that lets the customer know that the system is undergoing maintenance).

When the conversation in maintenance mode toggle is set to **OFF**, Notifi will respond to messages sent by customers with the appropriate template depending on the keyword sent by the customer or the detected customer intent.

The conversation in maintenance mode toggle is set to **OFF** by default.

## Mute Settings ##

You can use mute settings if you have bad data coming from a back-end system or for other temporary situations where you want to suppress messages sent from Notifi. When a mute setting is turned on, Notifi will still process data and generate messages for received events, but it will not send the message to recipients. Messages that are muted this way are **not** sent to recipients when the mute setting is turned off.

Mute settings only affect outbound or proactive messages from the Notifi system to customer contacts. To adjust messaging for two-way SMS text conversations, you must use the **Conversation in Maintenance Mode** toggle, if it is available for your implementation.

You can turn on the “Mute All” setting to stop all automated proactive messages, or you can turn on one of the other mute settings to mute

+ a specific message category,
+ all messages for a communication channel,
+ a specific type of outage status message, or
+ all messages for an operating company.

For example, turning on a “Mute Outage” setting will stop automated communications about outages, such as outage notifications, ETR updates, and restoration notifications.

To turn on a mute setting, click and drag the white button next to the setting you want to change from left to right. The button should move from the **OFF** position to the **ON** position.

To turn off a mute setting, click and drag the white button next to the setting you want to change from right to left. The button should move from the **ON** position to the **OFF** position.

### Mute System Pauses ###

If you turn on the "Mute System Pauses" setting, Notifi will stop sending messages to customers letting the customer know when other message types have been automatically paused.

Muting messages about automatic system pauses does not turn off the excessive messaging protection feature - messages to customer contacts will still be automatically paused according to the configured excessive messaging protection rules.
