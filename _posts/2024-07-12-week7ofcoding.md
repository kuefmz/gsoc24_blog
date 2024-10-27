---
layout: post
title:  "Coding period - 7th week"
date:   2024-07-12
author: "Jenifer Tabita Ciuciu-Kiss"	
categories: progress
---



The progress of the week:
- This week I was working on the testcases. 
- Adding issues to GitHub corresponding to both the Project proposal and development.
- Make sure that the parameters work properly according to the description.
- Finalized the PR on ontology Archivo: https://github.com/dbpedia/archivo/pull/48


Discussion:
- We discussed the questions I had regarding the project.
- Natanael recommended to switch form argparse to click (https://click.palletsprojects.com/en/8.1.x/)
- I had some issues with setting up the testcases, the plan is to switch to the Proxy.py unittest (https://proxypy.readthedocs.io/en/latest/#unit-testing-with-proxy-py)
- Some additional resources for the parameter: 
    - https://docs.pytest.org/en/7.1.x/example/parametrize.html
    - https://docs.pytest.org/en/7.1.x/how-to/parametrize.html#parametrize-basics
- I had an issue with intercepting only the in scope HTTPS request, for which we agreed on opening a discussion here: https://stackoverflow.com/help/minimal-reproducible-example
- HTTPS SSL Issue
    - Addressing HTTPS SSL interception, specifically with out-of-scope URLs.
- Task and Issue Tracking
    - Plan to add actual tasks to GitHub issues to keep better track of progress and problem areas.
- Project Tools and Testing
    - ClickPoject: Used for creating argparse interfaces for ease of interaction.
    - Unittesting proxy.py: Can be utilized to verify parameter handling.
    - Python Unittest: Generate relevant test cases to ensure functionality.
- Mini-project for HTTPS Interception
    - Proposal to create a mini-project to demonstrate HTTPS interception and contribute to the ongoing proxy discussion.
    - Goal: Minimal Working Example for reproduction.
- Dependency-Based Model
    - Concept of creating a base/manifest file with exact versions to use:
    - Define base files to investigate existing ontology dependencies.
    - Resolve naming conventions (e.g., base vs. name).
    - Ideal solution: design an ontology for dependency management in RDF.

Next steps:
- Start a new discussion about the ontology intercept
- Start the proxy with different parameter setups for testing
- Check out how some package managers generate the dependencies


Some notes:
- The scope of the project slightly extended compared to the proposal, which causes some delay, therefore the project will probably be extended by a few extra weeks to make sure that the project is properly implemented and delivered.

