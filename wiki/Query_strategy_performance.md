---
title: Query strategy performance
permalink: wiki/Query_strategy_performance
layout: wiki
tags:
 - Queries
 -  Query Execution
 - Informatics
 - Database
---

# Abstract

The Phenoscape prototype demonstrated at the SICB workshop (the SICB
prototype) in January 2009 suffered from very poor query execution
times. Following this, various querying strategies have been tested to
improve the execution times. This page discusses the requirements of the
various data access modules of the Phenoscape application to be
demonstrated at the ASIH workshop, and documents the performance of the
various
<a href="Queries#Proposed_querying_strategies_for_the_ASIH_prototype"
class="wikilink" title="querying strategies">querying strategies</a>
being tested for these modules. Testing on these querying strategies
have revealed significant speedup of execution times, as compared to the
performance of the SICB prototype. As an example, a query for the
anatomical entity 'fin' (TAO:0000108) took around 15 - 20 minutes to
retrieve all the pertinent information from the database in the SICB
prototype. Some of the querying strategies discussed on this page manage
to do the same in about 200 milliseconds, an improvement by several
orders of magnitude.

- NOTE: Familiary with SQL and PostgreSQL stored procedures may be
  necessary to fully comprehend these contents.

# Phenotype data summaries and details services

Given a specific anatomical entity A, the requirements of the anatomy
data service module are as follows:

1.  Identify ALL unique phenotypes {P} that are composed of the entity A
    or any of its subtypes.
2.  For each identified phenotype P which is of the form inheres_in(Q,
    E)
    1.  Identify the quality Q.
        1.  In addition, identify the character C which subsumes Q. This
            requires navigating the PATO hierarchy recursively in some
            cases
    2.  Identify the entity E. E may be the same as A, or any valid
        subtype of A.
    3.  Identify the set of taxa {T} or genotypes {GT} that exhibit the
        phenotype P.
        1.  For a genotype GT, identify the gene G that encodes it.

The result should be a list in the format shown below

<javascript> <Search-Anatomical-Entity> <Phenotype> <Entity> <Quality>
<Character> <List of taxa>OR<List of genes> </javascript>

## Strategy \#1

This strategy is the
<a href="Queries#Strategy_#1:_Simple_table_joins" class="wikilink"
title="simplest way">simplest way</a> to try and get all the necessary
information related to the anatomical entity being searched for. Below
is the actual query which attempts to do this. This query returns the
unique phenotypes associated with the anatomical entity, and the
qualities and specific anatomical entities associated with the
phenotype, as well as the list of taxa that exhibit each of these
phenotypes in one fell table join (uh, swoop).

### Query 1 (keep it simple, no stored procedure invocations)

\<source lang=sql SELECT DISTINCT phenotype_node.uid AS phenotype,
taxon_node.uid AS taxon, quality_node.uid AS quality, anatomy_node.uid
AS entity FROM link AS inheres_in_link, link AS search_link, link AS
is_a_link, link AS exhibits_link, node AS taxon_node, node AS
exhibits_pred_node, node AS phenotype_node, node AS search_pred_node,
node AS search_node, node AS inheres_in_pred_node, node AS anatomy_node,
node AS is_a_pred_node, node AS quality_node WHERE
exhibits_pred_node.uid = 'PHENOSCAPE:exhibits' AND is_a_pred_node.uid =
'OBO_REL:is_a' AND inheres_in_pred_node.uid = 'OBO_REL:inheres_in' AND
search_pred_node.uid = 'OBO_REL:inheres_in' AND search_node.uid =
'TAO:0000108' AND inheres_in_link.is_inferred = 'f' AND
is_a_link.is_inferred = 'f' AND exhibits_link.node_id IS NOT NULL AND
search_link.node_id = phenotype_node.node_id AND
search_link.predicate_id = search_pred_node.node_id AND
search_link.object_id = search_node.node_id AND inheres_in_link.node_id
= phenotype_node.node_id AND inheres_in_link.predicate_id =
inheres_in_pred_node.node_id AND inheres_in_link.object_id =
anatomy_node.node_id AND is_a_link.node_id = phenotype_node.node_id AND
is_a_link.predicate_id = is_a_pred_node.node_id AND is_a_link.object_id
= quality_node.node_id AND exhibits_link.node_id = taxon_node.node_id
AND exhibits_link.predicate_id = exhibits_pred_node.node_id AND
exhibits_link.object_id = phenotype_node.node_id;

