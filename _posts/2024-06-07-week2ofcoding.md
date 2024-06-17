---
layout: post
title:  "Coding period - 2nd week"
date:   2024-06-07
author: "Jenifer Tabita Ciuciu-Kiss"	
categories: progress
---

This week I created my first pull request with the following updates:

- Set up the project
- Create poetry venv
- Set up the HTTP proxy
- Implement the failover mode
- Add testcases
- Add GitHub action for running the tests

Johannes reviewed it and he gave me the following feedback:
- I think there is still a litte misunderstanding what a proxy does. a proxy forwards http requests to the server and returns them to the client. It is NOT a webserver on its own or a reverse-proxy. so in other words it forwards the get requests but does not serve get requests on its own like you did at the moment.

We had a follow-up discussion to clear the misunderstandings and I also received the following resources:
- Example proxy 116.203.28.43 port 80
- https://en.wikipedia.org/wiki/Proxy_server --> Our aim is a transparent proxy
- https://httptoolkit.com/ allows to see the connections locally
- Note that the transparent proxy has multiple meaning: https://serverfault.com/questions/916610/whats-the-difference-between-transparent-proxy-and-explicit-proxy
- https://github.com/richardg867/WaybackProxy/tree/master
- This might be useful for academic purposes: https://github.com/inaz2/proxy2/blob/master/README.md
- Aso pretty cool and more powerful then proxy.py seems this mitmdump. it also has a little example for redirection what we need: https://docs.mitmproxy.org/stable/addons-examples/#http-redirect-requests
- https://proxypy.readthedocs.io/en/latest/#embed-proxy-py 
- https://github.com/abhinavsingh/proxy.py/tree/develop/skeleton


Johannaes also gave me access to the DBpedia server.

During the meeting we discussed all of the above. The next step is to rewrite the proxy accordingly and to have another meeting for the steps after the basic setup is done correctly.
