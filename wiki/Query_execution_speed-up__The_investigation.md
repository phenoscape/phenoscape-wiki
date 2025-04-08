---
title: Query execution speed-up: The investigation
permalink: wiki/Query_execution_speed-up%3A_The_investigation
layout: wiki
---

A number of potential factors affect the performance of the queries that
are executed on the Phenoscape database. These can be classified under a
few major categories:

- Hardware: This has to do mainly with the database server configuration
- RDBMS
- Database schema
- Querying strategy

The last category has been discussed at some length in the
<a href="Queries" class="wikilink" title="Queries">Queries</a> page.
This page mainly presents the findings in the other categories and
proposes possible steps to improve these

## Hardware

The Phenoscape database is currently hosted on a production server. The
size of the database (as on August 21, 2009) is approximately 3.6 GB.

## Software

The querying module for the Phenoscape API has been implemented
primarily in Java (version 1.5). Much of the code has been inherited
from the [BBOP group](http://www.berkeleybop.org/). An extensible Shard
interface has been developed by the BBOP team to encapsulate a variety
of data repositories ranging from conventional relational databases to
RDF triple stores. The Shard interface and the classes that implement it
such as the AbstractShard and the OBDSQLShard contain method definitions
that can retrieve data from the repositories by executing SQL or more
XML based query formats. For the RDBMS-based implementation of the Shard
interface, stored procedures have also been developed to both populate
the database and query it.

## RDBMS

The Phenoscape data is stored in a database that is managed through the
PostgreSQL RDBMS (Version 8.3.3).

## Database Schema

The database schema includes the tables, views and functions that go
into the Phenoscape database. There are 18 tables in the public schema
of the database of which, the NODE and the LINK tables are the most
important and most frequently accessed. Other important tables such as
ALIAS and DESCRIPTION are also accessed when the Auto Completion service
of the Phenoscape application is invoked. There are over 200 views
stored into the database, many of which are used to retrieve data
directly for query implementations on the OBDSQLShard.

- Indexes on the NODE table have been created on 'label' and 'source.'
  To this, an index on 'uid' has been added.
- Indexes on the LINK table have been created on 'node', 'predicate',
  and 'object,' apart from combinations of 'node' and 'predicate,'
  'predicate' and 'object,' 'node' and 'object,' and finally 'node,'
  'predicate,' and 'object' triples.
