---
title: Novel reasoning strategies
permalink: wiki/Novel_reasoning_strategies
layout: wiki
---

Potential strategies to implement novel inference procedures introduced
in the <a href="OBD_Reasoner#Novel_inference_procedures_for_Phenoscape"
class="wikilink" title="OBD Reasoner">OBD Reasoner</a> page. These
comprise: the Mabee rule for inferring the absence of features in taxa.

## Prelude: Instance relations and class relations

It is useful to conceptualize two entities in a domain of knowledge such
as biology viz. classes and instances. Every entity in the domain is an
instance. Instances can be grouped together on the basis of the
properties they exhibit, such as the things that are colorless. Classes
are groupings or sets of instances on the basis of common properties
that they exhibit. An example of a class would be car, which includes
all the entities (instances) which comprise a chassis resting
(typically) on 4 wheels which is powered by an internal combustion
engine, such as my Porsche 911 Turbo or the car you drive.

Subsumption semantics (as inherent in the *is_a* relation) hold between
sets of real-world instances or classes. For example, the set of all
left-handed people above the age 35 is subsumed by the set of all the
people above the age 35 (who may be left- or right-handed or
ambidextrous). The subsumption semantics of the *is_a* relation are
defined in the OBO relations ontology as follows: "...C is_a C' if and
only if: given any c that instantiates C at a time t, c instantiates C'
at t..." In plain English, this means: the set of all left-handed people
above the age 35 **is subsumed by (or included by)** the set of people
above 35 if and only if, a person who belongs to the group of left
handed people above the age of 35 also belongs to the set of people
above the age of 35. This is trivially valid in the real world.

## The absence of features problem

Canonical ontologies define properties of typical or ideal classes in
the domain of knowledge. In the domain of fishes, it is typical for
"wild" fish specimens belonging to the Ostariophysian clade to exhibit
basihyal cartilage. However, fishes belonging to the Siluriformes clade,
which is subsumed by the Ostariphysian clade are characterized by the
absence of basihyal cartilage. The Mabee rule is a proposal to resolve
the conflicting assertions formally stated as "ALL instances of a clade
C1 *typically* exhibit a feature F1 AND ALL instances of a clade C2
which is a subclass of C1 do not exhibit F1." This creates what is
termed a *logical inconsistency*. These are shown in (1) and (2) below.

$`\forall`$A, B, F: *is_a*(A, B) $`\and`$*exhibits*(A, F)
$`\Rightarrow`$ *exhibits*(B, F) -- (1)

**NOT** *exhibits*(B, F) -- (2)

The Mabee rule involves inferences propagated to the lower levels of a
taxonomy from assertions (or definitions) in the higher levels. Given
that ALL instances of fishes belonging to the Ostariophysian clade are
defined to possess basihyal cartilage, it can be inferred that instances
of fishes belonging to the Siluriformes clade (which is subsumed by the
Ostariophysian clade) would possess basihyal cartilage as well. An
assertion to the contrary creates the contradiction or inconsistency.

- NOTE
  - The NOT operator in equation (2) is the negation operator from first
    order logic. In (2), it is used to state the entity B *does not*
    exhibit the feature F. The semantics of the negation operator and
    its pertinence to the Phenoscape project will be discussed in
    another section. For now, it is enough to understand that the
    inference derived in (1) (*exhibits*(B, F)) and the assertion in (2)
    directly contradict one another.

<REMARK> *\[It looks like there is a typo in (1) above. It should
read*is_a''(B, A) -- both to correspond to the example, and to enable
the contradiction. Also, for the sake of clarity, (2) could better be
written as

**NOT** *exhibits*(Siluriformes, basihyal_cartilage)

Finally, to make it more clear that the contradiction is derivable, one
might want to mention that

*exhibits*(Ostariophysian, basihyal_cartilage)

and

*is_a* (Siluriformes, Ostariophysian)

are in the database.

The bottom line: The rule (1), *as stated above*, is a perfectly sound
rule that does not lead to any contradiction. The rule (1), *as
corrected above*, is unsound (leads to a contradiction) -- it cannot be
used for any consistent reasoning.
<a href="User%3AVg34" class="wikilink" title="Vg34">Vg34</a> 13:56, 29
June 2009 (EDT)\]'' </REMARK>

### Implementation Strategies

A few potential strategies to address this situation are presented here.

#### The move to existential quantification

If instead of constraining every instance of A to exhibit the feature F,
the constraint was loosened to only some instances of A, the
contradiction scenario can be avoided. If only some instances of A
exhibited F and all A are B, then it cannot be inferred that all B
exhibit F. When the assertion in (2) is added, a contradiction is
averted.

This strategy will require careful curation of the top level classes in
the taxonomy. Definitions of higher level classes and their properties
will have to be constructed carefully to specify existential (SOME) and
universal (ALL) constraints, so that inconsistencies are not entailed.

#### The default property

This strategy is based on the proposals by Hoehndorf et al and Ceusters
et al. Property values as specified by definitions in canonical
ontologies can be transformed into default values. For example, a
canonical ontology would define all animal cells to contain at least one
nucleus in them. However, red blood corpuscles lack nuclei, the
exception to this rule. This situation is represented in FOL as shown
below. The $`\not`$ in (3) is the NOT operator, to specify for all
instances of red blood cell, there does not exist even one instance of a
nucleus that is contained in any of them.

$`\forall`$c $`\exists`$n : *instance_of*(c, Cell) $`\and`$
*instance_of*(n, Nucleus) $`\and`$ *contains*(c. n) -- (1)

$`\forall`$c: *instance_of*(c, Red_Blood_Cell) $`\Rightarrow`$
*instance_of*(c, Cell) -- (2)

$`\forall`$rbc$`\not`$ $`\exists`$n : *instance-of*(rbc,
Red_Blood_Cell)$`\and`$ *instance_of*(n, Nucleus) $`\and`$ *contains*(c.
n)--(3)

**Inference from (1) and (2):**

$`\forall`$c $`\exists`$n : *instance_of*(c, Red_Blood_Cell) $`\and`$
*instance_of*(n, Nucleus) $`\and`$ *contains*(c. n) -- (4)

An inference (4) derived from combining (1) and (2) would directly
contradict (3). If the *contains* relation in (1) were to be transformed
into a default relation as shown in (5) below, this conflict would be
avoided

$`\forall`$c $`\exists`$n : *instance_of*(c, Cell) $`\and`$
*instance_of*(n, Nucleus) $`\and`$ *contains_by_default*(c. n) -- (5)

In this case, combining (5) and (2) would derive (6) which does not
contradict with (3) because *contains_by_default* relation is different
from *contains*.

**Inference from (5) and (2):**

$`\forall`$c $`\exists`$n : *instance_of*(c, Red_Blood_Cell) $`\and`$
*instance_of*(n, Nucleus) $`\and`$ *contains_by_default*(c. n) -- (6)

This strategy can be implemented by marking up relations used in concept
definitions within ontologies as *default relations* and treating
relations used in assertions as separate entities from default
relations. This can be done by slightly changing the module which loads
ontological definitions of relations and concepts into the OBD database
