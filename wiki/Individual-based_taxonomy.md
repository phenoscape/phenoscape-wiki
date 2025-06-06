---
title: Individual-based taxonomy
permalink: wiki/Individual-based_taxonomy
layout: wiki
tags:
 - Reasoning
 - Ontology
---

Representing evolutionary lineages using ontological individuals has
some modeling advantages, and may be more realistic, compared with using
a simple class hierarchy. We described some of the rationale in [these
ICBO conference proceedings](http://ceur-ws.org/Vol-833/paper82.pdf).
For the purposes of the Phenoscape KB, this model supports specification
of the <a href="Semantics_of_phenotype_annotations" class="wikilink"
title="semantics of particular phenotype annotations">semantics of
particular phenotype annotations</a>: the phenotype applies to all
members of a clade, is observed for some members, or is applied to the
ancestor of the members.

In the KB build process, the VTO taxon class hierarchy is translated
into a relationship graph. For every class relationships such as

`Class: Ictaluridae`  
`    SubClassOf: Siluriformes`

individuals with the same IDs (using OWL punning) are created with a
relationship such as:

`Individual: Ictaluridae`  
`    Facts: subCladeOf Siluriformes`

The properties used in the evolutionary lineage model are currently held
in the [Phenoscape KB vocabulary
ontology](http://purl.org/phenoscape/vocab.owl) (a holding place for
KB-specific and preliminary terms). These include the inverse property
pairs *subCladeOf/containsClade* (taxon to taxon) and
*memberOf/hasMember* (organism to taxon/taxon to organism). *subCladeOf*
is transitive, and also a member of a given taxon is inferred to be a
member of all taxa containing that taxon (using a property chain).

## Comparison with CDAO tree model

The [Comparative Data Analysis
Ontology](http://www.evolutionaryontology.org/cdao) (CDAO) includes
classes and properties for modeling phylogenetic trees which are
different from the ones used here. We distinguish between models of
information artifacts (e.g. a phylogeny produced by a particular
analysis), such as is described by CDAO, and models of evolutionary
lineages in nature. Obviously they are tightly related; the former is
used to make hypotheses about the latter. However, the type of reasoning
we would like to enable for each may be slightly different. The
usefulness of this distinction is not yet well developed, however one
example is that for a phylogenetic tree information artifact we can
state that we know all of the nodes descending from a given node; i.e.
we can close some of the open world.
