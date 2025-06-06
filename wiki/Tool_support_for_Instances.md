---
title: Tool support for Instances
permalink: wiki/Tool_support_for_Instances
layout: wiki
tags:
 - Ontology
 - Informatics
---

## Instances in Phenoscape Ontologies/Vocabularies

Several Phenoscape ontologies, particularly the TTO and the Fish
Collection Ontology, might more appropriately represent their contents
as instances or individuals. Unfortunately, the current versions of
OBO-Edit (either 1.1 or 2.0Beta) do not support creating, editing, or
viewing OBO Instance Stanzas. Additionally, current OWL/OBO conversion
tools ignore instances when converting. Hopefully, a future version of
OBO-Edit will support editing and reasoning with OBO Instances. However,
at present (21 August 2008), adding such support to OBO Edit 2.0 would
further delay the release process and providing this support as an
OBO-Edit plugin would likely be buggy. Therefore, the interim solution
to this problem will consist of a user defined instance_of relation
(which should xref to OBO_REL:instance_of). This relation will allow
creation of OBO child terms related to parents by instance_of. An
outboard conversion utility will convert terms that are linked as
children of instance_of relations back and forth between Instance and
Term stanzas in the OBO file. To view an OBO file with instances, a user
would run the tool to convert instances to terms, creating a new OBO
file which OBO-Edit could display fully. Any changes to this file would
require running the tool to convert in the opposite direction to restore
the instance stanzas.

Since the OBO backend supports instance round-tripping, making modified
versions of existing generation tools (e.g., TTOUpdate) that use
instances when appropriate should not be unnecessarily difficult.
