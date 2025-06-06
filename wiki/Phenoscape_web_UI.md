---
title: Phenoscape web UI
permalink: wiki/Phenoscape_web_UI
layout: wiki
tags:
 - Roadmaps
 - User Interface
 - Informatics
---

Phenoscape web UI development plan.

## 2009

### February 2009

- Mockup changes to existing interfaces required to incorporate 1/5/09
  team feedback on existing interface components
- Taxon search interface **Done**
  - Mockup interface using dummy data within web application - request
    group feedback
    - Front page search interface and results table - may include
      intermediate results summary page
- Interface demo and feedback session - DECAP meeting, Feb. 27, 2009
  **Done**
  - Present screenshots and mockups
  - Possible live demo depending on data service performance progress
    - Services should return in no more than 2 seconds
    - Evaluate feasibility 2 weeks before meeting
- Mockup publication data interface within web application **Done**
- Mockup "splashy" search entry page - we should have a more graphically
  capturing entry gateway for exploring the data content
  - One of the following:
    - Hierarchical term explorer
    - Visual explorer, using schematic drawings ("the prototypical
      fish")
    - Visual explorer using 3D scans of catfish (and eventually
      zebrafish when done).
  - Should explore various prototypes of these ideas using HTML mockups
    and get feedback from project team
- Mockup taxonomy-based tree-mapped data perspective
  - View taxonomic phenotype annotation results organized by a
    phylogenetic tree
  - Group phenotypes as simplistic union of descendant nodes, rather
    than ancestral reconstruction
  - Use taxonomy as basis for phylogenetic tree
  - Develop HTML mockups in web application

### March 2009

- Incorporate 1/5/09 team feedback on existing interface components **In
  progress**
  - Anatomy term search results - reorganize according to
    <a href=":Image:Phenotype_search_page_mockup.jpg" class="wikilink"
    title="sketch">sketch</a>
  - Gene search results - reorganize according to
    <a href=":Image:Gene_search_page_mockup.jpg" class="wikilink"
    title="sketch">sketch</a>
  - Taxonomic phenotype results page - add Order column for taxonomic
    grouping
  - Present various phenotypic results grouped by custom "character
    slim" done
    - Requires slim development by team members (Wasila, Paula)
      Done--<a href="User%3APmabee@usd.edu" class="wikilink"
      title="Pmabee@usd.edu">Pmabee@usd.edu</a> 12:20, 20 March 2009
      (EDT)done and service implementation by Cartik
- Taxon search interface
  - Design data service schema to be implemented by Cartik
  - Implement interface using live data service once developed by Cartik

### April 2009

- Implement "splashy" search entry page as defined by mockup work
- Incorporate publication data into user interface
  - Incorporate publication links into annotation results displays
    - Columns referencing numbers of taxonomic phenotype or mutant
      phenotype match results will be accompanied by a column including
      number of publications referencing the search item
    - Link from publication count to a publication listing
  - Publication listing includes brief citation each of which links to a
    publication detail page
  - Publication detail page(s)
    - Full citation information
    - Display curator credits
    - Display or link to original matrix including free-text data and
      specimen listing
    - Display or link to all phenotype annotations resulting from
      publication
  - Requires publication data implementation in OBD by Cartik
  - Requires specimen data implementation in OBD by Cartik
- Possible user testing session in conjunction with RCN meeting at
  NESCent

### May 2009

- Implement taxonomy-based tree-mapped data perspective
- Implement appropriate scalable deployment of web application **Done**
  - Multiple application instances and load balancing **Done**

### Release candidate - June 2009

- Project team testing
- Bug fixes
- Overall performance evaluation

### Public launch: ASIH meeting, Portland, Oregon - July 22, 2009

## 2010

### February 2010

- Develop overall site revision plan based on feedback from
  Knowledgebase Beta 1 interface **\[Done\]**
- Knowledgebase 2.0 site revision mockup testing **\[Done\]**
  - Present mockups to naive users in Eugene, Oregon, February 16-17
    \[**Done**\]
  - Revise mockups using testing session user feedback \[**Done**\]
- Develop 2.0-beta implementation plans with feedback from Phenoscape
  stakeholders \[**Deferred**\]

### March 2010

- Annotation search results pages with editable data filters
- Working taxonomy cladogram data interfaces
- Complete mockups of advanced query interfaces
- Phenoscape meeting at Field Museum, Chicago
  - Conduct user feedback sessions with mockups of forthcoming
    interfaces, and live testing of implemented pages \[**Done**\]
  - Write-up results of feedback and proposed changes
- Generate permanent unique ID for each publication \[**Done**\]
- Enter unique IDs for publications into Endnote \[**Done**\]
- Data imported KB via Endnote XML files \[NOTE: This part was done
  quite a while ago. However, a slight modification needs to be made to
  use the new unique IDs for publications\]
  - citation information as individual semantic pieces (individual
    authors, title, journal, etc.) - \[**Deprioritized**\]
  - abstract
  - DOI if available
- Investigate importing previous names of ZFIN genes
- Gene symbol as primary name - \[NOTE: This was the old status quo
  before we decided to the display the complete name of the gene, can
  easily revert to this.\]

### April 2010

- Term search results pages incorporating ontology tree browser
- Publication pages with citation and abstract, links to publications
  from other data types
- Advanced query interface, data download implementation
- type of mutation/defect producing phenotype result (requires
  feasibility investigation)
- ZFIN publication ID for each phenotype annotation
- import common names for taxa

### May 2010

- Publication pages with data matrix (table view and downloadable)
- Publication pages with specimens
- Link to taxonomy cladogram interfaces via data on other pages
- Official release of Phenoscape Knowledgebase 2.0-beta

### June 2010

- User testing sessions of Knowledgebase 2.0-beta
- Bug and feedback revisions

### July 2010

- Official release of Phenoscape Knowledgebase 2.0
