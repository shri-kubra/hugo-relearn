---
title: "Broadcast"
weight: 7
---

The Notifi Broadcast tool allows you to send ad hoc messages to customers. You can send a broadcast message to

+ all registered customer contacts in the Notifi system
+ a specific category of customer contacts in the Notifi system
+ registered customer contacts associated with a list of customer account numbers you provide in a CSV file
+ customer contacts included with a list of account numbers in a CSV file you provide

Before you try to broadcast your message, refer to the [PreBroadcast Checklist](/notifi/management-console/broadcast/#prebroadcast-checklist) to check if you have completed all the steps.

## Initial View ##

When you first open the Broadcast tool, you will see a list of messages that are being composed and have not been sent or scheduled, messages that are pending delivery, and messages that are in the process of being sent.

### Message Status ###

You can filter the list of broadcast messages by status. Notifi uses these broadcast message statuses:

+ Composing - the message is being composed and has not been sent or scheduled (it is a draft)
+ Pending - the message is awaiting delivery
+ Running - the message is being delivered
+ Completed - the message has been sent to all selected contacts
+ Cancelled - the message was cancelled after being composed or scheduled
+ Aborted - the message was stopped partway through delivery
+ Failed - the message was not successfully sent

## Create a Broadcast Message ##

To create a broadcast message:

1. Click the plus sign icon at the upper right of the message list - the icon will change to show the word "New" when you hold your mouse cursor over it.
2. Enter a name for the broadcast message.
3. Enter content for the message for all channels and languages you want to include.
4. Select criteria to identify message recipients.
5. (Optional) Upload a CSV file to identify a list of account numbers to receive the broadcast message.
6. (Optional) Send a test message to one or more provided contacts to check that the message appears or sounds correct.
7. Send the message immediately or schedule the message to be sent at a later date and time.

### Name a Message ###

By default, the name of a new broadcast message is "New Broadcast" followed by the current date and time. For example: "New Broadcast - Jan 2, 2020 4:45 PM."

To change the name of the message, click the message name or the Edit button (pencil icon) that appears when you hold the mouse cursor over the message name.

The broadcast message name is for your reference inside the Broadcast tool. It will not appear anywhere in the messages sent to customer contacts.

### Enter Template Content ###

The **Templates** section of the create message form shows the message templates for each available channel. If your Notifi implementation supports multiple languages, each available channel will also have a separate template for each supported language.

At a maximum, Notifi supports broadcast message templates for voice, email, SMS text, and push notification channels.

To create or edit a broadcast message template:

1. Select the channel.
2. (Optional) Select the language.
3. Enter text for the message template.
4. Repeat steps 1-3 for each channel and language you want to include in the broadcast message.
5. Click the **Next** button to continue to the **Criteria** section of the form.

{{% notice note %}}
The Broadcast tool does not provide any checks on the text you enter in the template fields. Please check the spelling, grammar, and message tone carefully. You may want to ask another person to check your work before you send the broadcast.
{{% /notice %}}

If you do not create a template for a channel, contacts for that channel will not receive the broadcast message. For example, if you only create an email template, the broadcast message will only be sent to email addresses.

If you do not create a template for a language, contacts with that language selected as a preference will not receive the broadcast message. For example, if English and Spanish are supported and you only create English templates, only contacts with a preference for English will receive the broadcast message.

#### Email Templates ####

The text you enter in the **Subject** field will be the subject line of the email message. The text you enter in the **Body** field will be the body or main content of the email message.

Notifi does not add any formatting around the content in the **Body** field, so you must include any HTML formatting you want to appear in the email messages sent to customers.

If you have an HTML email template created in another program, such as an email marketing program or a design program, you can use that HTML for the email template body.

To include HTML formatting in a broadcast email template:

1. Click the **Edit HTML** button (pencil icon).
2. Copy the HTML from your other program.
3. Paste the HTML into the Broadcast tool.
4. Click the **Edit HTML** button again to preview the HTML content in rich text view.

#### Push Notification Templates ####

The text you enter in the **Alert Title** field will be the title of the push notification. The text you enter in the other field will be the body or detailed content of the push notification.

Push notifications are only supported for Android and iOS mobile apps. This option will not appear if neither Android nor iOS applications are integrated with your Notifi implementation.

iOS push notifications support a maximum of 65 characters for the alert title and 240 characters for the body of the message. Android push notifications support a maximum of 200 characters for the alert title and 1024 characters for the body of the message. Because the same broadcast message template is used for both iOS and Android, we recommend using the smaller character lengths.

#### SMS Text Templates ####

SMS text templates support a maximum of 140 bytes (or 160 characters, see below) in the U.S. for English-language messages. With Notifi 3.2 & 4.0, the Broadcast tool works on the backend to stitch together multiple segments into one message a customer sees, allowing you to go over 160 characters. However, mobile carriers will still send such a longer message via multiple separate SMS messages/segments.

The counter at the lower right side of the template field tracks the number of characters you have entered. A red counter serves as an alert indicating that your template exceeds the character limit, causing the message to be sent in more than one SMS segment, each limited to 140 bytes. The number of bytes you use depends both on the number of characters (1 character = 7/8 byte when using [ONLY GSM-7 characters](https://en.wikipedia.org/wiki/GSM_03.38)) and the type of characters you use. If you use non-GSM-7 characters such as common non-English characters á, Á, í, Í, ó, Ó, ú, or Ú, the mobile carriers need to use the larger UCS-2 character set, which uses 16 rather than 7 bits per character, allowing for less characters per segment. KUBRA recommends you keep segment count lower and thus your costs down. You can do this by substituting non-accented characters where reasonable, as we do when working on non-broadcast templates with clients i.e. use a, A, i, I, o, O, u, or U if customers can infer the word you are spelling without the accent marks.

{{% notice note %}}
The Broadcast tool is set up with a default limitation of 480 characters or three message segments but additional segments can be added up to a limit of 1600 for an extra cost. Talk to your CSM if you want to extend your limits.
{{% /notice %}}

To minimize cost to both sender and recipient, the following special characters will be replaced automatically when entered into a SMS broadcast template upon save or when sending the broadcast:

{{%expand "Click here to expand list of replaced characters for SMS" %}}

| Unicode Character | Glyph         | Changed to            |
|-------------------|---------------|-----------------------|
| U+0009            | &#x9;         | "&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;" (five spaces) |
| U+00AB            | &#xAB;        | <<                    |
| U+00BB            | &#xBB;        | >>                    |
| U+2002            | &#x2002;      | " " (single space)    |
| U+2003            | &#x2003;      | " " (single space)    |
| U+2004            | &#x2004;      | " " (single space)    |
| U+2005            | &#x2005;      | " " (single space)    |
| U+2006            | &#x2006;      | " " (single space)    |
| U+2007            | &#x2007;      | " " (single space)    |
| U+2008            | &#x2008;      | " " (single space)    |
| U+2009            | &#x2009;      | " " (single space)    |
| U+200A            | &#x200A;      | " " (single space)    |
| U+200B            | &#x200B;      | " " (single space)    |
| U+200C            | &#x200C;      | " " (single space)    |
| U+200D            | &#x200D;      | " " (single space)    |
| U+200E            | &#x200E;      | " " (single space)    |
| U+200F            | &#x200F;      | " " (single space)    |
| U+2010            | &#x2010;      | - (dash)              |
| U+2011            | &#x2011;      | - (dash)              |
| U+2012            | &#x2012;      | - (dash)              |
| U+2013            | &#x2013;      | - (dash)              |
| U+2014            | &#x2014;      | - (dash)              |
| U+2015            | &#x2015;      | - (dash)              |
| U+2016            | &#x2016;      | &#124; (vertical line) |
| U+2017            | &#x2017;      | _                     |
| U+2018            | &#x2018;      | '                     |
| U+2019            | &#x2019;      | '                     |
| U+201A            | &#x201A;      | ,                     |
| U+201B            | &#x201B;      | '                     |
| U+201C            | &#x201C;      | "                     |
| U+201D            | &#x201D;      | "                     |
| U+201E            | &#x201E;      | ,,                    |
| U+2022            | &#x2022;      | *                     |
| U+2023            | &#x2023;      | *                     |
| U+2026            | &#x2026;      | ...                   |
| U+2032            | &#x2032;      | '                     |
| U+2033            | &#x2033;      | ''                    |
| U+2034            | &#x2034;      | '''                   |
| U+2035            | &#x2035;      | '                     |
| U+2036            | &#x2036;      | ''                    |
| U+2037            | &#x2037;      | '''                   |
| U+2039            | &#x2039;      | <                     |
| U+203a            | &#x203a;      | >                     |
| U+203c            | &#x203c;      | !!                    |
| U+203d            | &#x203d;      | ?                     |
| U+2043            | &#x2043;      | *                     |
| U+204e            | &#x204e;      | *                     |

{{% /expand%}}

#### Voice Templates ####

Voice templates for broadcast messages use text-to-speech to convert the text you type in the **Body** field into spoken voice messages.

To have numbers or letters read separately, as for a phone number or address, add space characters between the number or letter characters. For example, this can help make sure a phone number is read as `five nine eight two` instead of `five thousand nine hundred eighty two`. You can also use space characters to indicate pauses in the message.

A more specific example of recommended formatting for a phone number is `2 1 0 ... 3 5 3 ... 4 3 5 7`, which would be read with an additional pause between the area code and the first three digits of the phone number and between the first three digits and the last four digits of the phone number.

### Select Recipients ###

The **Criteria** section of the create message form allows you to do the following:
1. Select **Criteria** manually to filter who receives messages.
OR
2. Designate a CSV file you upload to filter who receives the messages.
OR
3. Designate a CSV file + subscriptions to filter who receives the messages.

{{% notice warning %}}
If you choose to designate a CSV file, you cannot choose any other criteria except subscriptions.
{{% /notice %}}

Once the intended recipients are defined, there is an option to add a list of subscriptions to filter those recipients against (see next section).

You can choose recipients for the message using the following address criteria types:

+ Companies - if your organization has only one operating company, you can select the operating company to select all account numbers with contacts registered in the Notifi database
+ States
+ Counties
+ ZIP Codes

To add recipient criteria:

1. Move the mouse cursor over the **Add Criteria** text to show the list of criteria types.
2. Click on a criteria type.
3. Select the values for that criteria type you want to use to identify message recipients.
4. Click the **X** icon at the upper right corner of the pop-up window to close it. Your selected criteria will appear in a list below the **Add Criteria** text.
5. Repeat steps 1-4 for all criteria types you want to include.

If you select multiple options within one type of recipient criteria, the options will act as ALL/ANY/OR selections. If you select multiple types of recipient criteria, the selections will act as AND selections.

For example, if you select five ZIP Codes, the broadcast message will be sent to contacts in the Notifi database registered to account numbers associated with ANY of the selected ZIP Codes.

If you select two ZIP Codes and a County, the broadcast message will be sent to contacts in the Notifi database registered to account numbers associated with ANY of the selected ZIP Code AND the selected County.

#### Upload a CSV File ####

In addition to or as an alternative to the criteria types shown in the broadcast tool, you can upload a CSV file with a list of account numbers to identify recipients for the broadcast message. The CSV file can also include contact information.

To upload a CSV file:

1. Click the **Upload** button in the **Criteria** section of the create message form.
2. Drag and drop the CSV file onto the pop-up window or click the **Select File** button and then locate the file on your computer.
3. Click the **X** icon in the upper right corner of the pop-up window or "Close" once the progress bar says "file uploaded successfully".

{{% notice note %}}
The file you upload will be verified when it is uploaded to ensure it conforms to the file format information below. Verification may take several more minutes after the upload dialog is closed to finish saving the file, particularly if it is 100,000+ lines long. If you attempt to send the broadcast immediately (rather than a scheduled broadcast) before the file save process is complete, you may be forced to wait to start the broadcast until the file save process is fully complete in the background.
{{% /notice %}}

#### CSV File Format ####

The CSV file name has a length limit of 50 characters. The CSV file has a maximum size limit of 150 MB.

A header row is required for CSV files to indicate which attributes the file includes and the order of the attributes.

| Attribute | Required? | Description |
| --------- | --------- | ----------- |
| account | Yes | An account number - the Broadcast message will be sent to all contacts in the Notifi database registered to this account number, unless restricted by other selected criteria. |
| contact | No | A phone number or email address you want to include as a contact for the account in addition to or in place of any contacts in the Notifi database registered to the account number. Phone numbers must be 11 digits (with leading country code and area code). Phone numbers must not contain any special characters. |
| channel | No if contact not provided; yes if contact provided | The channel for the provided contact: one of `SMS`, `IVR`, or `E_MAIL`. |
| supplemental | No if contact not provided or if using `ignoreSubscribedContacts`; yes if contact provided and not using `ignoreSubscribedContacts` | Boolean - this tells Notifi whether to treat the provided contact as a Supplemental Contact or a Default Contact. If `true`, Notifi will treat the contact as a Supplemental Contact. If `false`, Notifi will treat the contact as a Default Contact. If you include a contact but do not specify a value for this attribute, Notifi will treat the contact as a Default Contact. |
| ignoreSubscribedContacts | No if contact not provided; yes if contact provided and not using `supplemental` | Boolean - this tells Notifi whether to ignore any contacts in the Notifi database registered to the account number when sending a message to the contact supplied in the CSV file. If `true`, Notifi will only send the broadcast message to the contact supplied in the CSV file. If `false`, Notifi will also send the broadcast message to contacts in the Notifi database registered to the account number, unless restricted by other selected criteria. The use case for this attribute is to provide a complete list of contacts for a broadcast message, which requires the attribute to be set to `true` for all rows in the CSV file. |

Broadcast messages are sent to Supplemental Contacts in addition to eligible registered contacts. Broadcast messages are sent to Default Contacts only when there are no contacts in the Notifi database registered to the account number.

#### Use Case Examples for CSV File ####

The supported attributes for CSV file upload in the Broadcast tool support the following use cases:

1. Provide a list of account numbers - Notifi will send the broadcast message to contacts registered in the Notifi database to the provided account numbers. The file must not contain duplicate account numbers.
2. Provide account numbers and supplemental contacts - Notifi will send the broadcast message to contacts registered in the Notifi database to the provided account numbers and to the provided supplemental contacts. The file must not contain duplicate account numbers.
3. Provide account numbers and default contacts - Notifi will send the broadcast message to contacts registered in the Notifi database to the provided account numbers or to the provided default contacts if there are no contacts registered in the Notifi database for a specific account number. The file must not contain duplicate account numbers.
4. Provide account numbers and contacts and ignore subscribed contacts - Notifi will send the broadcast message only to the contacts provided in the CSV file. This is the only use case that allows the CSV file to contain duplicate account numbers.

##### Example 1 - CSV with Account Numbers Only #####

```
account
123456789010
123456789011
123456789012
123456789013
```

##### Example 2 - CSV with Account Numbers and Supplemental Contacts #####

```
account,contact,channel,supplemental
123456789010,username@example.com,E_MAIL,true
123456789011,15551234567,SMS,true
123456789012,user@kubra.com,E_MAIL,true
123456789013,customer@abcenergy.com,E_MAIL,true
```

##### Example 3 - Account Numbers and Default Contacts #####

```
account,contact,channel,supplemental
123456789010,username@example.com,E_MAIL,false
123456789011,15551234567,SMS,false
123456789012,user@kubra.com,E_MAIL,false
123456789013,customer@abcenergy.com,E_MAIL,false
```

##### Example 4 - Account Numbers and Contacts, Ignore Subscribed Contacts #####

```
account,contact,channel,ignoreSubscribedContacts
123456789010,username@example.com,E_MAIL,true
123456789011,15551234567,SMS,true
123456789012,user@kubra.com,E_MAIL,true
123456789013,customer@abcenergy.com,E_MAIL,true
```

This example allows you to include duplicate account numbers to provide more than one contact for a single account. If you use this example format, the `ignoreSubscribedContacts` attribute must be included and must be set to `true` for all rows in the file.

### (Optional) Set Subscriptions To Filter On ###

To optionally designate only contacts subscribed to specific messaging programs such as Outage, Bill Ready, Payment Reminder, or Usage (will be dependent on your configuration) to receive the broadcast message, you can choose one or many subscriptions that will be provided to Notifi to help down-select which contacts the broadcast message is sent to.

{{% notice note %}}
While subscriptions selected will affect the eventual number of messages sent, they will not affect the count of accounts seen in the broadcast details dialog when sending or scheduling a broadcast.
{{% /notice %}}

### Save a Draft ###

To save a draft broadcast message without sending it or scheduling it to be sent, click the **Save without Sending** button on the create message form.

### Test a Message ###

The **Test** section of the create message form allows you to send a test message to check that a broadcast message sounds or appears correctly before you send the broadcast message to the selected recipients.

To send a test message:

1. Hold your mouse cursor over the **Add Contact** text.
2. Select a channel for the contact you want to use for the test message.
3. Enter the contact information in the text box.
4. (Optional) Select the language you want to use for the test message.
5. Repeat steps 1-4 for any additional contacts you want to include in the test.
6. Click the **Send Test** button.

<!--- ### (Optional) Ignore Do Not Disturb ###

Added in September 2022, Notifi has an optional checkbox just above the **Send Immediately** checkbox called **Ignore customers' Do-Not-Disturb preferences**. This provides an option to ignore any per-registration or default "Do Not Disturb" (DND) settings provided by individual customers or during configuration of Notifi.

{{% notice warning %}}
This feature will ignore customers' preference to get messages at a specific time of day, but is intended for use in time-critical or storm situations where timeliness is paramount.
{{% /notice %}} --->

### Send a Message Immediately ###

The **Schedule** section of the create message form allows you to send a broadcast message to the selected recipients.

To send a broadcast message immediately:

1. Click the **Send Immediately** checkbox.
2. Click the **Send Broadcast** button.
3. Review the details for the message.
4. Click the **Yes** button to confirm message delivery.

{{% notice note %}}
Contacts with an active do not disturb period at the time the broadcast is sent will receive the message when their do not disturb period ends.
{{% /notice %}}

### Schedule a Message for Later Delivery ###

The **Schedule** section of the create message form allows you to schedule a broadcast message for later delivery to the selected recipients.

To schedule a broadcast message for later delivery:

1. Click the **Date** field.
2. Select a date and time in the pop-up window. The slider at the bottom of the pop-up window allows you to select a time.
3. Click the **Done** button.
4. Click the **Send Broadcast** button.
5. Review the details for the scheduled message.
6. Click the **Yes** button to confirm message scheduling.

To clear a selected date and time, click the **Unschedule** button.

{{% notice note %}}
The Broadcast tool uses your computer's current local time zone as the time zone for scheduled broadcast messages. Contacts with an active do not disturb period at the time the broadcast is scheduled will receive the message when their do not disturb period ends.
{{% /notice %}}

## Monitoring the Status of a Broadcast ##

To check the status of a broadcast that is in the process of sending, you can select a previously-created broadcast that is currently sending. The message that opens will not be editable, but it is possible to view the content that is being sent. You can see a percentage-based status bar at the top of the screen that provides a view of how much of the broadcast has been sent at this moment.

The progress of this bar will be a near-realtime view of how quickly messages are passing through the event handling and message sending segments of Notifi. The progress bar data is based on the quantity of events that have been processed divided by the number of events submitted.

As the broadcast is starting, the progress bar might be somewhat volatile: this is normal. The volatility is a result of the number of events submitted to Notifi being low and not a reflection of the total number of events. As all the events are submitted, the progress bar should indicate a more accurate view of the actual state of how much of the broadcast has been sent to KUBRA's method aggregators.

## Edit a Broadcast Message ##

To resume working on a draft message or to edit a message that is pending delivery, select the message name from the list in the Broadcast tool. You may need to select the "Composing" or "Pending" message status to see the message name in the list.

You cannot edit a broadcast message after it has been sent. To create a new broadcast message with content based on a previously sent message, you must create a new broadcast and copy over the template content.

## Cancel a Broadcast Message ##

To cancel a broadcast message, click the **Cancel Broadcast** button at the bottom of the create message form.

If the broadcast message is being sent, you can abort the message. Some individual messages may still be delivered to recipients if they were already sent for delivery before the message was aborted.

## Copy a Broadcast ##

Notifi lets you copy a broadcast, allowing you to duplicate a previously created broadcast. To copy the broadcast, click on the green **Copy** button to the right of the broadcast.

The new copy will have the same verbiage, templates, and criteria as your original version. If you delete the recipient CSV file, it deletes the CSV file from the original as well.

## Upload a Broadcast Audio File ##

{{% notice info %}}
The audio file upload functionality is only available with Notifi 4.0 after KUBRA has configured voice calling templates to use the audio files.
{{% /notice %}}

Notifi lets you upload a new audio file via the UI to supplement Text-to-Speech when creating an IVR template. The IVR templates have two template types: **Audio file** and **Text-to-Speech**. Broadcast supports either **Audio file** or **Text-to-Speech**, but not both.

New broadcasts will default to the **Text-to-Speech** IVR template type.

To upload an audio file:

1. Check the **Audio file** box in **Voice Template Type** to enable the **Upload** button.
2. Click the **File upload** button and select a supported audio file (see note below).

{{% notice note %}}
The max supported file size for an audio file is 50 MB. The audio file length should not exceed 10 minutes. The preferred audio file format is .wav.
{{% /notice %}}

Once the audio file is uploaded successfully, the audio file name will appear in a tag below the file upload area.

To delete the audio file, click the delete button to the right of the audio file name tag. Clicking the delete button will remove the audio file from the broadcast and re-enable Text functionality.

* Existing broadcasts will default to a type based on template data.
  * If an audio file exists - default to **Audio file**.
  * If no audio file exists - default to **Text-to-Speech**.

{{% notice warning %}}
Uploading an audio file will override Text-to-Speech for all locales. The uploaded file will be sent to all contacts regardless of language preference. The audio file will be transcoded for the phone system as-needed.
{{% /notice %}}

Supported MIME types:

| MIME         | TYPE                          |
|--------------|-------------------------------|
| audio/mpeg   | mpeg layer 3 audio            |
| audio/wav    | wav format audio              |
| audio/wave   | wav format audio              |
| audio/x-wav  | wav format audio              |
| audio/aiff   | audio interchange file format |
| audio/x-aifc | audio interchange file format |
| audio/x-aiff | audio interchange file format |
| audio/x-gsm  | GSM audio format              |
| audio/gsm    | GSM audio format              |
| audio/ulaw   | μ-law audio format            |

## PreBroadcast Checklist ##

Refer to the PreBroadcast checklist to confirm if you have completed all steps for a successful broadcast.

{{<attachments title="" style="green" />}}