</source>

#### Query Execution Plan

#### Execution Details

- Rows returned: 968
- Phenoscape data revision: 449
- Time: 0.25 ~ 9 s

#### Discussion

This query (referred to as QfS1, short for "Query for Strategy 1")
returns each phenotype associated with the 'TAO:0000108' and also the
specific entities and qualities associated with each phenotype. In
addition, the taxa that exhibit the phenotype and the genotypes are also
returned. If several taxa {T} or genotypes {GT} exhibit the same
phenotype P, which is of the form, inheres_in(Q, E), the results are
returned in rows in the format shown below.

<javascript> P1 E1 Q1 T1 P1 E1 Q1 T2 . . P1 E1 Q1 Tn P2 E2 Q2 GT1 . . P2
E2 Q2 GTn </javascript>

Note that for each quality Q in the result above, the character that
subsumes it needs to be determined. This cannot be done directly from
the query because a recursive traversal of the PATO hierarchy may be
required in many cases. Recursive traversals are best implemented by
stored procedures. This will definitely add to the execution times
documented for this query. Further, note that only the genotypes
associated with each phenotype are returned. To find the genes that
encode these genotypes, another query needs to be executed. It is not
possible to unilaterally join this gene query with QfS1 because both
taxa as well as genotypes are returned by QfS1. What is required is a
procedural attachment that invokes the gene query if the returned result
is a genotype. Again, this procedural attachment can only be implemented
as a stored procedure.

Finally, the performance of the query QfS1 varied widely from 0.25 (very
good) to 9 seconds (mildly acceptable) in a random set of executions
issued from the command line. If instead of searching for 'TAO:0000108'
(fin), a more general term (like TAO:0100000, the parent term for all
term definitions in TAO) were to be searched for, the performance of
this query would be much more unpredictable and much slower too.

### Query 2 (Bring on the stored procedures, some of them to start)

Let us examine the performance of the very same query where specific
stored procedures for identifying the characters subsuming the qualities
and genes encoding the genotypes are invoked as part of QfS1.

\<source lang=sql SELECT DISTINCT phenotype_node.uid AS phenotype,
quality_node.uid AS quality_id, quality_node.label AS quality,
getAttributeForQuality(quality_node.node_id) AS attribute,
anatomy_node.uid AS entity_id, anatomy_node.label AS entity,
getTaxaForPhenotype(phenotype_node.node_id) AS taxonOrGene FROM link AS
inheres_in_link, link AS search_link, link AS is_a_link, link AS
exhibits_link, node AS taxon_node, node AS exhibits_pred_node, node AS
phenotype_node, node AS search_pred_node, node AS search_node, node AS
inheres_in_pred_node, node AS anatomy_node, node AS is_a_pred_node, node
AS quality_node WHERE exhibits_pred_node.uid = 'PHENOSCAPE:exhibits' AND
is_a_pred_node.uid = 'OBO_REL:is_a' AND inheres_in_pred_node.uid =
'OBO_REL:inheres_in' AND search_pred_node.uid = 'OBO_REL:inheres_in' AND
search_node.uid = 'TAO:0000108' AND inheres_in_link.is_inferred = 'f'
AND is_a_link.is_inferred = 'f' AND exhibits_link.node_id IS NOT NULL
AND search_link.node_id = phenotype_node.node_id AND
search_link.predicate_id = search_pred_node.node_id AND
search_link.object_id = search_node.node_id AND inheres_in_link.node_id
= phenotype_node.node_id AND inheres_in_link.predicate_id =
inheres_in_pred_node.node_id AND inheres_in_link.object_id =
anatomy_node.node_id AND is_a_link.node_id = phenotype_node.node_id AND
is_a_link.predicate_id = is_a_pred_node.node_id AND is_a_link.object_id
= quality_node.node_id AND exhibits_link.node_id = taxon_node.node_id
AND exhibits_link.predicate_id = exhibits_pred_node.node_id AND
exhibits_link.object_id = phenotype_node.node_id;

