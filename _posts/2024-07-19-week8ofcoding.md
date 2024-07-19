---
layout: post
title:  "Coding period - 8th week"
date:   2024-07-19
author: "Jenifer Tabita Ciuciu-Kiss"	
categories: progress
---


The progress of the week:
- Added all the issues to GitHub with the corresponding labels
- Started a discussion about the HTTPS interception issue in the Proxy.py repository: https://github.com/abhinavsingh/proxy.py/discussions/1432
- Read up on how the requirements for existing package managers are generated

Here is an examples RDF that we want to use to define the dependencies in RDF:

```
@prefix ex-version: <https://example.org/versioning/>
<https://example.org/ontology/> owl:imports <http://xmlns.com/foaf/spec/>, <http://purl.org/dc/terms/> ;
    ex-version:current <https://example.org/ontology/2024-01-24> ;
    ex-version:version
    <https://example.org/ontology/2024-01-24> ,
    [
         ex-version:snapshot <https://databus.dbpedia.org/ontologies/w3.org/2020--example/2023.02.11-215415> ;
         ex-version:file <https://archivo.dbpedia.org/download?o=https%3A//example.org/ontology/&f=ttl&v=2023.02.01-215415> ;
         ex-version:dependency <http://xmlns.com/foaf/spec/20100101.html>, <https://databus.dbpedia.org/ontologies/w3.org/2020--dct/2020.05.23-215415> ;
    ] .
    
<https://example.org/ontology/2024-01-24>
    ex-version:snapshot <https://databus.dbpedia.org/ontologies/w3.org/2020--example/2024.01.24-215415> ;
    ex-version:file <https://archivo.dbpedia.org/download?o=https%3A//example.org/ontology/&f=ttl&v=2024.01.24-215415> ;
    ex-version:dependency <http://xmlns.com/foaf/spec/20140114.html>, <https://databus.dbpedia.org/ontologies/w3.org/2020--dct/2020.05.23-215415> ;
]
    

<http://xmlns.com/foaf/spec/20100101.html> ex-version:snapshot <http://xmlns.com/foaf/spec/20100101.html> ;
    ex-version:file <http://xmlns.com/foaf/spec/20100101.rdf> .
         
<http://xmlns.com/foaf/spec/20140114.html> ex-version:snapshot <http://xmlns.com/foaf/spec/20140114.html> ;
    ex-version:file <http://xmlns.com/foaf/spec/20140114.rdf> .
    

<https://databus.dbpedia.org/ontologies/w3.org/2020--dct/2020.05.23-215415> ex-version:snapshot <https://databus.dbpedia.org/ontologies/w3.org/2020--dct/2020.05.23-215415> ;
    ex-version:file <https://archivo.dbpedia.org/download?o=http%3A//purl.org/dc/terms/&f=ttl&v=2020.05.23-215415> .

```


Discussion:


Next steps:

