---
title: Reasoning over homology statements
permalink: wiki/Reasoning_over_homology_statements
layout: wiki
tags:
 - Homology
 - Reasoning
 - Ontology
---

This document provides a collection of inference rules for homology
relations. The emphasis is on implementation in OBD, although the rules
can be used in other inference systems.

The core homologous_to relation is introduced together with its relation
characteristics. This relation is defined in terms of the
derived_by_descent_from relation and its inverse.

## Introduction

### Problem

Phenoscape is curating homology relationships between anatomical
entities across species. It is imperative that the semantics of the
homology relation is specified, to ensure annotation consistency and to
allow for reasoning.

Use cases:

1.  Searching for phenotypes or genes by anatomy term also retrieves
    qualities inhering in anatomical structures homologous (or serially
    homologous) to the query term, or homologous to any subclass of the
    query term.
2.  Searching for phenotypes or genes by an anatomy term that, by direct
    assertion or inference, is a part of an anatomical structure that is
    asserted or inferred to be homologous to another anatomical
    structure, also retrieves qualities inhering in the homologous
    structure or any subclasses or parts of it.
    - As an example, a user is looking for candidate genes associated
      with the radials (the anatomical query term) of the pectoral fins
      of fishes. Radials are part_of the pectoral fins of fishes, which
      are homologous as forelimbs to the anterior limbs of amphibians
      and arms of humans – for which there are known genes. In this case
      the parts are not homologous (i.e. the bones inside the pectoral
      fin of Danio are not considered homologues of the bones inside the
      forelimb of amphibians or humans), but the limbs unquestionably
      are homologous – as forelimbs.
3.  Searching for phenotypes or genes by an anatomy term in one taxon
    that is asserted (or inferred) not to be homologous to the same term
    in another taxon will not retrieve taxa that descend from a taxon in
    which the anatomical query structure is non-homologous. An anatomy
    term can be inferred as non-homologous if it is a part or a subclass
    of a term asserted (or inferred) as non-homologous.
4.  Searching for phenotypes or genes by anatomical superstructure (or
    anatomical complex, such as Weberian apparatus) retrieves qualities
    inhering in subclasses or parts of the anatomical query structure
    only for those taxa for which these subclass and parthood relations
    hold.
5.  Searching for taxa annotated with qualities inhering in an
    anatomical superstructure (or anatomical complex) retrieves only
    those taxa for which the annotated anatomical structure is indeed a
    subclass or part of the query structure.

### Outline

The background section covers key ontology concepts, in particular those
of relevance to homology reasoning, such as the distinction between
generic classes and mereological sums. A section describing the logical
characteristics of relations follows.

The main part of this document presents the core relations intended to
be used in phenoscape curation and reasoning. The core relation is the
pairwise homologous_to, a strict binary 1:1 homology relation that can
be used to specify anatomical entities related by common descent.

I then describe the characteristics of these relations. The emphasis is
on the syntax and semantics of OBD, although other ontology information
systems or reasoners may be used.

The next section of the document explores ternary (3-argument)
relations, and their formalization in terms of a derived_by_descent_from
relation. I explore ways of representing 3-ary relations in OBD on
ontology formalisms, including modeling as instances or classes.
Modeling in this way is shown to have strong correspondences with both
the HOG and MRCA approaches.

### Background

#### Classes and Instances

The distinction between the classes such as "finger" and "left hand
finger 1" and individual instances of (e.g. my left hand finger 1) is
crucial. Classes are organized in a subsumption (isa) hierarchy.

When making statements about classes, the implications for instances
must be explicit.

#### Named classes and class expressions

A class is essentially a set of instances. Classes can be named (e.g.
pre-composed in the ontology) or class expressions (e.g. post-composed).

OBD uses a special ID syntax for class expressions, allowing them to be
treated on an almost equal footing to named classes. When describing the
basic axioms, we use the OBD ID syntax to denote class expressions (as
is used through the phenoscape documentation).

The most common type of class expression used in the context of homology
relations is a taxon-restricted anatomical entity class. For readability
I will generally write these as:

