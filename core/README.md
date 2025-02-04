
# OGC API - Records - Part 1: Core

This folder contains the content for the OGC API - Records - Part 1: Core standard.

The repo is organized as follows:

* standard - the main standard document content
  - organized in multiple sections and directories
* openapi - normative OpenAPI components specified by the standard
* examples - JSON and XML examples

## Building

```
cd core

docker run -v "$(pwd)":/metanorma -v ${HOME}/.fontist/fonts/:/config/fonts  metanorma/metanorma  metanorma compile --agree-to-terms -t ogc -x html standard/document.adoc
```
