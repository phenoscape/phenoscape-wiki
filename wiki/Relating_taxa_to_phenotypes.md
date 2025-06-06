---
title: Relating taxa to phenotypes
permalink: wiki/Relating_taxa_to_phenotypes
layout: wiki
tags:
 - Reasoning
 - Ontology
 - EQ Annotation
---

In Phenoscape, we are annotating the phenotypes of species as described
in systematic literature. Because we are working within an ontological
framework, we require a well-defined relation to link a taxon to a
phenotype. This page describes the properties of, and issues related to,
our proposed relation, *exhibits*.

## Defining *exhibits*

### Proposed definition

A taxon X *exhibits* phenotype Y if phenotype Y has been observed in
some organism which is a member of taxon X.

### Discussion

In an ideal world, all phenotype annotations would be directly to some
organism specimen where the phenotype was observed. However, for various
reasons direct specimen annotation is not feasible in practice. So, we
create phenotype annotations for "leaf" taxa, species. As the given
definition suggests, *exhibits* statements do not preclude polymorphism
within the taxon. Some member organsims of that taxon may have one
phenotype while others may have another. For example:

- Species X *exhibits* "round dorsal fin"

is not in conflict with another annotation:

- Species X *exhibits* "pointed dorsal fin"

Both have been observed within members of this species. Furthermore,
phenotypic qualities within PATO cannot really be considered to be
alternatives to one another. For example:

- Species X *exhibits* "yellow dorsal fin"

would not be supposed an alternative to either of the previous two
phenotypes. The situation is no different between "round" and "pointed"
themselves.

## Implications

### Propagation

If a taxon X *exhibits* a phenotype, this should hold implications for
related taxa. Specifically, the parent taxon of X should be inferred to
also exhibit that phenotype. This is more easily understood when it is
recognized that member taxa do not stand in a subtype or subclass
relation to their parent taxa. It is instead purely a genealogical
relation. So when one asks, "What phenotypes does the genus *Danio*
exhibit?", the answer is "All the phenotypes exhibited by its member
species".

Put another way, the definition makes clear that the phenotype is
actually possessed by some organism or organisms which are members of
the annotated taxon. **The organism is also a member of every parent
taxon of that taxon, so those taxa also exhibit the phenotype.**

### Some vs. All

The *exhibits* relation has "some of" semantics. As described above, an
*exhibits* annotation tells us that some organism or organisms in that
taxon possess the phenotype. This works well for describing
characteristics of evolving entities such as taxa. We can only state
what we have seen. Since membership in a taxon is, ontologically,
decided only by genealogy and not by any defining characteristic, it is
always possible that a new or undiscovered member of a taxon may exhibit
some quality. Diagnostic characters may epistemologically suggest
membership in a taxon, but such characters are not the cause of
membership: genus-differentia definitions of taxa cannot be constructed.

These semantics are consistent whether we create annotations on leaf
taxa (species) or on higher taxa. Annotations to higher taxa are exactly
the same as those that might be inferred by a reasoner from annotations
to its member taxa. An annotation to a higher taxon tells us only that
some member of that taxon possesses the phenotype, but does not provide
knowledge that any particular member taxon possesses the phenotype. For
example, an annotation entered such as:

- Cyprinidae *exhibits* "notched caudal fin"

does not tell us whether its member taxon *Danio rerio* has a "notched
caudal fin". It might.

## Annotating ancestral or default conditions

It might be expected that one could annotate a phenotype for an order
(or any taxon), and thus "apply" that phenotype to all species within
that order. However, as explained above:

1.  Such an annotation does not generate any more knowledge than we put
    in. We know that some member(s) of the order exhibit the phenotype,
    but not which species or which families (member taxa of the order).
2.  Furthermore, we do not know whether this phenotype was the ancestral
    condition for members of that order, or evolved in only one
    specialized member lineage.

There are ways in which we can address these two situations. If we are
entering a phenotype which applies to every member of some higher taxon
(like an order), we should generate annotations at the level of
specificity which we desire. Concretely, if we "know" that every species
in some order has phenotype X, we should create *exhibits* annotations
for every species in the taxonomy belonging to that order for phenotype
X, attaching the appropriate evidence code (e.g. "evidence based on
everybody says so"). In this way we explicitly capture the facts we want
to rely on, with the weight of evidence (perhaps weak) we want to
provide. This does not preclude a convenient interface for "expanding" a
single taxonomic annotation to generate annotations for all its member
taxa when this is desired.

We cannot rely on logical inferences from ontological reasoning to know
the phenotype of the most recent common ancestor for a particular clade.
This requires evolutionary inferences from phylogenetic analysis.
However, we may want to add inferred annotations from such analyses to
our datastore. One possibility is to use a different annotation. Instead
of *exhibits*, one could also create statements such as "Taxon X
*ancestrally_exhibits* Phenotype Y". Such annotations could have
evidence codes related to the type of evolutionary analysis supporting
them. Like exhibits annotations, *ancestrally_exhibits* annotations
would unfortunately not provide information about current phenotypic
states of descendant taxa.

## Shortcomings and questions

- What are the criteria for which phenotypes are possessed by an
  organism? I.e. a missing fin could have been severed by a biologist.
  Can phenotypes which are the product of an organism's "developmental
  system" be distinguished from less interesting phenotypes such as
  severed fins? \[This is distinguishable for being unique to individual
  specimens and a phenotype for which no statement of homology can
  possibly be made
  --<a href="User%3ATjvision" class="wikilink" title="Tjvision">Tjvision</a>
  22:06, 9 February 2009 (EST)\]
- Considering only taxonomic *exhibits* statements, we don't know which
  phenotypes co-occur (or don't) within one individual organism.
  \[Unless multiple annotations are made to a single specimen
  --<a href="User%3ATjvision" class="wikilink" title="Tjvision">Tjvision</a>
  22:06, 9 February 2009 (EST)\]
- What are use-cases for the *ancestrally_exhibits* annotations?
