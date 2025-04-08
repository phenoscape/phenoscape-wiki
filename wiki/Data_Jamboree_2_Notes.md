---
title: Data Jamboree 2/Notes
permalink: wiki/Data_Jamboree_2/Notes
layout: wiki
tags:
 - Curation
 - Ontology
 - Taxonomy
 - Informatics
 - User Interface
redirect_from:
 - wiki/Data_Jamboree_2/Taxonomy
---

## User interface

### User interface demonstration

DATE? SUNDAY MEETING OR DO THESE NOTES ALSO APPLY TO MEETING WITH
INDIVIDUALS IN PAIRS ON MONDAY/TUESDAY/WED?

- Visualization
  1.  Jim Balhoff suggested enabling drill down from higher taxa to
      lower ones. Typically, query for annotations will yield more
      results at higher levels in the taxonomy. Drilling down into the
      lower levels will serve to prune the results and narrow down to
      users' exact requirements. Monte Westerfield, and Paula Mabee
      seconded.
  2.  Mark Sabaj suggested using a fish landscape with different
      predefined areas for visualization of results and guiding the
      search. Paula Mabee and John Lundberg approved.
  3.  Todd Vision suggests displaying only those nodes of a taxonomy
      that have been annotated
  4.  Judith Blake suggested using Cytoscape to browse through various
      nodes in the tree
  5.  Monte Westerfield suggested linking phenotypes to genes
  6.  Todd Vision suggested character correlations

<!-- -->

- Querying
  1.  Todd Vision suggested using auto composition of search terms
  2.  Monte Westerfield suggested using Boolean combinations of query
      parameters. Seconded by Judith Blake

<!-- -->

- option for hierarchical indexing of results (taxonomy, phylogeny, but
  also anatomy ontology)
- mapping characters on a tree: multiple phenotypes may match any
  particular query
  - map to different colors for indicators? use numbers as indexes?
  - mapping phenotypes onto trees cannot typically reconstruct character
    state changes, and hence traditional visualizations may be
    misleading?
- ability to prune species with no data (values) for export
- search interface: ability to combine taxon/entity/quality
  specifications (and, or, not)
- graph navigation: Dbgraphnav, Cytoscape
- clickable fish image for starting navigation
- most common entry point is likely to be a simple one-field form for
  entering terms
- phenotype query prototype: how do I get from here to the genes?
- ability to see correlations between phenotypes

MGI batch query demo

- users don't use complex query forms
- auto-detect type of input tokens
- allow download in different formats
- computationally savvy users
- pre-written SQL as available from GO website

### User interface strategy

- Most common entry gateways: search by
  - taxon
  - gene (from ZFIN)
  - anatomical entity
- Use case: find evolutionary phenotypes that match a mutant ZFIN
  phenotype
  - Query by phenotype, result is species and ZFIN mutants that have
    matching annotations
  - Alternatively, query by phenotype profile (several phenotypes)
    - This could be retrieved by ZFIN mutant rather than typing them all
      in
- Inverting this use case: find ZFIN mutants for a set of phenotypes
  that differs between two taxa
  - Query by two taxa, pull out all phenotype annotations that aren't
    annotated to both taxa (each of which may be a clade)
  - User can remove phenotype annotations from that result to create the
    search profile
- Use case: find matching taxa and/or genes for a phenotype or phenotype
  profile
  - Query by anatomical entity to retrieve matching phenotypes
    (\[Q\]ualities, essentially)
  - Build phenotype profile from that (choosing or removing phenotype
    annotations)
- Summarization of results:
  - Number of matching taxa, ZFIN genes, publications
- Search by anatomy term
  - obtain the qualities (and entities if query is higher-level) for the
    query term
  - use this to be build query profile for obtaining matching ZFIN genes
- Search by taxon:
  - results in phenotypes annotated to this taxon
  - list of publications, possibly as a secondary result after narrowing
    down phenotype list by anatomy term
  - should be able to see where in the tree the currently selected taxon
    is
- Search publications:
  - Search by author, by taxon, by anatomical term
  - Search by identifier (doi)
- Search by ZFIN gene (or mutant)
  - Results in phenotypes annotated to this mutant
  - Use these to retrieve publications describing such phenotypes
    (regardless of taxon or gene)
  - Obtain the number of these phenotypes that are used for evolutionary
    annotation (i.e., annotated to - presumably normal - taxa)
- Summarizing data per publication
  - number of taxa and/or anatomical entities or phenotypes matching the
    original query, compared to overall number of taxa or anatomical
    entities or phenotypes

