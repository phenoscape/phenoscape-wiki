---
title: Queries
permalink: wiki/Queries
layout: wiki
tags:
 - Informatics
 - Database
 - Queries
---

This section describes the queries that have been implemented for the
Phenoscape data services, in addition to the execution details of each
queries on the PostgreSQL database.

### Summary

In the Phenoscape application, queries are assembled in a Java program
and dispatched through a connection to the database, and executed at the
database end. For brevity's sake, the Java program is called the client
side and the database side is called the backend henceforth. The
database has been implemented using the
[PostgreSQL](http://www.postgresql.org/) Relational Database Management
System (DBMS).

Query execution in PostgreSQL occurs in four sequential steps. In the
first step, the query is transferred from the client side over the
network to the database. In the second step, the query is parsed and an
execution plan is drawn up by the PostgreSQL DBMS to retrieve the data
as efficiently as possible in terms of time and memory utilization. In
the third step, the DBMS executes the query as per the drawn up
execution strategy and retrieves the results. In the last step, the
retrieved results are sent back over the connection to the client side.

## Relations of interest

The relations described in this section are of use in finding
information about phenotypes, and are therefore leveraged in the
implementation of the phenotype summary and details modules of the
Phenoscape application.

Post compositions of Entities and Qualities are used to relate taxa (and
genes) and phenotypes through the *exhibits* relation as shown in (1)
and (2). <javascript> Taxon exhibits inheres_in(Quality, Entity) -- (1)
Gene exhibits inheres_in(Quality, Entity) -- (2) </javascript> In
addition, the OBD database also contains information relating post
composed phenotypes to both the Quality and the Entity by different
relations as shown in (3) and (4) respectively <javascript>
inheres_in(Quality, Entity) is_a Quality -- (3) inheres_in(Quality,
Entity) inheres_in Entity -- (4) </javascript> Quality is related to
Character by the *value_for* relation as shown in (5) <javascript>
Quality value_for Character -- (5) </javascript>

Phenotypes can also be traced back to the publications and datasets they
are extracted from as explained below. Phenotype data summaries and
details retrieved by the services modules of Phenoscape are filtered by
publications as well.

Every dataset is associated with a publication as shown in (6). The list
of link statements posited by a dataset can be retrieved by traversing
the relation shown in (7) <javascript> DataSet has_publication
Publication -- (6) LinkStatement posited_by Dataset -- (7) </javascript>
