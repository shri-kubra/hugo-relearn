---
title: "Create Outage Data Layers"
weight: 14
---

Typically, a Storm Center outage map provides two kinds of layers for showing outage information. One kind of layer shows outage location icons for individual outages and cluster icons for groups of outages. The other kind of layer shows the number or the percentage of customers affected by outages by shading a geographical area such as a county, municipality, or postal code area.

When creating an Additional Map Layer, refer to the [Create Additional Map Layer page](/storm-center/configuration-guide/create-AML-data-layers).

To create an outage data layer, use the **Data Layers** sub-section of the **Shared Resources** section of the Instance Dashboard.

## Layer Name, Source, and Titles ##

1. Click the **Create Data Layer** button.
1. Enter a name for the layer - this name is how you will identify the layer in other areas of the Instance Manager; it will not show up on the map.
1. Select an access restriction policy. The options available in the drop-down come from the policies created in the [Access Restriction section](/storm-center/configuration-guide/#create-access-restriction-policies) of the Instance Dashboard.
1. Select a layer type.
    + "Thematic" is for showing outages by area and has a source type of ZIP (postal code), County, Cities/Towns/Villages (CTV), or a Custom thematic name, depending on the thematic file types you uploaded when you [set up thematic data](/storm-center/configuration-guide/connect-data-files/#set-up-thematic-data) for the instance.
    + "Outages" is for showing active outages by location and includes cluster icons for representing groups of nearby active outage locations.
    + "Planned" is for showing planned outages by location and includes cluster icons for representing groups of nearby planned outage locations. This layer type is only available with the Planned Outages module.
1. Enter titles for the layer for each language supported by the instance - these titles will be used at the top of the information panels on the map.
    + If you want to use the name of the specific area (such as the county name) as the information panel title, enter `${name}` in the layer title fields.
    + If you want to include the name of the state in the information panel title, enter `${hierarchy.state}` in the layer title fields.
    + For an Outages layer, a Planned layer, or an Additional Map layer, enter a title for the information panels associated with individual outage icons and a title for the information panels associated with cluster icons.
    + KUBRA recommends a maximum of 15-20 characters for these titles. You may need to adjust the length or formatting of the titles after testing them on a map to ensure that they display and wrap well.

## Layer Data Source and Information Panel Fields ##

1. Under Layer Sources, select the region data you want to associate with the layer.
1. Under Information Panel Fields, select the data fields you want to include in the information panels for the layer.

The following table shows which data fields are available for thematic layers, for individual location icons in an outages layer, for cluster icons in an outages layer, for individual location icons in a planned layer, for cluster icons in a planned layer.

| Data Field | Thematic Layer | Individual Location - Outages Layer | Cluster - Outages Layer | Individual Location - Planned Layer | Cluster - Planned Layer |
| ------- | ------- | ------- | ------- | ------- | ------- |
| Cause                            |   | X |   | X |   |
| Comments                         |   | X |   | X |   |
| Crew Status                      |   | X |   |   |   |
| Duration                         |   |   |   | X |   |
| End Time                         |   |   |   | X | X |
| Estimated Restoration Time       | X | X | X |   |   |
| Incident ID                      |   | X |   | X |   |
| Metadata                         |   | X |   | X |   |
| Number of Customers Affected     | X | X | X | X | X |
| Number of Customers Served       | X |   |   |   |   |
| Number of Outages                | X |   | X |   | X |
| Percentage of Customers Affected | X |   |   |   |   |
| Start Time                       | X | X | X | X | X |

### Metadata Fields - Additional Data for Outage Location Information Panels ###

In addition to the standard data fields, you can optionally define one or more **Metadata** fields to display additional types of data in the information panels for individual outage locations or individual planned outage locations.

To add a metadata field, click the **Add Metadata Field** button in the Individual Data subsection of the Information Panel Fields section for an Outages layer or a Planned layer.

1. Provide a name for the metadata field. This name must match the name of a metadata element property supplied in outage data files submitted to Storm Center.
1. Select a data type from the drop-down. Options are
    + string
    + number
    + percentage
    + datetime
    + HTML markup

{{% notice note %}}
Element names are case-sensitive. Ensure you think about case when naming elements.
{{% /notice %}}

## Data Mapping for Outages Layers and Planned Outage Layers ##

The Field Mappings selection of the data layer form associates data field mapping with one or more field types in the data layer. This allows the map to mask field values from an outage file, or planned outage file with customer-friendly or public-facing values.

If you want to provide mapping for one or more data fields in the information panel for individual active or planned outage location icons, click the **Submit** button at the bottom of the Create Data Layer form to save your in-progress layer and then follow the instructions to [create data mapping](/storm-center/configuration-guide/create-data-labels/#outage-data-mapping).

After you create the data mapping you want to use, return to the edit data layer form under Data Layers and click the **Add Field Mapping Relationship** button. Next, select a data field from the drop-down and then select the mapping name.

{{% notice note %}}
Data mapping can only be provided for crew status, cause, and metadata fields. Planned outage layers can include cause and metadata fields, but do not include crew status fields.
{{% /notice %}}

## Extra Text for Information Panels ##

The Infobox Extra Text section of the data layer form associates configurable content blocks with the information panels in the data layer. This allows the map to show additional content at the bottom of the information panels, and can include different content for individual outage icon information panels than for cluster icon information panels.

If you want to include extra content at the bottom of the information panels, click the **Submit** button at the bottom of the create data layer form to save your in-progress layer and then follow the instructions to [create a configurable content block](/storm-center/configuration-guide/create-buttons).

After you create the content blocks you want to use, return to the edit data layer form under Data Layers and select the content block name from the **Info Panel Content Block** drop-down field for the information panel you want to add the content to.

Storm Center can optionally include expanded cluster information panels at some zoom levels. These information panels are associated with a cluster icon, but they show information for each of the individual outages elements included in the cluster. If you provide extra text for individual outage icon information panels, that text will also appear in the outage cards for each outage in an expanded cluster information panel.

## Additional Settings for Outages Layers and Planned Outage Layers ##

1.  Crew Icon Indicator on individual outage location icons when the outage data indicates a crew is on site at the location can be defined in **Range Expressions**. However, you still need to click the **Enable Crew Icon Indicator** checkbox to ensure the crew icon is visible. This setting is not applicable for Planned Outage Layers.
    + Crew indicators will be shown on the map when all of the following are true:
	    + this setting is enabled
	    + the data provided in the outage data feed for an outage location indicates that there is a crew at the location
      + `crew_icon` is set to `true` in **Range Expressions** for that outage layer
1. If you do not want to display polygons behind individual outage location icons to indicate the area affected by the outage when an outage affects three or more delivery nodes, click the **Disable Polygons** checkbox.
1. Provide zoom settings and cluster tolerance.
    + Enter a maximum zoom level at which to combine outage location icons into Clusters.
    + Enter a zoom level at which to provide expanded outage information in the information panels for outage cluster icons - KUBRA recommends setting this zoom level one level below the **Max Zoom to Cluster** setting. If you do not want to show individual outage information in cluster icon information panels at any zoom level, set the **Start Zoom to Paginate Outage** to -1.
    + Select a Cluster Tolerance Level on the slider between 20 and 40.

{{% notice tip %}}
The recommended Cluster Tolerance Level is based on the size of the outage location and cluster icons. If you are using the default WCAG-compliant icon set, KUBRA recommends setting the cluster tolerance to 35.
{{% /notice %}}

## Estimated Restoration Time Settings ##

1. If you want to show expired estimated restoration time (ETR) values in the information panels for the layer, clear the **Mask Expired ETR** checkbox. This checkbox is selected by default. You may want to clear this checkbox if you are creating an internal-facing map and want to see all ETRs as reported from the source system for outage data, for example.
1. Select an ETR grouping condition - options are "Latest ETR Any" and "Latest ETR All."
    + "Latest ETR Any" means that the map will display the latest ETR for outages in the cluster or area if **any** of the outages has a specific, valid ETR (not null or expired). If none of the outages in the cluster or area has a specific, valid ETR, the map will display the default message specified for null or expired ETRs in the [Data Labels](/storm-center/configuration-guide/create-data-labels) sub-section of the **Shared Resources** section.
    + "Latest ETR All" means that the map will display the latest ETR for outages in the cluster or area only if **all** of the outages have a specific, valid ETR (not null or expired). If any of the outages in the cluster or area has a null or expired ETR, the map will display the default message for null or expired ETRs.

{{% notice note %}}
The Planned layer type uses these settings for the "End Time" field.
{{% /notice %}}

## Range Styles for Outage, Thematic, Planned Outage, and Additional Map Layers ##

You can customize how a Storm Center layer looks by writing a JSON object. For a map data layer, each JSON object consists of properties representing the ranges.

Storm Center provides 3 choices to assist you in writing your JSON object.

1. Select a pre-existing template under **Apply Styling Template**, modify if needed
OR
1. Copy a template from another layer in the same instance, modify if needed
OR
1. Write your own JSON object.

This table lists all the choices you have while writing or editing a range on a JSON object.

| JSON property | Description | Possible use cases |
| ------- | ------- | ------- |
| `legendOrder` | Decides the order of the defined range in the legend. | A legend order of `-1` will hide this range style from the legend. |
| `rangeExpr` | Decides range conditions. | See [Range Expressions](/storm-center/configuration-guide/create-outage-layers/#range-expressions) for more details. |
| `rangeLabel` | Defines the range label for each range, appears to the right of the icon in the map legend. | Each defined range should have range labels in all languages supported for that instance of Storm Center. KUBRA recommends a maximum of 25 characters for these labels. |
| `rangeStyles` | Defines the styles associated with a range. | Since it is an object that contains the styles, all options under **Range Styles** will be included in the table with a dot notation. |
| `rangeStyles.shape` | Defines all the characteristics of a polygon shape. | These characteristics exist when there is a shape to represent for thematics or outage polygons. |
| `rangeStyles.shape.borderColor` | Defines the polygon's border color. | Use Hex color codes. |
| `rangeStyles.shape.borderOpacity` | Defines the polygon's border opacity. | Accepts a decimal value between and including 0 and 1. |
| `rangeStyles.shape.borderWeight` | Defines the polygon's border weight. | Accepts an integer value equal to or greater than 0. |
| `rangeStyles.shape.fillColor` | Defines the polygon's fill color. | Use Hex color codes. |
| `rangeStyles.shape.opacity` | Defines the polygon's opacity. | Accepts a decimal value between and including 0 and 1. |
| `rangeStyles.icon` | Defines all the characteristics of the icon specific to that range. | These characteristics exist when there is an icon to represent the outage location. |
| `rangeStyles.icon.url` | Defines the url for the icon. | KUBRA requires using the path URL from Image Resource Manager for this purpose. |
| `rangeStyles.icon.size` | Defines the icon size. | Provide a width and height in pixels for the icon. Input accepted is an array [width, height]. |
| `rangeStyles.icon.anchor` | Defines the icon anchor. | The coordinates of the "tip" of the icon (relative to its top left corner). The icon will be aligned so that this point is at the marker's geographical location. Input accepted is an array [x,y]. |
| `rangeStyles.icon.labelValue` | Displays a map label for that icon. | Clients can request specific values they want the label to display. You can use properties of the record for the label value, for example `${n_out}`, `${cust_a.val}`. |
| `rangeStyles.icon.labelAnchor` | Defines the icon label anchor. | The coordinates of the "tip" of the icon label (relative to its top left corner). The label will be aligned so that this point is at the marker's geographical location. Input accepted is an array [x,y]. |
| `rangeStyles.icon.opacity` | Defines icon opacity. | Accepts a decimal value between and including 0 and 1. |

### Range Expressions ##

A range expression is a JSON property which decides range definition conditions. Conditions are defined over data fields. Each data field supports specific operators depending on the data type of the field.

{{% notice note %}}
Range expressions can include one or more conditions using the && (AND) and || (OR) operators.
{{% /notice %}}

You can use the following conditions to define a range.

| Condition | JSON parameter | Data type | Special features |
| ------- | ------- | ------- | ------- |
| Cluster | `cluster` | boolean | Special field indicating if the map element corresponds to a cluster or not. |
| Cause | `cause` | string, JSON object | Supports mapping tables; view warning below when using mapping tables for Range Expressions.  |
| Number of customers affected | `cust_a.val` | integer | To access the `value` of `cust_a`, use the `cust_a.val` parameter. |
| Percentage of customers affected | `perc_cust_a.val` | integer | To access the `value` of `perc_cust_a`, use the `perc_cust_a.val` parameter. |
| Comments | `comments` | string | No special features. |
| Crew icon | `crew_icon` | boolean | To determine whether the crew icon is shown for the outage location on the Storm Center map. If **True**, the crew icon will be shown. If **False**, the crew icon will not be shown. However, you still need to click the **Enable Crew Indicator** checkbox to confirm the icon will be visible. |
| Crew status | `crew_status` | string, JSON object | Supports mapping tables; view warning below when using mapping tables for Range Expressions. |
| Metadata | `metadata` | JSON object, supports integer, string, boolean | Elements within the Metadata property support mapping tables depending on the configuration; view warning below when using mapping tables for Range Expressions. |
| Number of outages | `n_out` | integer | No special features. |

When using mapping tables for a range expression, you should reference mapping table languages with square brackets like `parameter['language']`. The languages available are EN-US, ES-ES, es-US, and fr-CA. For example, accessing the cause in French would be `cause['fr-CA']`. Ideally, we recommend using the default language used when creating the instance when you reference a language in the mapping table.

Ensure you have an additional condition defining the parameter as not equal to null (to avoid an error when parsing the expression).

For example, "cause != null". "cause != null && cause['EN-US'] == 'Planned maintenance'" is an example of a condition that supports mapping tables.

The table below indicates the operators allowed with data types used in Range Expressions.

| Data type | Operators allowed |
| ------- | ------- |
| boolean | OR, AND, ==, !=, unary operator (!a) |
| string | OR, AND, ===, ==, !==, !=, can use (<, >, <=, >=) operators when lexical and case dependent matching |
| integer | OR, AND, ===, ==, !==, !=, <, >, <=, >=, +, -, *, /, unary operators (+a, -a, !a) |

Specific data fields are available for Range Expressions that work only with specific layers. Refer to the [Layer Data Source and Information Panel Fields](/storm-center/configuration-guide/create-outage-layers/#layer-data-source-and-information-panel-fields) for more clarity.

For a sample template for each data layer type, refer to the sample JSON object attached below.

{{<attachments title="JSON templates" style="blue" />}}

### KUBRA-recommended icons and color/shape combinations ###

{{% notice note %}}
Storm Center recommends using a combination of color and shape for location icons to help users with color vision deficiency. In addition, the colors for the recommended icons were selected to provide adequate contrast with the white color used for the icon shapes and with the background map.
{{% /notice %}}

{{% notice tip %}}
KUBRA recommends using the following image sizes (in pixels):
24x24 up to 32x32 for individual outages and 40x40 for outage clusters
{{% /notice %}}

#### Icons for Outage layers ####

These are the default KUBRA-recommended ADA-compliant icons for an outage layer or cluster outage layer:

 + Blue Circle
 + Yellow Star (five-pointed)
 + Purple Triangle
 + Red Diamond
 + Green Square
 + Orange Equals Sign
 + Pink Star (six-pointed)
 + Cluster

![WCAG-compliant outage location icons](/images/default-active-outage-icons.png)

These are the default KUBRA-recommended ADA-compliant icons for an outage layer with crew dispatched:

  + Blue Circle with crew
  + Yellow Star (five-pointed) with crew
  + Purple Triangle with crew
  + Red Diamond with crew
  + Green Square with crew
  + Orange Equals Sign with crew
  + Pink Star (six-pointed) with crew

![WCAG-compliant outage location icons with crew](/images/default-active-outage-icons-crew.png)

Shown below is the default KUBRA single outage location icon.

![Single outage location icon](/images/single-active-outage-icon.png)

Shown below is the KUBRA outage location crew icon.

![Outage location crew icon](/images/default-crew-icon.png)

#### Color combinations for thematic layers ####

These are the KUBRA-recommended ADA-compliant colors for thematic area:

  + Blue
  + Green
  + Purple
  + Red
  + Yellow
  + Orange
  + Pink
  + Gray

![WCAG-compliant thematic area colors](/images/default-thematic-area-colors.png)

#### Icons for Planned Outage layers ####

These are the KUBRA-recommended ADA-compliant Planned outage icons:

+ Blue Circle
+ Yellow Star (five-pointed)
+ Purple Triangle
+ Red Diamond
+ Green Square
+ Orange Equals Sign
+ Pink Star (six-pointed)
+ Cluster

![Planned outage location icons](/images/default-planned-outage-icons.png)

Shown below is the default KUBRA single planned outage icon.

![KUBRA-recommended single planned outage location icon](/images/single-planned-outage-icon.png)

## Legend Labels ##

The map legend includes an introductory label to indicate what the numbers for each range refer to. For example, if you chose "Customers Affected" as the method for determining ranges, you could use "Customers Affected" or "Affected by Outages" as the Legend Label.

Enter labels to be used on the map legend for each language supported by the instance. KUBRA recommends a maximum of 25 characters for the map legend labels.

## Layer Field Labels ##

You can determine the order of the data fields shown in the information panel for the layer and provide labels for each field. Data fields are arranged vertically - the field with order 1 will be at the top of the information panel, followed by the field with order 2, and so on.

Choose an order for each data field and enter labels for each language supported by the instance. Labels for mobile browsers should be shorter than labels for desktop browsers so they can be read on a narrow screen.

{{% notice tip %}}
If you want to include punctuation after the field labels in the information panel, you **must** include the punctuation in the text fields here.
{{% /notice %}}

KUBRA recommends a maximum of 45 characters for information panel field labels. You may need to adjust the length or formatting of the labels after testing them on a map to ensure that they display and wrap well.

{{% notice note %}}
The field labels and order for Start Time, Estimated Restoration Time, End Time, and Number of Customers Affected are shared by the information panels for individual outage locations and outage clusters.
{{% /notice %}}

## Buttons for External Links ##

If you want to add one or more buttons to the bottom of the information panels for the layer, click the drop-down under **Custom Footer Buttons** and then select a button name from the list.

Before you can select a button here, you must [create buttons](/storm-center/configuration-guide/create-buttons).

## Customers Affected Masking ##

1. If you want to mask the exact number of customers affected at or below a specific value, click the **Customer Masking** checkbox and then enter a number.
1. If you want to mask the exact percentage of customers affected at or below a specific value, click the **% Customer Masking** checkbox and then enter a number.

The value or values you enter for customer masking here will be combined with verbiage you enter in the **Shared Resources** section of the [Create New View form](/storm-center/configuration-guide/create-map-view/#shared-resources) to create a label on the map such as "Fewer than 5" or "Less than 10%."
