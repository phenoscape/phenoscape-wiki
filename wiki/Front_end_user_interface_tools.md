---
title: Front end user interface tools
permalink: wiki/Front_end_user_interface_tools
layout: wiki
tags:
 - Informatics
 - API
 - User Interface
---

### Phenex curation tool

<a href="Phenex" class="wikilink" title="Phenex">Phenex</a> is an
application for annotating character matrix files with ontology terms to
describe phenotypes and identify taxa. Phenex is a Java application
based on code from the [OBO-Edit](http://oboedit.org/) and
[Phenote](http://www.phenote.org/) projects. While still under
development, Phenex is ready for use and enables our ongoing data
curation activities.

### Data services built on OBD

We are adopting
[OBD](http://www.bioontology.org/wiki/index.php/OBD:Main_Page) as the
ontology-driven datastore for our phenotype annotations. We are
collaborating with the [Berkeley Bioinformatics Open-source
Projects](http://www.berkeleybop.org/) group in driving future
development of OBD. We are also developing a suite of web services on
top of OBD to serve as a data access API and foundation for our
user-oriented Phenoscape web application. These web services make use of
the OBD Java API and present a
[RESTful](http://en.wikipedia.org/wiki/Representational_State_Transfer)
service interface using [Restlet](http://www.restlet.org/).

### Phenoscape web UI

The Phenoscape web application will allow scientists to browse and query
the phenotype annotations as well as the supporting ontologies.
Initially, the query capabilities will concentrate on implementing a
select set of "use-cases", research questions that show the utility of
the approach. Ultimately, we will build interfaces that allow
researchers to ask open-ended questions of the data. The web application
is being developed using [Ruby on Rails](http://www.rubyonrails.org/)
and accesses phenotype data and ontology information via our OBD web
services.
