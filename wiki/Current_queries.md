---
title: Current queries
permalink: wiki/Current_queries
layout: wiki
---

This page documents the queries implemented to retrieve data for the
Anatomy Web Services module of the Phenoscape project, which was
demonstrated at the SICB Workshop in Boston, MA in Jan 2009.

## Summary

Post compositions of Entities and Qualities are used to relate taxa and
phenotypes through the *exhibits* relation as shown in (1). <javascript>
Taxon *exhibits* *inheres_in*(Quality, Entity) -- (1) </javascript> In
addition, the OBD database also contains information relating post
composed phenotypes to both the Quality and the Entity by different
relations as shown in (2) and (3) respectively

<javascript> *inheres_in*(Quality, Entity) *is_a* Quality -- (2)
*inheres_in*(Quality, Entity) *inheres_in* Entity -- (3) </javascript>
Quality can be either a Value or an Attribute (beside other slims) and
is related to these by the *in_subset_of* relation as shown in (4)
<javascript> Quality *in_subset_of* Slim -- (4) </javascript>

Qualities and Anatomical entities are subclassed in the PATO and TAO
hierarchies respectively as shown in (5) and (6) <javascript> Value
*is_a* Attribute -- (5) Sub Anatomical Feature *is_a* Anatomical Feature
-- (6) </javascript>

The queries implemented for this iteration of the Phenoscape UI use the
following strategy to retrieve taxa and qualities associated with an
Anatomical Entity.

1.  Phenotypes containing the anatomical feature and the taxa exhibiting
    these phenotypes were extracted from the database using regular
    expression keyword matches. This was done with one query (Q1) that
    uses the relation in (1)
2.  Results from Q1 are parsed to extract the Anatomical Feature and the
    Quality that went into each Phenotype (again using regular
    expressions)
3.  The Quality extracted in the previous step is analyzed by running a
    query (Q2) on relation (4), to see if it is an attribute or value.
    If the Quality is a value, then a second query (Q3) is used to
    determine the attribute it is a value of. This query runs on the
    *is_a* relation in (5), and is invoked in sequence until an
    attribute higher in the quality branch is found
4.  The results from the previous step are used to group the qualities
    that an entity can take under specific attributes. Value qualities
    such as Distorted, Regular etc may be grouped under an attribute
    quality such as Shape
5.  In another direction, the taxa retrieved in Q1 are also collected
6.  Now, the anatomical features that are sub features of the search
    feature are collected. For example, if the search was for dorsal
    fins, now we retrieve all the sub features of dorsal fin such as
    dorsal fin lepidotrichium etc by querying (Q4) over the relation
    shown in (6) below
7.  For every sub anatomical feature retrieved by Q4, we repeat the
    previous steps

In summary, the relations (2) and (3) are not leveraged in this
strategy. The transitive relations between the Attribute and Value
Qualities in the PATO hierarchy and the Anatomical Features in the TAO
hierarchy (which are inferred by the OBD reasoner) are also not
utilized. An assortment of queries are executed over the database
backend and their results are fed into the JAVA methods implemented on
the client side, which is a very expensive process in terms of time.
Some data structures like lookup tables for Attributes and Values have
been implemented to minimize database connections and query executions,
however the whole retrieval process is still very time consuming

## Query details