### Feedback and Suggestions on proposed Phenoscape UI

- Data cube like representation to represent taxa, phenotypes, and genes
  on three dimensions. This should allow combinations of two of the
  three parameters to be displayed at any given time(Rick Mayden)
- While looking for gene-phenotype associations, display ALL phenotypes
  the gene is associated with IN ADDITION to the phenotypes of interest
  (Rick Mayden)
- Term Information area for a selected term can be used to display all
  synonyms (dbxrefs?) and misspellings (Rick Mayden)
- In publication search results, indicate whether the publication was
  curated or not. If curated, display the details of curations such as
  curator's info, date curated, and importantly, versions of the
  ontologies that were used in the curation process (Mark Sabaj, Rick
  Mayden)
- Provide external links to other morphological databases such as
  MorphBank, MorphoBank etc (Rick Mayden, Mark Sabaj, Terry Grande, Eric
  Hilton)
- Enable search for related entity to the phenotype (Eric Hilton)
- While displaying publications, include a link to Authors' page and if
  possible, links to related people (Terry Grande)
- Provide links to images (Terry Grande)
- Group phenotype query results by taxa. Higher taxa should be
  expandable to display lower taxa (Paula Mabee, John Lundberg)
- Display result distributions among taxa when displaying results from
  phenotype queries (Paula Mabee)
- Group results by author, publication date etc while displaying
  publications (Paula Mabee)
- Group annotations by author, annotation date (Paula Mabee)
- Allow taxon/gene/phenotype combinations for querying (Paula Mabee)

## Taxon Concepts subgroup meeting (Monday, Sept. 29, 2008)

(Present: Peter Midford, Paula Mabee, Todd Vision, Wasila Dahdul, Hilmar
Lapp, John Lundberg, Suzi Lewis, Judy Blake)

Synonym scanner is working well but will never be perfect because CoF
doesn't list every synonym in existence (because they may not detect
every use in literature, or maybe deemed a name not worthy of addition
as synonym)

TJP (TV?): Have we checked requested taxa not in CoF against UBio? -
that would provide an LSID that could provide a dbxref to anchor the
taxon

Addition of synonyms not in TTO: currently Peter must add by hand.

Need to track - Association between synonym, person who requested and
publication? - Not being tracked right now.

JGL: We don't want to give this to CoF because these synonyms are picked
up in morphological or phylogenetic studies. These names that appear and
we flag as synonyms to valid names in CoF are not names coming out of
taxonomic research; these are mistakes: OCR, typographical mistakes of
author, or author mistakes of species in wrong genus.

Seems we should track all of this in database?