` `<taxon label>` `<anatomical entity label>

These could also be written as an ID expression

` `<anatomical entity id>`^in_taxon(`<taxon id>`)`

For example:

` cyprinidae vertebra 1 <--> TAO:nnnn^in_taxon(TTO:nnnn)`

### Mereological Sums

The distinction between generic classes such as "vertebra" and
collection classes such as "vertebral column" is crucial.

1.  finger 1 is a subclass of finger
2.  every finger 1 is an instance of a finger
3.  every finger 1 is part of a collection of fingers on a hand

The FMA uses the "Set of <X>" terminology, but this is confusing because
classes can already be equated with sets. We use "collection of" here,
but we frequently substitute a more convenient synonym. E.g. maximal
collection of vertebrae = vertebral column.

For convenience we sometimes use the term "msum" as a functor in a class
expression denoting a mereologic sum. So "msum(v1...vn)" denotes a class
representing the mereological sum of all vertebrae in an organism.
"msum(finger2,finger3)\[hand\]" denotes the mereological sum of fingers
on one hand.

We assume that in general all required mereological sums will be named
classes in the ontology. This is already standard practice in TAO.
Strictly speaking the axioms defining these are outside the scope of
this document since they fall within the purview of the AO. However,
more will be said of this in the appendix.

## Classification and characteristics of relations

I now present some of the characteristics and means of classification of
relations, with an emphasis on the expressive capabilites of OBD.

### Binary vs ternary relations

Relations can be classified according to how many arguments they take.
Typically relations are binary, but ternary relations may be required.

Homology relations are typically expressed as 3-ary (ternary) relations,
read as "A is homologous to B as a C". For example:

| mammalian forelimb | avian wing           | forelimb  | TRUE  |
|--------------------|----------------------|-----------|-------|
| mammalian forelimb | teleost pectoral fin | appendage | TRUE  |
| avian wing         | bat wing             | wing      | FALSE |
| avian wing         | bat wing             | forelimb  | TRUE  |

Unfortunately most ontology information systems do not allow for direct
representation of relations with arity greater than 2.

For now I assume the asserted statements are binary, and that the 3rd
argument is unstated. I return to the subject of n-ary relations later
in this paper.

### Axes of classification

There needs to be multiple homology relations, not just one. These
relations can be classified along multiple (not necessarily independent)
axes:

- 1:1 vs 1:many vs many:many
- inter-species vs intra species
- orthology vs paralogy
- characters and character states: anatomical entities, proteins, DNA
- deep vs "superficial"

Some might include historical homology vs analogy as an additional axis,
but here we take the term "homology" to strictly imply common descent.

The focus of this document is anatomical entities as character states.
However, we do not want to reinvent the wheel for sequences, and where
applicable the same abstractions can be used. This is covered more in
the more detailed formalization.

We can derive a full relational lattice by materializing all valid
non-redundant combinations of these relation facets. A full exploration
of the full cross-product is outside the scope of this document. Instead
we select a subset relevant to current Phenoscape use cases. In the
future it would be useful to explore other relations in the lattice,
particularly with a view to unifying sequence-level and structure-level
homology in a knowledge base.

### Homology Relations Characteristics

We can describe the properties of various relations according to the
following relation characteristics:

- class or instance level
- relation hierarchy
- symmetry
- transitivity
- homeomorphicity
- cardinality constraints
- relation chains

Note that many of these are only well-defined for binary relations.

### Class or instance level

In the current implementation of OBD, there is no distinction between
class and instance level relations - relations are treated as predicates
with semantics supplied on a case by case basis.

In order to improve compatibility with OWL, and to make the semantics of
OBD knowledgebases clearer, the following changes will be introduced.

- Relations will be explicitly declared to be class or instance level
- The semantics will be much clearer

See appendix for more details

If a relation R is class level, then a statement

`X R Y`

Is treated as a binary predicate connecting two classes. There are no
default reasoning rules here, but rules for R can be introduced by the
KB manager.

If a relation R is instance level, then a statement

`X R Y`

