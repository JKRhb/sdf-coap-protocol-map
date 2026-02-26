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

normative:
  RFC7252: coap
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

TODO

## General Considerations

TODO

## Properties

TODO

## Actions

TODO

## Events

TODO

# Examples

TODO

# Security Considerations

The security considerations of {{-sdf}} as well as {{-coap}} apply to this document as well.

<!-- TODO: Add additional references/considerations. -->

# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
