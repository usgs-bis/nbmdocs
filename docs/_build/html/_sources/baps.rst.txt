.. _baps:

Biogeographic Analysis Packages
*******************************

Overview
========

Biogeographic Analysis Packages are the heart and soul of the National Biogeographic Map. Fundamentally, we are building a scientifically robust decision analysis platform focused through the lens of a national map. At the root of this are discrete analytical workflows that leverage a variety of data sources to examine particular issues of importance to resource management and policy making challenges.  We call these foundational units "packages" to denote a method for putting the process and results of our analyses into a cohesive construct that can be explained, reviewed, deployed into a variety of venues (including but not limited to the National Biogeographic Map), and built upon by us and others. We will continue to evolve the BAP concept and will keep this documentation up to date with the latest developments and method descriptions.

Version Control
===============

Using the Git platform affords the ability to develop Analysis Packages iteratively and openly with our colleagues internal and external. It helps us keep track of the entire analytical workflow, including various dead ends and failed experiments that we conduct in the process such that we and others can learn over time. Using platforms like GitHub and GitLab gives us other capabilities as part of the packages such as issue tracking and associated threaded conversations about the analysis. This allows for a heterogenous mix of scientific programming tools and methods while giving a platform for everyone to contribute in some way to the process.

Open vs. Closed Source
======================

In general, we default to completely open development of our analyses. The one exception to completely open development (until a publication milestone) is when we are building something with pre-publication sensitivity, meaning that the substance of the analysis is new, publishable scientific information that we will be submitting through internal USGS review controls and often to a particular journal. We do things in the open wherever possible, because we desire and solicit outside feedback, input, and contributions. We want people to poke into what we are doing and how we are analyzing data to help us make better products. By design, we are also always targeting an application to resource management, conservation planning, policy making, and other direct partner uses of our analyses. Conducting our analyses iteratively in the open reduces the barriers for our management partners to co-develop the science with us.

When we can develop in the open, we build our analyses as discrete repositories a particular Organization in GitHub (<https://github.com/usgs-bis>) to organize things into one logical space and give team members access. When we have to conduct our analyses internally until initial release, we use either private repos in GitHub or one of our internal GitLab instances. Once we are able to release in the open, we move the internal repos to the usgs-bis org.

Iterative Development and Milestones
====================================

We are still working out our process for how we conduct the analytical process. We are borrowing some concepts from software engineering and other disciplines and figuring out the best way to apply them to the scientific process within the particular cultural context of our mix of government and university labs. We are working to leverage the capabilities of our chosen platforms where an Analysis Package is made up of the following basic components:

* Collection of files
* Software code in a variety of languages (mostly Python and R at the moment)
* Issues with labels (more on this below)
* Repository metadata that dynamically drives much of how BAPs function

Organization and Navigation
---------------------------

For now, we are usgs-bis GitHub organization with repos flagged to the topic, "`analysis-package <https://github.com/search?q=topic%3Aanalysis-package+org%3Ausgs-bis&type=Repositories>`_", as the way in which Analysis Packages make their official online debut. We are using the GitHub API to pull information on the repos in this category to evaluate capability maturity of the packages and drive different types of representations (e.g., through the National Biogeographic Map).

Issues and Labels
-----------------

Within the GitHub context, we are experimenting with use of issues labeled a particular way to describe milestones and directions of our analyses. While most of the work in an analyses is going to be evidenced through some type of code and associated "formal" documentation, we are also working to foster a form of capturing the broader conversation about an analysis as part of the package. Labels on these conversations will help us to examine where an analysis is in its lifecycle based on our evolving thinking about the process. This will likely be adjusted significantly over time as we continue to work through specific cases.

The purpose of the labels is to flag issues about a particular aspect of the analysis. Issues may come about through one of the following "events":

* The author(s) of the analysis package raise the issues themselves as a reference point for discussion
* Someone else from the team may raise an issue during a solicited or extemporaneous review
* As we get more sophisticated, we may write algorithms that are able to introspect an analysis package, look for particular characteristics, and then raise issues for discussion and resolution.

Eventually, we hope to get more sophisticated in how we use this process and iteratively develop our analyses. In the near term we will be looking for a couple of things (either as team members or in our softward codes) with regard to issues and labels.

* The complete lack of any issues with the labels in our list means that the topic has not even been raised, indicating a lower level of capability maturity.
* Issues raised with the labels but unresolved mean that the issue has at least come up but not yet been brought to a satisfactory conclusion.
* Issues with no discussion or involvement (comment postings) from other team members or collaborators means that the particular aspect of the analysis has not yet been through some level of review and discussion.
* Issues with the labels that are closed after including some external discussion indicate a more mature concept is likely developing.

Purpose
~~~~~~~

The most basic element of an analysis is an ability to clearly state a purpose. This could be phrased as a scientific hypothesis being pursued or could focus more on an application of the particular type of analysis.

Abstract Stakeholder
~~~~~~~~~~~~~~~~~~~~

This this stage in the development of our practices, most if not all the analyses we are conducting have a direct application to a stakeholder of some kind in terms of decisionmaking processes. Some of our efforts will stop at the level of an abstract stakeholder or persona that we think the work is targeted toward, while other efforts will get all the way to tests with actual representatives of a stakeholder group Actual Stakeholder.

Actual Stakeholder
~~~~~~~~~~~~~~~~~~

When possible, we are trying to take many of our efforts all the way to sitting down with real people representing a stakeholder community and testing the efficacy of our ideas and presentation with them, soliciting critical feedback, and incorporating that into future iterations. Whenever we can and it makes sense, this involves some level of science co-development where we work together with a partner on all aspects of the analytical workflow. It's not always possible or necessary to explicitly identify actual stakeholders and may not be appropriate, but when it can be done and makes sense, it would be good to see those folks online with us contributing tangibly to the work.

Test
~~~~

We are working to combine the foundational scientific method with Test Driven Development from agile software engineering where early in our analytical workflow, we design a logical test that will pass if an analysis proves out. The logical test is designed to prove the purpose and deliver capability to the stakeholder. Eventually, we should get sophisticated enough in our thinking that we can conduct at least a portion of the testing process through software code and collect evidence over time through reported metrics on usage of the analysis in decisionmaking pathways. For now, we will look to issues with this label evidencing discussion on the tests being planned and conducted.

Inputs
~~~~~~

While there are a number of additional labels (elements of Analysis Packages) that we will likely get into over time, we are starting with the inputs to the analysis as one key aspect that needs immediate attention. Inputs in this sense come down to the data sources, algorithms, theories, article citations, and other necessary ingredients for an analysis to be conducted. We focus on these at this stage in our development, because the inputs will be a major source of scrutiny in identifying new elements that need to be incorporated into the :ref:`bis`. Eventually, we will provide a small range of options for how a package identifies its inputs in a way that can be clearly examined by humans and algorithms, but in the near term we will allow for lots of heterogeneity and will use the "Inputs" issue label as a way to identify discussion.