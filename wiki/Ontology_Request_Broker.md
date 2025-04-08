---
title: Ontology Request Broker
permalink: wiki/Ontology_Request_Broker
layout: wiki
tags:
 - Curation
 - Software
 - Phenex
---

In the process of annotating data files, curators may encounter terms in
the data that have not yet been added to an appropriate ontology.
Requesting a new ontology term and adding it to the ontology may take
several days or weeks when it involves discussion with other ontology
editors and requires a new production release of the ontology. For this
reason we have developed the Ontology Request Broker (ORB) for use with
<a href="Phenex" class="wikilink" title="Phenex">Phenex</a>. Using ORB,
when an appropriate ontology term cannot be found during annotation, the
curator simply requests a new term, providing a suggested label and
description, using a special interface within Phenex. A provisional term
is immediately created in the
[Bioportal](http://bioportal.bioontology.org) provisional term database
and added to the Phenex session for use by the curator. Independently,
this term can be provided with a permanent ID after the ontology editing
and release process are complete, and Phenex will automatically replace
references to the provisional term with the permanent ID.

## Components

### Phenex term request interface

![Phenex term request
panel\|250px](ORB-request.png "Phenex term request panel|250px") During
annotation in Phenex, curators can use the term request panel to obtain
provisional terms. See the
<a href="Phenex#Ontology_Request_Broker_.28ORB.29" class="wikilink"
title="Phenex documenation">Phenex documenation</a> for more details on
usage. Phenex interacts with the Bioportal provisional term services to
create provisional terms and also to query their properties and status.
At launch time Phenex loads all provisional terms previously created by
Phenoscape curators into its ontology session, making them available for
use in annotation.

### Bioportal provisional term services

The NCBO Bioportal provides [web services for creating, and querying and
updating the properties of, provisional
terms](http://www.bioontology.org/wiki/index.php/BioPortal_Provisional_Terms).
Provisional terms are created with a UUID-based IRI such as
<http://purl.bioontology.org/ontology/provisional/064dfc58-8143-491f-ab74-374507502f35>
(they currently do not dereference to anything useful). All Phenex
requests to the Bioportal services use a common Phenoscape user ID so
that curators can use any provisional term created by project members.

### Phenoscape provisional term management interface

Using the web-based [provisional term management
interface](http://phenoscape.github.io/orb-manager/app/#/provisional_terms),
Phenoscape ontology editors can review the requested terms,
independently of data annotation work. After adding a term to an
appropriate ontology, or deciding that an appropriate term already
exists, the management interface can be used to apply the preferred
permanent ID to the provisional term. The management interface, like
Phenex, makes use of Bioportal web services to interact with the
provisional terms database.

When Phenex opens a data file containing provisional terms, it checks to
see if any have been assigned permanent IDs. If so, the data is updated
to reference the permanent IDs.
