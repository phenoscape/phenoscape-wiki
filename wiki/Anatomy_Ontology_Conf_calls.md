---
title: Anatomy Ontology Conf calls
permalink: wiki/Anatomy_Ontology_Conf_calls
layout: wiki
tags:
 - Anatomy
---

**Weekly anatomy ontology calls are held on Mondays, 1:15 pm - 2:15 pm
ET.**

## Feb 6, 2012

Review and discussion of proposed definitions, labels, and synonyms for
limb podium terms

## Jan 23, 2012

### Agenda

Nizar will give an update on the limb terms and definitions - see Google
docs AMAO-Appendicular and VAO-appendicular.

**Attending:** Nizar, Dave, Christina, VG, Erik, Terry, Paula, Wasila

### Minutes

**Nizar, discussion of AMAO and VAO terms:**

- Currently working on specific terms and higher level terms from AMAO,
  VAO, and CARO
- Also going to highest levels (e.g., anatomical entity) for review
- Created new OBO file that they can edit all three ontologies directly
- Will generate diff file ([using GO diff
  tool](http://galaxy.berkeleybop.org:8080/)) to keep track of proposed
  changes to VAO and CARO. Changes to AMAO will be preserved.
- Provenance: Nizar has been doing index search for original
  definitions;
  - Podium terms in original literature, defined by Haeckel in 1895.
    Refers to skeletal elements only
  - would prefer to reserve podium terms for skeletal only
- Terry: need to have a way to designate the limb segments as well that
  contain skeletal elements
  - Could have two terms: stylopodial segment of limb and stylopod
    skeleton
  - could also have stylopod as related synonym for two terms
    'stylopodium skeleton' and 'stylopodial limb segment'
- David: usability very important, at least include recent usage as a
  pointer to historical usage
- Terry: better to define regional limb terms by the skeletal elements
  contained within, because terms like "arm" are confused in the
  literature
- Nizar: similar problem with terms like cranial skeleton, axial
  skeleton, postcranial axial skeleton; his community wouldn't include
  cranial as part of axial skeleton
- may need to be defined differently across ontologies; or treat as a
  presentation issue: not necessarily that cranium doesn't have axial
  parts in it
- In defining limb terms encounter difficulty in defining terms by
  internal elements; when lose structures becomes difficult

**AMAO terms and curation**

- Nizar will write AMAO defs at level of archosaurs
- Paula: yes, and have terms done for curation of archosaur limb
  literature first
- will result in "uneven" ontology but need to focus effort with eye on
  curation

## Nov 29, 2011

### Agenda

Melissa will lead the call summarizing proposed updates and requests to
process terms related to the skeletal system in the Gene Ontology,
extending the work done at last year's skeletal anatomy workshop. These
terms will be integrated in VAO cross-product definitions.

**Attending:** Ceri, Yvonne, Terry, Melissa, Nizar, David

### Minutes

- <a href="Media:GOoverview.pdf" class="wikilink"
  title="Download Melissa&#39;s slides">Download Melissa's slides</a>
  (PDF)

<!-- -->

- Gene ontology - 5 new classes being proposed (see slides)
- develops_from vs. replaced_by relation: cartilage doesn’t develop into
  a bone element; it’s “replaced by” bone and incoming osteoblasts
- Endochondral ossification definition: doesn’t need to be mineralized
  to replace bone, so removed that clause
- perichondral definition – some ossification occurs off the periosteum
  but not adjacent to it, so worded as from the surface rather than
  adjacent to
- intratendonous ossification results in formation of ossified tendon
  \[TO DO:change primary label on VAO term from ‘intratendonous
  ossification’ to ‘ossified tendon’
- Relation for GO processes: “results_in_formation_of” or
  “participates_in”/”has_participants_in” \[input/output has
  participants in it\] so might not want to use participates_in -- need
  to define subproperties
- Ligamentous ossification: replacement ossification – there is a
  ligament model replaced by a bone model; could also say that within a
  ligament have metaplastic ossification – ligament cell becomes bone
  without dividing; probably have both going on in one skeletal element
- Terms for modeling vs. remodeling vs. maturation have community
  specific definitions:
  - clinical: bone modeling (maintenance), bone remodeling (injury)
    which might be normal response to injury and not pathological; bone
    maturation
  - David: comparative literature, especially for amphibs, refers to
    bone remodeling for change in morphology in ontogeny

## Nov 21, 2011 -- Taxonomy Ontology call

### Agenda

- Discuss VTO workflow and curation of taxonomic names

**Attending:** Peter, Wasila, Paula, Ben, Nizar, Hilmar

### Minutes

- VTO Tool takes taxonomies and puts them together
- Planning to use single tracker (VTO tracker - link\]
- Review of workflow for taxonomic groups (see slides)
- Pending AMTO from Paul, could use NCBI scaffolding to curate directly
  in VTO
- PBDB
  - "bulk" update grabs all chordate data; needs review by curator;
    would have list of species with invalid parents
  - Action item: Peter to post list of problematic taxa, which can be
    fixed if corrected by curators
  - "simple" update - curator provides list of names for VTO; only
    update is to names curator provides
  - PBDB is patchy, not a complete taxonomy; VTO update from PBDB gives
    new terms and path to root, but doesn't change what's already in VTO
- Plans
  - Nizar can create a basic amniote taxonomy based on standard
    references, put in excel for Peter to pull into VTO

### Slides

|  |  |
|----|----|
| <img src="TaxonomyOverview.png" title="TaxonomyOverview.png" width="400"
alt="TaxonomyOverview.png" /> **Overview of taxonomy curation in Phenoscape II** | <img src="FishWorkflow.png" title="FishWorkflow.png" width="400"
alt="FishWorkflow.png" /> **Detailed workflow for fish taxa covered by the Catalog of Fishes** |
| <img src="AmphibianWorkflow.png" title="AmphibianWorkflow.png"
width="400" alt="AmphibianWorkflow.png" /> **Proposed workflow for amphibian taxa (with input from amphbiaweb)** | <img src="AmnioteWorkflow.png" title="AmnioteWorkflow.png" width="400"
alt="AmnioteWorkflow.png" /> **Proposed workflow for amniote taxa** |
| <img src="PaleoWorkflow.png" title="PaleoWorkflow.png" width="400"
alt="PaleoWorkflow.png" /> **Proposed workflow for taxa extracted from paleodb** |  |

## Nov 7, 2011

### Agenda

- Addition of fin terms (available from TAO) to VAO for annotation of
  basal vertebrate phenotypes (add to tracker)
- Review of proposed updates to [cranial skeleton
  terms](https://docs.google.com/spreadsheet/ccc?key=0Aj8NJdyb-leqdDM0R3hTVTRHRExDVjRCSkZEbDc5N1E)
  (from recent work with John Lundberg)

**Attending:** Ceri, Terry, Yvonne, Melissa, Paula, Ben, Wasila, David

### Minutes

- **Addition of fin terms** (available from TAO) to VAO for annotation
  of basal vertebrate phenotypes
  - Melissa: terms outside musculoskeletal scope (e.g., dorsal fin) are
    available in UBERON. These are organism subdivisions rather than
    skeletal subdivisions
    - organism subdivisions- large portions with various organs/
      elements included as part of “chunk” or organismsum of parts don’t
      add up to what is seen on surface, not adquately represented in
      CARO yet
  - VAO scope is musculoskeletal, import ‘dorsal fin’ from Uberon and
    have “dorsal fin skeleton” be part_of
  - Don’t need to import all of Uberon, import single classes or
    specific vertebrate files, not all of it.
  - Can also use placeholder term in Vao which gets obsoleted and
    replaced with term imported from existing ontologies
  - Melissa: Ideally would import from Uberon but tools not there yet
  - Paula: Median fins don’t develop from fin buds, we have the
    develop_from relationship in TAO/ZFA, how to change relationship for
    VAO? change in all ontologies—add to tracker in Uberon—developing
    tools to see differences and populate ontologies from higher
    ontologies
- Review of proposed updates to **cranial skeleton terms** spreadsheet
  - Chondrocranium could be defined logically as restricted set of
    replacement elements that is not replaced by mineralized tissue
  - Paul: chondrocranium and neurocranium used interchangeably- a
    problem, disparity in different types of literature over time
  - Paul generally agrees with using chondrocranium for the
    splanchnocranium + neurocranium precursors as there is no term for
    the full chondrocranium
- Action item: everyone fill in relevant cells in cranial skeleton
  spreadsheet for their ontology
- Action item: Nizar and Paul to review limb and cranial skeleton
  spreadsheets

## Oct 17, 2011

### Agenda

- Review ["Podium
  terms"](https://docs.google.com/spreadsheet/pub?hl=en_US&hl=en_US&key=0Aj8NJdyb-leqdFdTaEJjNkMyUXR1SE1PSUNJc0gwcmc&output=html)
  GoogleDoc spreadsheet
- Pectoral and pelvic fin representation - see [CARO tracker
  item](http://code.google.com/p/caro2/issues/detail?id=5)

**Attending:** Ceri, Terry, Monte, Yvonne, Christina, VG, Melissa,
Chris, Ben, Wasila

### Minutes

- Proposed synonyms of podial terms (e.g., upper arm, crus etc…) see
  spreadsheet
- Arm and leg defined differently:
  - In MA, VAO, arm = forelimb stylopod + forelimb zeugopod
  - In FMA, arm = forelimb stylopod
  - In MA, leg = hindlimb stylopod + hindlimb zeugopod ; (leg not in
    VAO)
  - In FMA, leg = hindlimb zeugopodium
- Question: wrist/ankle = synonyms of forelimb mesopodium/hindlimb
  mesopodium?
  - Terry: no, Common usage of wrist includes joint- composed of
    multiple articulations, zeugopodial segments, specific tendons,
    ligaments, etc...
  - Wrist region might be better term to represent everything; parent
    is_a anatomical cluster
- CARO appendage: refer to pelvic and pectoral regions? Or just sticking
  out part?
- Terry to look into development of appendages and girdles
- 

### Minutes

## Oct 17, 2011

### Agenda

- "podium" terms (stylodpod, zeugopod, autopod) as limb segments/
  organism subdivisions vs. skeletal subdivisions
- documentation of discussions, references, and resources in ontology
  development

**Attending:** Wasila, Ceri, Yvonne, Monte, Terry, David, Paula, Chris,
Christina, VG, Paul, Ben

### Minutes

\_**Podium terms**

- In Uberon, FMA, and MA, podium terms are types of limb segments; in
  AAO, they are types of skeletal subdivisions
- Literature is also mixed (examples presented); Might be consequence of
  skeletal elements being the most discrete embryologically, but assume
  patterning of soft tissues is also present. Paul: most of his
  literature refers to skeletal only.
- Could keep stylopod and introduce "skeleton of stylopod" terms
  - Or 'stylopod skeletal element' term (part_of stylopod)
- Everyone to review Google doc spreadsheet "podium terms" for
  discussion next week
- Chris: terms for shoulders, wrists, joints vary in relationships to
  regions
  - adjacent_to vs. overlaps; overlaps seems more appropriate:
  - knee region overlaps stylopod + zeugopod
  - humerus is contained in the shoulder region, but not the entire
    humerus, so use overlaps relation
- Chris: FMA uniquely among AOs has girdle part_of limb; FMA:free limb
  equivalent to "limb" in other AOs
  - Terry: limb field developmentally gives rise to girdle (possibly)
  - Appendage is term that includes girdle with limb (=pectoral
    appendage or pelvic appendage for VAO)

**Term documentation**

- Chris: [GO
  refs](http://amigo.geneontology.org/cgi-bin/amigo/term_details?term=GO:0048909&session_id=4472amigo1318874633)
  - links from term to references and other links within GO Ref
  - ZFA has ZFIN virtual publication
  - Paula: will ask Todd about microattribution

## Oct 10, 2011

### Agenda

- 

**Attending:**

### Minutes

## Sep 26, 2011

### Agenda

- Full vs. partial synchronization of model organism and multi-species
  ontologies

**Attending:** Jim, Wasila, Yvonne, Monte, Paula, Chris, Terry,
Christina, VG

### Minutes

- Wasila: Currently, TAO duplicates all ZFA terms, meaning that every
  term in ZFA has a corresponding term in TAO; links to gene data.
- ZFA duplicates only zebrafish-applicable terms and only terms that
  might be needed for curation (e.g., some skeletal element terms,
  although applicable to zfish, not added to ZFA).
- Chris pointed out that a reasoner can do the integration between TAO
  and ZFA. Would lessen the work involved in synchronizing and wouldn't
  need to duplicate every ZFA term in TAO
- Reasoning: can bridging axioms handle this? Jim: bridging axioms can
  be generated from xrefs
- Jim: in the redesigned version of the KB, this will work

<!-- -->

- How to keep track of terms that don’t apply to zfish or tao? Don’t
  want to re-visit each time…. Need to have a diff file for each
  release…

<!-- -->

- Chris: Do you want branch-specific exclusion?
  - Probably not needed; not a big task to review newly added terms for
    inclusion/exclusion

<!-- -->

- doing subsets with the synch tool;
  - exclude from zfa (housed in tao)
  - exclude from tao (housed in zfa)
- Subset tag (=slim) – a tao subset that excludes the terms from zfa
- for each term in the ontology, check box in OBO Edit – would add
  subset line to ZFA has "exclude from TAO" subset; TAO has "exclude
  from ZFA" subset
- discussed creating separate subsets for different reasons for
  exclusion; decided it was better to begin simple with one subset

<!-- -->

- Paula: Is there a way to make a comment appear after subset in OBO
  format?
  - Chris: trailing qualifier can be used in OBO format - line or two of
    free txt, in {}; not sure if preserved in OBO-edit

<!-- -->

- Could also use a shared external file containing subset info, readable
  by Synch Tool

<!-- -->

- Jim’s time: 1-2 days of coding…. (working just on this…)

## Sep 12, 2011

### Agenda

- <a href="Collaborative_Phenotype_Annotation" class="wikilink"
  title="Annotation tool requirements">Annotation tool requirements</a>

## Sep 12, 2011

### Agenda

<a href="Semantics_of_phenotype_annotations" class="wikilink"
title="Semantics of phenotype annotations">Semantics of phenotype
annotations</a> (Jim)

- - Jim to describe query results on KB interface for ancestral state
    annotation

## Sep 5, 2011 No call (Labor Day)

## Aug 29, 2011

**Attending:** Monte, Terry, Chris, Wasila, Jim, Paula, Yvonne, VG,
Christina, Hilmar (first half)

### Agenda

- annotation tools for Phenoscape: requirements and the pros and cons of
  desktop vs. web-based annotation tools (Wasila)
- instance-based annotation model (Jim)
  - <a href="Semantics_of_phenotype_annotations" class="wikilink"
    title="Semantics of phenotype annotations">Semantics of phenotype
    annotations</a>
- full vs. partial synchronization (for next week?)

### Minutes

Jim led discussion on
<a href="Semantics_of_phenotype_annotations" class="wikilink"
title="Semantics of phenotype annotations">Semantics of phenotype
annotations</a>

## Aug 15, 2011

**Attending:** Chris, Paula, Wasila, Jim, Erik, Terry, Paul

### Agenda

- Chris will present on ontology modularization - [Download slides from
  ICBO
  2011](http://icbo.buffalo.edu/2011/slides/WOMBO/WOMBO2011-04-Mungall-et-al.pdf)
- Discuss need for complete vs. partial synchronization

### Minutes

## Aug 8, 2011

**Attending:** Terry, Chris, Wasila, Jim, Paula, Yvonne

### Agenda

Review Obo-Edit Synchronization Tool

[Download Sync Tool
plugin](https://www.phenoscape.org/wiki/Synchronization_Tool)

### Minutes

For obsoleted terms, give reason for obsoletion in comments field

**Synch tool review**

1.  Features and bug reports (already on request tracker)
    - indicate (by color) and filter obsolete terms
    - Conflicting data tab: synonyms not copied over
    - Missing terms: filter TAO terms with never_in_taxon links to D.
      rerio
2.  Some conflicting data will be ok. For example, a ZFA definition may
    begin with the broad genus-differentia definition shared with the
    corresponding TAO term, followed by zfish specific information not
    in TAO definition.
3.  To maintain needed differences between ontologies (e.g., differences
    between defs, relationships, synonyms), synch tool could interact
    with a local file that keeps track of differences so that curator
    doesn't need to review these in each synch session

**Long-term synch goals**

1.  Chris - use annotations to guide ontology synch. For example,
    vertebra 1 part_of Weberian apparatus in Danio rerio allows this
    relationship in ZFA and explains its absence in TAO.
2.  Could also make use of textual annotations for synchronization

**Working plan:** update synch tool with easy fixes and requests, and
reassess its use after one year

**Complete or partial synchronization?** Chris: instantiating everything
in TAO is probably not necessary (e.g., every term added to ZFA
currently gets duplicated in TAO). In some cases, ZFA would have very
specific terms defined based on zfish research but unknown in other
teleosts. Should still be able to search genes on these terms because
their parents are cross-referenced.

## July 27, 2011

### ICBO Anatomy Workshop Notes

- ZFA in charge of mapping to Cl
- TAO responsible for transitively linking to ZFA/Cl
- When MIREOTing should be recording version of ontology you are using
  (is this captured in release notes?); do filtered save, allow dangling
  refs.
- David importing is_a tree to root, assuming tree is reasoned
- Communication important, but also having clear lines of responsibility
  important
- If ZFA has two parallel classes infer the Cl; ask what asserted is_a
  links in Cl are not the correct inference for ZFA; which is_a links do
  I not re-infer in ZFA; down the line cache on a per term basis
- VAO only skeletal, UBERON will hold everything else
  (common/universal/non-species specific terms)
- ZFA needs to be doing intersections now. Strip them out for the
  database - they don't really need them do they?
- Treat Phenoscape like a special case of ZFA/ZFIN to understand how to
  do the hard queries that utilize the intersections
- TAO wants to import CARO and VAO; do filtered save as TAO; How do you
  add new imported terms?(David copy and pastes in, stripping out all
  relations?); Ideally plugin or webservice for OBOedit

## July 18, 2011

**Attending:** Terry, Christina, VG, Paula, Chris, Dave, Erik, Wasila

### Agenda

Discuss strategies for [cross-species ontology
synchronization](http://obofoundry.org/wiki/index.php/Strategies_for_cross-species_ontology_synchronization)

- multispecies ontologies and import vs. MIREOT
  - tool support for import/mireot in Obo-Edit
- species specific ontologies and macro x-refs
  - XAO/AAO plan
  - tool support for synchronization (Obo-edit; GO diff tool)

### Minutes

**Multispecies ontologies and import vs. MIREOT**

- [MIREOT](http://obi-ontology.org/page/MIREOT) lets you import a part
  of an ontology (e.g. so that we don’t get ‘tibia’ in the teleost
  ontology)
  - Mireot only developed in owl; applied mainly in cell ontology to
    date; easier than working with imports because can extract a
    submodule as basis for the import; variation of it in obo-edit where
    you save only the relevant terms (save is_a closure)
  - develop a subset file - need external script to keep subset
    synchronized
  - WD: Plans to develop a mireot module for obo? Roundtripping tool
    being developed for OWL
- another option: use ‘never in taxon’ designation instead of mireot;
  Put taxon info in VAO with never_in_taxon links; TAO/VAO e.g. –want to
  import only teleost specific;
  - never_in_taxon will be difficult for e.g., structures lost
    repeatedly in a clade
- Homology discussion
  - Don't add terms to VAO that are not required \[incomplete notes
    here...\]
- For now: just import/mireot the whole thing
- Better tool support needed

**Species specific ontologies and [macro
x-refs](http://obofoundry.org/wiki/index.php/Strategies_for_cross-species_ontology_synchronization#Provide_explicit_cross-species_axioms)**

- XAO/AAO plan originally involved merging AAO into XAO, with AAO terms
  being alt-ids ot XAO terms. But messy to deal with alt-ids and
  obsoleting terms in XAO
- New plan for [AAO/XAO alignment using
  xrefs](https://www.phenoscape.org/index.php?title=Anatomy_Ontology_Development_Plan#Amphibian_Anatomy_Ontology_.28AAO.29)
  - At end of year 1 would clone out AAO (keeping original AAO ids)
    terms not in Xenopus added back to AAO
  - OK to add VAO xrefs (with David) to AAO now and then
  - XAO would preferentially xref VAO terms where they are available
  - Primary location of xrefs would be in XAO now; the ssAOs hold xrefs
    to multispecies
- Another issue: where XAO to get non-skel terms; not ideal to xref ZFA
  - Uberon xrefs AAO; easier to do from purpose of synchronization
  - currently XAO xrefs ZFA - should they be maintained? Keep as
    historical record and leave as xrefs without defined semantics;
    don't rush to get rid of

WD: should AAO hold xrefs to Uberon or Uberon to AAO? CM: doesn't matter
which file it lives in - need a bridging file which contains axioms for
xrefs

- **XAO workflow**: if XAO need a new term, where to get them? Better to
  get term from higher level
  - in order of preference for a new term: AAO, VAO, Uberon, ZFA, create
    new term (no xref needed)
  - if AAO xrefs VAO, then VAO ID should be used preferentially over AAO
    id
  - non-skel terms not added to AAO until cloning

<!-- -->

- Should terms be directlly requested from Uberon? Could do that or on
  the other hand, UBeron will pick up new terms when it gets updated
- When pulling terms from above and definition is terrible, then start
  an external dialogue to fix it.

## July 11, 2011

**Attending:** Judy, Terry, Monte, Aaron, Christina, VG, Wasila

### Agenda

1\. Review anatomy ontology [development
plans](https://www.phenoscape.org/index.php?title=Anatomy_Ontology_Development_Plan)

2\. Alternative formalisms for inter-ontology links. From Chris email,
7/8/2011:

- equivalence (e.g. VAO:ligament equivalentTo Uberon:skeletal_ligament)
- subclass_of (e.g. EMAPA:islets_of_langerhans SubClassOf
  Uberon:islets_of_langerhans) note that EMAPA includes several classes
  called "islet of langerhans" and no single generic class, so we're
  forced to use subclass here
- equivalence given a taxon (e.g. MA:ligament EquivalentTo
  Uberon:ligament and partOf some NCBITaxon:10090)

3\. Discuss use of vertebrate anatomy [term tracker and mailing
lists](https://www.phenoscape.org/wiki/Ontologies#Anatomy_Ontologies)

4\. Issues raised by Chris:

1.  1.  alternate project meetings with calls where we invite other
        members of the obo-anatomy list?
    2.  make the agenda pages on the wiki publicly readable?

### Minutes

1\. Reviewed ontology development plan for year 1:

- multispecies ontologies (TAO, AAO, AMAO) will import VAO; cross
  references in VAO, TAO, AAO, AMAO to upperlevel ontologies unnecessary
  - **Action item**: Chris and Jim to discuss handling of imports in OWL
    version of ontologies
- single species ontologies (MA, XAO, ZFA) will maintain
  species-specific versions of terms, and cross reference VAO and
  appropriate multispecies ontology
  - Cross references in single species ontologies are specified as
    "equivalent in taxon" links by having a line describing the meaning
    of the xref in the header of ontology file; for example, ZFA has the
    following lines in the header:

`treat-xrefs-as-genus-differentia: CL part_of NCBITaxon:7955`  
`treat-xrefs-as-genus-differentia: TAO part_of NCBITaxon:7955`  
`treat-xrefs-as-genus-differentia: CARO part_of NCBITaxon:7955`

- macro-xrefs tralsated into owl: ZFA term is the equivalent of the TAO
  term
- Beware if two terms xref a single term: indicates that there is a
  duplicate term (error)

Aaron: XAO will be adding upwards of several thousand terms, many
embryological; will ref ZFA, VAO, CARO

- will be done manually, case by case basis, - are there tools for
  automating this?
- **Action item**: Chris and Jim to discuss tools for adding large
  chunks of ontologies to other ontologies - Paula suggests involving
  Jeff Bowes
- Chris: mapping issue here: don't xref at sibling level (e.g., XAO
  shouldn't xref ZFA), should inherit the term
- Long term goal for XAO is to follow import model;

Chris: need generic guidelines for when to subtype and when to merge

- when need to designate develops_from relationship that is not general,
  would create a subclass rather than add relationship at amphibian
  level
  - this is a shortterm solution; get latticy ontology, difficult to
    navigate

Wasila: way to handle taxonomically variable relationships as
annotations? Chris: difficult to edit a separate data table, which would
need extensions and way to view as ontology relationships

Terry: possible redundancy issue: Uberon has skeletal terms that VAO
doesn't yet; what should be xrefed?

Wasila: VAO is musculo-skeletal so xrefs should be made to VAO;
non-skeletal terms can be xrefed to Uberon

- Term addition to VAO is ongoing, but focus xref addition on limb/fin
  anatomy in first year

Decided to keep this time slot for project specific issues but there is
interest in participating in a general call; also could revisit using
this time slot after project work settles down

## June 13, 2011

**Attending:** Monte Westerfield, Paula Mabee, Judy Blake, Aaron Zorn,
Jeff Bowes, Wasila Dahdul, Jim Balhoff, Terry Hayamizu

### Agenda

- Judy:
  - Discussion on how to initiate the Amniote Anatomy Ontology for terms
    outside skeletal system
  - Report on status of unified anatomy \[emap + MA\]
  - What exactly is abstract mouse?
  - Clone MA, UBERON, unified mouse \[emap + MA\], or abstract mouse?
- Monte:
  - Discussion on moving ZFA to GO like model; possibility of
    implementing VAO import (so that XAO can just clone this VAO chunk
    when they also clone the rest of ZFA)
- Aaron and Jeff:
  - Discussion on setting up modular ontology model and specifics of
    importing model species-specific information (like devo stage)

### Action items resulting from call:

- Monte: Charge to the zfin group (from Monte) is to write up plan and
  potential problems
- Judy: Will send Jim contact for Amelia Ireland for diff
- All: short term goal to add xrefs to VAO to ZFA, XAO, MA
- Wasila: give VAO write access to other groups
- Wasila: find out how often UBERON gets updated **-- done WD
  6/25/2011**
- Wasila: Schedule weekly meeting to sort out what is happening in these
  AOs, beginning in July **-- done WD 6/25/2011**

### Minutes

- Wasila will demonstrate diffs between Uberon and MA using non-skeletal
  terms
  - e.g. 'naris' in mouse is 'part of nose'
  - e.g. 'naris' in uberon with lots of xrefs but missing relationship
    'part of' olfactory apparatus
  - not sure how often Chris updates Uberon
- Terry - developed adult Mouse Anatomy; working with Edinburgh group to
  update their ontology
  - 'unified mouse anatomy' not an official term, just a descriptor
  - Ed. developmental mouse anatomy developed 15 years ago in an effort
    to code mouse expressiondata. Built along lines of an atlas by
    kauffman and baird; partonomy; Used for expression annotation by ...
    for years now. Two parts: abstract mouse which is a time -inedpent
    collection of terms in a hierarhy not a dag; and from that extracted
    stage-dependent hierarchies. stage 28 is postnatal -- this is not
    developed at all. 8-10 years ago, a postnatal developed by jax. jax
    added is-a and expanded on stages. Examined all relevant ontologies
    in updating. Two entities (MA vs. developmental) not connected
    currently -- working to make it an anatomy ontology encompassing the
    whole of mouse development.
  - Q: re: timeline? Terry: within next two weeks could give clearer
    answer.
  - would like to work with rest of ao community to make it a resource
    that will best serve needs of community. It works for expression and
    for phenotype, but needs to work better for other communities. Have
    updated based on other working groups. Would like to work to update
    weak points.
  - Judy - Terry funded for small portion of time on issues relevant to
    project
  - Wasila - use mouse
  - Judy -- start with MA, great place to start. Talk with Chris to see
    where he last updated and worked with it.
  - Terry -- Uberon - made an effort to take into consideration only
    things that are shared - not less valuable for it; structurally less
    consistent than mouse; mouse is lacking becuase of roots in ed
    anatomy and purpose for expression -- so the high level structure is
    a partonomy; first level division into regions, then into organ
    systems, etc. Need to think about primary goals of new ontology.
    Where along tree does it no longer serve amniotes or chickens?
  - Some avian terms are already in uberon -- use mixed approach. Also
    uberon follows more of a is_a approach;
  - MA, Uberon, VAO, AmAO are all separate right now; good documentation
    of proposed changes;
- Judy: suggestion -- all work together on one aspect at a time - start
  with limb/fin
- Terry: Historically for MA, when significant changes made, to a
  section in response to some input; not a constant stream of changes;
  structurally and in terms of big picture, not changes often. Need to
  do in coordination.
- Wasila: Conclude -- need mixed approach

<!-- -->

- Monte:
  - Need to improve ways of synchronizing zfish ontology with vao,
    uberon, etc. Met with db admins etc. to discuss future re:
    ontologies and new mechanism to stay in synch. Potential problem is
    that lead curator out on maternity leave, so people he discussed it
    with not necessarily in charge, but they understood basic issue.
    Charge to the zfin group (from Monte) is to write up plan and
    potential problems. Briefly -- problem how to grow two ontologies
    grow in synch. Big concern that curators have is if they become
    dependent on outside group such as Phenoscape, there could be
    changes made without consideration for the implications of zfin.
    Also, term request brokerage rights need to be grant to zfin. Need
    to work out sop for how updates are made.
  - Concern how we represent developmental staging. Start and stop times
    in same db table. If bringing in terms from outside resource, will
    break the devo and it will have to be moved to an outside table.
    This has implications for xao. If xao is dependent on zfin, this
    will take some time.
- Aaron: best way to go is to clone zfa. Have to develop ways to import
  VAO.
- Jeff: Inheritance structure?
- Wasila: Yes, direct links
- Jeff: inheritance from next highest ontology? correct?
- Wasila: Yes, go up to next higher level ontology.
- Jeff: Given current architecture, not hard to do. However concerns
  about changing higher level terms and effects on lower level terms.
- Monte: talked about how zfin does with go currently - via diffs list -
  not overly onerous - but have to have sop - can run checks on
  reasoning, but human will have to fix a couple of things
- Judy - -yes
- Aaron: VAO not complete for all organ systems....how does this work?
- Jeff: This is ok -- for terms that exist in VAO, we can show as
  inherited.
- Jeff: Development not taken into account in higher-level ontologies.
  Have to have a way to associate development with terms. Just show
  which terms are inherited and maintain just as we do now.
- Aaron: Will clone vao and zfa terms and keep xrefs. When we transition
  to other system, can track what we are importing.
  - In short term, clone vao terms into xao - ok?
- Short term goal: Add xrefs to VAO to ZFA, XAO, MA
- Judy: weekly meeting to sort out what is happening in these anatomies?
- Wasila: yes, it would be useful
- Aaron: jamboree approach --
- Judy: Even a 1/2 hour check up
- Wasila: Even a open weekly call
- Judy: open up wiki for agenda building and notes
- Aaron re: data jam: 22 Aug-26 Aug; Erik S for 5 days
- Paula: Most efficient way to add xrefs to VAO to zfa etc.?
- Monte: ZFA and XAO etc. need write access to VAO
- Paula: Jim -- how to get this diff file automatically generated?
- Judy: Will send Jim contact for Amelia Ireland for diff
- Wasila: Will give write access to VAO to other groups. Will be making
  lots of changes over next two months.
- Paula: How coordinated in GO?
- Judy: Webex every/most mornings by the GO development team, share
  screen and work together ---additions at leaves easy; others assigned
  to people; coordination - big branches worked on by whole group
- bowes@ucalgary.ca and terry to be added to email list; Wasila will
  send out notes
