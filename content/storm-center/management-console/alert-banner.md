---
title: "Alert Banner App"
weight: 31
---

To access the Alert Banner app, click the **Alert Banner** button on the Control Center Dashboard under "Apps."

You can use the Alert Banner app to create alert banners and messages and associate them with Storm Center maps. Each map can show one alert banner at a time.

![Alert Banner App - no content](/images/alert-banner-app-empty.png)

## Create an Alert Banner ##

To create a new alert banner, click the **Create an Alert** button.

### Banner Position and Visibility ###

You can choose to show the alert banner either at the bottom of the screen or at the top of the screen. The banner position will be aligned to the right.

Select the desired option for the alert banner position from the **Alert Position** drop-down field.

If you want to show the full alert banner message when a user opens the map for the first time, select the **Show Alert on Page Load** checkbox. This setting is off by default.

### Alert Banner Colors ###

You can use a color picker to select colors for the alert banner background and font. The color picker shows the RGB values for the currently selected color.

The default banner background color is red `#BE281E` or `rgb(190,40,30)`. The default banner font color is white `#FFFFFF` or `rgb(255,255,255)`.

The tables below provide some suggested banner background colors that meet contrast requirements for WCAG 2.1, level AA.

Pair these colors with white text: `#FFFFFF` or `rgb(255,255,255)`

| Banner Color | Hex Code | RGB Code |
| ------------ | -------- | -------- |
| Red | #E60000 | rgb(230,0,0) |
| Fuchsia | #CC00CC | rgb(204,0,204) |
| Purple | #800080 | rgb(128,0,128) |
| Green | #008000 | rgb(0,128,0) |
| Blue | #0000FF | rgb(0,0,255) |
| Navy Blue | #000080 | rgb(0,0,128) |

Pair these colors with black text: `#000000` or `rgb(0,0,0)`

| Banner Color | Hex Code | RGB Code |
| ------------ | -------- | -------- |
| Red-Orange | #FF662E | rgb(255,102,46) |
| Orange | #FFA500 | rgb(255,165,0) |
| Yellow | #FFD700 | rgb(255,215,0) |
| Lime Green | #00FF00 | rgb(0,255,0) |
| Cyan | #00FFFF | rgb(0,255,255) |
| Hot Pink | #FF57B0 | rgb(255,87,176) |

### Banner Title and Message Content ###

For each language supported by the map, you can enter a banner title. The title will appear on the map.

{{% notice note %}}
The alert banner title field accepts a maximum of 80 characters. KUBRA recommends keeping alert banner titles as short as possible.
{{% /notice %}}

You can also enter a longer text for the alert message. The alert message will appear when a user selects the banner on the map. The alert message can include bold, italics, underline, strikethrough, subscript, superscript, block quotes, numbered lists, bulleted lists, links, images, tables, and embedded video.

{{% notice note %}}
The Alert Banner tool supports a maximum file size of 8MB across all supported languages. KUBRA recommends using no more than 2,000 words or approximately 8,700 text characters per language, and no more than six total image files across all supported languages.
{{% /notice %}}

#### Alert Message Tables ####

To insert a table in an alert message, click the **Table** button above the alert message field.

![Table button](/images/alert-banner-app-table-button.png)

A selector will open that allows you to choose the number of columns and rows for the table.

Select one or more table cells to see tools that allow you to adjust the number of rows or columns, split or merge cells, fix the column width, or add a table header style.

![Table example](/images/alert-banner-app-table-example.png)

#### Alert Message Video ####

The alert message content supports embedded video using links from either Vimeo or YouTube. To insert an embedded video, click the **Video** button above the alert message field.

![Video button](/images/alert-banner-app-video-button.png)

A pop-up will open that allows you to paste in the embed URL for the video.

You can also adjust the width and height of the video within the alert message card using percentage or ratios and choose whether the video is aligned to the left, center, or right of the alert message card.

![Video tools](/images/alert-banner-app-video-tools.png)

#### Connect Alert Banner to Maps ####

After you enter the text you want for the banner title and the content you want for the alert message, select one or more map views for the banner to be displayed on from the **Views** drop-down list.

### Schedule an Alert ###

Toggle **Enable Alert** if you want to schedule a time for the alert to be displayed. When you toggle the button, you can choose a date and time for the alert to be displayed at. Optionally, you can also add an end time for the alert. 

![Schedule an Alert](/images/alert-banner-schedule-alerts.png)

If you do not choose a start date and time, the alert will not be immediately displayed on the map. However, the alert will be displayed in the list of alert messages available to be deployed.

### Save an Alert ###

To save the alert, click the **Submit** button. To return to the Alert Banner app screen without saving the new alert, click the **Cancel** button.

## Manage Alert Banner Content and Visibility ##

The Alert Banner app screen shows a list of all saved alert banners and messages. You can edit, delete, show, or hide these alerts by clicking on the appropriate button to the right of the alert name.

![Alert Banner App - example](/images/alert-banner-app-example.png)

{{% notice tip %}}
The Show/Hide button acts as a toggle. If the button says "Show," the alert is currently set to be hidden. If the button says "Hide," the alert is currently set to be shown on the associated map or maps.
{{% /notice %}}

To deploy changes you have made to one or more alert messages, click the **Deploy** button below the list of Alert Messages.

{{% notice note %}}
You must click the **Deploy** button to apply any changes you make in this app - banner colors, banner title, long text, show, hide, or any combination of these settings - to the map or maps for the instance.
{{% /notice %}}

## Review Alert Banners Visible on Storm Center Maps ##

The **Deployed Alert Messages** section shows the alert title and map view name for each alert banner currently deployed to and visible on a map.

{{% notice tip %}}
If you hide a previously visible alert banner or show a previously hidden alert banner and then click the **Deploy** button, you may also need to refresh the Alert Banner tool before the list of Deployed Alert Messages will update.
{{% /notice %}}

## Alert Banner Examples ##

Example 1 below shows an alert banner with the default red background and white text, appearing at the bottom of the map.

![Alert Banner Example 1](/images/alert-banner-example-1.png)

Example 2 below shows an alert banner with the suggested orange background and black text, appearing at the top of the map.

![Alert Banner Example 2](/images/alert-banner-example-2.png)
