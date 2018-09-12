.. _releasenotes:

Release Notes
*************

This page provides overview documentation of releases of the National Biogeographic Map. Detailed tallying of issues dealt with and features is evolving, and we'll reference that from here as soon as we are able.

Version 2.0
-----------

Version 2.0 is an almost complete redesign of the National Biogeographic Map concept. It removed a number of the features that were problematic in the Version 1.0 design such as the whole bioscape idea, focusing instead on a more sophisticated architecture for determining what BAPs are available at any given place and time. It introduced a place name lookup capability driven by an API based on the Spatial Feature Registry work. It also introduced a time period selection capability triggered by the availability of BAPs that take a time input control, giving us the ability to begin introducing BAPs that explore temporal as well as spatial data.

Version 1.0
-----------

This was the initial release of the National Biogeographic Map in July 2017. The interface for Version 1.0 was based heavily on the `Burwell <https://macrostrat.org/map/>`_ app from the Macrostrat project at University of Wisconsin. While not a direct fork of that app, it was heavily inspired by Burwell in overall layout and design. It featured the concept of a menu of data to put on the map, much like traditional web mappers, and a flyout panel on the right that we called a "Bioscape" (a composition of Biogeographic Analysis Packages for a given context like a spatial area of interest).

Version 1.0 proved to help sell the overall idea of the National Biogeographic Map, but it had a number of limitations in terms of underlying architecture that made it difficult to scale up quickly to many more analysis packages. We also ran into the issue of users expecting it to behave like a traditional online mapper instead of centering focus on the analysis packages, which are the heart of the overall concept we are pursuing.

One concept that we borrowed from Macrostrat's Burwell was the "find-by-click" interface idea where the user clicks some area of interest on the map and a panel unfolds with all the information on that area. This is what launched our Bioscape construct of analysis packages. We introduced this initially with only Omernik Level III Ecoregions and Large Marine Ecosystems as available areas to examine. It was a nice device, but we suffered from needing something more sophisticated to let users choose from any number of areas to examine under their one mouse click and the need for some type of place name lookup functionality.