---
title: Taxonomic Ranks
permalink: wiki/Taxonomic_Ranks
layout: wiki
tags:
 - Ontology
 - Taxonomy
---

See also the <a href="Taxonomic_Rank_Ontology" class="wikilink"
title="Taxonomic Rank Ontology">Taxonomic Rank Ontology</a> being under
development.

## Developing an Ontology for Taxonomic Ranks

When the Teleost Taxonomy Ontology (TTO) was submitted to OBO, the
suggestion was made that the terms for taxonomic ranks (e.g., Family,
Genus, Species) should be broken out. At present, taxonomic ranks are
included in the TTO and cross referenced to similar terms in the NCBI
taxonomy ontology. Although the process of constructing an ontology of
rank terms is straightforward, there are some semantic issues that need
to be resolved.

The current implementation can be diagrammed as follows:

`       Cyprinidae   -------------------->  Family`  
`            ^             has_rank`  
`            |`  
`       is_a |`  
`            |`  
`         Devario    -------------------->  Genus`  
`            ^             has_rank`  
`            |`  
`       is_a |`  
`            |`  
` Devario aequipinnatus ---------------->  Species`  
`                         has_rank`

In the first draft of the ranks ontology, submitted to Chris Mungal and
Michael Ashburner, the rank terms are simply subclasses of
taxonomic_rank. There is no relation defined between the rank terms. The
has_rank relation, as defined in the NCBO ontology is a meta_data
relation (c.f. OWL annotation properties), which means it is intended to
be ignored by any reasoner.

As there is clearly an ordering among the rank terms, it would be
worthwhile to define an ordering relation between terms so that the term
'family' is indicated as 'larger' or 'more inclusive' than the term
'genus.'

The proposed situation is

`         TTO                                TaxonRank Ontology`

`       Cyprinidae   -------------------->  Family`  
`            ^             has_rank           ^`  
`            |                                |`  
`       is_a |                                |  "rank_order"`  
`            |                                |`  
`         Davario    -------------------->  Genus`  
`            ^             has_rank           ^`  
`            |                                |`  
`       is_a |                                |  "rank_order"`  
`            |                                |`  
` Davario aequipinnatus ---------------->  Species`  
`                         has_rank`

There has been some question as to the nature of this ordering relation.
There appear to be two points of view:

1.  A special relation exists between taxonomic ranks. It would be
    transitive and antisymmetric.
2.  The relation is simply part_of. Part_of is transitive and
    antisymmetric.

  
Chris Mungall's response to this question was:

` 3. What about imposing an ordering among ranks and, if so, is part_of the appropriate relation?`

`so with any ontology you should ask "what are the instances". In this case, the instances are best considered`  
`to be terms/classes/categories rather than something tangible in nature. This takes us close to weird metaclass`  
`modeling territory.`

`but not to worry. I would say reserve part_of for "real" part_of relations, between objects and processes. I`  
`would just go with a custom relation for ranks. I don't have strong opinions on what you name it - above/below?`  
`more_ancestral_than?`

`Declare the relation transitive`

There is another property of the 'rank ordering' that should be noted.
The current TTO currently uses a rather limited number of taxonomic
ranks. However, if this ontology is intended to be shared across OBO
projects, it will need to incorporate additional taxonomic level terms.
For example, the NCBI taxnomy defines over 30 rank terms. As other
groups develop taxonomies they will want to add ranks that are used in
their systems. Furthermore, the system of ranks is open-ended, so any
particular group might need to add additional ranks in the future.
However, any one taxonomy will only use a subset of these terms, which
means that in most cases, the is_a relation between two taxa will
frequently correspond to more than one link up the rank taxonomy.
Another case where this situation comes up, even for a single taxonomy,
is an incertae sedis taxa. Thus a definition for the ordering relation
needs to work without depending on having every step in the rank chain
correspond to a taxonomic term in each tip to root path in the tree.

Resolving this issue may depend on the resolution of a second, closely
related issue that may have to be reopened for discussion.

## Modeling Taxa

Following the example of the OBO translation of the NCBI taxonomy, the
TTO models taxa as a hierarchy of classes, defined by an is_a relation
based on set theory. This means that classes, hence taxa terms are
represented as sets. The taxon as set model extends all the way down to
and including the species level.

However, an increasingly influential view among philosophers of biology
is that species should be not be seen as either classes (or natural
kinds), but as evolutionary units, and hence as individuals (e.g., Hull
1974, Ghiselin 1978). In this view, species are not sets of individual
organisms, rather there is a part_of relation between organisms and
their species. The particular part_of relation is commonly portrayed as
species (and other clades) being composed of lineages and lineages
consisting of related individual organisms.

This view can be extended to consider clades as individuals, since they,
like species are comprised of lineages. Individuals comprised of
lineages might be modeled as instances of the class 'portion of clade',
which might include species (the class of all individual species) as a
particular subclass because individual species are evolutionary units,
unlike larger clades.

Modeled this way, the TTO and taxon rank ontology might look as follows:

`                         TTO                                TaxonRank Ontology`

`                       is_a`  
` "portion of clade" <--------------  Cyprinidae   -------------------->  Family`  
`                                         ^             has_rank           ^`  
`                                         |                                |`  
`                                 part_of |                                |  "rank_order"`  
`                        is_a             |                                |`  
` "portion of clade" <-----------      Davario    -------------------->  Genus`  
`                                         ^             has_rank           ^`  
`                                         |                                |`  
`                                 part_of |                                |  "rank_order"`  
`                      is_a               |                                |`  
` "portion of clade" <------- Davario aequipinnatus ---------------->  Species`  
`                                                   has_rank`

Or even:

`      TTO                                       TaxonRank Ontology`

`                       is_a                        is_a`  
`  Cyprinidae   -------------------->  Family ------------------> "portion of clade"`  
`       ^                                 ^`  
`       |                                 |`  
`       | part_of                         |  "rank_order"`  
`       |                is_a             |`  
`    Davario    -------------------->   Genus ------------------> "portion of clade"`  
`       ^                                 ^         is_a`  
`       |                                 |`  
`       | part_of                         |  "rank_order"`  
`       |                   is_a          |`  
` Davario aequipinnatus ------------>  Species -----------------> "portion of clade"`

This approach also provides a natural bridge to the use of Phylogenetic
definitions, which more or less restrict taxonomic labels to
monophyletic clades. A more detailed description of this approach can be
found
<a href="Taxonomic_Rank_Ontology" class="wikilink" title="here">here</a>.

The major difficulties with such a model are potential conflicts with
the OBO ontologies focus on classes, rather than individuals.
