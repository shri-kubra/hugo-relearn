---
title: "Custom Layers App"
weight: 33
---

To access the Custom Layers app, click the **Custom Layers** button on the Control Center Dashboard under "Apps."

You can use the Custom Layers app to add, edit, view, and delete ad hoc information items on the Storm Center outage map to communicate additional information to customers or other map users. The categories of information you can communicate are determined by the Information Area and Information Point categories set in the Custom Layers Admin tool.

![Custom Layers App - no content](/images/custom-layers-app-empty.png)

An **Information Area** is a shape you can draw on the map that is shaded with a specified color. You can use information areas to provide information about a geographical area.

![Information Area example](/images/custom-layers-app-information-area.png)

An **Information Point** is an icon you can add to the map that has a specified image. You can use information points to provide information about a specific location.

![Information Point example](/images/custom-layers-app-information-point.png)

## View Information Area or Information Point Data ##

First, decide whether you want to work with an Information Area or an Information Point. To open a list of existing Information Area or Information Point items, select the corresponding option from the **Select a Layer Type** drop-down menu.

After you choose the layer type you want to work with, you can add an item of that type to the map using the item editor. To open the item editor, click the green plus sign button below the filter and at the upper right of the list of information areas or information points.

For both Information Areas and Information Points, there are five parameters you can add using the item editor. You can use some or all of these parameters.

The item parameters are:

+ **Create Point/Area:** This defines the placement of the item on the Storm Center map, and differs depending on the layer type. For an Information Area, you must mark the area boundaries on the map. For an Information Point, you must select a location for the icon on the map.
+ **Name:** This identifies the item in the list of all items (Areas or Points). The Name will also be shown in the information panel for the item on the Storm Center map. If the name field is left empty, the information panel for the item will not show a name. There are separate Name fields for each language supported by the instance.
+ **Layer Type:** This defines the appearance of the item to be added to the map. The item type differs depending on the layer type. For an Information Area, the Type determines the color of the shaded area on the map. For an Information Point, the Type determines the image or icon on the map. The information panel for the item on the Storm Center map will show a label for the item type that matches the title for the category set up in the [Custom Layers Admin tool](/storm-center/management-console/custom-layers-admin).
+ **Notes:** This is a formatted content block that will be shown in the information panel for the item on the Storm Center map. You can insert hyperlinks, hypertext, or images in this field.
+ **Visible:** This is a checkbox to make the object visible or not visible on the Storm Center map. Items are visible by default.

![Example form with information area](/images/custom-layers-app-form-information-area.png)

![Example form with information point](/images/custom-layers-app-form-information-point.png)

## Add a New Item ##

To add a new Information Area or Information Point to the map, select the layer type from the **Select a Layer Type** drop-down and then click the green plus sign button.

![Create Item button](/images/custom-layers-app-create-button.png)

Navigate or search on the map to the location where you want to place the Information Area or Information Point and then click the **Create** button under **Create Point/Area**. When you move your mouse cursor over the map, it will change to a cross shape.

To place an Information Area, click on a corner of the shape you want to create, and then move the mouse cursor and click on each additional corner of the shape. To complete the shape, click again on the first corner you placed on the map.

To adjust the borders of the shape, click the **Edit** button under **Create Point/Area**. This will add dots to the shape on the map that you can click and drag to adjust the shape as needed.

To place an Information Point, click on the map where you want to put the Information Point icon.

To move the icon, click the **Edit** button under **Create Point/Area**. This will change the icon on the map to an icon of a flag that you can click and drag to any location on the map.

To save the shape or icon location when you have finished adjusting it, click the **Done Editing** button. To discard your changes, click the **Cancel Edit** button.

Enter a name, select a layer type, and add any notes related to the Information Area or Information Point. The layer type drop-down shows a preview of the area color or icon shape while it is open.

{{% notice note %}}
The Custom Layers tool supports a maximum file size of 8MB per custom layers item. KUBRA recommends using no more than 2,000 words or approximately 8,700 text characters, and no more than six total image files in the notes for a single custom layers item.
{{% /notice %}}

To save the Information Area or Information Point and make it visible on the map, click the **Visible** checkbox and then click the **Apply** button.

To save the Information Area or Information Point without making it visible on the map, leave the **Visible** checkbox unselected and then click the **Apply** button. You may want to do this if you are pre-configuring custom layers items to be shown later, such as during a storm.

The next time you select the Information Area or Information Point list, the item you created will be visible on the preview map on the right side of the Custom Layers tool, and you will see a note that says "Changes Not Yet Deployed."

To deploy your changes to the map or maps for the instance, click the **Deploy** button.

![Deploy button](/images/custom-layers-app-deploy-button.png)

## Edit an Item ##

To edit an existing Information Area or Information Point, select the layer type from the **Select a Layer Type** drop-down and then click on the row for the Information Area or Information Point you want to edit. The list includes a filter feature that allows you to filter the list by item type, whether the item is visible or not, item name, or item notes.

After you click on a specific Information Area or Information Point in the list, the item editor will open and allow you to:

+ Change whether the item is visible on the map
+ Edit the item's name
+ Change the item's layer type
+ Adjust the borders of the information area shape or the location of the information point icon
+ Edit any associated notes

To quickly open the preview map at the location of the item, click the **Go To** button under **Create Point/Area**.

To save your changes and return to the list of items, click the **Save** button. To discard your changes, click the **Cancel** button.

Whenever you save changes to an Information Area or Information Point, the changes will not be deployed to the map or maps for the instance until you click the **Deploy** button.

## Remove an Item ##

