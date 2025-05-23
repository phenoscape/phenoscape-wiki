---
title: Phenoscape use cases
permalink: wiki/Phenoscape_use_cases
layout: wiki
tags:
 - Informatics
 - Use Cases
redirect_from:
 - wiki/Web_application_use_cases
---

# For South Dakota

## UI functionality related to identifying and mapping evolutionary changes based on mutant phenotypes

### Identify evolutionary phenotypes that match an input phenotype

**Motivation**

**Example**

**Input**

- A phenotype description - e.g. input some entity and/or some quality.

**Output**

- A list of annotations from the database which match that entity and
  quality, with taxon.

# Full List

## 1. Identify zebrafish candidate genes for an evolutionary phenotype (ranked \#1 by TJV and PM)

### Motivation

To obtain one or more candidate genes for an evolutionary change in
phenotype, one would like to know which genes, when perturbed in a model
organism, give rise to a "similar" phenotypic difference between
wildtype and mutant genotypes.

### Example

User observes evolutionary variation among fishes in the size of the
ceratobranchial 5 bone. User queries Phenoscape for matching mutant
zebrafish phenotypes using Entity = Ceratobranchial 5 \[from TAO\] and
all qualities pertaining to attribute ‘size’ \[from the PATO\]. The
response is a list of zebrafish mutants and their phenotypes, along with
the associated genes, and possibly gene expression images, in this case
for genes such as sox9a, since there is a size reduction in
ceratobranchial 5 in the mutant line sox9ahi1134.

### Input

A phenotype search specification: entity (TAO), quality (PATO). Option
to match exactly or to match descendant terms (as in quality "size",
above). \[Also, option to match ancestral terms a node or two up will be
frequently desired. E.g. if a search yields no phenotype matches to
"ceratobranchial 5 bone", the user may want to search "ceratobranchial
bone" (Is_a parent, one node up), "ceratobranchial 5 cartilage"
(develops_from relationship), "Pharyngeal arch skeleton (Part_of
relationship). even pharyngeal arch (more nodes up). User will want to
visualize the ontology simultaneously in order to make decisions about
what nodes might be informative/how to proceed in a search.
--<a href="User%3APmabee@usd.edu" class="wikilink"
title="Pmabee@usd.edu">Pmabee@usd.edu</a> 15:50, 18 August 2008 (EDT)\]

### Output

A list of ZFIN mutant identifiers with matching phenotype(s) of each,
associated gene(s), perhaps gene expression images (or links to).
\[Needs analysis workshop identified "Downloadable reports of query
results (e.g. candidate genes; comparative phenotypic data)" as a
priority --<a href="User%3APmabee@usd.edu" class="wikilink"
title="Pmabee@usd.edu">Pmabee@usd.edu</a> 18:15, 18 August 2008 (EDT)\]

## Use cases related to identifying and mapping evolutionary changes based on mutant phenotypes

### Identify evolutionary changes that match the phenotype of a zebrafish mutant (ranked \#2 by TJV & PM; see two other similar mapping use cases, also ranked \#2)

**Motivation**

It would be of interest to identify phenotypic variation among wild
species that could plausibly arise from changes in the same gene that is
perturbed in particular zebrafish mutant.

**Example**

User observes a reduction in number of branchiostegal rays in a
zebrafish mutant for the gene endothelin-1. The user wants to know
whether branchiostegal ray number is variable among fish species, and if
so, what is the pattern of change across fish evolution. User queries
Phenoscape using Entity = Branchiostegal rays \[from TAO\] and all
qualities pertaining to attribute ‘count’ \[from the PATO\]. Phenoscape
returns a list \[just a
list?--<a href="User%3ATjvision" class="wikilink" title="Tjvision">Tjvision</a>
12:40, 15 August 2008 (EDT)\] of taxa and phenotypes. The user would see
that all cypriniforms, including zebrafish, have three branchiostegal
rays, but other fishes, including close ostariophysan relatives, have
higher and lower numbers. \[Better to be able to return (default)
phylogeny with mapped character state changes
--<a href="User%3APmabee@usd.edu" class="wikilink"
title="Pmabee@usd.edu">Pmabee@usd.edu</a> 16:00, 18 August 2008 (EDT)\]

**Input**

A phenotype search specification: entity, quality, etc. Option to match
exactly or to match descendant terms (as in quality "count", above). \[
Also, option to match ancestral terms a node or two up as per above use
case --<a href="User%3APmabee@usd.edu" class="wikilink"
title="Pmabee@usd.edu">Pmabee@usd.edu</a> 16:02, 18 August 2008 (EDT)\]

**Output**

A list of matching evolutionary phenotypes and the taxon for each. \[A
list is too crude - the phenotypes should be phylogenetically mapped as
in the use case below
--<a href="User%3ATjvision" class="wikilink" title="Tjvision">Tjvision</a>
12:40, 15 August 2008 (EDT)\]

