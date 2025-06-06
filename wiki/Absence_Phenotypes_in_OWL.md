---
title: Absence Phenotypes in OWL
permalink: wiki/Absence_Phenotypes_in_OWL
layout: wiki
tags:
 - Reasoning
redirect_from:
 - wiki/Absence
 - wiki/Discussion_about_the_Absence_of_Phenotypes_issue
 - wiki/Modeling_Absence_of_Phenotypes
---

Phenotypes describing the absence of a type of structure require
particular consideration for both semantic modeling and reasoning.

## Basic EQ modeling

We generally represent phenotypes as classes describing relationships
between an entity and a quality. The entity is usually an anatomical
structure, such as a **dorsal fin**, which is the *bearer_of* some
quality, such as an instance of **serrated**. The inverse of *bearer_of*
is *inheres_in*, so we can either describe the set of organisms with
this phenotype:

> *`has_part`*` some (`**`dorsal fin`**` and `*`bearer_of`*` some `**`serrated`**`)`

or describe this class of phenotypes (from the perspective of the
quality):

> **`serrated`**` and `*`inheres_in`*` some `**`dorsal fin`**

These expressions are not equivalent but describe different aspects of
the same data model.

## "Absent" quality

The PATO ontology of phenotypic qualities includes a commonly used
quality **absent**. However, using this term in the above EQ model is
problematic. For the entity **dorsal fin** and the quality **absent**,
we would end up with an expression such as:

> *`has_part`*` some (`**`dorsal fin`**` and `*`bearer_of`*` some `**`absent`**`)`

The obvious problem is that this asserts the existence of a **dorsal
fin**, needed to bear the instance of **absent**.

Additionally, reasoning with these classes produces unintuitive results.
An organism with no dorsal fin would be described as
*`has_part`*` some `**`dorsal fin`**` and `*`bearer_of`*` some `**`absent`**.
An organism with no fins at all would be in the class
*`has_part`*` some `**`fin`**` and `*`bearer_of`*` some `**`absent`**.
An OWL reasoner would correctly infer that the former is a subclass of
the latter, which is the opposite of what we really intend (organisms
without dorsal fins are a superset of the organisms without any fins).

## Using OWL class complements or cardinality

Instead of representing absence with a quality, we can describe it in
OWL using a class complement (logical negation):

> `not (`*`has_part`*` some `**`dorsal fin`**`)`

This results in reasoning that matches our expectations:
`not (`*`has_part`*` some `**`fin`**`)` is a subclass of
`not (`*`has_part`*` some `**`dorsal fin`**`)`. Also, we don't infer the
existence of a structure that is supposed to be absent. However, this
approach introduces two difficulties. First, we lose the ability to
directly describe the phenotypic quality (there is no instance of
"absence" to refer to; we are instead describing the organism or
structure). This can be problematic when the application otherwise
presents or queries for phenotypes as qualities. Second, complement
expressions are not available within the OWL EL profile. Reasoning with
such expressions requires a complete OWL DL reasoner, which is far less
scalable.

We could also use a cardinality expression:

> *`has_part`*` exactly 0 `**`dorsal fin`**

This is logically equivalent to the complement expression, and
cardinality expressions present the same difficulties just described.
Also, while cardinalities other than 0 can be used to express counts,
transitive properties such as *has_part* cannot be used in cardinality
expressions (except possibly in the special case of cardinality 0).

## "Lacks all parts of type" quality

The solution provided by PATO for the problems with the **absent**
quality is the "relational" quality **lacks all parts of type**.
Relational qualities in PATO are qualities that are further specified by
a relation to another class, for example **sensitivity** toward
**ultraviolet light**. So instead of describing an entity **dorsal fin**
which bears an **absent** quality, we should instead describe the entity
**body** which bears a quality **lacks all parts of type** toward
**dorsal fin**. At first glance, this approach seems to address all the
above issues:

- We can describe phenotypes from the quality perspective; **lacks all
  parts of type** is a subclass of **quality** and doesn't require use
  of a complement expression.
- The instance of **lacks all parts of type** *inheres_in* an instance
  of **body** (or other containing structure) rather than in a
  non-existent **dorsal fin**.

and...

- A **lacks all parts of type** toward **fin** should be a subclass of
  **lacks all parts of type** toward **dorsal fin**... but is it??

Defining an explicit OWL representation for **lacks all parts of type**
introduces some reasoning difficulties. To relate the quality to the
missing part, we might expect to use the standard existential
restriction:

> **`lacks all parts of type`**` and `*`inheres_in`*` some `**`body`**` and `*`towards`*` some `**`dorsal fin`**

However, we end up with the same backwards reasoning found with absent.
**`lacks all parts of type`**` `*`towards`*` some `**`fin`** is a
superclass of
**`lacks all parts of type`**` `*`towards`*` some `**`dorsal fin`**, the
opposite of what we intend. But an existential restriction on *towards*
clearly holds the wrong semantics anyway (and furthermore implies the
existence of the absent structure). The object of the towards relation
is the type **dorsal fin** itself, not some instance. To reference the
class directly we must use it in a value restriction, where we would
expect an instance:

> **`lacks all parts of type`**` and `*`inheres_in`*` some `**`body`**` and `*`towards`*` value `**`dorsal fin`**
