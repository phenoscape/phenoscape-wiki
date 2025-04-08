---
title: TTOUpdate tool
permalink: wiki/TTOUpdate_tool
layout: wiki
tags:
 - Taxonomy
 - Software
 - Phenoscape I
---

## Overview 

TTOUpdate is a tool used for merging updated exports from the [Catalog
of
Fishes](http://researcharchive.calacademy.org/research/Ichthyology/catalog/fishcatmain.asp).
The exports are merged into a preexisting copy of the Teleost Taxonomy
Ontology (cite) in OBO format.

The source code for TTOUpdate is available [within the Phenoscape
repository on
Sourceforge](http://sourceforge.net/p/phenoscape/code/HEAD/tree/trunk/tools/TTOUpdate/)
under the MIT license.

## Input Files

The export from the Catalog of Fishes (CoF) consists of 3 Excel 2003
files, consisting of species, genera, and higher level lineages
respectively. Because the free text comments included in the CoF include
comma, tab, and newline characters, csv and tab delimited text formats
could not be used. The tool can also incorporate synonyms from multiple
sources, including ITIS.

## Output

The output of TTOUpdate is an updated copy of the TTO in OBO (1.2)
format.
