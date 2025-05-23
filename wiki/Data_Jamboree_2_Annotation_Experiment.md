---
title: Data Jamboree 2/Annotation Experiment
permalink: wiki/Data_Jamboree_2/Annotation_Experiment
layout: wiki
tags:
 - Data Jamboree 2
 - Curation
---

### Background:

The curation experiment was given to five curators on the third day of
the <a href="Data_Jamboree_2/Agenda" class="wikilink"
title=" second data jamboree"> second data jamboree</a>. The goals of
the experiment were to assess curation consistency among a group of new
curators, and to identify areas of improvement in curator training,
ontology development, and software improvement.

### Participant Training:

Only one of the five curators had experience using Phenex prior to the
data roundup. Training for all curators consisted of:

- A hands-on, group curation exercise led and assisted by experienced
  curators given on the first day of the data roundup
- Two days of individual curation work on publications related to each
  participant's area of taxonomic expertise, with assistance from
  project personnel
- For reference, participants were given an
  <a href="Guide_to_Character_Annotation" class="wikilink"
  title=" Annotation Guide"> Annotation Guide</a> with examples of
  character types commonly encountered in the fish systematic literature

### Results:

A summary of results for each character is presented below, and a
comparison to the
<a href="Data_Jamboree_1/Annotation_Experiment" class="wikilink"
title=" first consistency experiment"> first consistency experiment</a>
given at the Data Jamboree I is presented in this <a
href="Data_Jamboree_2/Annotation_Experiment#Comparison_of_Consistency_Experiment_I_vs._II"
class="wikilink" title=" table."> table.</a> Additional notes on the
discussion of results with curators and advisors can be found <a
href="Data_Jamboree_2/Notes#Curation_consistency_experiment:_Review_of_Results"
class="wikilink" title=" here."> here.</a>

#### Character Summary and Suggestions for Improvement

*1. Presence or absence of intercalar: (0) present; (1) absent.3*

- Consistency: 5/5
- Summary: all curators annotated this character identically

*2. Opercle depth to width ratio: (0) less than two; (1) about two or
greater than two. Essentially, this character distinguishes between
those taxa with a short, relatively broad opercle and those with a tall
relatively slender opercle.2*

- Consistency: 1/5
- Summary of variable annotations:
  - The majority of curators used various size qualities (e.g.,
    increased width; decreased depth) to describe differences in shape.
- Suggestions to improve consistency:
  - Definitions of size terms need to be improved; also, size and it's
    children do not share a parent with shape.
  - Annotation of characters with detailed size information should be
    annotated to higher level (shape in this case).

***3.** Number of unbranched plus branched pelvic-fin rays: (0) 11; (1)
nine; (2) more than 11.3*

- Consistency: 3/5
- Summary of variable annotations:
  - Increased count used as quality term for state 2 by one curator;
    this is OK because parent is_a count
  - Incorrect entity chosen by two curators (pelvic fin actinotrichium
    instead of pelvic fin lepidotrichium)
  - Quality and Count left blank by one curator

*4. Basihyal: (0) present and ossified; (1) present and cartilaginous;
(2) absent.1*

- Consistency:
- Summary of variable annotations:
  - most curators recorded both presence and absence of bone and
    cartilage terms for each state
  - bone composition (cartilaginous vs. ossified) used by one curator
    for quality
- Suggestions and group discussion:
  - for state 2: basihyal cartilage absent implies basihyal bone absent
    (because the latter develops from the former)
    - in fact it can also be that the cartilage is absent b/c it has
      developed into the bone (completely ossified)
    - hence need to add that basihyal is absent too
  - graph view can be very helpful to visualize develops_from
    relationships

*5. Position of anterior margin of nasal: (0) falling short of lateral
process of mesethmoid (= lateral ethmoid wing of Weitzman, 1962); (1)
extending anteriorly to overlie or extend beyond lateral process of
mesethmoid.3*

- Consistency: 1/5
- Summary:
  - Incorrect entity (naris vs. nasal bone) used in post-composition
  - Monadic qualty incorrectly used rather than relational quality
  - Post-composed entity term chosen rather than approporiate
    pre-composed term
  - Relational structural quality used rather than relational positional
    quality
