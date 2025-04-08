---
title: BBOP OBD visit
permalink: wiki/BBOP_OBD_visit
layout: wiki
tags:
 - Informatics
---

These are notes from Jim's and Cartik's visit to BBOP. Also of interest
are Chris Mungall's
<a href="BBOP_OBD_visit/Chris_notes" class="wikilink"
title="original notes">original notes</a> for a work plan for the week.

## Notes

### OBD model

- Began mapping of Phenex data model to OBD model. This is currently
  implemented in `org.phenoscape.bridge.OBDModelBridge.java`, in the
  Phenex source.
  - "Administrative" entities such as the character matrix, characters,
    and states, are modeled as instances of types from CDAO. This is
    currently done in a placeholder manner, e.g.
    "cdao:CharacterStateDataMatrix".
  - The mapper gives some of these entities generated IDs, which makes
    them easier to work with in OBD (avoiding blank nodes). These IDs
    are being generated because it doesn't seem prudent to rely on the
    given ID in the NeXML file/Phenex, as that is more of a local,
    in-file identifier. However, this presents complications for adding
    or modifying data for a data set already in OBD.
  - Need to interact with EvoInfo group to confirm correct usage of
    types and relations from CDAO.
  - Mapping of specimens is still to be implemented.
- Phenotypes
  - Quantities such as measurement are not yet handled. This will
    require further discussion between Cartik, Chris, and Jim. Beyond
    basic quantities, we want to also handle min and max, as defined in
    PhenoXML.
  - We may want to remove the count field from Phenex and input counts
    as measurements instead. The "count" unit is available in the units
    ontology. This is up for discussion at the moment.
  - The relation of a taxon to a phenotype is currently called
    "exhibits". The default semantics do not automatically map a
    phenotype to supertypes in the taxonomy ontology. However, such
    inferences could be desirable.
  - Could find "some particular genus" exhibits "all the phenotypes of
    its member species"
  - Need to decide if we want that to come from reasoner and then
    provide needed semantics to relation
  - This behavior would be consistent with how this relation is
    understood for a particular species (i.e. not all individuals must
    exhibit phenotype).
- Status of phylogeny data is still undecided and unimplemented. Could
  leave as an opaque piece of data and deal with only in application.
  Other extreme is to completely represent phylogeny via OBD links.
  Middle path could leave opaque but at least create relations to TTO
  taxa referenced within.

### OBD SQL

- Source:
  <https://obo.svn.sourceforge.net/svnroot/obo/obo-database/trunk>
- Instantiating the OBD database is easiest via running of scripts in
  the scripts directory in the OBDAPI project.
  - These scripts and those in the OBO-Edit project must all be in your
    Unix PATH.
  - Run `obd-create-db.pl -h `<HOST>` -d obdevo -c obdevo.conf`
  - Then run `obd-reasoner.pl -d obdevo@HOST`
  - This populates the deductive closure
  - "obdevo.conf" would just be a newline separated list of ontology IDs
    (teleost_anatomy, quality etc) or URLs
- These scripts are currently not written to accept arbitrary DB
  usernames and passwords, but work well for a DB on localhost with no
  password.
- The scripts are critical for easy importing of all needed ontologies.
- Workaround - created a local OBD instance on laptop, then dumped and
  imported into darwin.nescent.org.
- Importing dump into darwin.nescent.org is complicated by its attempt
  to create a plpgsql language, which can only be done by a DB
  superuser.
- Workaround - have superuser create language for a blank DB. Copy it as
  a template for future use ("emptydbplpgsql"). Comment out language
  creation in dump SQL. Import dump into darwin DB.
- We need to work with Chris and Rob on script workflow and handling of
  stricter DB security situations.

### OBD API

- Source: <https://obo.svn.sourceforge.net/svnroot/obo/OBDAPI/trunk>
- We used the OBD Java API to implement the mapping in Phenex (above),
  including data loader from Phenex into OBD.
- We successfully connected to and manipulated a local OBD database as
  well as an OBD instance at darwin.nescent.org via the OBD API.
- Queries to the API can be performed directly from the Restlet
  application. However, it would make sense to develop convenience APIs
  above OBDAPI for our application data model (reduce tedious traversals
  performed by view code).
- Cartik has implemented sample queries using the OBD API (these are on
  his machine and may not have been committed anywhere yet).

### OBD Web UI

- Source
  <https://geneontology.svn.sourceforge.net/svnroot/geneontology/OBDUI>
- BBOP instance: <http://spade.lbl.gov:8080/OBDUI>
- OBDUI project is quite easy to build and package into a WAR from
  Eclipse. Automated server builds via Ant are not yet implemented. Ant
  builds and automated deployment would be desirable from a NESCent
  perspective.
- It is also quite simple to run the OBDUI application directly from
  Eclipse via a local copy of Tomcat.
- Some of the URLs in the application including certain OBO identifiers
  require the following options enabled in Tomcat:
  - `-Dorg.apache.tomcat.util.buf.UDecoder.ALLOW_ENCODED_SLASH=true`
  - `-Dorg.apache.catalina.connector.CoyoteAdapter.ALLOW_BACKSLASH=true`
- Additional databases can be made available in the application by
  adding to the configuration in `WebContent/obdRestServletConfig.xml`.
- The Phenoscape web UI can be begun by implementing Phenoscape-specific
  Resources within the existing OBDUI project. The OBDUI application
  provides a useful infrastructure (such as important superclasses like
  `org.obd.ws.coreResource.OBDResource.java`), and the Phenoscape data
  source can easily be added in its own URL-space separate from other
  data sources loaded in the application.
- Longer term it may be wise to sort out better ways to develop a
  completely independent application which reuses functionality from the
  core OBDUI code.

### Phenex OBD interaction, OBD data loading

- Source: <https://obo.svn.sourceforge.net/svnroot/obo/phenote/trunk>
- Loading of data from Phenex into OBD is implemented in
  `org.phenoscape.bridge.OBDModelBridgeTest.java`, as a JUnit test.
- Ideally the reasoner needs to be run after ontology and data loading,
  to precompute relations.
- For this reason a "data warehousing" approach may be the best plan for
  using the current code.
  - Annotated data could be deposited into a public directory (possibly
    SVN), and a script could periodically clear and repopulate the
    database, by importing those files, then run the reasoner.
  - This approach also avoids issues still under consideration regarding
    unique IDs for particular datasets and how to import modifications
    to datasets already in ODB.
  - This would also keep ontology content up-to-date. The reasoner
    cannot currently remove previously precomputed links that an updated
    ontology version no longer implies.