### Map changes of an evolutionary character on a phylogeny (ranked \#2 by TJV & PM; see two other similar mapping use cases, also ranked \#2)

**Motivation**

After observing phenotypic variation among species in a given trait (as
in use case <a
href="#Identify_evolutionary_changes_that_match_the_phenotype_of_a_zebrafish_mutant"
class="wikilink" title="above">above</a>), the user wants to know what
the pattern of evolution of this trait has been.

**Example**

The user observes variation in number of branchiostegal rays across taxa
from above. They prompt Phenoscape to map the character changes on a
phylogeny. From this they can see that all cypriniforms, including
zebrafish, have three branchiostegal rays, but other fishes, including
close ostariophysan relatives, have higher and lower numbers.
Specifically, reduction in number has occurred multiple times;
solenostomids and syngnathids (ghost pipefishes and pipefishes),
giganturids, and saccopharyngoid (gulper and swallower) eels have the
fewest branchiostegal rays.

**Input**

A list of taxa and their phenotypes for a previously searched character
specification. A phylogenetic tree including the taxa of interest.
\[There should be trees internal to the system. And I think this should
simply be combined with the previous use
case--<a href="User%3ATjvision" class="wikilink" title="Tjvision">Tjvision</a>
13:02, 15 August 2008 (EDT)\]

**Output**

A graphical representation of the phylogenetic tree (cladogram). The
branches are colored to represent reconstructed ancestral states of the
given character values (or ambiguity) using, e.g. parsimony. The
phenotypic data matrix is shown at the tips.

### View every change in an anatomical entity mapped on a tree (ranked \#2 by PM with two other similar mapping use cases, also ranked \#2)

**Motivation**

The user may be interested in how a particular structure has evolved,
without knowing what types of changes have occurred in that structure.
It would be useful to view the pattern of evolution of all species
phenotypes involving that structure, visualized on a phylogeny as in
<a href="#Map_changes_of_an_evolutionary_character_on_a_phylogeny"
class="wikilink"
title="#Map changes of an evolutionary character on a phylogeny">#Map
changes of an evolutionary character on a phylogeny</a>. \[If multiple
structures are examined, this could feed into a "generate me a NEXUS
file" use
case--<a href="User%3ATjvision" class="wikilink" title="Tjvision">Tjvision</a>
13:20, 15 August 2008 (EDT)\] \[Narrowed searches (e.g. from
E="Branchiostegal rays", Q="all" to Q="count" are equivalent to Use
cases "Map changes of an evolutionary character on a phylogeny" and
"Identify evolutionary changes that match the phenotype of a zebrafish
mutant" --<a href="User%3APmabee@usd.edu" class="wikilink"
title="Pmabee@usd.edu">Pmabee@usd.edu</a> 17:33, 18 August 2008 (EDT)\].
A user may also want to broaden a search (e.g., to "E=dermal bone") in
the cases where the search results are
null--<a href="User%3APmabee@usd.edu" class="wikilink"
title="Pmabee@usd.edu">Pmabee@usd.edu</a> 16:35, 18 August 2008 (EDT)\]

**Example**

A biologist is interested in the parietal bone. She chooses this term
from the anatomy ontology and then views a phylogeny displaying all
reconstructed character transitions involving the parietal as an entity.

**Input**

An anatomical term from an anatomy ontology. A (user supplied or
built-in) phylogeny containing the species of interest.

**Output**

A display of the phylogeny mapping changes for each phenotypic
character. (Possibly a listing of all phenotypes for each species which
contain the entered term as an entity).

## 3. Comparison of genetically and evolutionarily correlated characters

### Motivation

For phylogenetic systematics, one would like to know if two or more
characters show phylogenetic correlation due to an underlying
genetical/developmental correlation. One way to address this is to
determine if changes to both (all) those characters are found in a
single-gene zebrafish mutant. \[The reverse of this use case can be
imagined--<a href="User%3ATjvision" class="wikilink" title="Tjvision">Tjvision</a>
12:55, 15 August 2008 (EDT)\]\[agree with
Todd--<a href="User%3APmabee@usd.edu" class="wikilink"
title="Pmabee@usd.edu">Pmabee@usd.edu</a> 16:03, 18 August 2008 (EDT)\]

### Example

The user observes a suite of changes in the size of the dentary,
maxilla, ceratohyal, and opercle bones that support the monophyly of a
particular clade. The user queries the system for zebrafish mutant
phenotypes in which two or more of the above anatomical terms are used.
Phenoscape returns sox9ahi1134, in which the the dentary, opercle, and
maxilla bones are reduced in size relative to wild-type, whereas other
bones are relatively unaffected. \[This seems like a variant on the
first use case with multiple Es and no Qs, so perhaps these can be
combined
--<a href="User%3ATjvision" class="wikilink" title="Tjvision">Tjvision</a>
12:55, 15 August 2008 (EDT)\]

