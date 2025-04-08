---
title: Ontologies
permalink: wiki/Ontologies
layout: wiki
tags:
 - Ontology
---

The Phenoscape Project uses community anatomy, quality, spatial, and
taxonomic ontologies for the annotation of phenotypes from the
comparative biology literature. The development of these ontologies
follows OBO Foundry principles as much as possible, including reuse of
ontology terms as the preferred mechanism for using shared terms. These
ontologies can be downloaded, searched, and visualized at
[Ontobee](http://www.ontobee.org/),
[NCBO BioPortal](http://bioportal.bioontology.org/), or downloaded
from [OBO Foundry](http://www.obofoundry.org/). Ontologies can also be
edited and viewed using
the [Protégé](https://protege.stanford.edu/) desktop software.

# Anatomy Ontologies

## Uberon Anatomy Ontology

We use and contribute to the Uberon Anatomy Ontology, into which the
Teleost Anatomy Ontology, Amphibian Anatomy Ontology, and Vertebrate
Skeletal Anatomy Ontology were merged. More information about the
development of Uberon can be found in [Mungall et al.
(2012)](https://doi.org/10.1186/gb-2012-13-1-r5) and [Haendel et al.
(2014)](http://dx.doi.org/10.1186/2041-1480-5-21).

Uberon is separated into a core file and an "extension" file
(phenoscape-ext) which allows for separate editing by Phenoscape
curators and the core Uberon developers. New terms required by
Phensocape for annotation of vertebrate phenotypes are added to
phenoscape-ext, which also contains the terms sourced from the TAO, AAO,
and VSAO. We use the [Protégé](https://protege.stanford.edu/) desktop
software to edit phenoscape-ext. The release version of Uberon contains
both core and ext terms in a single file.

- Ontology update requests can be made on the Uberon term request
  tracker: [1](https://github.com/obophenotype/uberon/issues)
- Source edit file available here:
  [2](https://github.com/obophenotype/uberon-phenoscape-ext)

phenoscape-ext.owl is the editors version. The release uberon/ext.owl
retains the import chains and is pre-reasoned. uberon/ext.obo merges the
import chain into one ontology because obo does not have good support
for imports. Many of the other uberon derived artifacts such as
composite-metazoan do not use ext but this may be changed in the future.
See \[<http://uberon.org>; uberon.org\] for details of all the various
cuts.

## Anatomy ontologies merged with Uberon and no longer under development

### Vertebrate Skeletal Anatomy Ontology (VSAO)

VSAO contains terms representing structures in the skeletal system of
vertebrates. It references terms from the Common Anatomy Reference
Ontology (CARO), Gene Ontology (GO) Biological Process, Cell Ontology
(CL), and the Phenotype and Trait Ontology (PATO). VSAO can be
downloaded at the [OBO
Foundry](http://obofoundry.org/cgi-bin/detail.cgi?id=vertebrate_skeletal_anatomy)
and browsed at
[BioPortal](http://bioportal.bioontology.org/ontologies/45737?p=terms).
Development of the VSAO is described in [Dahdul et al.
(2012)](http://dx.plos.org/10.1371/journal.pone.0051070).

The VSAO as released represents the outcome of the
<a href="Skeletal_Anatomy_Jamboree" class="wikilink"
title=" skeletal anatomy workshop held at NESCent"> skeletal anatomy
workshop held at NESCent</a> and [corresponding paper in PLOS
ONE](http://dx.plos.org/10.1371/journal.pone.0051070). New skeletal
terms for the limb/fin and cranial skeleton have and will continue to be
added to the Phenoscape-ext ontology based on work done at the Phenotype
RCN Vertebrate Working Group meeting in Boulder, CO (June 1-3, 2011) and
from ongoing work.

### Teleost Anatomy Ontology (TAO)

TAO is a multi-species ontology for teleost fishes that was initialized
with terms from the Zebrafish Anatomical Ontology (ZFA). The development
of the TAO focused on the skeletal system because it varies
significantly across fishes, is well-preserved in fossil specimens, and
it is often the focus of morphologically-based evolutionary studies in
ichthyology. The development of the TAO is described in [Dahdul et al.
(2010)](http://sysbio.oxfordjournals.org/content/59/4/369.full). TAO can
be downloaded from the [OBO
Foundry](http://obofoundry.org/cgi-bin/detail.cgi?id=teleost_anatomy)
and browse at
[BioPortal](http://bioportal.bioontology.org/visualize/38362). Further
documentation <a href="Teleost_Anatomy_Ontology" class="wikilink"
title=" about TAO is described here"> about TAO is described here</a>.

### Amphibian Anatomy Ontology (AAO)

AAO is a multispecies ontology for amphibian anatomy. Development of AAO
is described in [Maglia et al.
(2007)](https://doi.org/10.1142/9789812772435_0035). View AAO at the
[BioPortal](http://bioportal.bioontology.org/ontologies/AAO). The last
updated version (April 2012) includes terms merged from the Xenopus
Anatomy Ontology and updates from David Blackburn and Wasila Dahdul.

## Model organism anatomy ontologies

Phenotype data for model organisms are imported into the Phenoscape KB
for mouse (MGI), human (HPO), zebrafish (ZFIN), and frog (Xenbase).
Uberon maintains cross-references to terms from the corresponding model
organism anatomy ontologies.

### Mouse Adult Gross Anatomy (MA)

The Adult Mouse Anatomy (MA) ontology contains terms that represent
structures in the postnatal mouse (*Mus*) and is used to annotate gene
expression and phenotypes for the mouse at [Mouse Genome Informatics
(MGI)](http://www.informatics.jax.org/) and other resources. Development
of the MA is described in [Hayamizu et al.
(2005)](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC1088948/).

- The MA is available for download at the [OBO
  Foundry](http://obofoundry.org/cgi-bin/detail.cgi?id=adult_mouse_anatomy)
  and can be browsed using the [Mouse Anatomy
  Browser](http://www.informatics.jax.org/searches/AMA_form.shtml).
- Term requests can be submitted on the [mouse anatomy
  tracker](http://sourceforge.net/tracker/?group_id=76834&atid=1205376)

### Xenopus Anatomy Ontology (XAO)

XAO contains terms that represent anatomical structures for the model
organism *Xenopus laevis* (African clawed frog).
[Xenbase](http://www.xenbase.org) uses XAO to annotate Xenopus gene
expression and phenotypes.

- XAO can be downloaded at the [OBO
  Foundry](http://obofoundry.org/cgi-bin/detail.cgi?id=xenopus_anatomy)
  and browsed at the
  [BioPortal](http://bioportal.bioontology.org/ontologies/45264?p=terms).
- Term tracker is available here:
  [3](https://sourceforge.net/tracker/?atid=1127722&group_id=76834)
- Source directory is available here:
  [4](http://phenoscape.svn.sourceforge.net/viewvc/phenoscape/trunk/vocab/xenopus_anatomy_2.0.8_eriks3.obo)

### Zebrafish Anatomical Ontology (ZFA)

ZFA is used by [ZFIN](http://zfin.org) to annotate mutant phenotypes for
the model organsim zebrafish (*Danio rerio*).

- Download from the [OBO
  Foundry](http://obofoundry.org/cgi-bin/detail.cgi?id=zebrafish_anatomy)
  or browse at the
  [BioPortal](http://bioportal.bioontology.org/ontologies/1051).
- Term requests can be submitted to the [ZFA
  tracker](http://sourceforge.net/tracker/?group_id=76834&atid=994726).
- Edit version is kept internally at ZFIN, but a prerelease edit version
  is available at
  [5](http://obo.cvs.sourceforge.net/viewvc/obo/obo/ontology/anatomy/gross_anatomy/animal_gross_anatomy/fish/preversion.zfish.obo)

ZFA terms are cross referenced to TAO terms, and these cross references
will be maintained and updated as needed.

## Previous work on ontology coordination

Previously, Phenoscape coordinated the development and integration of
vertebrate skeletal terms across anatomy ontologies for vertebrates,
with taxonomic focus on teleosts, zebrafish, amphibians, Xenopus,
amniotes, and mouse. The limb/fin branch was the primary focus of
ontology development in Phenoscape II. We held regular project
<a href="Anatomy_Ontology_Conf_calls" class="wikilink"
title=" anatomy ontology conference calls"> anatomy ontology conference
calls</a> to discuss ontology development with the curators of the
various anatomy ontologies (ZFA, XAO, MA). We also coordinated our
development calls with the [Phenotype RCN](http://phenotypercn.org)
vertebrate working group. Currently, we use and contribute new terms to
the Uberon anatomy ontology (metazoans) into which the Teleost Anatomy
Ontology, Amphibian Anatomy Ontology, and Vertebrate Skeletal Anatomy
Ontology were merged.

# Taxonomy Ontologies

## Vertebrate Taxonomy Ontology (VTO)

The Vertebrate Taxonomy Ontology [(Midford, Dececchi, et al.
2013)](http://dx.doi.org/10.1186/2041-1480-4-34) includes the TTO, ATO,
and uses the NCBI taxonomy as a source covering amniotes and basal
chordates outside the scope of the TTO. The ontology has an assigned OBO
purl [<http://purl.obolibrary.org>](http://purl.obolibrary.org), and
there is a repository at
[<https://code.google.com/p/vertebrate-taxonomy-ontology/>](https://code.google.com/p/vertebrate-taxonomy-ontology/).
The current release covers vertebrates and was built by starting with
the NCBI taxonomy for vertebrates and splicing in TTO (except hagfish),
and the downloadable [amphibiaweb
taxonomy](http://amphibiaweb.org/amphib_names.txt).  Subspecies names
were added to their parent species as synonyms (not subclasses). The
taxonomy is currently in the available in OWL format, as generated by
the OBO release tool. It also uses the Taxonomic Rank Vocabulary to tag
taxa with specified rank.

- [NCBI](http://www.ncbi.nlm.nih.gov/Taxonomy/taxonomyhome.html/) This
  taxonomy provides the amniote portions of the current VTO. This
  provides taxonomy for GenBank submissions (including fossil taxa), but
  does not claim to be an authoritative source (and generally doesn't
  cover taxa that have not been submitted). It does provide some
  taxonomic synonyms as well.
- [Paleobiology Database](http://paleodb.org/) This covers all groups
  represented in the fossil record - we have implemented a way to
  incorporate bulk taxonomy downloads in the VTO. We are still somewhat
  uncertain about how hierarchies are (dynamically) built in this
  resource.

These can provide links to additional synonyms and resources (e.g., TTO
uses fishbase to provide common names and links to their pages).
Taxonomic synonyms are particularly useful as aids to data curation, but
common names can assist users in browsing the website. Taxonomic
resources (above) can be used as sources of names as well.

- [Fishbase](http://www.fishbase.org/) - their taxonomy is close to TTO
  (both based on Catalog of Fishes). TTO (hence VTO) uses it as a source
  of common names and includes links to Fishbase's species pages.
- [Global Names Index (GNI)](http://gni.globalnames.org/) - Extensive
  list of names.

## Teleost Taxonomy Ontology (TTO)

The <a href="Teleost_Taxonomy_Ontology" class="wikilink"
title="Teleost Taxonomy Ontology">Teleost Taxonomy Ontology</a> (TTO) is
derived from the [Catalog of
Fishes](http://www.calacademy.org/RESEARCH/ichthyology/catalog/fishcatsearch.html)
(see also the [representation on
BioPortal](http://bioportal.bioontology.org/visualize/38363), which can
be navigated on-line). The TTO was developed from the Phenoscape I
project and provides coverage of fish in the VTO. The TTO is updated in
concert with Catalog of Fishes updates.

- The TTO in OWL format is [available
  here](http://purl.obolibrary.org/obo/tto.owl).
- Browse TTO [at
  BioPortal](http://bioportal.bioontology.org/ontologies/38703)

## Taxonomic Rank Vocabulary (TAXRANK)

During 2010, we released a separate
<a href="Taxonomic_Rank_Vocabulary" class="wikilink"
title="Taxonomic Rank Vocabulary">Taxonomic Rank Vocabulary</a>, and
removed all rank terms (e.g., family, genus, etc.) from the taxa within
the TTO. Taxa in the TTO specify their ranks as property values via the
metadata relation has_rank, but the object of the has_rank links is
contained in the TAXRANK vocabulary.

Developing TAXRANK as a vocabulary, rather than an ontology (e.g., by
defining an ordering relation between ranks) should facilitate its reuse
in other taxonomic ontologies. Developing a cross-authority (e.g., ICZN,
ICBN, etc.) ontology of ranks may be possible, but there does not appear
to be a compelling need for such an ontology.

- The TAXRANK vocabulary is available in OWL format
  [here](http://purl.obolibrary.org/obo/taxrank.owl).
- The vocabulary can be browsed at
  [Bioportal](http://bioportal.bioontology.org/ontologies/1419).

## Fish Collection Codes Vocabulary

There is a flat vocabulary of fish collections, based on [a list used in
Catalog of
Fishes](http://research.calacademy.org/research/ichthyology/catalog/abtabr.html),
though with a few additions listed on the
<a href="Fish_Collection_Updates" class="wikilink"
title="Fish Collection Updates">Fish Collection Updates</a> page. The
master list, from which the OBO-format ontology is generated is
available as a [google docs
spreadsheet](https://docs.google.com/spreadsheet/ccc?key=0AmUeHhtnDeCZcDZpa1YwVG82Zlhwcmc4OTk4elJhTlE).
It has been augmented with links to entries in the [Biodiversity
Collections Index](http://biodiversitycollectionsindex.org/).

The current release, as used in Phenex is [Fish Collection
Abbreviations](https://sourceforge.net/p/obo/svn/HEAD/tree/phenote/trunk/obo-files/fish_collection_abbreviation.obo)

## Amphibian Taxonomy Ontology (ATO)

The ATO has been deprecated in favor of generating the Amphibian
component of the VTO directly from
[Amphibiaweb](http://amphibiaweb.org/amphib_names.txt).

- [The version available at
  BioPortal](http://bioportal.bioontology.org/ontologies/40791?p=terms)
  is very old and neither used in VTO nor recommended.

## Additional documentation

- <a href="Documenting_taxon_concepts_used_in_a_publication"
  class="wikilink"
  title="Documenting taxon concepts used in a publication">Documenting
  taxon concepts used in a publication</a>
- <a
  href="Taxonomy_ontology:_ranks,_unknown/unnamed_species,_&amp;_related_issues"
  class="wikilink"
  title="Taxonomy ontology: ranks, unknown/unnamed species, &amp; related issues">Taxonomy
  ontology: ranks, unknown/unnamed species, &amp; related issues</a>
- <a href="Hypodigm" class="wikilink"
  title="Ambiguous specimen information: annotating phenotypes for specimens or species">Ambiguous
  specimen information: annotating phenotypes for specimens or species</a>
  (also called the Hypodigm problem)

# Shared Ontologies

These ontologies listed below were initiated by the model organism
communities. Phenoscape is actively involved in extending these
ontologies.

- [Phenotype and Trait Ontology
  (PATO)](http://bioportal.bioontology.org/visualize/38339)
- [Evidence Code
  Ontology](http://bioportal.bioontology.org/visualize/36625)
- [OBO-relations](http://www.obofoundry.org/ro/)
- [Spatial Ontology](http://bioportal.bioontology.org/visualize/29952)
- [Comparative Data Analysis Ontology
  (CDAO)](http://www.evolutionaryontology.org/), developed by the
  [EvoInfo working group](http://www.nescent.org/wg_evoinfo/Main_Page)
  at NESCent, and used within the Phenoscape OBD data repository.
