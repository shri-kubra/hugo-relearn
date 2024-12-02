---
title: "User Management - Storm Center"
weight: 37
---

KUBRA administrators must create accounts with User Administrator permissions for each tenant in Instance Manager as part of a Storm Center implementation project. After these accounts are created, admin users can sign in to Instance Manager and access tools for creating and managing additional Instance Manager user accounts.

{{% notice info %}}
If the organization is using single sign-on via an identity provider such as Active Directory, all user management will be done by the organization's identity provider administrators.
{{% /notice %}}

## Access User Management ##

To access the User Management Dashboard for Instance Manager:

1. Navigate to the Instance Manager website and sign in.
1. If you have access to more than one tenant account, select the name of the tenant for which you want to manage user information from the list and then click the **Submit** button.
1. On the app selection screen, click the gear icon in the upper right corner of the "Make a Selection" list or select the "User Management" app.

There are two tools on the User Management Dashboard. The **Create User Account** tool allows you to create new user accounts and assign access groups. The **Manage Users** tool allows you to manage information and access groups for user accounts and to delete user accounts.

## Create a User Account ##

To create a new user account for Instance Manager, access the User Management Dashboard and then click the **Create User Account** button. In the form that opens:

1. Enter the name of the user.
1. Enter the email address of the user.
1. Enter an initial password for the user. You must enter the password twice.
1. Select one or more permission groups for the user. The available options are listed in the tables below.

### Instance Manager User Permission Groups - Storm Center ###

| Group Name | Description |
| ---------- | ----------- |
| Data Feed Client Service Account | This group is intended for use by web services submitting data to KUBRA solutions, rather than by human users.  |
| Storm Center Control Center Admin | User has edit access to the Control Center apps for Storm Center, edit access to the Deploy Manager list of processed jobs, edit access to the Control Center Admin tools for Storm Center, and access to view and upload files for Storm Center data feeds. |
| Storm Center Control Center Edit | User has edit access to the Control Center apps for Storm Center, edit access to the Deploy Manager list of processed jobs, and access to view and upload files for Storm Center data feeds. |
| Storm Center Control Center Read-Only | User has read-only access to the Control Center apps for Storm Center and read-only access to the Deploy Manager list of processed jobs. |
| Storm Center Instance Admin | User has admin access to all Storm Center instances for the tenant. |
| Storm Center Instances Read-Only | User can view all Storm Center instances for the tenant, but cannot make changes to instances or configurations. |
| Storm Center Map History Admin | User can access the Map History app for Storm Center. |
| User Administrator | User can create and manage user accounts for the organization. |

### Instance Manager User Permission Groups - Other Applications ###

| Group Name | Description |
| ---------- | ----------- |
| EnergySuite Admin Administrator | User has admin access to the ESAdmin app, which provides administrative tools for Notifi and for previous versions of Storm Center. |
| Enterprise Blitz Client | This group is intended for use by web services connected to the Notifi Broadcast tool, rather than by human users. |
| Enterprise ESAdmin Client | This group is intended for use by web services submitting data to the ESAdmin app, rather than by human users. |
| Enterprise Notifi Client | This group is intended for use by web services submitting data to Notifi, rather than by human users. |
| IncidentWatch Admin | User has admin access to the Data Feeds module, including Asset Management data feeds, and can view job information for Asset Management data. |
| Message History Admin | User has permission to search and read history data and to resend messages from Notifi and KUBRA IQ. |
| Message Provider Admin | User has admin access to message provider configurations used for sending and receiving messages. |
| Message Provider Read-Only | User has read-only access to view the current message providers configured for sending and receiving messages.  |
| Modify Notifi Preferences | User has access to the Notifi Preferences tool with the option to update all customer accounts' communication preferences. |
| Notifi Broadcast Write | User has access to create and view Notifi Broadcast messages. |
| Notifi Enrollment Access | User has access to view the Notifi Enrollments tool with information about changes to customer enrollments for messages. |
| Notifi History Access | User has access to view the Notifi History tool with message history data and the option to re-send messages. |
| Notifi Messaging Administration | User has access to the Notifi Admin tool with the option to mute or un-mute outbound messages from the Notifi system. |
| Read Message History | User can search and read history data from Notifi and KUBRA IQ. |
| Template Manager Admin | User can create, update, and delete message templates and approve changes to non-development instances. |
| Template Manager Approver | User can view templates and approve changes to non-development instances. |
| Template Manager Editor | User can create, update, and delete message templates and globals, but not approve changes to other instances. |
| View Notifi Reports | User has access to the Notifi Reports tool. |

## Manage User Information ##

To manage Instance Manager user information, access the User Management Dashboard and then click the **Manage Users** button. This will open a list of user accounts by email address.

To edit information for a user account, click the **Edit** button to the right of the user's email address. In the form that opens, you can:

+ Change the user's password
+ Change the user's permission Groups

To save your changes to the user's account, click the **Save** button. To discard your changes, click the **Cancel** button.

To delete an Instance Manager user account, click the **Delete** button to the right of the user's email address in the "Manage Users" list.
