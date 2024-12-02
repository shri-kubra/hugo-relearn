+++
title = 'IncidentWatch'
type = ''
weight = 1
+++

## What is IncidentWatch?

IncidentWatch is KUBRA's online, map-based incident reporting and management product. IncidentWatch uses asset data provided by an organization to show information about those assets on an interactive online map. End-users can then access the map from a link on the organization's website to report incidents related to assets or to see the status of an incident.

The IncidentWatch product is deployed on a multi-tenant architecture supported by Amazon Web Services. All clients or organizations who use IncidentWatch to create maps for their end-users use the same Production environment but have separate map instances with individual configuration settings.

## Benefits of IncidentWatch

| Benefits |  |
-----|-----
Highly configurable | Includes options for controlling report forms and views on the map
Durable and scalable infrastructure | Amazon Web Services resources adjust to support user traffic while taking advantage of economies of scale
Mobile-friendly design | Allows end-users to access maps from desktop or mobile web browsers
Ongoing updates | Multi-tenant architecture allows KUBRA to provide updates to all clients at the same time without altering production map configurations

### Interactive Map with Responsive Design

The Google Maps API provides the background map. The map interface allows users to search for an address, use location services to zoom to their current location, or pan and zoom manually. Responsive design supports both desktop and mobile web browsers, which is especially important for customers who may only think about reporting an incident when they are at the incident location.

You can choose which types of information to request in the incident report form based on the data you track in your Asset Management System or other incident data source.
