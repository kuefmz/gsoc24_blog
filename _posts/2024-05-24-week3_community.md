---
layout: post
title:  "Communty bonding period - 3rd week"
date:   2024-05-24
author: "Jenifer Tabita Ciuciu-Kiss"
categories: progress

---

This week I was provided with this tool that I can use to look up which ontology a term belongs to:
- http://tools.dbpedia.org:9274/lookup-application/api/search?query=Person


We also had a long meeting with my mentors discussing all the details of the first phase and the next steps. Here is a summary of the discussion:


### Transparent Proxy


The Proxy has two modes:

- fail over (in the case a term or ontology is requested, but is not available online/at its IRI, so it takes the most recent version from archivo)
- time travel (the proxy is configured to always answer from archivo by taking the version according to one of the following strategies)
    - time travel (Based on a time stamp the ontology version is selected, closest or last; time > snapshot)
    - dependency-lock (based on a dependency description, see below, that is specified in the dependency description)



#### Infer the Ontology IRI from on a Term (Class, Property)

##### Explicit Semantics

Based on rdfs:isDefinedBy unfortunately is not available, if the ontology is not available.

##### Additionally: Distinguish between multiple statements

We have to identify the authoritative source. E.g. based on the IRI substring.

##### Using the SOLR Index

##### Based on the IRI

Caveat: Hash-IRIs vs. Slash-IRIs.
Remove the ""last part" (what ever is the "last part") from the IRI.

- http://xmlns.com/foaf/0.1/Person
- http://www.w3.org/2000/01/rdf-schema#label




### Dependency

Assume you have some ontology:

```
@prefix myont: <http://example.org/myontology/> .
@prefix foaf: <http://xmlns.com/foaf/0.1/> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
```

myont:Cook rdfs:subClassOf foaf:Person.


This Ontology would depend on the foaf-Ontology.

Dependency can be a general dependency, but could also be a dependency on a specific version of an Ontology.


#### general dependency

myont: - depends on → foaf:


#### specific version

myont: - depends on → foaf from 2014-01-14 13.37


## Next steps:
- Find a Python Library that can be used for the Proxy
- Create the Proxy
- Set up PyTest test cases
    - Test whether the proxy is working, and return a static string in case of a specific URI
    - Test this properties:
        - https://archivo.dbpedia.org/info?o=http://ontologi.es/days#
        - https://archivo.dbpedia.org/info?o=http://linked-web-apis.fit.cvut.cz/ns/core
- Set up CI in GitHub for running the tests
