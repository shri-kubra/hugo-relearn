---
title: "Template Manager"
weight: 8
---

Notifi uses message templates for proactive messages that include static content and data elements. The Template Manager tool allows you to review the content of these message templates and to submit changes to the templates for review and promotion from a test instance to the production instance.

{{% notice info %}}
The Template Manager tool only contains templates for proactive (one-way, outbound) messages. Interactive automated conversations (two-way messages) are managed separately. You must submit a ticket to KUBRA support for any requested changes to conversation verbiage.
{{% /notice %}}

## Access ##

Access to the Template Manager tool may require a second login using the same username and password you use for the Notifi Management Console.

The Template Manager tool may open in a new browser tab. You may need to close the tab and/or use the primary Notifi Management Console URL to access other Notifi management tools.

## Navigation ##

The Template Manager tool includes the following sections:

+ Edit Templates
+ Latest Activity
+ Deploy Changes

By default, the tool opens to show the Edit Templates section.

## Edit Templates ##

The Edit Templates section shows options for message channels supported by the Notifi implementation and an option called "Globals" for elements shared by multiple message templates. If the Notifi implementation supports more than one language, there is a language selection option under each channel and under the Globals option.

After you select a message channel and a language if applicable, you will see a list of message templates or assets organized by message topic. You can select a template to view a preview or edit its contents.

After you click the **Edit** button to edit a specific template, you will see an Edit Template panel with four tabs:

+ Body - a rich-text editor for the template body content
+ Parts - plain-text fields for the message subject and the message body (only applicable for email templates)
+ Placeholders - plain-text fields for variables such as the message title (only applicable for email templates)
+ Preview - a preview of any changes you have made in the Body tab or the Placeholders tab

{{% notice note %}}
Edits you make in the Body tab do NOT copy over to the Parts tab automatically. The **Plaintext** field in the Parts tab should contain the plain-text version of the email body content, excluding HTML annotations. This plain-text version is used by the [Notifi History tool](/notifi/management-console/history). The plain-text version of the email body will also be sent to recipients who cannot receive rich-text email messages.
{{% /notice %}}

To save your changes, click the **Save** button. To discard your changes, click the **Cancel** button.

### Tips for Editing Templates ###

+ Variable values will not be the same length as the variable in the message template.
+ SMS or text messages have a maximum character limit of 160 characters in the U.S. and 140 characters in Canada for English language messages.
+ Voice templates have a maximum Unicode character limit of 4,096 characters.
+ Punctuation such as commas and periods in voice templates will be interpreted as natural pauses.
+ The text-to-speech program used for voice messages will make assumptions about how to pronounce numbers, dates, times, amounts of money and other abbreviations.
+ You can format initialisms or acronyms in voice templates with a space between each letter to have the text-to-speech program pronounce each letter separately - for example, `E T R` would be read as "ee tee ar."

### Template Variables ###

There are four types of variable or conditional content used in Notifi message templates:

1. Placeholders or local variables such as `{$ title $}`, which refers to the Title placeholder for an email template. These variables can be used in more than one location within a specific message template and are managed in the Placeholders section of the Edit Template form.
2. Global variables such as `{$ g_sms_contact $}` or `{$ g_resume_alerts_link $}`. These variables can be used in more than one message template and are managed in the Globals section of the Template Manager tool.
3. Notifi variables that use event data to create messages for customers, such as `{{Subscriptions.contactId}}` for a contact ID such as an email address or a user-provided nickname for the email address, or `{{Address.longAddress}}` for the long form of the street address.
4. Conditional Notifi expressions such as the expression `{{#if (crewsAreDispatched CrewStatus)}}Our crews have been assigned to investigate the situation.{{/if}}`, which will include the text "Our crews have been assigned to investigate the situation." if the `CrewStatus` variable value indicates that crews have been dispatched.

Notifi templates also use standard HTML such as `<a href="www.example.com">Example hypertext</a>` for hypertext and `<strong>bold words</strong>` for bold text.

{{% notice tip %}}
Opening and closing characters are required for both variable content and HTML elements. If you would like to make changes to variables or conditional Notifi expressions, please contact KUBRA support for assistance.
{{% /notice %}}

## Edit Globals ##

After you select the Globals option and a language if applicable, you will see a file called `global.yml`. Select the file name to view or edit a list of global values used by multiple message templates.

Some implementations will also have environment-specific files in the Globals section. These files use names such as `global.test.yml` for the Test environment and `global.prod.yml` for the Production environment. Values in an environment-specific file will override the values in the main `global.yml` file.

You can use the environment-specific global files to set environment-specific values such as test links and phone numbers if those items are different from the production items.

## Latest Activity ##

The Latest Activity section shows a list of recent template change deployments to either the test environment or the production environment.

Select a deployment to view the following information:

+ Service Name - the name of the service used for the deployment
+ Date - the date and time at which the deployment was made
+ Files - a list of template files changed by the deployment
+ Changes - a list of changes made to the template files

Click the **View Details** link for a specific change to view the following information:

+ Description - a brief description of the change.
+ Files - the location of the template files that were changed.
+ Diff - an excerpt of the file content focusing on the content that changed. Removed content is shown in red with a "-" symbol at the start of the row. Added content is shown in green with a "+" symbol at the start of the row.
+ Date - the date and time at which the change was made.
+ By - the username of the person who made the change.

## Deploy Changes ##

The Deploy Changes section shows a list of environments and the number of changes, if any, that are ready to be deployed to the environment.

Select an environment name to view changes to the environment and deploy the changes. To view details about a specific change, click the **View Details** link next to the change description. The details shown are the same as in the [Latest Activity section](/notifi/management-console/template-manager/#latest-activity)

If there are no pending changes for an environment, the **Deploy** button will be disabled.

To deploy changes, click the **Deploy** button. Changes always move from development to test or from test to production.

## Examples of Template Edits ##

### Example 1 - Add an additional note to an outage email ###

1. Access the "Edit Templates" section of the Template Manager tool.
2. Select "Email" and "English."
3. Select the name of the outage template file, such as "out_new.njk."
4. Click the **Edit** button.
5. In the Body tab, scan the template for the location where you want to add the additional content.
6. Type the new content into the outage template body. Be careful not to disturb any variables or conditional elements.
7. In the Parts tab, scan the template for the location where you want to add the additional content, and copy the change you made in the Body tab. Be careful not to disturb any variables or conditional elements.
8. Use the Preview option to check the results of your edits.
9. Click the **Save** button to save your changes.

Repeat these steps for templates in other supported languages, replacing "English" with the appropriate language, as needed.

### Example 2 - Change a term used in an English SMS message to reduce character count ###

1. Access the "Edit Templates" section of the Template Manager tool.
2. Select "SMS" and "English."
3. Select the name of the template file, such as "contact_paused.njk."
4. Click the **Edit** button.
5. Scan the template for the term you want to change.
6. Edit the template content.
7. Use the Preview option to check the results of your edit.
8. Click the **Save** button to save your changes.

### Example 3 - Update the company name ###

1. Access the "Edit Templates" section of the Template Manager tool.
2. Select "Globals."
3. Select the "global.yml" file.
4. Click the **Edit** button.
5. Locate the variable or variables for the company name. There may be more than one version, such as an SMS Greeting, a Formal Company Name, and a Sender Name.
6. Edit the variables.
7. Click the **Save** button to save your changes.
