---
title: KB-OWL
permalink: wiki/KB-OWL
layout: wiki
---

This page describes the data model, data loading process, and query
methods being developed for a new version of the Phenoscape
Knowledgebase built on top of RDF and making use of standard OWL
reasoners.

## Data model

### Phenotypes

Phenotypes in the new data model are modeled as OWL class expressions.
They are now constructed in an inverse fashion from the form in the
original KB — rather than describing classes of particular qualities
which inhere in particular structures, we describe parts which bear
particular qualities (at the level of instance data the model is the
same: *inheres_in* is the inverse of *bearer_of*).

For example, "serrated dorsal fin":

- **old:** *exhibits* some (serrated and *inheres_in* some dorsal_fin)
- **new:** *has_part* some (dorsal_fin and *bearer_of* some serrated)

We can now model absence correctly. The previous version of the KB used
a quality class called 'absent' in a way which produces unintended
inferences. In the new model we use negation. For "dorsal fin, absent":

- not (*has_part* some dorsal_fin)

For a localized absence we would use a nested *has_part*:

- *has_part* some (head and not (*has_part* some scale))

The *has_part* formulation also provides the benefit of automatic
"present" inferences for structures used in any phenotype, not just
"present" phenotypes.

### Taxa and phenotype annotations

Taxa in the new data model are modeled as OWL individuals, rather than
OWL classes. Thus, the taxonomic hierarchy is represented directly in
RDF as a tree of *subclade_of* property relationships between taxa,
rather than OWL subclass axioms. This model allows for richer modeling
of how phenotypes are propagated due to taxon membership and ancestral
states than a class-based taxonomy
([1](http://www.mendeley.com/download/public/2280031/4561422715/faae92a74742bc35ceca9b3f5862cb94a4cde61e/dl.pdf)).

A given phenotype expression (*has_part* some ...) describes the
condition of an individual organism, not a whole taxon. So to create a
phenotype annotation for a taxon, the relationship of this organism to
the taxon must be captured. We use one of two forms,
<a href="Semantics_of_phenotype_annotations" class="wikilink"
title="depending on the intended meaning">depending on the intended
meaning</a>:

- **Observation annotation:** *has_member* some (*has_part* some
  (dorsal_fin and *bearer_of* some serrated))
- **Ancestral state annotation:** *has_progenitor* some (*has_part* some
  (dorsal_fin and *bearer_of* some serrated))

The actual phenotype annotation can be created as a class assertion
axiom for the given taxon:

- Ictalurus_punctatus Type (*has_member* some (*has_part* some
  (dorsal_fin and *bearer_of* some serrated)))

### Genes and phenotype annotations

## Reasoning

Currently all reasoning is conducted during the data load process, in
which required inferences are precomputed and then asserted in the data.
This allows for more expressive reasoning than is available at query
time (for example, RDFS reasoners in triplestore SPARQL engines), and
also allows for faster queries (since all need facts are asserted).

*Need more here about advantages and limitations.*

## Data loader

The data loader is a set of Scala classes which manipulate ontologies in
various ways. They can be called from within an Ant file which describes
the build process. The data loader classes are developed within the
[phenoscape-owl-tools](https://github.com/phenoscape/phenoscape-owl-tools)
project. The Ant file which builds the RDF files constituting the KB
triplestore is part of the
[phenoscape-builder](https://github.com/phenoscape/phenoscape-builder)
project.

## Data store
