=================
 The SFM Project
=================

------------
 Objectives
------------

Social Feed Manager (SFM) empowers social media researchers, students, archivists, librarians,
and others to define and collect datasets from social media services. To support this work,
SFM presents an easy-to-use web-based user interface that lets users define collections
comprising sets of targeted accounts, keywords, and other search strategies appropriate to
different platforms, and lets users authorize SFM to collect data from those accounts, keywords,
searches, and related web resources on those users' behalf. Behind the scenes, SFM uses
a set of carefully managed processes to crawl, collect, and store this data, recording its
actions in detail. Collected information and metadata about crawls are then available to users,
who may extract, filter, and export these to formats appropriate to their work.

--------------
 Requirements
--------------

SFM is designed around these key requirements:

* Individual users must be able to create and export collections with a minimum of training and
  staff intervention.
* Staff must be able to install, maintain, and support SFM based on a concise, clear set of
  documentation and automated management tools.
* Developers must be able to add support for additional social media platforms by implementing
  code that follows a concise, clear set of documented design conventions.
* Access to and use of social media data is subject to distinct terms of service offered by each
  platform; SFM will only support methods that fall clearly within these terms of service, such
  as using only supported API methods and respecting API rate limits.

--------------
 Out of scope
--------------

These objectives are not directly supported by SFM:

* SFM is not a primary access, discovery, publishing, dataset hosting/sharing, analysis, or
  archival platform for collected data. It may provide some baseline statistics, summarization,
  and browsing of collections in support of users and staff in defining, assessing, and exporting
  collections, but access, analysis, and long-term storage are complementary to sfm, rather than
  core functions.
* SFM is not a general-purpose web crawling and archiving application; although it may support
  direct capture of web pages and sites, it is complementary to, rather than a substitute for,
  more established, robust tools like Heritrix.
* SFM is not a "one-click install" application; although its installation is supported through
  automation tools, we assume most who deploy SFM will have some unix system administration
  skills on their team.

-----------------
 Funding history
-----------------

* Development of this project has been supported by a grant (#NARDI-14-50017-14) from
  the `National Historical Publications & Records Commission <http://www.archives.gov/nhprc/>`_
  to George Washington University Libraries from 2014-2017.
* Development of the Sina Weibo harvester is supported by a grant from the `Council on East Asian
  Libraries <http://www.eastasianlib.org/>`_.
* Prior development of SFM under the `previous repository <https://github.com/gwu-libraries/social-feed-manager>`_
  was supported by a grant (#LG-46-13-0257-13) from the `Institute of Museum and Library Services <http://www.imls.gov/>`_
  to George Washington University Libraries from 2013-2014.
