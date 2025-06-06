---
title: OBD Reasoner
permalink: wiki/OBD_Reasoner
layout: wiki
tags:
 - Database
 - Ontology
 - Reasoning
 - API
---

The OBD reasoner uses definitions of transitive relations, relation
hierarchies, and relation compositions to infer implicit information.
These inferences are added to the OBD Phenoscape database. This section
documents the inherited code in Perl and embedded SQL, that extracts
implicit inferences from the downloaded ontologies and annotations of
ZFIN and Phenoscape phenotypes.

## Notation

### Classes, instances, relations

When describing rules below, we use the following notations:

- A, B, C: classes (as subjects or objects). Note that relationship
  concepts can also appear as subject or object in an assertion.
- a, b, c: instances, or individuals (as subjects or objects)
- *R*: relationship (predicate)
- *R*(A, B): A *R* B, for example *is_a*(A, B) is equivalent to A
  *is_a* B. This is the functional form of assertions.
- Reification: assertions about assertions. I.e., A, B, ... may also be
  assertions. For example, the yellow that *inheres_in* a particular
  dorsal fin *is_a* yellow, which we can write formally as:
  *is_a*(*inheres_in*(yellow, dorsal_fin), yellow).

### Conjunction and Implication

- The double arrow ($`\Rightarrow`$) is also called *directional
  implication*. It can be translated into English to mean "it implies"
  or "it follows."
- The "cap" or "A minus the stripe" ($`\and`$) is the FOL construct to
  specify *conjunction* and can be translated to "and" in plain English.

### Quantification of instances

In first order logic (FOL), it is common to assert statements about all
possible instances of a concept in the real world. Let us start with the
assertion, "All puppies are dogs." This can be stated as shown below in
(1)

**$`\forall`$ A: *instance_of*(A, Puppy) $`\Rightarrow`$
*instance_of*(A, Dog)** -- (1)

The inverted A ($`\forall`$) is called the *universal quantifier* and
can be translated to "for every" or " for all" in plain English.
Similarly, the colon (:) in the FOL statement above can be read as "such
that." Therefore, the sentence above translated into English reads:

"*For all A such that A is a Puppy, implies that A is a Dog*"

or even simpler as we shall readily comprehend, "*All puppies are
dogs*." Note this is a simple assertion of the semantics of the *is_a*
predicate that is so common to Phenoscape. The formulation as
*is_a*(Puppy, Dog) is a class-level abstraction from the quantified
instances we have used in (1).

The FOL statement below states the transitive property of the *is_a*
relation

**$`\forall`$ A, B, C: *is_a*(A, B) $`\and`$ *is_a*(B, C)
$`\Rightarrow`$ *is_a*(A, C)** -- (2)

The statement (2) above can be translated to read:

*For all A, B, and C, such that A is a B, and B is a C, it follows that
A is a C*

The *existential quantifier* ($`\exists`$) can be translated to "there
exists" or "at least" in plain English. Now consider the statement,
"Some birds are flightless" This can be stated as shown below

**$`\exists`$ A: *instance_of*(A, Bird) $`\and`$ *instance_of*(A,
Flightless thing)** -- (3)

This can be translated to plain English to:

"*There exists an A such that A is a Bird and A is a Flightless thing*"

