---
title: ComparativeAnalysis
permalink: wiki/ComparativeAnalysis
layout: wiki
---

This is part of the SCATE project. For more background on SCATE and its
predecessors, see the
<a href="Main_Page" class="wikilink" title="Main Page">Main Page</a>.

## Phylogenetic Comparative Analyses using Ontologies

The current project of the Phenoscape team is Enabling
Machine-actionable **S**emantics for **C**omparative **A**nalysis of
**T**rait **E**volution (SCATE).

A major goal of the SCATE project is to leverage the power of ontologies
and the Phenoscape Knowledgebase to assist in evolutionary analyses of
trait evolution. For example, researchers may wish to estimate
phylogenies from phenotypic data, reconstruct ancestral states, or
estimate correlations between phenotypes. Borrowing from molecular
sequence data, the methods used for conducting such analyses typically
make a series of assumptions that are very poorly suited for phenotypic
data. For example, a common assumption is that every character in a
character matrix is independent of each other. Phenotypic characters
regularly violate this principle. By leveraging the information in
phenotypic ontologies, we can correctly model character evolution by
accounting for the dependencies of structures among each other.
Furthermore, metrics such as semantic similarity can provide useful data
that can be integrated into many steps in a phylogenetic comparative
analysis.

### Structured Markov Models

Ontologies provide knowledge of dependencies among traits. For example,
the *humerus* is a bone that is *part of* the *forelimb*. Thus, the
presence of a *humerus* depends on the presence of a *forelimb*.
Treating these as independent characters can result in, for example,
ancestral reconstructions in which an organism has a humerus, but lacks
a forelimb. Such dependencies can be built into how we model traits by
making use of structured markov models [(Tarasov,
2018)](https://academic.oup.com/sysbio/article/68/5/698/5298740). By
structuring the dependencies among traits (as described by [Tarasov,
2018](https://academic.oup.com/sysbio/article/68/5/698/5298740)), we can
reconstruct not only individual traits, but entire ancestral anatomies
in a logically consistent framework. We have developed a stochastic
mapping pipeline called *PARAMO* [(Tarasov et al.
2019)](https://academic.oup.com/isd/article/3/6/1/5584145) that allows
users to reconstruct ancestral anatomies, seamlessly moving between
levels of anatomical hierarchy to query the phenome and ask questions
about evolutionary rates, ancestral states, and character evolution.

### Hidden State Models & Gene Regulatory Networks

In addition to modeling the dependencies of characters on each other,
proper modeling of dependent phenotypic characters requires inclusion of
*hidden states* ([Tarasov,
2018](https://academic.oup.com/sysbio/article/68/5/698/5298740),
[2019](https://academic.oup.com/sysbio/advance-article/doi/10.1093/sysbio/syz050/5541792)),
that is a character state in which the observable phenotype corresponds
to different genetic states. Hidden states add the possibility of
incorporating more knowledge regarding the evo-devo of traits and
account for evolution of novel phenotypic traits.

### Character Construction

Character construction is the first step of any comparative analysis,
and involves categorizing different free-text semantic descriptions
(e.g. *pectoral fin curved*, *pectoral fin round*, *pectoral fin
absent*, *pectoral fin elongate*, *pectoral fin circular*). Some of
these phenotypes may be different ways of describing the same phenotypic
state, while others may represent mutually exclusive states. This step
of character construction has traditionally relied on expert opinion and
reasoning. However, with phenotypic ontologies, such information can be
automated to allow machine-reasoning to accomplish similar ends, while
improving reproducibility. Furthermore, the distinction between
character and character state disappears when using properly structured
and hidden state models [(Tarasov,
2018)](https://academic.oup.com/sysbio/article/68/5/698/5298740). We are
exploring how this principle can be leveraged in character construction
together with semantic similarity (see below) to construct
"well-behaved" character codings in phylogenetic analysis.

### Evolutionary Enrichment Analyses

Phylogenetic analysis allows researchers to estimate the evolutionary
history of phenotypic evolution. As with gene ontologies, we can ask
question such as which branches and at which time periods in
evolutionary history has there been a particularly rapid rate of change.
Ontologies allow to not only ask which characters are enriched on a
given branch, but also which concepts are enriched. For example, are
features associated with the fin-to-limb developmental transition
particularly evolvable during the Devonian? Does a suite of traits
related to a specific gene regulatory network demonstrate concerted
evolution across the phylogeny?

### Semantic Similarity

Semantic similarity metrics measure concept similarity. We are working
to integrate semantic similarity metrics into phylogenetic comparative
models, as these contain information that allows users to partition,
cluster and amalgamate different characters and character states to make
sense of evolutionary patterns.
