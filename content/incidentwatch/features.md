+++
title = 'Feature List'
weight = 2
+++

The following diagram shows the different parts of the IncidentWatch map interface.

![IncidentWatch map wireframe](/images/incidentwatch_map_wireframe.jpg)

## Map Header

The map header at the top of the map includes a button for the tool panel as well as a search box. The header can optionally include an Organization logo with a link.

### Open Tool Panel Button

The button in the upper left corner of the map opens and closes the map tool panel. This button can optionally include a text label such as “Menu.”

### Search

The search box allows users to enter an address, city name, or ZIP code to navigate to a specific location on the map. The search function is powered by Google Maps.

## Map Legend

The map legend defines the color-coding used for asset or incident icons and the location the user has searched for, if any. For desktop browsers, the map legend appears directly below the map header. For mobile browsers, a button to open the legend appears in the map navigation tools.

### Status Banner

The status banner appears at the top of the map under the header as users interact with the map. It provides prompts and updates about the status of the map. For example, if a user has not yet zoomed in enough to view asset icons, the status banner prompts the user to zoom in further.

## Tool Panel

The tool panel opens to the left side of the map and contains configurable information about the assets included on the map, tools for adjusting map settings, and help information. The tool panel can be configured to be open or closed on page load.

### Information

The Information section of the tool panel can include general information about the assets included on the map, any relevant safety information, and phone numbers or other contact information for incidents that should be reported through other channels, such as down wires or gas leaks.

### Map Styles

The Map Styles section of the tool panel includes a drop-down list that allows users to change the map background between Road, Satellite, and Hybrid.

### Help

The Help section of the tool panel includes information about how to search for an address, how to select an ad hoc location, and how to submit an incident report.

## Map Navigation

The map navigation is a collection of buttons at the upper left corner of the map, to the right of the tool panel when the tool panel is open.

For desktop browsers, the buttons from top to bottom are:

+ Zoom in
+ Zoom out
+ Zoom to location (requires the user to allow location services)

For mobile browsers, the buttons from top to bottom are:

+ Open map legend
+ Zoom in
+ Zoom out
+ Zoom to location (requires the user to allow location services)

## Map Background

The map background uses the Google Maps API and includes up to three options: road, satellite, and hybrid.

## Service Territory Boundary

The map can include an outline of the Organization's service territory to let users know where they can and cannot submit incident reports. If an Organization partners with other organizations in the same area, the map can also include outlines of those organizations' service territories.

## Asset or Incident Location Icons

The IncidentWatch map shows locations of assets tracked by the Organization as well as locations of assets with issues reported by users of the map. The color and symbol of the icon indicates the status of the asset or incident. Icon shapes, colors, and status descriptions are configurable.

If an Organization does not want to pre-load asset locations on the map, users can still choose a location on the map to report an incident.

## Information Panel

When users interact with an asset or incident icon, an information panel opens from the right side of the map (for desktop browsers) or the bottom of the map (for mobile browsers).

Information panels can include any combination of the following data:

+ Asset Type
+ Responsible Organizations
+ Pole Number
+ Asset Status
+ Report Form Link (for report forms not managed in IncidentWatch)
+ Report Incident Button (opens report form in information panel)
+ Asset Image
+ Asset Description

### Report Form

When users choose to report an incident for an asset or at a location they have specified, the information panel contents will change to a report form.

Incident report forms can include any combination of the following data:

+ Contact Name
+ Phone Number
+ Email
+ Problem Type
+ Pole Number
+ Comments
+ Cross Streets
+ Address of Incident
+ Acknowledgement
+ Opt-In for Email Updates

## Email Updates

IncidentWatch can be configured to provide status updates via email to Organization employees, users who have reported an incident, or both. KUBRA configures these update messages as part of an IncidentWatch implementation project. The Organization can design a status workflow; specify which incident status transitions will trigger email updates to employees, customers, or both; and provide wording for the update messages.
