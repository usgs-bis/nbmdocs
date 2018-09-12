.. _bis:

Biogeographic Information System
********************************

.. contents:: Table of Contents

The Biogeographic Information System (BIS) is the underlying cyberinfrastructure we are building behind the National Biogeographic Map. It is a set of software codes and information components being contributed to the broader Modular Science Framework vision of the USGS [CSSScienceStrategy]_. We are also borrowing heavily from ideas pioneered with the Global Change Information System (`GCIS <http://data.globalchange.gov>`_) in terms of a foundational information system that is semantically as well as syntactically intelligent and takes the idea of full traceability seriously.

A brief description of the components that we will reference throughout this documentation is provided below, and we'll be getting around to better documenting these subsystems in future.

Registries
----------

Much of the information we need to make sense of and work with in the BIS comes from other established sources that we reach out and assimilate in a way that makes sense for what we're trying to accomplish. We call these "registries" because they essentially start with a process of registering a set of source material in a way we can write code against to build out what we need. Registrants often start with a file or some pointer to an online data service. They are often heterogeneous and may not have very complete metadata directly on board. In all cases so far, we are using `ScienceBase <https://www.sciencebase.gov>`_ as our initial point of registration, taking advantage of a few key capabilities:

* Flexible information model that lets us define what we want to record about a registrant in a fairly simple way
* Ability to provide flexibly described links to online sources for a registrant's content
* Ability to store one or more files in an accessible repository as a cache of a registrant's content when we need to do so
* Reasonably robust API for us to write code against to process registrant content into what we need

Spatial Feature Registry
~~~~~~~~~~~~~~~~~~~~~~~~

Much of our work involves spatial analysis that runs analytics for a set of areas of interest, allowing us to report on the status of biodiversity and various stressors in a variety of ways. Some of the things we register and process are spatial frameworks based on hydrography or ecology and others are more human-centered like political boundaries of different types. While there are lots of reasonable sources for this kind of information, no one of them serves all our needs, and so we built a registry function to identify the best sources that make sense for our work and run code to pull them all together into something cohesive. Right now, our focus is on assembling certain areas of interest into a common index, complete with full geometry where we have it, that can serve as a place name lookup capability. This will then be used to either send geometry off to spatial processors for live analytics or send identifiers of one kind of another to other services to return pre-calculated metrics. These will drive BAPs in our next iteration of the National Biogeographic Map.

ScienceBase Collection: https://www.sciencebase.gov/catalog/item/55fafaf5e4b05d6c4e501b81

Note: The ScienceBase SFR collection currently has a bunch of cruft and experimental stuff in it, so bear with us while we do some housekeeping.

Taxa Information Registry
~~~~~~~~~~~~~~~~~~~~~~~~~

We also do a bunch of our work with information about species (and other levels of the taxonomic tree). We needed a place where we could assemble relevant information needed in our work that helps to make sense across a bunch of disparate sources. This information includes stuff from taxonomic authorities about taxonomy, but also includes species trait information, regulatory context, judgment calls from different groups about conservation status, and other details that are never all in one place. We also need a way to keep versions of information from these different sources over time as we build decision analysis capabilities so that stakeholders who use our information can count on us to get back to previous results we've presented.

As we've worked through this and other registry concepts, we've come to determine that the TIR is more about a process that produces purpose-built data for use (and keeps track of what it does over time) rather than a giant database. Each species list of interest comes from a particular context, and the rules in that context to things like what taxonomic authorities to consult or how to create meaningful linkages to potential connected information will vary from another context. The first real exposure of the resulting data in the TIR concept will be through our BIS API, though you can see one end result in the web app for the `State Species of Greatest Conservation Need <https://www1.usgs.gov/csas/swap/>`_.

Libraries
---------

Some of the resources we are building are more permanent data or information that need to be persisted over time. We are currently referring to these as "Libraries." This is somewhat a philosophical statement on how we would like to think about digital library resources and a partnership we are working to forge with our USGS Library organization. These digital asset pools we are creating have a few characteristics in common with many other libraries.

* Curation of the resources in the libraries is a key feature. Users can count on a certain level of rigor applied to the metadata and condition of the resources for use.
* The libraries contain a mix of original materials not found anywhere else and copies of materials borrowed from other places and assembled for ease of access.
* Cross referencing is a major part of the curatorial process to help add value to the materials in any given library.
* Openness, transparency, and traceability are core values that we ascribe to in order to make the resources found in our libraries more understandable and trustworthy

Data Reference Library
~~~~~~~~~~~~~~~~~~~~~~

Our analytical processes and products use a lot of data that are either originated by us, integrated and enhanced by us for particular uses, or are referenced from other sources. It is important that we keep track of all of this over time, apply data management best practices to our own works and the documentation of works from others, and clearly tie our analytical workflows to particular versions of data through time. We've started assembling our `Data Reference Library <https://www.sciencebase.gov/catalog/item/5644f3c1e4b0aafbcd0188f1>`_ as a collection in ScienceBase, but it is one of our early components that needs a fair bit of work in cleanup and practice development.

Research Reference Library
~~~~~~~~~~~~~~~~~~~~~~~~~~

We also base our work and pull specific information from many different reference materials that range from scientific journal articles to government reports and online materials. Similar to the Data Reference Library, it is important for us to have a curated source of research references that we can count on over time, especially with more transient materials that may not always be available from the location we found them. We are developing the idea for and an instantiation of a Research Reference Library in a new data model that will consist of a document store based on the schema.org/article specification and a cloud file store for materials we need to stash. To start with, we are building from several existing stores of this type of information that need to come together into something more cohesive.

* GAP species literature references
* US National Vegetation Classification literature references
* Dam Removal Science Database literature references

In addition to these, we are judiciously working with several partners who share an affinity with this idea on incorporating a few other sources.

Included in the Research Reference Library concept is the idea of a micro-citation or a smaller piece of a fundamental citable unit that is the subject of a particular reference. There is much research in the broader world of informatics and library science on this topic we are paying attention to, but we have an immediate practical need to record and reference micro-citations from which we are extracting data attributes across a number of our projects.

Software Reference Library
~~~~~~~~~~~~~~~~~~~~~~~~~~

Our analysis activities also result in the need for a Software Reference Library consisting of both our own original works and the various software dependencies that our work generates over time. We are still working out what all this practice will consist of and the rules for operating this component of the BIS, but we are working to identify and adopt best appropriate practices from software engineering in this work. This ranges from our own software development practices using git methods with both GitHub and GitLab (internally) to declaring and managing software requirements in our code and leveraging technologies like Docker to cache some of those dependencies within the Library.

We consider the following two GitHub organizations to be primary entry points to the Software Reference Library:

* https://github.com/usgs-bcb Lab space for experimental works
* https://github.com/usgs-bis More curated space for major software components of the BIS

In addition, we maintain a GitLab space within the secure part of code.usgs.gov and a group there for software projects that require temporary or permanent security controls.