</source>

#### Execution Details

- Rows returned: 69
- Execution time: 7 - 30 seconds

#### Discussion

This query returns all the required information for an input anatomical
entity. Note the taxa or genes exhibiting or responsible for a specific
phenotype are all grouped together in one row with the said phenotype.
The character which subsumes the quality of a phenotype is retrieved as
well. But since 13 tables are joined together, query execution planning
may still be a significant cause to the unpredictable and relatively
slow performance of this query. Moreover, note these results are being
obtained for a query for fin. If the query was for TAO:0100000, the root
term of TAO, the performance would be much slower and unpredictable.

## Strategy \#2

This strategy tries to save on query execution planning times by
specifying the <a
href="Queries#Strategy_#2:_Specifying_the_order_of_table_joins_in_the_original_query"
class="wikilink" title="order of table joins in the query itself">order
of table joins in the query itself</a>.

### Query

\<source lang=sql SELECT DISTINCT phenotype_node.uid AS phenotype,
quality_node.uid AS quality_id, quality_node.label AS quality,
getAttributeForQuality(quality_node.node_id) AS attribute,
anatomy_node.uid AS entity_id, anatomy_node.label AS entity,
getTaxaForPhenotype(phenotype_node.node_id) AS taxonOrGene FROM link AS
inheres_in_link, link AS is_a_link, node AS taxon_node INNER JOIN link
AS exhibits_link INNER JOIN node AS phenotype_node INNER JOIN link AS
search_link INNER JOIN node AS search_node ON (search_link.object_id =
search_node.node_id) ON (phenotype_node.node_id = search_link.node_id)
ON (exhibits_link.object_id = phenotype_node.node_id) ON
(taxon_node.node_id = exhibits_link.node_id), node AS
exhibits_pred_node, node AS search_pred_node, node AS
inheres_in_pred_node, node AS anatomy_node, node AS is_a_pred_node, node
AS quality_node WHERE exhibits_pred_node.uid = 'PHENOSCAPE:exhibits' AND
is_a_pred_node.uid = 'OBO_REL:is_a' AND inheres_in_pred_node.uid =
'OBO_REL:inheres_in' AND search_pred_node.uid = 'OBO_REL:inheres_in' AND
search_node.uid = 'TAO:0000108' AND inheres_in_link.is_inferred = 'f'
AND is_a_link.is_inferred = 'f' AND exhibits_link.node_id IS NOT NULL
AND search_link.node_id = phenotype_node.node_id AND
search_link.predicate_id = search_pred_node.node_id AND
search_link.object_id = search_node.node_id AND inheres_in_link.node_id
= phenotype_node.node_id AND inheres_in_link.predicate_id =
inheres_in_pred_node.node_id AND inheres_in_link.object_id =
anatomy_node.node_id AND is_a_link.node_id = phenotype_node.node_id AND
is_a_link.predicate_id = is_a_pred_node.node_id AND is_a_link.object_id
= quality_node.node_id AND exhibits_link.node_id = taxon_node.node_id
AND exhibits_link.predicate_id = exhibits_pred_node.node_id AND
exhibits_link.object_id = phenotype_node.node_id;

</source>

### Execution details

- Rows returned: 69
- Execution time: Approx. 9.8 seconds

### Discussion

The results obtained by this query are consistent with the requirements
of the anatomy data service. The query performance is also very stable
(approx. 9.8 seconds) over repeated executions. This time was recorded
for querying over fins. Querying for the root entity of TAO will
expectedly result in much longer execution times.

## Strategy \#3

