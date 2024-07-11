---
layout: post
title:  "Coding period - 4th week"
date:   2024-06-21
author: "Jenifer Tabita Ciuciu-Kiss"	
categories: progress
---



The progress of the week:
- Change prints to logging
- Improve README
- Fix the HTTPS interception

Discussion:
- The HTTPS intercetion works locally, but not on the deployed version, brainstoming on what the issue might be.
- How should we treat the different status codes.
- How should we implement the parameters that we want to add to the proxy, like the mode to be used and the timestamp in case we need any.
- An HTTPS request is basically the same as the HTTP request after a CONNECT method, make sure this is treated accordingly.

Next steps:
- Handle the HTTPS requests correctly.
- Implement the functionalities in case of the different status codes.
- Make sure that the deployed proxy also works correctly.



