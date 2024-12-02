---
title: "Analytics"
weight: 35
---

KUBRA uses Google Analytics Universal (GAU) and Google Analytics 4 (GA4) to track information about how users interact with Storm Center maps. These Analytics tools collect information from the map web page such as button clicks and anonymous information from the user's browser such as language preference, browser version, and the device and operating system type.

GAU and GA4 data from Storm Center maps helps KUBRA improve the map interface, optimize the data flow, and help organizations providing Storm Center maps to their customers to understand how those customers are using the map.

A GAU tracking code managed by KUBRA is included in all Storm Center maps. Since Google announced the sunsetting of GAU, KUBRA advises organizations to add their own Google Analytics 4 measurement ID when they [create a new map view](/storm-center/configuration-guide/create-map-view/#general-information). Organizations can also work with KUBRA support to update or replace organization-managed Google Analytics Universal codes for existing map views.

KUBRA supports five tracking codes for GAU and five measurement IDs for GA4. One tracking code for GAU and one measurement ID is already prepopulated for the platform on which Storm Center is built, in addition to one another tracking code and measurement ID for Storm Center itself. So, KUBRA supports adding three more codes/IDs to Storm Center.

We have separated the tracked events for GAU and the measured events for GA4 on their own pages.

The [Google Analytics Universal page](/storm-center/analytics/google-analytics-universal) details the interactions GAU tracks for Storm Center.

The [Google Analytics 4 page](/storm-center/analytics/google-analytics-4) details the interactions GA4 measures for Storm Center.

{{% notice warning %}}
[Google has announced a sunset date for Google Analytics Universal](https://support.google.com/analytics/answer/11583528) (July 2023). They recommend companies make the switch to or add Google Analytics 4 as soon as possible.
{{% /notice %}}
