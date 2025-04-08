---
title: KB data integrity checks
permalink: wiki/KB_data_integrity_checks
layout: wiki
tags:
 - Informatics
 - Curation
 - Reasoning
---

This page documents data integrity checks that would be useful to
implement in a testing framework running against the Knowledgebase.

# Data

Wherever the integrity checks are formulated as a query (SPARQL wherever
possible), they use the RDF/OWL representation of the data in the
following version: [November 17,
2011](http://phenoscape.svn.sourceforge.net/viewvc/phenoscape/tags/data-2011-11-17/rdf%2Bowl/)

The most current version of the RDF/OWL is also in svn:
<http://phenoscape.svn.sourceforge.net/viewvc/phenoscape/trunk/data/rdf%2Bowl/>

# Integrity checks

## Obsolete terms used in phenotype annotations

## Check that there is no multiple inheritance within TTO

## Relational qualities should have related entity

## Non-relational qualities should not have related entity
