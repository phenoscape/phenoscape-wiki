---
title: EQ Editor
permalink: wiki/EQ_Editor
layout: wiki
tags:
 - Informatics
---

# Overview

Currently, the EQ Editor is being developed by customizing
[Phenote](http://www.phenote.org/) to our needs. We are collaborating
with the developers of Phenote at NCBO by contributing improvements to
the core Phenote code, and we are also developing specialized components
and configuration required for our annotation workflow.

# Requirements

These are the currently understood requirements - an earlier draft can
be viewed at <a href="EQ_Editor_requirements_draft_1" class="wikilink"
title="EQ Editor requirements draft 1">EQ Editor requirements draft
1</a>.

The EQ Editor will be used by curators to annotate phenotypic
descriptions of Ostariophysi fish using EQ syntax and ontologies.

The curators will use the EQ Editor to code phenotypic data from an
existing publication into the EQ format. This data consists of
descriptions of character state values for corresponding species (or,
more precisely, specimens). A published character state description may
contain: the species or higher taxonomic specification, a textual
description of the character state value, reference to a voucher
specimen for this description, an image showing the character.

## Data Model

The following are essential data elements to be captured by the EQ
Editor for each character state description (format is in parentheses).
EQ coding will be performed at the level of character states, but there
may be a facility for dynamically viewing entries in a character matrix
format. See <a href="EQ_for_character_matrices" class="wikilink"
title="&quot;EQ for character matrices&quot;">"EQ for character
matrices"</a> for a discussion - at the
<a href="WG:PI_Meeting_5Jun07" class="wikilink"
title="June 5 PI meeting">June 5 PI meeting</a> we decided to work with
only character states. Phenotype annotations should generally be made at
the species taxonomic level.

### Phenotype Annotation

- species name (ontology ID)
- EQ statement for character state (Q should be a value)
  - E from fish anatomy (ontology ID) - may be post-composed from
    multiple ontology terms, especially in conjunction with a spatial
    modifier ontology
  - Q from PATO (ontology ID)
  - measurement - used if Q is an attribute suitable for measurement
    (e.g. "length")
    - number - should be able to put in single value, a range, or \<, \>
      *- can all this be done within EQ formalism?*
    - unit (units ontology ID)
  - E2 from fish anatomy (if Q is descendant of "relational quality of
    continuant" or "relational quality of occurrent") (ontology ID)
- textual description (free text)
- publication/citation (DOI? older publications don't have DOI, do they?
  Another possibility is
  [SICI](http://iphylo.blogspot.com/2007/05/openurl-and-spiders.html))
- Reference to section, figure, or image from publication (free text)
- Evidence code (*the list of evidence codes requires discussion*)
  - Specimen catalog number(s) supporting evidence code when required
    (direct observation)

### Additional data per publication

Some data from the publications may be useful to store in our database,
independent of phenotype annotations.

- Entire specimen list (catalog numbers) in publication materials. This
  could be useful to users of the site who may want to see what
  specimens the author was using, even if the annotated phenotypes were
  not explicitly tied to a catalog number. Further, we could use the
  catalog numbers to access museum specimen data services for various
  future applications.

## Workflow

### Sources of data

The publication being coded may contain data in one of a few different
formats. The given data format may suggest its own style of workflow.
These publication types include 3 main forms:

1.  Description of many characters for many species and higher taxonomic
    levels; no character-by-taxon matrix published.
2.  A data matrix with multiple species and multiple characters. There
    is a character state value for each cell in this matrix.
3.  A single species description of values for many characters.
4.  Description of a single character for many species (perhaps less
    common than the other formats?). If focusing on a single character
    the data may come from multiple publications.

It seems like scenarios 2 and 3 can be treated as special cases of
scenario 1. For each character, an interface is required for choosing
the Entity and Quality from their respective ontologies, and entering
free text such as the original character descriptions, as well as other
<a href="#Data_Model" class="wikilink" title="relevant data">relevant
data</a>.

### Detailed steps

The standard workflow would be a curator dealing with a single
publication during a session of working with the EQ Editor. Steps might
be:

1.  Create a new EQ Editor document.
2.  Enter document-wide data:
    1.  publication information (author, title, journal)
    2.  list of species - choose taxon from taxonomic ontology for each
        one
        - For each species, input list of specimen catalog numbers used
          in the publication, choosing museum institutions from a pick
          list
3.  Begin making character state annotations:
    1.  Select a species or multiple species to which this character
        state applies (there should be facilities for efficiently
        choosing sets of taxa)
        - If the author makes a statement about a higher taxon (e.g. a
          family), make a phenotype annotation for every species in the
          materials list for that publication which is a member of the
          taxon.
    2.  Create a new EQ statement
    3.  Choose Entity from anatomy ontology
    4.  Choose Quality from PATO (usually a Value term)
    5.  If the Quality is an Attribute term (such as "length"), enter a
        measurement and its units
    6.  If the Quality is relational, enter a second Entity from the
        anatomy ontology
    7.  Enter the evidence code appropriate for the published
        statement - if the phenotype is clearly based on one or more
        specific specimen numbers, enter them into the catalog number(s)
        field to support the appropriate evidence code.
    8.  Enter any information for the figure or section within the paper
        showing the character.
4.  At any point, the curator can save the current work to a document
    (or database).

### Working with EQ statements

- A particular EQ statement (specific combination of Entity and Quality)
  will often be applied to multiple species within one document. Species
  are likely to share EQ values as a result of phylogenetic history, so
  facilities for efficiently selecting groups of related species should
  be available. Entries with this EQ statement would be generated for
  each selected species.
  - An EQ entry panel could allow the user to choose a taxon from the
    taxonomic ontology, either by directly browsing the ontology or
    through an autocomplete text search field. All species within that
    taxon would be selected.
  - A phylogenetic tree view could be provided, which allows the user to
    select a node or nodes to which to apply an EQ statement. All
    species descending from that node would be selected. This tree could
    be initialized by using the taxonomic ontology. The user could
    manually edit the tree to provide additional resolution (perhaps by
    following a tree in the paper). Alternatively, the software could
    allow the specification in Newick format of a tree created by
    another application.
  - It would be useful to be able to invert selections generated by
    either of the preceding methods.
- The EQ statements entered into the document should be able to be
  viewed in various ways to allow checking data entry progress. Various
  views are desired:
  - Flat list of all entered EQ statements.
  - Filtered flat list - a search text field can allow quick filtering
    by any of the data fields.
  - Character-by-taxon matrix - generated from EQ statements by grouping
    via shared PATO Attributes.
  - Filtered matrix view - what capabilities are needed? filter by
    taxon, entity, quality: if one of these is a higher term in the
    ontology, show all descendant matches

### Questions

- What should the user be able to do if there is not an appropriate term
  in the ontology?
- Need to add a button to say "Need a new term"
- What will be done (in the immediate term) with the annotations
  produced by the EQ Editor? Will they be stored in separate documents,
  or compiled into a central repository?

# Roadmap

See the <a href="software_roadmap" class="wikilink"
title="software roadmap">software roadmap</a> for further plans.