This strategy uses <a
href="Queries#Strategy_#3:_Stored_procedures_that_use_simple_table_joins"
class="wikilink" title="back-end stored procedures">back-end stored
procedures</a> to minimize execution planning times. All the stored
procedures are introduced here.

### Stored procedures

#### Stored procedure \#1: getAttributeForQuality

This procedure navigates the PATO hierarchy recursively if needed to
identify the character that is associated with a given quality. Facets
have been provided in this procedure to handle qualities which do not
belong to attribute slim or value slim subsets, and to handle qualities
that are specified as aliases for other qualities. Note the PATO think
tank is about to replace attribute slims with character slim subset
specifications. The functionality of this procedure will however remain
the same.

\<source lang=sql CREATE OR REPLACE FUNCTION getAttributeForQuality(INT)
RETURNS VARCHAR AS \$\$ DECLARE res VARCHAR; attr_id INT; slim VARCHAR;
slim_id INT; temp_id INT; super_id INT; BEGIN SELECT DISTINCT object_id,
node_uid(object_id) INTO slim_id, slim FROM link WHERE node_id = \$1 AND
predicate_id = (SELECT node_id FROM node WHERE uid =
'oboInOwl:inSubset') AND object_id IN (SELECT node_id FROM node WHERE
uid IN ('value_slim', 'attribute_slim')); IF (slim IS NULL) THEN

`   SELECT object_id FROM link INTO super_id WHERE node_id = $1 AND predicate_id = (SELECT node_id FROM node WHERE uid = 'OBO_REL:is_a') AND is_inferred = 'f';`  
`   IF (super_id IS NULL) THEN`  
`       SELECT DISTINCT node_id FROM link INTO temp_id WHERE object_id = $1 AND predicate_id = (SELECT node_id FROM node WHERE uid = 'oboInOwl:hasDbXref');`  
`       IF temp_id IS NULL THEN`  
`           RETURN 'Attribute Undefined';`  
`       ELSE`  
`           RETURN getAttributeForQuality(temp_id);`  
`       END IF;`  
`   ELSE`  
`       RETURN getAttributeForQuality(super_id);`  
`   END IF;`

ELSIF (slim = 'attribute_slim') THEN res := node_uid(\$1) \|\| '(' \|\|
node_label(\$1) \|\| ')'; RETURN res; ELSE SELECT object_id INTO attr_id
FROM link WHERE node_id = \$1 AND predicate_id = (SELECT node_id FROM
node WHERE uid = 'OBO_REL:is_a') AND is_inferred = 'f'; RETURN
getAttributeForQuality(attr_id); END IF; END \$\$ LANGUAGE 'plpgsql';

</source>

#### Stored procedure \#2: getTaxaForPhenotype

This procedure retrieves all the taxa and genes that are associated with
a given phenotype. Given that genes are indirectly associated with
phenotypes (genotypes being the intermediary), this procedure navigates
the link from genotypes to genes to find the association.

\<source lang=sql CREATE OR REPLACE FUNCTION getTaxaForPhenotype(INT)
RETURNS VARCHAR\[\] AS \$\$ DECLARE rec RECORD; gene RECORD; taxa
VARCHAR\[20\]; ct int := 0; BEGIN FOR rec IN SELECT node_id,
node_uid(node_id) AS uid, node_label(node_id) AS label FROM link WHERE
predicate_id = (SELECT node_id FROM node WHERE uid =
'PHENOSCAPE:exhibits') AND object_id = \$1 LOOP ct := ct + 1; taxa\[ct\]
:= rec.uid \|\| '(' \|\| rec.label \|\| ')'; IF (rec.uid NOT LIKE
'%TTO%') THEN FOR gene IN SELECT node_uid(node_id) AS gId,
node_label(node_id) AS gLabel FROM link WHERE predicate_id = (SELECT
node_id FROM node WHERE uid = 'PHENOSCAPE:has_allele') AND object_id =
rec.node_id LOOP taxa\[ct\] := gene.gId \|\| '(' \|\| gene.gLabel \|\|
')'; END LOOP; END IF; END LOOP; RETURN taxa; END \$\$ LANGUAGE
'plpgsql';

