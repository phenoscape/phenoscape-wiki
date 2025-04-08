---
title: Entities with taxonomic context
permalink: wiki/Entities_with_taxonomic_context
layout: wiki
tags:
 - Ontology
 - Informatics
 - Curation
 - Reasoning
 - EQ Annotation
---

Our phenotype annotations currently involve linking a phenotype
composition to a taxon via an *exhibits* relation. However this model
has not provided an obvious way to employ taxon-specific homology
annotations to the anatomical entities being annotated. This page
describes an alternative representation of phenotype annotations which
may provide a solution for employing homology annotations as well as
anatomical relations which are taxon-specific.

## Phenotype annotations

### Old form

Our current phenotype annotation model has the form "a particular taxon
has some phenotype, consisting of some quality inhering in some
anatomical entity":

`Danio rerio `*`exhibits`*` sigmoid^`*`inheres_in`*`(vertebra 1)`

The phenotype is a post-composition with the following properties:

`sigmoid^`*`inheres_in`*`(vertebra 1) `*`is_a`*` sigmoid`  
`sigmoid^`*`inheres_in`*`(vertebra 1) `*`inheres_in`*` vertebra 1`

### New form

This annotation can be stated differently as "some anatomical entity, in
a particular taxon, has some quality":

`vertebra 1^`*`in_taxon`*`(Danio rerio) `*`has_quality`*` sigmoid`

The entity is a post-composition with the following properties:

`vertebra 1^`*`in_taxon`*`(Danio rerio) `*`is_a`*` vertebra 1`  
`vertebra 1^`*`in_taxon`*`(Danio rerio) `*`in_taxon`*` Danio rerio`

Taking into account the contents of the TAO and TTO ontologies, we can
infer useful statements such as:

`vertebra 1^`*`in_taxon`*`(Danio rerio) `*`is_a`*` vertebra 1^`*`in_taxon`*`(Cyprinidae)`  
`vertebra 1^`*`in_taxon`*`(Danio rerio) `*`is_a`*` bone`

## Taxonomically variable ontology relationships

Using these entity post-compositions, we can assert taxon-specific
anatomical relationships such as:

`vertebra 1^`*`in_taxon`*`(Cyprinidae) `*`part_of`*` Weberian apparatus`

Now if we search for phenotype annotations in which the subject entity
is part_of the Weberian apparatus, we will find the one about vertebra 1
of Danio rerio:

`vertebra 1^`*`in_taxon`*`(Danio rerio) `*`has_quality`*` sigmoid`

However, we would correctly not find an annotation about vertebra 1 in
Chanos chanos, which is not in Cyprinidae:

`vertebra 1^`*`in_taxon`*`(Chanos chanos) `*`has_quality`*` serrated`

Searching for phenotype annotations in which the subject entity is
vertebra 1 would return both statements.

## Homology annotations

Entity post-compositions provide a method to formulate and employ
homology statements:

`intercalarium^`*`in_taxon`*`(Otophysi) `*`homologous_to`*` neural arch 2^`*`in_taxon`*`(Teleostei)`

Given the following two phenotype annotations:

`intercalarium^`*`in_taxon`*`(Danio rerio) `*`has_quality`*` sigmoid`  
`neural arch 2^`*`in_taxon`*`(Chanos chanos) `*`has_quality`*` serrated`

We know that the subjects of these annotations are homologous because
these statements are implied:

`intercalarium^`*`in_taxon`*`(Danio rerio) `*`is_a`*` intercalarium^`*`in_taxon`*`(Otophysi)`  
`neural arch 2^`*`in_taxon`*`(Chanos chanos) `*`is_a`*` neural arch 2^`*`in_taxon`*`(Teleostei)`

## Impact on curation

Modeling the data in this way shouldn't have an effect on data
curators - the interface would be the same in Phenex. The data would be
modeled in this way on its way into OBD. So, there would be no need for
curators to create post-compositions of anatomy terms with taxa; they
would just choose the plain anatomy term to use in the phenotype. These
post-compositions are created behind the scenes. This scenario does open
up the possibility of using more relations than just
inheres_in/has_phenotype, however. We could, in the future, make the
relationship selectable, allowing curators to input relations between
anatomy terms in a more direct manner than using relational qualities.
For example, if there were a relation "fused_with" (not the relational
quality), the curator could just make the taxon-specific annotation:

`bone_x `*`fused_with`*` bone_y`
