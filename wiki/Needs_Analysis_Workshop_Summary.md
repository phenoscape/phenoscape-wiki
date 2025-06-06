---
title: Needs Analysis Workshop/Summary
permalink: wiki/Needs_Analysis_Workshop/Summary
layout: wiki
tags:
 - Needs Analysis Workshop
 - Informatics
 - Use Cases
---

## Background

The PhenoScape <a href="Needs_Analysis_Workshop" class="wikilink"
title="Needs Analysis Workshop">Needs Analysis Workshop</a> was held
September 17-18, 2007 at NESCent. We invited
<a href="Needs_Analysis_Workshop#Participants" class="wikilink"
title="9 scientists">9 scientists</a> from the fields of morphology,
development, evolution, genetics, and ichthyology to help us define what
informatic tools need to exist in order to enable synthetic research
that takes full advantage of the accumulated data in each of these
fields. We hoped to identify driving biological questions and use cases
to guide the development of our software tools and database.

## Agenda

After being introduced to the project goals, the meeting participants
each provided a brief
<a href="Needs_Analysis_Workshop/Chalk_talks" class="wikilink"
title="chalk talk">chalk talk</a> outlining their integrative research
problems. The participants then split into two break-out groups, each
arranged around either the
<a href="Needs_Analysis_Workshop/Breakout_group_1" class="wikilink"
title="developmental genetics of morphology">developmental genetics of
morphology</a> or the
<a href="Needs_Analysis_Workshop/Breakout_group_2" class="wikilink"
title="evolution of morphology">evolution of morphology</a>. At the end
of the day the groups merged again to discuss the
<a href="Needs_Analysis_Workshop/Report-out_Day1" class="wikilink"
title="research questions">research questions</a> arising in the
breakout groups.

The second day began with three break-out groups:
<a href="Needs_Analysis_Workshop/Correlation_Breakout" class="wikilink"
title="correlations">correlations</a>,
<a href="Needs_Analysis_Workshop/Phylogeny_Breakout" class="wikilink"
title="phylogeny">phylogeny</a>, and
<a href="Needs_Analysis_Workshop/Semantics_Breakout" class="wikilink"
title="semantics">semantics</a>. As before, the whole group then
<a href="Needs_Analysis_Workshop/Report-out_Day2" class="wikilink"
title="discussed">discussed</a> the uses cases arising in the break-out
groups, and tried to identify
<a href="Needs_Analysis_Workshop/Prioritization" class="wikilink"
title="priorities">priorities</a> for the project.

## Driving questions/use cases

The following is a bullet-point summary highlighting both research
questions and software use cases produced by the discussion. Minutes
from the relevant session are linked next to each point.

- Use the database to identify discrete evolutionary modules
  <a href="Needs_Analysis_Workshop/Breakout_group_1" class="wikilink"
  title="BG1">BG1</a>
  - Depends on identifying patterns of evolutionary covariation among
    phenotypes
- For a branch hypothesized to be under positive selection (from e.g. a
  molecular analysis), identify candidate phenotypes that could have
  been selected for
  <a href="Needs_Analysis_Workshop/Breakout_group_1" class="wikilink"
  title="BG1">BG1</a>
  - Requires mapping phenotypic changes on phylogeny, visualizing
    synapomorphies
  - Topology can be modified and the results of modification visualized
- Use the database to help with negative information - what knowledge is
  missing that is required to answer a particular question?
  <a href="Needs_Analysis_Workshop/Breakout_group_1" class="wikilink"
  title="BG1">BG1</a>
- Integrate data regarding ecologic conditions, life history,
  adaptation, and evolutionary time with phenotypic and genetic data to
  elucidate mechanisms of phenotypic change
  <a href="Needs_Analysis_Workshop/Breakout_group_2" class="wikilink"
  title="BG2">BG2</a>
  - must integrate with existing databases, literature, across
    biological levels
  - use other factors (environment, ecology) as constraints on data
    presentation
- User adds own annotations using modified curator interface, compares
  own data with database
  <a href="Needs_Analysis_Workshop/Breakout_group_2" class="wikilink"
  title="BG2">BG2</a>,
  <a href="Needs_Analysis_Workshop/Phylogeny_Breakout" class="wikilink"
  title="PB">PB</a>
  - user may also want to store media such as images and movies
- Enrichment analysis: given a list of genes, find which phenotype terms
  are overrepresented among them
  <a href="Needs_Analysis_Workshop/Report-out_Day1" class="wikilink"
  title="RO1">RO1</a>
- User is notified of additions or changes to the database relevant to
  him/her
  <a href="Needs_Analysis_Workshop/Report-out_Day1" class="wikilink"
  title="RO1">RO1</a>
  - save user-defined queries as RSS feeds
- Capture and represent within-species variation in phenotypes and
  genotypes
  <a href="Needs_Analysis_Workshop/Report-out_Day1" class="wikilink"
  title="RO1">RO1</a>
  - describe polyphenism dependent on environmental factors or variable
    gene expression
  - view population frequencies of polymorphic phenotypes
  - describe phenotypic change through developmental time series
- View traits related to particular parts of anatomy - just tail, or
  just vertebra
  <a href="Needs_Analysis_Workshop/Correlation_Breakout" class="wikilink"
  title="CB">CB</a>