</source>

#### Stored procedure \#3: getQualityFromPhenotype

This procedure finds the quality associated with the given phenotype

\<source lang=sql CREATE or REPLACE FUNCTION
getQualityFromPhenotype(INT) RETURNS RECORD AS \$\$ SELECT object_id AS
quality_id, node_uid(object_id) \|\| ' (' \|\| node_label(object_id)
\|\| ')' AS quality FROM link WHERE predicate_id = (SELECT node_id FROM
node WHERE uid = 'OBO_REL:is_a') AND node_id = \$1 AND is_inferred =
'f'; \$\$ LANGUAGE 'sql';

</source>

#### Stored procedure \#4: getEntityFromPhenotype

This procedure finds the anatomical entity directly associated with the
given phenotype

\<source lang=sql CREATE OR REPLACE FUNCTION getEntityFromPhenotype(INT)
RETURNS VARCHAR AS \$\$ DECLARE entity_id VARCHAR; BEGIN SELECT
node_uid(object_id) \|\| ' ' \|\| node_label(object_id) INTO entity_id
FROM link WHERE predicate_id = (SELECT node_id FROM node WHERE uid =
'OBO_REL:inheres_in') AND node_id = \$1 AND is_inferred = 'f'; RETURN
entity_id; END; \$\$ LANGUAGE 'plpgsql';

</source>

#### Stored procedure \#5: getAnatomyInfo

This is the master stored procedure which can be invoked directly from
the client side. It invokes the other stored procedures in turn to
retrieve all the information associated with the searched anatomical
entity in one go.

\<source lang=sql CREATE TABLE anatomyrow (search_id VARCHAR,
phenotype_id INT, phenotype_label VARCHAR, entity_info VARCHAR,
quality_info VARCHAR, attribute_info VARCHAR, taxa_info VARCHAR);

CREATE OR REPLACE FUNCTION getAnatomyInfo(VARCHAR) RETURNS SETOF
anatomyrow AS \$\$ DECLARE

`   result anatomyrow%rowtype;`  
`   qualityRecord RECORD;`  
`   phenotype INT;`  
`   quality VARCHAR;`  
`   entity VARCHAR;`  
`   taxa VARCHAR;`  
`   gene VARCHAR;`  
`   attribute VARCHAR;`  
`   qualityAndAttribute VARCHAR[2];`

BEGIN FOR result IN SELECT DISTINCT 'TAO:0000108' AS search_id,
phenotype_node.node_id as phenotype_id, phenotype_node.uid AS
phenotype_label, 'entity' AS entity_info, 'quality' AS quality_info,
'attribute' AS attribute_info, 'taxa' AS taxa_info FROM node AS
taxon_node INNER JOIN link AS exhibits_link INNER JOIN node AS
phenotype_node INNER JOIN link AS inheres_in_link INNER JOIN node AS
search_node ON (inheres_in_link.object_id = search_node.node_id) ON
(phenotype_node.node_id = inheres_in_link.node_id) ON
(exhibits_link.object_id = phenotype_node.node_id) ON
(taxon_node.node_id = exhibits_link.node_id), node AS
inheres_in_pred_node, node AS exhibits_pred_node WHERE search_node.uid =
'TAO:0000108' AND exhibits_pred_node.uid = 'PHENOSCAPE:exhibits' AND
inheres_in_pred_node.uid = 'OBO_REL:inheres_in' AND
exhibits_link.predicate_id = exhibits_pred_node.node_id AND
inheres_in_link.predicate_id = inheres_in_pred_node.node_id LOOP

`   phenotype := result.phenotype_id;`  
`   qualityRecord := getQualityFromPhenotype(phenotype);`  
`   attribute := readCharacterForState(qualityRecord.quality_id);`  
`   quality := qualityRecord.quality;`  
`   taxa := getTaxaForPhenotype(phenotype);`  
`   entity := getEntityFromPhenotype(phenotype);`  
`   result.search_id := $1;`  
`   result.entity_info := entity;`  
`   result.quality_info := quality;`  
`   result.attribute_info := attribute;`  
`   result.taxa_info := taxa;`  
`   RETURN NEXT result;`

