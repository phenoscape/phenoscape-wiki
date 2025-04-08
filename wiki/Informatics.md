---
title: Informatics
permalink: wiki/Informatics
layout: wiki
tags:
 - Informatics
---

This page provides a broad overview of our informatics activities.
Phenoscape supports open development processes and collaboration. All
source code we create is available from open source repositories such as
Sourceforge, and we work with existing open-source projects whenever
possible. Development plans can be found at our
<a href="software_roadmap" class="wikilink"
title="software roadmap">software roadmap</a>.

One of the chief objectives of the Phenoscape project is to present a
centralized repository to store annotations entered by curators. These
annotations can be queried from a user interface and used to answer
<a href="Driving_Research_Questions" class="wikilink"
title="Driving Research Questions">Driving Research Questions</a> and
for advanced <a href="Phenoscape_use_cases" class="wikilink"
title="Phenoscape use cases">Phenoscape use cases</a>. The following
tools which are under various stages of development, will serve to
realize this objective.

## Phenoscape software components

### Phenex curation tool

<a href="Phenex" class="wikilink" title="Phenex">Phenex</a> is a
platform-independent desktop application for annotating
character-by-taxon matrices with ontology terms. Phenex allows a user to
describe phenotypic variation among taxa (or specimens) using
Entity-Quality syntax and write the data to a NeXML file. Phenex is
written in Java, based on code from the [OBO-Edit](http://oboedit.org/)
and [Phenote](http://www.phenote.org/) project, and is being released
under an open-source license. It can be configured to load user-selected
ontologies, and in this way can be adapted to data curation in different
taxonomic groups.

### Phenoscape data repository

We are adopting [OBD](http://berkeleybop.org/obd/) as the
ontology-driven datastore for our phenotype annotations. We are
collaborating with the [Berkeley Bioinformatics Open-source
Projects](http://www.berkeleybop.org/) group in driving future
development of OBD. The ontological definitions of all the terms used in
the annotation stage (on Phenex) and the annotations themselves are
stored in the <a href="Phenoscape_data_repository" class="wikilink"
title="Phenoscape data repository">Phenoscape data repository</a>. In
sequential order, the term definitions in all the ontologies are first
downloaded and stored in the database. Next, the annotations of
phenotypes are downloaded from [ZFIN](http://zfin.org) and
[Phenoscape](http://phenoscape.svn.sourceforge.net), post composed and
stored in the database. An outline of these two stages is described in
the <a href="Phenoscape_data_loader" class="wikilink"
title="Phenoscape data loader">Phenoscape data loader</a> section. Then,
the <a href="OBD_Reasoner" class="wikilink" title="OBD Reasoner">OBD
Reasoner</a> is used to extract inferences from the annotations and
definitions in the OBD Phenoscape database. These inferences are added
to the database as well.

### Data services built on OBD

We are also developing a suite of web services on top of OBD to serve as
a data access API and foundation for our user-oriented Phenoscape web
application. These web services make use of mostly standard SQL queries
and present a
[RESTful](http://en.wikipedia.org/wiki/Representational_State_Transfer)
service interface using [Restlet](http://www.restlet.org/). The
specifications of these services are detailed in
<a href="Data_Services" class="wikilink" title="Data Services">Data
Services</a>.

### Phenoscape web UI

The <a href="Phenoscape_web_UI" class="wikilink"
title="Phenoscape web application">Phenoscape web application</a> will
allow scientists to browse and query the phenotype annotations as well
as the supporting ontologies. Initially, the query capabilities will
concentrate on implementing a select set of "use-cases", research
questions that show the utility of the approach. Ultimately, we will
build interfaces that allow researchers to ask open-ended questions of
the data. The web application is being developed using [Ruby on
Rails](http://www.rubyonrails.org/) and accesses phenotype data and
ontology information via our OBD web services.

### Synchronization Tool

The <a href="Synchronization_Tool" class="wikilink"
title="Synchronization Tool">Synchronization Tool</a> is a plug-in for
[OBO-Edit](http://oboedit.org/) which aided in keeping the Teleost
Anatomy Ontology (no longer in development) and the Zebrafish Anatomy
Ontology consistent with each other.

## Source code

Phenoscape-created source code is primarily hosted at Github within the
[Phenoscape organization](http://github.com/phenoscape). Some legacy
projects and data are still hosted in [our Sourceforge
repository](http://phenoscape.svn.sourceforge.net/viewvc/phenoscape).
Some code is being contributed back directly to a variety of existing
projects we build upon, such as the [OBO Subversion
repository](http://obo.svn.sourceforge.net/viewvc/obo/) on SourceForge.

- Phenex:
  - [Github home](http://github.com/phenoscape/Phenex)
- Database and database loading:
  - [Browse
    source](http://obo.svn.sourceforge.net/viewvc/obo/OBDAPI/trunk/scripts)
  - Code check out:
    `svn co `[`http://obo.svn.sourceforge.net/svnroot/obo/OBDAPI/trunk`](http://obo.svn.sourceforge.net/svnroot/obo/OBDAPI/trunk)
- Data services and middleware:
  - Data model and database access API (OBD-API):
    - [Browse
      source](http://obo.svn.sourceforge.net/viewvc/obo/OBDAPI/trunk)
    - Code check out:
      `svn co `[`http://obo.svn.sourceforge.net/svnroot/obo/OBDAPI/trunk`](http://obo.svn.sourceforge.net/svnroot/obo/OBDAPI/trunk)
  - Web-services (OBD-WS):
    - [Github home](http://github.com/phenoscape/PhenoscapeOBD-WS)
- Web-based user interface ([Knowledge Base](http://kb.phenoscape.org)):
  - [Github home](http://github.com/phenoscape/PhenoscapeWeb)
- Ontology conversion and management:
  - TTOUpdate
    - [Browse
      source](http://obo.svn.sourceforge.net/viewvc/phenoscape/trunk/tools/TTOUpdate)
    - Code checkout:
      `svn co `[`http://obo.svn.sourceforge.net/svnroot/phenoscape/trunk/tools/TTOUpdate`](http://obo.svn.sourceforge.net/svnroot/phenoscape/trunk/tools/TTOUpdate)
  - Synchronization Tool
    - [Github home](http://github.com/phenoscape/synctool-oboedit)
- Other scripts and small tools:

## Affiliated projects

### NeXML

Phenex saves character matrix data using the evolutionary data standard
[NeXML](http://www.nexml.org/). NeXML is an XML Schema and has robust
facilities for embedding additional data, such as our phenotype
annotations, within a traditional character-by-taxon matrix.
