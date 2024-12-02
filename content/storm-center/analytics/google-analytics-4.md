---
title: "Google Analytics 4"
weight: 37
---

Google Analytics 4 measures the events listed below for Storm Center 5.

## Measured Events ##

The analytics for Storm Center maps measure three types of interactions: page views, clicks, and changes. Depending on map configuration, a specific map may not include all of the events described here.

The descriptions of measured events use the terms from the following diagram of the parts of the Storm Center map interface.

![Storm Center map wireframe](/images/storm_center_map_wireframe.png)

### Page View Interactions ###

Storm Center maps include three items that are measured as separate page views: the main map page, summary reports, and the message associated with an alert banner.

Google Analytics 4 records a page view event when a user opens the page from a URL typed into the web browser or when the user opens the page from a link included on another web page.

Page view events are **not** recorded when a user opens a summary report or the alert banner message after accessing the main map page. Also, page view events are **not** recorded when a user closes a summary report or the alert banner message.

### Individual Interactions ###

Change interactions measure selections the user might make on a map base or data layer.

Click interactions measure most of the possible user behavior when interacting with the Storm Center map. Interactions that include a label measure the configured HTML label in all languages configured for the map, so data can be sorted by user language.

When adding a _Data Stream_ to your _Property_ in GA4, select *Web* as the platform choice.

| Event Name | Event Label | Description |
| ---------- | ----------- | ----------- |
| Change | Select Data Layer - *VisibilityOptionInLanguage* | User selected a choice from the map view selector in the map legend, such as View By County or View by Zip - measuring includes the label for the visibility option |
| Change | Select Map Base - h | User changed the map background to the Hybrid option |
| Change | Select Map Base - r | User changed the map background to the Road option |
| Change | Select Map Base - s | User changed the map background to the Satellite option |
| Change | Summary Report Filter by Area | User changed the summary report area filter to filter the report by area name |
| Change | Weather Opacity Change | User changed the opacity setting for the weather radar layer |
| Click | Alert Banner | User clicked the alert banner |
| Click | Application Custom Button Click *ButtonNameInLanguage* | User clicked a configurable button in the map header or the overview panel - measuring includes the label for the button |
| Click | Browser Support | User clicked the Browser Support link in the overview panel |
| Click | Clear Map Marker | User clicked the Clear Map Marker button in the information panel after searching for an address, accessing a bookmarked location, or using the Show My Location button |
| Click | Custom Button - *ButtonNameInLanguage* | User clicked a configurable button in the overview panel or the help panel - measuring includes the label for the button |
| Click | Custom Icon Button - *ButtonNameInLanguage* | User clicked an icon button in the map header or the overview panel - measuring includes the label for the button |
| Click | Custom Layers Show/Hide | User clicked the checkbox to show or hide Custom Layers information |
| Click | Download Report - *ReportTitleInLanguage* | User clicked the Export Data button in a summary report - measuring includes the title of the summary report |
| Click | Delete Bookmark | User clicked the Delete Bookmark button in the search address modal or in the information panel after accessing a bookmarked location |
| Click | Edit Bookmark | User clicked the Edit Bookmark button in the search address modal |
| Click | Find Street Address | User pressed **Enter** after entering an address in the search field or selected a suggested address in the search address modal |
| Click | Go to Area - *ReportTitleInLanguage* | User clicked an area name in a summary report to go to that area on the map - measuring includes the title of the summary report |
| Click | Go to Bookmark | User clicked a bookmark in the search address modal to go to the bookmarked location on the map |
| Click | Infobox Custom Button Click *ButtonNameInLanguage* | User clicked a configurable button at the bottom of the information panel - measuring includes the label for the button |
| Click | Infobox Zoom In | User clicked the Magnify/Zoom button in the information panel |
| Click | Map Control Click - *MapOverviewInLanguage* | User clicked the Map Overview button in the map display options - measuring includes the label for the button |
| Click | Map Control Click - *SearchInLanguage* | User clicked the Search button in the map display options - measuring includes the label for the button |
| Click | Map Control Click - *MapZoomInLanguage* | User clicked the Map Zoom In button in the map controls - measuring includes the label for the button |
| Click | Map Control Click - *MapZoomOutInLanguage* | User clicked the Map Zoom Out button in the map controls - measuring includes the label for the button |
| Click | Map Control Click - Show My Location | User clicked the Show My Location button in the map display options to navigate on the map to their current GPS location |
| Click | Map Control Click - *ToggleLanguageInLanguage* | User clicked the Select Language button in the map display options to open the language selection modal - measuring includes the label for the button |
| Click | Save Infobox Bookmark | User clicked the Save Bookmark option associated with the bookmarks tool |
| Click | Search Address Panel - Show My Location | User clicked the Show My Location button in the search address modal |
| Click | Select Language - *LocaleCode* | User clicked a language name in the language selection modal - Locale code is "en-US" for English, "es-ES" for Spanish, or "fr-CA" for French |
| Click | Show/Hide Weather Radar | User clicked the Radar checkbox to show or hide the weather radar layer |
| Click | Toggle Header Tab - *TabName* | User clicked the access button for the overview panel or the help panel - measuring includes the label "tools" for the overview panel or the label "help" for the help panel |
| Click | Toggle Legend | User clicked the Map Legend button to open the map legend or the close icon on the map legend to close the map legend |
| Click | Toggle Service Areas On/Off | User clicked the checkbox to show or hide the service territory layer |
| Click | Toggle Tool - *ToolNameInLanguage* | User clicked the name of a tool in the overview panel to show or hide its content - measuring includes the label for the tool name |
| Click | Update Bookmark | User clicked the Update Bookmark button in the search address modal  |
| Click | Utility Logo | User clicked on the logo in the map header |
| Click | View Summary - *ReportNameInLanguage* | User clicked a summary report name to open the summary report - measuring includes the label for the report name |
| Click | Weather Animation On/Off | User clicked the Loop checkbox to turn weather animation on or off |
| Open Infobox | Open Infobox - *LayerName* | User clicked on an element on the map such as an outage location icon or shaded thematic area that opens the information panel - measuring includes the label for the data layer (active outages, planned outages, county, ZIP code, municipality, etc.) |

{{% notice note %}}
Zoom in and zoom out actions performed using a mouse wheel, double click, or pinch-to-zoom are **not** measured.
{{% /notice %}}
