---
title: "Troubleshooting"
weight: 37
---

## Deploying Configuration Updates ##

Each time you change the configuration for an instance - any changes made in the Instance Manager outside of the Control Center tools - you must re-deploy the instance to see those changes reflected on the map views associated with the instance. Check the Status section of the instance dashboard to see if there are changes to the instance configuration that have not been deployed. If the deployed instance is up to date with the current configurations in the Instance Manager, you will see a green check mark icon next to **Deployment Up-to-Date** under the instance status.

If there are undeployed changes to the instance configuration, you can deploy them using the [Deploy Manager page](/storm-center/deploy-manager/) tools.

## Embedding Outage Map Pages ##

When an organization uses an iframe to embed a Storm Center outage map in an organization-controlled website, the organization should not use a meta tag such as `<meta http-equiv="X-UA-Compatible" content="IE=10">`. Attempting to use `content="IE=10"` will cause the outage map page to return an error message. MS Edge will automatically use the latest browser version to render content without a compatibility meta tag.

If an organization sets up a CNAME for a Storm Center map and also wants to embed the map in a different web page or other application, the full-screen map web page and the iframe or div element for the embedded map must use the same URL. KUBRA recommends that users only access the outage map page from the CNAME URL after the CNAME is set up.

## Inactivity Timeout ##

By default, users of Instance Manager and Control Center will be logged out after 15 minutes of inactivity. By default, users of any map views with access restrictions will be logged out after 2 hours of inactivity.

## Inconsistent Customers Affected Count ##

There are three possible reasons why the number of customers affected in a summary report and the number of customers affected in the overview panel may not match.

1. If the thematic file used for a report is not used to filter delivery nodes and the thematic areas do not cover the entire region or service territory.
  + This means there may be some delivery nodes that are included in the areas for the thematic file used to filter delivery nodes but are outside the areas in the thematic file for the report.
2. If one or more of the delivery nodes is filtered due to spatial scanning or because the area name does not match any of the provided area names in the thematic file used to filter delivery nodes.
3. If a user has entered an overwritten value for customers affected in the Area Manager app. Overwritten values are used for summary reports and information panels, but not for the summary in the overview panel.

## Known Issues ##

When a user first accesses the map or changes the language on the map in the Microsoft Edge browser with the LastPass browser extension installed, the map breaks until the user reloads the web page. This issue also affects the Custom Layers tool. Possible solutions include uninstalling the LastPass extension or using a different browser. Google Chrome and Mozilla Firefox browsers are unaffected, even with the LastPass extension. - Reported February 1, 2018
