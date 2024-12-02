---
title: "Configure Map Interface"
weight: 19
---

The user interface (UI) for Storm Center outage maps includes configurable features for buttons and links, a logo, UI background colors, and UI font colors.

{{% notice note %}}
The typeface and font size used for Storm Center outage maps are NOT configurable.
{{% /notice %}}

To provide settings for the configurable parts of the map interface, use the **Design Manager** sub-section of the **Shared Resources** section of the Instance Dashboard.

1. Click the **Create a Design** button.
1. Enter a name for the design - this name is how you will identify the design in other areas of the Instance Manager; it will not show up on the map.

## Layout and Button Settings ##

1. If you want to show text on the access buttons for the overview panel and the help panel, set the **Show Header Text** slider to the "On" position. The slider is On by default.
1. If you want to create a map without a map header, set the **Enable Flex View** slider to the "On" position. The slider is Off by default.
1. If you want to expand the overview panel on page load for desktop browsers, mobile browsers, or both, set the appropriate sliders under **Expand Menu on Load** to the "On" position. These sliders are Off by default.
    + If you set the help panel access button to be on the left and the overview panel access button to be on the right, this setting will affect the help panel instead of the overview panel.
1. If you want to expand the map legend card on page load for desktop browsers, mobile browsers, or both, set the appropriate sliders under **Expand Legend on Load** to the "On" position. The Desktop slider is On and the Mobile slider is Off by default.
1. If you want to change the label or icon shown when an access button is selected, use the fields under **Tab Selection** to edit the labels for all languages supported by the instance and the key associated with the Font Awesome icon you want to use.
1. If you created a content block that you want to include in the overview panel below the summary information, you can use the Summary Content Block drop-down to select the name of the content block. See the [create buttons](/storm-center/configuration-guide/create-buttons) page for instructions on how to set up configurable content blocks.
1. If you created one or more Buttons or Icon Buttons that you want to include in the map header or in the overview panel (depending on the layout and browser size), you can select Application Buttons and Application Icon Buttons to include on the map. See the [create buttons](/storm-center/configuration-guide/create-buttons) page for instructions on how to set up these buttons.

{{% notice note %}}
The KUBRA implementation team can provide a list of supported Font Awesome icons and keys for use with Storm Center. For images you want to use in Content Blocks and Icon Buttons, each utility can now use personalized images that have been uploaded to **Image Resource Manager** by the KUBRA team. However, KUBRA recommends using the default ADA-compliant Font Awesome icons.
{{% /notice %}}

## Overview Panel ##

These settings appear under the **Menu Content** heading.

1. If you want to remove the overview panel and access button from the map, clear the **Visible** checkbox. The overview panel is visible by default.
2. Enter a label for the overview panel access button for all languages supported by the instance.
3. Enter the key associated with the Font Awesome icon you want to use for the overview panel access button.
4. Specify the order in which you want the overview panel access button to appear - the numerical order in the Edit Design form is the order in which the buttons for the overview panel and help panel will appear from left to right on the map.
5. If you created one or more buttons or content blocks that you want to include at the bottom of the overview panel, you can select them from the **Buttons/Content Blocks** drop-down list. See the [create buttons](/storm-center/configuration-guide/create-buttons) page for instructions on how to set up these items. The order in which you select items is the order in which the items will appear from top to bottom in the overview panel, under the Summary and Weather sections if those sections are visible.
6. If you want to remove the Summary section from the Menu content, clear the **Visible** checkbox under "Summary." You may want to do this if your map does not include any summary reports.
7. Enter a label for all languages supported by the instance, enter the key associated with the Font Awesome icon you want to use for the Summary section, and specify an order for the Summary section. The numerical order in the Edit Design form is the order in which the Summary and Weather sections will appear from top to bottom in the overview panel.
8. If you want to remove the Weather section from the Menu content, clear the **Visible** checkbox under "Weather." This will prevent the weather radar option from being included on the outage map.
9. Enter a label for all languages supported by the instance, enter the key associated with the Font Awesome icon you want to use for the Weather section, and specify an order for the Weather section.

## Help Panel ##

These settings appear under the **Help/Information Content** heading.

1. If you want to remove the help panel and access button from the map, clear the **Visible** checkbox. The help panel is visible by default.
2. Enter a label for the help panel access button for all languages supported by the instance.
3. Enter the key associated with the Font Awesome icon you want to use for the help panel access button.
4. Specify the order in which you want the help panel access button to appear - the numerical order in the Edit Design form is the order in which the access buttons for the overview panel and the help panel will appear from left to right on the map.
5. If you created one or more buttons or content blocks that you want to include in the help panel, you can select them from the **Buttons/Content Blocks** drop-down list. See the [create buttons](/storm-center/configuration-guide/create-buttons) page for instructions on how to set up these items. The order in which you select items is the order in which the items will appear from top to bottom in the help panel.

## Logo Settings ##

You can provide a company logo to be included in the map header if you are configuring a map that includes a header.

1. If you want to include a logo, first upload the logo using Image Resource Manager. Use the path URL IRM generates for the logo image.
1. If you want the logo to link to a website, provide a URL for each language supported by the instance.
1. Select a target for the link URL - options are "Blank" and "Parent."
    + "Blank" will open the link in a new browser window or tab.
    + "Parent" will open the link in the user's current browser window or tab.

{{% notice note %}}
PNG format is preferred for logo images. JPEG, GIF, and SVG are also acceptable. The logo file must have a transparent background. PNG and JPEG files can be a maximum of 225px wide and 54px high. SVG files must specify width, height, viewbox, and xmlns properties. For best results, do NOT add extra padding to the top or sides of the logo file.
{{% /notice %}}

