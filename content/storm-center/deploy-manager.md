---
title: "Deploy Manager"
weight: 32
---

## Introduction ##

The Deploy Manager dashboard allows you to verify configuration changes made to an instance, deploy configuration changes for an instance, check the current deployment status for an instance, and view the history of previous deployments and file processing jobs for an instance.

The available tools on the Deploy Manager dashboard are

+ [Deploy](#deploy-tool)
+ [Verify Instance](#verify-instance-tool)
+ [Current Status](#current-status-tool)
+ [Deployment History](#deployment-history-tool)

Users with access restricted to the Storm Center Control Center only have access to the Deployment History tool.

## Deploy Tool ##

To access the deploy tool and deploy an instance, click the **Deploy** button on the Deploy Manager dashboard.

{{% notice tip %}}
Before you deploy an instance, use the Verify Instance tool to check that the configurations are valid and can be deployed correctly.
{{% /notice %}}

The deploy tool shows the instance name and status. If there is not a deployment in process, the status will be blank. To deploy the instance, click the **Deploy!** button.

The status will change to "Deploying..." and then to "Successfully Deployed" if the deployment is started successfully.

After the deployment starts, a delivery node file and an outage file must be successfully processed before the maps connected to the instance will show the configuration updates included in the deployment.

## Verify Instance Tool ##

To access the verify instance tool and verify the status of the currently saved configurations for an instance, including any changes made since the last successful deployment, click the **Verify Instance** button on the Deploy Manager dashboard.

The verify instance tool shows the instance name, the request status for the verification, and the status of the verification. If there is not a verification request in process, the request status will either show the status of the previous request or it will be blank. To request a new verification, click the **Verify!** button.

The request status will change to "In Progress" and then to "Done." When the request status is "Done," the "Verified" status message shows the state of the verification, such as "Passed."

## Current Status Tool ##

To access the current status tool and view the current deployment status of an instance, click the **Current Status** button on the Deploy Manager dashboard.

The current status tool shows the instance name, the current deployment status of the instance, the last successful delivery node file processing date/time, and the last successful outage file processing date/time.

If the instance is currently deployed, the status will be "Active."

If the instance is being deployed, the status will indicate which step of the process the instance is on: "Deployment in Pending State," "Pending Delivery Node," or "Pending Outage."

### Deployment Process ###

The deployment process is

1. User requests deployment.
2. Configuration changes are applied from Instance Manager to the instance.
3. The most recently submitted delivery node file is processed.
4. The most recently submitted outage file is processed.
5. The most recently submitted planned outage file (if any) is processed.
6. The results of the delivery node, outage, and planned outage file processing are used to update the data on the map.
7. The currently deployed map views (if any) are replaced with the results of the updated configuration and data file processing.

The current status information does not update automatically while you are viewing the current status tool. To update the status information, click the **Refresh** button.

## Deployment History Tool ##

To access the deployment history tool and view the list of deployments and file processing jobs for an instance, click the **Deployment History** button on the Deploy Manager dashboard.

The deployment history tool shows a list of deployments for an instance in reverse chronological order (from most recent to oldest). This list includes

+ Deploy Date - the date and time of the deployment
+ Status - the current status of the deployment (the current deployment has the status "Active," in progress deployments have the status "Pending Delivery Node" or "Pending Outage," and previous deployments have the status "Archived")
+ Configuration - a button to download the configuration data for the deployment in JSON format
+ Jobs - an option to view the list of delivery node and outage file processing jobs associated with the deployment
+ Last Status Changed At - the date and time at which the deployment status was last changed

To download a JSON file with the configuration used for a specific deployment of an instance, click the **Download** button in the Configuration column for the deployment. You can use the configuration file to assist with troubleshooting configuration issues or to set up a new instance that uses the same configuration options as an existing instance.

### File Processing Jobs List ###

To view the list of file processing jobs for a specific deployment, click the **View Jobs** link in the Jobs column for the deployment. A new screen will open that includes sections for Selected Deployment and Jobs.

The Selected Deployment section of the jobs list screen includes the date and time of the deployment, the status, a link to download the configuration data for the deployment, and the date and time at which the deployment status last changed.

The Jobs section of the job list screen includes a filter drop-down that allows you to filter the jobs listed in the table by job type or job status. The Jobs section also includes a table of information for individual file processing jobs. By default, the table shows information for all job types and all job statuses.

+ ID - an ID number for the file processing job
+ Type - the type of file being processed: "Delivery Node," "Outage," or "Planned Outage"
+ Status - the current status of the file processing job:
    - Received - The job has been received by the system.
    - Submitted - The job has been submitted and is waiting to run.
    - Running - The job is running.
    - Failed - The job has failed.
    - Succeeded - The job has successfully completed processing and all steps were successful.
    - Succeeded with Errors - The job has successfully completed processing, but some steps were not successful. See metadata for additional information.
    - Ignored - The job was not processed because file processing was turned off in the [Settings app](/storm-center/management-console/settings).
+ Triggered By - describes the source of the request for the file processing job; for deployments started from the Deploy Manager or a file uploaded in the Data Feeds application, this is "Auto-Submit"
+ File Location - shows the location of the file in Amazon S3
+ File Download - a button to download a copy of the file
+ Last Status Changed - the date and time at which the file processing job last changed status
+ View Additional Details - an option to open a pop-up window with the Batch ID, ECS IDs, Created date/time, and Updated date/time for the file processing job
+ Reprocess Job - a button to request that the selected file be re-processed
+ Metadata - an option to open a pop-up window with messages and JSON or JSONL log files related to the file processing job

{{% notice note %}}
Users with read-only access to the Deployment History tool cannot reprocess job files. You cannot reprocess job files for any archived deployments. You cannot reprocess a job file if it was submitted more than 90 days ago. If you attempt to reprocess a job file that has been archived, you may see an error message in the job metadata that includes "Path does not exist."
{{% /notice %}}

#### Additional Details ####

The Additional Details pop-up for a specific file processing job includes

+ Batch ID - the AWS Batch service ID number for the job
+ ECS IDs - the ID numbers for the Elastic Container Service (ECS) containers used by AWS to fulfill the job
+ Created - the date and time at which the file processing job was created or started
+ Updated - the date and time at which the file processing job was last updated or completed

#### Metadata ####

The Job Metadata pop-up for a specific file processing job includes messages and files related to the job.

For delivery node files, the related files include

+ Error Nodes - error_nodes.jsonl - a JSON Lines file that lists thematics with one or more [critical errors](/shared-file-specifications/failure-types/#delivery-node-files)
+ Unresolved Thematics - unresolved_thematics.json - a JSON file that lists thematics with no customers served
+ Resolved Thematics - resolved_thematics.json - a JSON file that lists thematics with one or more customers served
+ Filtered Nodes - filtered_nodes.jsonl - a JSON Lines file that lists delivery nodes that were filtered out of the delivery node file due to one or more file processing failures such as coordinates outside of the specified region and/or thematic areas
+ Unfiltered Nodes - unfiltered_nodes.jsonl - a JSON Lines file that lists the delivery nodes that were not filtered and therefore will be available to be shown on the map when there are outages that reference them

If the delivery node job encounters errors, additional files such as a Duplicate Nodes file may be included in the job metadata.

For outage files, the related files include

+ Error Outages - error_outages.jsonl - a JSON Lines file that lists outages with one or more [critical errors](/shared-file-specifications/failure-types/#outage-files)
+ Non-Matching Delivery Nodes - non-matching_delivery_nodes.jsonl - a JSON Lines file that lists any affected delivery node IDs that do not match any of the IDs in the delivery node file
+ Resolved Outage Thematics - resolved_outage_thematics.json - a JSON file that lists all thematics with one or more customers served
+ Resolved Outages - resolved_outages.jsonl - a JSON Lines file that lists all outages with one or more customers affected

For planned outage files, the related files include

+ Error Outages - error_outages.jsonl - a JSON Lines file that lists outages with one or more [critical errors](/shared-file-specifications/failure-types/#planned-outage-files)
+ Non-Matching Delivery Nodes - non-matching_delivery_nodes.jsonl - a JSON Lines file that lists any affected delivery node IDs that do not match any of the IDs in the delivery node file
+ Referencing Invalid Delivery Nodes - referencing_invalid_dn_outages.jsonl - a JSON Lines file that lists any outages in the file that are referencing invalid delivery nodes or that are missing affected delivery node IDs
+ Resolved Outages - resolved_outages.jsonl - a JSON Lines file that lists all planned outages with one or more customers affected
