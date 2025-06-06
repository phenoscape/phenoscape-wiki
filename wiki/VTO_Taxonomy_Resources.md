---
title: VTO Taxonomy Resources
permalink: wiki/VTO_Taxonomy_Resources
layout: wiki
tags:
 - Taxonomy
 - Ontology
---

# Resources for Constructing a Vertebrate Taxonomy Ontology

Note: The material on this section has been moved and incorporated into
the main
<a href="Ontologies" class="wikilink" title="Ontologies">Ontologies</a>
page.

# Tools

## VTO Construction Tool

This tool uses a script to construct a taxonomic ontology by specifying
a starting taxonomy, then modifying it by removing branches and splicing
corresponding pieces of alternate taxonomies (e.g., start with the NCBI
taxonomy and replace the teleost part of the tree with the tree from the
TTO). It also allows taxonomic synonyms to be extracted from taxonomies
or name lists and attached to terms in the taxonomy. Currently, the tool
generates a taxonomy in the OBO format, though support for an
individual-based OWL format is in progress.

The tool source is available at
[GitHub](https://github.com/NESCent/Taxonomy-Ontology-Tool).

## TTOUpdate

This tool is used to merge an existing TTO with a Catalog of Fishes
update file, which will consist either of a single Microsoft Access
database or three Excel (2003) files (one each for lineages, genera, and
species). Does not use CSV or tab-delimited text files as the free-text
comments, which include extractable synonyms, contain commas, tabs and
line breaks, so rendering the common text formats unusable. TTO update
includes libraries for reading the pre-2007 Excel formats which properly
handle the various breaking characters.