END LOOP; END \$\$ LANGUAGE 'plpgsql';

</source>

### Execution details

The master stored procedure *getAnatomyInfo()* can be invoked from the
client side using a command similar to the one below

\<source lang=sql SELECT \* FROM getAnatomyInfo('TAO:0000108');

</source>

- Rows returned: 69
- Execution time: Approx. 0.25 seconds

### Discussion

This strategy resulted in the fastest execution times. All the required
information is obtained. Moreover, when querying for TAO:0100000, the
root PATO term, this strategy returned approximately 2500 unique
phenotypes with their associated sets of taxa and genes, qualities,
entities, and atttributes in approximately 8 seconds. That is
presumptively every annotation in the database!

## Strategy \#4

This <a href="Queries#Strategy_#4:_Materialized_views" class="wikilink"
title="strategy">strategy</a> involves materializing views for the
following relations:

- *OBO_REL:inheres_in*
- *OBO_REL:is_a*
- *PHENOSCAPE:exhibits*
- *PHENOSCAPE:has_allele*

A stored procedure can be invoked to query from these materialized views
and retrieve the information of interest.

### getAnatomyInfoFromMatViews

\<source lang=sql CREATE OR REPLACE FUNCTION
getAnatomyInfoFromMatViews(VARCHAR) RETURNS SETOF anatomyrow AS \$\$
DECLARE result anatomyrow%rowtype; search_id INT; phenotype_id INT; taxa
VARCHAR\[2\]; taxaRec RECORD; phenRec RECORD; count INT; gene VARCHAR;
qId INT; BEGIN SELECT node_id INTO search_id FROM node WHERE uid = \$1;
PERFORM realize_relation('OBO_REL:inheres_in'); PERFORM
realize_relation('PHENOSCAPE:exhibits'); PERFORM
realize_relation('OBO_REL:is_a'); PERFORM
realize_relation('PHENOSCAPE:has_allele'); FOR phenRec IN SELECT \* FROM
OBO_REL.inheres_in WHERE object_id = search_id LOOP count := 0; taxa :=
NULL; result.search_id := \$1; result.phenotype_id := phenRec.node_id;
result.phenotype_label := node_uid(phenRec.node_id); SELECT
node_uid(object_id) \|\| '(' \|\| node_label(object_id) \|\| ')' INTO
result.entity_info FROM asserted_OBO_REL.inheres_in WHERE node_id =
phenRec.node_id; SELECT node_uid(object_id) \|\| '(' \|\|
node_label(object_id) \|\| ')', object_id INTO result.quality_info, qId
FROM asserted_OBO_REL.is_a WHERE node_id = phenRec.node_id;
result.attribute_info := readCharacterForState(qId); FOR taxaRec IN
SELECT node_id AS TorGid, node_uid(node_id) AS TorG FROM
asserted_PHENOSCAPE.exhibits WHERE object_id = phenRec.node_id LOOP
count := count + 1; IF (taxaRec.TorG LIKE '%TTO%') THEN

`   taxa[count] := taxaRec.TorG;`

ELSE

`   SELECT node_uid(node_id) INTO gene FROM asserted_PHENOSCAPE.has_allele WHERE object_id = taxaRec.TorGid;`  
`   taxa[count] := gene;`

END IF; END LOOP; result.taxa_info := taxa; RETURN NEXT result; END
LOOP; END \$\$ LANGUAGE 'plpgsql';

</source>

### Execution Details

This stored procedure can be invoked by the query

<javascript> SELECT \* FROM getAnatomyInfoFromMatViews('TAO:0000108')
</javascript>

- Time: Approx 0.19 seconds
- Rows returned: 75

### Discussion

