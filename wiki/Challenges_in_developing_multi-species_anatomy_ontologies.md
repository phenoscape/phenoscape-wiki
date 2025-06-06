---
title: Challenges in developing multi-species anatomy ontologies
permalink: wiki/Challenges_in_developing_multi-species_anatomy_ontologies
layout: wiki
tags:
 - Curation
 - Ontology
---

### Representing taxonomically variable part_of relationships for an entity

See related [TAO tracker
request](http://sourceforge.net/tracker/index.php?func=detail&aid=2137065&group_id=76834&atid=994764)

An entity may have taxonomically variable part_of relationships. For
example, vertebra 1 may or may not be part_of the Weberian apparatus.
(The Weberian apparatus is an anatomical cluster consisting of the first
four vertebrae (additional vertebra in some taxa) and associated
structures which connect the gas bladder to the inner ear. It is
diagnostic of the Otophysi (Cypriniformes, Characiformes, Gymnotiformes,
Siluriformes). Some species have vertebra 5 and/or 6 as part of Weberian
apparatus). How to represent taxonomically variable part_of information
in a multi-species ontology?

#### 1. Multiple vertebra 1 terms as children of “vertebra”

`precaudal vertebra`  
`     <--is_a vertebra 1`  
`     <--is_a vertebra 1 part of Weberian apparatus`

The term “vertebra 1 part of Weberian apparatus” has relationship
part_of: Weberian apparatus

\- Requires curator to choose the taxonomically correct term at time of
annotation

\- Search on “vertebra 1” will bring back results for all ostariophysans
only if homologous_to statement is used:

"vertebra 1" in Anotophysi homologous_to "vertebra 1 part of Weberian
apparatus in Otophysi

#### 2. Vertebra 1 term with child “vertebra 1 part_of Weberian apparatus”

`precaudal vertebra`  
`     <-- vertebra 1`  
`           <-- vertebra 1 part_of Weberian apparatus`

\- Also requires curator to choose the taxonomically correct term at
time of annotation

\- Search on "vertebra 1 will bring back results for all ostariophysans,
regardless of whether homologous_to statement is made

#### 3. part_of variability as a phenotype statement using entity post-composition

`E: vertebra 5^part_of Weberian apparatus; Q: present; Taxon: Otophysi`

### Representing serial homologues

neural arch 2 and intercalarium are children of neural arch
