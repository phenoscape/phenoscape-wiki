---
title: WebHints
permalink: wiki/WebHints
layout: wiki
---

This page is an easily editable source for help popups in the Phenoscape
web UI. Each entry below should be contained in a block element (DIV)
with a mnemonic ID.

NOTE that there may be other wiki pages that also appear in the
Phenoscape web UI, e.g.
<http://phenoscape.org/wiki/Knowledgebase:File_formats_(for_data_downloads)>

<div id="WhatArePhenotypes" style="border: 2px dashed silver;">

**About Phenotypes**

Phenotypes are a combination of an **Entity**, such as an anatomical
structure, with a **Quality**, a description of some qualitative aspect
of the entity such as shape, color, or size. Some qualities describe
aspects of one entity relative to another: these use the optional
**Related Entity** term.

</div>

<div id="FindSpecificTerm" style="border: 2px dashed silver;">

**Find a Specific Term**

Search using any valid term (taxon, gene, etc.) in the Knowledgebase.
**You must choose a matched value from the drop-down list before you can
search.**

</div>

<div id="BrowseAllPhenotypes" style="border: 2px dashed silver;">

**Browse All Phenotypes**

View all phenotypes used within annotations. Narrow results by taxa,
anatomical entity, phenotypic quality, or gene classification.

</div>

<div id="BrowseTaxa" style="border: 2px dashed silver;">

**Browse Taxa**

Browse the taxonomic hierarchy and view detailed information about each
term.

</div>

<div id="BrowseAnatomicalEntities" style="border: 2px dashed silver;">

**Browse Anatomical Entities**

Browse the anatomy ontology hierarchy and view detailed information
about each term.

</div>

<div id="BrowsePhenotypicQualities" style="border: 2px dashed silver;">

**Browse Phenotypic Qualities**

Browse the phenotypic quality ontology hierarchy and view detailed
information about each term.

</div>

<div id="BrowseGenes" style="border: 2px dashed silver;">

**Browse Genes**

TODO

</div>

<div id="BrowseComparativePublications" style="border: 2px dashed silver;">

**Browse Comparative Publications**

TODO

</div>

<div id="QueryPhenotpyeAnnotationsToTaxa" style="border: 2px dashed silver;">

**Query Phenotype Annotations To Taxa**

Find **phenotypes** associated with particular **taxa**; filter by
publication.

</div>

<div id="QueryPhenotpyeAnnotationsToGenes" style="border: 2px dashed silver;">

**Query Phenotype Annotations To Genes**

Find **phenotypes** associated with particular **genes**.

</div>

<div id="QueryTaxa" style="border: 2px dashed silver;">

**Query Taxa**

Find the **taxa** associated with a particular phenotype or publication.

</div>

<div id="QueryGenes" style="border: 2px dashed silver;">

**Query Genes**

Find a list of **genes** associated with a particular phenotype.

</div>

<div id="QueryCompatarivePublications" style="border: 2px dashed silver;">

**Query Comparative Publications**

Find **publications** that contain descriptions of particular taxa or
phenotypes.

</div>

<div id="QueryPhenotpyes" style="border: 2px dashed silver;">

**Query Phenotypes**

Find a list of **phenotypes** associated with a particular taxon, gene,
or publication.

</div>

<div id="VisualizePhenotypicProfileTree" style="border: 2px dashed silver;">

**Visualize Phenotypic Profile Tree**

Visualize the extent to which a specified set of phenotypes is exhibited
within and between taxa.

</div>

<div id="VisualizePhenotypicVariationTree" style="border: 2px dashed silver;">

**Visualize Phenotypic Variation Tree**

Visualize the taxonomic distribution of a specified phenotype.

</div>

<div id="AboutInferredAnnotations" style="border: 2px dashed silver;">

**Apply higher taxon annotations to all included species**

Using this option, phenotypes annotated to a higher taxon (e.g.,
Vertebrata) are assumed to apply to all organisms within that group. For
example, searching for 'basihyal bone absent' would return a list of all
catfish (Siluriformes) species because this phenotype has been annotated
at the level of the Siluriformes.

</div>

<div id="AboutTheWorkspace" style="border: 2px dashed silver;">

**Add to workspace**

When viewing query results, check the box to the left of any result to
add it to the workspace. On the workspace page, you can combine saved
items into new queries.

</div>

<div id="ChooseTermForFacet" style="border: 2px dashed silver;">

**Choose a specific term**

Use this button to choose a specific term to jump to, rather than
narrowing down via the ontology hierarchy links.

</div>

<div id="PhenotypeProfiles" style="border: 2px dashed silver;">

**Phenotype Profiles**

A phenotype profile is a set of phenotypes exhibited by a taxon. Taxa in
the tree are displayed in groups exhibiting a common phenotype profile.
A given phenotype may appear in multiple profiles—select a phenotype in
the table to see in which profiles in the tree it is present.

</div>

<div id="Entity" style="border: 2px dashed silver;">

**Entity term**

An anatomical structure or other item ("basihyal bone", "tooth",
"head").

</div>

<div id="Quality" style="border: 2px dashed silver;">

**Quality term**

A qualitative aspect of the entity, such as shape, size, or color.

</div>

<div id="RelatedEntity" style="border: 2px dashed silver;">

**Related Entity term**

A second entity which further species the quality term: may be another
structure to which the first is attached.

</div>

<div id="PhenotypeQueryResults" style="border: 2px dashed silver;">

**Query Phenotypes**

View distinct phenotypes meeting the query criteria. To view
intersections (AND) of phenotypes, use the pulldown menu to choose a
query for either **Taxa**, **Genes**, or **Publications**.

</div>

<div id="TaxonPhenotypeAnnotationQueryResults" style="border: 2px dashed silver;">

**Query Phenotype annotations to taxa**

View distinct annotations of phenotypes to taxa which meet the query
criteria. To view intersections (AND) of phenotypes, use the pulldown
menu to choose a query for either **Taxa**, **Genes**, or
**Publications**.

</div>

<div id="GenePhenotypeAnnotationQueryResults" style="border: 2px dashed silver;">

**Query Phenotype annotations to genes**

View distinct annotations of phenotypes to genes which meet the query
criteria. To view intersections (AND) of phenotypes, use the pulldown
menu to choose a query for either **Taxa**, **Genes**, or
**Publications**.

</div>

<div id="TaxaQueryResults" style="border: 2px dashed silver;">

**Query Taxa**

View taxa which meet the query criteria.

</div>

<div id="GenesQueryResults" style="border: 2px dashed silver;">

**Query Genes**

View genes which meet the query criteria.

</div>

<div id="ComparativePublicationsQueryResults" style="border: 2px dashed silver;">

**Query Comparative publications**

View comparative publications which meet the query criteria. These
publications contain the evolutionary data matrices annotated by
Phenoscape.

</div>

Add more entries here...
