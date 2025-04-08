---
title: Anatomy Tree Display
permalink: wiki/Anatomy_Tree_Display
layout: wiki
tags:
 - Mockups
 - User Interface
---

## Version 4

This revision puts the ontology tree on the left as the primary browsing
tool. Data for the selected term appears in the tabbed panels to the
right.

### page 1

<figure>
<img src="singlewindow1.png" title="singlewindow1.png" width="700" />
<figcaption>singlewindow1.png</figcaption>
</figure>

#### Comments

- We should display all relationship types in the tree view, not just
  *is_a*.

### page 2

<figure>
<img src="singlewindow2.png" title="singlewindow2.png" width="700" />
<figcaption>singlewindow2.png</figcaption>
</figure>

#### Comments

### page 3

<figure>
<img src="singlewindow3.png" title="singlewindow3.png" width="700" />
<figcaption>singlewindow3.png</figcaption>
</figure>

#### Comments

### page 4

<figure>
<img src="singlewindow4.png" title="singlewindow4.png" width="700" />
<figcaption>singlewindow4.png</figcaption>
</figure>

#### Comments

- Since the search produces a list of mixed types of terms, should be an
  indicator of what the term is - entity, quality, gene, taxon, etc.

## Version 3

For conference call on 1/26/10. Notes and features on screenshots based
on 1/22/10 conference call.

### Two panel display of summary results

#### page 1

<figure>
<img src="anatomy-tree-2panels-p1-rev1.png"
title="anatomy-tree-2panels-p1-rev1.png" width="700" />
<figcaption>anatomy-tree-2panels-p1-rev1.png</figcaption>
</figure>

#### page 2

<figure>
<img src="anatomy-tree-2panels-p2-rev1.png"
title="anatomy-tree-2panels-p2-rev1.png" width="700" />
<figcaption>anatomy-tree-2panels-p2-rev1.png</figcaption>
</figure>

## Version 2

For conference call on 1/22/10

### Access anatomy tree summary results from front search page:

<figure>
<img src="anatomy-search.png" title="anatomy-search.png" width="700" />
<figcaption>anatomy-search.png</figcaption>
</figure>

### Summary results, page 1

<figure>
<img src="anatomy-tree1-rev1.png" title="anatomy-tree1-rev1.png"
width="700" />
<figcaption>anatomy-tree1-rev1.png</figcaption>
</figure>

### Summary results, page 2

<figure>
<img src="anatomy-tree2-rev1.png" title="anatomy-tree2-rev1.png"
width="700" />
<figcaption>anatomy-tree2-rev1.png</figcaption>
</figure>

### Two panel display of summary results

<figure>
<img src="anatomy-tree-2panels.png" title="anatomy-tree-2panels.png"
width="700" />
<figcaption>anatomy-tree-2panels.png</figcaption>
</figure>

## Version 1

From conference call on 1/21/2010"

### Access anatomy tree summary results from front search page:

<figure>
<img src="anatomy-search.png" title="anatomy-search.png" width="700" />
<figcaption>anatomy-search.png</figcaption>
</figure>

### Summary results, page 1

<figure>
<img src="anatomy-tree1.png" title="anatomy-tree1.png" width="700" />
<figcaption>anatomy-tree1.png</figcaption>
</figure>

#### Comments:

- Alternatively, this could be a two-panel display with tree in the left
  panel and results table in right panel, similar to BioPortal's layout.
  - make mockup for next conf call

<!-- -->

- How to clearly indicate relationships on branches? For example, "type
  of" and "part of" with arrow pointing to parent?
  - Don't need to display relationships on branches if tree has "subtype
    results" and "subpart results" labeled.

<!-- -->

- tree is confusing. Would be clearer to indent child terms, similar to
  OBO-edit's ontology tree viewer.

### Summary results, page 2

<figure>
<img src="anatomy-tree2.png" title="anatomy-tree2.png" width="700" />
<figcaption>anatomy-tree2.png</figcaption>
</figure>

## Version 0

### Search summary results

Copied from this page: <a href="Knowledgebase_mockups" class="wikilink"
title="Knowledgebase_mockups">Knowledgebase_mockups</a>

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