Is always quantified. The options are:

1.  all X R some Y
2.  all X R only Y
3.  some X R some Y

This quantification is always explicit in OBD (although in the past this
has not been used).

### Homology Relation Hierarchy

Given a lattic of relations in a relation hierarchy, we can infer more
generic statements from more specific ones.

OBD implements the generic rules:

` R1 is_a R2`  
` all X R1 some Y`  
` ==>`  
` all X R2 some Y`

(instance level relations)

` R1 is_a R2`  
` X R1 Y`  
` ==>`  
` X R2 Y`

(class level relations)

note that obo syntax is followed and the label "is_a" is used for the
subrelation_of relation.

### Symmetric Relations

OBD implements the generic rule:

` symmetric R`  
` class_level R`  
` X R Y`  
` ==>`  
` Y R X`

(not implemented as yet, but could be added easily)

### Transitive Relations

OBD implements the generic rule:

` transitive R`  
` X R Y`  
` Y R Z`  
` ==>`  
` X R Z`

(class level)

` transitive R`  
` all X R some Y`  
` all Y R some Z`  
` ==>`  
` all X R some Z`

For example:

` human limb homologous_to mouse limb`  
` mouse limb homologous_to teleost fin`  
` ==>`  
` human limb homologous_to teleost fin`

### Propagation over isa

OBD implements the generic rules:

` W is_a X`  
` all X R some Y`  
` Y is_a Z`  
` ==>`  
` all W R some Z`

(note that is_a is reflexive, so effectively the first or last is_a is
optional)

### Cardinality

1:1 homology relations are only 1:1 within taxa.

We can express this as:

` A^in_taxon(T) 1:1 B^in_taxon(U)`  
` ==>`  
` NOT exists C : [`  
`   A^in_taxon(T) 1:1 C^in_taxon(U)`  
`   AND`  
`   C != B`  
` ]`

Note that this is not a horn rule, as the head of the clause is negated.
However, it can be expressed as a constraint using horn logic. At the
moment, OBD does not have a generic mechanism for such constraints, but
the constraint can be expressed as a SQL query and executed on demand.
In future the OBD reasoner will have an option for automatically
checking all specified constraints.

### Relation Chains

`R <- R1 o R2`  
`X R1 Y`  
`Y R2 Z`  
`==>`  
`X R Z`

`R <- R1 o R2`  
`all X R1 some Y`  
`all Y R2 some Z`  
`==>`  
`all X R some Z`

## Core Asserted Homology Relations

The core relation that a phenoscape curator will be using in homology
assertions is the homologous_to relation.

I also consider the serially_homologous_to relation, but more research
is required as to if and when this relation would be asserted.

There are a number of support relations that are used for inference and
querying. The key relation here is the evolutionary relation
derived_by_descent_from. Even though we may never explicitly assert
information about ancestors, this relation turns out to be key for
formalization and reasoning.

#### homologous_to

Characteristics:

- class-level
- transitive
- symmetric

Examples:

| human limb              | mouse limb              |
|-------------------------|-------------------------|
| human hand digit        | mouse hand digit        |
| human hand digit 1      | mouse hand digit 1      |
| human left hand digit 1 | mouse left hand digit 1 |
| mammalian limb          | teleost fin             |
| tetrapod frontal bone   | teleost parietal bone   |

This is a 1:1 relation, which means that an anatomical entity class in
one species cannot be related to two different classes in two different
species.

See further on in this document for discussion of the homologous-as
argument. For now we assume this is present but unstated.

Note that as a class level relation, this does not display propagation
over/under is_a. This is desirable consider if we used propagation to
infer:

- human hand digit 1 homologous_to human hand digit
- human hand digit 2 homologous_to human hand digit

because of the symmetry property we would infer:

- human hand digit homologous_to human hand digit 1
- human hand digit homologous_to human hand digit 2

this already violates the 1:1 property, and consider the addition of
transitivity:

- human hand digit 1 homologous_to human hand digit 2

So the lack of such propagation is desirable. But some kind of
propagation is desirable. I return to this issue later on, with the
descendant relations

