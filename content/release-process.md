+++
title = "Release Process"
weight = 5
+++

## Types of Releases ##

KUBRA makes four types of releases for the multi-tenant products documented on this website.

1. Maintenance Releases
2. Maintenance Downtime Releases
3. Feature Releases
4. Preview Releases

**Maintenance Releases** do not include any changes to features or configuration items. They may include security updates, bug fixes, or internal product changes that are only visible to KUBRA.

**Maintenance Downtime Releases** are similar to Maintenance Releases, except that they may cause a period of downtime. KUBRA will provide email announcements before a Maintenance Downtime Release to organizations that may be affected by the downtime.

**Feature Releases** are used when a release includes new features or feature changes that are fully compatible with existing instances. Changes to administrative user interfaces are also considered Feature Releases. KUBRA will provide an email announcement about new features or feature changes included in a Feature Release when the feature is available to all production instances.

**Preview Releases** are used when a release includes new features or feature changes that impact the map layout or the customer experience. Preview Releases may also include new features or feature changes that require activation for an instance.

KUBRA will provide an email announcement two weeks before a Preview Release. Changes included in a Preview Release are released in a two-to-four-week preview period to non-critical instances before they are released to critical instances.

The preview period is intended to allow organizations to

+ preview any changes to the user interface
+ let the KUBRA team know about any observed bugs
+ plan for configuration updates as desired
+ update help documents, videos, images on the organization's website, etc.

## Pre-Release Testing ##

Before all releases, KUBRA completes automated and manual regression testing to confirm that updates included in the release will not have an unintended impact on user interfaces and instances in production.

For Feature Releases and Preview Releases, KUBRA also completes manual testing of new configuration options or features.

## Communication about Maintenance Downtime Releases ##

KUBRA will provide an email announcement one week before the Maintenance Downtime Release and a second email announcement 60 minutes before the Maintenance Downtime Release. These announcements will include a description of the maintenance, its impact, and the duration of the expected downtime. Organizations are not expected to take any action in response to these announcements.

## Communication about Feature Releases ##

KUBRA will provide an email announcement about new features or feature changes included in a Feature Release when the feature is available. Features and feature changes included in a Feature Release will not automatically change production instances. The new features or settings must be enabled or changed through configuration before they will be visible to users.

## Communication about Preview Releases ##

KUBRA will provide an email announcement about new features or feature changes to be included in a Preview Release two weeks before the Preview Release is made to non-critical instances. The preview will be available for two to four weeks, after which the feature changes in the Preview Release will be released to all instances, including critical instances.

When a preview is available, users with access to admin user interfaces will see a note on the instance dashboard for all non-critical instances. When a user accesses a user interface associated with a non-critical instance, a pop-up will indicate that a preview is available and allow the user to either view the user interface with the feature changes applied or view the user interface in its previous version, without feature changes.

## Critical Instances vs. Non-Critical Instances ##

Each tenant account can have multiple product instances, which behave similarly to environments in a single-tenant application. For example, a tenant can include a Development instance, a Test instance, and a Production instance. Each tenant account can have one "critical" instance, which is typically the instance used for production user interfaces.

New feature previews are not displayed on a critical instance. This allows each organization to view the new features on a non-critical instance (such as a Test environment), make any desired configuration adjustments, and provide feedback to KUBRA before the new features are released for critical instances as well.

KUBRA may delay the release of a preview to critical instances if bugs are reported that need to be fixed. Other comments users provide to KUBRA during the preview period will be considered for future releases.
