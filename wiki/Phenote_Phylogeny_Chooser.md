---
title: Phenote:Phylogeny Chooser
permalink: wiki/Phenote%3APhylogeny_Chooser
layout: wiki
tags:
 - Curation
 - Informatics
 - EQ Annotation
 - User Interface
redirect_from:
 - wiki/Phenote%3APhylogeny-based_Selector
---

When selecting specimens for EQ editing from the specimen list, a user
may want to view a phylogenetic tree relating the specimens, and then
simply select a node containing all the specimens to use. This
functionality is available in an accessory window within Phenote. When
viewing the <a href="Phenote:Specimen_List" class="wikilink"
title="specimen list window">specimen list window</a>, click on the
"Choosers" menu, and select "Phylogeny Chooser". You should see a new
window like this:

<figure>
<img src="phylogeny-chooser.png" title="phylogeny-chooser.png" />
<figcaption>phylogeny-chooser.png</figcaption>
</figure>

You can paste
[Newick-format](http://evolution.genetics.washington.edu/phylip/newicktree.html)
tree text into the "Newick Tree" field at the bottom of the window.
Press "Return", and the tree will be loaded into the window. Click on
any node to select it and its descendants. Press the "Apply Selection"
button, and the specimen list window will come forward - any specimens
with exactly matching taxon names will be checked. Only taxa on the tips
of the tree can match specimens (not internal nodes).

When the taxonomy ontology is available for inclusion within Phenote,
your Newick tree should be composed of ontology IDs from the taxonomy
ontology. The tree view will automatically display the actual taxon name
from the ontology.

Hints:

- Create your tree using Mesquite, MacClade, or other tree-editing
  software.
- Any internal node labels in your Newick tree can be displayed by the
  tree view, making it easier to find the node you're looking for.
- If there is a problem with your Newick format, the "Newick Tree:" text
  will be colored red.
- Control-click a node to select or deselect it without affecting the
  rest of your selection.
- You can drag over instead of directly clicking on nodes to select
  them.
