---
title: "Settings App"
weight: 34
---

To access the Settings app, click the **Settings** button on the Control Center Dashboard under "Apps."

You can use the Settings app to manage data feed processing, redirect map URLs, change the map view choice shown on map page load, and update the wording shown on the map to let users know how often data is updated.

![Settings App](/images/settings-app.png)

## Turn Data Feed Processing On or Off ##

By default, the delivery node, outage, and planned outage data feeds are active. To turn file processing off for a data feed, click the toggle next to the data feed name on the Settings app screen to change it from On to Off.

To resume processing for a data feed, click the toggle next to the data feed name on the Settings app screen to change it from Off to On.

Files sent to a data feed endpoint while processing is turned off will not be processed. When file processing is turned on, new files sent to the data feed endpoint will be processed, but files sent while data feed processing was off will not be processed. Files sent while data feed processing is off will be marked with the status **IGNORED** in the list of file processing jobs in [Deploy Manager](/storm-center/deploy-manager/#file-processing-jobs-list).

## Edit Map View Settings ##

To edit the settings for a specific map view, click the **Edit** button to the right of the map view name.

![Map view settings form](/images/settings-app-map-setting-form.png)

To redirect the map to a different URL, such as a maintenance message page when the OMS or the map is under maintenance, enter a URL in the **Redirect URL** field. You must enter a complete URL including the protocol. For example, `https://example.com`.

To change the map to Storm Mode, click the **Enable STORM Mode?** checkbox. This will change the map layer option shown on page load to the option selected in the [Edit Visibility Configuration form](/storm-center/configuration-guide/configure-layer-visibility/#select-default-options-per-map-mode) for storm mode.

{{% notice note %}}
If a map view includes more than one Visibility Configuration, the Storm Mode setting will only apply for the first visibility configuration in the list.
{{% /notice %}}

To change the wording displayed on the map to tell users how often data on the map is updated, edit the text in the Update Wording boxes for each language supported by the instance.

To save your changes, click the **Submit** button. To discard your changes, click the **Cancel** button.

{{% notice note %}}
You must click the **Submit** button to save any changes you make in this tool: redirect URL, storm mode vs. blue-sky mode, update wording, or any combination of these settings.
{{% /notice %}}

The current map settings are displayed in the "Deployed Settings" section of the **Edit Setting** form.

## Deploy Settings Changes to Storm Center Maps ##

Whenever you save a change to map view settings in the Settings app, a message will appear at the top of the app that says "Changes Not Yet Deployed." To deploy your changes to the Storm Center map or maps, click the **Deploy** button.

![Deploy button](/images/settings-app-deploy-button.png)

After you deploy changes, the message at the top of the Settings app will disappear.
