---
title: Virtuoso
permalink: wiki/Virtuoso
layout: wiki
tags:
 - Informatics
 - Software
---

## Helpful Virtuoso documentation links

- [Bulk loading RDF source
  files](http://www.openlinksw.com/dataspace/dav/wiki/Main/VirtBulkRDFLoader)
  - Within isql:
    `ld_dir_all('/usr/local/virtuoso/6.1.4/share/virtuoso/vad/kb', '*.owl', '`[`http://kb.phenoscape.org/`](http://kb.phenoscape.org/)`');`
  - then, `rdf_loader_run();`
  - Before doing the above you may need to
    `delete from db.dba.load_list;` to make it reload files that have
    previously been loaded.
- [Removing all
  triples](http://www.openlinksw.com/dataspace/dav/wiki/Main/VirtRemoveTriples)
  - Within isql:
    `sparql clear graph <`[`http://kb.phenoscape.org/`](http://kb.phenoscape.org/)`> ;`
  - Or, to remove all triples except those from the system:
    `RDF_GLOBAL_RESET ();`
- [Setting default
  passwords](http://docs.openlinksw.com/virtuoso/newadminui.html)
- [Inference rules and
  reasoning](http://docs.openlinksw.com/virtuoso/rdfsparqlrule.html)
  - Within isql:
    `rdfs_rule_set('`[`http://kb.phenoscape.org/`](http://kb.phenoscape.org/)`', '`[`http://kb.phenoscape.org/`](http://kb.phenoscape.org/)`');`
    - First arg is name of rule set, second is RDF graph to include
- [Full-text
  indexing](http://docs.openlinksw.com/virtuoso/sparqlextensions.html)
  - Within isql: `DB.DBA.RDF_OBJ_FT_RULE_ADD (null, null, 'All');`
- [Performance
  tuning](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtRDFPerformanceTuning)
  - Add index on predicate:
    `CREATE BITMAP INDEX RDF_QUAD_PGOS ON DB.DBA.RDF_QUAD (G, P, O, S) PARTITION (O VARCHAR (-1, 0hexffff));`
  - adjust memory settings
- Configure
  [CORS](http://en.wikipedia.org/wiki/Cross-origin_resource_sharing)
  (Cross-Origin Resource Sharing) to allow SPARQL queries from any web
  application
  - <http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtTipsAndTricksGuideCORSSetup#CORS%20Setup%20for%20Virtuoso%20servers>
