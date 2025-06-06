---
title: EQ for character matrices
permalink: wiki/EQ_for_character_matrices
layout: wiki
tags:
 - Curation
 - Informatics
 - EQ Annotation
---

Encoding evolutionary character matrices using the [EQ
format](http://www.bioontology.org/wiki/index.php/PATO:About) (PATO
formalism) currently presents some problems that may need to be
resolved. I will try to describe the issues here.

## Background

### EQ statements vs. character matrices

The EQ format provides a "phenotype statement" documenting the phenotype
of an individual organism (usually a genetic mutant). The anatomical
structure being described is represented by the Entity term chosen from
an anatomical ontology, and the aspect of that structure being described
is the Quality term, chosen from the PATO ontology. These phenotype
statements usually describe the value the mutant exhibits:

E="dorsal fin" Q="round" --\> This fish has a rounded dorsal fin.

Evolutionary phenotype descriptions are often formatted as a character
matrix. For a given set of species, a list of distinguishing characters
is formulated, and the species-specific value for each character is
entered into the matrix. In this situation, each character (column in
the matrix) represents an entity and attribute, and the character state
cells contain values. Here is a graphical depiction of the relationship
between evolutionary characters and the components of the EQ system:

<figure>
<img src="EQmatrix.png" title="EQmatrix.png" width="500" />
<figcaption>EQmatrix.png</figcaption>
</figure>

The character (a column header in the matrix) is composed of an Entity,
and a Quality representing an attribute (e.g. "shape"). Values for this
character are entered into the cells (e.g. "round"). So you can see that
the Q of EQ is represented in both the character and the character
state. When EQ is used to describe mutant phenotypes, typically only the
value is stated, since one can traverse back through the PATO hierarchy
to find ancestor terms representing attributes - "round" is a child of
"shape".

Clearly, evolutionary characters and character states can be represented
using an EQ system as mutant phenotypes are. However there is a major
difference in the two data models: the data formats being developed for
mutant phenotype EQ statements store only a list of phenotype value
statements, with no place to reference an independent character. So you
may have a data set like this:

| Genotype | Entity       | Quality |
|----------|--------------|---------|
| fish1    | dorsal fin   | round   |
| fish2    | dorsal fin   | lobate  |
| fish2    | dorsal fin   | red     |
| fish1    | pectoral fin | blue    |

If these fish are different species, you can see that there are 2 values
for the character "dorsal fin shape", 1 value for "dorsal fin color",
and 1 value for "pectoral fin color". But nowhere in the existing EQ
data formats is the character stored. We have to infer it from the PATO
hierarchy to generate a matrix like this:

| Species | dorsal fin shape | dorsal fin color | pectoral fin color |
|---------|------------------|------------------|--------------------|
| fish1   | round            | ?                | blue               |
| fish2   | lobate           | red              | ?                  |

So the problem is that the existing EQ system (and formats such as
[PhenoSyntax and
PhenoXML](http://www.fruitfly.org/~cjm/obd/formats.html)) only stores a
list of character states, and cannot group those states into characters.
Storing only character states would be perfectly adequate for most of
the data integration benefits provided by the PhenoScape project.
However, evolutionary data is often described in the character+character
state framework, and a few reasons why we may want to preserve this are
listed below. Possible solutions to this problem for evolutionary data
are: 1) Only storing character values and automatically generating
characters when a matrix is desired, or 2) Finding a way to code and
store EQ statements for both characters and character states.

## Possible solutions

### Automatically inferring characters from character states using PATO

PATO does not distinguish qualities representing values from those
representing attributes, except that values descend from attributes in
the hierarchy. But given an arbitrary value, it is not possible to
automatically infer the attribute it is a value for. Many values are
children of other values - for example, "bright blue" and "dark blue"
are children of "blue". You need to traverse up two levels to reach the
attribute "color". Also, some terminal terms in PATO are not values -
they are attributes for which no values are defined in PATO. Examples
are "acceleration" and "buoyancy".

<figure>
<img src="Patofragment.png" title="Patofragment.png" width="500" />
<figcaption>Patofragment.png</figcaption>
</figure>

In order to automatically generate a character matrix from EQ data in
Phenote, Attribute and Value slims were added to PATO. These slims are
categories which are applied to each term in PATO, so that software can
determine the use of each term. In the Phenote NEXUS-format exporter,
the list of phenotype statements is grouped into characters based on
whether they share a nearest common Attribute ancestor. Problems:

- In order for this to work, the Attribute and Value slims must continue
  to be maintained by curators as terms are added to PATO. However no
  one else seems to be using these slims at this time.
- A researcher may be interested in coding a character such as "fin
  morphology", with various species having values "lobate", "stubby",
  and "elongated". However, without a way to store the desired character
  attribute, the current Phenote NEXUS exporter would see these
  phenotypes as states for the separate characters "fin shape", "fin
  size", and "fin length", respectively ("morphology" is a deeper
  ancestor of these 3 attributes). Conversely, if the researcher was
  generating a matrix from a database of EQ statements by choosing an
  entity-attribute pair such as "fin morphology", what should happen if
  a given species has values for both "fin lobate" and "fin elongated" -
  i.e. would this be a different character state from another species
  which was only coded for "fin lobate"?
- The original publication may have valuable textual information
  describing the character, independent of particular character states.
  We may want a place to preserve this.

### Storing EQ statements for both characters and character states

It would be possible to store EQ statements for both characters
(Entity+Attribute) and character states (maybe just Value), either by
defining a custom data format or by extending PhenoXML and PhenoSyntax.
Probably, given a character such as "dorsal fin color", valid values
would only be PATO descendants of "color", such as "red" or "bright
blue". However this approach may have some problems as well:

- It would require development of a specialized data model and prevent
  the use of the current NCBO standards.
- Such extensions to the PhenoXML standard may not be desired by the
  current developers and users.
- If an ancestor-descendant relationship between attributes and values
  is desired, this coding would not be robust to future rearrangements
  of PATO (where a value may not descend from a particular attribute in
  the future, and so becomes an invalid statement).