We want: - author year of the reference (right now it's in comments) -
want in a searchable context - does CoF have a database of publications?

PM: ed publication information (DOI, SCSI) -CoF has an internal
reference - We also need to record the full citation ourselves (name,
year, unpublished dissertation...)

Peter: dbxref from CoF can be added to TTO; OBO ontologies are
structured to hold dbxrefs, whole references in any structured way.

synonym reference - how should it be handled?

SL: synonym xref can be a person (initials)

to summarize: full text ref would be in db; ontology would have a
pointer to that

Peter: need interface to the db; won't be visible to obo-edit - make the
dbxref a url link to URI

TV: We need a universal place to resolve that URL

PM: synonym types necessary? misspellings; narrow etc...

Peter: Hoping we can scan stuff in from CoF

JGL: see ANSP collection search: type in a type specimen name and it
pulls in the CoF ref need CoF identifier; CASspec?

PM: who should do this?

JGL: why can't curator do this?

PM: too much time; can be done in bulk

Peter: synonym types: - current vocab is exact, related, broader,
narrower - all synonyms currently are related (the weakest relation). -
we will want misspelling to be even weaker than related; - distinguish
between published synonomy vs, curator made decision

HL: weighing how trustworthy the evidence vs. designation of
weak/strong; to HL, misspelling is a strong exact synonym not weak

PM: are misspelings the only exact synonyms?

TV: not critical to have the types of synonyms; just use related

all in agreement (misspellings will be taken as exact, other taxonomic
synonyms use related).

### Hilmar's notes

There are taxonomic names that are found in publications and are absent
from TTO.

- These are usually synonyms of existing taxonomic definitions.
- Curators file TTO synonym term requests for those missing terms,
  indicating what the currently valid taxon is
- Based on a brief survey, some of these synonyms are in fact contained
  in the latest CoF update, but many are not.
- Resolution against uBio has not been attempted yet.

Evidence for synonym to current name assignment needs to be recorded.

- OBO format allows dbxref for the synonym, which is used for storing
  the reference, such as the curator (e.g., pers. comm.)
- Also need unique URLs and GUIDs for publications so that these can be
  referenced as dbxref.
- OBO edit allows typing in those references, but doesn't allow
  hyperlinking to a display of the source.
- Many of these publications could be imported from CoF, which maintains
  a database of publications with identifiers (CoF#).
- Synonym assignments will have relationship type 'RELATED' except for
  misspellings, for which it would be 'EXACT'.

### Action items

- Peter will try UBIO for synonyms not in CAS (and report to Phenoscape
  group)
- Peter will request dbx prefix from OBO for specifying CAS publication
  ids (e.g., CASREF)
- Peter will propose scheme for adding the name of the requester to
  synonyms added to the TTO
- Wasila/Paula provide full refs for all curated pubs with CAS number
  (if cited in CAS); PMID or DOI if not cited in CAS

## Notes from Data Curation Sessions

Sylvan Lake Lodge Meeting Room - September 29, 2008 (Monday)

***Wasila & Paula's notes***

Comparative phenotypes: discussion of relative size, shape characters:
Problem: Descriptors comparing size, shape among taxa within a pub
cannot be extended to taxa outside the study (e.g., Rick's size of bone
example with three character states: large (0), small (1), extremely
small (2)) How to do this with ontologies? Judy pointed out that there
is a (dynamic line)in annotation, between the depth of a structured
vocabulary and free text. I.e. where do you stop using an ontology and
begin using free text? Data specific to study should be free-text.

Judy Blake intially suggested simply annotating our complex anatomical
characters to "shape". This indexing first pass is useful for users to
be able to aggregate the data (vs. full curation). Through further
discussion, we agree that annotating to a more granular level, i.e.
"shape: width" would be better and more informative. The weakness of the
current PATO comes in here, in that there need to be more nodes between
shape and all the terminal nodes (the descriptors such as "narrow"
"broad" etc.). This might allow more depth than just "shape:width".

We need to index our comparative systematic studies at a level that is
useful for the field. It is like a library, "binning" index to multiple
things.

John's idea for recording size comparison within a study: Use shape:
width and ALSO apply an internal grading system for these characters
such that the least/smallest value is given 1.

- graded series of lengths, widths, etc.. give 1, 2, 3 ...
- least/smallest value is given 1

Eric's example of incomplete/complete scute series:

- E: scute series; Q: in contact RE: skull
- E: scute series; Q: in contact RE: dorsal fin
- E: scute series; Q: separated from RE: skull
- E: scute series; Q: separated from RE: dorsal fin

Judy: important to separate tasks of 1) anatomy ontology development and
2) annotation of publications

- suggested having ontology development workshops and curation workshops
- her suggestion: Curator needs to enter terms ahead of time and have
  experts fix the annotations (problem at our workshop currently is that
  people are not finding entities in ontology - need ontology work)

Mark submitted TAO request on Weberian vertebra - relationships that
don't hold for all taxa

Wasila: batching vs. one term request: ok to submit related terms in one
request

Suzi: suggested having a small PATO workshop with ichthyologists, like
anatomy workshop

curators understand details of system

JB: put 2-3 people together to do anatomical subtree: send out invite to
ontology development

***Judy's observation notes***

- Wasila and John talking about anatomical terms and what they should be
- Paula showing Mark how to log into sourceforge
- Rick looking at characters for his paper
- Wasila from Peter: question on batching or one term per request
- Jeff helps Eric remember how to log into sourceforge
- Terry working on her paper
- looking for "right" first ... low hanging fruit
- Rick annotating with Wasila's help
- Mark entering successful s.f. proposal
- Eric looking for term in his paper
- Terry asking Jeff how to enter post-composed terms

## Wrap-up discussion with curators

October 1, 2008 (Wed morning)

***Wasila + Paula's notes***

Paula: suggestions for improving curation process?

- Terry: would like to go through a paper first to deal with needed
  terms
  - also liked annotating easy terms to become familiar with ontology
    structure

<!-- -->

- John: some things, like joints, can be added in bulk (e.g. in ontology
  development meeting like the one in Philadelphia)

<!-- -->

- All: Had visualization issues - how to know what terms are there, and
  their relationships?
  - Need large poster of all terms (Paula, Wasila, Jeff Engeman will
    make one and send file to all curators to print)

<!-- -->

- - Paula: PDF mark-up tool that highlights terms matching to TAO;
    characters not highlighted would likely require new term
  - Todd and Paula: use Phenex to highlight ontology terms because
    character and state descriptions from pub are pre-entered as free
    text (Paula added this to Phenex tracker)

