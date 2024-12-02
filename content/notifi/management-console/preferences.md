---
title: "Preferences"
weight: 6
---

The Notifi Preferences tool allows you to look up a customer account to view or edit the customer's communication preferences.

Enter an account number in the search bar and press **Enter** or click the **Search** button to view Notifi preference center information for that account.

{{% notice note %}}
If you are comparing information between the Preferences tool and the History tool, make sure you are looking at the same environment for both (test, production, etc.).
{{% /notice %}}

## Initial View ##

If there are no registered contacts in Notifi for the account, the initial view shows the **Add a Contact** form.

If there are registered contacts in Notifi for the account, the initial view shows a list of available message types with a drop-down list of registered contacts at the top of the screen.

If an account is not eligible for one or more message types, those message types will not be visible in the preference center or in the Preferences tool.

## Add a Contact ##

To add a new contact for an account with registered contacts, click the plus sign icon at the top right of the screen. The icon will change to show the word **Add** when you hold your mouse cursor over it.

You can also click the drop-down to the right of the contact information at the top of the screen and select **Add a new contact** to open the **Add a Contact** form.

In the **Add a Contact** form, you may be able to use information on file for a new contact. Click the drop-down next to the **Select a contact** field to see a list of contacts on file for the account. Select the contact you want and then enter a Contact Name.

To create a new contact:

1. Select the Contact Method you want from the options below the **Add a New Contact** text - Email, Text, or Voice.
2. Enter the email address or phone number. You may need to enter the contact information twice. This helps to prevent typing errors.
3. Enter a Contact Name.
4. (Optional) Choose Do Not Disturb settings.
5. (Optional) Choose a language to use for messages to the contact.
6. Review and accept the Terms of Use.
7. Click the **Submit** button.

### Voice and Text Contacts ###

You can use the same mobile phone number for both Voice and Text messages, but Notifi treats these as two separate contacts, one contact for each contact method.

This allows a phone number owner to receive bill reminders as voice messages and outage alerts as text messages, for example.

### Do Not Disturb Settings ###

If there is a regular period of time during which the contact owner does not want to receive alerts, such as while they are asleep, you can set a do not disturb period for the contact.

To set a Do Not Disturb period:

1. Click the **Start** field.
2. Use the arrows to select a start time.
3. Click the **Done** button.
4. Click the **End** field.
5. Use the arrows to select an end time.
6. Click the **Done** button.

If you do not select a start time and an end time for a Do Not Disturb period, messages may be sent to the contact at any time of day.

If the contact owner wants to receive messages related to electrical outages even during the Do Not Disturb period, click the checkbox next to the message "Disregard DO NOT DISTURB preference for OUTAGE notifications and alerts."

### Language Settings ###

If the Notifi implementation supports more than one language, you can choose which language to use for messages to each contact.

To choose a language, click the radio button next to the name of the language.

### Terms of Use ###

You must click the checkbox next to the sentence "I have read and agree to the terms of use." to accept the Terms of Use for the Notifi messaging system and save a new contact. Click on the **terms of use** text to open a pop-up window or a new browser tab with the Terms of Use document.

### Confirmation Messages ###

When you enter and save a Text or Email contact for the first time, the Notifi messaging system may send a Confirmation Message to the contact. The owner of the contact must respond to the Confirmation Message before the messaging system will send messages to that contact.

If an account has one or more contacts that have not been verified using a Confirmation Message, you will see a note at the top of the preference center indicating that the contact is unverified. If you need to re-send a Confirmation Message, click the **Resend message** text in the note.

## Edit a Contact ##

To edit information for an existing contact, click the **Edit** button (gear icon) to the left of the contact information at the top of the screen.

In the **Edit Contact** form, you can change the Contact Name, the Do Not Disturb settings, or the Language Settings for the contact.

To save your changes, click the **Submit** button.

### Re-Confirm a Contact ###

If a message to a contact experiences a hard bounce, Notifi sets the contact back to an unverified state. In the Preferences UI, this looks the same as a contact that has been added for the first time and has not yet been verified. An unverified contact will not receive any messages from Notifi.

![Contact drop-down list with unverified contact](/images/preferences-contact-dropdown-unverified.png)

In this example, the red dot next to the text message icon for **Mobile2** indicates that contact **Mobile2** is unverified.

To re-verify a contact and allow it to start receiving messages again, select the contact from the contacts drop-down list and then click the **Resend message** text in the banner to send a new confirmation message.

![Resend message prompt for an unverified contact](/images/preferences-unverified-contact-resend-message.png)

When the contact owner responds to the confirmation message, the contact will be re-verified and will be able to receive messages according to its preference settings.

## Delete a Contact ##

To delete a contact:

1. Click the **Edit** button (gear icon) to the left of the contact information at the top of the preference center screen.
2. In the **Edit Contact** form, click the **Delete Contact** button.
3. Click **OK** to confirm the delete action.

## Enroll a Contact to Receive Messages ##

To enroll a specific contact for a specific message type:

1. Select the desired contact from the drop-down list at the top of the preference center screen.
2. Click the toggle next to the desired message type to change it from the **OFF** setting (red with X visible) to the **ON** setting (green with check mark visible).

### Message Type Settings and Enrollments by Message Type ###

Some message types have additional preference settings. These settings are indicated by an icon with a note under the description for the message type. For example, a Payment Due message type can have an additional setting for the number of days before the due date that the message will be sent.

To adjust these additional message type settings:

1. Click the message description.
2. Enter or select the setting option (such as a number of days).
3. Click the **Submit** button.

Message type settings apply to all contacts enrolled for that message type for the selected account. A list of contacts is shown below the message type settings for reference.

You can also click on any message description to see a list of contacts and adjust enrollments for that message type.

## Unenroll a Contact to Stop Messages ##

To unenroll a specific contact for a specific message type:

1. Select the desired contact from the drop-down list at the top of the preference center screen.
2. Click the toggle next to the desired message type to change it from the **ON** setting (green with check mark visible) to the **OFF** setting (red with X visible).
