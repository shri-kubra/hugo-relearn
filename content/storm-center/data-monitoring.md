---
title: "Storm Center Data Monitoring"
weight: 36
---

KUBRA has set up multiple monitors for receipt and processing of data files related to Storm Center. The following list describes these monitors.

## Outage File Processing Queue Monitor ##

This monitor triggers an alarm if there are more than 20 messages indicating an outage file was successfully uploaded in the data feeds queue. Messages are removed from the queue when the file is pulled for processing, so a backlog of messages indicates an issue with file processing. KUBRA support receives the alarm message.

## Delivery Node File Processing Queue Monitor ##

This monitor triggers an alarm if there are more than 5 messages indicating a delivery node file was successfully uploaded in the data feeds queue. Messages are removed from the queue when the file is pulled for processing, so a backlog of messages indicates an issue with file processing. KUBRA support receives the alarm message.

## Planned Outage File Processing Queue Monitor ##

This monitor triggers an alarm if there are more than 20 messages indicating a planned outage file was successfully uploaded in the data feeds queue. Messages are removed from the queue when the file is pulled for processing, so a backlog of messages indicates an issue with file processing. KUBRA support receives the alarm message.

## Batch Jobs Monitor and Terminator ##

One function of this monitor looks for batch jobs running for more than 90 minutes and sends a warning message to KUBRA support. The other function of this monitor looks for batch jobs running for more than 120 minutes and terminates the job. The second function also sends an alert message to KUBRA support.

## Recent Outage Jobs Monitor ##

This end-to-end monitor checks if the tenant has recent successful outage jobs. By default, if no jobs have completed successfully in the last 20 minutes, the monitor sends a warning message to KUBRA support. If no jobs have completed successfully after 30 minutes, the monitor sends an alert message to KUBRA support. KUBRA support sets thresholds for warning and alert messages for each tenant (utility).

The monitor also returns an error if the API is down and creates an alert for KUBRA support.
