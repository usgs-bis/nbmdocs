.. _sfr:

Spatial Feature Registry
************************

.. contents:: Table of Contents

The Spatial Feature Registry is a core component of the Biogeographic Information System used to manage the process of bringing spatiotemporal features of interest into the system in various ways for analysis, reference, and reporting. This page lays out the overall approach we are taking to build this component.

SFR Registration
----------------

We are using ScienceBase as the point of registration for collections of features that we want to integrate for use. This gives us a flexible information model for capturing details about the source material, a repository to store file artifacts as necessary, and an API for building processing code against. What it doesn't yet do for us dynamically is provide a built in versioning system such that we have one logical item for a given source that represents and provides access to different versions of the source material over time. We still need to work out the best solution for this particular dynamic.

There are a number of core principles that we are continuing to develop for what the point of registration means:

* Characterize the origin - We need to record enough information about the origin that we can manage the source over time. This includes details on organization and person contacts, links to online sources and informational material, and important dates associated with the source (when it was considered current by the source, when we last obtained the source material, etc.).
* File cache - We try to look at every source with a critical eye as to its projected longevity and any problems we foresee in the source being maintained over time. We also look at the actual point of distribution to determine whether or not it will be performant enough for the type of processing we need to run. If there is an indication of brittleness or lack of performance, we will stash a file of some kind on the ScienceBase Item that is either exactly what the source provides or is run through a set of transparent processing logic to turn it into something we can use.

SFR Processing
--------------

Once we have a set of manageable registered sources, we can build processing code to work with the data in a variety of ways. We are currently building out logic that handles the following operations:

* Pre-processing - If we do anything to source data to set them up for our use before running them through a pipeline to bring them into our platform, we do that with code in source control that is linked to from the ScienceBase Item. We are working iteratively to improve this over time, moving from purpose-built individual scripts to overarching processing logic in our core "pybis" package. If there are particular configuration parameters or processing logs produced as part of a pre-processing step, these are either stored in source control and linked to the ScienceBase Item or stashed on the ScienceBase Item with the data.
* Data mobilization - In our current iteration of the SFR concept, we are finding that there is a certain amount of additional data processing and prep work needed that can take advantage of the data being loaded in pretty much their raw or minimally pre-processed form into PostGIS. This means that there is additional processing logic run against the data to tee them up for broader use in our systems. This can include transformations in the geometry, logical combinations of features, and other processes encoded in SQL. These codes also need to be made open and transparent somewhere that is linked to the original sources and to forms of the data put online for use in the BIS API.
* Purpose-built indexes - Once we have data mobilized and have a coherent set of basic usability processing steps in place, we can build out any number of indexes for broader use in the BIS. These indexes are also built with code so that we can show exactly how any given record came to be in our system, where it came from, and what happened to it along the way.

Example: Place Name Index
-------------------------

We anticipate building a number of specialized indexes over time to serve various purposes. For instance, we are planning a separate index of "removed dams" to serve as the backing for a new version of the Dam Removal Information Portal. Our seminal use case was a place name index built for use in the National Biogeographic Map. This tool is giving us the chance to work through what may be some commonly applied concepts across some or all of the indexes created from the SFR, manifesting as data properties in the index. We are also experimenting with the use of a JSON Schema as a way to document any given schema in the BIS (e.g., rough `schema <https://github.com/usgs-bis/schema-registry/blob/master/sfr-feature.json>`_ for the place name index features).

feature_id
~~~~~~~~~~

We need to be able to uniquely call up and refer to any given feature in an index. After some experimentation with various ways of doing this, we opted on a Uniform Resource Name (URN) type of construct where we adopt some meaningful identifier from the source that may be useful in linking to information already tied to that ID and then giving the identifier a classification that puts it in context. In the strictest sense, `RFC2141 <https://www.ietf.org/rfc/rfc2141.txt>`_ states that a URN is three parts:

.. code::

   All URNs have the following syntax (phrases enclosed in quotes are
   REQUIRED):

                     <URN> ::= "urn:" <NID> ":" <NSS>

   where <NID> is the Namespace Identifier, and <NSS> is the Namespace
   Specific String.  The leading "urn:" sequence is case-insensitive.
   The Namespace ID determines the _syntactic_ interpretation of the
   Namespace Specific String (as discussed in [1]).

::

In our initial foray, we kind of violated this syntax, adding in a logical fourth element to the identifier. As we go back in a future iteration, we'll correct this to come up with a compliant URN syntax, mostly because we need to start pointing the <NID> aspect of the name to a resolvable vocabulary resource that describes exactly what the context for the identifier signifies. With these two pieces of information, context and a meaningful identifier, we can generate explicit linkages between various pools of information already in existence or processed in some way that are identified by the original identifier. Good examples in our area include US State and County FIPS codes, Omernik Ecoregion Identifiers, and NHD Common Identifiers for watersheds.

In our next iteration, NID (namespace identifier) will be resolvable to a vocabulary source (expressed through the BIS API) that provides details about the namespace context, what it means, where it comes from, and what it can be used for.

feature_class
~~~~~~~~~~~~~

Within a given integrated index or even within a given feature source, we may have one or more classes or categories of features that form useful groupings or search facets for use. These values should be meaningful and useful as name strings but also need to be resolvable to a vocabulary source where further information can be obtained. A rule associated with feature_class is that all feature_name values need to be unique within a given feature_class.

feature_name
~~~~~~~~~~~~

Feature names are the commonly used identifiers for a given feature that are meaningful to users and use cases. They need to be unique within a given feature_class.

feature_description
~~~~~~~~~~~~~~~~~~~

In some cases, we have rich descriptive information for a given set of features that can serve for discovery, display, and understanding purposes. Feature descriptions can be any length text string.

source_data
~~~~~~~~~~~

In an information system of multiple disparate feature sources, we end up with widely varying schemas containing additional properties for features. Over time, we may incorporate more of these properties into some synthesized, higher level properties. In the near term, we have started simply dumping a data structure with source data into a separate property (object of key/value pairs in JSON) and adding this to the search index to facilitate additional discovery vectors.