To remove an Information Area or Information Point from the map, select the layer type from the **Select a Layer Type** drop-down and then click on the row for the Information Area or Information Point you want to remove. The list includes a filter feature that allows you to filter the list by item type, whether the item is visible or not, item name, or item notes.

After you click on a specific information item, the item editor will open. To delete the item, click the **Delete** button at the bottom of the item editor. To confirm that you want to delete the item, click **OK** in the confirmation window. To cancel and keep the item, click the **Cancel** button.

### Bulk Import Items ###

The Custom Layers app allows you to import information for multiple Information Area items or multiple Information Point items using an Excel Strict Open XML Spreadsheet (.xlsx).

To import a new file with Custom Layers data:

1. Create a new Information Area file or Information Point file following the format described below. You can use the **Export** button to download a template with the correct headings.
2. Select Information Areas or Information Points from the "Select a layer type" drop-down in the Custom Layers app. Select the option that matches the layer type of the file you created.
3. Click the **Import** button.
4. Drag and drop the file from your desktop into the upload area or click the **Browse Computer** button to locate the file and then select "Open."

{{% notice note %}}
When you import a new file, all existing items of the selected type (either information area or information point) will be replaced by the data in the file. If you upload a file that includes only a header line, all existing items of the selected type will be removed.
{{% /notice %}}

#### Custom Layers Import File Format ####

The maximum supported file size for custom layers import is 1 GB. Custom layers import supports a maximum of 1000 custom layers items per file.

A file must include either Information Areas or Information Points, not a mix. The file must include at least one empty row to indicate the end of the list of custom layers items.

| Attribute | Required? | Description |
| --------- | --------- | ----------- |
| Type | Yes | String - defines the appearance of the item to be added to the map. The string must match one of the **Name** values defined in the Custom Layers Admin tool. You can see the **Name** values in the Layer Type drop-down field when you create or edit an item in the Custom Layers app. Type values are case-sensitive. |
| Visible | Yes | Boolean - indicates whether to show the item on the Storm Center map. If `true`, the item will be visible. If `false`, the item will not be visible on the Storm Center map. |
| Geometry | No | String - a set of coordinates representing the area for the Information Area or the location for the Information Point icon, in {{<extlink title="WKT" url="http://docs.opengeospatial.org/is/12-063r5/12-063r5.html">}} format. Information Area files will accept the LineString, Polygon, or MultiPolygon types. Information Point files will only accept the Point type. |
| Name (one column for each supported language: "Name en-US," "Name es-ES," or "Name fr-CA") | No | String - a name to identify the item in the Custom Layers app and at the top of the information panel for the item on the Storm Center map. If you do not provide a name for an item, the header of the information panel on the Storm Center map will be blank. |
| Notes (one column for each supported language: "Notes en-US," "Notes es-ES," or "Notes fr-CA") | No | String - notes related to the item that will appear in the information panel for the item on the Storm Center map. Notes can be either plain text or html formatted. For example, bold text in this field must be indicated with HTML tags such as `<b></b>`.|

If you do not include a `Geometry` attribute for one or more custom layers items, you must add the geometry in the Custom Layers app before the item can be shown on the Storm Center map.

{{% notice note %}}
Images are not supported in the `Notes` attribute for Custom Layers import files.
{{% /notice %}}

#### Geographic Coordinate System for Geometry Elements ####

Information Area files and Information Point files can include a `geometry` attribute in {{<extlink title="Well-known text (WKT)" url="https://en.wikipedia.org/wiki/Well-known_text">}} format. Of the geometric objects supported by WKT, information areas will accept LineString, Polygon, and MultiPolygon, and information points will accept only Point.

Coordinate pairs must be presented with the longitude followed by the latitude. The coordinate points of each geometry element must be provided in EPSG:4326, also known as WGS84. There is currently no support for providing coordinates in other geographic projection systems. For details about the EPSG:4326 coordinate system, access the {{<extlink title="specification provided by Spatial Reference" url="https://spatialreference.org/ref/epsg/wgs-84/">}}.

The Open Geospatial Consortium standard for WKT requires a polygon to be topologically closed. If the exterior linear ring of a polygon is defined in a counter clockwise direction, it will be seen from the "top."

### Bulk Export Items ###

Custom Layers allows you to export data for all currently entered Information Areas or Information Points in Excel Strict Open XML Spreadsheet (.xlsx) format.

To bulk export data:

1. Select Information Areas or Information Points from the "Select a layer type" drop-down in the Custom Layers app.
2. Click the **Export** button.

An exported file of Information Areas will be called **informationareas.xlsx**. An exported file of Information Points will be called **informationpoints.xlsx**.

{{% notice note %}}
Images are not supported in the `Notes` attribute for Custom Layers export files. If any of the existing custom layers items have images in the Notes field, those images will be omitted from the exported file.
{{% /notice %}}

### Bulk Delete Items ###

Custom Layers allows you to delete data for all currently entered Information Areas or Information Points.

To bulk delete data:

1. Select Information Areas or Information Points from the "Select a layer type" drop-down in the Custom Layers app.
2. Click the **Delete All** button.

The Custom Layers app will ask you to confirm the delete action.

## Deploy Custom Layers Changes to Storm Center Maps ##

Whenever you save a change in the Custom Layers app, a message will appear at the top of the app that says "Changes Not Yet Deployed." To deploy your changes to the Storm Center map, click the **Deploy** button.

![Deploy button](/images/custom-layers-app-deploy-button.png)

After you deploy changes, the message will disappear and the **Deploy** button will become unselectable.