## Map Display Options and Zoom Buttons ##

For each of the map display options buttons, you can chose to show or hide the button on desktop and mobile screen sizes.

There are up to four buttons in the map controls section:

+ Search
+ Show My Location
+ Show Map Overview
+ Select Language

You can also choose to show or hide the Zoom In and Zoom Out buttons on desktop and mobile screen sizes. If shown, the zoom buttons appear above the map background selector in the lower right corner of the map. If a map display option button is hidden for desktop screen sizes, it will also be hidden for mobile screen sizes.

To hide one or more of these buttons on desktop screen sizes, click the toggle below the button name and next to the word "Show" to change it to the "off" position. By default, all map display options buttons and zoom buttons are "on" for desktop screen sizes.

To hide one or more of these buttons on mobile screen sizes, click the toggle below the button name and next to the word "Mobile" to change it to the "off" position. By default, all map display options buttons are "on" for mobile screen sizes, and zoom buttons are "off" for mobile screen sizes.

## Map Interface Colors ##

You can provide hex color codes for the colors you want to use for each configurable portion of the map UI. A preview of the color value will be shown after you enter a hex color code.

![Storm Center map wireframe](/images/storm_center_map_wireframe.png)

### Brand Colors ###

The lists below provide examples of locations where the brand colors are used. These lists do not include all locations for the colors. We have also included screenshots of an example map to demonstrate the brand color locations.

The "Primary" color is used for

+ the backgrounds for configurable buttons in the map header, overview panel, and help panel
+ the backgrounds for buttons in modals like the search modal, the alert banner modal, and the summary report modal
+ the background of the Save to Bookmark, Delete Bookmark, and Clear Map Marker buttons in the search information panel
+ the icon color for icon buttons
+ the default color for hyperlinks in configurable content blocks
+ the text color for buttons at the bottom of the information panel
+ the link color for summary report names and area names in summary reports
+ the backgrounds for the map legend button and the map view selector in the map legend
+ the text color for the selected language in the language selection modal

The "Secondary" color is used for

+ the background of the overview panel button and help panel button when selected
+ the background of the Summary and Weather section headers for the overview panel when not selected
+ the icon hover color for icon buttons
+ the default hover color for hyperlinks in configurable content blocks
+ the text hover color for buttons at the bottom of the information panel
+ the link hover color for summary report names and area names in summary reports
+ the background of the location button in the search modal

The "Tertiary" color is used for

+ the background of the Summary and Weather section headers for the overview panel when selected
+ the background of selected checkboxes in the Weather section for the overview panel
+ the background of selected checkboxes in the map legend

The "Light Gray" color is used for

+ the background of the show custom layers and service area options at the bottom of the map legend
+ the weather opacity slider in the overview panel
+ the background of the buttons at the bottom of the information panel
+ the background of bookmarks information in the search modal

The "Disabled" color is used for

+ the text labels below the access buttons for the overview panel and help panel
+ the background of the overview panel button and help panel button when not selected
+ the placeholder text in the search field of the search modal

The "Light" color is used for

+ the text on the Summary and Weather section headers for the overview panel
+ the background of the Summary and Weather section headers for the overview panel on hover
+ the text on the map view selector for the map legend
+ the text for configurable buttons in the map header, overview panel, and help panel
+ the background of the map view selector for the map legend on hover
+ the background of configurable buttons in the map header, overview panel, and help panel on hover
+ the text on the buttons in modals like the search modal, the alert banner modal, and the summary report modal
+ the text on the Save to Bookmark, Delete Bookmark, and Clear Map Marker buttons in the search information panel
+ the icons for the map display options buttons and map controls buttons
+ the background of the language selection modal

The "Dark" color is used for

+ the text in the overview panel, map legend, and information panel (not including configurable content blocks)
+ the text in summary reports
+ the text above the search field and of bookmarks information in the search modal
+ the background of the map display options buttons and map controls buttons
+ the text of the not selected languages in the language selection modal

The "Overlay" color is used at 70% opacity for

+ the overlay put on the map when using the search modal, summary reports, or the alert banner message
+ the overlay put on the map when using the map view selector in the map legend on a mobile device

The "Card" color is used for

+ the background of information cards in the overview panel, help panel, and information panel
+ the background of the map legend
+ the background of the search modal
+ the background of summary reports

The "Panel" color is used for

+ The background of the overview panel, help panel, and information panel

The "Menu" color is used for

+ the background of the map header

### Brand Color Configuration Example ###

The following images show examples of the brand colors using the following key:

1. Primary - #007FAD
2. Secondary #536372
3. Tertiary - #018748
4. Light Gray - #F2F2F3
5. Disabled - #979DA3
6. Light - #FFFFFF
7. Dark - #242424
8. Overlay - #536372 (shown at 70% opacity)
9. Card - #FFFFFF
10. Panel - #CBD0D4
11. Menu - #EAECEE

![Map Header - colors](/images/map-header-colors.png)

![Overview Panel - colors](/images/overview-panel-colors.png)

<img src="/images/help-panel-colors.png" style="width:50%" alt="Help Panel - colors">

![Search and Bookmarks - colors](/images/search-bookmarks-colors.png)

<img src="/images/map-display-options-colors.png" style="width:50%" alt="Map Display Options - colors">

![Map Legend - colors](/images/map-legend-colors.png)

![Information Panel - colors](/images/info-panel-colors.png)

![Summary Report - colors](/images/summary-report-colors.png)

<img src="/images/alert-message-colors.png" style="width:75%" alt="Alert Banner Message - colors">

![Map Controls - colors](/images/map-controls-colors.png)
