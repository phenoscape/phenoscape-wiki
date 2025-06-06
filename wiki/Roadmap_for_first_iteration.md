---
title: Roadmap for first iteration
permalink: wiki/Roadmap_for_first_iteration
layout: wiki
tags:
 - Archive
---

This is a development roadmap for the first production iteration of the
Phenoscape database and web interface, for introduction at the [SICB
2009 meeting](http://www.sicb.org/meetings/2009/index.php3).

## Nov. 10-14

### Jim

- **\[Complete\]** Document interface design requirements on wiki
  - See <a href="Web_UI_first_iteration" class="wikilink"
    title="overview">overview</a> and
    <a href="Web_UI_mockups" class="wikilink" title="mockup drawings">mockup
    drawings</a>.
  - These will continue to be updated.
- **\[Ongoing\]** Investigate and begin documenting additional data
  service needs required by interface
- **\[Complete\]** Start Rails web interface project; commit to SVN.
- **\[Complete\]** Write EQ count script, as per Paula's request, using
  Ruby; provide results to Phenoscape mailing list.

### Cartik

- **\[Complete\]** Set up Eclipse project for Restlet based web service
  application on personal machine, commit to OBD-WS SVN.
  - Cartik and Jim worked together on this and discussed the basics of
    Restlet applications.
  - Can be found in SVN at
    <https://obo.svn.sourceforge.net/svnroot/obo/OBD-WS/trunk>
- **\[Complete\]** Begin implementing dummy term info and autocomplete
  services.

## Nov. 17-21

### Jim

- **\[Ongoing\]** Document data retrieval web service specifications
  - Anatomy **\[Done\]**
  - Taxon **\[Postponed\]**
  - Genes **\[Done\]**
- **\[Complete\]** Implement Rails app skeleton and code front page
- **\[Complete\]** Implement reusable JavaScript term info panel and
  embed in front page search interface.
- **\[Postponed to after SICB\]** Address NEXUS/Phenote file merging
  issues with Paula. Provide problematic files as NeXML to Paula and
  Wasila.

### Cartik

- **\[Complete\]** Deploy OBD-WS application; continue deploying
  in-progress builds.
  - Package as WAR, deploy on Eryops.
  - Include dummy autocomplete and term info services.
- **\[Complete\]** Begin implementing live Term Info service within
  OBD-WS application.
- **\[Complete\]** Begin implementing live Autocomplete service within
  OBD-WS application.

## Nov. 24-28

### Jim

- **\[Complete\]** mostly on vacation

### Cartik

- **\[Complete\]** Complete Term Info service
- **\[Complete\]** Complete Autocomplete service.
  - *NOTES (December 9, 2008)*: Term info search and autocomplete
    services have been tested on Phenoscape database on Eryops.
  - Results for autocomplete are returned in JSON format and have been
    verified by Jim
- **\[Abandoned\]** Provide dummy Anatomy, Taxon, and Gene data
  service(s).

## Dec. 1-5

### Jim

- **\[Done\]** Implement anatomy UI.
- **\[Complete\]** Begin using autocomplete and term info services in
  all so-far developed user interfaces.

### Cartik

- **\[Complete 2008-11-20\]** Write code to parse ZFIN phenotype data
  and load into OBD
  - See <http://zfin.org/zf_info/downloads.html#phenotype>
  - Data: <http://zfin.org/data_transfer/Downloads/pheno_obo.txt>
  - should use "exhibits" relation
  - NOTES (Date: Nov 20, 2008):

  1.  ZFIN phenotype curations have been loaded into OBD database on
      Cartik's laptop along with 71 NeXML files from Phenoscape project
  2.  ZFIN curations use PHENOSCAPE:exhibits and PHENOSCAPE:hasAllele
      relations
  3.  Database size is 1.6 GB after running the OBD reasoner
  4.  Database upload to Darwin complete (Nov 21, 2008)
  5.  Loaded ZFIN data has been tested against OBD query engine and Term
      search engine. The latter is to be part of prototype to be demo'ed
      at SICB, Boston
- **\[Completed on 2008-12-10\]** Enhance OBD data loader pipeline to
  perform pre-processing of ZFA ontology, replacing xrefs with is_a
  links to TAO
  - These xrefs seem to still be in TAO - may have to fix that or work
    around
  - NOTES (Date: Dec 10, 2008)

  1.  Is a links corresponding to DbXref links between ZFA and TAO terms
      have been added to Phenoscape database
  2.  Is a links are added correctly irrespective of direction of DbXref
      link between ZFA and TAO terms
  3.  New Phenoscape database will be loaded into Darwin tomorrow via
      PGSQL dump

## Dec. 8-12

### Jim

- **\[Done\]** Complete anatomy user interface.
- **\[Ongoing\]** Begin implementing taxon user interface - changed to
  Gene interface

### Cartik

- **\[Complete\]** Complete ZFIN data loading tasks.
- **\[First version deployed 12-12-2008\]**Implement data service(s)
  related to Anatomy (requirements documented Nov. 17-21).
  - *NOTES*
    1.  Next version deployed on Dec 14, 2008
    2.  Tested on Eryops by Cartik on Dec 14
    3.  To be verified by Jim

## Dec. 15-19

### Jim

- Complete taxon user interface. **\[Postponed\]**
- **\[Ongoing\]** Implement and complete gene user interface.

### Cartik

- **\[Complete\]**Complete implementing Anatomy data services.
- **\[Complete\]**Begin implementing Taxon data services - changed to
  Gene.

## Dec. 22 - Jan. 2 (2 weeks)

### Jim

- Mostly on vacation.

### Cartik

- **\[Postponed\]**Complete Taxon data services.
- **\[Complete\]**Completely implement Gene data services.
  - *NOTES*
    1.  First few versions of anatomy data services have been
        implemented and deployed on Eryops as of Dec 20
    2.  First version of gene data services has been implemented and
        deployed on Eryops as of Dec 20

## Outcome

### Query UI

- Anatomy
- Taxon
- Gene

### Data Content

- Ontologies
- Anatomy ontologies linkage
- Phenoscape annotations (NeXML)
- ZFIN annotations (tab-delimited)
