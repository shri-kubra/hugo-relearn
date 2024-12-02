---
title: "Enrollments"
weight: 12
---

The Notifi Enrollments tool allows you to look up a customer account and view a list of all changes to enrollments for contacts registered to that account.

You can use the Enrollments tool to view:

+ The type and number of enrollments for a specific account
+ When a specific enrollment was created
+ If the email address or phone number for a specific account is correct (in response to a customer call, for example)
+ How many and what kind of enrollments were created for a specific account on a specific date or over a range of dates

## Search for an Account ##

To see information in the Enrollments tool, you must enter an account number in the **Search** bar at the top of the tool. All actions related to enrollments associated with that account will appear in the table below the search bar after you click the **Search** button.

## Enrollment Audit Column Descriptions ##

+ **Contact** – The contact value (email address or phone number) for the modified enrollment.
+ **Principal** – The user who made the change. This value can be overridden on the Preference Center interface by passing in a `principal` parameter.
+ **Source** – The location where the change was made. This will be one of the following values:
	+ **ALEXA** – user requested the change during a conversation on an Alexa-enabled device
	+ **APN_FEEDBACK** - the change was made based on feedback from Apple regarding an iOS device
	+ **CALLBACK** – the change was made based on feedback from the message aggregator (for example, because the phone number is invalid)
	+ **CSR** - the change was made using a CSR-specific UI
	+ **DB_DIRECT** – the record was inserted manually
	+ **EMAIL** – user requested the change by clicking a link in an email message
	+ **FACEBOOK** – user requested the change during a conversation on Facebook Messenger
	+ **FCM** – the change was made based on feedback from Google regarding an Android device enrolled after the transition to Firebase Cloud Messaging (FCM)
	+ **GCM** - the change was made based on feedback from Google regarding an Android device enrolled before the transition to Firebase Cloud Messaging (FCM)
	+ **GOOGLE** – user requested the change during a conversation with a Google Assistant-enabled device
	+ **INIT_LOAD** – the record was part of an initial load of enrollments requested by the organization
	+ **IQ CHAT** – user requested the change during a conversation with the whitelabel web chat bot
	+ **IVR** – user requested the change during a voice call
	+ **MOBILE_CHECK_IN** - the change was made by a mobile app without an associated messaging type (either Apple or Android); this is used if the token associated with the device needs to be updated
	+ **NOTIFICATION_ENGINE** - the change was made by the Notifi notification processor
	+ **PROVIDER** - the change was made based on feedback from the message aggregator
	+ **SMS** – user requested the change via two-way text messaging
	+ **SOAP** – the change was made via a web service call
	+ **TWITTER** – user requested the change during a private message conversation on Twitter
	+ **UNKNOWN** – the source of the change is unknown
	+ **WEB** – the change was made using the Preference Center interface
+ **Action** – The action that occurred. This will be one of the following values:
  + **DELETE** – the enrollment was removed (aka opt-out)
  + **INSERT** – the enrollment was created (aka opt-in)
  + **UPDATE** – the enrollment was modified
+ **Channel** – The channel of the modified enrollment (SMS, E_MAIL, VOICE, or PUSH).
+ **Program** – The name of the program for which the enrollment was modified.
+ **Created** – The date and time when the event happened.
