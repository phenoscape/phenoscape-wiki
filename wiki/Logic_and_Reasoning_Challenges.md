---
title: Logic and Reasoning Challenges
permalink: wiki/Logic_and_Reasoning_Challenges
layout: wiki
tags:
 - EQ Annotation
 - Informatics
 - Ontology
 - Queries
 - Reasoning
 - Data
 - Curation
 - Taxonomy
 - OBD
redirect_from:
 - wiki/Technical_issues_to_be_resolved_in_the_reasoner_and_relation_semantics
---

This page discusses issues to be resolved in the near future. These
issues pertain to relation semantics as well as inference procedures.

## Inferring in both directions on the taxonomy

It is desired that annotations to higher taxa in the taxonomy be
propagated to the lower taxa that are subsumed by the higher taxon; i.e.
classical top down inferences. Given that the reasoner already reasons
bottom upward, associating phenotype annotations from the lower level
taxa to the higher level taxa, adding top-down inferencing may cause
widespread inconsistencies in the data if unchecked.

The OBD reasoner can reason from annotations at the lower levels of the
taxonomy to the higher levels. Given that *Danio rerio* exhibits a
phenotype P, the OBD reasoner infers that *Danio* exhibits the same
phenotype P. This is reasoning up the taxonomy, using the subsumption
relationship between *Danio rerio* and *Danio*. This is possible because
the annotations to each taxon are (implicitly) existentially quantified.
The annotation "*Danio rerio* exhibits increased length of maxillary
barbel towards orbit" is shown in (1). The semantics are in (2).

<javascript> TTO:1001979 PHENOSCAPE:exhibits
PATO:0000573^OBO_REL:inheres_in(TAO:0001938)^OBO_REL:towards(TAO:0001967)
-- (1) </javascript>

$`\exists`$ X : *instance_of*(X, TTO:1001979) $`\and`$
*PHENOSCAPE:exhibits*(X,
PATO:0000573^OBO_REL:inheres_in(TAO:0001938)^OBO_REL:towards(TAO:0001967))
-- (2)

Given that *Danio rerio* (TTO:1001979) is subsumed by the genus *Danio*
(TTO:101040) in the Teleost Taxonomy as shown in (3), it is possible to
infer that "*Danio* exhibits increased length of maxillary barbel
towards orbit" (4).

<javascript> TTO:1001979 OBO_REL:is_a TTO:101040 -- (3) TTO:101040
PHENOSCAPE:exhibits
PATO:0000573^OBO_REL:inheres_in(TAO:0001938)^OBO_REL:towards(TAO:0001967)
-- (4) </javascript>

Inferring down the taxonomy, that is using assertions at higher levels
to extract inferences at lower levels, requires universal
quantification. For example, the assertion that all "Siluriformes
exhibit decreased width of mesethmoid bone" can be captured using OBD
semantics as shown in (5). The universal semantics of this assertion is
shown in (6). Siluriformes directly subsumes Ictaluridae as shown in
(7). From (5) and (7), it is straightforward to infer that "Ictaluridae
exhibit decreased width of mesethmoid bone" as shown in (8).

<javascript> TTO:1380 PHENOSCAPE:exhibits
PATO:0000599^OBO_REL:inheres_in(TAO:0000323) -- (5) </javascript>

$`\forall`$ X : *instance_of*(X, TTO:1380) $`\and`$
*PHENOSCAPE:exhibits*(X, PATO:0000599^OBO_REL:inheres_in(TAO:0000323))
-- (6)

<javascript> TTO:10930 OBO_REL:is_a TTO:1380 -- (7) TTO:10930
PHENOSCAPE:exhibits PATO:0000599^OBO_REL:inheres_in(TAO:0000323) -- (8)
</javascript>

The problem with using top-down inferences using universally quantified
statements is that currently there is no way to distinguish these from
existentially quantified statements. We use the *PHENOSCAPE:exhibits*
relation for existentially quantified statements. Using the same
relation for universally quantified statements would make it possible to
extract incorrect inferences given the current configuration. Consider
the subsumption relationship between *Danio* and *Danio choprai* shown
in (9). If there is no distinction between existentially and universally
quantified statements, it is possible to infer from (9) and (4) the
erroneous conclusion that "*Danio choprai* exhibits increased length of
maxillary barbel towards orbit" (10). At present, there are no
annotations to *Danio choprai*.

<javascript> TTO:1052801 OBO_REL:is_a TTO:101040 -- (9) TTO:1052801
PHENOSCAPE:exhibits
PATO:0000573^OBO_REL:inheres_in(TAO:0001938)^OBO_REL:towards(TAO:0001967)
-- (10) </javascript>

