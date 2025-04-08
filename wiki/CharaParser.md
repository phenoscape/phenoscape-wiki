---
title: CharaParser
permalink: wiki/CharaParser
layout: wiki
tags:
 - Software
 - Curation
 - NLP
---

CharaParser is a natural-language processing tool which analyzes the
text of character and character state descriptions to produce a
structured output. It was initially developed in [the "Fine-Grained
Semantic Markup of Descriptive Data for Knowledge Applications in
Biodiversity Domains"
project](http://sites.google.com/site/biosemanticsproject/). We are
adapting it to generate proposals for ontological phenotype annotations.
When it is ready, we plan to integrate it with
<a href="Phenex" class="wikilink" title="Phenex">Phenex</a>, so that
data curators can take advantage of natural-language processing to
accelerate their workflow.

A prototype of adapted CharaParser participated in the BioCreative 2012
Workshop with
<a href="Phenex" class="wikilink" title="Phenex">Phenex</a>. The
evaluation results showed that CharaParser was quite capable of
identifying candidate entity and quality phrases (it outperformed
biocurators by 20% in recall on average), but it had difficulty
translating candidate phrases to ontology terms. This is the area we are
currently working on.

The Phenoscape customizations of CharaParser are available through an
open source (MIT) license at [GitHub](https://github.com/phenoscape) and
the original code is on [Google
Code](http://sites.google.com/site/biosemanticsproject/project-source-code).
