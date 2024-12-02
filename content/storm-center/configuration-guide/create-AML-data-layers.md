---
title: "Create AML Data Layers"
weight: 15
---

Storm Center also allows you to display additional data like hazards, gas outages, flooding etc. on your public or internal Outage Maps using Additional Map Layers.

To create an Additional Map Layer, use the **Data Layers** sub-section of the **Shared Resources** section of the Instance Dashboard.

{{% notice warning %}}
Additional Map Layers can only be created once you have outage maps; they cannot exist in isolation.
{{% /notice %}}

## Layer Name, Source, and Titles ##

1. Click the **Create Data Layer** button.
1. Enter a name for the layer - this name is how you will identify the layer in other areas of the Instance Manager; it will not show up on the map.
1. Select an access restriction policy. The options available in the drop-down come from the policies created in the [Access Restriction section](/storm-center/configuration-guide/#create-access-restriction-policies) of the Instance Dashboard.
1. Select a layer type. For an Additional Map Layer, select AML.
    + "AML" is for showing non-outage data on a map layer. This layer type is only available with the Additional Map Layer module.
1. Enter titles for the layer for each language supported by the instance - these titles will be used at the top of the information panels on the map.
    + If you want to use the value of the specific property (such as the name) as the information panel title, enter ``${name}`` in the layer title fields..
    + Enter a title for the information panels associated with individual icons and a title for the information panels associated with cluster icons.
    + KUBRA recommends a maximum of 15-20 characters for these titles. You may need to adjust the length or formatting of the titles after testing them on a map to ensure that they display and wrap well.
1. Select the type of layer you want the AML to be. Your choices are **Client Cluster** or **Vector**.
    + Client Cluster - Allows for clustering to be done on your data. Allows both clustered icons and individual icons.
    + Vector - Allows the map to display data as-is, no clustering

## Layer Data Source and Information Panel Fields ##

1. Under Layer Sources, select the AML data you want to associate with the layer.
1. Under Information Panel Fields, use the **Add Data Fields** button to define each data field included in the Additional Map Layer data feed.

## Information Panel Fields and Data Fields for Additional Map Layers ##

AML GeoJSON files contain elements that you need to define for the layer. You can create data fields for an Additional Map Layer similar to how you currently create metadata fields for outage layers.

1. Define the element name indicated in the GeoJSON files
1. Define the element path to the element in the data feed
1. Input the Reduce function for this element. This is the operation/aggregation function you want to run on the AML data to display as a cluster
1. Select the data type for the element from the drop-down. Options are
    + string
    + number
    + datetime

{{% notice note %}}
Aggregation functions can only be run when the AML data type is string or number.
{{% /notice %}}

{{% notice note %}}
Element names are case-sensitive. Ensure you think about case when naming elements.
{{% /notice %}}

## Data Mapping for Additional Map Layers ##

The Field Mappings selection of the data layer form associates data field mapping with one or more field types in the data layer. This allows the map to mask field values from an AML file with customer-friendly or public-facing values.

If you want to provide mapping for one or more data fields in the information panel for AML icons, click the **Submit** button at the bottom of the Create Data Layer form to save your in-progress layer and then follow the instructions to [create data mapping](/storm-center/configuration-guide/create-data-labels/#outageaml-data-mapping).

After you create the data mapping you want to use, return to the edit data layer form under Data Layers and click the **Add Field Mapping Relationship** button. Next, select a data field from the drop-down and then select the mapping name.

## Additional Settings for Additional Map Layers ##

1. Provide zoom settings and cluster tolerance.
    + Enter a maximum zoom level at which to combine AML location icons into Clusters.
    + Enter a zoom level at which to provide expanded AML information in the information panels for AML cluster icons - KUBRA recommends setting this zoom level one level below the **Max Zoom to Cluster** setting. If you do not want to show individual AML information in cluster icon information panels at any zoom level, set the **Start Zoom to Paginate Outage** to -1.
    + Select a Cluster Tolerance Level on the slider between 20 and 40.

{{% notice tip %}}
The recommended Cluster Tolerance Level is based on the size of the AML location and cluster icons. If you are using the default WCAG-compliant icon set, KUBRA recommends setting the cluster tolerance to 35.
{{% /notice %}}

## Range Styles for Additional Map Layers ##

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
| `rangeExpr` | Decides range conditions. | See [Range Expressions](/storm-center/configuration-guide/create-AML-data-layers/#range-expressions) for more details. |
| `rangeLabel` | Defines the range label for each range, appears to the right of the icon in the map legend. | Each defined range should have range labels in all languages supported for that instance of Storm Center. KUBRA recommends a maximum of 25 characters for these labels. |
| `rangeStyles` | Defines the styles associated with a range. | Since it is an object that contains the styles, all options under **Range Styles** will be included in the table with a dot notation. |
| `rangeStyles.shape` | Defines all the characteristics of a polygon shape. | These characteristics exist when there is a shape to represent for AML polygons. |
| `rangeStyles.shape.borderColor` | Defines the polygon's border color. | Use Hex color codes. |
| `rangeStyles.shape.borderOpacity` | Defines the polygon's border opacity. | Accepts a decimal value between and including 0 and 1. |
| `rangeStyles.shape.borderWeight` | Defines the polygon's border weight. | Accepts an integer value equal to or greater than 0. |
| `rangeStyles.shape.fillColor` | Defines the polygon's fill color. | Use Hex color codes. |
| `rangeStyles.shape.opacity` | Defines the polygon's opacity. | Accepts a decimal value between and including 0 and 1. |
| `rangeStyles.icon` | Defines all the characteristics of the icon specific to that range. | These characteristics exist when there is an icon to represent the AML location. |
| `rangeStyles.icon.url` | Defines the url for the icon. | KUBRA requires using the path URL from Image Resource Manager for this purpose. |
| `rangeStyles.icon.size` | Defines the icon size. | Provide a width and height in pixels for the icon. Input accepted is an array [width, height]. |
| `rangeStyles.icon.anchor` | Defines the icon anchor. | The coordinates of the "tip" of the icon (relative to its top left corner). The icon will be aligned so that this point is at the marker's geographical location. Input accepted is an array [x,y]. |
| `rangeStyles.icon.labelValue` | Displays a map label for that icon. | Clients can request specific values they want the label to display. You can use properties of the record for the label value, for example `${n_out}`, `${cust_a.val}`. |
| `rangeStyles.icon.labelAnchor` | Defines the icon label anchor. | The coordinates of the "tip" of the icon label (relative to its top left corner). The label will be aligned so that this point is at the marker's geographical location. Input accepted is an array [x,y]. |
| `rangeStyles.icon.opacity` | Defines icon opacity. | Accepts a decimal value between and including 0 and 1. |

{{% notice note %}}
When styling mapped data fields, the original data has a `.orig` added to it. You can use `fieldName.orig` in your Range Expressions to avoid adding translations when performing data mapping.
{{% /notice %}}

### Range Expressions ##

A range expression is a JSON property which decides range definition conditions. Conditions are defined over data fields. Each data field supports specific operators depending on the data type of the field.

{{% notice note %}}
Range expressions can include one or more conditions using the && (AND) and || (OR) operators.
{{% /notice %}}

You can use the following conditions to define a range:

| Condition | JSON parameter | Data type | Special features |
| ------- | ------- | ------- | ------- |
| Cluster | `cluster` | boolean | Special field indicating if the map element corresponds to a cluster or not. |
| Cause | `cause` | string, JSON object | Supports mapping tables; view warning below when using mapping tables for Range Expressions.  |
| Number of customers affected | `cust_a.val` | integer | To access the `value` of `cust_a`, use the `cust_a.val` parameter. |
| Percentage of customers affected | `perc_cust_a.val` | integer | To access the `value` of `perc_cust_a`, use the `perc_cust_a.val` parameter. |
| Comments | `comments` | string | No special features. |
| Crew icon | `crew_icon` | boolean | To determine whether the crew icon is shown for the AML location on the Storm Center map. If **True**, the crew icon will be shown. If **False**, the crew icon will not be shown. However, you still need to click the **Enable Crew Indicator** checkbox to confirm the icon will be visible. |
| Crew status | `crew_status` | string, JSON object | Supports mapping tables; view warning below when using mapping tables for Range Expressions. |
| Metadata | `metadata` | JSON object, supports integer, string, boolean | Elements within the Metadata property support mapping tables depending on the configuration; view warning below when using mapping tables for Range Expressions. |
| Number of AML elements | `n_out` | integer | No special features. |

When using mapping tables for a range expression, you should reference mapping table languages with square brackets like `parameter['language']`. The languages available are EN-US, ES-ES, es-US, and fr-CA. For example, accessing the cause in French would be `cause['fr-CA']`. Ideally, we recommend using the default language used when creating the instance when you reference a language in the mapping table.

Ensure you have an additional condition defining the parameter as not equal to null (to avoid an error when parsing the expression).

For example, "cause != null". "cause != null && cause['EN-US'] == 'Planned maintenance'" is an example of a condition that supports mapping tables.

The table below indicates the operators allowed with data types used in Range Expressions.

| Data type | Operators allowed |
| ------- | ------- |
| boolean | OR, AND, ==, !=, unary operator (!a) |
| string | OR, AND, ===, ==, !==, !=, can use (<, >, <=, >=) operators when lexical and case dependent matching |
| integer | OR, AND, ===, ==, !==, !=, <, >, <=, >=, +, -, *, /, unary operators (+a, -a, !a) |

{{% notice note %}}
AML uses data fields specifically defined for it. Ensure you use those data fields while defining Range Expressions.
{{% /notice %}}

### KUBRA-recommended icons and color/shape combinations ###

{{% notice note %}}
KUBRA recommends using a combination of color and shape for AML icons to help users with color vision deficiency. In addition, the colors for the recommended icons are selected to provide adequate contrast with the white color used for the icon shapes and with the background map.
{{% /notice %}}

{{% notice tip %}}
KUBRA recommends using the following image sizes (in pixels):
24x24 up to 32x32 SVGs for individual elements and 40x40 SVGs for element clusters, similar to the recommended icon sizes for outages and outage clusters.
{{% /notice %}}

#### Icons for Additional Map Layers ####

These are the default KUBRA-recommended ADA-compliant icons for an Additional Map layer:

 + Water Outage
 + Water Cluster
 + Gas Outage
 + Gas Cluster
 + General Hazard
 + Hazard Cluster
 + Fire
 + Road Closure
 + General Water
 + Gas Leak

![WCAG-compliant AML icons](/images/default-aml-icons.png)

## Legend Labels ##

The map legend includes an introductory label to indicate what the numbers for each range refer to. For example, if you chose "Customers Affected" as the method for determining ranges, you could use "Customers Affected" as the Legend Label.

Enter labels to be used on the map legend for each language supported by the instance. KUBRA recommends a maximum of 25 characters for the map legend labels.

## Layer Field Labels ##

You can determine the order of the data fields shown in the information panel for the layer and provide labels for each field. Data fields are arranged vertically - the field with order 1 will be at the top of the information panel, followed by the field with order 2, and so on.

Choose an order for each data field and enter labels for each language supported by the instance. Labels for mobile browsers should be shorter than labels for desktop browsers so they can be read on a narrow screen.

{{% notice tip %}}
If you want to include punctuation after the field labels in the information panel, you **must** include the punctuation in the text fields here.
{{% /notice %}}

KUBRA recommends a maximum of 45 characters for information panel field labels. You may need to adjust the length or formatting of the labels after testing them on a map to ensure that they display and wrap well.

## Buttons for External Links ##

If you want to add one or more buttons to the bottom of the information panels for the layer, click the drop-down under **Custom Footer Buttons** and then select a button name from the list.

Before you can select a button here, you must [create buttons](/storm-center/configuration-guide/create-buttons).
