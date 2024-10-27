---
layout: post
title:  "Coding period - 13th week"
date:   2024-08-23
author: "Jenifer Tabita Ciuciu-Kiss"
categories: progress
---

## Progress

- Archivo PR
    - New PR for Archivo is ready for review and has been merged.
- Ontology Retrieval and Code Cleanup
    - Improved retrieval of ontology IRIs with the get ontology function.
    - Began cleaning up the codebase and restructuring the configuration dictionary.

## Discussion
- Parameter handling and interface design
    - Question on parameter management:
    - Considering placing main components outside proxy.py to enhance interface design.
    - Aim to improve flexibility by making the interface more modular.
- Factory function implementation
    - Passing parameters to a factory function to create objects with necessary setups.
    - Monkey Patching:
        - Implemented for customization in specific areas:
            - URL edges
            - Parameterizing plugins for customization.
        - Factory function outputs a new plugin object, facilitating introspection.

## Next steps
- Fixes and testcases: Working on fixing issues and adding test cases to validate functionality.
- Code Cleanup: Continue refining the code for readability and efficiency.
- Authentication: Implement basic HTTP authentication.
- API Review: Assess the current API structure for potential improvements.