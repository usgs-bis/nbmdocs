.. _maptool:

National Biogeographic Map - the map tool
*****************************************

.. contents:: Table of Contents

Map Tool Overview
=================

While the National Biogeographic Map is more than a web tool, the primary access point for many uses of the platform is the central online map tool at `https://maps.usgs.gov/biogeography`_. This page provides documentation on the major features of the tool.

Analysis Packages
=================

As of version 2.0, the major feature and purpose of the NBM interface is to access and work with Analysis Packages. The "flyout panels" of the previous version have been reduced to a single panel of available analyses that are controlled by interactions on the map and user selections. The available Analysis Packages are determined by a selected area of interest.

The list of Analysis Packages has a select button to the right of the title. This feature indicates that a particular package is primary or active in the interface, and a user can select a different analysis to be primary. Making an Analysis Package primary will trigger the following:

* Certain data may be added to the map based on the configuration of the Analysis Package and associated functionality will be turned on (legend and time series exploration tool if applicable)
* The time selection control at the bottom of the map may be enabled if the Analysis Package can accept a time period of interest

The core visualization for an Analysis Package can be "popped out" using the "Compare charts in a new window" button at the top of the particular package view. This enables users to compare different Analysis Packages about the same area of interest.

The raw input data for a given Analysis Package can be viewed using the "View the raw JSON used for analysis" button at the top of a particular package view. As of NBM 2.0, this feature is pretty raw in that the data view may not be particularly useful to anyone not intimately familiar with the data already. This will be replaced in subsequent versions with a more robust view of the underlying Application Programming Interface(s) behind each analysis.


Locations/Places
================

One of the primary modes of operating in the NBM interface is to select an area of interest through one of the following mechanisms:

* Search for a place of interest in the box in the upper left; uses a type ahead to provide a list of available places (:ref:`Spatial Feature Registry`)
* Click in the map somewhere, and then select a place from the list in the search box
* Draw a polygon using the draw tool in the upper right corner of the map

You might also trigger any one of these entry points from a link shared with you that contains instructions on what the map is supposed to do.

Not all of the Analysis Packages respond with information on all of the possible places of interest. The list of analyses will be responsive to user selection.

Time Period
===========

The time slider at the bottom of the map can be used in some circumstances to set a time period of interest for analysis. Analysis Packages that have a temporal component to the data and the analytical workflow. When activated, you will see a change in the time input parameter within the view of applicable Analysis Packages, and in some cases, a button to submit the time period and run the analysis.