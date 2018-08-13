.. _devmethods:

Development Methods
*******************

.. contents:: Table of Contents

Philosophy
**********

Scientific analysis can be done in a wide variety of ways using many different tools. We expect that the analyses that we "adopt" or consider to be part of our Biogeographic Information System framework as :ref:`baps` will be developed in a variety of different tools, using a variety of methods and techniques, and resulting in many different ways of looking at problems of interest. However, we do see the need to develop, test, and refine a set of core principles, approaches, and overarching methods that we will adopt across the board. These should put some useful sideboards on our work, providing the basic mechanics for how certain things are done so that we can all concentrate on the more important substance of the scientific analytical work itself.

Shareable Code
--------------

We do feel strongly that all of our analyses need to be in the form of shareable code. Other people need to see exactly what we are doing and an instantiation of our scientific thought process both to provide transparency into our methods and sources and to help accelerate the pace of new analytical work by providing ready building blocks. The code can be in many different forms and languages, but it needs to be in some form that can be shared with others.

Buildable Code
--------------

Code can be shareable without being particularly buildable; we want our code to be buildable by others. What we mean by buildable is the ability to quickly pick up one set of code or a particular algorithm within code and use it to build something else. If there are dependencies within a Biogeographic Analysis Package that are out of reach for someone, then that package is not buildable. We will work on methods and practices across our various coding platforms and traditions to instantiate clear indications of requirements within our Analysis Packages, ensuring through testing that they can all be met by someone interested in building on what we've done.

"Contributability"
------------------

Analysis Packages are not just made up of core scientific code doing the actual analysis. They also have documentation, conversation, helper functions, and data management. Our intent is to operate a platform that accepts and celebrates all of these contributions. Below are a few thoughts on how we are working for these specific types of contributions to play out in practice.

Documentation
~~~~~~~~~~~~~

Documentation for an Analysis Package happens at a number of levels. There are core metadata that describe the purpose of an analysis and provide instructions for use. There may be additional documents that help to further understand the analysis, how it can be used, and perhaps how it should not be used. There are also inline comments within the code that help to understand how certain functions are meant to perform or what a workflow entails. Our intent is that documentation of our analyses is a team effort, with multiple people from across our group able to jump in and help work on the documentation for any analysis.

Conversation
~~~~~~~~~~~~

The very nature of science is that it is always in flux. Our understanding of anything at any given time is always incomplete, waiting for the next discovery or perspective to disrupt and further previous understanding. We expect our Analysis Packages to capture and foster ongoing conversation within and beyond our team, and with both other scientists and resource management stakeholders. We will work on ways to make these conversations as productive as possible by keeping them pointed toward specific aspects of our analyses. We will make best use of available technologies over time such as issue tracking in GitHub and GitLab to make the conversation a core part of the overall analytical record.

Helper Functions
~~~~~~~~~~~~~~~~

The nature of building scientific software or any type of code is one of putting building blocks together. These can be in the form of Python Packages or R Libraries or any number of other types of packaging. We use libraries from the larger community and from within our own group. We've already seen the need to start developing specific packages of functions in common across the Biogeographic Information System and have launched the pyBIS project to contain one form of these functions for common use. As we develop each of our Analysis Packages, we will look for opportunities to improve upon or build new tools into our overall toolbox in an appropriate language. We will strive for a healthy iterative approach where the lead author of a particular analysis may flag some part of their code for further examination by someone else on the team with the expertise to build out a particular function in the best way possible.

Data Management
~~~~~~~~~~~~~~~

One of the key aspects of making buildable code is to make the leap from offline to online data. If a set of analytical code has references to data sitting on the lead author's local machine, someone else can't meet that particular dependency without somehow getting those same data onto their own local machine and then changing the path. Each of the data input dependencies to our analyses needs some level of careful examination to determine the best pathway for the data to be made accessible and long-lived so that the analysis is buildable and sustainable. The lead author may not always know the best way of getting this done, but there's a good chance that someone else on our team will know how to take at least the first step.

Practical
*********

In the near term, there are a number of ways the philosophical development approach can be achieved in practical terms given the platforms we are choosing to operate on at the moment. The following are some practices we are working to develop and employ in the GitHub environment.

Personal --> BCB (lab) --> BIS
------------------------------

We are working under some longstanding permission from within our particular USGS Science Center to develop much of what we do that is not new science in GitHub in the open, potentially starting under a person account but moving into one of the two GitHub Orgs we set up. We will be working to formalize this a little bit, but the current accepted practice is to include the `USGS Provisional Software Disclaimer Statement <https://www2.usgs.gov/fsp/fsp_disclaimers.asp#11>`_ in the LICENSE and README of a repository unless and until the software goes through formal review and release.

Personal account repos may be the starting place for many analyses until we are ready to spin it up as part of our lab space (https://github.com/usgs-bcb). We may sometimes immediately start up a repo under our `Biogeographic Information System org <https://github.com/usgs-bis>`_ or we may move a repo to this location at some point in its lifecycle as we progress toward an official release and incorporation into the BIS.

README
------

At a minimum, the expectation is that every repository has at least a README containing core documentation for the Analysis Package or other component. We will keep working over time on methods for leveraging structured information in the README and linked documentation. READMEs and other docs should be written in reStructuredText (preferred) or Markdown. This is the first place people will look for information on what the package is and what it does, so write a good readme.

LICENSE
-------

Everything that our lab produces is done either by US Government Federal staff or by university cooperators who are generally working under the same guidelines where our work cannot be copyrighted and must be released into the public domain (inherently unlicensed). Projects in GitHub and elsewhere have established a convention for this kind of work using the `unlicense <http://unlicense.org>`_. We tweaked the standard unlicense text slightly to include the USGS provisional software disclaimer but may need to revisit as that changes the dynamic for how GitHub evaluates the standard license designation for a repository.

Branching and Pull Requests
---------------------------

We are using the git methods of branching and pull requests with the additional GitHub features of review and threaded discussion to good effect within https://github.com/usgs-bcb and https://github.com/usgs-bis. We ask that all contributors create a branch for a particular piece of work (preferably in small chunks), commit files in the branch, and issue a pull request. That sets up the contribution such that it can be reviewed, commented on, and either accepted or rejected into the particular project. If we know who else on the team would be good to review our contribution, we add them as a reviewer via GitHub. Reviewers comment on the approach or other substance of the contribution and either accept it or indicate that it should not be accepted. Right now, anyone with permissions in a given repo (generally our entire team) has the ability to merge a pull request or handle issues like collisions between branches. Some projects may eventually require a little more management rigor, and we'll be exploring continuous integration tools once we get some better testing rigor in place.

