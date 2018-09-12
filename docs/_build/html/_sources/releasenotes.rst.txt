.. _releasenotes:

Release Notes
*************

This page provides overview documentation of releases of the National Biogeographic Map. Detailed tallying of issues dealt with and features introduced is evolving, and we'll reference that from here as soon as we are able. For Version 2.0, most of that is still done on an internal ticketing system that we can't share directly.

Version 2.0
-----------

Version 2.0 is an almost complete redesign of the National Biogeographic Map concept. It removed a number of the features that were problematic in the Version 1.0 design such as the whole bioscape idea, focusing instead on a more sophisticated architecture for determining what BAPs are available at any given place and time. It introduced a place name lookup capability driven by an API based on the :ref:`Spatial Feature Registry` work. It also introduced a time period selection capability triggered by the availability of BAPs that take a time input control, giving us the ability to begin introducing BAPs that explore temporal as well as spatial data.

One feature we had do deprecate temporarily in version 2.0 is related to a transition we are making in the :ref:`Taxa Information Registry`. We had a feature within one of the Biogeographic Analysis Packages on species protection status that brought up information about that species pulled from a couple of different sources. We did not finish work in time on the new API behind that capability and decided to remove the feature entirely for now.

Biogeographic Analysis Packages expressed in NBM 2.0 are still partially driven by metadata in ScienceBase Items, but we're moving to an architecture that is driven from base documentation in Git code repositories. We have an API end point planned for this, but in the near term you can browse those Analysis Packages included in the NBM with a couple of topic references under our primary GitHub Org via `this link <https://github.com/search?utf8=%E2%9C%93&q=topic%3Aanalysis-package+topic%3Anbm+org%3Ausgs-bis+fork%3Atrue&type=Repositories>`_.

Version 1.0
-----------

This was the initial release of the National Biogeographic Map in July 2017. The interface for Version 1.0 was based heavily on the `Burwell <https://macrostrat.org/map/>`_ app from the Macrostrat project at University of Wisconsin. While not a direct fork of that app, it was heavily inspired by Burwell in overall layout and design. It featured the concept of a menu of data to put on the map, much like traditional web mappers, and a flyout panel on the right that we called a "Bioscape" (a composition of Biogeographic Analysis Packages for a given context like a spatial area of interest).

Version 1.0 proved to help sell the overall idea of the National Biogeographic Map, but it had a number of limitations in terms of underlying architecture that made it difficult to scale up quickly to many more analysis packages. We also ran into the issue of users expecting it to behave like a traditional online mapper instead of centering focus on the analysis packages, which are the heart of the overall concept we are pursuing.

One concept that we borrowed from Macrostrat's Burwell was the "find-by-click" interface idea where the user clicks some area of interest on the map and a panel unfolds with all the information on that area. This is what launched our Bioscape construct of analysis packages. We introduced this initially with only Omernik Level III Ecoregions and Large Marine Ecosystems as available areas to examine. It was a nice device, but we suffered from needing something more sophisticated to let users choose from any number of areas to examine under their one mouse click and the need for some type of place name lookup functionality.