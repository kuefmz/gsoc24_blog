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
    ] .* 01/08
le.org/ontology/2024-01-24>
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
- Brainstorming about the dependency based mode
    - Focused on three key areas:
        - owl:version IRI
        - owl:versionInfo
        - dc:date
- Probably another tool would be needed to generate the file with the dependency (outside of the scope of this project)
- Checksum on the Canonicalized Ontology
    - This will assist in verifying if the version being referenced is correct.
    - Note: Currently unable to check which versions are present on external data sources or repositories
- Goal: Emphasize the use of owl:versionInfo for version tracking.
- Command Line Tool for Checksums
- Aim to create a command-line tool for managing checksums, especially for large files or datasets.
- Dependency file creation: Manually generating the dependency file should be part of the ontology engineering workflow.


Next steps:
- Define dependencies:
    - When a request for a new ontology version is received, return the correct version based on pre-defined dependencies.
- Handle single dependency:
    - If the version does not match the dependency, an error should be thrown.
- Wrap up tests related to dependency handling.
