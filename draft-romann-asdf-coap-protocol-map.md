---
v: 3
coding: utf-8

title: >
  Semantic Definition Format (SDF): Protocol Mapping for the Constrained Application Protocol (CoAP)
abbrev: SDF Protocol Mapping for CoAP
docname: draft-romann-asdf-coap-protocol-map-latest

category: std
submissiontype: IETF
consensus: true

area: "Applications and Real-Time"
workgroup: "A Semantic Definition Format for Data and Interactions of Things"
keyword: Internet-Draft

venue:
  group: "A Semantic Definition Format for Data and Interactions of Things"
  mail: "asdf@ietf.org"
  github: "JKRhb/sdf-coap-protocol-map"

author:
  - name: Jan Romann
    org: Universität Bremen
    email: jan.romann@uni-bremen.de
  - name: Rohit Mohan
    org: Cisco Systems
    street: 170 West Tasman Drive
    code: 95134
    city: San Jose
    country: USA
    email: rohitmo@cisco.com
  - name: Lorenzo Corneo
    org: Ericsson
    street: Hirsalantie 11
    code: 02420
    city: Jorvas
    country: Finland
    email: lorenzo.corneo@ericsson.com

normative:
  RFC7252: coap
  RFC7641: observe
  RFC7959: blockwise
  RFC8323: coap-tcp
  RFC8610: cddl
  RFC9880: sdf
  I-D.ietf-asdf-sdf-protocol-mapping: sdf-protocol-mapping
  I-D.ietf-asdf-instance-information: sdf-instance-information

informative:
  WoT-CoAP-Binding:
    title: Web of Things (WoT) CoAP Binding
    author:
      - name: Klaus Hartke
      - name: Jan Romann
    date: false
    target: https://w3c.github.io/wot-binding-templates/bindings/protocols/coap/index.html

...

--- abstract

This memo defines vocabulary to integrate the Constrained Application Protocol (CoAP) into Protocol Mappings {{-sdf-protocol-mapping}} for the Semantic Definition Format (SDF) for Data and Interactions of Things {{-sdf}}.

--- middle

# Introduction

This memo defines vocabulary to integrate the Constrained Application Protocol (CoAP) {{-coap}} into Protocol Mappings {{-sdf-protocol-mapping}} for the Semantic Definition Format (SDF) for Data and Interactions of Things {{-sdf}}.

<!-- TODO: Maybe this reference to WoT TD can also be removed later. -->

The vocabulary and "feature-based" approach taken within this document is heavily inspired by the CoAP Protocol Binding {{WoT-CoAP-Binding}} for the W3C Web of Things (WoT), which is to be used with WoT Thing Descriptions (TDs).
Considering SDF's role as a "hub format", we aspire to be able to also take into account CoAP vocabulary when converting from and to TDs.

An important additional aspect to the base protocol-mapping specification {{-sdf-protocol-mapping}} is the fact that we rely on instance-related messages {{-sdf-instance-information}} to complement protocol information present in SDF models.
Compared to the WoT approach, we achieve a stricter separation of model and instance information this way, reducing the amount of information that needs to be supplied by a Thing itself to a minimum to enable interactions.

# Conventions and Definitions

The definitions of {{-sdf}}, {{-sdf-protocol-mapping}}, and {{-sdf-instance-information}} apply.

{::boilerplate bcp14-tagged}

# CoAP Protocol Mapping

The Constrained Application Protocol (CoAP) has been originally specified in {{-coap}}, but has since been extended with a number of specifications such as blockwise transfer {{-blockwise}}, the observation of resources {{-observe}}, and additional transport mechanisms {{-coap-tcp}} in addition to UDP and DTLS.
The blockwise transfer and Observe extensions in particular are essential for using CoAP in practice, which is why covering the only the base specification in this document would not not enough.

A protocol mapping for CoAP should support the features currently defined for CoAP, but it should also be extensible to cover potential future additions to the CoAP specification body as well.

## General Considerations

CoAP can be used with all three kinds of interaction affordances defined in SDF {{-sdf}}, namely, `sdfProperty`, `sdfAction`, and `sdfEvent`.
The protocol mapping for an affordance MUST specify the `method` as well as an `href`, which combines the URI path and potential query parameters for the resource the interaction affordance is mapped to.
To differentiate between the available transport protocols, a URI `scheme` (with a default value of `coap` for CoAP over TCP) MAY be supplied.

Other general qualities for CoAP include parameters for blockwise transfer, the available and accepted Content-Formats, as well as the minimal polling interval that is accepted by the respective CoAP server.
Note that since CoAP messages do not allow for the use of generic headers as HTTP does, all of these qualities map to standardized CoAP options with specific semantics that are registered with IANA.
For this reason, we also need to explicitly cover relevant features with our protocol mapping specification.

In contrast to the WoT approach, the protocol binding information that is supplied via this document is targeting the _model_ level.
That means that information such as URI paths will be shared by all device instances that adhere to the given model.
Instance-specific information, e.g., a device's `host` name or its `ipAddress`,  is provided via instance-related messages {{-sdf-instance-information}} that pass the values for the `sdfParameters` the protocol mapping defines via designated properties.
The selected `sdfProperty` definitions are indicated via JSON pointers within the `sdfParameters` map.

Per interaction affordance type, the CoAP Protocol Mapping defines at least one type of operation (`read`, `write`, `invoke`, and `subscribe`).
Currently, the definitions for these different operations look almost identitical, with the main difference being the default method per operation.
Future specifications may extend the set of operations per interaction affordance type.

## Properties

With `sdfProperty`, a `read` operation (default method: `GET`) and a `write` operation (default method: `PUT`) are supported when using CoAP.

Note that this memo does not define an "observe" operation as it is already covered by the `read` operation:
With a property that is marked as `observable`, a client can simply include the CoAP Observe option {{-observe}} in its `GET` or `FETCH` request.
If the server that receives the request does not support the Observe option, the client can simply fall back to polling.

## Actions

In the case `sdfAction`, an `invoke` operation is supported when using CoAP.
This operation uses the `POST` method by default.

## Events

In the case of `sdfEvent`, a `subscribe` operation is supported when using CoAP.

This operation is very similar to the `read` operation, with the main difference that a client SHOULD always assume that the indicated resource is observable.
If the observe option is not supported, the client SHOULD fall back to polling.
While polling, a client is likely to receive responses only asynchronously (i.e., when the described event actually occurs).

# Examples

TODO

# Security Considerations

The security considerations of {{-sdf}} as well as {{-coap}} apply to this document as well.

<!-- TODO: Add additional references/considerations. -->

# IANA Considerations

This document has no IANA actions.

# Formal Syntax of the SDF Protocol Mapping for CoAP  {#syntax}

This normative appendix describes the syntax of this protocol mapping definition using CDDL {{-cddl}}.

<!-- TODO: Actually add extension points -->
Via the defined extension points, future specifications may add new definitions to the CDDL schema.

~~~ cddl
{::include sdf-coap-protocol-map.cddl}
~~~

--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
