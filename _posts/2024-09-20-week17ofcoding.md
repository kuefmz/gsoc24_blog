---
layout: post
title:  "Coding period - 17th week"
date:   2024-09-20
author: "Jenifer Tabita Ciuciu-Kiss"
categories: progress
---

## Progress

- Continued the discussion and the implementation of the parameters of the proxy.

Here is a summary of the final results

configuration options (incomplete sketch)

-  defaultOntoVersion: (default originalFailoverLive)
    -  original
        -  intercept requests but serve the original upstream ontology response, NOTE if ontoFormat patchAcceptUpstream option is true, the Accept headers modified. This can be useful for debugging e.g. analyzing which files (or ontologies) requests are being made.
    -  originalFailoverLiveLatest
        -  proxy tries do determine live during performing the request if there is an accessibility failure and hands over to Archivo to serve the latest version from there in case a failure is detected
    -  originalFailoverArchivoMonitor (NOTE: maybe later since not easy / no API call in Archivo availble for it yet)
        -  proxy determines accessibility healthiness of the ontology from the Archivo crawling monitor state and hands over to Archivo if is reported as inaccessible by Archivo
    -  latestArchived 
        -  proxy always serves the latest version of an ontology directly from Archivo (if it is contained in it). This can be considered as the most robust mode in terms of accessibility (can e.g. be useful if the original hosted version has syntax errors in RDF since partially recovered files are served from Archivo)
    -  timestampArchived <timestamp>
        -  proxy always serves the version of an ontology directly from Archivo (if it is contained in it)
    -  dependencyManifest <fileIRI>
-  ontoFormat: has 2 required + 1 optional arguments  (default is ntriples,enforcedPriority,false)
    -  format: desired representation of the (ontology) resource
        -  one of "turtle" "ntriples" "rdfxml" "htmldocu" 
    -  precedence: of the desired format over the clients Accept headers - one of
        -  default
            -  format is used as default fallback for Accept header if no format specified in Accept header by the client 
        -  enforcedPriority
            -  boost priority of the specified format as highest even if client specified other formats with higher priority BUT ONLY if this format is specified in the Accept Header or the header is empty 
                -  e.g. if enforcedPriority ntriples
                -  client sends: turtle only → no change to Accept header
                -  clients sends: turtle, ntriples → ntriples will be added with the highest priority meaning in the beginning of the Accept string with 1.0 score
        -  always 
            -  ignore the clients preferences in the Accept header
        -  NOTE: by default these parameters only have an effect on requests that are served by Archivo. If they should be applied to all upstream connections use patchAcceptUpstream
        -  ATTENTION:  when using  default  or enforcedPriority mode an HTTP error code 406 is thrown if the request triggered that the content has to be served from Archivo but no supported format matches the (modified) Accept header (e.g. Accept header is just JSON-LD)
    -  patchAcceptUpstream (optional default: false)
        -  defines if the Accept Header is only patched for proxy internal behavior or whether it is actually sent in the changed form to the upstream server
-  restrictedAccess (default: disabled) enable mode to only serve requests to URLs of Archivo ontologies all others are denied/discarded by sending a proxy status 407 response and a message that you need to deploy your own proxy instance to make that work. 
    -  
-  httpsInterception (if a CA cert is provided this option can be used to control HTTPs interception for specific set of fully qualified domain names FQDNs, default is none)
    -  none (default)
        -  no https interception is performed but the request is passed through. NOTE: when hosting this publicly this can be abused by clients to connect to any port and e.g. send spam messages.
    -  block
        -  all https connections will be blocked
    -  archivo 
        -  https interception only for FQDNS that have at least one ontology in Archivo
            -  CHALLENGE: @Jenifer Tabita Ciuciu-Kiss need to fetch this list on startup and keep it up to date during runtime from this here e.g. https://databus.dbpedia.org/ontologies/archivo-indices or novel archivo API call
            -  NOTE: this will block also 
    -  all
        -  for every request to every domain (FQDN)
    -  allNotLocal
        -  for every FQDN but not loopback addresses localhost, ::1, 127.0.0.1/32
    -  <authority-list-file>
        -  path to a file with a list of FQDN entries for which https should be intercepted
    -  manifest ???
        -  apply based on dependency manifest
-  authMode (default: off)
    -  off (no auth required)
    -  basic auth with user provide password and username on startup  --auth user:pass
    -  time travel timestamp (username provides timestamp)
    -  apply request based configuration
-   proxyXffHeaders (default: false)
    -  true 
        -  add https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Forwarded-For and https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Via headers for every http and intercepted https request
    -  false
-  disableRemovingRedirects (default: false) 
    -  if true do not remove redirects but return them. NOTE; if this set to TRUE too many redirects errors will not be detected. Note that this only will have an effect on http and intercepted https connections.
-  SubjectBinarySearchThreshold

