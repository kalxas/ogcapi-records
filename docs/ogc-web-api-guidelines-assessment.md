# OGC API Records Support of OGC Web API Guidelines (Part 1)

This document outlines the support by OGC API Records of the design principles of the [OGC Web API Guidelines](https://github.com/opengeospatial/OGC-Web-API-Guidelines).

- [x] Principle #1 – Don’t Reinvent
  - consistent with the current architecture of the web, leverages existing, widely used and implemented specifications (e.g. HTTP/HTTPS, Web Linking, OpenAPI, HTML, schema.org, GeoJSON, JSON Schema, DCAT), follows existing practices where no commonly used standard exists (e.g. how paging is implemented or how links are encoded) and only adds minimal additional requirements consistent with the [W3C/OGC Spatial on the Web Best Practices](https://www.w3.org/TR/sdw-bp/)
- [x] Principle #2 – Keep the API Simple and Intuitive
  - the scope of Part 1 is limited to capabilities that almost anyone needs who wants to share record data on the Web via a record-oriented API; the API building blocks are consistent with the current Web architecture and straightforward to understand by web developers
  - the spatial concepts introduced in Part 1 are minimal (just bbox, only a single CRS following common practice)
  - all query parameters are optional with default values that will produce meaningful responses
  - more advanced capabilities like support for coordinate reference systems or richer selection criteria are added in additional parts for those that needs them, but still with a focus on support for capabilities needed by many
- [x] Principle #3 - Use Well-Known Resource Types
  - records and catalogs are resource types that have been in use for many years
  - IANA registered media types are used, except in the OpenAPI case, where [no registered media type exists yet](https://github.com/OAI/OpenAPI-Specification/issues/110)
- [x] Principle #4 – Construct consistent URIs
  - the resources are structured in a [simple path structure](https://docs.ogc.org/DRAFTS/20-004.html#api-path-table) that is intuitive and at the same time extensible (both for additional parts of Records that will make use of other HTTP methods beyond GET, HEAD, OPTIONS or add resources as well as for other top-level OGC API resource types)
  - the path structure is consistent with the examples in Principle #4
- [x] Principle #5 – Use HTTP Methods consistent with RFC 9110
  - Part 1 uses GET (and recommend support for HEAD and OPTIONS). All methods are used in conformance with the requirements and semantics specified in RFC 9110
- [x] Principle #6 – Put Selection Criteria behind the ‘?’
  - selection criteria for the representation are query parameters (Part 1: `bbox`, `datetime`, `limit`, `q`, `type`, `ids`, `externalIds`, `filter`, `filter-lang`, `filter-crs`).
- [x] Principle #7 – Error Handling and use of HTTP Status Codes
  - HTTP status codes are used to represent the semantics of the response, because they are commonly understood by web developers; implementations are encouraged to provide meaningful error messages to clients
  - no normative schema for exceptions has been specified, the current developments in IETF ([revision of RFC 7807](https://github.com/ietf-wg-httpapi/rfc7807bis)) are monitored and RFC 7807 or its successor may be recommended in the future
- [x] Principle #8 – Use explicit list of HTTP Status Codes
  - see [HTTP Status Codes](https://docs.ogc.org/is/17-069r3/17-069r3.html#http_status_codes) and the more detailed guidance for each resource in the document
- [x] Principle #9 – Use of HTTP Header
  - all HTTP headers can be used as specified by the HTTP RFCs
  - the headers `Accept`, `Accept-Language` and `Link` (specified in RFC 8288) are in particular relevant and discussed in the document
  - for the GML encoding, where we cannot include some response information in a valid GML-SF record collection, this information is returned in HTTP headers
- [x] Principle #10 - Allow flexible Content Negotiation
  - see Principle #9, server-driven content negotiation is supported
- [x] Principle #11 - Pagination
  - pagination as described in the principle is fully supported for records (offset pagination is not required, since this is a problem for some backends)
  - future parts may add paging for APIs that serve many collections
- [ ] Principle #12 – Processing Resources
  - not applicable; currently OGC API Records does not expose any processing resources
- [x] Principle #13 – Support Metadata
  - each resource provides the metadata for using the API
  - to keep the API simple and intuitive only the minimal metadata is specified
  - additional metadata can be added or referenced using links; in some cases, this is required (`service-desc`, `service-doc`) or recommended and used in examples (`license`, `describedby`).
- [x] Principle #14 – Consider your Security needs
  - supports HTTPS and RFC2818
  - includes authentication status codes in the list of HTTP status codes highlighted in the standard
  - the standards discuss security considerations
- [x] Principle #15 – API Description
  - supports OpenAPI for API documentation (`service-desc`) and requires also a human readable API documentation (`service-doc`)
  - does not require OpenAPI 3.0 and is open for other API description formats
- [x] Principle #16 - Use well-known identifiers
  - uses media types and link relations types that are registered with IANA, where available
  - extensions will be registered in the OGC Definitions Server (the registers have just recently been created)
- [x] Principle #17 - Use explicit relations
  - the link relation types for the links between the resources are specified by the standards
  - recommendations are provided for link relations to external resources (see also Principle #13)
  - no guidance is provided for relations between records as this is considered outside of the scope of the existing parts of OGC API Records
- [x] Principle #18 - Support W3C Cross-Origin Resource Sharing
  - the importance to support cross-origin requests is [highlighted in the standard](https://docs.ogc.org/is/17-069r3/17-069r3.html#cross_origin)
  - CORS is listed as the first option
- [x] Principle #19 - Resource encodings
  - there is no mandatory encoding that implementations have to support (to avoid a lock-in to a specific encoding since preferences can and will change with time)
  - support for both HTML and JSON/GeoJSON as encodings is recommended (and most API deployments support both)
- [x] Principle #20 - Good APIs are testable from the beginning
  - all published parts include an abstract test suite with detailed test cases
  - all parts are tested with running client and server code before they move to the approval phase
- [x] Principle #21 - Specify whether operations are safe and/or idempotent
  - Parts 1 is restricted to safe and idempotent operations via HTTP GET
- [x] Principle #22 – Make resources discoverable
  - OGC API Records by design supports the ["Make your spatial data indexable by search engines" best practice](https://www.w3.org/TR/sdw-bp/#indexable-by-search-engines) through its recommendation for HTML support and the fact that clients, including crawlers, can follow links to the resources
- [x] Principle #23 - Make default behavior explicit
  - all requests work without a query parameter (see Principle #2)
  - defaults are documented in the API definition (and in the standard, where applicable)