- Suggestions:
  - software should prevent filling in relative entities for qualities
    that aren't relational
  - full text search of the definitions would be very useful

*6. Number of hypurals in upper lobe of caudal fin: (0) four; (1)
three.2*

- Consistency: 2/5
  - Incorrect post-composition for entity (in various ways; see
    individual annotations below)
  - Quality and Count left blank
  - contained_in used for post-composition
- Suggestions:
  - display definitions for relationship types (contained_in vs.
    part_of)
  - hypural can also be "contained in" upper lobe of caudal fin

*7. Presence or absence of medially directed, spine-like process on
ventral surface of post-temporal: (0) present; (1) absent.3*

- Consistency: 3/5
- Summary:
  - post-composed entity incorrectly started with quality term
  - post-composed entity term lacking spatial information
- Suggestions:
  - Software should ensure that entity starts with a spatial or anatomy
    term if post-composed, not a quality

*8. Presence or absence of contact between frontal and pterotic: (0)
frontal and pterotic bones in contact; (1) pterotic excluded from
contact with frontal by sphenotic.3*

- Consistency: 5/5 for state 0; 4/5 for state 1
- Summary:
  - curator mistakenly(?) used same quality for both states
- Suggestions:
  - Record free-text information not used in annotation in the comments
    field (e.g., sphenotic needs to go into the comment field)

*9. Orientation of infrapharyngobranchial 1: (0) proximal tip anteriorly
directed; (1) proximal tip posteriorly directed.1*

- Consistency: 2/5
  - monadic quality term used incorrectly (related entity used in
    annotation)
  - less specific entity term used in post-composition
    (pharyngobranchial vs. pharyngobranchial 1)
  - spatial term incorrectly used as quality term
  - spatial term incorrectly used as related entity
- Suggestions:
  - software should prevent filling in spatial or monadic terms for
    quality if related entity field is filled.
  - if too complex to express the exact nature of the orientatin, then
    annotate quality as "orientation"

*10. Dermosphenotic (0) triangular; (1) triradiate; (2) tubular.1*

- Consistency: 5/5
  - Summary: all curators annotated this character equivalently
  - Discussion about approporiateness of tripartite for state 1

References:

1Hilton, EJ. 2003. Comparative osteology and phylogenetic systematics of
fossil and living bony-tongue fishes (Actinopterygii, Teleostei,
Osteoglossomorpha). Zoological Journal of the Linnean Society 137:1-100.

2Sanger, TJ and AR McCune. 2002. Comparative osteology of the Danio
(Cyprinidae: Ostariophysi) axial skeleton with comments on Danio
relationships based on molecules and morphology. Zoological Journal of
the Linnean Society 135: 529-546.

3Zanata AM and Vari RP. 2005. The family Alestidae (Ostariophysi,
Characiformes): a phylogenetic analysis of a trans-Atlantic clade.
Zoological Journal of the Linnean Society 145: 1-144.

#### Comparison of Consistency Experiment I vs. II

| Character \# | \# Participants with Completed Annotations (n=4; Exp. I) | % Consistency with Key (Exp. I) | \# Participants with Completed Annotations (n=5; Exp. II) | % Consistency with Key (Exp. II) |
|----|----|----|----|----|
| 1 | 4 | 100 | 5 | 100 |
| 2 | 3 | 0 | 5 | 20 |
| 3 | 3 | 0 | 4 | 60 |
| 4 | 4 | 0 | 5 |  |
| 5 | 3 | 33 | 5 | 20 |
| 6 | 4 | 0 | 5 | 40 |
| 7 | 4 | 50 | 5 | 60 |
| 8 | 3 | 33 | 5 | 100 |
| 9 | 3 | 0 | 5 | 40 |
| 10 | 2 | 50 | 5 | 100 |
|  |  |  |  |  |

#### Raw data from participants

- <a href="Media:Consistency-expt-II-rawdata.xls" class="wikilink"
  title="download excel file">download excel file</a>
