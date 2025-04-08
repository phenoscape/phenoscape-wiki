---
title: Knowledgebase mockups
permalink: wiki/Knowledgebase_mockups
layout: wiki
tags:
 - Informatics
 - User Interface
 - Mockups
---

## Grouping data by using an ontology tree view

### Phenotype results

This would be an enhancement to the results currently displayed on a
page like
<http://kb.phenoscape.org/phenotype/evo/TTO:10930/TAO:0000326/PATO:0000070/>

The nearest common ancestor term of the annotated taxon terms is used as
the root of the tree display. The only leaf terms displayed are those
with annotations. Internal nodes show the union of the annotations to
their descendant nodes.

<figure>
<img src="phenotype_ontology_tree.png"
title="phenotype_ontology_tree.png" width="700" />
<figcaption>phenotype_ontology_tree.png</figcaption>
</figure>

#### Comments

- From Paula: start off with taxon tree semi-collapsed (at genus level).
  *Starts semi-collapsed, but not yet at genus level*
- From Paula: Put the number of taxa for which there are annotations in
  parens behind, e.g., the genus name. *Tracked in FogBugz now*
- From Todd: can we avoid repetition of the entity (ie "caudal
  vertebra") if all the phenotypes concern that one entity, or are you
  listing it to allow for the possibility of subsumed entities as well?
  *yes indeed, to allow for subsumed entities*
- From Todd: show numbers of taxa with annotations in parens for
  collapsed entities *is this not the same as Paula's comment above?*
- From Todd (cosmetic): italicize species names *tracked in FogBugz*
- From Todd: will the names be links to other pages? *They are now.*

### Search summary results

This would be an enhancement to the Phenotypes results currently
displayed on a page like
<http://kb.phenoscape.org/search/anatomy/TAO:0000376>

The leftmost column is intended to represent a disclosable tree display.
The nearest common ancestor of the represented annotated anatomy terms
is used as the root of the tree display. Each anatomy term has a flat
list of the qualities annotated for it. *Don't pay too much attention to
the dummy numbers given in these results.*

Root anatomy term "infraorbital" collapsed:

<figure>
<img src="infraorbital_closed_ontology_tree.png"
title="infraorbital_closed_ontology_tree.png" width="600" />
<figcaption>infraorbital_closed_ontology_tree.png</figcaption>
</figure>

Root anatomy term "infraorbital" expanded:

<figure>
<img src="infraorbital_open_ontology_tree.png"
title="infraorbital_open_ontology_tree.png" width="600" />
<figcaption>infraorbital_open_ontology_tree.png</figcaption>
</figure>

Possible further enhancement to page capabilities - redisplay data on a
quality tree. The included results would be somewhat different.

Nearest quality ancestor collapsed:

<figure>
<img src="quality_closed_ontology_tree.png"
title="quality_closed_ontology_tree.png" width="600" />
<figcaption>quality_closed_ontology_tree.png</figcaption>
</figure>

Quality ancestor expanded:

<figure>
<img src="quality_open_ontology_tree.png"
title="quality_open_ontology_tree.png" width="600" />
<figcaption>quality_open_ontology_tree.png</figcaption>
</figure>

#### Comments

- From Paula: Rename 'Entity' 'Anatomy' as per other mockups for
  consistency <http://kb.phenoscape.org/search/anatomy/TAO:0000376>
- From Paula: swap column headings Entity-Quality on Quality tree table
  (below ' Nearest quality ancestor collapsed" text)
- From Todd (cosmetic): I'm not sure the alternating colors will be
  clear when there are multiple rows - those are most useful as an aid
  to follow horizontally across many columns within a row
- From Todd: would it be possible to collapse the quality column too (ie
  to "4 qualities" for a given entity? or "4 anatomical terms" for a
  given quality)?
- From Todd: Personally I think having the anatomical entity in the 1st
  column is a lot more useful than having the quality tree there.

## Display of citation and free-text basis for annotations

Here is a list of specific phenotype annotations resulting from a
search. There is an added "Source(s)" link next to each one. *The yellow
bubble is not part of the page.*

<figure>
<img src="phenotypes_and_sources.png" title="phenotypes_and_sources.png"
width="600" />
<figcaption>phenotypes_and_sources.png</figcaption>
</figure>

If the user clicks a "Source(s)" link, the citation information for a
particular taxon-phenotype annotation is retrieved and displayed in a
page overlay.

<figure>
<img src="phenotypes_and_sources_open.png"
title="phenotypes_and_sources_open.png" width="600" />
<figcaption>phenotypes_and_sources_open.png</figcaption>
</figure>

A particular taxon-phenotype annotation may have been asserted from more
than one publication:

<figure>
<img src="phenotypes_and_2_sources_open.png"
title="phenotypes_and_2_sources_open.png" width="600" />
<figcaption>phenotypes_and_2_sources_open.png</figcaption>
</figure>

#### Comments

- From Todd (cosmetic): Add more buffer to table cells, with more subtle
  boundaries between them - you don't want the cells to visually
  overwhelm the data text.
- From Todd (big issue): Showing the phenotypes makes me think we really
  need to list the reference point for them, since "increased size" is
  explicitly relative. One option would be to list the group to which
  the data matrix is being applied, so that "increased size" would be
  interpreted as relative to all catfish, or characiforms, or whatever
  the inclusive taxon was for that study.
- From Todd: Shouldn't the reference be specific to each annotation,
  rather than to each taxon? I would suggest making a little icon to
  represent source/publication, and displaying it immediately after the
  phenotype annotation in the same cell, kind of like a superscript
  footnote. And I wouldn't have guessed that I would see the original
  character state description from the name "Source" - before I clicked
  it, I assumed it was just going to show me the citation.
- From Paula: I think we need to add comments where there are some (if
  possible would be best not to see an empty comments field where there
  are not comments). E.g., in Siebert (1987), the matrix code "0"
  conflicts with the assessment of the condition in the text. So we'd
  like to leave the original coding in the matrix, but make sure that
  the comment appears to users. The comment is: "Gyrinocheilidae: text
  states pg 75 "An Ipb IV could not be positively identified as a
  separate element in my material." Fig 24 has "IpbIV?" This could go
  right below state and above curated by.

## Simple display of homology information

Anatomy pages can make use of homology information from the database to
list possible homologous terms. This mockup adds a list of homologous
terms to the term info panel. The user can click one of these term links
to go to the anatomy page about that term.

<figure>
<img src="homology_list.png" title="homology_list.png" />
<figcaption>homology_list.png</figcaption>
</figure>

#### Comments

- From Todd: include evidence string
- From Paula: I agree with Hilmar, that under 'Possible homologs' it
  should say 'accessory neural arch in TAXON' Then maybe a "evidence"
  button that links to the pub?