Recall that the reasoner works in sweeps. It extracts one set of
inferences (Inf-1) from the assertions (A) in its first sweep. In the
next sweep, the reasoner pulls out a different set of inferences (Inf-2)
from the assertions A **AS WELL AS** the inferences Inf-1 from the
previous sweep. The reasoner repeats these sweeps until no new
inferences are added. This is why the reasoner will likely infer all
taxa exhibit all phenotypes if it is used to reason both up and down the
taxonomy without checking for universal and existential semantics.

### Possible solutions

In this section, we discuss possible approaches to resolving this issue
with reasoning both up and down the taxonomy.

#### Different relations for different purposes

In classical first-order logic (FOL), all relations and properties
asserted upon concepts (or taxa in the case of Phenoscape) are inherited
by the subsumed concepts. This is because by default, all assertions
about the concepts are universally quantified, i.e. hold true for ALL
instances of the concept. If all cars have four wheels, and if all SUVs
are cars, then all SUVs have four wheels. This is the way of top-down,
classical FOL inferencing.

In Phenoscape, we have adopted the OBD schema of modeling concepts,
wherein all assertions to the concepts are existentially quantified,
i.e. the assertion is true with at least one instance of the concept.
This is very convenient for the life sciences, where exceptions are so
prevalent. As a ready example, consider how the duck-billed platypus
easily overrules the "all mammals are viviparous" rule. Further,
existential quantification allows us to reason up the taxonomy. If some
Teleostei exhibit round fins, and all Teleostei are Ostariophysi, then
some Ostariophysi exhibit round fins.

By default, we use the *PHENOSCAPE:exhibits* relation to link taxa to
phenotypes using existential semantics. Using the same relation to model
universally quantified relationships between taxa and phenotypes, would
cause incorrect inferencing and loss of data integrity. The easiest way
to address this issue is to use different relations; one for universally
quantified relations and the other for existentially quantified
relations. Let us call these relations *PHENOSCAPE:all_exhibit* and
*PHENOSCAPE:some_exhibit* respectively.

Now the OBD reasoner uses the following rule to extract inferences up
the taxonomy using the *PHENOSCAPE:exhibits* relation (1).

**Rule-1:** $`\forall`$A, B, x: *is_a*(A, B) $`\and`$*exhibits*(A, x)
$`\Rightarrow`$ *exhibits*(B, x)

This can be replaced with the following two rules, which use the two new
relations, *PHENOSCAPE:all_exhibit* and *PHENOSCAPE:some_exhibit*.
(Please suggest better names for these if you can think of them).

**Rule-2:** $`\forall`$A, B, x: *is_a*(A, B) $`\and`$*some_exhibit*(A,
x) $`\Rightarrow`$ *some_exhibit*(B, x)

**Rule-3:** $`\forall`$A, B, x: *is_a*(A, B) $`\and`$*all_exhibit*(B, x)
$`\Rightarrow`$ *all_exhibit*(A, x)

This will keep the inferences from getting mixed up. Let us consider the
scenario where species Sp1 and Sp2 (from genus Gen1) are asserted to
exhibit phenotype Phen1. These assertions are shown in (A-1) and (A-2).
The subsumption relations are shown in (A-3) and (A-4)

<javascript> Sp1 PHENOSCAPE:some_exhibit Phen1 -- (A-1) Sp2
PHENOSCAPE:some_exhibit Phen1 -- (A-2) Sp1 OBO_REL:is_a Gen1 -- (A-3)
Sp2 OBO_REL:is_a Gen1 -- (A-4) </javascript>

The reasoner makes the inference (I-1) from the assertions (A-1) ~ (A-4)
and the inference rule Rule-2.

<javascript> Gen1 PHENOSCAPE:some_exhibit Phen1 -- (I-1) </javascript>

Now. given this new inference (I-1), the reasoner cannot infer that all
the species Sp1, Sp2, and let us say 10 other species Sp3 ~ Sp12 also
exhibit Phen1, because the inference rule for some_exhibit cannot be
used to infer down the taxonomy. Again, consider the assertion that ALL
instances of genus Gen1 exhibit a phenotype Phen2 as shown in (A-5)

<javascript> Gen1 PHENOSCAPE:all_exhibit Phen2 -- (A-5) </javascript>

Given (A-5) and all the subsumption relations between Gen1 and the
hypothetical twelve species under Gen1 (including A-3 and A-4), the
reasoner uses inference rule Rule-3 to infer (I-2) ~ (I-13)

