---
title: Needs Analysis Workshop/Semantics Breakout
permalink: wiki/Needs_Analysis_Workshop/Semantics_Breakout
layout: wiki
tags:
 - Needs Analysis Workshop
---

**Participating**: Toby Kellogg, Hilmar Lapp, John Lundberg, Austin
Mast, Peter Midford, David Stern

  
----

Hilmar – David’s talk – changes characterized – fell into categories
Database is a knowledge base -

DS - What is ontology for change – words to describe change PM –
develops from? DS – comparison PM – How to describe change of position ?

H – Q formalism - entity, quality – extend to include relational
qualities

e.g. red dot, posterior to, midgut (sp. 1)  
red dot, anterior to, midgut (sp. 2)

posterior and anterior – come from PATO – know that this indicates
position

JL - does this assume that entities are stable during transformation
Does this confuse aspects of the process?

H – just states relative position

JL – OK if htat’s all you want

PM – might be able to infer which moved relative to a third structure

HL – might get data on a mutant that indicate that the red dot changed
position

DS – suppose species diff is posterior/anterior, mutant moves half way –
Could you retrieve direction of movement and then retrieve it

HL – key question – what do we need to be able to infer –

DS – if you map on phylogeny infer that red dot moves anterior, mutant
moves red dot

AM – would it be less ambiguous if red dot is relative to axis

DS – if each entity can have multiple quality descriptors, can describe
multiple phenomena

JL – if things are in different positions, need a standard position.
Hard to interpret if you are just going through the literature

HL – need to be very careful of hypothesizing cause

JL – also interpreting the literature –

DS – similar to people describing morphometric of wing vs. outline

PM – would be nice to have a representation that let you see data in two
different ways

DS – would it be better to make database to describe phenotype of each
species

JL – more what we’re doing, descriptions of species, then building up

PM – if you have developmental data, better to describe in terms of own
development

DS – discover mutations based on distinction between two things – white
cow vs. black cow – wt vs. mutant

TK – a different way to represent data

DS – not by mutation but rather by alleles – describe data in terms of
alleles, not mutation

PM – need the alleles – do you need a step matrix to indicate if you
need

JL – lots of different colored cows, multiple species, allele
information – if you are interested in looking in evolutionary context,
get a tree for cows and map color on tree. You would reconstruct steps
according to what you know about mutation

PM – not necessarily a tree, could be a lattice

JL – this is what we’re trying to do with ZFIN – mutants of zebrafish
vs. morphological variation in species of fish

PM – not trying to infer anything, trying to develop hypotheses

DS – would be interesting if you could include QTL data –

TK – so if db were constructed with alleles as entities, then different
states of QTL would be the entities

DS – probably easier to ignore the QTL literature for now and wait until
people get the genes

DS – how to integrate with fish db

HL – would be useful, but best to use the same formalism

DS – can you make this in FileMaker and export to your system?

HL – subject needs to come from an ontology, predicate comes from PATO,
relational quality needs to be formalized

DS – if things are not in ontologies now?

PM – ask them to be added

DS – is your work going to be integrated with NCBI? Hoping to have
direct links in that direction

HL – link to NCBI would come through ZFIN; are describing mutant
phenotypes of which they know the genetic basis

JL – for most of the species that we are looking at, there is no
information on the genetic basis – expect that genes will be
zebrafish-like

HL – NCBI is expanding to recording phenotypes – have a new database
related to clinical studies database, primarily driven through medical
applications. One question I was wondering abou in our effort to
annotate phenotypes – what is level of completeness for annotations.
Some property may be recorded of red dot, then find a specimen that
differs in some way – get disconnected phenotypes

TK – this is inherent in the data

JL – can’t get a description complete enough to relate to everything to
everything – if you have the luxury of being thorough you could go back
and score everything – we won’t have the luxury – will be holes in the
data

DS – in this example, cells differ in ability to process salt – would
have a separate setoff qualities – only way to deal with it need to have
real taxonomic experts dealing with each group –

JL – some things are very straightforward like numbers of fingers and
toes, other things such as relative sizes of parts are harder

DS – flybase doesn’t have all information translated into ontologies

JL – trying to seize on all knowledge built up in evolutionary
morphology

DS – is there an intermediate state where sentence can be lifted from
papers

Very detailed ontologies may not be necessary – the people using these
may want to look at the organisms themselves

HL – how would biologists want to take advantage of this in a way that
does take advantage of the semantics

DS – go to flybase – skip the ontology, scan for key words, go and read
the paper

HL – look at your own database, what kinds of queries do you use?

DS – need to have all data in one place in one format –

PM – if you are looking for a single word, may be able to scan the text
– if you want to look for a term and its relation to something else,
ontology might be useful. May want to give me everything in which dot
position changes

HL – relative position – can go higher and higher level

DS – are we finding only a subset of genes that coule affect this trait?
Would like to find a set of genes that could affect a trait. What are
all genes that affect trichomes?

TK – many people just want a list

JL – if the database becomes fairly dense, could imagine someone using
it to help reconstruct a phylogeny – depends on how dense the product is

TK – possibly the ability to manipulate the data is ahead of the
availability of data

JL – as taxonomic ontology develops and as ontology becomes richer and
richer then become more useful

HL – this project could evolve in to the next BLAST as a way of
analyzing phenotypes, similar to that of analyzing sequences. At some
point might use images and their annotation as the basis of a BLAST
search

AM – was thinking more about annotations to images – sifting through EQ
statements. Would want to search across data sources, not just image
annotations

HL – is it interesting to search for similar phenotypes – is there
meaning in doing that?

AM – would be interesting if you could query for variation in
phenotypes; e.g. want to identify a branch, describe the hairs,
trichomes; leaf broad vs. terate – are there other instances of genera
in Australia that have both broad and terate leaves -