This strategy offers the fastest performance yet when the fin
(TAO:0000108) is searched for. When the root TAO entity (TAO:0100000) is
queried, execution times vary between 4 and 9 seconds.

## Publications

Retrieved phenotype data summaries and details needs to be filtered by
publications they originate from. This adds a new dimension to the query
execution. Retrieved data must be displayed in the format shown below
<javascript> Phenotype Taxon Quality Character Entity Publication
</javascript>

### Retrieving publication data by specifying order of TABLE JOINs

This strategy specifies the <a
href="Queries#Strategy_#2:_Specifying_the_order_of_table_joins_in_the_original_query"
class="wikilink" title="order of table joins in the query itself">order
of table joins in the query itself</a> for efficiency. The
<a href="Queries#Relations_of_interest" class="wikilink"
title="relations among phenotypes, characterstatedata, datasets and publications">relations
among phenotypes, characterstatedata, datasets and publications</a> are
leveraged. Given below is a query to retrieve all the phenotypes,
associated taxa, entities, and characters that are taken from one of the
larger publications in the collection in terms of number of curations
viz.*Phylogenetic relationships of North American Cyprinidae* by
Cavender and Coburn.

### Query

\<source lang=sql SELECT DISTINCT phenotype_node.uid AS phenotype,
taxon_node.uid AS taxon_id, taxon_node.label AS taxon_label,
entity_node.uid AS entity_id, entity_node.label AS entity_label,
quality_node.uid AS quality_id, quality_node.label AS quality_label,
character_node.uid AS character_id, character_node.label AS
character_label, publication_node.uid AS publication_id FROM link AS
publication_link JOIN node AS publication_node ON
(publication_link.object_id = publication_node.node_id) JOIN node AS
ds_node ON (publication_link.node_id = ds_node.node_id) JOIN link AS
posited_link ON (posited_link.object_id = ds_node.node_id) JOIN node AS
annotation_node ON (posited_link.node_id = annotation_node.node_id) JOIN
link AS state_link1 ON (state_link1.node_id = annotation_node.node_id)
JOIN node AS csdatum_node ON (state_link1.object_id =
csdatum_node.node_id) JOIN link AS state_link2 ON (state_link2.node_id =
csdatum_node.node_id) JOIN node AS csdomain_node ON
(state_link2.object_id = csdomain_node.node_id) JOIN link AS
phenotype_link ON (phenotype_link.node_id = csdomain_node.node_id) JOIN
node AS phenotype_node ON (phenotype_link.object_id =
phenotype_node.node_id) JOIN link AS inheres_in_link ON
(inheres_in_link.node_id = phenotype_node.node_id) JOIN node AS
entity_node ON (inheres_in_link.object_id = entity_node.node_id) JOIN
link AS is_a_link ON (is_a_link.node_id = phenotype_node.node_id) JOIN
node AS quality_node ON (is_a_link.object_id = quality_node.node_id)
JOIN link AS value_for_link ON (value_for_link.node_id =
quality_node.node_id) JOIN node AS character_node ON
(value_for_link.object_id = character_node.node_id) JOIN link AS
exhibits_link ON (exhibits_link.object_id = phenotype_node.node_id) JOIN
node AS taxon_node ON (exhibits_link.node_id = taxon_node.node_id) WHERE
exhibits_link.is_inferred = 'f' AND is_a_link.is_inferred = 'f' AND
inheres_in_link.is_inferred = 'f' AND exhibits_link.predicate_id =
(SELECT node_id FROM node WHERE uid = 'PHENOSCAPE:exhibits') AND
is_a_link.predicate_id = (SELECT node_id FROM node WHERE uid =
'OBO_REL:is_a') AND inheres_in_link.predicate_id = (SELECT node_id FROM
node WHERE uid = 'OBO_REL:inheres_in') AND value_for_link.predicate_id =
(SELECT node_id FROM node WHERE uid = 'PHENOSCAPE:value_for') AND
state_link1.predicate_id = (SELECT node_id FROM node WHERE uid =
'cdao:has_State') AND state_link2.predicate_id = (SELECT node_id FROM
node WHERE uid = 'cdao:has_State') AND phenotype_link.predicate_id =
(SELECT node_id FROM node WHERE uid = 'cdao:has_Phenotype') AND
posited_link.predicate_id = (SELECT node_id FROM node WHERE uid =
'posited_by') AND publication_link.predicate_id = (SELECT node_id FROM
node WHERE uid = 'PHENOSCAPE:has_publication') AND
publication_link.object_id = (SELECT node_id FROM node WHERE uid LIKE
'%North American Cyprinidae%');

