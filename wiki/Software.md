---
title: Software
permalink: wiki/Software
layout: wiki
---

This page provides a overview of our software development activities.
Phenoscape supports open development processes and collaboration. All
source code we create is available from open source repositories such as
[Github](http://github.com/phenoscape) and
[Sourceforge](http://sourceforge.net/projects/phenoscape/), and we work
with existing open-source projects whenever possible.

## Phenoscape Knowledgebase

One of the chief objectives of the Phenoscape project is to present a
centralized repository to store evolutionary phenotype annotations
entered by curators and also integrate relevant data imported from
partner projects. The Knowledgebase consists of a back-end semantic data
store, web services which provide a query API for the data, a web
application user interface allowing exploration of the Knowledgebase,
and accessory tools for loading data. To meet requirements for
scalability, reasoning expressivity, and support for linked data
standards, we are developing a our Knowledgebase infrastructure using
the RDF and OWL semantic web standards.

The live KB can be accessed at <http://kb.phenoscape.org/>. For more
information on the Phenoscape Knowledgebase see these wiki pages:

- <a href="Phenoscape_KB" class="wikilink"
  title="Phenoscape KB">Phenoscape KB</a>
- <a href="KB_build_process" class="wikilink" title="KB build process">KB
  build process</a>

Software components:

- [phenoscape-owl-tools](http://github.com/phenoscape/phenoscape-owl-tools)—build
  application for generating the RDF content for the Phenoscape KB,
  including utilities for converting datasets to OWL and running
  reasoning tasks. Written in Scala using the OWL API.
- [phenoscape-kb-services](http://github.com/phenoscape/phenoscape-kb-services)—updated
  web services API for the Knowledgebase. Written in Scala using
  [Spray](http://spray.io) web services.
- [phenoscape-kb-ui](http://github.com/phenoscape/phenoscape-kb-ui)—Phenoscape
  KB web user interface. A client-side web application using AngularJS.
- [phenoscape-data](http://github.com/phenoscape/phenoscape-data)—document
  store for semantically annotated character matrix files. This is the
  evolutionary data content for the Phenoscape KB. NeXML.
- [owlet](http://github.com/phenoscape/owlet)—integration of OWL
  reasoner queries within SPARQL. It parses embedded OWL class
  expressions and uses an OWL reasoner to either generate a new query by
  injecting FILTER statements containing the reasoner results, or
  instead return the reasoner results in SPARQL results format (for use
  in [SPARQL federated
  queries](http://www.w3.org/TR/sparql11-federated-query/)). Written in
  Scala using OWL API and Jena.
- [owlery](http://github.com/phenoscape/owlery)—web service interface
  for OWL API reasoner queries. In addition to direct DL queries, Owlery
  provides a SPARQL endpoint powered by Owlet. Written in Scala using
  Spray web services.
- [scowl](http://github.com/phenoscape/scowl)—a Scala library allowing a
  declarative approach to composing OWL expressions and axioms using the
  [OWL API](http://owlapi.sourceforge.net/). Written in Scala.

## Software tools to access and analyze KB data

- [RPhenoscape](http://rphenoscape.phenoscape.org/)— R package that
  facilitates interfacing with the Phenoscape Knowledgebase for
  searching ontology terms, querying data matrices, obtaining dependency
  matrices, and computing semantic similarity metrics.

<!-- -->

- [OntoTrace](http://beta.phenoscape.org/#/ontotrace) — tool used to
  query the KB for a synthetic character matrix of asserted and inferred
  presence/absence characters for anatomical structures. OntoTrace is
  also accessible by using
  [RPhenoscape](http://rphenoscape.phenoscape.org/) to query the web
  services API.

## Data curation tools

- [Phenex](http://github.com/phenoscape/Phenex)—ontology annotation
  software tailored for phenotype annotation of evolutionary character
  matrices. It saves ontology annotations alongside traditional
  character matrix data using the [NeXML](http://www.nexml.org/) format
  standard for evolutionary data. Also see the
  <a href="Phenex" class="wikilink" title="Phenex homepage">Phenex
  homepage</a>.
- [phenoscape-nlp](http://github.com/phenoscape/phenoscape-nlp)—Phenoscape
  version of the <a href="CharaParser" class="wikilink"
  title="CharaParser">CharaParser</a> natural-language processing tool,
  which analyzes the text of character-state descriptions to produce a
  structured output used to generate proposals for ontological phenotype
  annotations. We are working to enhance the performance of CharaParser
  and also to integrate it with Phenex, so that data curators can take
  advantage of natural-language processing to accelerate their workflow.
  Developed and maintained by [Hong
  Cui](http://hongcui.faculty.arizona.edu).
- [charaparser-unsupervised](http://github.com/phenoscape/charaparser-unsupervised)—implementation
  of the CharaParser unsupervised learning algorithm in Java, to be
  incorporated into the main CharaParser code.

## Other active projects

- [presence-absence-matrix](http://github.com/phenoscape/presence-absence-matrix)—tool
  for querying a local copy of the Phenoscape KB and generating a
  synthetic presence/absence character matrix using anatomical
  reasoning.
- [kb-sparql-queries](http://github.com/phenoscape/kb-sparql-queries)—miscellaneous
  queries for use with the Phenoscape KB SPARQL endpoint. Used for
  reports and may also aid in navigating the KB RDF datamodel.
- [phenoscape.github.com](http://github.com/phenoscape/phenoscape.github.com)—source
  for Phenoscape public website
- [phenoscape-ontologies](http://github.com/phenoscape/phenoscape-ontologies)—ontologies
  developed internally for the Phenoscape project. Currently contains
  only a demonstration ontology for presence/absence reasoning.
- [Taxonomy-Ontology-Tool](http://github.com/NESCent/Taxonomy-Ontology-Tool)—tool
  used to assemble the VTO by starting from an initial taxonomy (NCBI)
  and deleting and splicing in group specific taxonomies (e.g., TTO,
  ATO).
- [phenoday-reasoning-paper](http://github.com/phenoscape/phenoday-reasoning-paper)—Demonstration
  code for [paper
  submission](http://phenoday2014.bio-lark.org/pdf/11.pdf) to the
  Bio-ontologies SIG [Phenotype Day](http://phenoday2014.bio-lark.org)
  at ISMB 2014.

## Exploratory projects

These are in a state of preliminary development or just for
exploration/testing.

- [vue2owl](http://github.com/phenoscape/vue2owl)—Convert a VUE document
  to an OWL ontology. Scala.

## Repositories no longer being used/maintained

### Classic Phenoscape KB

The first edition of the Phenoscape Knowledgebase is still live at
<http://fish.phenoscape.org/>. It makes use of the following software
projects:

- [OBD](http://berkeleybop.org/obd/) - an ontology-driven datastore
  developed by the [Berkeley Bioinformatics Open-source
  Projects](http://www.berkeleybop.org/) group. It provides a generic
  schema for storing ontologies and semantic data expressed with those
  ontologies. It also includes an automated reasoner used to materialize
  inferred knowledge into the datastore. The master build script for
  loading the Phenoscape Knowledgebase is included within the [OBD
  source code](http://obo.svn.sourceforge.net/svnroot/obo/OBDAPI/trunk).
- [PhenoscapeOBD-WS](http://github.com/phenoscape/PhenoscapeOBD-WS) - a
  suite of web services on top of OBD to serve as a data access API and
  foundation for our user-oriented Phenoscape web application. These web
  services present a
  [RESTful](http://en.wikipedia.org/wiki/Representational_State_Transfer)
  service interface using the [Restlet](http://www.restlet.org/) Java
  API. The specifications of these services are detailed in
  <a href="Data_Services" class="wikilink" title="Data Services">Data
  Services</a>.
- [PhenoscapeWeb](http://github.com/phenoscape/PhenoscapeWeb) - a web
  application providing user-friendly interfaces for browsing and
  querying data and ontologies within the Knowledgebase, written using
  Ruby on Rails.
- [PhenoscapeDataLoader](http://github.com/phenoscape/PhenoscapeDataLoader) -
  a Java library providing translations of various data inputs into the
  OBD model, used within the OBD build script.

### Others

- [phenoscape-builder](http://github.com/phenoscape/phenoscape-builder)—early
  Ant-based tool for building the RDF-based KB. Replaced by Scala script
  within
  [phenoscape-owl-tools](http://github.com/phenoscape/phenoscape-owl-tools).
- [skeleton-image-annotation](http://github.com/phenoscape/skeleton-image-annotation)—reference
  images for the vertebrate skeleton annotated with Uberon terms, using
  Phenote.
- [phenoscape-kb-rdf-data](http://github.com/phenoscape/phenoscape-kb-rdf-data)—some
  obsolete full dumps of the RDF knowledgebase. We are exploring making
  current data dumps available elsewhere, such as at
  <http://datahub.io>.
- [Phenotype-Matching-Queries](http://github.com/phenoscape/Phenotype-Matching-Queries)
- [CMAPOBO](http://github.com/phenoscape/CMAPOBO)
- [synctool-oboedit](http://github.com/phenoscape/synctool-oboedit)
- [ontophenotype-eol](http://github.com/phenoscape/ontophenotype-eol)
- TTOTool...
