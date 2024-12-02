---
title: "Create Data Labels and Mapping"
weight: 18
---

## Estimated Restoration Time Labels ##

Storm Center outage maps can show standard text in place of estimated restoration time (ETR) values for null data and for expired values.

To configure the standard text to use on the Storm Center map, use the **Data Labels** sub-section of the **Shared Resources** section of the Instance Dashboard. You can use the same text for both null data and expired values, or different text for null data than for expired values.

1. Click the **Create Data Labels** button.
1. Enter a name for the ETR label configuration - this name is how you will identify the ETR label configuration in other areas of the Instance Manager; it will not show up on the map.
1. Enter a label to be used on the map in place of null ETR values for each language supported by the instance. If you do not provide a label, the ETR field will not appear in the information panel when an outage has a null ETR value.
1. Enter a label to be used on the map in place of expired ETR values for each language supported by the instance. If you do not provide a label, the ETR field will not appear in the information panel when an outage has an expired ETR value, unless you choose to [show expired ETR values](/storm-center/configuration-guide/create-outage-layers/#estimated-restoration-time-settings) when configuring the outage data layer.
1. Enter a label to be used on the map in place of null planned outage End Time values for each language supported by the instance. If you do not provide a label, the End Time field will not appear in the information panel when a planned outage has a null End Time value.
1. Enter a label to be used on the map in place of expired planned outage End Time values for each language supported by the instance. If you do not provide a label, the End Time field will not appear in the information panel when an outage has an expired End Time value, unless you choose to [show expired End Time values](/storm-center/configuration-guide/create-outage-layers/#estimated-restoration-time-settings) when configuring the planned outage data layer.
1. To save the new configuration, click the **Submit** button. To discard your changes, click the **Cancel** button.

{{% notice note %}}
Labels for Planned Outage End Time are only applicable if you are using the optional Planned Outages module.
{{% /notice %}}

To edit a configuration, click the **Edit** button next to the configuration name in the list under **Data Labels**.

To delete a configuration, click the **Delete** button next to the configuration name in the list under **Data Labels**.

## Outage/AML Data Mapping ##

Storm Center outage and AML maps can optionally use data mapping to provide customer-facing or masked values for data included in outage/AML files.

{{% notice note %}}
Data mapping or masking can only be provided for crew status, cause, and metadata fields and AML elements.
{{% /notice %}}

To configure data mapping, use the **Data Mapping** sub-section of the **Shared Resources** section of the Instance Dashboard.

1. Click the **Create a Data Mapping** button.
1. Enter a name for the data mapping - this name is how you will identify the data mapping in other areas of the Instance Manager; it will not show up on the map.
1. Click the **Add New Code** button.
1. Enter the name of the data element to be masked under "Code" and then provide a label to be used on the map in place of that data element for each language supported by the instance.
    + The value in the "Code" column must exactly match the name of the data element in the outage files.
1. Repeat steps 4 and 5 for each data element value to be mapped or masked.
1. Click the **Submit** button.

{{% notice note %}}
When styling mapped data fields, the original data has a `.orig` added to it. You can use `fieldName.orig` in your Range Expressions to avoid adding translations when performing data mapping.
{{% /notice %}}

You must create separate sets of data mapping for each field you want to map. After you create a data mapping, you can add it to an outage layer from the [Edit Data Layer form](/storm-center/configuration-guide/create-outage-layers/#data-mapping-for-outages-layers-and-planned-layers). The same rules will apply when creating data mapping for Additional Map Layers.

{{% notice note %}}
If a data field uses data mapping but does not include a default label, that field will not show up in the information panel when a value is not provided in an outage file for that field.
{{% /notice %}}
