---
title: "Storm Center"
url: storm-center
type: index
weight: 1
---

## What is Storm Center? ##

Storm Center is KUBRA's online outage map product. Storm Center uses outage data provided by an organization such as a utility company to show information about power outages on an interactive online map. Customers can access the map from a link on the utility's website to see information about outages in their area or across the utility's service territory.

The Storm Center product is deployed on a multi-tenant architecture supported by Amazon Web Services. All clients (utility companies) who use Storm Center to create maps for their customers use the same Production environment but have separate instances. A single client can have multiple instances, such as an instance for testing configurations or data feeds and an instance for live maps. Each instance can include multiple maps, such as a map for the public, a map for inclusion in a mobile app, and a map for employees.

## Benefits of Storm Center ##

| Benefits |  |
------ | -----------
Quick implementation | Instance Manager makes it easy to set up and launch a new map
Highly configurable | Instance Manager includes many options for controlling data and views on a map
Flexible structure | Supports multiple maps for different audiences that use the same data feeds, map layouts with or without a header, and multiple options for embedding maps in websites and applications
Durable and scalable infrastructure | Amazon Web Services resources adjust to support user traffic while taking advantage of economies of scale
Standardized features | Based on KUBRA's years of experience building outage maps for utilities
Mobile-friendly design | Allows customers to access maps from desktop and mobile web browsers
Multilingual interface | Map and information can be displayed in English, French, and Spanish
Ongoing updates | Multi-tenant architecture allows KUBRA to provide updates to all clients at the same time without altering production map configurations

### Interactive Map with Responsive Design ###

The Google Maps API provides the background map. The map interface allows users to search for an address, use location services to zoom to their current location, or pan and zoom manually. Responsive design supports both desktop and mobile web browsers, which is especially important for customers experiencing power outages, who may only be able to view the map from a mobile device using cellular data for internet access.

Storm Center maps can show outage data in two main ways: by location and by area. All views include information panels with information about outages, such as

+ the number of customers affected
+ an estimated restoration time
+ the cause of the outage
+ the start time of the outage

An organization using Storm Center can choose which types of information to provide in the information panels based on the data available in an Outage Management System or other outage data source.

### Outage Information by Location ###

Storm Center maps represent outage locations using icons with color coding and shapes based on the number of customers affected by the outage. At zoom levels that show a bigger area such as an entire state or multiple states, outage location icons which are close together are grouped into cluster icons. Outage clustering is based on the distance between outage location icons at a particular zoom level, screen size, and browser window size. Different devices may therefore see different arrangements of cluster icons.

### Outage Information by Area ###

Storm Center maps represent outage locations by area using color-coded shading based on the number or the percentage of customers affected by outages in the area. A Storm Center map can have more than one type of area represented, so users can switch between viewing outages by county and viewing outages by ZIP code, for example.

## Maps with Access Restrictions ##

Storm Center supports both public maps and "internal" maps or other maps that include access restrictions. This allows authorized users to access a different map than the general public, which can include additional information such as outage ID numbers and internal comments. By default, users are logged out of maps with access restrictions after 2 hours of inactivity.

## Supported Browsers ##

KUBRA strives to provide compatibility with a range of browsers to make our software widely accessible while also using modern web design and security practices that may limit compatibility with some legacy browsers. For Storm Center maps, the following browsers are officially supported.

### Desktop Browsers ###

+ Google Chrome - current version and previous version
+ Mozilla Firefox - current version and previous version
+ Apple Safari - current version and previous version on Mac OS X
+ Microsoft Edge - current version

### Mobile Device Browsers ###

For mobile devices, support is limited to the stock web browser installed on the device by the manufacturer.

+ Google Android - current version of Chrome on Android 4.4+
+ Apple iOS - Mobile Safari on the current and previous major versions of iOS

{{% notice note %}}
Storm Center 5 does not support landscape mode in mobile devices.
{{% /notice %}}

## Admin Features ##

The Storm Center product includes a management console called Control Center. Control Center allows admin users at a utility to manage some of the configurable features of their deployed maps.

Control Center includes tools for managing

+ Update Interval Note - tells users of the map how often data on the map is updated
+ Page Mode - allows a different default map view choice for blue-sky or storm situations, as well as URL redirects for map maintenance
+ Alert Banner - a banner at the top or bottom of the map with a link to a longer alert message that can communicate storm updates, upcoming maintenance, etc.
+ Custom Layers - ad hoc icons and area shading that can provide information about ice distribution, shelters, flood zones, etc.
+ Overwritten Data - allows administrators to overwrite Estimated Restoration Times, Customers Affected numbers, or both for the individual areas on the map

Storm Center also includes an admin tool for viewing historical outage data. This Map History tool allows administrators to review outage data from up to five years ago on a map interface similar to a Storm Center outage map.

{{% notice note %}}
Some admin features are provided as additional-cost modules to the Storm Center product.
{{% /notice %}}

## Implementing Storm Center ##

To set up a new Storm Center instance, start by reviewing the [Getting Started](/storm-center/getting-started) document.
