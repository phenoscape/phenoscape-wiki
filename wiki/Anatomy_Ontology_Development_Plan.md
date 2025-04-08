---
title: Anatomy Ontology Development Plan
permalink: wiki/Anatomy_Ontology_Development_Plan
layout: wiki
tags:
 - Anatomy
 -  Ontology
---

1.  REDIRECT
    <a href="Ontologies" class="wikilink" title="Ontologies">Ontologies</a>

The Phenoscape project is coordinating the development and integration
of multispecies and single species anatomy ontologies for vertebrates,
with taxonomic focus on teleosts, zebrafish, amphibians, Xenopus,
amniotes, and mouse. The limb/fin branch is the focus of ontology
development in year 1.

The development of these ontologies follows [OBO Foundry
principles](http://obofoundry.org/). Reusing ontology terms (by import
or MIREOT) is the preferred mechanism for using shared terms and VAO
will be imported into TAO, AAO, and AMAO. However, the existing model
organism databases are largely hardcoded to reference identifiers for
their own ontologies (e.g., MGI database reads MA term identifiers). In
the long term, we will be exploring how to import terms into these
ontologies. In the interim, the existing MOD vertebrate ontologies will
continue to duplicate equivalent terms from other ontologies, with
cross-references to the external ontology identifiers.

## Year 1 Development Plan

### Vertebrate Musculoskeletal Anatomy Ontology (VAO)

VAO will be expanded to include terms in the muscular and skeletal
systems that are shared by two or more multispecies vertebrate
ontologies. These shared terms will be imported into the multispecies
ontologies. For example, ‘femur’, a term applicable to AAO and AMAO,
will be added to VAO and imported into AMAO (Year 1) and AAO (Year 2).
Shared terms that already exist in multispecies ontologies will be
obsoleted, given a "replaced_by" relationship to the relevant VAO term,
and the shared term subsequently imported into the ontology. Terms
shared by a multispecies ontology and its corresponding single-species
ontology (e.g., AAO and XAO) would also ideally be imported from the
multispecies ontology into the single species ontology (or rather, a
single ontology for that taxonomic group could be used). However,
because MODs currently cannot import terms, shared terms will instead be
duplicated in single species ontologies and cross-referenced to the term
in the external ontology. For example, because XAO and AAO both contain
‘radio-ulna’, the term XAO term will cross-reference the AAO ID for
radio-ulna.

**Next target release date:** Late August 2011

**Features:**

- New skeletal terms for the limb/fin and cranial skeleton will be added
  based on work done at the Phenotype RCN Vertebrate Working Group
  meeting in Boulder, CO (June 1-3, 2011)
- Relationships to terms from external ontologies (GO, PATO, CL) will be
  included

### Teleost Anatomy Ontology (TAO)

**Next target release date:** Late August 2011

**Features:**

- VAO musculo-skeletal terms will be imported, and existing TAO terms
  applicable outside of Teleostei will be obsoleted and added to VAO for
  subsequent import

### Amphibian Anatomy Ontology (AAO)

**Next target release date:** Late August 2011

'''Features:

- children of "unclassified anatomical entity" will be given appropriate
  is_a parents
- add VAO xrefs

As a long term goal, AAO and XAO will be aligned, XAO terms will cross
reference their AAO parents, and these ontologies will be regularly
synchronized. However, because AAO development is not scheduled for the
first year (whereas XAO will be adding many new non-skeletal terms), an
initial synchronization at the beginning of year 1 will take place,
followed by cloning AAO from XAO at the beginning of year 2.
Specifically, AAO terms applicable to Xenopus will be added to XAO and
given an AAO xref. If AAO xrefs VAO, then the VAO ID should be used
preferentially over the AAO ID. Relationships for xrefed terms will be
the same as those in AAO. AAO terms not applicable to Xenopus won't be
added or cross-referenced in XAO. In Year 1, XAO will continue to add
new terms whereas AAO development will be frozen.

In Year 2, AAO will be cloned out from XAO, with AAO xrefs converted
into primary AAO IDs and new AAO identifiers created for terms added to
XAO in year 1. The non-Xenopus AAO terms that weren't added to XAO will
then be added to the newly cloned AAO. XAO will retain xrefs to AAO
terms.

### Amniote Anatomy Ontology (AMAO)

**Next target release date:**

'''Features:

- In the initial release, musculo-skeletal terms from VAO and
  non-skeletal terms from the amniote subset of the Uber Anatomy
  Ontology
  [(Uberon)](http://obofoundry.org/cgi-bin/detail.cgi?id=uberon) will be
  imported into AMAO

### Zebrafish Anatomical Ontology (ZFA)

ZFA terms are cross referenced to TAO terms, and these cross references
will be maintained and updated as needed. In addition, cross references
to VAO musculo-skeletal terms will be added.

**Next target release date:**

**Features:**

### Xenopus Anatomy Ontology (XAO)

(see desciption of XAO/AAO merge above)

**Next target release date:**

**Features:**

- Cross references to AAO and VAO musculo-skeletal terms will be added

### Mouse Adult Gross Anatomy (MA)

**Next target release date:**

'''Features:

- Cross references to VAO musculo-skeletal terms will be added
