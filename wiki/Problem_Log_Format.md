---
title: Problem Log Format
permalink: wiki/Problem_Log_Format
layout: wiki
tags:
 - Informatics
 - Database
 - Curation
 - Help
---

The <a href="Data_Repository_and_Data_Services#Phenoscape_Data_Loader"
class="wikilink" title="Phenoscape Data Loader">Phenoscape Data
Loader</a> is responsible for loading curated NeXML data, along with the
ontological definitions of the terms used in the curation. Often, the
curated files are in varying degrees of completeness comprising records
with blank placeholders for taxon names and phenotype descriptions. Such
records are not inserted into the database, because there is no real use
for them until they are complete. Instead, these records are entered
into a Problem Log by the Data Loader which can then be viewed and
worked upon by curators. This is an excerpt from such a Problem Log
created during the execution of the Data Loader. The problematic,
incomplete records are grouped under the name of the curated NeXML file
which contained them.

The current problem log can be found
[here](https://obo.svn.sourceforge.net/svnroot/obo/phenex/trunk/testfiles/problemLog.txt).

## PROBLEM LOG

**Buckup_1998.xml**

- Taxon: TTO:1030219 exhibits null phenotype
- Null identifier for taxon: untitled exhibiting quality cartilaginous
  inhering in mesethmoid-prevomer joint
- Null identifier for taxon: untitled exhibiting null phenotype
- Taxon: TTO:1004541 exhibits null phenotype
- Taxon: TTO:1004170 exhibits null phenotype
- Null identifier for taxon: untitled exhibiting quality present
  inhering in antorbital
- Taxon: TTO:1004398 exhibits null phenotype
- Taxon: TTO:1030015 exhibits null phenotype
- Taxon: TTO:1029666 exhibits null phenotype
- Taxon: TTO:1020741 exhibits null phenotype
- Taxon: TTO:1004142 exhibits null phenotype
- Taxon: TTO:1004160 exhibits null phenotype
- Taxon: TTO:1004148 exhibits null phenotype
- Null identifier for taxon: untitled exhibiting quality present
  inhering in upper pharyngeal 4 tooth
- Null identifier for taxon: untitled exhibiting quality absent inhering
  in rhinosphenoid

... ...

**Castro_Vari_2004.xml**

- Taxon: TTO:1030219 exhibits null phenotype
- Null identifier for taxon: untitled exhibiting quality cartilaginous
  inhering in mesethmoid-prevomer joint
- Null identifier for taxon: untitled exhibiting null phenotype
- Taxon: TTO:1004541 exhibits null phenotype\*\*Taxon: TTO:1004170
  exhibits null phenotype
- Null identifier for taxon: untitled exhibiting quality present
  inhering in antorbital
- Taxon: TTO:1004398 exhibits null phenotype
- Taxon: TTO:1030015 exhibits null phenotype
- Taxon: TTO:1029666 exhibits null phenotype
- Taxon: TTO:1020741 exhibits null phenotype
- Taxon: TTO:1004142 exhibits null phenotype
- Taxon: TTO:1004160 exhibits null phenotype
- Taxon: TTO:1004148 exhibits null phenotype
- Null identifier for taxon: untitled exhibiting quality present
  inhering in upper pharyngeal 4 tooth

... ...

**Langeani_1998.xml** .. .. ..