- User view ancestral character states on tree using default
  reconstruction methods
  <a href="Needs_Analysis_Workshop/Correlation_Breakout" class="wikilink"
  title="CB">CB</a>
- User downloads data in a form useful for applying their own methods of
  character reconstruction
  <a href="Needs_Analysis_Workshop/Correlation_Breakout" class="wikilink"
  title="CB">CB</a>
- Find cloud of similar annotations using summary matrices
  <a href="Needs_Analysis_Workshop/Correlation_Breakout" class="wikilink"
  title="CB">CB</a>
  - traits vs traits, traits vs genes, genes vs genes
  - cells would be number of branches on which the two traits change in
    common (traits vs traits), or number of mutants they have in common
    (traits vs traits, and traits vs genes), or number of traits in
    common (genes vs genes)
- User uses interactive tree view to select taxa for summary matrix
  <a href="Needs_Analysis_Workshop/Correlation_Breakout" class="wikilink"
  title="CB">CB</a>
- User selects one or more regions on body plan view to view
  traits(genes) affecting all
  <a href="Needs_Analysis_Workshop/Correlation_Breakout" class="wikilink"
  title="CB">CB</a>
  - then map corresponding traits on tree
- User creates and edits a tree using MacClade-like interface, then
  visualizes character changes on tree
  <a href="Needs_Analysis_Workshop/Phylogeny_Breakout" class="wikilink"
  title="PB">PB</a>
- User may want to work with data regarding mutations actually
  underlying evolutionary change
  <a href="Needs_Analysis_Workshop/Semantics_Breakout" class="wikilink"
  title="SB">SB</a>
  - different genetic states in different species

## Requirements arising from the use cases

### Overview

The use cases above present requirements for both our scientific
framework/data model and our software tools (curation tools and web
application). A good overview can also be found
<a href="Needs_Analysis_Workshop/Prioritization" class="wikilink"
title="here">here</a>.

- Provide character-state reconstructions on given phylogenies
  - analysis
  - visualization
- View and interactively/graphically edit phylogenies containing some
  subset of the taxa in the database
- Connect with and integrate data from external databases
  - ZFIN, GenBank, other genomics-oriented databases
  - Ecological, geographic, historical data - perhaps through museum
    catalog data
- Provide curation interface, storage, and analysis integration for
  private user data
- Save user queries as RSS feeds
- Filter view of data by ontology terms: anatomy, species, qualities
  - Provide advanced filtering functionality by means of ontology
    structure
- Provide views of data in downloadable forms convenient for further
  analysis
  - simple tables
  - generated NEXUS format
- Provide summary matrix views showing covariance/co-occurrence of
  various datatypes
  - Should be easily linked to other types of views (tree, etc.)
    restricted to data in particular cells
- Provide body plan view linked to anatomical terms for selection and
  filtering
- Support genetic diversity data along with phenotypic diversity data -
  molecular changes directly related to evolutionary changes

### Web application

The requirements primarily address capabilities of the web application
used as a front end to our data collection. In many cases they do not
significantly diverge from capabilities we would already be planning:
using filters to restrict the data being fed into a view, providing
link-outs to other genomic or museum databases, integrating data from
those databases in useful ways, providing a means for a user to save and
check favorite queries, and exporting the data to their local computer.

Some of the proposed views are more challenging but doable. The
phylogenetic tree view is not a new idea, but the participants desired
some advanced capabilities from it. Displaying character state changes
on the tree requires programming the graphics to do that, as well as
computing the reconstruction of ancestral states. Because there are
several ways to do that reconstruction, we might choose a basic method
and let users download the data for more complex analyses. All methods
of reconstruction rely on the data being in character matrix form - more
on that below. Further capabilities desired of the tree view lead to an
almost complete implementation of the MacClade/Mesquite tree editing
features within a webpage (presumably via JavaScript). This would be a
significant project, although probably quite useful to the community.
Some beginnings exist in other projects on the web.

The body plan view will require annotation of a complex image with
various ontology terms. This could be fairly coarse, or as complex and
fine-grained as we want to make it.

### Data model

Matrices displaying covariation/co-occurrence of phenotypic traits with
other traits (or other data) will in many cases require ancestral state
reconstruction, already mentioned as a desirable analytic view of the
data. This requires a tree, a reconstruction algorithm, and data in the
proper format. While our data describe character diversity, the
annotations require processing to be converted into evolutionary
character matrix form. This processing relies on distinguishing between
attributes and values in the PATO ontology and following a particular
algorithm. Since this process is central to many of the forms of data
analysis that came up in the meeting, I think we need to look more
carefully at how we want matrix generation to work and what is possible
with our annotation strategy and ontologies. Some of this is touched on
in <a href="EQ_for_character_matrices" class="wikilink"
title="EQ for character matrices">EQ for character matrices</a>, but a
more complete description of the current status of matrix generation
will be forthcoming.

The other topic which could have an impact on our data model is the idea
of dealing with genetic diversity along with phenotypic diversity. This
was primarily driven by David Stern's interests. Currently we are
cataloging phenotypic diversity, and linking these changes to mutant
phenotypes in a single species about which we have genetic data
(zebrafish). Within David's research, genetic changes are known in
multiple species and a causal link can sometimes be demonstrated between
specific evolutionary genetic changes and phenotypic evolution. Our
system as currently proposed does not accommodate these data, nor
provide a way to analyze them.
