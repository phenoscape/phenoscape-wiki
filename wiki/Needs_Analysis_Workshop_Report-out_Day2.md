---
title: Needs Analysis Workshop/Report-out Day2
permalink: wiki/Needs_Analysis_Workshop/Report-out_Day2
layout: wiki
tags:
 - Needs Analysis Workshop
---

### Phylogenies: Report-out (Paula Mabee)

- ability to choose from the phylogenies in the database
  - even with the possibility of constructing a consensus tree
  - ability to move branches around
  - choose a subset (pruned phylogeny)
- map character changes onto the phylogeny
  - choose a feature of interest, e.g. by entity
  - issues of visualizing many characters on a branch
- link to genes
  - e.g. show genes with elevated expression
  - need to be careful about showing statistics - may be misused or of
    generating hypotheses for user (they should think for themselves)
- BLAST-like similarity search for how a trait (or trait change) maps
  across a tree
  - for example, a user has discovered elevated expression of a gene in
    certain branches of the tree; are there phenotypes that are similar
    to this distribution?
- Questions that this might be used for
  - Evolvability
  - Constraints
  - Parallel evolution

### Phenotype correlation (Todd Vision): Report-out

<figure>
<img src="Day2-correlation2.whiteboard.JPG" title="Whiteboard examples"
width="384" />
<figcaption>Whiteboard examples</figcaption>
</figure>

- matrix showing numerical summaries
- find cloud of similar annotations
  - traits vs traits, traits vs genes, genes vs genes
  - cells would be number of branches on which the two traits change in
    common (traits vs traits), or number of mutants they have in common
    (traits vs traits, and traits vs genes), or number of traits in
    common (genes vs genes)
  - problem of whether to use entity alone, entity and attribute
    (character), or EQ (character state)
  - problem of opening a can of worms by offering too detailed of an
    analysis, especially if it involves ancestral state reconstruction
    using phylogenies
  - e.g., is limblessless associated with elongation
- tree view
  - highlight terminal taxa or phylogenies for bringing up a matrix for
- body-plan view
  - highlight different areas and ask for traits affecting all of those
  - highlight different areas and then map the corresponding and
    correlated traits onto a tree

### Semantics: Report-out

- most queries aren't complex, and often simply want to have a list
  (e.g., genes, phenotypes)
  - for this, complex semantics may not be needed
  - shallower ontologies, or higher-level (more general) terms may
    largely suffice
- searching or analyzing phenotypes by similarity would require more
  rigorous or deep semantics
- too fine grained ontologies may be problematic for annotation
- allelic links:
  - emerging dataset of genetic mutations that are experimentally proven
    to have caused evolutionary change (D. Stern); experiments that
    allow strong hypotheses for polarity of gene change
  - directionality of allelic changes may be important
  - may need an evolves-from (develops-from?) relationship
  - restrict some queries to where information (e.g. gene expression) is
    available for \>50% of the taxa
  - Visualizations: phylogenies, body maps, time series, geography

### Discussion

<figure>
<img src="Day2-dataintegration.whiteboard.JPG"
title="Data interrelationships" width="384" />
<figcaption>Data interrelationships</figcaption>
</figure>

- Other data types or dimensions we haven't looked at
  - Time: e.g., developmental time-series
  - Geography
- Abilities to restrict traits by
  - high-level character modules
  - gene
  - GO
  - location
  - developmental stage
  - availability of sufficient data
- Discovery of data holes