Note in the examples above I include homology statements at different
levels of specificity. This is possible, and does not create any
incorrect inferences under the semantics specified here.

#### serially_homologous_to

TODO

Examples:

| mouse vertebra 1   | mouse vertebra 2   |
|--------------------|--------------------|
| human hand digit 1 | human hand digit 2 |
| human hand digit 1 | human foot digit 1 |
| human hand digit 1 | human foot digit 2 |

This is not a 1:1 relation. This relation is also symmetric and
transitive.

### deeply_homologous_to

Marcotte et al

eye

## Recording provenance on asserted statements

Provenance is vital for homology assertions. In OBD these would be
created as standard annotations using the built-in OBD reification
mechanism. We write this as:

` A homologous_to B [S1]`  
` S1 has_source `[`PMID:12345`](PMID:12345)

This is trivially convertible to RDF, with subject, predicate and object
triples generated for S1.

## Negation

` NOT[A homologous_to B]`

### Conflict and contradiction

TODO

## Homology and descent

Thus far we have been treating homology relations as binary. Many
treatments of homology include a 3rd "homologous-as" argument.

In order to formalize this we need to introduce a
derived_by_descent_from relation. Later on in this document we attempt
to fully define this relation, in terms of genetic specification.
However, it is unlikely this definition will need to be used in the
short term, so for now I present a high-level treatment, and state the
characteristics of this relation.

### Derived by descent from

This relation has the following characteristics:

- instance-level
- transitive
- inverse_of: has_derived_by_descendant
- reflexive
- anti-symmetric

This relation obeys the "straight-line" rule:

` a derived_by_descent_from b, a derived_by_descent_from c`  
` ==> b=c or b derived_by_descent_from c or c derived_by_descent_from b`

This can be encoded in OBD as a constraint.