These are just some of the many constructs from first order logic which
find common use in the Phenoscape project. There is a more full-fledged
introduction to [FOL on
Wikipedia](http://en.wikipedia.org/wiki/First-order_logic).

## Implemented Relation Properties

### Relation Transitivity

**Rule:** $`\forall`$A, B, C, *R* and *R* transitive: *R*(A, B) $`\and`$
*R*(B, C) $`\Rightarrow`$ *R*(A, C)

Transitive relationships are the simplest inferences to be extracted and
comprise the majority of new assertions added by the reasoner. When the
ontologies are loaded into the database, every transitive relation is
marked with a specific value of a property called *is_transitive* prior
to loading. Transitive relationships include (ontology in brackets):

- is_a (OBO Relations)
- has_part (OBO Relations)
- part_of (OBO Relations)
- integral_part_of (OBO Relations)
- has_integral_part (OBO Relations)
- proper_part_of (OBO Relations)
- has_proper_part (OBO Relations)
- improper_part_of (OBO Relations)
- has_improper_part (OBO Relations)
- location_of (OBO Relations)
- located_in (OBO Relations)
- derives_from (OBO Relations)
- derived_into (OBO Relations)
- precedes (OBO Relations)
- preceded_by (OBO Relations)
- develops_from (Zebrafish Anatomy)
- anterior_to (Spatial Ontology)
- posterior_to (Spatial Ontology)
- proximal_to (Spatial Ontology)
- distal_to (Spatial Ontology)
- dorsal_to (Spatial Ontology)
- ventral_to (Spatial Ontology)
- surrounds (Spatial Ontology)
- surrounded_by (Spatial Ontology)
- superficial_to (Spatial Ontology)
- deep_to (Spatial Ontology)
- left_of (Spatial Ontology)
- right_of (Spatial Ontology)
- complete_evidence_for_feature(Sequence Ontology)
- evidence_for_feature (Sequence Ontology)
- derives_from (Sequence Ontology)
- member_of (Sequence Ontology)
- exhibits (Phenoscape Ontology)

Transitive relations are extracted from the database by the reasoner and
transitive relationships are computed by the reasoner for each relation.
For example, given that *is_a* is a transitive relation, and if the
database holds A *is_a* B and B *is_a* C, then the reasoner computes A
*is_a* C and adds this new assertion to the database. Similarly, new
inferred assertions are added to the database for every transitive
relation.

#### Note

Relation transitivity is the only relation property whose definition is
(indirectly) extracted by the reasoner from the loaded ontologies (using
the *is_transitive* metadata tag) in order to compute inferences.
Although definitions of many of the other relation properties (such as
relation reflexivity) can be found in the ontologies as well, in the
current implementation inference mechanisms associated with these
relation properties are hard coded into the reasoner.

### Relation (role) compositions

**Rule:** $`\forall`$A, B, C, *R*: *R*(A, B) $`\and`$ *is_a*(B, C)
$`\Rightarrow`$ *R*(A, C)

**Rule:** $`\forall`$A, B, C, *R*: *is_a*(A, B) $`\and`$ *R*(B, C)
$`\Rightarrow`$ *R*(A, C)

Relation (role) compositions are of the form A *R*<sub>1</sub> B, B
*R*<sub>2</sub> C =\> A (*R*<sub>1</sub>\|*R*<sub>2</sub>) C. For
example, given A *is_a* B and B *part_of* C then A *part_of* C. The
reasoner computes such inferences and adds them to the database.

### *is_a* Relation Reflexivity

**Rule:**$`\forall`$A, *R* and *R* reflexive $`\Rightarrow`$ A *R* A

Reflexive relations relate their arguments to themselves. A good
example: "A rose *is_a* rose." The *is_a* relation is reflexive. In the
database, every class, instance, or relation (having a corresponding
identifier in the *Node* table of the database) is inferred by the
reasoner to be related to itself through the *is_a* relation. Given a
class called Siluriformes (with identifier TTO:302), the reasoner adds
the TTO:302 *is_a* TTO:302 to the database.

The subsumption (*is_a*) relation is the only reflexive relation that is
handled by the reasoner. Other reflexive relations abound in the real
world, *subset_of* is a good mathematical example from the domain of set
theory. Every set is a subset of itself. Such relations are NOT dealt
with by the reasoner.

### Relation Hierarchies

**Rule:** $`\forall`$A, B, *R<sub>1</sub>*, *R<sub>2</sub>*:
*R<sub>1</sub>*(A, B) $`\and`$ *is_a*(*R<sub>1</sub>*, *R<sub>2</sub>*)
$`\Rightarrow`$ *R<sub>2</sub>*(A, B)

An example: If A *father_of* B and father_of *is_a* parent_of, then A
*parent_of* B

### Relation Chains

**Rule:** $`\forall`$A, B, C: *inheres_in*(A, B) $`\and`$ *part_of*(B,
C) $`\Rightarrow`$ *inheres_in_part_of*(A, C)

Relation chains are a special case of relation composition. Component
relations are accumulated into an assembly relation. Specifically,
instances of the relation *inheres_in_part_of* are accumulated from
instances of the relations of *inheres_in* and *part_of*. IF A
inheres_in B and B part_of C, THEN A inheres_in_part_of C. This relation
chain is specified by a *holds_over_chain* property in the
*inheres_in_part_of* stanza of the [Relation
Ontology](http://www.berkeleybop.org/ontologies/obo-all/ro_proposed/ro_proposed.obo).
However, the actual rule is hard coded into the OBD reasoner and not
derived from the ontology.

### Decomposing "post-composition" relations

**Rule:** $`\forall`$Q, E: *inheres_in*(Q, E) $`\Rightarrow`$
*inheres_in*(*inheres_in*(Q, E), E)

**Rule:** $`\forall`$Q, E: *inheres_in*(Q, E) $`\Rightarrow`$
*is_a*(*inheres_in*(Q, E), Q)

Phenotype annotations are typically "post-composed", where an entity and
quality are combined into a Compositional Description. For example, an
annotation about the quality *decreased size (PATO:0000587)* of the
entity *Dorsal Fin (TAO:0001173)* may be post-composed into a
Compositional Description that looks like
*PATO:0000587^OBO_REL:inheres_in(TAO:0001173)*. Instances of *is_a* and
*inheres_in* relations are extracted from post compositions like this.
In the above example, the reasoner extracts:

1.  PATO:0000587^OBO_REL:inheres_in(TAO:0001173) OBO_REL:inheres_in
    TAO:0001173, and
2.  PATO:0000587^OBO_REL:inheres_in(TAO:0001173) OBO_REL:is_a
    PATO:0000587

## Phenoscape-specific rules

This section describes the Phenoscape-specific rules added to the OBD
reasoner.

### PATO Character State relations

The Phenotypes and Traits Ontology (PATO) contains definitions of
qualities, many of which are used in phenotype descriptions. These
qualities are partitioned into various subsets (or slims) such as
attribute slims, absent slims, and value slims. Attribute and value
slims are mutually exclusive subsets. Attribute slims include qualities
that correspond to Characters of anatomical entities, Color or Shape for
example. Value slims include qualities, which correspond to States that
a Character may take, for example Red and Blue for the Color character
and Curved and Round for the Shape character. These relationships are
not explicitly defined in the PATO ontology but can be inferred using
the relations shown below

1.  PATO:0000587 oboInOwl:inSubset value_slim
2.  PATO:0000587 OBO_REL:is_a PATO:0000117
3.  PATO:0000117 oboInOwl:inSubset attribute_slim

From these definitions, the relationship

1.  PATO:0000587 PHENOSCAPE:value_for PATO:0000117

can be inferred by the reasoner. Ideally, the inference rule for this
can be represented as

**Rule:** $`\forall`$V, A: *in_Subset*(V, value_slim) $`\and`$ *is_a*(V,
A) $`\and`$ *in_subset*(A, attribute_slim) $`\Rightarrow`$
*value_for*(V, A)

However, not all qualities are partitioned into one of the attribute or
value slim subsets. In such cases, the super quality of these qualities
is discovered by the reasoner and checked to find out if it is in the
attribute or value slim subsets. This process continues until a quality
belonging to the attribute slim subset is found. This can be represented
as

**Rule:** $`\forall`$V, A: *NOT in_subset*(V, value_slim) $`\and`$
*is_a*(V, A) $`\and`$ *in_subset*(A, attribute_slim) $`\Rightarrow`$
*value_for*(V, A)

Lastly, there are orphan qualities in PATO which are not related to any
other qualities by subsumption and which do not belong to the attribute
or value slim subsets. These are grouped under an unknown or undefined
attribute.

**Rule:** $`\forall`$V, A: *NOT in_Subset*(V, value_slim) $`\and`$ *NOT
is_a*(V, A) $`\Rightarrow`$ *value_for*(V, unknown attribute)

### The Balhoff rule

**Rule:** $`\forall`$A, B, x: *is_a*(A, B) $`\and`$*exhibits*(A, x)
$`\Rightarrow`$ *exhibits*(B, x)

This rule was proposed by Jim Balhoff to reason upwards in a (typically
taxonomic) hierarchy using the *exhibits* relation. A relevant example:
GIVEN THAT *Danio rerio* exhibits a round fin AND *Danio rerio* is a
Danio THEN Danio exhibits a round fin. Note that *exhibits* has someOf
semantics - so the inference is that *some of* Danio exhibit the
phenotype.

This is the exact opposite of the *genus differentia* rule which
postulates reasoning only downwards in a hierarchy.

## Sweeps

A reasoner functions over several sweeps. In each sweep, new implicit
inferences are derived from the explicit annotations (as described in
the previous sections) and added to the database. In the following
sweep, inferences added from the previous sweep are used to extract
further inferences. This process continues until no additional
inferences are added in a sweep. This is when the *deductive closure of
the inference procedure* is reached. No further inferences are possible
and the reasoner exits.

## Future directions

Possible future directions for the extension of the reasoner include
adding more relation properties as well as some <a
href="Technical_issues_to_be_resolved_in_the_reasoner_and_relation_semantics"
class="wikilink" title="outstanding technical issues">outstanding
technical issues</a>.

### Relation Properties to be implemented

The following relation properties may be implemented on the reasoner in
future if necessary.

#### Relation Symmetry

**Rule:** $`\forall`$A, B, *R* and *R* symmetric: *R*(A, B)
$`\Rightarrow`$ *R*(B, A)

An example of a symmetric relation is the *neighbor* relation. IF Jim
neighbor_of Ryan THEN Ryan neighbor_of Jim. A more biologically relevant
example is the *in_contact_with* relation. IF middle_nuchal_plate
*in_contact_with* spinelet, THEN spinelet *in_contact_with*
middle_nuchal_plate

NOTE: There is no direct relationship between *relation symmetry* and
*relation reflexivity*

#### Relation Inversion

**Rule:** $`\forall`$A, B, *R<sub>1</sub>*, *R<sub>2</sub>*:
*R<sub>1</sub>*(A, B) $`\and`$ *inverse_of*(*R<sub>1</sub>*,
*R<sub>2</sub>*) $`\Rightarrow`$ *R<sub>2</sub>*(B, A)

An example of relation inversions can be found in the *posterior_to* and
*anterior_to* relations. IF anterior_nuchal_plate *anterior_to*
middle_nuchal_plate AND *anterior_to* *inverse_of* *posterior_to*, THEN
middle_nuchal_plate *posterior_to* anterior_nuchal_plate
