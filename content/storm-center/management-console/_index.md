---
title: "Management Console for Storm Center (Control Center)"
type: index
weight: 30
---

## Control Center Dashboard ##

The Control Center Dashboard acts as the management console for Storm Center. It allows admin users at an organization to manage some configurable features of their deployed Storm Center outage maps. The dashboard includes three sections: Apps, Deployments, and App Administration.

For users in a Control Center access group, the app and tool names appear in a navigation panel on the left side of the screen. Users who have access to more than one instance can see the name of the selected instance in the navigation panel, under the Control Center title. The image below shows an example Control Center dashboard with the instance name highlighted in red.

![Control Center Dashboard](/images/storm-center-control-center-dashboard.png)

### Apps ###

The **Apps** section of the dashboard includes up to four apps:

+ [Alert Banner](/storm-center/management-console/alert-banner) - allows you to create and deploy an alert banner to one or more maps
+ [Area Manager](/storm-center/management-console/area-manager) - allows you to enter and manage overwritten values for Estimated Restoration Time, Customers Affected, or both to be displayed on maps in place of the data from the outage feed
+ [Custom Layers](/storm-center/management-console/custom-layers) - allows you to add ad hoc information areas and icons to the maps
+ [Settings](/storm-center/management-console/settings) - allows you to redirect a map to a different URL, change from blue-sky mode to storm mode, and edit the update wording

### Deployments ###

The **Deployments** section of the dashboard includes a link to the deployment history for the instance with details about jobs to process delivery node and outage files. The Deploy Manager also allows you to download a configuration file for a specific deployment of the instance. Depending on your user permissions, the Deploy Manager may allow you to reprocess a specific outage file or delivery node file. For more information, see the [Deployment History section of the Deploy Manager page](/storm-center/deploy-manager/#deployment-history-tool).

![Deploy Manager - History list](/images/deploy-manager-history-list.png)

### App Administration ###

The **App Administration** section of the dashboard includes up to two tools:

+ [Area Manager Admin](/storm-center/management-console/area-manager-admin) - allows you to configure whether the Area Manager app includes options for overwriting ETR information, Customers Affected information or both, and to configure the hierarchy for thematics included in the Area Manager app
+ [Custom Layers Admin](/storm-center/management-console/custom-layers-admin) - allows you to configure the information areas and information points available in the Custom Layers app to be placed on map views

## Access ##

Users who are part of the Storm Center Control Center Read-Only group can view the Apps section and the Deployments section of the Control Center, but they cannot make changes to the features in the Control Center apps or reprocess data processing jobs.

Users who are part of the Storm Center Control Center Edit group can view the Apps section and the Deployments section of the Control Center, and they can make changes to the features in the Control Center apps and reprocess data processing jobs.

Users who are part of the Storm Center Control Center Admin group can view the Apps section, the Deployments section, and the App Administration section and they can make changes in all of the Control Center apps and tools.

For more information about user management and user groups, see the [User Management page](/storm-center/management-console/user-management).