This relation holds between anatomical entity instances (for example, my
left hand and my grandfather's left hand). Usually we would not make
statements about instances, but instead would generalize to the class
level (e.g. all human hand derived_by_descent_from some ancestral
primate hand).

A is derived_by_descent_from B if A is encoded in a genome GA that is
inherited from a genome GB, and B is encoded by GB. This formalization
is explored in more detail later on.

### Homology as descent

We can provide a definition of the binary homology relation:

` A homologous_to B`  
` <==>`  
` all A derived_by_descent_from some (has_derived_by_descendant some B)`  
` all B derived_by_descent_from some (has_derived_by_descendant some A)`

With OBD we can actually make a stronger rule:

` A homologous_to B`  
` <==>`  
` all A derived_by_descent_from some anc(A,B)`

Here anc(A,B) is just shorthand for the ID expression

` entity^has_derived_by_descendant(A)^has_derived_by_descendant(B)`

We use anc(A,B) for convenience in this document, but in OBD it would be
stored as the ID expression, which would automatically entail:

` all anc(A,B) has_derived_by_descendant some B`  
` all anc(A,B) has_derived_by_descendant some A`

(Note this feature of the OBD reasoner is inexpressible in many rule
systems)

### shares_ancestor_with

We define a new relation shares_ancestor_with

- instance-level
- transitive
- reflexive

simple relation chain:

` derived_by_descent_from o has_derived_by_descendant -> shares_ancestor_with`

i.e.

` all X derived_by_descent_from some (has_derived_by_descendant some Y)`  
` ==>`  
` all X shares_ancestor_with some Y`

Note we can see that this is entailed by homologous_to

` X homologous_to Y`  
` ==>`  
` all X derived_by_descent_from some anc(X,Y)`  
` all anc(X,Y) has_derived_by_descendant some Y`  
` ==>`  
` all X shares_ancestor_with some Y`

Note that this is \*not\* equivalent to homologous_to. It is an
instance-level relation, and does not have the symmetry property.

Note also that because of restrictions on the derived_by_descent_from
relation, this is not a trivial relation that holds between all entities
across species.

Remember this is an instance level relation, so when applies to classes
it should be read "all X R some Y"

#### Query chains

- shares_ancestor_with_part_of \<- shares_ancestor_with o part_of
- shares_ancestor_with_develops_from \<- shares_ancestor_with o
  develops_from

## Modeling homologous-as and ancestry information

Assuming we wish to represent pairwise homology with the addition of a
homologous-as relation, we need some kind of ternary relation, with a
3rd homologous_to argument. We can give this semantics using the
derived_by_descent_from relation.

We have 2 modeling options here:

- Direct n-ary relations
- n-ary relations pattern; which breaks down into
  - Homologous groupings
  - Common Ancestor (CA) classes

More information on the n-ary relations pattern can be found on the
[n-ary relations pattern W3C
note](http://www.w3.org/TR/2006/NOTE-swbp-n-aryRelations-20060412/),

### direct n-ary relations

Typically a statement involving a 3-argument predicated would be written
in FOL something like:

` P(A1,A2,A3)`

We introduce a syntactic sugar keyword "as" purely for documentation
purposes, so we can write the 3-arg version as:

` X homologous_to Y as A`

We treat the binary relation as equivalent but with an unspecified 3rd
argument. Or more precisely:

` X homologous_to Y as A`  
` ==>`  
` X homologous_to Y`

and

` X homologous_to Y`  
` ==>`  
` exists A : X homologous_to Y as A`

(this can't be stated in OBD, as the head is an existential)

specifying a more generic A is allowed. i.e.

` X homologous_to Y as A`  
` A is_a B`  
` ==>`  
` X homologous_to Y as B`

This means we can translate:

` X homologous_to Y`  
` ==>`  
` X homologous_to Y as anatomical entity`

(which can be represented in OBD)

We need a slightly modified version of transitivity

` X homologous_to Y as A`  
` Y homologous_to Z as B`  
` A is_a C`  
` B is_a C`  
` ==>`  
` X homologous_to Z as C`

Symmetry:

` X homologous_to Y as A`  
` ==>`  
` Y homologous_to Z as A`

Finally, we can supply a definitional rule:

` X homologous_to Y as A`  
` <==>`  
` all X derived_by_descent_from some (A and has_derived_by_descendant some Y)`  
` all Y derived_by_descent_from some (A and has_derived_by_descendant some X)`

We can also use a skolem ID to name the descendant class:

` X homologous_to Y as A`  
` ==>`  
` all X derived_by_descent_from some anc(X,Y)`  
` anc(X,Y) has_derived_by_descendant some X`  
` anc(X,Y) is_a A`

Unfortunately 3-ary predicates cannot be directly implemented easily in
OBD, RDF or OWL.

One way is to use RDF reification:

` X homologous_to Y as A`  
` ==>`  
` X homologous_to Y [S1]`  
` S1 homologous_as A`

This is a little awkward.

OBD has some experimental support for more direct n-ary relations, this
could be extended.

Another approach is to use an n-ary relations pattern. We present two
forms of this, one involving creating a grouping entity or class that
subsumes or collects the homology elements. The second involves creating
a class representing an ancestral entity or set of entities.

In either case, the above rules could still be useful for a
formalization that is not reasoned over directly.

### Homology groupings

I explore two similar variants of homology groupings. Both of these are
compatible with the existing HOG ontology.

The first variant involves grouping entities. For documentation purposes
I will name these as:

` `<taxon1>`_`<entity1>`_`<taxon2>`_`<entity2>`_homology`

But these could have numeric IDs if required. These entities would be
information artefacts.

OBD would contain triples following this template:

` H instance_of HomologyGrouping`  
` H has_member TE1`  
` H has_member TE2`  
` H homologous_as AE`

For example:

` mammalian_forelimb_avian_wing_homology instance_of HomologyGrouping`  
` mammalian_forelimb_avian_wing_homology has_member mammalian_forelimb`  
` mammalian_forelimb_avian_wing_homology has_member avian_wing`  
` mammalian_forelimb_avian_wing_homology homologous_as forelimb`

This translates to the direct n-ary form as:

` H instance_of HomologyGrouping`  
` H has_member TE1`  
` H has_member TE2`  
` H homologous_as AE`  
` ==>`  
` TE1 homologous_to TE2 as AE`

Additional provenance triples could be added:

` mammalian_forelimb_avian_wing_homology has_source `[`PMID:12345`](PMID:12345)

Note that this communicates the same information as the 3-ary relation
above. In fact there is a general pattern called the \[n-ary relations
pattern
<http://www.w3.org/TR/2006/NOTE-swbp-n-aryRelations-20060412/>\], and
this can be seen as a straightforward application of the pattern. It is
sometimes called reification (which can lead to confusion, as RDF uses
reification in a more restricted sense, and OBD follows this usage).

The main rule here is a macro rule for rewriting the grouping as a pair
of axioms:

` H has_member X`  
` H has_member Y`  
` H homologous_as A`  
` ==>`  
` all X derived_by_descent_from some (A and has_derived_by_descendant some Y)`

Note we do not need to add a second head clause for the symmetric case,
because there is no ordering of the members in the has_member axioms

(we may optionally want a clause to avoid reflexivity)

Note that there is nothing that restricts us to pairwise homology here.
The macro expansion rule will work even though it looks pairwise, as it
applies to all pairs. However, we may wish to make a more efficient
axiom:

` H has_member X1`  
` ...`  
` H has_member Xn`  
` H homologous_as A`  
` ==>`  
` all X1 derived_by_descent_from some anc(X1..Xn)`  
` all anc(X1..Xn) has_derived_by_descendant some X1`

### Homology grouping classes

One variant of this is to treat the homology groupings not as
information entities, but as anatomical entity classes:

` mammalian_forelimb is_a mammalian_forelimb_avian_wing_homology`  
` avian_wing is_a mammalian_forelimb_avian_wing_homology`  
` mammalian_forelimb_avian_wing_homology homologous_as forelimb`

(note: change naming convention for grouping class)

Note the explicit subsumption relationship.

We can still add provenance information:

` mammalian_forelimb_avian_wing_homology has_source `[`PMID:12345`](PMID:12345)

Macro rule:

` X is_a H`  
` Y is_a H`  
` H homologous_as A`  
` ==>`  
` all X derived_by_descent_from some (A and has_derived_by_descendant some Y)`  
` all Y derived_by_descent_from some (A and has_derived_by_descendant some X)`

Again, we can make this accept arbitrary numbers of members in the
grouping, not just pairs:

` X is_a H`  
` H homologous_as A`  
` ==>`  
` H is_a A`  
` all X derived_by_descent_from some anc(H)`  
` all anc(H) has_derived_by_descendant some X`

Note that this can be treated as a formalization of the HOG ontology.
Although HOG leaves out the "homologous_as" argument, this can be
treated as a default "anatomical entity" or the ontology LCS of all
grouped classes.

### Common Ancestor

This turns out to be very similar to the homologous grouping class
approach. The difference is that rather than represent a class that
subsumes all homologs, we make a class that subsumes all ancestors of
that class:

` ALL mammalian_forelimb derived_by_descent_from SOME mammalian_forelimb_avian_wing_ancestor`  
` ALL avian_wing derived_by_descent_from SOME mammalian_forelimb_avian_wing_ancestor`  
` mammalian_forelimb_avian_wing_ancestor is_a forelimb`

The general template for pairwise homology assertions is:

` all TE1 derived_by_descent_from some AE`  
` all TE2 derived_by_descent_from some AE`  
` AE is_a GE`

The macro rule becomes much simpler - simply adding class-level symmetry

` all X derived_by_descent_from some A`  
` ==>`  
` all A has_derived_by_descendant some X`

Note that additional biological information can be added to the
derived_by_descent_from statements. For example, if a temporal range is
known, this can be added. Or if the ancestral class has a temporal
range, this too can be added.

### Comparison of approaches

With the rules provided, all above approaches are inter-convertible,
although going in some directions may entail some information loss. In
fact with a system such as OBD, all approaches can co-exist in the same
KB (albeit with additional adminstrative burden, and potential loss of
efficiency due to storing redundant data).

- All forms can be interconverted via OBD-expressable rules, but there
  may be info loss
- Simple binary associations contain the least information
- Both HOGs and CA axioms allow expressing something about the ancestor
- CA axioms explicitly represent the line of evolutionary descent and
  the ancestor
- Simple binary relations might be the simplest relations to work with
- Symmetry is implicit with HOGs and CAs
- HOGs and CAs naturally extend beyond pairwise homology

The (MR)CA approach was initially criticized on the grounds that
homology information should not be stored in an ontology. But as far as
OBD and every RDF or OWL system is concerned, everything is an ontology.
We can trivially add the all-important provenance axioms to either the
ancestor class or to the derived_by_descent_from statements.

From an ontology management perspective, the CA axioms can be managed
separately from the homology-neutral ontology. This is perhaps where the
difference in strategy lies. A purist MRCA approach may avoid a
homology-neutral ontology, and utilize purely taxonomic leaf anatomical
entity classes and classes representing common ancestors.

The CA approach offers potential benefits - for example, temporal ranges
and other metadata can be assigned to the descendant triples.

## Discussion

### Consequences of omitting arg3

The 3rd argument can be regarded as optional for homologous_to. This is
because this relation is already heavily constrained by the 1:1
characteristic.

In contrast, arg3 is more useful for non 1:1 homology. Consider serial
homology. With pairwise relations we have statements of the form

1.  hand digit 3 serially homologous to hand digit 4
2.  hand digit 3 serially homologous to foot digit 4

<!-- -->

1.  hand digit 3 serially homologous to hand digit 4 as hand digit
2.  hand digit 3 serially homologous to foot digit 4 as digit

## Recommended Strategy

### Annotations

Phenoscape is currently collecting a small number of pairwise binary
homology statements. On examination, these appear to be promotable to
stronger homologous_to statements, as they all have the 1:1 property.

It is not clear that there is an immediate benefit to recording the
homologous_as argument, or if this is even possible in all cases.

### Reasoning strategy

If pairwise binary statements are asserted, the OBD reasoner can be
instructed to materialize the implicit ancestral classes, and the
descendant relations. For example:

` forelimb_digit_1[mouse] homologous_to forelimb_digit_1[human]`  
` ==>`  
` all forelimb_digit_1[mouse] derived_by_descent_from some forelimb_digit_1[mouse+human]`  
` all forelimb_digit_1[mouse+human] has_derived_by_descendant some forelimb_digit_1[mouse]`

(we don't need to write a symmetric rule, as we already have the
class-level symmetry rule for homologous_to).

The expanded axioms are all-some statements and thus have the expected
propagation over and under is_a.

We can also name the composition of derived_by_descent_from and
has_derived_by_descendant. This will give us inferences such as:

` all forelimb_digit_1[mouse] derived_by_descent_from some forelimb_digit_1[mouse+human]`  
` all forelimb_digit_1[mouse+human] has_derived_by_descendant some forelimb_digit_1[mouse]`  
` ==>`  
` all forelimb_digit_1[mouse] shares_ancestor_with some forelimb_digit_1[human]`

Because of the all some rule we infer further statements such as:

` all left_forelimb_digit_1[mouse] shares_ancestor_with some forelimb_digit_1[human]`  
` all forelimb_digit_1[mouse] shares_ancestor_with some forelimb_digit[human]`  
` all forelimb_digit_1[mouse] shares_ancestor_with some digit[human]`  
` all forelimb_digit_1[mouse] shares_ancestor_with some anatomical_entity[human]`  
` all forelimb_digit_1[mouse] shares_ancestor_with some digit[vertebrate]`  
` all left_forelimb_digit_1[mouse] shares_ancestor_with some digit[vertebrate]`

As can be seen, this could potentially lead to a large number of
inferred statements. The pattern here is one of "up-along-up" - we go up
the is_a hierarchy, along the class-level homologous_to, and then up the
is_a hierarchy.

If the named subset of the cross-product of taxon x anatomical entity is
large, then the number of inferred statements will be large. If this
becomes problematic, then some of the reasoning can be done by backward
chaining (although this is not yet implemented in the OBD reasoner,
non-recursive backward chaining horn rules can be implemented simply as
SQL views that mimic statements).

## Future Recommendations

## OBD Implementation

See
[vocab/homology](https://phenoscape.svn.sourceforge.net/svnroot/phenoscape/trunk/vocab/homology/)

and legacy documentation in
[vocab/homology/README.obd](https://phenoscape.svn.sourceforge.net/svnroot/phenoscape/trunk/vocab/homology/attic/README.obd)

### Relations

OBO Format (legacy):
[homol_relations.obo](https://sourceforge.net/p/phenoscape/code/HEAD/tree/trunk/vocab/homology/attic/homol_relations.obo)

### \#homologous_to

Note: this is OBO_REL:homologous_to in the above file

This expands to two all-some relations. In OBD, macro-expansion is just
another kind of rule

A homologous_to B \<==\> all A derived_by_descent_from some anc(A,B) and
all B derived_by_descent_from some anc(A,B)

where anc(A,B) =

entity^has_derived_by_descendant(A)^has_derived_by_descendant(B)

The function can be implemented as a SQL function which materializes the
class expression.

A constraint can be specified as:

A homologous_to B and A homologous_to C and B in_taxon T and C in_taxon
T

## \> B

C

i.e. no two distinct entity classes can be homologs of the same
structure in one species

### \#shares_ancestor_with

(this is the instance-level relation VBO calls homologous_to)

ID: [RO_0002158](http://purl.obolibrary.org/obo/RO_0002158). (Also see
legacy declaration in
[homol_relations.obo](https://sourceforge.net/p/phenoscape/code/HEAD/tree/trunk/vocab/homology/attic/homol_relations.obo))

This is simply the chain of two relations. In OWL:

SubPropertyOf(
PropertyChain(<a href="#derived_by_descent_from" class="wikilink"
title="#derived_by_descent_from">#derived_by_descent_from</a>
<a href="#has_derived_by_descendant" class="wikilink"
title="#has_derived_by_descendant">#has_derived_by_descendant</a>)
<a href="#shares_ancestor_with" class="wikilink"
title="#shares_ancestor_with">#shares_ancestor_with</a>)

Currently the OBD reasoner lacks a general property chain rule but this
is easily implemented in specific cases via horn rules.

derived_by_descent_from(X,A) and has_derived_by_descendant(A,Y) -\>
shares_ancestor_with(X,Y)

Note that materializing this closure could result in large sets of
inferred links. One option to explore is to not materialize this, i.e.
leave the horn clause as a view. Some changes to the OBD API may be
required.

### Composition with other relations

- part_of and has_part

Recommendation: do this at query time. This will save on materializing
on large numbers of links. In addition some of the desired use cases may
be difficult to formulate as logical axioms and are better implemented
programmatically. E.g. finding structure-pairs that are not homologous
yet a large number of the parts of each structure are homologous.

- develops_from

Recommendation: same as above.

Open question: a strict transformation_of relation may be useful for the
formalization. E.g. if A is iso_homologous to B, and A is a
transformation_of A2, is A2 homologous to B?

### Treatment of class level relations in OBD

- TODO - explicitly use the quantification flags in OBD. This will make
  the mapping to OWL cleaner but is not required for the above steps.

## Usage Guidelines

### Assert homology at the appropriate level

For example, if tax1 has a bone B that develops from a cartilage element
C, and tax2 has a homologous element but is purely cartilaginious, then
we can annotate either of the following:

1.  tax1-B homologous_to tax2-C
2.  tax1-C homologous_to tax2-C

But a better strategy might be name a skeletal element superclass E,
such that B and C are subclasses of E, and then declare

1.  tax1-E homologous_to tax2-E

From this we would infer the 2 axioms above

### Fusions

Assume that v1 and

### Examples

#### Mereological Sums and Fusions

- human mc3 po.df.hd \[some\] cow cannon bone

## Appendix

### Representation of mereological sums in anatomy ontologies