<javascript> Sp1 PHENOSCAPE:all_exhibit Phen2 -- (I-2) Sp2
PHENOSCAPE:all_exhibit Phen2 -- (I-3) .. .. Sp12 PHENOSCAPE:all_exhibit
Phen2 -- (I-13) </javascript>

Again, cyclical inferences are ruled out because there are no inference
rules to infer up the taxonomy using the *all-exhibit* relation.

##### What has to change?

To implement this strategy, two new relations can be defined in the
Phenoscape Vocab ontology, where the current definition of the
*PHENOSCAPE:exhibits* relation is found. At the curation level, curators
have to qualify their assertions as being either existentially or
universally quantified. Specifically, the Phenex UI could tap the
curator's shoulder and ask, "Ahem, does this annotation hold true for
all specimens belonging to this taxa or just some specimens?" This needs
some changes (no less!) to the Phenex interface and also to the
character matrix format in which the data is exported. The data loader
module of Phenoscape has to know this information so that the
appropriate relation is used in creating the taxon-phenotype statement
to be loaded into the knowledgebase. The query module will have to be
modified to retrieve both inferred and asserted taxon-phenotype
statements using the two different relations. The JSON format in which
the data is exported needs to be modified to accommodate the two
different kinds of relation statements, and lastly the UI will have to
explicitly distinguish between the two.

###### A possible simpler solution (Update: Feb 22, 2010)

It is possible to check the rank of the taxon to which the phenotype
assertion is made. If the rank of the taxon is not "species", then the
new relation *all_exhibit* can be used in the top-down reasoning as
shown below. The new rule is shown in (Rule-4)

**Rule-4:** $`\forall`$A, B, x: *is_a*(A, B) $`\and`$*exhibit*(B, x)
$`\and`$ ¬*rank*(B, "species") $`\Rightarrow`$ *all_exhibit*(A, x)

Assertion (A-6) is a phenotype assertion to a taxon of a higher rank,
let us say a Genus Gen1. Now, let's assume Gen1 has 2 species Sp1 and
Sp2. Inferences to Sp1 and Sp2 from the assertion (A-6) may use the new
relation *all_exhibit* as shown in (I-14) and (I-15).

<javascript> Gen1 PHENOSCAPE:exhibit Phen1 -- (A-6) Sp1 OBO_REL:is_a
Gen1 -- (A-7) Sp2 OBO_REL:is_a Gen1 -- (A-8)

Sp1 PHENOSCAPE:all_exhibit Phen1 -- (I-14) Sp2 PHENOSCAPE:all_exhibit
Phen1 -- (I-15) </javascript>

The inferences with the *all_exhibit* relation cannot be associated with
the higher taxa.

Similarly, for any taxon to which a phenotype assertion has been made,
the phenotype can be inferred on the higher taxa using the
*some_exhibit* relation as shown in (Rule-5)

**Rule-5:** $`\forall`$A, B, x: *is_a*(A, B) $`\and`$*exhibit*(A, x)
$`\Rightarrow`$ *some_exhibit*(B, x)

Given assertion (A-6) to a genus and assuming it belongs to a family
Fam1, the inference (I-16) can be made about the family Fam1.
<javascript> Gen1 PHENOSCAPE:exhibit Phen1 -- (A-6) Gen1 OBO_REL:is_a
Fam1 -- (A-9)

Fam1 PHENOSCAPE:some_exhibit Phen1 -- (I-16) </javascript>

The relation *some_exhibit* cannot be used to infer down the taxonomy.
Therefore, we can see that this new methodology can use the existing
assertions that use the *exhibits* relation, but can distinguish the
inferences that are made in both top-down and bottom-up reasoning. The
relations *all-exhibit* and *some-exhibit* are only inferred, never
asserted. Moreover, they can never be used to create new inferences.
This distinction averts the extraction of incorrect inferences.

In this solution, no changes are necessary to the NeXML format or to
Phenex. The changes need to be made to the OBD reasoner to use these two
new relations and the data query module needs to be changed to deal with
the two new relations as well. The REST services would not need to be
modified for this purpose.

#### Probabilistic assertions