### Input

Multiple phenotype search specifications: entity, quality, etc.,
representing the evolutionary character changes. Option to match exactly
or to match descendant terms (as in quality "count", above).\[Also,
option to match ancestral terms a node or two
up.--<a href="User%3APmabee@usd.edu" class="wikilink"
title="Pmabee@usd.edu">Pmabee@usd.edu</a> 16:04, 18 August 2008 (EDT)\]

### Output

A list of ZFIN mutant identifiers and associated genes which are
associated with phenotypes matching 2 or more of the search criteria.
\[The output should at least be a matrix of genes against phenotypes
--<a href="User%3ATjvision" class="wikilink" title="Tjvision">Tjvision</a>
12:55, 15 August 2008 (EDT)\] \[Needs analysis workshop identified this
"Correlation matrix of traits" as a high (#2) priority
--<a href="User%3APmabee@usd.edu" class="wikilink"
title="Pmabee@usd.edu">Pmabee@usd.edu</a> 18:10, 18 August 2008 (EDT)\]

## 4. View values for a particular character for a set of species with some value for another character (ranked equivalently with one other use case)

### Motivation

A particular phenotype change may have evolutionary consequences for
another aspect of phenotype. This may be because they are linked via
developmental or physical constraints, or are related through their
effect on natural selection.

### Example

User observes a number of species missing the parietal bone and notes
that these species are also generally small in size. To determine the
generality of that conclusion, the user searches for all species in the
database which lack the parietal bone and requests the body length value
for each. \[Is this not also or alternatively done with zebrafish mutant
data?--<a href="User%3ATjvision" class="wikilink" title="Tjvision">Tjvision</a>
13:12, 15 August 2008 (EDT)\]

### Input

A phenotype search specification for the phenotype to match. A second
phenotype search specification for the attribute for which to search for
values.

### Output

A table containing, in each row, the name of the taxon matching the
first entered phenotype, the value of the first phenotype (included
under the assumption this may vary), and the value of the second
phenotype.

## 4. View all species with multiple phenotypes matching a condition

### Motivation

To find taxa (or mutants) matching complex phenotype descriptions. <a
href="This_begins_to_really_take_advantage_of_ontological_reasoning--[[User%3ATjvision"
class="wikilink" title="Tjvision">Tjvision</a> 13:16, 15 August 2008
(EDT) \]\]

### Example

A biologist wants to list all the species that have lost more than one
bone. Or more specifically, all species that have lost more than one
bone in the head.

### Input

A phenotype search specification, with constraints on the entity term
such as "is_a term1" and "part_of term2". The threshold number of
annotations matching the phenotype required to include a taxon.

### Output

A list of taxa (and/or mutants?) and their phenotypes matching the input
criteria.

## 5. Find morphological hot spots

### Motivation

Some parts of anatomy may evolve rapidly relative to others. These can
be identified as those that exhibit many evolutionary changes in
phenotype. This could be a simple metric like finding anatomical terms
that exhibit many different value states for characters. A more complex
analysis might perform ancestral state reconstruction for every
character in the database, and return the entity terms involved in
phenotypes with the most transitions. \[Quality terms also of
significant interest - is size, shape, or presence/absence the most
common change in a particular clade? How does frequency of different
types (size, shape, qualitative) compare across clades? compare between
clades and mutants? --<a href="User%3APmabee@usd.edu" class="wikilink"
title="Pmabee@usd.edu">Pmabee@usd.edu</a> 16:25, 18 August 2008 (EDT)\]

\[Are there other general properties of interest that are easily
measured? Slowest evolving, most/least evolutionary data available,
affected by most/least mutants, etc\].

### Example

The user wants to know whether structures that evolve rapidly share any
genetic commonality. User obtains a list of rapidly evolving structures
using this query, and then performs further analyses of those
structures.

### Input

All phenotypes in the database.

### Output

A list of anatomy terms exhibiting the highest number of phenotypes or
changes, depending on the metric.

## 6. Genetic or evolutionary modules: discovery and testing

### Motivation

Some parts of anatomy may be developmentally integrated, sharing common
genetic pathways. Structures that are identified as sharing common
developmental genes and/or pathways may be grouped as a possible module;
this assemblage of entities can be mapped on phylogeny to see the level
of constraint on its parts (i.e. whether it is evolutionarily conserved
across, e.g. more nodes than one would expect from a randomly assembled
group of entities). Genetic module discovery mechanism unclear.

### Example

A user may want to know whether some a priori group of entities
constitute a module (testing). User may also want to know whether
modules exist and what constitutes them (discovery)

### Input

All phenotypes in the database.

### Output
