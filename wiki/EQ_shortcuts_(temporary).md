---
title: EQ shortcuts (temporary)
permalink: wiki/EQ_shortcuts_(temporary)
layout: wiki
tags:
 - Curation
 - EQ Annotation
---

Here are temporary curation shortcuts for creating particular kinds of
phenotypes. These can be used until better EQ entry interfaces are
available in Phenex. The KB data loader will watch for and correctly
interpret each of these.

## Complementary phenotypes ("negation")

Example: "opercle, not round". Create a postcomposition for the quality,
choosing a meaningful genus term and using the "not" relation.

- E: opercle
- Q: shape^not(round)

## Comparative phenotypes (one structure relative to another)

Example: "supraorbital increased in size relative to frontal". Put the
compared to structure in the related entity column. Choose one of the
"increased/decreased X" qualities. While these qualities technically
compare to "normal", the data loader will replace them with the correct
quality.

- E: supraorbital
- Q: increased size
- RE: frontal

## Locally relative phenotypes

Example: "opercle size: small, medium, or large". Choose the quality
being compared, and place a number in the Count column indicating the
proper sort order (1 \< 2 \< 3). For "small":

- E: opercle
- Q: size
- Count: 1