Uncertainties are everywhere in the life sciences. The taxon-phenotype
assertions can be augmented with uncertainty factors to address this
issue. Inferences could use uncertainty calculi such as the
[Dempster-Schafer
method](http://en.wikipedia.org/wiki/Dempster%E2%80%93Shafer_theory) or
Bayes conditional probability rule to derive uncertainty factors of the
inferences given the uncertainty factors of the assertions.

The advantage of this strategy will be that we can continue to use the
*PHENOSCAPE:exhibits* relation for taxon-phenotype statements, and at
the same time display the uncertainty values associated with every
assertion displayed at the UI; far more intuitive than "Taxon T exhibits
increased size of E AND decreased size of E."

##### What needs to change?

Curators will have to manually enter uncertainty factors (UFs) of the
assertions in the Phenex UI, which needs modification to handle these.
The character matrix format needs to be modified to accommodate UFs. The
data loader module needs to use reified statements around assertions to
store UFs. The OBD reasoner will have to be augmented with an
implementation of uncertainty calculus. The query module needs to
retrieve the UF associated with every assertion, and export this in a
modified JSON format. Lastly, the UI will have to add a provision to
display uncertainty factors.

## The problem with absence of features

Descriptions of phenotypes as used in the Phenoscape project (and a
plethora of phenomena in the real world) are replete with exceptions, or
aberrations from what is considered to be "normal." While canonical
ontologies like the [FMA](http://sig.biostr.washington.edu/projects/fm/)
and the
[TAO](http://www.berkeleybop.org/ontologies/obo-all/teleost_anatomy/teleost_anatomy.obo)
contain ontological definitions of ideal specimens, observations in the
life sciences are full of aberrations to these general rules.

Phenoscape has some typical issues dealing with absence of anatomical
features in certain species of Ostariophysian fishes. For example, the
basihyal cartilage is found in all species of Ostariophysian fishes,
except the Siluriformes. At present, this information is captured in
Phenoscape using the combination of the PATO term for "absent in
organism" (PATO:0000462), the "inheres_in" relation from the OBO
Relations Ontology, the TAO term for "basihyal cartilage" (TAO:0001510),
the "exhibits" relation from the PHENOSCAPE ontology, and the TTO term
for Siluriformes (TTO:1380). This is shown below.

<javascript> TTO:1380 PHENOSCAPE:exhibits
PATO:0000462^OBO_REL:inheres_in(TAO:0001510) </javascript>

In plain English, this translates to "Siluriformes exhibit absence in
organism which inheres in basihyal cartilage." The semantics of this
sentence are vague to say the least. Going by this methodology, it is
impossible to state that basihyal cartilage is absent in Siluriformes
without referring to *at least one* instance of basihyal cartilage.
Combining a quality *absent* with a *feature* through the *inheres_in*
property is very misleading in itself (ex: absence inheres in
cartilage), contorting the intrinsic semantics of the *inheres_in*
relation. These problems have been discussed in [Ceusters et
al](http://www.ncbi.nlm.nih.gov/pubmed/17369081) and [Hoehndorf et
al](http://www.biomedcentral.com/1471-2105/8/377). Both these
publications propose solutions to integrate these aberrant observations
with canonical definitions, without causing inconsistencies in reasoning
procedures.

<a href="Media:PhenotypesInPhenoscape.ppt" class="wikilink"
title="Media:PhenotypesInPhenoscape.ppt">Media:PhenotypesInPhenoscape.ppt</a>

<a href="Discussion_about_the_Absence_of_Phenotypes_issue"
class="wikilink"
title="Discussion about the Absence of Phenotypes issue">Discussion
about the Absence of Phenotypes issue</a>

Another issue specific to the Phenoscape project was raised by Paula at
the SICB workshop. Given that basihyal cartilage is absent in
Siluriformes, basihyal bone should be absent in Siluriformes as well.
This is because basihyal bone develops from basihyal cartilage. This may
be inferred by adding a new relation chaining rule shown below to the
OBD reasoner

**Rule:**$`\forall`$F1, F2, S: *absent_in*(F1, S) $`\and`$
*develops_from*(F2, F1) $`\Rightarrow`$ *absent_in*(F2, S)

This relation chain corresponds to the observation GIVEN THAT
Basihyal_Cartilage *absent_in* Siluriformes AND Basihyal_Bone
*develops_from* Basihyal_cartilage, THEN Basihyal_Bone *absent_in*
Siluriformes. This and other similar relation chains (as per identified
requirements) are to be implemented for the Phenoscape project in the
future. Strategies to deal with absent features in general are also to
be implemented in the near future.

Differences between the
<a href="The_exhibits_relation_conundrum" class="wikilink"
title="existing semantics">existing semantics</a> and
<a href="Relating_taxa_to_phenotypes" class="wikilink"
title="desired semantics">desired semantics</a> of the *exhibits*
relation need to be resolved to address this issue. Potential strategies
to implement the absence of features problem are discussed
<a href="Novel_reasoning_strategies" class="wikilink"
title="here">here</a>.
