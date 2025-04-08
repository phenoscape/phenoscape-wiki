---
title: Creating Tree Files
permalink: wiki/Creating_Tree_Files
layout: wiki
tags:
 - Curation
---

The following are instructions for creating and saving trees using
[Mesquite](http://mesquiteproject.org/mesquite/mesquite.html). You might
begin with an existing nexus file containing the data matrix for the
publication, or create a new nexus file containing a list of matrix taxa
copied from the Matrix Taxon column in Phenex. Make sure that tree names
match Matrix Taxon names.

#### General Instructions

1.  Open the nexus file in Mesquite. You should see the data matrix with
    the taxon list in the left-hand column.
2.  Create a Tree Block (which will contain one or more trees for the
    publication) by selecting Taxa&Trees \> New Empty Block of Trees.
    Click OK if Mesquite asks for Name of trees block.
3.  Click on the “View Trees” icon below “Trees” on the left hand side
    of the Mesquite window. You may need to click on the arrow to
    display the tree icons.
    1.  A ”default bush” tree will appear.
4.  Optional: format the tree display to make it easier to read the
    taxon names and to manipulate the tree
    1.  go to Drawing \> Tree Form \> Square Tree
    2.  go to Drawing \> Orientation \> Right
    3.  go to Drawing \> Set Current Orientation as Default
5.  Modify the tree as needed to replicate the publication tree. You may
    need the tree icons listed below.
6.  Store the tree by going to Tree\>Store Tree As
    1.  Name the tree after the figure number (e.g., Figure 6.).
7.  To add additional trees to the file, modify the stored tree (e.g.,
    Figure 6) as needed, then go to Tree \> Store Tree As
    1.  Name the tree after the new figure number

#### Tree tools commonly used

Tree Window buttons

- Prune clade button: delete taxon or branch from tree
- Collapse branch button: create polytomy
- Interchange branches button: rotate branches

Character Matrix buttons:

- Add taxa button: this creates an extra row in the character matrix for
  the new taxon. Double-click on the Taxon cell to rename the taxon.
