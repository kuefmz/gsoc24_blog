---
layout: post
title:  "Coding period - 1st week"
date:   2024-05-31
author: "Jenifer Tabita Ciuciu-Kiss"	
categories: progress
---

Progress since last week:
- Setting up the project structure
- Set up poetry virtual environment
- Create the basic structure of the proxy with the http library and I used the threading library in Python to spin up the HTTP proxy server on a new thread
- Added 2 test cases to check that the proxy is up and running and behaves as expected

We had a meeting with my mentor and we had a short discussion about how the proxy should behave in the failover mode and in the time based mode.

Next steps:
- Set up CI in GitHub actions.
- Implement the failover mode:
    - If the IRI is throwing and error (404, 500, etc.) catch that and return the correct ontology using the Archivo API:
        - The DBpedia Archivo API: https://archivo.dbpedia.org/download?o={ontology}&f={format}
    - The the IRI doesn't return an error, check if the content type corresponds to an ontology format or not, and in case it doesn't follow the previous approach.
- Add test cases for the following IRIs:
    - http://linked-web-apis.fit.cvut.cz/ns/core
    - https://archivo.dbpedia.org/info?o=http://ontologi.es/days#
- Work on the time based mode, in case the ontology is asked from a specific point in time, return the relevant snapshot.
    - If a snapshot from that specific time doesn't exist, there are two options:
        - Use another Archivo API to check the available snapshots and chose the most relevant one.
        - Patch the existing Archivo API and implement a similar logic there.

Johannes will give me access to a server where we can deploy the proxy and therefore it can be used and tested externally.