</source>

### Execution details

- Rows returned: 5706
- Execution time: \> 4 min (Too long)

### Discussion

This query is very slow in terms of execution. When the taxon results
are excluded, the query is much faster returning 49 rows (unique
phenotypes documented in this publication) in about 3 seconds. This may
be improved by creating a separate table listing publications, the
phenotypes they describe and the taxa exhibiting these phenotypes that
are recorded in each publication

## Conclusion and potential areas for improvement

From the above discussion, it can be seen the performance of queries
from the SICB prototype can be significantly improved. At present, (Feb
11, 2009), the database contains approximately 122500 phenotype
assertions from the Phenoscape project and roughly 23000 assertions from
ZFIN. While significant additions to the ZFIN assertions are not
expected, the number of assertions in the Phenoscape project are
expected to go up to 7.5 million. Scalability of these querying
strategies can be different from one another. Querying strategies that
entirely depend upon table joins and other relational operations (<a
href="Queries#Strategy_#2:_Specifying_the_order_of_table_joins_in_the_original_query"
class="wikilink" title="Strategies 1 and 2">Strategies 1 and 2</a>)
scale logarithmically; while those that use procedural logic (Strategies
3 and 4) may scale worse than logarithmically (linearly or worse).

On the other hand, the results of the queries executed in 1 and 2 will
have to be parsed on the client side (because of their strict tabular
format shown below) to isolate the taxa or genotypes/genes that are
associated with a specific phenotype. In the example below, client side
parsing of the tabular format will isolate {T1, T2, ...Tn} as the taxa
that exhibit the phenotype P1.

<javascript> P1 E1 Q1 T1 P1 E1 Q1 T2 . . P1 E1 Q1 Tn P2 E2 Q2 GT1 . . P2
E2 Q2 GTn </javascript>

Strategies 3 and 4 however, accumulate these taxa in advance and
associated them with each unique phenotype in a single row. This
requires minimal parsing on the client side, specifically if this is to
be packaged into a JSON object to be delivered to the Phenoscape UI.

### Materializing views for Attribute-Quality (or Character-State) combinations

Given that stored procedures display the
<a href="Query_strategy_performance#Strategy_#4" class="wikilink"
title="fastest execution times">fastest execution times</a>, the
invocation of a procedure that recursively executes SQL queries to
traverse the PATO hierarchy in order to identify characters that subsume
qualities is a bottleneck of its own. This can be overcome by the
creation of a
<a href="Queries#Strategy_#4:_Materialized_views" class="wikilink"
title=" materialized view"> materialized view</a>, which contains the
mapping information from several qualities to a common attribute (or
from several states to a common character), as shown below.

<javascript>

Quality Attribute ------- --------- Blue Color Red Color Round Shape
Bifurcated Shape . . </javascript>

The attribute identification for a quality can be done by simply reading
from this view, which should lead to more savings in query execution
time.

### Comparison parameters

Note that in almost all the queries discussed so far, the query looks up
the node ID for relations such as "*PHENOSCAPE:exhibits*" and so forth.
If these can be statically read in to the client side application during
data load time, hundreds of thousands of lookup operations will be saved
over tens of thousands of queries as a result. The materialized views
option can be used at database refresh/reload time to generate tables
for these relationships so that relation lookups such as these can be
optimized. Alternatively, a feature to update the node ID values on the
client side at every data refresh/reload of the Phenoscape database may
be implemented in the future for this purpose
