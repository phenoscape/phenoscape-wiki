---
title: Teleost Anatomy Ontology
permalink: wiki/Teleost_Anatomy_Ontology
layout: wiki
tags:
 - Ontology
 - Curation
 - Anatomy
---

## Summary

The Teleost Anatomy Ontology (TAO) is a multi-species anatomy ontology
for teleost fishes. The TAO uses terms from the Common Anatomy Reference
Ontology [(CARO)](http://code.google.com/p/caro2/) as a template for its
upper level nodes, and the Vertebrate Skeletal Anatomy Ontology
[(VSAO)](http://www.obofoundry.org/cgi-bin/detail.cgi?id=vertebrate_skeletal_anatomy)
for general skeletal anatomy classes. Growth of the TAO is enabled by
contributions from data curators and the ichthyological community (see
<a href="#Anatomy_Term_Tracker_and_Teleost-discuss_Mailing_List"
class="wikilink" title="Anatomy Term Trackers">Anatomy Term Trackers</a>).
The TAO can be browsed by using the [NCBO
BioPortal](http://bioportal.bioontology.org/visualize/38362) and data
annotated using TAO terms can be queried using the [Phenoscape
Knowedgebase](http://kb.phenoscape.org/). Details about the development
and use of TAO can be found in [Dahdul et al.
2010](http://sysbio.oxfordjournals.org/cgi/content/abstract/syq013/)

The current release may be found
[here](http://purl.obolibrary.org/obo/tao.obo).

## TAO and ZFA synchronization

The TAO was initialized with terms from the Zebrafish Anatomical
Ontology (ZFA), and we currently maintain manual synchronization of the
two ontologies. We developed the [Synchronization
Tool](http://phenoscape.org/wiki/Synchronization_Tool) as an Obo-Edit
plug-in to help automate this process.

One of the challenges in synchronzing the two ontologies involves the
addition of terms to the TAO that are not required for the ZFA. The
addition of these terms to the TAO may require the creation of
additional intermediate terms that are redundant for the ZFA. For
example, zebrafish have only one type of tooth (ceratobranchial 5
tooth). Other teleost species have teeth on the jaw bones and other
branchial arch and oral cavity bones. Because of this, the term ‘tooth’
is needed in the TAO as a parent to all tooth types:

- TAO:
  - ceratobranchial 5 tooth is_a tooth
  - premaxillary tooth is_a tooth
  - tooth is_a multi-tissue structure

The term ‘tooth’ is redundant for the ZFA because zebrafish have only
one type of tooth:

- ZFA:
  - ceratobranchial 5 tooth is_a multi-tissue structure

## Anatomy Term Tracker and Teleost-discuss Mailing List

The anatomy ontology is regulary updated to include new terms and
developed based on feedback from the community. Requests for changes are
submitted to the anatomy term tracker and a summary is forwarded to the
teleost-discuss mailing list for community discussion (see
<a href="Term_Requests" class="wikilink"
title=" instructions on requesting terms"> instructions on requesting
terms</a> for details). Terms are added to the TAO usually within one
week, with any comments or suggestions from teleost-discuss
incorporated. We invite you to join the [teleost-discuss mailing
list](https://lists.sourceforge.net/lists/listinfo/obo-teleost-discuss)
and contribute to the discussion of terms.
[Archives](http://sourceforge.net/mailarchive/forum.php?forum_name=obo-teleost-discuss)
of teleost-discuss are also available.

## Homology

Homology links are important in the use of multi-species ontologies to
define homology relations between different terms in the ontology, and
because homology is not implied if the same term is used in annotations
for different species. Terms in the anatomy ontology are defined based
on structural similarity, and it cannot be assumed that this similarity
is due to common ancestry. For example, zebrafish and humans both
possess a frontal bone; however, there is evidence that the zebrafish
frontal bone is homologous to the human parietal bone. Our use of the
homologous_to relation between entities that are homologues will help
clarify the identity of such similarly named but nonhomologous bones.

We have developed a method for homology designation by recording
homology statements outside of the ontology, as an annotation with
attribution and evidence codes. Homology statements are hypotheses, and
users of our database will have the option of viewing competing
hypotheses of homology when they occur.

## License

<span class="plainlinks">[<http://i.creativecommons.org/l/zero/1.0/80x15.png>](http://creativecommons.org/publicdomain/zero/1.0/)</span>
To the extent possible under law, Wasila M. Dahdul has waived all
copyright and related or neighboring rights to the Teleost Anatomy
Ontology (TAO). This work is published from the United States.