<!-- -->

- Mark: how does a curator decide to precompose vs. postcompose?
  - Wasila: if entity will be used repeatedly (in single or multiple
    pubs) then add to TAO; if not, post-compose
  - Mark: when post-composing, would be helpful if Phenex would
    autocomplete to pre-composed cross-product term (if present in TAO)
    so that curator can be aware of similar term in ontology

<!-- -->

- Suzi: tough anatomy stuff: you can discuss as a group of curators then
  submit and enter in ontology

<!-- -->

- Paula: need to set up svn for Phenex files (Jim will do this) - WD
  will send instructions to new curators

<!-- -->

- Rick: can we break down single character into multiple characters?
  - Paula: make into multiple annotations - don't break down character

<!-- -->

- Pubs with same characters
  - Paula: curate it all separately
  - Jim: duplicates will come together in database

Paula: Problem: Currently we are not curating of entities that are
always present (e.g. "maxilla" present in all Teleostei). Problem is
that users may search for distribution of a character and may find
variability in very restricted taxon (genus) but have no information as
to the condition in the larger group (teleost fishes). Need to add these
conserved characters. Two approaches - either fine for us - need input
from Jim regarding database feasibility.

- 1\. Inherit: annotate 1-2 basal species within each ostariophysan
  subgroup whose character states are optimized to ancestral/internal
  nodes.
- 2\. Propagate: annotate higher level group node (e.g. "Teleostei")
  with a character state (e.g. "presence") and flag with weak evidence
  code. This character state is propagated to leaf
  nodes/species/terminals (unless run into different character state).

<!-- -->

- Jim: preference for 1 (inherit);
- Jim: relationship between EQ and taxon: "inferred to exhibit";
  phenotypes are exhibited by taxa; congregating "exhibits" to higher
  levels seems to be ok to do (e.g., cypriniformes exhibit red and blue
  dorsal fin)

<!-- -->

- Jim: might need more than one relationship between taxon and a
  phenotype; right now we have "exhibits" as the relationship
- John: We want biological principles incorporated here/ examples of
  optimization

<!-- -->

- Paula: This relates to character mapping/optimization. May need new
  methods to optimize EQs?

Action items:

- Paula: Will followup with curators regarding completeness of
  literature surveyed --<a href="User%3APmabee@usd.edu" class="wikilink"
  title="Pmabee@usd.edu">Pmabee@usd.edu</a> 11:05, 14 October 2008
  (EDT)Done
- Paula & John: Will work up optimization example for group that
  summarizes basic user mapping needs

## Curation consistency experiment: Review of Results

Five curators (Engeman, Grande, Hilton, Mayden, Sabaj) participated in
the consistency experiment on September 30, 2008 (Wed.). The results of
the experiment are discussed in more detail
<a href="Data_Jamboree_2/Annotation_Experiment" class="wikilink"
title=" here."> here.</a>

***Hilmar's notes on discussion of experiment with curators and
advisors***

Character \#2

- difference between depth, length, width
- some failed to post-compose (e.g., increased length)
- need to standardize shape, length, depth, and width definitions
- should then use higher level character (such as 'shape')

Character \#3

- some use 'increased count' which is-a count

Character \#4

- question of whether basihyal bone precludes presence (or implies
  absence) of cartilage
- question of how to annotate this looks more difficult than in reality
  is
- basihyal cartilage absent implies basihyal bone absent (because the
  latter develops from the former)
  - in fact it can also be that the cartilage is absent b/c it has
    developed into the bone (completely ossified)
  - hence need to add that basihyal is absent too
- graph view can be very helpful

Character \#5

- software should prevent filling in relative entities for qualities
  that aren't relational
- post-composed relative entity because of uncertainty of whether the
  full (existing) term would be compatible with the definition the
  author may have been using (for a different clade)
- difficulty to find the 'bony projection' by auto-completion (because
  it doesn't pop up when typing the beginnings of 'projection')
- problem of capturing the 'overlaps with' aspect in addition to
  'anterior to'
- full text search of the definitions would be very useful

Character \#6

- hypural is also contained within the upper lobe of the caudal fin
- difficulty of finding and comparing definitions of relationship types

Character \#7

- Software should ensure that entity starts with an entity term if
  post-composed, not a quality

Character \#8

- sphenotic needs to go into the comment field

Character \#9

- too complex to express the exact nature of the orientation, so choose
  just 'orientation'

Character \#10

- triradiate versus tripartite
