---
title: "Create Buttons and Content Blocks"
weight: 17
---

Storm Center outage maps can include buttons to provide links to external websites such as social media accounts or to other pages on the website of the organization using the map. Depending on the selected layout, these buttons can appear in the map header, in the overview panel, in the help panel, and at the bottom of information panels.

Storm Center outage maps can also include configurable content blocks that can appear in the overview panel, in the help panel, at the top of summary reports, and at the bottom of information panels.

To create buttons and content blocks, use the **Buttons/Content Blocks** sub-section of the **Shared Resources** section of the Instance Dashboard.

1. Click the **Create New** button.
1. Enter a name for the button or content block - this name is how you will identify the item in other areas of the Instance Manager; it will not show up on the map.
1. Select a type for the button or content block. Options are:
    + Button - This button type will be available to add to
        + the bottom of information panels when you create or edit an outage data layer
        + the map header when you configure the map interface
            - If a map does not include a map header, buttons will appear in the overview panel below the Summary section instead of in the map header.
        + the bottom of the overview panel
        + the help panel
    + Content Block - This content block will be available to add to
        + the overview panel between the Summary section and the default tools
        + the bottom of the overview panel (below the default tools)
        + the help panel
        + the top of summary reports (as a summary report description)
        + the bottom of information panels
    + Icon Button - This button type will be available to add to the map header when you configure the map interface, and is designed to provide a social media icon with a link to a social media profile page. Storm Center uses Font Awesome icons by default. However, you can use Image Resource Manager to upload the image you want to associate with the icon buttons.
        + If a map does not include a map header, these buttons will appear in the overview panel below the Summary section.
1. Enter labels to be used on the map for the button or the content for the content block for each language supported by the instance.
    + The label for an icon button will be used as alternative text (also known as alt text or alt tags) for the icon on the map.
    + KUBRA recommends a maximum of 25 characters for most button labels.
    + Do not include images in content blocks to be used as summary report descriptions. To add images in content blocks, please read the tip below.
1. Enter the URL for the web page the button should point to for each language supported by the instance.
1. Select a target for the button's URL - options are "Blank" and "Parent."
    + "Blank" will open the link in a new browser window or tab.
    + "Parent" will open the link in the user's current browser window or tab.
1. If you are creating an Icon Button, you have two options. KUBRA recommends providing the key associated with the Font Awesome icon for the button icon you want to use. A preview for the icon will be shown after you enter a valid icon name. You can request a list of supported Font Awesome icons from the KUBRA implementation team.  
If you want to use custom images, select an image from Image Resource Manager under the **Icon** selection. With Image Resource Manager, you are free to upload and reference the social media image of your choice.
{{% notice warning %}}
For custom images, the supported image file types are JPEG, GIF, PNG, and SVG (recommended). The maximum file size allowed per image is 1 MB. _KUBRA also recommends using image sizes of 22x22 pixels; otherwise the image will be scaled down to fit that space constraint._
{{% /notice %}}
    + If you are creating an Icon Button for a social media account, KUBRA recommends providing the brand name associated with the icon. The social media icon names supported by Storm Center are
      + Facebook
      + Instagram
      + Twitter
      + YouTube
1. Click the **Submit** button.

{{% notice tip %}}
If you want to use an image within a content block, please do the following:
1. Click on the Image button under the Label & URL section.
2. Navigate to the Link option in the popup that appears.
3. Add an Image Resource Manager path URL in the URL to link section.
4. Click the Submit button.
{{% /notice %}}
