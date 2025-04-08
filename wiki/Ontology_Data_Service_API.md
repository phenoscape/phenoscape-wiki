---
title: Ontology Data Service API
permalink: wiki/Ontology_Data_Service_API
layout: wiki
tags:
 - Informatics
 - API
redirect_from:
 - wiki/Ontology_Service_API_Break-out_Group
 - wiki/Public%3AOntology_Data_Service_API
---

*This is a legacy high-level specification of a common programmatic API
needed by EQ editors (such as
<a href="Phenex" class="wikilink" title="Phenex">Phenex</a> and
[Phenote](http://phenote.org)) to interface with ontology (and
phenotype) repositories. It resulted from a breakout group, consisting
of C. Mungall, J. Balhoff, and H. Lapp, of the
<a href="Fish_Evolution_Working_Group" class="wikilink"
title="Fish Evolution Working Group">Fish Evolution Working Group</a> at
their last meeting in November 2006, and served as part of the early
input to the web-service design of the Bioportal.*

*This specification as such has not been implemented in the [Phenoscape
Knowledgebase](http://kb.phenoscape.org) (KB), though some functions
proposed here are among the implemented
<a href="Data_Services" class="wikilink" title="Data Services">Data
Services</a> (for example "Look up term" as
<a href="Data_Services#Term_info" class="wikilink" title=" Term Info">
Term Info</a> and "Completion list" as
<a href="Data_Services#Autocomplete" class="wikilink"
title=" Autocomplete"> Autocomplete</a>. Also, the Bioportal meanwhile
has a [full-featured REST
API](http://www.bioontology.org/wiki/index.php/NCBO_REST_services) that
does implement all of the ontology-specific functions enumerated below,
and the Phenoscape KB
<a href="Data_Services" class="wikilink" title="Data Services">Data
Services</a> implement a much richer set of phenotype annotation
services than envisioned below (albeit read-only).*

## Goal and motivation

A common API implemented by ontology data services enables clients such
as EQ editors that heavily rely on such a service to plug into different
data providers, local or remote, at their choice.

## Service definitions

### Ontology Data Service

1.  Ontology listing lookup
    - Function: lookup the ontologies being served by the data service
    - Input: none, or a particular name, and/or the name of the ontology
      category
    - Output: a record of name, version, identifier, meta-data (e.g.,
      retired? in production? purpose?) for each ontology being served
2.  Look up term
    - Function: Obtain the full term information for a given ID
    - Input: a term ID, or the combination of a term name and ontology
      ID
    - Output: the matching term in OBO or RDF/OWL format
    - Notes: do we need neighborhood here too (e.g., with IDs only); OBO
      only has parents, not children.
3.  Completion list
    - Function: Obtain matching term names for a partial term name
      string
    - Input: partial term name string, a list of ontology IDs, search
      parameters (search names only or synonyms only or both, search
      obsoletes or not, search definition or not)
    - Output: matches as records of term name, term ID, ontology ID,
      synonym that was hit, how the term was hit (name, synonym, or
      definition)
4.  Neighborhood graph
    - Function: Obtain parents, children, descendants, or ancestors for
      a given term
    - Input: term ID, list of relationships to include or exclude,
      number of levels (path length) up and down to include
    - Output: list of terms in OBO or RDF format
    - Note: Is it sensible to return a graph as OBO format? Do we need
      to mandate the semantics of matching mixed-type paths (e.g., is-a
      and part-of)?
5.  Downloading ontology
    - Function: Obtain all terms and relationships comprising an
      ontology
    - Input: ontology ID, optionally name of the slim
    - Output: the ontology as an OBO or OWL stream of text
    - Notes: do we need a parameter for specifying the desired format?
      do we need parameter for including obsoletes or not
6.  SPARQL endpoint
    - Function: Issue SPARQL queries and obtain the results in RDF
    - Input:
    - Output:

**Notes applicable to all:**

- Do we need to add search parameter to specify the 'slim' for each
  service that involves specifying an ontoloy?
- Should we have a protocol for client and server negotiating the
  desired return format, or should this be a parameter (in which case we
  also need a method to obtain all supported formats from the server)?

### Phenotype Data Service

1.  Login
    - Function: Given a username and secret, obtain an authentication
      token
    - Input:
    - Output:
2.  Save EQ statements
    - Function: Save an array of EQ statements to the data store
    - Input: a list of EQ statements on OBD-xml or pheno-xml format
    - Output: success/failure indicator
3.  Load EQ statements
    - Function: Load an array of EQ statements from the data store
    - Input: author, or list of taxa,
    - Output: matching EQ statements in pheno-xml or pheno-syntax format
    - Notes: do we need parameter of list of entities to obtain EQs for?

### Query languages

- SPARQL

### Data exchange formats

- Plain text over HTTP:
  - OBO format
  - YAML
  - JSON

<!-- -->

- XML over HTTP:
  - OBO-XML format
  - OBD-XML format

<!-- -->

- RDF over HTTP:
  - RDF/XML
  - RDF/N-triples

## Other ontology service definitions

- [Ontology Lookup Service (OLS)](http://www.ebi.ac.uk/ontology-lookup/)
  at the EBI[^1]. According to the website, the OLS can integrate any
  ontology available in OBO format. OLS is implemented as a web-service.
  The website has documentation on
  - [web-service
    API](http://www.ebi.ac.uk/ontology-lookup/WSDLDocumentation.do)
    (representing the WSDL) with [JavaDoc for the interface
    contract](http://www.ebi.ac.uk/ontology-lookup/api/uk/ac/ebi/ook/web/interfaces/QueryImpl.html),
    and
  - [implementation
    overview](http://www.ebi.ac.uk/ontology-lookup/implementationOverview.do)
    (architecture)
  - OLS also provides 3 ReST-style services, similar to some of the
    lookups described above. These queries return a simple key-value XML
    format.
    - Term info:
      <http://www.ebi.ac.uk/ontology-lookup/ajax.view?q=termmetadata&termid=ID&ontologyname=LABEL>
    - Completion list:
      <http://www.ebi.ac.uk/ontology-lookup/ajax.view?q=termautocomplete&termname=NAME&ontologyname=LABEL>
    - Term name for ID:
      <http://www.ebi.ac.uk/ontology-lookup/ajax.view?q=termname&termid=ID&ontologyname=LABEL>
- The NCBO
  [BioPortal](http://www.bioontology.org/ncbo/faces/index.xhtml)
  supports a [SOAP-based web-service
  API](http://www.bioontology.org/docs/bioportal/development/web_services.html):
  - WSDL:
    <http://www.bioontology.org/ncboservicebeans/NCBOWebserviceBean?wsdl>
  - Java JUnit test:
    [test.webservice.NCBOServiceTest](http://smi-protege.stanford.edu/repos/cbio/ncbo/trunk/test/webservice/NCBOServiceTest.java)
- The [Zthes profile for
  SRU](http://zthes.z3950.org/srw/zthes-srw-1.0.html) is a specification
  for navigating and querying remote thesauri
  - [SRU](http://www.loc.gov/sru/) is a Library of Congress-sponsored
    standard for query interoperability between digital repositories
  - The Zthes profile for SRU is based on an [abstract model for
    thesaurus
    representation](http://zthes.z3950.org/model/zthes-model-1.0.html),
    which is also available as an XML Schema implementation.

## Next Steps

1.  Finalize list of services for the ontology data service API.
    - This will be an initial revision 1.0 - we'll surely have
      iterations later down the road.
    - We'll need an acronym - anyone had a flash of creativity? What
      about OBODS
2.  Define which services are mandatory, and which are optional.
3.  Decide on protocol and query syntax.
    - What about using REST, e.g.,
      <http://onto.myorg.edu/obods?q=list_ontology&category=anatomy>, or
      using paths
      <http://onto.myorg.edu/obods/ontology/list?category=anatomy>)
4.  Create a reference implementation for the server.
    - A very generic reference implementation would be a wrapper over a
      SPARQL endpoint, i.e., translating API calls into SPARQL queries
      and transforming returned RDF into the required format.
5.  Create a reference implementation for a web-application client
    (using JavaScript) and for, e.g., a Java client (for servlets or
    Java stand-alone apps).

## References

<references />

[^1]: <pubmed>16507094</pubmed>
